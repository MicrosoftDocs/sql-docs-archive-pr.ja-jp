---
title: 'チュートリアル: レポートへの円グラフの追加 (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eaadf7bf-c312-428a-b214-0a1fbf959c3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 318370b185dcd75a8c3c54be49c47756bad5f3c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720961"
---
# <a name="tutorial-add-a-pie-chart-to-your-report-report-builder"></a>チュートリアル: レポートへの円グラフの追加 (レポート ビルダー)
  円グラフおよびドーナツ グラフは、データを全体に対する比率として表示します。 円グラフは、主に、グループ間の比較を示すために使用されます。 円グラフとドーナツグラフは、ピラミッドグラフおよびじょうごグラフと共に、図形グラフと呼ばれるグラフのグループを構成します。 図形グラフには軸がありません。 図形グラフに数値フィールドをドロップすると、それぞれの値の全体に占める比率が計算されます。  
  
 円グラフのデータ ポイントが多すぎると、データ ポイント ラベルが過密状態になって見づらくなる場合があります。 その場合は、折れ線グラフの使用を検討してください。 円グラフは、データを少数のデータ ポイントに集計したうえで使用するようにします。  
  
 次の図に、ここで作成する円グラフを示します。  
  
 ![rs_TutorialPieChartConcave](../../2014/tutorials/media/rs-tutorialpiechartconcave.gif "rs_TutorialPieChartConcave")  
  
##  <a name="what-you-will-learn"></a><a name="BackToTop"></a>学習内容  
 このチュートリアルでは、次の内容を学習します。  
  
