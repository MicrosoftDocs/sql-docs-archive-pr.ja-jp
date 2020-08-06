---
title: 予測の作成 (基本的なデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a8410ed2-bb98-4d51-a9eb-b239be1201c2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 456aec6c6b9d0d1a5d0ee1d9949507a37577130c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711205"
---
# <a name="creating-predictions-basic-data-mining-tutorial"></a>予測の作成 (基本的なデータ マイニング チュートリアル)
  マイニングモデルの精度をテストし、結果に満足したと判断したら、データマイニングデザイナーの [**マイニングモデル予測**] タブにある予測クエリビルダーを使用して予測を生成できます。  
  
 予測クエリ ビルダーには 3 つのビューがあります。 **デザイン**ビューと**クエリ**ビューでは、クエリをビルドして確認できます。 その後、クエリを実行し、**結果ビューで**結果を表示できます。  
  
 すべての予測クエリは、DMX を使用します。DMX とは、データ マイニング拡張機能 (Data Mining Extensions、DMX) 言語の略称です。 DMX の構文は T-SQL と似ていますが、データ マイニング オブジェクトに対するクエリに使用されます。 DMX 構文は複雑ではありませんが、このようなクエリビルダーを使用する場合や、 [Office 用の SQL Server データマイニングアドイン](../../2014/analysis-services/data-mining/sql-server-data-mining-add-ins-for-office.md)を使用する場合は、入力と式を簡単に選択できるようになるため、基本を理解することを強くお勧めします。  
  
## <a name="creating-the-query"></a>クエリの作成  
 予測クエリを作成するには、まず、マイニング モデルと入力テーブルを選択します。  
  
#### <a name="to-select-a-model-and-input-table"></a>モデルと入力テーブルを選択するには  
  
1.  データマイニングデザイナーの [**マイニングモデル予測**] タブで、[**マイニングモデル**] ボックスの [**モデルの選択**] をクリックします。  
  
2.  **[マイニングモデルの選択**] ダイアログボックスで、ツリー内を移動先の**メーリング**構造に移動し、構造を展開して、を選択し、[OK] を `TM_Decision_Tree` クリックします。 **OK**  
  
3.  [**入力テーブルの選択**] ボックスで、[**ケーステーブルの選択**] をクリックします。  
  
4.  **[テーブルの選択**] ダイアログボックスの [**データソース**] ボックスの一覧で、データソースビューを選択し [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] ます。  
  
5.  [**テーブル名またはビュー名**] で、[ **ProspectiveBuyer (dbo)** ] テーブルを選択し、[ **OK]** をクリックします。  
  
     テーブルは、 `ProspectiveBuyer` **Vtargetmail**のケーステーブルによく似ています。  
  
## <a name="mapping-the-columns"></a>列のマッピング  
 入力テーブルを選択すると、列名に基づいてマイニング モデルと入力テーブルの間に既定のマッピングが作成されます。 構造の列と外部データの列は 1 つ以上一致する必要があります。  
  
> [!IMPORTANT]  
>  モデルの精度を判断するために使用するデータには、予測可能列にマッピングできる列が含まれている必要があります。 そのような列が存在しない場合は、空の値で列を作成できますが、データ型が予測可能列と同じである必要があります。  
  
#### <a name="to-map-the-inputs-to-the-model"></a>入力をモデルにマップするには  
  
1.  [**マイニングモデル**] ウィンドウに接続している行を右クリックし、[**入力テーブルの選択**] ウィンドウで [**接続の変更**] を選択します。  
  
     すべての列をマップするわけではありません。 複数の**テーブル列**のマッピングを追加します。 一致する列を増やすため、現在の日付の列に基づいて新しい生年月日の列も生成します。  
  
2.  [**テーブル列**] で、 `Bike Buyer` セルをクリックし、ドロップダウンから [ProspectiveBuyer] を選択します。  
  
     これにより、予測可能列 [Bike Buyer] が入力テーブルの列にマップされます。  
  
3.  **[OK]** をクリックします。  
  
4.  **ソリューションエクスプローラー**で、**対象メーリング**データソースビューを右クリックし、[**ビューデザイナー**] を選択します。  
  
5.  ProspectiveBuyer テーブルを右クリックし、[**新しい名前付き計算**] を選択します。  
  
6.  [**名前付き計算の作成**] ダイアログボックスの [**列名**] に「」と入力 `calcAge` します。  
  
7.  [**説明**] に、「**誕生日に基づいて年齢を計算**する」と入力します。  
  
8.  [**式**] ボックスに「 `DATEDIFF(YYYY,[BirthDate],getdate())` 」と入力し、[ **OK]** をクリックします。  
  
     入力テーブルには、モデル内の列に対応する**age**列がないため、この式を使用して、入力テーブルの [誕生日] 列から顧客の年齢を計算できます。 **Age**は、自転車の購入を予測するために最も影響力の高い列として識別されたため、モデルと入力テーブルの両方に存在する必要があります。  
  
9. データマイニングデザイナーで、[**マイニングモデル予測**] タブを選択し、[**接続の変更**] ウィンドウを再び開きます。  
  
10. [**テーブル列**] の下の [ **Age** ] セルをクリックし、ドロップダウンリストから [ProspectiveBuyer] を選択します。  
  
    > [!WARNING]  
    >  一覧に列が表示されない場合は、場合によって、デザイナーに読み込まれたデータ ソース ビューの定義を更新する必要があります。 これを行うには、[**ファイル**] メニューの [**すべてを保存**] をクリックし、デザイナーでプロジェクトを閉じてから開き直します。  
  
11. **[OK]** をクリックします。  
  
## <a name="designing-the-prediction-query"></a>予測クエリのデザイン  
  
1.  [**マイニングモデル予測**] タブのツールバーにある最初のボタンは、[**デザインビューに切り替え]/[結果ビューに切り替え]/[クエリビューに切り替え**] ボタンです。 このボタンの下矢印をクリックし、[**デザイン**] を選択します。  
  
2.  [**マイニングモデル予測**] タブのグリッドで、[**基**になる列] の最初の空白行のセルをクリックし、[**予測関数**] を選択します。  
  
3.  **予測関数**の行の [**フィールド]** 列で、を選択し `PredictProbability` ます。  
  
     同じ行の [**別名**] 列に「 **result of Probability**」と入力します。  
  
4.  上の [**マイニングモデル**] ウィンドウで、[自転車購入者] を選択し、[**条件と引数**] セルにドラッグします。  
  
     使用する場合は、[TM_Decision_Tree] を参照してください。[自転車購入者] が [**条件と引数**] セルに表示されます。  
  
     これにより、`PredictProbability` 関数の対象列を指定します。 関数の詳細については、「[データマイニング拡張機能 &#40;DMX&#41; 関数リファレンス](/sql/dmx/data-mining-extensions-dmx-function-reference)」を参照してください。  
  
5.  [**ソース**] 列の次の空白行をクリックし、[マイニングモデルの**TM_Decision_Tree** ] を選択します。  
  
6.  行の `TM_Decision_Tree` [**フィールド**] 列で、を選択し `Bike Buyer` ます。  
  
7.  行の [ `TM_Decision_Tree` **条件と引数**] 列に「」と入力 `=1` します。  
  
8.  [**ソース**] 列の次の空白行をクリックし、[ **ProspectiveBuyer table**] を選択します。  
  
9. 行の [ `ProspectiveBuyer` **フィールド**] 列で、[ **ProspectiveBuyerKey**] を選択します。  
  
     予測クエリに一意識別子が追加され、自転車を購入する可能性が高い顧客とそうでない顧客を特定できるようになります。  
  
10. グリッドに 5 つの行を追加します。 行ごとに、**ソース**として [ **ProspectiveBuyer table** ] を選択し、[**フィールド]** セルに次の列を追加します。  
  
    -   calcAge  
  
    -   LastName  
  
    -   FirstName  
  
    -   AddressLine1  
  
    -   AddressLine2  
  
 最後に、クエリを実行して結果を参照します。  
  
 **予測クエリビルダー**には、次のコントロールも含まれます。  
  
-   チェックボックス**を表示する**  
  
     句をデザイナーから削除せずに、句をクエリから削除することができます。 複雑なクエリを使用しているときに、DMX 構文のコピーとウィンドウへの貼り付けを行わずに構文を保持しようとする場合に役立ちます。  
  
-   **グループ**  
  
     選択した行の先頭に開く (左) かっこを挿入するか、現在の行の末尾に閉じる (右) かっこを挿入します。  
  
-   **AND/OR**  
  
     現在の関数または現在の列の直後に、`AND` 演算子または `OR` 演算子を挿入します。  
  
#### <a name="to-run-the-query-and-view-results"></a>クエリを実行して結果を表示するには  
  
1.  [**マイニングモデル予測**] タブで、[**結果**] ボタンを選択します。  
  
2.  クエリを実行して結果が表示されたら、その結果を確認できます。  
  
     [**マイニングモデル予測**] タブには、自転車購入者である可能性がある潜在顧客の連絡先情報が表示されます。 **結果列の確率**は、予測が正しいかどうかを示します。 これらの結果を使用すると、メールを送信する対象となる潜在顧客を特定できます。  
  
3.  この時点で、結果を保存できます。 この場合、3 つの選択肢があります。  
  
    -   結果内のデータ行を右クリックし、[**コピー** ] をクリックして、その値 (および列見出し) だけをクリップボードに保存します。  
  
    -   結果内の任意の行を右クリックし、[**すべてコピー** ] を選択して、結果セット全体 (列見出しを含む) をクリップボードにコピーします。  
  
    -   [**クエリ結果の保存**] をクリックして、次のようにして結果を直接データベースに保存します。  
  
        1.  [**データマイニングのクエリ結果の保存**] ダイアログボックスで、データソースを選択するか、新しいデータソースを定義します。  
  
        2.  クエリの結果が保存されるテーブルの名前を入力します。  
  
        3.  テーブルを作成して既存のデータソースビューに追加するには、[ **DSV に追加**] オプションを使用します。 これは、モデルのすべての関連テーブル (トレーニングデータ、予測ソースデータ、クエリ結果など) を同じデータソースビューに保持する場合に便利です。  
  
        4.  [**存在する場合は上書き**する] オプションを使用して、既存のテーブルを最新の結果に更新します。  
  
             予測クエリに列を追加した場合、予測クエリで列の名前またはデータ型を変更した場合、または保存先テーブルで ALTER ステートメントを実行した場合、このオプションを使用してテーブルを上書きする必要があります。  
  
             また、複数の列に同じ名前 (既定の列名の**式**など) がある場合は、名前が重複している列の別名を作成する必要があります。そうしないと、デザイナーが SQL Server に結果を保存しようとしたときにエラーが発生します。 SQL Server では、複数の列に同じ名前が含まれることが許可されないためです。  
  
             詳細については、「[[データマイニングクエリ結果の保存] ダイアログボックス &#40;マイニングモデル予測ビュー&#41;](../../2014/analysis-services/save-data-mining-query-result-dialog-box-mining-model-prediction-view.md)」を参照してください。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [構造データでのドリルスルーの使用 &#40;基本的なデータマイニングチュートリアル&#41;](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [予測クエリ ビルダーを使用した予測クエリの作成](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  