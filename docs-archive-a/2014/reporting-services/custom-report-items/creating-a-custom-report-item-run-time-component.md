---
title: カスタム レポート アイテムの実行時コンポーネントの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- custom report items, creating
ms.assetid: b3e15a4a-98f8-4dbb-b847-bbcb20327051
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50c5c0211bc5cd1359af9d1493782bd9d96c2b3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631669"
---
# <a name="creating-a-custom-report-item-run-time-component"></a>カスタム レポート アイテムの実行時コンポーネントの作成
  カスタムレポートアイテムの実行時コンポーネントは、任意の CLS 準拠の言語を使用するコンポーネントとして実装され、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 実行時にレポートプロセッサによって呼び出されます。 実行時コンポーネントのプロパティをデザイン環境で定義するには、カスタム レポート アイテムの対応するデザイン時コンポーネントを変更します。  

<!--
Replacing the following multiValue.....

ms.technology: 
  - "docset-sql-devref"
  - "reporting-services-native"

.....with the following single value.....

ms.technology: reporting-services
.

(GeneMi = MightyPen  ,  2019-04-20  ,  DevO= 1515083)
-->

 完全に実装されたカスタム レポート アイテムの例については、「[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889)」 (SQL Server Reporting Services の製品サンプル) を参照してください。  
  
## <a name="definition-and-instance-objects"></a>定義オブジェクトおよびインスタンス オブジェクト  
 カスタム レポート アイテムを実装する前に、*定義オブジェクト*と*インスタンス オブジェクト*の違いを理解しておくことが重要です。 定義オブジェクトはカスタム レポート アイテムの RDL 表記を提供するのに対し、インスタンス オブジェクトは定義オブジェクトの評価されたバージョンです。 定義オブジェクトは、レポートの各アイテムに 1 つしか存在しません。 定義オブジェクトのプロパティのうち、式が含まれたプロパティにアクセスすると、評価されていない式の文字列を取得します。 インスタンス オブジェクトには定義オブジェクトの評価されたバージョンが含まれるので、インスタンス オブジェクトはアイテムの定義オブジェクトと一対多のリレーションシップを持つことができます。 たとえば、詳細行に <xref:Microsoft.ReportingServices.OnDemandReportRendering.Tablix> を含む <xref:Microsoft.ReportingServices.OnDemandReportRendering.CustomReportItem> データ領域がレポートにある場合、定義オブジェクトは 1 つしか存在しませんが、インスタンス オブジェクトはデータ領域の各行に存在します。  
  
## <a name="implementing-the-icustomreportitem-interface"></a>ICustomReportItem インターフェイスの実装  
 `CustomReportItem` 実行時コンポーネントを作成するには、<xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> インターフェイスを実装する必要があります。このインターフェイスは Microsoft.ReportingServices.ProcessingCore.dll で次のように定義されています。  
  
```csharp  
namespace Microsoft.ReportingServices.OnDemandReportRendering  
{  
    public interface ICustomReportItem  
    {  
        void GenerateReportItemDefinition(CustomReportItem customReportItem);  
void EvaluateReportItemInstance(CustomReportItem customReportItem);  
    }  
}  
```  
  
 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem> インターフェイスを実装すると、<xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> および <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> という 2 つのメソッド スタブが生成されます。 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.GenerateReportItemDefinition%2A> メソッドが最初に呼び出され、定義プロパティの設定と <xref:Microsoft.ReportingServices.OnDemandReportRendering.Image> オブジェクトの作成に使用されます。このオブジェクトには、アイテムの表示に使用される定義プロパティとインスタンス プロパティの両方が含まれます。 <xref:Microsoft.ReportingServices.OnDemandReportRendering.ICustomReportItem.EvaluateReportItemInstance%2A> メソッドは、定義オブジェクトの評価後に呼び出され、アイテムの表示に使用されるインスタンス オブジェクトを提供します。  
  
 次に、コントロール名をイメージとして表示するカスタム レポート アイテムの実装例を示します。  
  
```csharp  
namespace Microsoft.Samples.ReportingServices  
{  
    using System;  
    using System.Collections.Generic;  
    using System.Collections.Specialized;  
    using System.Drawing.Imaging;  
    using System.IO;  
    using System.Text;  
    using Microsoft.ReportingServices.OnDemandReportRendering;  
  
    public class PolygonsCustomReportItem : ICustomReportItem  
    {  
        #region ICustomReportItem Members  
  
        public void GenerateReportItemDefinition(CustomReportItem cri)  
        {  
            // Create the Image object that will be   
            // used to render the custom report item  
            cri.CreateCriImageDefinition();  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
        }  
  
        public void EvaluateReportItemInstance(CustomReportItem cri)  
        {  
            // Get the Image definition  
            Image polygonImage = (Image)cri.GeneratedReportItem;  
  
            // Create the image for the custom report item  
            polygonImage.ImageInstance.ImageData = DrawImage(cri);  
        }  
  
        #endregion  
  
        /// <summary>  
        /// Creates an image of the CustomReportItem's name  
        /// </summary>  
        private byte[] DrawImage(CustomReportItem customReportItem)  
        {  
            int width = 1;          // pixels  
            int height = 1;         // pixels  
            int resolution = 75;    // dpi  
  
            System.Drawing.Bitmap bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            System.Drawing.Graphics graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Get the Font for the Text  
            System.Drawing.Font font = new System.Drawing.Font(System.Drawing.FontFamily.GenericMonospace,  
                12, System.Drawing.FontStyle.Regular);  
  
            // Get the Brush for drawing the Text  
            System.Drawing.Brush brush = new System.Drawing.SolidBrush(System.Drawing.Color.LightGreen);  
  
            // Get the measurements for the image  
            System.Drawing.SizeF maxStringSize = graphics.MeasureString(customReportItem.Name, font);  
            width = (int)(maxStringSize.Width + 2 * font.GetHeight(resolution));  
            height = (int)(maxStringSize.Height + 2 * font.GetHeight(resolution));  
  
            bitmap.Dispose();  
            bitmap = new System.Drawing.Bitmap(width, height);  
            bitmap.SetResolution(resolution, resolution);  
  
            graphics.Dispose();  
            graphics = System.Drawing.Graphics.FromImage(bitmap);  
            graphics.PageUnit = System.Drawing.GraphicsUnit.Pixel;  
  
            // Draw the text  
            graphics.DrawString(customReportItem.Name, font, brush, font.GetHeight(resolution),   
                font.GetHeight(resolution));  
  
            // Create the byte array of the image data  
            MemoryStream memoryStream = new MemoryStream();  
            bitmap.Save(memoryStream, ImageFormat.Bmp);  
            memoryStream.Position = 0;  
            byte[] imageData = new byte[memoryStream.Length];  
            memoryStream.Read(imageData, 0, imageData.Length);  
  
            return imageData;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>参照  
 [カスタムレポートアイテムのアーキテクチャ](custom-report-item-architecture.md)   
 [カスタムレポートアイテムのデザイン時コンポーネントの作成](creating-a-custom-report-item-design-time-component.md)   
 [カスタムレポートアイテムクラスライブラリ](custom-report-item-class-libraries.md)   
 [方法: カスタム レポート アイテムを配置する](how-to-deploy-a-custom-report-item.md)  
  
  