1.  [グラフ ウィザードから円グラフを作成する](#Chart)  
  
2.  [グラフの種類を選択する](#ChartType)  
  
3.  [各スライスにパーセンテージを表示する](#Percentages)  
  
4.  [小さな複数のスライスを 1 つのスライスにまとめる](#CombineSlices)  
  
5.  [描画効果をカスタマイズする](#DrawingEffect)  
  
6.  [レポートタイトルを追加する](#Title)  
  
7.  [レポートを保存する](#Save)  
  
> [!NOTE]  
>  このチュートリアルでは、ウィザードに関する手順を 2 つにまとめて示します。 レポート サーバーの参照、データ ソースの選択、データセットの作成に関する詳細な手順については、このシリーズの最初のチュートリアル (「[チュートリアル: 基本的な表レポートの作成 (レポート ビルダー)](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)」) を参照してください。  
  
 このチュートリアルの推定所要時間: 10 分  
  
## <a name="requirements"></a>必要条件  
 要件に関する詳細については、「[チュートリアルの前提条件 (レポート ビルダー)](../reporting-services/report-builder-tutorials.md)」を参照してください。  
  
##  <a name="1-create-a-pie-chart-from-the-chart-wizard"></a><a name="Chart"></a>1. グラフウィザードから円グラフを作成する  
 [作業の開始] ダイアログ ボックスで、グラフ ウィザードを使用して埋め込みデータセットを作成し、共有データ ソースを選択して、円グラフを作成します。  
  
> [!NOTE]  
>  このチュートリアルのクエリにはデータ値が含まれているため、外部のデータ ソースを必要としません。 このため、クエリが非常に長くなっています。 ビジネス環境でクエリにデータを含めることはありません。 これは、学習に使用することのみを目的としています。  
  
#### <a name="to-create-a-new-chart-report"></a>新しいグラフ レポートを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[プログラム]**、 **[Microsoft SQL Server 2012 レポート ビルダー]** の順にポイントして、 **[レポート ビルダー]** をクリックします。  
  
     [作業の開始] ダイアログ ボックスが表示されます。  
  
    > [!NOTE]  
    >  [はじめに] ダイアログボックスが表示されない場合は、[レポートビルダー] ボタンの [**新規作成**] をクリックします。  
  
2.  左ペインで、 **[新しいレポート]** が選択されていることを確認します。  
  
3.  右ペインで、 **[グラフ ウィザード]** をクリックします。  
  
4.  **[データセットの選択]** ページで **[データセットを作成する]** をクリックし、 **[次へ]** をクリックします。  
  
5.  **[データ ソースへの接続の選択]** ページで、既存のデータ ソースを選択するか、レポート サーバーを参照してデータ ソースを選択し、 **[次へ]** をクリックします。 ユーザー名とパスワードの入力が必要な場合があります。  
  
    > [!NOTE]  
    >  適切な権限を持っている限り、選択するデータ ソースは重要ではありません。 データ ソースからはデータを取得しません。 詳細については、[「別の方法でデータ接続を取得する &#40;レポート ビルダー&#41;」](../reporting-services/alternative-ways-to-get-a-data-connection-report-builder.md)を参照してください。  
  
6.  [**クエリのデザイン**] ページで、[**テキストとして編集**] をクリックします。  
  
7.  次のクエリをクエリ ペインに貼り付けます。  
  
    ```  
    SELECT 'Advanced Digital Camera' AS Product, CAST(254995.21 AS money) AS Sales  
    UNION SELECT 'Slim Digital Camera' AS Product, CAST(164499.04 AS money) AS Sales  
    UNION SELECT 'SLR Digital Camera' AS Product, CAST(782176.79 AS money) AS Sales  
    UNION SELECT 'Lens Adapter' AS Product, CAST(36333.08 AS money) AS Sales  
    UNION SELECT 'Macro Zoom Lens' AS Product, CAST(40199.3 AS money) AS Sales  
    UNION SELECT 'USB Cable' AS Product, CAST(53245.5 AS money) AS Sales  
    UNION SELECT 'Independent Filmmaker Camcorder' AS Product, CAST(452288.0 AS money) AS Sales  
    UNION SELECT 'Full Frame Digital Camera' AS Product, CAST(247250.85 AS money) AS Sales  
    ```  
  
8.  (省略可) [実行] ボタン (**!**) をクリックして、グラフの基になるデータを確認します。  
  
9. **[次へ]** をクリックします。  
  
##  <a name="2-choose-the-chart-type"></a><a name="ChartType"></a>2. グラフの種類を選択する  
 あらかじめ定義されているさまざまなグラフの種類から選択できます。  
  
#### <a name="to-add-a-pie-chart"></a>円グラフを追加するには  
  
1.  [**グラフの種類の選択**] ページで、[**円**] をクリックし、[**次へ**] をクリックします。 **[グラフのフィールドの配置]** ページが開きます。  
  
     **[グラフのフィールドの配置]** ページで、Product フィールドを **[カテゴリ]** ペインにドラッグします。 カテゴリは円グラフのスライスの数を定義します。 この例では、各製品に 1 つずつ、合計 8 個のスライスになります。  
  
2.  Sales フィールドを **[値]** ペインにドラッグします。 Sales は、サブカテゴリの売上高を表します。 各製品の集計がグラフに表示されるので、[**値**] ペインが表示され `[Sum(Sales)]` ます。  
  
3.  **[次へ]** をクリックします。  
  
4.  [**スタイルの選択**] ページのスタイルペインで、スタイルを選択します。  
  
     スタイルは、フォント スタイル、色、および罫線のスタイルを指定します。 スタイルを選択すると、プレビュー ペインにそのスタイルのグラフのサンプルが表示されます。  
  
5.  **[完了]** をクリックします。  
  
     グラフがデザイン画面に追加されます。  
  
6.  グラフをクリックして、グラフのハンドルを表示します。 グラフの右下隅をドラッグして、グラフのサイズを大きくします。 レポート デザイン画面も、グラフ サイズに合わせて大きくなります。  
  
7.  **[実行]** をクリックして、レポートをプレビューします。  
  
 各製品に 1 つずつ、合計 8 個のスライスを含む円グラフがレポートに表示されます。 各スライスのサイズはその製品の売上を表します。 これらのスライスのうち 3 つは、非常に小さくなります。  
  
##  <a name="3-display-percentages-in-each-slice"></a><a name="Percentages"></a>3. 各スライスにパーセンテージを表示する  
 円グラフの各スライスには、そのスライスの全体に占めるパーセンテージを表示できます。  
  
#### <a name="to-display-percentages-in-each-slice-of-the-pie-chart"></a>円グラフの各スライスにパーセンテージを表示するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  円グラフを右クリックし、 **[データ ラベルの表示]** をクリックします。 グラフにデータ ラベルが表示されます。  
  
3.  ラベルを右クリックし、[**系列ラベルのプロパティ**] をクリックします。  
  
4.  [ラベルデータ] のドロップダウンボックスから、[ **#PERCENT**] を選択します。  
  
     値をパーセンテージとして表示するには、UseValueAsLabel プロパティを false に設定する必要があります。 **[アクションの確認]** ダイアログでこの値の設定を求めるメッセージが表示されたら、 **[はい]** をクリックします。  
  
5.  Optionalラベルに表示する小数点以下桁数を指定するには、「」と入力し `#PERCENT{Pn}` ます。ここで、 *n*は、表示する小数点以下の桁数です。 たとえば、小数点以下の桁数を表示しない場合は、「」と入力 `#PERCENT{P0}` します。  
  
    > [!NOTE]  
    >  **[系列ラベルのプロパティ]** ダイアログ ボックスの **[数値書式]** は、パーセンテージの表示形式には影響しません。 この場合、ラベルの表示形式がパーセンテージに設定されるだけで、円グラフに対する各スライスのパーセンテージが計算されるわけではありません。  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  **[実行]** をクリックして、レポートをプレビューします。  
  
 円グラフの各スライスがそれぞれ全体の何パーセントを占めているかが表示されます。  
  
##  <a name="4-combine-small-slices-into-one-slice"></a><a name="CombineSlices"></a>4. 小さいスライスを1つのスライスにまとめる  
 円グラフ内の 3 つのスライスは、非常に小さくなります。 複数の小さなスライスをまとめて 1 つの大きなスライスで表すことができます。  
  
#### <a name="to-combine-any-slices-on-the-pie-chart-smaller-than-5-percent-into-one-slice"></a>円グラフの 5% 未満のスライスを 1 つのスライスにまとめるには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  [**表示**] タブの [**表示/非**表示] グループで、[**プロパティ**] を選択します。  
  
3.  デザイン画面で、円グラフの任意のスライスをクリックします。 系列のプロパティが [プロパティ] ペインに表示されます。  
  
4.  **[全般]** セクションで、 **[CustomAttributes]** ノードを展開します。  
  
5.  **[CollectedStyle]** プロパティを **[SingleSlice]** に設定します。  
  
6.  **[CollectedThreshold]** プロパティが 5 に設定されていることを確認します。  
  
7.  **[CollectedThresholdUsePercent]** プロパティが **True**に設定されていることを確認します。  
  
8.  リボンの [**ホーム**] タブで、[**実行**] をクリックしてレポートをプレビューします。  
  
 凡例に "その他" というカテゴリが追加されています。 この新しいスライスでは、5% 未満のすべてのスライスが 1 つにまとめられて、円グラフ全体の 6% を占めるスライスが作成されています。  
  
##  <a name="5-customize-the-drawing-effect"></a><a name="DrawingEffect"></a>5. 描画効果をカスタマイズする  
 グラフ ウィザードの場合、円グラフの既定のスタイルは、凹型の描画効果が特徴的な [オーシャン] です。 スタイルは、ウィザードの実行後にも変更できます。  
  
#### <a name="to-add-a-drawing-effect-to-the-pie-chart"></a>円グラフに描画効果を追加するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  プロパティペインがまだ開いていない場合は、[**表示**] タブで [**プロパティ**] を選択します。  
  
3.  円グラフ自体をダブルクリックします。 プロパティ ペインに、円グラフの系列のプロパティが表示されます。  
  
4.  プロパティ ペインで、 **[CustomAttributes]** ノードを展開します。  
  
5.  **PieDrawingStyle**を**SoftEdge**に設定します。  
  
    > [!NOTE]  
    >  描画効果と 3 次元効果を同時に使用することはできません。 グラフに3次元効果が適用されている場合、[プロパティ] ペインで**PieDrawingStyle**を使用することはできません。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
 次の図に、ぼかし効果が適用された円グラフを示します。  
  
 ![rs_TutorialPieChartSoftEdge](../../2014/tutorials/media/rs-tutorialpiechartsoftedge.gif "rs_TutorialPieChartSoftEdge")  
  
##  <a name="6-add-a-report-title"></a><a name="Title"></a>6. レポートタイトルを追加する  
  
#### <a name="to-add-a-report-title"></a>レポート タイトルを追加するには  
  
1.  デザイン画面で、 **[クリックしてタイトルを追加]** をクリックします。  
  
2.  「 **Camera and Camcorder Sales**」と入力して Enter キーを押し、さらに「 **As a Percentage of Total Sales**」と入力します。次のように表示されます。  
  
     **Camera and Camcorder Sales**  
  
     **As a Percentage of Total Sales**  
  
3.  [**カメラとカムコーダーの売上**] を選択し、リボンの [**ホーム**] タブの [**フォント**] セクションで [**太字**] ボタンをクリックします。  
  
4.  **全体の売上に対する比率**としてを選択し、[**ホーム**] タブの [**フォント**] セクションで、フォントサイズを**10**に設定します。  
  
5.  (省略可) 2 行のテキストに合わせて、[タイトル] テキスト ボックスの高さを高くする必要が生じる場合もあります。  
  
     このタイトルは、レポートの最上部に表示されます。 ページ ヘッダーが定義されていないとき、レポート本文の最上部にあるアイテムがレポート ヘッダーに相当します。  
  
6.  **[実行]** をクリックして、レポートをプレビューします。  
  
##  <a name="7-save-the-report"></a><a name="Save"></a>7. レポートを保存する  
  
#### <a name="to-save-the-report"></a>レポートを保存するには  
  
1.  レポート デザイン ビューに切り替えます。  
  
2.  レポート ビルダー のボタンの **[名前を付けて保存]** をクリックします。  
  
3.  **[名前]** に「 **Sales Pie Chart**」と入力します。  
  
4.  **[保存]** をクリックします。  
  
 レポートがレポート サーバーに保存されます。  
  
## <a name="next-steps"></a>次の手順  
 これで、「レポートへの円グラフの追加」チュートリアルを終了します。 グラフの詳細については、「[グラフ (レポート ビルダーおよび SSRS)](report-design/charts-report-builder-and-ssrs.md)」と「[スパークラインとデータ バー (レポート ビルダーおよび SSRS)](report-design/sparklines-and-data-bars-report-builder-and-ssrs.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md)   
 [SQL Server 2014 のレポート ビルダー](report-builder/report-builder-in-sql-server-2016.md)  
  
  
