---
title: ニューラルネットワークの構造とモデルの作成 (中級者向けデータマイニングチュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- discretization [Analysis Services]
- DISCRETIZED column
- DiscretizationBuckets property
- DiscretizationMethod property
- EQUAL_AREAS method
ms.assetid: 3f16215c-531e-4ecf-a11f-ee7c6a764463
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 91c0210213083868eaab36cf34a05d0b7824a654
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632234"
---
# <a name="creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial"></a>ニューラル ネットワーク構造およびモデルの作成 (中級者向けデータ マイニング チュートリアル)
  データ マイニング モデルを作成するには、まずデータ マイニング ウィザードを使用して、新しいデータ ソース ビューに基づく新しいマイニング構造を作成する必要があります。 ここでは、ウィザードを使用してマイニング構造を作成し、同時に、[!INCLUDE[msCoName](../includes/msconame-md.md)] ニューラル ネットワーク アルゴリズムに基づく関連マイニング モデルを作成します。  
  
 ニューラル ネットワークは高い柔軟性を持ち、さまざまな入力と出力の組み合わせを分析できるため、最良の結果を得るためにはいくつかのデータ処理方法を試す必要があります。 たとえば、特定のビジネス要件を対象とし*て、サービス*品質の数値ターゲットをビン分割またはグループ化する方法をカスタマイズすることができます。 そのためには、数値データを別の方法でグループ化する新しい列をマイニング構造に追加して、その新しい列を使用するモデルを作成します。 その後、それらのマイニング モデルを使用して探索を行います。  
  
 実務上の目的に最も大きい影響を与える要因がニューラル ネットワーク モデルからわかったら、最後に、予測およびスコアリングのための別のモデルを作成します。 そのためには、[!INCLUDE[msCoName](../includes/msconame-md.md)] ロジスティック回帰アルゴリズムを使用します。このアルゴリズムは、ニューラル ネットワーク モデルが基になっていますが、特定の入力に基づくソリューションの検索用に最適化されています。  
  
 **手順**  
  
 [既定のマイニング構造とモデルを作成する](#bkmk_defaul)  
  
 [分離を使用して予測可能列をビン分割する](#bkmk_ColumnCopy)  
  
 [列をコピーして別のモデル用に分離メソッドを変更する](#bkmk_Alias)  
  
 [モデルを比較できるように予測可能列の別名を作成する](#bkmk_Alias2)  
  
 [すべてのモデルの処理](#bkmk_SeedProcess)  
  
## <a name="create-the-default-call-center-structure"></a>既定のコールセンター構造を作成する<a name="bkmk_defaul"></a>  
  
1.  のソリューションエクスプローラーで [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、[**マイニング構造**] を右クリックし、[**新しいマイニング構造**] をクリックします。  
  
2.  **[データ マイニング ウィザードへようこそ]** ページで **[次へ]** をクリックします。  
  
3.  [**定義方法の選択**] ページで、[**既存のリレーショナルデータベースまたはデータウェアハウスから**] が選択されていることを確認し、[**次へ**] をクリックします。  
  
4.  [**データマイニング構造の作成**] ページで、[**マイニングモデルを含むマイニング構造を作成**する] オプションが選択されていることを確認します。  
  
5.  [**使用するデータマイニング技法**を選択してください] のドロップダウンリストをクリックし、[ **Microsoft ニューラルネットワーク**] を選択します。  
  
     ロジスティック回帰モデルはニューラル ネットワークに基づくため、同じ構造を再利用して新しいマイニング モデルを追加できます。  
  
6.  **[次へ]** をクリックします。  
  
     **[データソースビューの選択**] ページが表示されます。  
  
7.  [**使用できるデータソースビュー**] で、[] を選択 `Call Center` し、[**次へ**] をクリックします。  
  
8.  [**テーブルの種類の指定**] ページで、 **FactCallCenter**テーブルの横にある [**ケース**] チェックボックスをオンにします。 **DimDate**に対しては何も選択しないでください。 **[次へ]** をクリックします。  
  
9. [**トレーニングデータの指定**] ページで、[FactCallCenterID] 列の横にある [**キー** ] を選択し**ます。**  
  
10. [] `Predict` および [**入力**] チェックボックスをオンにします。  
  
11. 次の表に示すように、[**キー**]、[**入力**]、および [チェック] チェックボックスをオンにし `Predict` ます。  
  
    |テーブルまたは列|[キー]/[入力]/[予測]|  
    |---------------------|-------------------------|  
    |AutomaticResponses|入力|  
    |AverageTimePerIssue|[入力]/[予測]|  
    |呼び出し|入力|  
    |DateKey|使用しない|  
    |DayOfWeek|入力|  
    |FactCallCenterID|Key|  
    |IssuesRaised|入力|  
    |LevelOneOperators|[入力]/[予測]|  
    |LevelTwoOperators|入力|  
    |Orders|[入力]/[予測]|  
    |ServiceGrade|[入力]/[予測]|  
    |シフト|入力|  
    |TotalOperators|使用しない|  
    |WageType|入力|  
  
     予測可能列が複数選択されていることに注意してください。 ニューラル ネットワーク アルゴリズムには、入力属性と出力属性のあらゆる組み合わせを分析できるという利点があります。 処理時間が指数関数的に増加する可能性があるため、大きなデータセットに対してこれを行う必要はありません。  
  
12. [**列のコンテンツおよびデータ型の指定**] ページで、次の表に示すように、グリッドに列、コンテンツの種類、およびデータ型が含まれていることを確認し、[**次へ**] をクリックします。  
  
    |[列]|コンテンツの種類|データ型|  
    |-------------|------------------|----------------|  
    |AutomaticResponses|継続的|Long|  
    |AverageTimePerIssue|継続的|Long|  
    |呼び出し|継続的|Long|  
    |DayOfWeek|離散|Text|  
    |FactCallCenterID|Key|Long|  
    |IssuesRaised|継続的|Long|  
    |LevelOneOperators|継続的|Long|  
    |LevelTwoOperators|継続的|Long|  
    |Orders|継続的|Long|  
    |ServiceGrade|継続的|Double|  
    |シフト|離散|Text|  
    |WageType|離散|Text|  
  
13. [**テストセットの作成**] ページで、[**テスト用データの割合**] オプションのテキストボックスをオフにします。 **[次へ]** をクリックします。  
  
14. [**ウィザードの完了**] ページで、[**マイニング構造名**] に「」と入力 `Call Center` します。  
  
15. [**マイニングモデル名**] に「 `Call Center Default NN` 」と入力し、[**完了**] をクリックします。  
  
     [**ドリル**スルーを許可する] ボックスは、ニューラルネットワークモデルを使用してデータにドリルスルーすることはできないため、無効になっています。  
  
16. ソリューションエクスプローラーで、先ほど作成したデータマイニング構造の名前を右クリックし、[**処理**] を選択します。  
  
## <a name="use-discretization-to-bin-the-target-column"></a>分離を使用して対象列をビン分割する  
 既定では、予測可能な数値属性を持つニューラル ネットワーク モデルを作成したとき、Microsoft ニューラル ネットワーク アルゴリズムではその属性は連続する数値として扱われます。 たとえば、ServiceGrade 属性は、理論上は 0.00 (すべての電話に応答している状態) ～ 1.00 (すべての発信元が電話を切っている状態) の範囲の数値です。 このデータセットにおいて、数値の分布は次のようになります。  
  
 ![サービス グレード値の分布](../../2014/tutorials/media/skt-service-grade-valuesc.gif "サービス グレード値の分布")  
  
 その結果、モデルを処理したときに、その出力が期待どおりにグループ化されないことがあります。 たとえば、クラスタリングを使用して最適な値グループを特定すると、アルゴリズムによって ServiceGrade の値が 0.0748051948-がのような範囲に分割されます。 この分類は数学的には正確ですが、このような範囲がビジネス ユーザーにとって有意なものではない場合もあります。  
  
 この手順では、結果をわかりやすくするために、数値をグループ化し、数値データ列のコピーを作成します。  
  
### <a name="how-discretization-works"></a>分離のしくみ  
 Analysis Services には、数値データのビン分割や処理のためのさまざまな方法が用意されています。 次の表は、出力属性 ServiceGrade を次の 3 とおりの方法で処理した場合の結果の違いを示しています。  
  
-   連続する数値として処理する。  
  
-   アルゴリズムでクラスタリングを使用して値の最適な分配を特定する。  
  
-   Equal Areas メソッドを使用して数値をビン分割することを指定する。  
  
 既定のモデル (連続)  
  
|値|SUPPORT|  
|-----------|-------------|  
|Missing|0|  
|0.09875|120|  
  
 クラスタリングによるビン分割  
  
|値|SUPPORT|  
|-----------|-------------|  
|\<0.0748051948|34|  
|0.0748051948-が|27|  
|が-0.13297297295|39|  
|0.13297297295 - 0.167499999975|10|  
|>= 0.167499999975|10|  
  
 Equal Areas メソッドによるビン分割  
  
|値|SUPPORT|  
|-----------|-------------|  
|\<0.07|26|  
|0.07 ~ 0.00|22|  
|0.09 ~ 0.11|36|  
|>= 0.12|36|  
  
> [!NOTE]  
>  これらの統計は、すべてのデータが処理された後のモデルのマージナル統計ノードから取得できます。 [最低限の統計] ノードの詳細については、「[ニューラルネットワークモデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-neural-network-models-analysis-services-data-mining.md)」を参照してください。  
  
 この表の "値" 列には、ServiceGrade の数値がどのように処理されたかが示されています。 "サポート" 列には、その値またはその範囲に分類されたケースの数が示されています。  
  
-   **連続する数値の使用 (既定)**  
  
     既定の方法を使用した場合、120 個の一意の値の結果が計算され、その平均値は 0.09875 になります。 また、不足値の数も確認できます。  
  
-   **クラスター化によるビン**  
  
     Microsoft クラスタリング アルゴリズムでオプションの値のグループを特定する場合、ServiceGrade の値が 5 つの範囲にグループ化されます。 "サポート" 列に示されているように、それぞれの範囲に分配されるケースの数は均等にはなりません。  
  
-   **同じ領域ごとのビン**  
  
     この方法を選択した場合、等しいサイズのバケットに値が分配されてから、各範囲の上限と下限が変更されます。 バケットの数は指定できますが、それぞれのバケットに含まれる値の数が数個だけにならないようにしてください。  
  
 ビン分割オプションの詳細については、「[データマイニング&#41;メソッド &#40;分離する方法](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)」を参照してください。  
  
 または、数値を使用する代わりに、サービスグレードを定義済みの対象範囲 ( **Best** (servicegrade servicegrade > 0.05) など) に分類し、 \<= 0.05), **Acceptable** (0.10 > **不適切**な (servicegrade >= 0.10) という個別の派生列を追加することもできます。  
  
###  <a name="create-a-copy-of-a-column-and-change-the-discretization-method"></a><a name="bkmk_newColumn"></a>列のコピーを作成し、分離メソッドを変更する  
 ターゲット属性 ServiceGrade を含むマイニング列のコピーを作成し、数値をグループ化する方法を変更します。 予測可能な属性を含め、マイニング構造の任意の列の複数のコピーを作成することができます。  
  
 このチュートリアルでは、Equal Areas 分離メソッドを使用して、バケット数を 4 に指定します。 結果のグループ化は、ビジネス ユーザーの興味の対象となるターゲット値に非常に近いものになります。  
  
####  <a name="to-create-a-customized-copy-of-a-column-in-the-mining-structure"></a><a name="bkmk_ColumnCopy"></a>マイニング構造に列のカスタマイズされたコピーを作成するには  
  
1.  ソリューション エクスプローラーで、作成したマイニング構造をダブルクリックします。  
  
2.  [マイニング構造] タブで、[**マイニング構造列の追加**] をクリックします。  
  
3.  [**列の選択**] ダイアログボックスで、[**ソース] 列**の一覧から [servicegrade] を選択し、[ **OK**] をクリックします。  
  
     マイニング構造列の一覧に新しい列が追加されます。 新しいマイニング列の既定の名前は、元の列と同じ名前に数値の接尾辞を付けたものです (例 : ServiceGrade 1)。 この列の名前を、よりわかりやすい名前に変更します。  
  
     分離メソッドも指定します。  
  
4.  [ServiceGrade 1] を右クリックし、[**プロパティ**] を選択します。  
  
5.  [**プロパティ**] ウィンドウで、 **name**プロパティを見つけ、名前を「 **Service グレード**ビン」に変更します。  
  
6.  関連するすべてのマイニング モデル列の名前を同じように変更するかどうかを確認するダイアログ ボックスが表示されます。 **[いいえ]** をクリックします。  
  
7.  [**プロパティ**] ウィンドウで、セクションの [**データ型**] を見つけ、必要に応じて展開します。  
  
8.  `Content` プロパティの値を `Continuous` から `Discretized` に変更します。  
  
     次のプロパティが使用できるようになりました。 次の表に従ってプロパティの値を変更します。  
  
    |プロパティ|既定値|新しい値|  
    |--------------|-------------------|---------------|  
    |`DiscretizationMethod`|`Continuous`|`EqualAreas`|  
    |`DiscretizationBucketCount`|値なし|4|  
  
    > [!NOTE]  
    >  <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn.DiscretizationBucketCount%2A> の既定値は実際は 0 です。これは、最適なバケット数がアルゴリズムによって自動的に決定されることを表します。 したがって、このプロパティの値を既定値に戻すには、「0」と入力します。  
  
9. データマイニングデザイナーで、[**マイニングモデル**] タブをクリックします。  
  
     マイニング構造列のコピーを追加すると、そのコピーの使用法フラグが自動的に `Ignore` に設定されます。 マイニング構造に列のコピーを追加する場合、通常は、そのコピーを元の列と一緒に分析に使用することはありません。一緒に使用すると、アルゴリズムでその 2 つの列の間に強力な相関関係が検出されて、他の関係がわかりにくくなってしまう可能性があります。  
  
##  <a name="add-a-new-mining-model-to-the-mining-structure"></a><a name="bkmk_NewModel"></a>マイニング構造への新しいマイニングモデルの追加  
 対象となる属性の新しいグループ化を作成できたら、次に、その離散化列を使用する新しいマイニング モデルを追加する必要があります。 この手順が完了すると、CallCenter マイニング構造に次の 2 つのマイニング モデルが含まれるようになります。  
  
-   ServiceGrade 値を連続する範囲として処理するマイニング モデル Call Center Default NN  
  
-   新しいマイニングモデルを作成します。これは、ターゲットとしてを使用し、ServiceGrade の列の値を、同じサイズの4つのバケットに分散して作成します。  
  
#### <a name="to-add-a-mining-model-based-on-the-new-discretized-column"></a>新しい離散化列に基づくマイニング モデルを追加するには  
  
1.  ソリューションエクスプローラーで、先ほど作成したマイニング構造を右クリックし、[**開く**] を選択します。  
  
2.  **[マイニング モデル]** タブをクリックします。  
  
3.  [**関連マイニングモデルの作成] を**クリックします。  
  
4.  [**新しいマイニングモデル**] ダイアログボックスの [**モデル名**] に、「」と入力 `Call Center Binned NN` します。 [**アルゴリズム名**] ドロップダウンリストで、[ **Microsoft ニューラルネットワーク**] を選択します。  
  
5.  新しいマイニング モデルに含まれる列の一覧で ServiceGrade を見つけて、使用法を `Predict` から `Ignore` に変更します。  
  
6.  同様に、ServiceGrade Binned を見つけて、使用法を `Ignore` から `Predict` に変更します。  
  
##  <a name="create-an-alias-for-the-target-column"></a><a name="bkmk_Alias2"></a>ターゲット列の別名を作成します。  
 通常は、別の予測可能な属性を使用するマイニング モデルを比較することはできませんが、 マイニング モデル列の別名を作成することができるため、 つまり、マイニングモデル内の ServiceGrade ビンの列の名前を変更して、元の列と同じ名前にすることができます。 データが別の方法で分離されていても、この 2 つのモデルを精度チャートで直接比較することができます。  
  
###  <a name="to-add-an-alias-for-a-mining-structure-column-in-a-mining-model"></a><a name="bkmk_Alias"></a>マイニングモデルのマイニング構造列に別名を追加するには  
  
1.  [**マイニングモデル**] タブの [**構造**] で、[servicegrade ビン] を選択します。  
  
     [**プロパティ**] ウィンドウに、scalarminingstructurecolumn 列のプロパティが表示されることに注意してください。  
  
2.  マイニング モデル ServiceGrade Binned NN の列で、ServiceGrade Binned 列に対応するセルをクリックします。  
  
     これで、[**プロパティ**] ウィンドウに、MiningModelColumn オブジェクトのプロパティが表示されます。  
  
3.  **Name**プロパティを見つけ、値をに変更し `ServiceGrade` ます。  
  
4.  **Description**プロパティを見つけ、「 **Temporary column alias**」と入力します。  
  
     [**プロパティ**] ウィンドウには、次の情報が含まれている必要があります。  
  
    |プロパティ|値|  
    |--------------|-----------|  
    |**説明**|Temporary column alias|  
    |**ID**|ServiceGrade ビン分割|  
    |**ModelingFlags**||  
    |**名前**|Service Grade|  
    |**SourceColumn ID**|Service Grade 1|  
    |**使用方法**|Predict|  
  
5.  [**マイニングモデル**] タブ内の任意の場所をクリックします。  
  
     グリッドが更新され、 `ServiceGrade` 列の使用法の横に新しい一時列の別名が表示されます。 マイニング構造と 2 つのマイニング モデルを含むグリッドは次のようになります。  
  
    |構造体|Call Center Default NN|Call Center Binned NN|  
    |---------------|----------------------------|---------------------------|  
    ||Microsoft ニューラル ネットワーク|Microsoft ニューラル ネットワーク|  
    |AutomaticResponses|入力|入力|  
    |AverageTimePerIssue|Predict|Predict|  
    |呼び出し|入力|入力|  
    |DayOfWeek|入力|入力|  
    |FactCallCenterID|Key|Key|  
    |IssuesRaised|入力|入力|  
    |LevelOneOperators|入力|入力|  
    |LevelTwoOperators|入力|入力|  
    |Orders|入力|入力|  
    |ServiceGrade Binned|無視|Predict (ServiceGrade)|  
    |ServiceGrade|Predict|無視|  
    |シフト|入力|入力|  
    |Total Operators|入力|入力|  
    |WageType|入力|入力|  
  
## <a name="process-all-models"></a>すべてのモデルを処理する  
 最後に、作成したモデルを簡単に比較できるように、既定のモデルとビン分割モデルのシード パラメーターを設定します。 シード値を設定すると、各モデルで同じポイントからデータの処理が開始されるようになります。  
  
> [!NOTE]  
>  シード パラメーターに数値を指定しなかった場合は、SQL Server Analysis Services により、モデルの名前に基づいてシードが生成されます。 モデルには必ず異なる名前が付けられるため、データが同じ順序で処理されるようにするにはシード値を設定する必要があります。  
  
###  <a name="to-specify-the-seed-and-process-the-models"></a><a name="bkmk_SeedProcess"></a>シードを指定してモデルを処理するには  
  
1.  [**マイニングモデル**] タブで、Call CENTER-LR という名前のモデルの列を右クリックし、[**アルゴリズムパラメーターの設定**] を選択します。  
  
2.  HOLDOUT_SEED パラメーターの行で、[**値**] の下の空のセルをクリックし、「」と入力し `1` ます。 **[OK]** をクリックします。 構造に関連付けられている各モデルに対してこの手順を繰り返します。  
  
    > [!NOTE]  
    >  関連するすべてのモデルで同じシードを使用する限り、シードとしてどのような値を選択するかは特に重要ではありません。  
  
3.  [**マイニングモデル**] メニューで、[**マイニング構造とすべてのモデルの処理**] を選択します。 [**はい**] をクリックして、更新されたデータマイニングプロジェクトをサーバーに配置します。  
  
4.  [**マイニングモデルの処理**] ダイアログボックスで、[**実行**] をクリックします。  
  
5.  [**閉じる**] をクリックして [**処理の進行状況**] ダイアログボックスを閉じ、[**マイニングモデルの処理**] ダイアログボックスでもう一度 [**閉じる**] をクリックします。  
  
 関連する 2 つのマイニング モデルを作成できたので、データを探索してデータの関係を見つけることができます。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [「&#40;中級者向けデータマイニングチュートリアル」のコールセンターモデルの調査&#41;](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [マイニング構造 (Analysis Services - データ マイニング)](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
  