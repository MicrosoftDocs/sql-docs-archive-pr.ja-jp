---
title: 'レッスン 3: マーケットバスケットシナリオの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a281aa62fbf08393c95f12ded9886ac212b3165f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720481"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a>レッスン 3: マーケット バスケット シナリオの作成 (中級者向けデータ マイニング チュートリアル)
  [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] のマーケティング部門は、クロスセルを促進するため自社の Web サイトを改善しようとしています。 サイトの更新に伴い、顧客の買い物かごの中に入っている他製品に基づいてその顧客が購入する可能性がある製品を予測できるようにしたいと考えています。 さらに、顧客の購入行動をより深く理解して、一緒に購入される可能性があるアイテムが同時に表示されるように Web サイトを設計したいとも考えています。 彼らはこの種の *マーケット バスケット分析* にはデータ マイニングが非常に効果的であることを理解しており、あなたにデータ マイニング モデルの開発を依頼してきました。  
  
 このレッスンを完了すると、顧客のトランザクション履歴から商品のグループを表示する完全なマイニング モデルを作成できます。 さらに、このマイニング モデルを使用して、顧客が追加購入する可能性がある商品を予測できます。  
  
 このレッスンのタスクを完了するには、「中級者向け[データマイニングチュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」の最初のレッスンで作成したソリューションとデータソースを使用します。 顧客関連のテーブル (顧客の購入情報が格納される入れ子になったテーブルなど) を含むデータ ソース ビューを追加することで、このソリューションを変更します。  次に、マーケット バスケット シナリオに適した Microsoft アソシエーション ルール アルゴリズムを使用するマイニング モデルを作成します。  
  
 このレッスンの内容は次のとおりです。  
  
-   [入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [&#40;中級者向けデータマイニングチュートリアルの作成&#41;](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [「中級者向けデータマイニングチュートリアル &#40;のマーケットバスケットモデルの変更と処理&#41;](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [&#40;中級者向けデータマイニングチュートリアルに関するマーケットバスケットモデルの調査&#41;](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [マイニングモデルでの入れ子になったテーブルのフィルター処理 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [&#41;の関連付けの予測 &#40;中級者向けデータマイニングチュートリアル](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [入れ子になったテーブルを含むデータソースビューの追加 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a>すべてのレッスン  
 [レッスン 1: 中級者向けデータマイニングソリューションの作成 &#40;中級者向けデータマイニングチュートリアル&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 レッスン 3: マーケット バスケット シナリオ (中級者向けデータ マイニング チュートリアル)  
  
 [レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [レッスン 5: ニューラル ネットワークおよびロジスティック回帰モデルの作成 &#40;中級者向けデータ マイニング チュートリアル&#41;](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [基本的なデータマイニングチュートリアル](../../2014/tutorials/basic-data-mining-tutorial.md)   
 [レッスン 2: 予測シナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)   
 [レッスン 4: シーケンスクラスターシナリオの構築中級者向けデータマイニングチュートリアル &#40;&#41;](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
