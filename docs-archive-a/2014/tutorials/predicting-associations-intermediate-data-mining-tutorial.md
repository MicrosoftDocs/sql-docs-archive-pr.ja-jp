---
title: アソシエーションの予測 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631414"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a>アソシエーションの予測 (中級者向けデータ マイニング チュートリアル)
  モデルの処理が完了したら、モデルに格納されているアソシエーションに関する情報を使用して予測を作成できます。 このレッスンの最後の作業では、作成したアソシエーション モデルに対して予測クエリを作成する方法について学習します。 このレッスンは、予測クエリ ビルダーの使用方法について理解していることを前提に、アソシエーション モデルに対する予測クエリの作成方法について説明します。 予測クエリビルダーの使用方法の詳細については、「[データマイニングクエリインターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)」を参照してください。  
  
## <a name="creating-a-singleton-prediction-query"></a>単一予測クエリの作成  
 アソシエーション モデルに対する予測クエリは、次のようなときに、非常に役に立ちます。  
  
-   以前の購入または関連する購入に基づいて、製品を顧客に勧める。  
  
-   関連するイベントを検索する。  
  
-   取引のセット内の、またはそれらにまたがる関係を識別する。  
  
 予測クエリを作成するには、まず使用するアソシエーション モデルを選択し、次に入力データを指定します。 値の一覧などの外部データ ソースから入力を得ることも、単一クエリを作成して値を指定することもできます。  
  
 このシナリオでは、まずいくつかの単一予測クエリを作成して、予測がどのように機能するかについて確認します。 次に、顧客の現在の購入状況に基づいて提案を行う場合に使用するバッチ予測用のクエリを作成します。  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a>アソシエーション モデルに対する予測クエリを作成するには  
  
1.  データマイニングデザイナーの [**マイニングモデル予測**] タブをクリックします。  
  
2.  [**マイニングモデル**] ペインで、[**モデルの選択**] をクリックします。 (適切なモデルが既に選択されている場合は、この手順と次の手順をスキップできます)。  
  
3.  **[マイニングモデルの選択**] ダイアログボックスで、マイニング構造の**関連付け**を表すノードを展開し、モデルの**関連付け**を選択します。 **[OK]** をクリックします。  
  
     ここでは、入力ペインは無視します。  
  
