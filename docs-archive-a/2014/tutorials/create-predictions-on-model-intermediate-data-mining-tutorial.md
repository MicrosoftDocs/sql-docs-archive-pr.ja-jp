---
title: シーケンスクラスターモデルでの予測の作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 2402c28a564502df9ce12c5e3f97b9d19590cfea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630725"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>シーケンス クラスター モデルでの予測の作成 (中級者向けデータ マイニング チュートリアル)
  ビューアーでシーケンスクラスターモデルを参照して理解した後、データマイニングデザイナーの [**マイニングモデル予測**] タブで予測クエリビルダーを使用して、予測クエリを作成できます。 予測を作成するには、まずシーケンス クラスター モデルを選択し、次に入力データを選択します。 入力については、外部データ ソースを使用するか、単一クエリを作成してダイアログ ボックスで値を指定することができます。  
  
 このレッスンでは、予測クエリ ビルダーの使用方法について理解していることを前提に、シーケンス クラスター モデルに固有のクエリの作成方法について説明します。 予測クエリビルダーの使用方法に関する一般的な情報については、「データマイニング[クエリインターフェイス](../../2014/analysis-services/data-mining/data-mining-query-tools.md)」、または「基本的なデータマイニングチュートリアル」の「[予測の作成 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)」を参照してください。  
  
## <a name="creating-predictions-on-the-regional-model"></a>地域モデルでの予測の作成  
 このシナリオでは、まずいくつかの単一予測クエリを作成し、予測が地域ごとにどのように異なるかについて確認します。  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>シーケンス クラスター モデルに対する単一クエリを作成するには  
  
1.  データマイニングデザイナーの [**マイニングモデル予測**] タブをクリックします。  
  
2.  [**マイニングモデル**列] メニューの [**単一クエリ**] をクリックします。  
  
     [**マイニングモデル**] ペインと [**単一クエリ入力**] ウィンドウが表示されます。  
  
3.  [**マイニングモデル**] ペインで、[**モデルの選択**] をクリックします。 (既にシーケンス クラスター モデルが選択されている場合は、この手順を省略します)。  
  
     **[マイニングモデルの選択**] ダイアログボックスが表示されます。  
  
4.  [マイニング構造]**シーケンスクラスター**を表すノードを [リージョン] で展開し、[**リージョンを含むモデルシーケンスクラスター**] を選択します。 **[OK]** をクリックします。 ここでは、入力ペインは無視します。入力は予測関数の設定後に指定します。  
  
5.  グリッドで、[**ソース**] の下の空のセルをクリックし、[予測関数] を選択し**ます。** [**フィールド**] の下のセルで、[ **PredictSequence**] を選択します。  
  
    > [!NOTE]  
    >  また、 **Predict**関数を使用することもできます。 この場合、テーブル列を引数として受け取る**Predict**関数のバージョンを選択してください。  
  
6.  [**マイニングモデル**] ペインで、入れ子になったテーブルを選択し、グリッド内の `v Assoc Seq Line Items` **PredictSequence**関数の [**条件と引数**] ボックスにドラッグします。  
  
     テーブル名と列名をドラッグアンドドロップすると、構文エラーを発生させずに複雑なステートメントを作成できます。 ただし、セルの現在の内容は置き換えられます。これには、 **PredictSequence**関数のその他の省略可能な引数が含まれます。 その他の引数を表示するには、関数の 2 番目のインスタンスを参照用として一時的にグリッドに追加します。  
  
7.  予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。  
  
 期待される結果には、見出し**式**を含む1つの列が含まれます。 **式**列には、次の3つの列を含む入れ子になったテーブルが含まれています。  
  
|$SEQUENCE|Line Number|モデル|  
|---------------|-----------------|-----------|  
|1||Mountain-200|  
  
 この結果からわかることは何でしょうか。 入力を指定していないことに注意してください。 予測はケースの母集団全体に対して作成され、Analysis Services からは最も可能性の高い全体的な予測が返されます。  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>単一予測クエリへの入力の追加  
 この時点では、まだ入力を指定していません。 次のタスクでは、[**単一クエリ入力**] ペインを使用してクエリへの入力を指定します。 まず、予測されたシーケンスがすべての地域で同じかどうかを判断するために、地域シーケンス クラスター モデルへの入力として [Region] を使用します。 次に、各予測の確率を追加するようにクエリを変更し、結果をフラット化して見やすくする方法について説明します。  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>特定の顧客グループの予測を生成するには  
  
