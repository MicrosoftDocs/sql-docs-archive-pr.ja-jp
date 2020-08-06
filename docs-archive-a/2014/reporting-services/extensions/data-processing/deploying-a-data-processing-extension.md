---
title: データ処理拡張機能の配置 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- data processing extensions [Reporting Services], deploying
- Extension element
- deploying [Reporting Services], extensions
ms.assetid: e5c0b5a9-1386-47cb-aade-96653ecfaa54
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 84fc2d2853ce7a6aae77f313ef0f4026ad2f35cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741605"
---
# <a name="deploying-a-data-processing-extension"></a>データ処理拡張機能の配置
  ご自分の [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能は、作成して [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ライブラリにコンパイルした後、レポート サーバーおよびレポート デザイナーで検出できるようにする必要があります。 これは、適切なディレクトリに拡張機能をコピーし、適切な [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 構成ファイルにエントリを追加するだけで簡単に行うことができます。  
  
## <a name="configuration-file-extension-element"></a>構成ファイルの Extension 要素  
 レポート サーバーまたはレポート デザイナーに配置するデータ処理拡張機能は、構成ファイルに **Extension** 要素として入力する必要があります。 構成ファイルは、レポート サーバーの場合は RSReportServer.config、レポート デザイナーの場合は RSReportDesigner.config です。  
  
 次の表では、データ処理拡張機能の **Extension** 要素の属性について説明します。  
  
|Attribute|説明|  
|---------------|-----------------|  
|`Name`|拡張機能の一意な名前。たとえば、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ処理拡張機能に対して "SQL"、OLE DB データ処理拡張機能に対して "OLEDB"。 `Name` 属性の最大文字数は 255 文字です。 名前は、構成ファイルの **Extension** 要素内にあるすべてのエントリの間で一意にする必要があります。|  
|`Type`|アセンブリの名前と共に完全修飾名前空間を含むコンマ区切りの一覧。|  
|`Visible`|`false` の値は、データ処理拡張機能がユーザー インターフェイスに表示されないことを示します。 この属性が指定されない場合、既定値は `true` になります。|  
  
 RSReportServer.config ファイルまたは RSReportDesigner.config ファイルの詳細については、「[Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[データ処理拡張機能をレポート サーバーに配置する方法](deploying-a-data-processing-extension-to-a-report-server.md)|レポート サーバーにデータ処理拡張機能を配置する方法について説明します。|  
|[データ処理拡張機能をレポート デザイナーに配置する方法](deploying-a-data-processing-extension-to-report-designer.md)|レポート デザイナーにデータ処理拡張機能を配置する方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../reporting-services-extensions.md)   
 [データ処理拡張機能の実装](implementing-a-data-processing-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
