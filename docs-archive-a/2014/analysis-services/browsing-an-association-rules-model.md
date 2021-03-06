---
title: アソシエーションルールモデルの参照 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, browsing
- mining model, association
- mining models, viewing
- association [data mining]
ms.assetid: faffe208-7a64-4ec6-825f-ecbaa79caff7
author: minewiskan
ms.author: owend
ms.openlocfilehash: de5adbca264fff81b44424d865a2c8201a6fdfc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633555"
---
# <a name="browsing-an-association-rules-model"></a>アソシエーション ルール モデルの参照
  **参照**を使用してアソシエーションモデルを開くと、のアソシエーションルールビューアーに似た対話型ビューアーにモデルが表示され [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。  このビューアーを使用すると、相互に関連付けられたアイテムをひとめで確認できます。また、このビューアーには、予測または提案を行うために使用できるルールが表示されます。  
  
##  <a name="explore-the-model"></a><a name="BKMK_ViewerTabs"></a>モデルの調査  
 アソシエーションルールアルゴリズムを使用して作成されたマイニングモデルを開くと、[ [!INCLUDE[msCoName](../includes/msconame-md.md)] **参照**] ウィンドウに次のビューが表示されます。各ビューは、モデルのさまざまな側面を調べることができるように設計されています。  
  
-   [アイテムセット](#BKMK_Itemsets)  
  
-   [ルール](#BKMK_Rules)  
  
-   [依存関係ネットワーク](#BKMK_Dependency)  
  
 各タブの [**長い名前を表示する**] オプションをメモしておきます。 このチェック ボックスをオンにすると、アイテムセットの元のテーブルを表示/非表示を切り替えたり、ルールまたはアイテムセットの名前の長さを変更したりすることができます。 このオプションは、ケース データと属性データが異なるデータ ソースから取得されている場合に特に役立ちます。  
  
 アソシエーション モデルをテストするには、サンプル データ ブックの [関連付け] タブにあるサンプル データを使用し、すべて既定値のままでアソシエーション モデルを作成します。 また、買い物かご分析モデルを作成して、[**参照**] を使用して開くこともできます。  
  
###  <a name="itemsets"></a><a name="BKMK_Itemsets"></a>アイテムセット  
 [**アイテムセット**] タブは、アソシエーションモデルの調査を開始するのに適した場所です。 このタブには、モデルによって同時に検出される頻度の高いアイテムの一覧が表示されます。  
  
 ![アソシエーション モデルのアイテムの一覧](media/dm13-association-itemsets.gif "アソシエーション モデルのアイテムの一覧")  
  
 アイテムセットの最も一般的な例は、買い物かごモデルにあります。買い物かごモデルでは、多くの顧客が同時に購入する製品の組み合わせやセットをアイテムセットで表します。 ただし、アイテムをどのようにグループ化および並べ替えするかに応じて、アイテムセットには、顧客が一定期間に注文した一連の映画や、特定の場所で開催される傾向のあるイベントが含まれる場合があります。  
  
 アイテムセットに含めることができる項目の数は 2 ~ 3 つ*ですが、* 多くの場合、モデルのアイテムセットの最大サイズとして設定されています。 ビューアーには、アイテムセットの*サポート*、*確率*、および*サイズ*が表示されます。 サポートと確率は、アソシエーション モデルで生成されたアイテムセットとルールに順位を付けるための主要な統計です。 これらの値は、重要度の計算と説明にも使用されます。  
  
 **サポート**。 サポートは、このアイテムを含む入力データのケースまたは行の数を示します。 たとえば、アイテムセットにショッピングカートで見つかった2つのアイテムが含まれている場合、[**サポート**] 列の数値は、ソースデータでアイテムの組み合わせが何回発生したかを示します。  
  
 **[サイズ]**。 アイテムセットのサイズを変更することで、アイテムセットの一覧の長さを制御できます。 一覧に単一の製品が表示されないようにするには、[アイテムセットの**最小サイズ**] オプションを2以上に変更します。  アイテムセットの最小サイズを大きくして、表示するアイテムセットを制限すれば、より明確なパターンを見つけることができます。 これは、膨大な量のデータを処理する場合にも役立ちます。  
  
 [**最小のサポート**] と [**最大行数**] の値を変更することで、タブに表示されるアイテムセットの数をフィルター処理できます。 [**最小サポート**] の値を大きくすると、一覧に表示されるアイテムセットの数は少なくなりますが、アイテムセットは入力データ内のより一般的なものになります。 共通の問題が重要であるかどうかはもう1つの質問で、[**ルール**] タブを使用して調べることができます。  
  
 [**アイテムセット**] タブのサポート値またはその他のコントロールを変更しても、表示される項目のみが変更され、基になるモデルには影響しないことに注意してください。 生成するアイテムセットの数を減らすか、サイズを制限する場合は、[ `MINIMUM_SUPPORT` `MAXIMUM_SUPPORT` **アルゴリズムパラメーター** ] ダイアログボックスで使用できるパラメーターとを使用する必要があります。  
  
##### <a name="explore-the-itemsets-list"></a>アイテムセットの一覧の調査  
  
1.  [**サポート**] 列をクリックすると、サポートのレベルが最も高いものから順に並べ替えられます。 これにより、顧客の購入頻度が最も高いものがわかります。  
  
2.  目的の特定のアイテムセットに注目するには、[アイテムセットの**フィルター** ] ボックスにテキストを入力します。  
  
     ここでは、「」と入力しました `Gloves` 。 フィルターを適用すると、一覧が更新され、グローブを含むアイテムセットのみが表示されます。 これにより、顧客がグローブとその他のアイテムを購入したトランザクションに注目することができます。  
  
     **[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。  
  
3.  [**最小のアイテム**セットのサイズ] の値を変更して、手袋のみを購入し、他のアイテムを含まない顧客を除外します。  
  
4.  属性の表示方法を制御するには、[**表示**] のドロップダウンリストをクリックします。  
  
    -   **[属性の名前と値を表示]**  
  
    -   **[属性値のみ表示]**  
  
    -   **[属性名のみ表示]**  
  
     名前がどのように変更されているかを確認してください。 複数の顧客が購入した製品の入れ子になったテーブルに基づいて作成されるマーケット バスケット モデルの場合、通常、属性名は製品名であり、一覧に製品が含まれていると "`Existing`" とマークされます (これは顧客がそのアイテムを購入したことを意味します)。  
  
     "`Existing`" の反対は "`Missing`" で、データ マイニングで調査を行う際に非常に役立つ属性となります。 たとえば、アイテム a + B が非常に人気であり、アイテム B を購入した顧客を検索する必要があるとします。これを行うには、予測クエリを使用して、一方のトランザクションだけを使用してトランザクションを取得し、その他の分析を実行します。 アソシエーションモデルに対する予測クエリの作成方法の詳細については、「SQL Server オンラインブックでの[アソシエーションモデルのクエリ例](data-mining/association-model-query-examples.md)」を参照してください。  
  
5.  新しいフィルター条件を使用してアイテムセットの一覧を強制的に再表示するには、[**長い名前を表示**する] チェックボックスをオンまたはオフにします。  
  
 [ページのトップへ](#BKMK_ViewerTabs)  
  
###  <a name="rules"></a><a name="BKMK_Rules"></a>ロジック  
 [**ルール**] タブには、アイテムセットとその相対値に関する情報が結合されます。  
  
 ![アソシエーション モデルによって作成されたルールの一覧](media/dm13-association-rules.gif "アソシエーション モデルによって作成されたルールの一覧")  
  
 *確率*は、対象となるアイテムの組み合わせを含むデータセット内のケースの割合を表します。 確率は、*信頼度*の統計的概念に似ており、ルールの結果が発生する可能性があるかどうかを示します。 このペインの [**最小確率**] の値を変更して、表示されるルールをフィルター処理できます。  
  
 最初に表示される**最小確率**の値は、モデルの作成時にアルゴリズムによって使用されたしきい値です。 モデルが完成した後は、この値を小さくすることはできませんが、大きな確率の項目だけを表示するように増やすことはできます。  
  
 *重要度*は、ルールの有用性を測定するように設計されています。 ごく一般的なルールはいたるところで見られるため、情報の価値はほとんどありません。 重要度が高いほど、結果を予測する上で、そのルールの利用価値が高くなります。 [買い物かご分析 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md) tool では、重要度と品目の価格を組み合わせて、売上の面で最も重要なバンドルを特定できます。  
  
##### <a name="explore-the-rules-list"></a>ルールの一覧の調査  
  
1.  列見出し (**確率**、**重要度**、**ルール**) をクリックして、データがどのように変化するかを確認してください。  
  
2.  [**ルールのフィルター** ] オプションを使用して、値を入力し、対象となるルールに注目します。  
  
     たとえば、顧客が手袋と共に購入される可能性があることを予測するすべてのルールを表示するには、テキストボックスに「グローブ」と入力し、ウィンドウを更新します。  
  
     **[アイテムセットのフィルター]** オプションでは、以前に使用したフィルターの一覧も表示されます。  
  
3.  フィルター条件を使用してルールの一覧を強制的に再表示するには、[**長い名前を表示**する] チェックボックスをオンまたはオフにします。  
  
4.  [**表示**] オプションを使用して、ルール名の表示方法を制御します。  
  
5.  [**最大行数**] オプションの値を100に設定し、[ **Excel にコピー**] をクリックします。  
  
     この値を変更しても、モデル内のデータ量には影響しないことに注意してください。表示リストの行数を制御するだけです。 このオプションは、非常に大規模なモデルを使用する場合に便利です。  
  
 [ページのトップへ](#BKMK_ViewerTabs)  
  
###  <a name="dependency-network"></a><a name="BKMK_Dependency"></a>依存関係ネットワーク  
 [**依存関係ネットワーク**] タブは、項目間の相関関係を視覚的にマップしたものです。 グラフ内の各楕円 (*ノード*と呼ばれます) は、属性と値のペアを表します。たとえば、"Age = Existing" または "Age = 1-30" のようになります。  楕円 (*エッジ*と呼ばれます) を接続する線は、相関関係の種類を表します。  
  
 ![アソシエーション モデルの依存関係ネットワーク グラフ](media/dm13-association-dependencynetwork.gif "アソシエーション モデルの依存関係ネットワーク グラフ")  
  
##### <a name="explore-the-dependency-network"></a>依存関係ネットワークの調査  
  
1.  [**検索**] ボタンをクリックし、[**ノードの検索**] ダイアログボックスを使用して目的の項目を入力します。  
  
     たとえば、「グローブ」と入力し、ウィンドウ内のグラフを最大化して、結果を簡単に確認できるようにします。  
  
     そのアイテムを含むノードが強調表示されると同時に、ノードを指す矢印はアイテムを結ぶルールを表します。  
  
     矢印の向きによって、ルールの方向が示されます。 たとえば、手袋を購入した人が権利を購入する可能性がある場合、矢印は "手袋" ノードから始まり、"権利がある" ノードで終了します。  
  
     このルールに関する追加の統計情報を取得するには、[**ルール**] タブをクリックし、"> 既存のもの" という説明が付いたルールを探します。  
  
2.  ビューアーの左側にあるスライダーをクリックしてドラッグします。  
  
     このスライダーは、ルールの確率に対するフィルターとして機能します。 スライダーを小さく設定すると、強力なルールのみが表示されます。  
  
3.  [ **Excel にコピー** ] をクリックして、現在のウィンドウのスナップショットを excel にコピーします。  
  
     Excel にコピーしたグラフを操作することはできません。対話型のネットワークグラフが必要な場合は、「 [Visio でのデータマイニングモデルの表示」 &#40;データマイニングアドイン&#41;](viewing-data-mining-models-in-visio-data-mining-add-ins.md)を使用します。  
  
 [ページのトップへ](#BKMK_ViewerTabs)  
  
## <a name="more-about-association-models"></a>アソシエーションモデルの詳細  
 **参照**機能を使用して、Microsoft アソシエーションルールアルゴリズムを使用して作成された任意のモデルを開いて探索することができます。 これには、[買い物かご分析 &#40;Table AnalysisTools For Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)ツール、**テーブル分析ツール**リボン、またはで作成されたモデルが含まれ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ます。  
  
 買い物かご分析ツールを使用してアソシエーション ルール モデルを作成した場合、詳細設定オプションの多くは自動的に構成されます。  
  
 高度なパラメーターを設定したり、最小の確率とサポートを変更したりするには、[excel [&#41;用のデータマイニングクライアント &#40;](associate-wizard-data-mining-client-for-excel.md) ] ウィザードを使用するか、または [ [&#40;構造へのモデルの追加] [Excel 用データマイニングアドイン&#41;](add-model-to-structure-data-mining-add-ins-for-excel.md)モデリング] オプションを使用して独自のモデルを作成します。  
  
-   **アイテムセット:** モデルを作成するときに、MINIMUM_PROBABILITY パラメーターに値を割り当てることによって生成されるアイテムセットの数を制御することもできます。 このパラメーターは、[アルゴリズム パラメーター] ダイアログ ボックスで設定できます。  
  
-   **ルール:**[!INCLUDE[msCoName](../includes/msconame-md.md)]アソシエーションルールアルゴリズムでは、確率値を使用して、生成されるルールの数を制限します。 ルールの数を制御するには、`MINIMUM_PROBABILITY` パラメーターまたは `MINIMUM _IMPORTANCE` パラメーターを設定します。  
  
 詳細なパラメーターの構成の詳細については、「データマイニング[アルゴリズム &#40;SQL Server データマイニングアドイン&#41;](data-mining-algorithms-sql-server-data-mining-add-ins.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Excel &#40;SQL Server データマイニングアドインのモデルの参照&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