4.  グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。** [**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。  
  
     また、 **predict**関数を使用してアソシエーションを予測することもできます。 この場合、テーブル列を引数として受け取る、 **Predict**関数のバージョンを選択してください。  
  
5.  [**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。  
  
     テーブル名と列名をドラッグ アンド ドロップすると、構文エラーを発生させずに複雑なステートメントを作成できます。 ただし、これにより、セルの現在の内容が置き換えられます。これには、関数の他の省略可能な引数が含まれ `PredictAssociation` ます。 その他の引数を表示するには、関数の 2 番目のインスタンスを参照用として一時的にグリッドに追加します。  
  
6.  [**条件と引数**] ボックスをクリックし、テーブル名の後に次のテキストを入力します。`,3`  
  
     [**条件と引数**] ボックスの完全なテキストは次のようになります。  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。  
  
 期待される結果には、見出し**式**を含む1つの列が含まれます。 [**式**] 列には、1つの列と次の3つの行を含む入れ子になったテーブルが含まれます。 入力値を指定していないため、これらの予測は、モデル全体で最も可能性の高い製品のアソシエーションを表します。  
  
|モデル|  
|-----------|  
|Women's Mountain Shorts|  
|Water Bottle|  
|Touring-3000|  
  
 次に、[**単一クエリ入力**] ペインを使用してクエリへの入力として製品を指定し、そのアイテムに関連付けられている可能性が最も高い製品を表示します。  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する単一予測クエリを作成するには  
  
1.  予測クエリビルダーの隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
2.  [**マイニングモデル**] メニューの [**単一クエリ**] をクリックします。  
  
3.  [**マイニングモデル**] ダイアログボックスで、**アソシエーション**モデルを選択します。  
  
4.  グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。** [**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。  
  
5.  [**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。 `,3`前の手順と同様に、入れ子になったテーブル名の後に「」と入力します。  
  
6.  [**単一クエリ入力**] ダイアログボックスで、[ **vassoc Seq 行項目**] の横にある [**値**] ボックスをクリックし、[ **..** .] ボタンをクリックします。  
  
7.  [**入れ子になったテーブルの入力**] ダイアログボックスの [ `Touring Tire` **キー列**] ペインでを選択し、[**追加**] をクリックします。  
  
8.  [**結果**] ボタンをクリックします。  
  
 Touring Tire との関連が最も高い製品の予測が結果として表示されます。  
  
|モデル|  
|-----------|  
|Touring Tire Tube|  
|Sport-100|  
|Water Bottle|  
  
 ただし、Touring Tire Tube が Touring Tire と一緒に購入されることが多いのは、モデルの調査から既にわかっています。それよりも関心があるのは、これらの製品を同時に購入した顧客にどの製品を提案できるかということです。 買い物かごに入っている 2 つの商品を基に関連する製品を予測するように、クエリを変更します。 また、予測された製品ごとに確率を追加するようにクエリを変更します。  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a>単一予測クエリに入力と確率を追加するには  
  
1.  予測クエリビルダーの隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
2.  [**単一クエリ入力**] ダイアログボックスで、[ **vassoc Seq 行項目**] の横にある [**値**] ボックスをクリックし、[ **..** .] ボタンをクリックします。  
  
3.  [**キー列**] ペインで、[] を選択し、 `Touring Tire` [**追加**] をクリックします。  
  
4.  グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。** [**フィールド**] の下のセルで、を選択し `PredictAssociation` ます。  
  
5.  [**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `vAssocSeqLineItems` 関数の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。 `,3`前の手順と同様に、入れ子になったテーブル名の後に「」と入力します。  
  
6.  [**入れ子になったテーブルの入力**] ダイアログボックスの [ `Touring Tire Tube` **キー列**] ペインでを選択し、[**追加**] をクリックします。  
  
7.  グリッドで、関数の行の `PredictAssociation` [**条件と引数**] ボックスをクリックし、引数を変更して引数を追加し INCLUDE_STATISTICS します。  
  
     [**条件と引数**] ボックスの完全なテキストは次のようになります。  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  [**結果**] ボタンをクリックします。  
  
 入れ子になったテーブル内の結果が変更され、予測がサポートおよび確率と共に表示されます。 これらの値を解釈する方法の詳細については、「 [&#40;Analysis Services データマイニング&#41;のアソシエーションモデルのマイニングモデルコンテンツ](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)」を参照してください。  
  
|モデル|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291...|0.252...|  
|Water Bottle|2866|0.192...|0.175...|  
|Patch Kit|2113|0.142...|0.132|  
  
## <a name="working-with-results"></a>結果の操作  
 結果に多数の入れ子になったテーブルが含まれている場合は、結果をフラット化して見やすくすることができます。 そのためには、クエリを手動で変更し、`FLATTENED` キーワードを追加します。  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>予測クエリで入れ子になった行セットをフラット化するには  
  
1.  予測クエリビルダーの隅にある [ **SQL** ] ボタンをクリックします。  
  
     グリッドが開いたペインに変わり、予測クエリ ビルダーで作成された DMX ステートメントを表示および変更できるようになります。  
  
2.  `SELECT` キーワードの後に、「`FLATTENED`」と入力します。  
  
     クエリの全テキストは次のようになります。  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。  
  
 クエリを手動で編集した後に [デザイン] ビューに戻ると、変更が失われることに注意してください。 クエリを保存する場合は、手動で作成した DMX ステートメントをテキスト ファイルにコピーします。 [デザイン] ビューに戻ると、クエリが [デザイン] ビューで有効であった最後のバージョンに戻ります。  
  
## <a name="creating-multiple-predictions"></a>複数の予測の作成  
 過去の購入記録を基に、各顧客に対して最も精度の高い予測を作成するとします。 予測クエリには、顧客 ID と最近購入した製品が記録されているテーブルなどの外部データを入力として使用できます。 その場合は、データ テーブルが Analysis Services データ ソース ビューとして既に定義されていることが条件となります。さらにモデルで使用されているものと同様のケース テーブルと入れ子になったテーブルが入力データに含まれている必要があります。 テーブル名が同じである必要はありませんが、構造は類似している必要があります。 このチュートリアルでは、モデルのトレーニングが行われた元のテーブルを使用します。  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a>予測クエリの入力方法を変更するには  
  
1.  [**マイニングモデル**] メニューで、[**単一クエリ**] をもう一度選択してチェックマークをオフにします。  
  
2.  単一クエリが失われることを警告するエラー メッセージが表示されます。 **[はい]** をクリックします。  
  
     入力ダイアログボックスの名前が **[入力テーブルの選択**] に変わります。  
  
 顧客 ID と製品一覧を入力として提供する予測クエリを作成することが目的であるため、ケース テーブルとして顧客テーブルを、入れ子になったテーブルとして購入記録テーブルをそれぞれ追加します。 その後に、提案を作成するための予測関数を追加します。  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する予測クエリを作成するには  
  
1.  [マイニング モデル] ペインで、[Association Filtered] モデルを選択します。  
  
2.  [**入力テーブルの選択**] ダイアログボックスで、[**ケーステーブルの選択**] をクリックします。  
  
3.  **[テーブルの選択**] ダイアログボックスの [**データソース**] で、[AdventureWorksDW2008] を選択します。 [**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqOrders] を選択し、[ **OK**] をクリックします。  
  
     テーブル vAssocSeqOrders がペインに追加されます。  
  
4.  [**入力テーブルの選択**] ダイアログボックスで、[**入れ子になったテーブルの選択**] をクリックします。  
  
5.  **[テーブルの選択**] ダイアログボックスの [**データソース**] で、[AdventureWorksDW2008] を選択します。 [**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqLineItems] を選択し、[ **OK**] をクリックします。  
  
     テーブル vAssocSeqLineItems がペインに追加されます。  
  
6.  [**入れ子になった結合の指定**] ダイアログボックスで、ケーステーブルの [ordernumber] フィールドをドラッグし、入れ子になったテーブルの [ordernumber] フィールドにドロップします。  
  
     [**リレーションシップの追加**] をクリックして、一覧から列を選択してリレーションシップを作成することもできます。  
  
7.  [**リレーションシップの指定**] ダイアログボックスで、[ordernumber] フィールドが正しくマップされていることを確認し、[ **OK**] をクリックします。  
  
8.  [ **OK** ] をクリックして [**入れ子になった結合の指定**] ダイアログボックスを閉じます。  
  
     ケース テーブルと入れ子になったテーブルがデザイン ペインで更新され、外部データの列とモデル内の列を結ぶ結合が表示されます。 リレーションシップが正しくない場合は、結合線を右クリックし、[**接続の変更**] を選択して列マッピングを編集するか、結合線を右クリックして [**削除**] を選択すると、リレーションシップが完全に削除されます。  
  
9. グリッドに新しい行を追加します。 [**ソース**] で、[ **vAssocSeqOrders table**] を選択します。 [**フィールド**] で [顧客キー] を選択します。  
  
10. グリッドに新しい行を追加します。 [**ソース**] で、[ **vAssocSeqOrders table**] を選択します。 [**フィールド**] で [Region] を選択します。  
  
11. グリッドに新しい行を追加します。 [**ソース**] で [**予測関数**] を選択し、[**フィールド**] でを選択し `PredictAssociation` ます。  
  
12. VAssocSeqLineItems を行の [**条件と引数**] ボックスにドラッグし `PredictAssociation` ます。 [**条件と引数**] ボックスの末尾をクリックし、次のテキストを入力します。`INCLUDE_STATISTICS,3`  
  
     [**条件と引数**] ボックスの完全なテキストは次のようになります。`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
13. [**結果**] ボタンをクリックすると、各顧客の予測が表示されます。  
  
 同様の予測クエリを複数のモデルに対して作成し、フィルター処理によって予測結果が変わるかどうかを確認してみてください。 予測およびその他の種類のクエリの作成の詳細については、「[アソシエーションモデルのクエリ例](../../2014/analysis-services/data-mining/association-model-query-examples.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [アソシエーションモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)   
 [DMX&#41;&#40;PredictAssociation](/sql/dmx/predictassociation-dmx)   
 [予測クエリ ビルダーを使用した予測クエリの作成](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  