1.  予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
2.  [**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリック `Region` し、[**ヨーロッパ**] を選択します。  
  
3.  [**結果**] ボタンをクリックすると、ヨーロッパの顧客の予測が表示されます。  
  
4.  予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
5.  [**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリック `Region` し、[**北米**] を選択します。  
  
6.  北米の顧客の予測を表示するには、[**結果**] ボタンをクリックします。  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>カスタム式を使用した確率の追加  
 確率は予測の属性であり、入れ子になったテーブルとして出力されるので、各予測の確率を出力するのはやや複雑です。 データ マイニング拡張機能 (DMX) に慣れている場合は、入れ子になったテーブルに対する下位選択ステートメントを追加するようにクエリを簡単に変更できます。 また、予測クエリ ビルダーでカスタム式を追加して下位選択ステートメントを作成することもできます。  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>カスタム式を使用して予測されたシーケンスの確率を出力するには  
  
1.  予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
2.  グリッドの [**ソース**] で、新しい行をクリックし、[**カスタム式**] を選択します。  
  
3.  [**フィールド**] の下のボックスは空白のままにします。  
  
4.  [**別名**] に「」と入力 `t` します。  
  
5.  [**条件と引数**] ボックスに、次のコード例に示すように、完全なサブ選択ステートメントを入力します。 必ず開始かっこと終了かっこも入力してください。  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  [**結果**] ボタンをクリックすると、ヨーロッパの顧客の予測が表示されます。  
  
 結果に、2 つの入れ子になったテーブルが含まれるようになります。一方のテーブルには予測、もう一方のテーブルには予測の確率が示されます。 クエリが機能しない場合は、クエリ デザイン ビューに切り替えて、次のようなクエリ ステートメント全体を確認できます。  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>結果の操作  
 結果に多数の入れ子になったテーブルが含まれている場合は、結果をフラット化して見やすくすることができます。 そのためには、クエリを手動で変更し、`FLATTENED` キーワードを追加します。  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>予測クエリで入れ子になった行セットをフラット化するには  
  
1.  予測クエリビルダーの隅にある [**クエリ**] ボタンをクリックします。  
  
     グリッドが開いたペインに変わり、予測クエリ ビルダーで作成された DMX ステートメントを表示および変更できるようになります。  
  
2.  `SELECT` キーワードの後に、「`FLATTENED`」と入力します。  
  
     クエリの完全なテキストは、次のようになります。  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  予測クエリビルダーの上隅にある [**結果**] ボタンをクリックします。  
  
 クエリを手動で編集した後、デザイン ビューに戻ると変更は失われます。 ただし、手動で作成した DMX ステートメントをテキスト ファイルに保存してからデザイン ビューに戻ることはできます。 この場合、クエリはデザイン ビューで有効であった最後のバージョンに戻ります。  
  
## <a name="creating-predictions-on-the-related-model"></a>関連モデルでの予測の作成  
 ここまでの例では、モデルで地域間の違いが見られたかどうかを確認するために、ケース テーブル列 [地域] を単一予測クエリへの入力として使用しました。 ただし、モデルの調査後に、その違いは地域ごとに製品の提案をカスタマイズするほど顕著なものではないと判断しました。 実際に予測する必要があるのは顧客が選択するアイテムです。 したがって、次のクエリでは、地域を含まないシーケンス クラスター モデルを使用して、すべての顧客に対する提案を生成します。  
  
### <a name="using-nested-table-columns-as-input"></a>入力としての入れ子になったテーブル列の使用  
 まず、単一のアイテムを入力として受け取り、次に選択される可能性が高いアイテムを返す単一予測クエリを作成します。 このような予測を得るには、入力値として入れ子になったテーブル列を使用する必要があります。 これは、予測する属性 "モデル" が入れ子になったテーブルの一部であるためです。 Analysis Services には、入れ子になったテーブルの属性に対する予測クエリを簡単に作成できるように、[**入れ子になったテーブルの入力**] ダイアログボックスが用意されています。予測クエリビルダーを使用します。  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>入れ子になったテーブルを予測への入力として使用するには  
  
1.  予測クエリビルダーの左上隅にある [**デザイン**] ボタンをクリックして、クエリ作成グリッドに戻ります。  
  
2.  [**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリックし、空の行を選択して、 `Region` このフィールドの入力をクリアします。  
  
3.  [**単一クエリ入力**] ダイアログボックスで、の [**値**] ボックスをクリックし、[... `vAssocSeqLineItems` ] ボタンをクリックします。  
  
4.  [**入れ子になったテーブルの入力**] ダイアログボックスで、[**追加**] をクリックします。  
  
5.  新しい行で、の下のボックスをクリックし、 `Model` 一覧から [ツーリング Tire] を選択します。 **[OK]** をクリックします。  
  
6.  [**結果**] ボタンをクリックすると、予測が表示されます。  
  
 最初のアイテムとして Touring Tire を選択したすべての顧客に、次のアイテムとして以下のものがモデルによって提案されます。 モデルの調査によって、顧客が Touring Tire 製品と Touring Tire Tube 製品を一緒に購入することが多いとわかっているので、この提案は適切です。  
  
|$SEQUENCE|Line Number|モデル|  
|---------------|-----------------|-----------|  
|1||Touring Tire Tube|  
|2||Sport-100|  
|3||Long-Sleeve Logo Jersey|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する一括予測クエリの作成  
 提案に使用できる予測がモデルによって作成されることを確認したので、次は外部データ ソースにマップされる予測クエリを作成します。 そのデータ ソースは、現在の製品を表す値を提供します。 顧客 ID と製品一覧を入力として提供する予測クエリを作成することが目的であるため、ケース テーブルとして顧客テーブルを、入れ子になったテーブルとして購入記録テーブルをそれぞれ追加します。 その後、提案を作成したときと同様に予測関数を追加します。  
  
 この手順は、レッスン 3 でマーケット バスケット シナリオ用の予測を作成したときと同じ手順です。ただし、シーケンス クラスター モデルの予測では、入力として注文も必要になります。  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>入れ子になったテーブルの入力を使用する予測クエリを作成するには  
  
1.  [**マイニングモデル**] ペインで、シーケンスクラスターモデルを選択します (まだ選択されていない場合)。  
  
2.  [**入力テーブルの選択**] ダイアログボックスで、[**ケーステーブルの選択**] をクリックします。  
  
3.  **[テーブルの選択**] ダイアログボックスの [データソース] で、[注文] を選択します。 [**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqOrders] を選択し、[ **OK**] をクリックします。  
  
4.  [**入力テーブルの選択**] ダイアログボックスで、[**入れ子になったテーブルの選択**] をクリックします。  
  
5.  **[テーブルの選択**] ダイアログボックスの [**データソース**] で、[注文] を選択します。 [**テーブル名またはビュー名**] ボックスの一覧で [vAssocSeqLineItems] を選択し、[ **OK**] をクリックします。  
  
     Analysis Services でリレーションシップの検出が試行され、データ型が一致して列名が類似している場合は、リレーションシップが自動的に作成されます。 作成したリレーションシップが正しくない場合は、結合線を右クリックし、[**接続の変更**] を選択して列マッピングを編集するか、結合線を右クリックして [**削除**] を選択すると、リレーションシップが完全に削除されます。 この場合、テーブルがデータ ソース ビューで既に結合されているため、これらのリレーションシップはデザイン ペインに自動的に追加されます。  
  
6.  グリッドに新しい行を追加します。 [**ソース**] で [vAssocSeqOrders] を選択し、[**フィールド**] で [顧客キー] を選択します。  
  
7.  グリッドに新しい行を追加します。 [**ソース**] で [**予測関数**] を選択し、[**フィールド**] で [ **PredictSequence**] を選択します。  
  
8.  VAssocSeqLineItems を [**条件と引数**] ボックスにドラッグします。 [**条件と引数**] ボックスの末尾をクリックし、次の引数を入力します `2` 。  
  
     [**条件と引数**] ボックスの完全なテキストは次のようになります。`[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. [**結果**] ボタンをクリックすると、各顧客の予測が表示されます。  
  
 これで、シーケンス クラスター モデルのチュートリアルは完了です。  
  
## <a name="next-steps"></a>次の手順  
 「中級者向け[データマイニングチュートリアル &#40;Analysis Services データ&#41;マイニングのチュートリアル](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)」に記載されているすべてのセクションを完了している場合は、次の手順として、データマイニング拡張機能 (DMX) ステートメントを使用してモデルを作成し、予測を生成する方法について学習することができます。 詳細については、「 [DMX を使用したデータマイニングモデルの作成とクエリ: チュートリアル &#40;Analysis Services データマイニング&#41;](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)」を参照してください。  
  
 プログラミングの概念について理解している場合は、分析管理オブジェクト (AMO) を使用してデータ マイニング オブジェクトをプログラムで操作することもできます。 詳細については、「 [AMO データ マイニング クラス](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [シーケンスクラスターモデルのクエリ例](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  