---
title: 多次元データソースからのインポート (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b26cc8ed7237f87fa5e23c6a2fd47e18de2c165
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645237"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a>多次元データ ソースからのインポート (SSAS テーブル)
  Analysis Services キューブ データベースは、テーブル モデルのデータ ソースとして使用できます。 Analysis Services キューブからデータをインポートするには、インポートするデータを選択するための MDX クエリを定義する必要があります。  
  
 SQL Server Analysis Services データベースに含まれている任意のデータをモデルにインポートできます。 ディメンションの一部またはすべてを抽出することも、キューブからスライスおよび集計 (現在の年の月ごとの売上合計など) を取得することもできます。ただし、キューブからインポートしたデータはすべてフラット化されていることに注意する必要があります。 したがって、複数のディメンションからメジャーを取得するクエリを定義した場合、インポートされるデータでは各ディメンションがそれぞれ別の列になります。  
  
 Analysis Services キューブのバージョンは、SQL Server 2005、SQL Server 2008、SQL Server 2008 R2、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]、または [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]である必要があります。  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>Analysis Services キューブからデータをインポートするには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[モデル]** メニューをクリックし、 **[データ ソースからのインポート]** をクリックします。  
  
2.  **[データ ソースへの接続]** ページで、 **[Microsoft Analysis Services]** を選択し、 **[次へ]** をクリックします。  
  
3.  テーブルのインポート ウィザードの手順に従って操作します。 **[MDX クエリの指定]** ページで MDX クエリを指定できます。 MDX クエリ デザイナーを使用するには、[MDX クエリの指定] ページで **[デザイン]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;データをインポートする](import-data-ssas-tabular.md)   
 [サポートされているデータ ソース &#40;SSAS テーブル&#41;](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
