---
title: データ フロー内でコンポーネントを連結する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], connections
- connections [Integration Services], data flow components
ms.assetid: 70616a58-8921-4218-85bf-f3e90c5a9dbf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8fc4a2fa81e9b110c27ea63b16d835d069bf12cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712254"
---
# <a name="connect-components-in-a-data-flow"></a>データ フロー内でコンポーネントを連結する
  この手順は、データ フロー内のコンポーネントの出力を、同じデータ フロー内にある別のコンポーネントに連結する方法について説明します。  
  
### <a name="to-connect-components-in-a-data-flow"></a>データ フロー内でコンポーネントを連結するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  **[制御フロー]** タブをクリックし、コンポーネントを連結するデータ フローが含まれているデータ フロー タスクをダブルクリックします。  
  
4.  **[データ フロー]** タブのデザイン画面で、連結する変換または変換元を選択します。  
  
5.  変換または変換元の出力を表す緑の矢印を、変換または変換先にドラッグします。 一部のデータ フロー コンポーネントはエラー出力をとり、同様の方法で連結できます。  
  
    > [!NOTE]  
    >  一部のデータ フロー コンポーネントには複数の出力があります。これらの各出力は、それぞれ個別の変換または変換先に連結できます。  
  
6.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [データフロー内のコンポーネントを追加または削除する](data-flow.md)   
 [データフローコンポーネントでのエラー出力の構成](../configure-an-error-output-in-a-data-flow-component.md)   
 [データ フロー](data-flow.md)  
  
  
