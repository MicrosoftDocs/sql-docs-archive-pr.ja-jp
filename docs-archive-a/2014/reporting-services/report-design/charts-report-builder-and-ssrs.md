---
title: グラフ (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.chartareaproperties.3doptions.f1
- "10256"
- sql12.rtp.rptdesigner.charttitleproperties.general.f1
- "10166"
- sql12.rtp.rptdesigner.seriesproperties.axesandchartarea.f1
- sql12.rtp.rptdesigner.chartproperties.general.f1
- sql12.rtp.rptdesigner.seriesproperties.seriesdata.f1
- "10251"
- "10172"
ms.assetid: d56d0521-362f-4361-843a-acf2c897a87c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8a68b793d25aef1e1ecdae97ded2dc15566ecc95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641467"
---
# <a name="charts-report-builder-and-ssrs"></a>グラフ (レポート ビルダーおよび SSRS)
  データをビジュアル形式でまとめるには、グラフ データ領域を使用します。 グラフを使用すると、大量の集計情報がひとめでわかります。 グラフを作成する前に、データを慎重に準備および理解することが重要です。これにより、グラフをすばやく効率的にデザインできます。 詳細については、「[レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)」を参照してください。 グラフの使用をすぐに開始するには、「チュートリアル」の横棒グラフ、縦棒グラフ、スパークライングラフ、および円グラフのチュートリアル[&#40;レポートビルダー&#41;](../report-builder-tutorials.md) 、または[Reporting Services のチュートリアル「SSRS &#40;](../reporting-services-tutorials-ssrs.md)」の横棒グラフおよび円グラフのチュートリアルを参照してください。  
  
 次の図は、グラフで使用されるさまざまな要素を示しています。  
  
 ![グラフ要素の図](../media/rs-chartelementsc.gif "グラフ要素の図")  
  
 グラフは、レポート パーツとしてレポートとは別にパブリッシュできます。 [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="designing-a-chart"></a><a name="DesigningChart"></a>グラフのデザイン  
 グラフ データ領域をデザイン画面に追加したら、グラフのグラフ データ ペインに数値データおよび非数値データのレポート データセット フィールドをドラッグします。 デザイン画面でグラフをクリックすると、カテゴリ グループ、系列グループ、および値の 3 つの領域を持つグラフ データ ペインが表示されます。 レポートに共有データセットまたは埋め込みデータセットが含まれている場合、データセットのフィールドがレポート データ ペインに表示されます。 データセットからフィールドを適切な領域にドラッグします。 既定では、フィールドがグラフのいずれかの領域に追加されると、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によってフィールドの集計が計算されます。 系列グループを使用して系列を動的に生成することもできます。 グラフは、マトリックスとも緊密な関係にあります。  
  
 ![rs_chartwSeriesCategories](../media/rs-chartwseriescategories.gif "rs_chartwSeriesCategories")  
  
> [!NOTE]  
>  デザイン時のグラフ内のデータは、レポートが処理されるときのグラフ内のデータとは異なります。 デザイン時のデータは、実際のデータではありません。 デザイン時に作成されるデータは、グラフの概要を把握してグラフを設計するために追加された生成データです。  
  
  
  
##  <a name="similarities-to-a-matrix"></a><a name="SimilarMatrix"></a>マトリックスとの類似点  
 グラフがどのように動作するかについての考え方の 1 つは、グラフをマトリックスと比較することです。  
  
 ![ツールボックスから追加された新しいマトリックス、選択済み](../media/rs-matrixtemplatenewselected.gif "ツールボックスから追加された新しいマトリックス、選択済み")  
  
 概念的には、グラフとマトリックスの組織は次のように同じです。  
  
-   マトリックスの [列] グループは、グラフの [カテゴリ グループ] 領域と同じです。  
  
-   マトリックスの [行] グループは、グラフの [系列グループ] 領域と同じです。  
  
-   マトリックスの [データ] 領域は、グラフの [値] 領域と同じです。  
  
 
  
##  <a name="adding-data-to-the-chart"></a><a name="AddingData"></a> グラフへのデータの追加  
 名前別売上を示すレポートがあるとします。 氏名フィールドを [カテゴリ グループ] 領域にドロップし、売上フィールドを [値] 領域にドロップします。  
  
 売上フィールドを [値] 領域に追加すると、データ フィールドのテキストが凡例に表示され、この数値フィールドのデータが 1 つの値に集計されます。 既定では、合計組み込み関数 SUM を使用して値が集計されます。 グラフ データ ペインには、フィールドの単純式が含まれます。 この例では、フィールド式 `[Sum(Sales)]` として、 `=Sum(Fields!Sales.Value)`が表示されます。 グループが指定されない場合、グラフで表示されるデータ ポイントは 1 つのみです。 複数のデータ ポイントを表示するには、グループ化したフィールドを追加してデータをグループ化する必要があります。 名前フィールドを [カテゴリ グループ] 領域に追加すると、フィールドの名前と同じ名前のグループ化フィールドがグラフに自動的に追加されます。 x 軸および y 軸に従って値を定義するフィールドが追加されると、データを正しくプロットするのに十分な情報がグラフに含まれることになります。  
  
 ![rs_chartwNoSeries](../media/rs-chartwnoseries.gif "rs_chartwNoSeries")  
  
 [系列グループ] 領域が空のままの場合、系列の数はデザイン時に固定されます。 この例では、売上は、グラフに表示される唯一の系列です。  
  
  
  
##  <a name="category-and-series-groups-in-a-chart"></a><a name="GroupsInChart"></a> グラフのカテゴリ グループと系列グループ  
 グラフでは、入れ子になったカテゴリ グループと系列グループがサポートされています。 グラフには詳細データは表示されません。 選択したグラフのカテゴリ ドロップ ゾーン、および系列ドロップ ゾーンにデータセット フィールドをドラッグして、グラフにグループを追加します。  
  
 円グラフなどの図形グラフでは、カテゴリ グループと入れ子になったカテゴリ グループがサポートされています。 棒グラフなどその他のグラフでは、カテゴリ グループと系列グループがサポートされています。 グループは入れ子にできますが、カテゴリまたは系列の数のためにグラフの情報の表示が見えにくくならないように確認してください。  
  
### <a name="adding-series-grouping-to-a-chart"></a>グラフへの系列グループの追加  
 フィールドを [系列グループ] 領域に追加する場合、系列の数は、フィールドに格納されているデータに応じて決定します。 前述の例で、年フィールドを [系列グループ] 領域に追加するとします。 年フィールドの数値によって、グラフに表示される系列の数が決定します。 年フィールドに 2004 年、2005 年、および 2006 年が含まれている場合、グラフでは [値] 領域のフィールドごとに 3 つの系列が表示されます。  
  
  
  
##  <a name="dataset-considerations-before-creating-a-chart"></a><a name="DatasetConsiderations"></a>グラフを作成する前のデータセットに関する注意点  
 グラフを使用すると、データの概要を表示できます。 ただし、大きなデータセットの場合、グラフの情報がわかりにくくなったり、読み取れなくなったりする可能性があります。 存在しないデータ ポイントや NULL データ ポイント、グラフの種類に適さないデータ型、およびグラフとテーブルの組み合わせなどの詳細設定の適用はすべて、グラフの読みやすさに影響します。 グラフをデザインする前に、データを慎重に準備し、理解しておく必要があります。これにより、短時間で効率的にグラフをデザインできます。  
  
 レポートには、必要な数だけグラフを作成することができます。 グラフは、マトリックスやテーブルなど他のデータ領域と同様に、1 つのデータセットにバインドされます。 複数のデータセットを同じグラフに表示する場合は、SQL クエリで JOIN ステートメントまたは UNION ステートメントを使用する追加のデータセットを作成した後、データをグラフに追加します。 JOIN ステートメントおよび UNION ステートメントの詳細については、オンライン ブックまたは SQL のその他のリファレンスを参照してください。  
  
 詳細データが不要な場合や有用ではない場合は、データセット クエリでデータを事前に集計することを検討してください。 各データ ポイントをより明確に表示するには、データセット内のカテゴリの数を減らします。 データセットをフィルター選択したり、返される行数を少なくする条件をクエリに追加したりすることができます。  
  
##  <a name="best-practices-when-displaying-data-in-a-chart"></a><a name="BestPractices"></a>グラフにデータを表示する際のベストプラクティス  
 グラフが最も効果を発揮するのは、表示される要素の数によって、基になっている情報のイメージが明確に表現できる場合です。 散布図など一部のグラフはデータ ポイントの数が多い場合に効果的ですが、円グラフなどの他のグラフはデータ ポイントが少ない場合に効果的です。 データセット内の値とその情報の表示方法に基づいて、慎重にグラフの種類を選択してください。 詳細については、「 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md)」を参照してください。  
  
 グラフ上のデータを整理するには、いくつかの方法があります。  
  
-   円グラフを使用している場合は、複数の小さいスライスを "その他" という 1 つのスライスにまとめます。 こうすると、円グラフのスライスの数が少なくなります。 詳細については、「 [円グラフの小さいスライスをまとめる (レポート ビルダーおよび SSRS)](collect-small-slices-on-a-pie-chart-report-builder-and-ssrs.md)」(グラフ (レポート ビルダーおよび SSRS)) を参照してください。  
  
-   データ ポイントの数が多い場合は、データ ポイント ラベルを使用しないでください。 データ ポイント ラベルが最も効果的なのは、グラフ上のポイントが少数の場合です。  
  
-   不要なデータや無関係なデータをフィルター処理します。 これにより、グラフに表示する主要なデータを強調することができます。 グラフ内のデータ ポイントをフィルター処理するには、カテゴリ グループまたは系列グループに対するフィルターを設定します。 既定では、組み込み関数 Sum を使って、同じグループに属する値が系列内の個々のデータ ポイントとして集計されます。 系列の集計関数を変更する場合は、フィルター式の集計関数を変更する必要もあります。 詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。  
  
-   テーブルやマトリックスのテンプレートに比率データを表示する場合は、横棒グラフではなく線形ゲージの使用を検討してください。 セル内にある 1 つの値を表示するには、ゲージの方が適しています。 詳細については、「 [入れ子になったデータ領域 &#40;レポート ビルダーおよび SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)」を参照してください。  
  
  
  
##  <a name="aggregating-values-from-a-data-field-on-the-chart"></a><a name="AggregateValues"></a>グラフ上のデータフィールドから値を集計する  
 既定では、フィールドがグラフの [値] 領域に追加されると、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によってフィールドの集計が計算されます。 フィールドを特定の領域にドロップせずにグラフ上にドラッグすると、グラフでは、フィールドのデータ型に基づいて、このフィールドがカテゴリ軸 (x 軸) または値軸 (y 軸) のいずれに属するかが判断されます。 [値] 領域にドロップされた数値フィールドは、SUM 関数を使用して集計されます。 [値] 領域で値フィールドのデータ型が String の場合、フィールドに数値が存在する場合でも、グラフに数値は表示されず、COUNT 関数が表示されます。 この動作を回避するには、フィールドに、書式設定された数値を格納した文字列ではなく、数値データ型を設定してください。 Visual Basic の式を使用して文字列値を数値データ型に変換するには、`CDbl` 定数または `CInt` 定数を使用します。 たとえば、次の複合式を使用すると、文字列として書式設定された数値を格納する `MyField` という名前のフィールドを変換できます。  
  
 `=Sum(CDbl(Fields!MyField.Value))`  
  
 集計式の詳細については、「[集計関数リファレンス &#40;レポート ビルダーおよび SSRS&#41;](report-builder-functions-aggregate-functions-reference.md)」を参照してください。  
  
  
  
##  <a name="in-this-section"></a><a name="InThisSection"></a> トピックの内容  
 [レポートへのグラフの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-chart-to-a-report-report-builder-and-ssrs.md)  
 レポートにグラフを追加する最初の手順について説明します。  
  
 [グラフの種類 &#40;レポート ビルダーおよび SSRS&#41;](chart-types-report-builder-and-ssrs.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]で使用できるすべてのグラフの種類とサブタイプについて説明します。また、さまざまな種類のグラフを使用する際の注意事項およびベスト プラクティスについても説明します。  
  
 [グラフの書式設定 &#40;レポート ビルダーおよび SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)  
 全体の見た目を向上させる書式設定を使用し、グラフの主要なデータ ポイントを強調表示します。  
  
 [グラフ内の空のデータ ポイントおよび NULL データ ポイント (レポート ビルダーおよび SSRS)](charts-report-builder-and-ssrs.md)  
 空の値または NULL 値を持つフィールドに基づくグラフを操作する際の考慮事項について説明します。  
  
 [グラフ上で複数のデータ範囲を持つ系列の表示 &#40;レポート ビルダーおよび SSRS&#41;](displaying-a-series-with-multiple-data-ranges-on-a-chart.md)  
 複数範囲のデータを含む系列にスケール区切りを追加する方法について説明します。  
  
 [グラフ上の複数の系列 &#40;レポート ビルダーおよび SSRS&#41;](multiple-series-on-a-chart-report-builder-and-ssrs.md)  
 同じグラフで複数の系列を表示するいくつかの方法について説明します。これには、グラフの種類の組み合わせ、セカンダリ軸の使用、異なるグラフの種類の指定、および複数のグラフ領域の使用などが含まれます。  
  
 [同じデータセットへの複数のデータ領域のリンク &#40;レポート ビルダーおよび SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md)  
 同じレポート データセットのデータをさまざまな形式で表示することができます。  
  
 [グラフでのグループの追加または削除 &#40;レポート ビルダーおよび SSRS&#41;](add-or-delete-a-group-in-a-chart-report-builder-and-ssrs.md)  
 グループや入れ子構造のグループをグラフに追加する方法について説明します。  
  
 [グラフへの移動平均の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-moving-average-to-a-chart-report-builder-and-ssrs.md)  
 系列内のデータの平均を計算する移動平均式の使用方法について説明します。  
  
 [グラフのトラブルシューティング &#40;レポート ビルダーおよび SSRS&#41;](troubleshoot-charts-report-builder-and-ssrs.md)  
 グラフを操作する際に役立つヒントについて説明します。  
  
## <a name="see-also"></a>参照  
 [画像、テキストボックス、四角形、および行 &#40;レポートビルダーと SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md)   
 [対話的な並べ替え、ドキュメントマップ、およびリンク &#40;レポートビルダーと SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [入れ子になったデータ領域 &#40;レポートビルダーと SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへの縦棒グラフの追加 &#40;レポートビルダー&#41;](../tutorial-add-a-column-chart-to-your-report-report-builder.md)   
 [チュートリアル: レポート &#40;レポートビルダーに円グラフを追加&#41;](../tutorial-add-a-pie-chart-to-your-report-report-builder.md)   
 [チュートリアル: レポートへの横棒グラフの追加 &#40;レポート ビルダー&#41;](../tutorial-add-a-bar-chart-to-your-report-report-builder.md)  
  
  
