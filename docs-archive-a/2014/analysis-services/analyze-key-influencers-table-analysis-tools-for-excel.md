---
title: 主要な影響元の分析 (Excel 用のテーブル分析ツール) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
ms.openlocfilehash: f60eb5144059b0976d52eec2329f27553132146c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633641"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>主要な影響元の分析 (Excel 用のテーブル分析ツール)
  ![リボンの [主要な影響元の分析] ボタン](media/tat-aki.gif "リボンの [主要な影響元の分析] ボタン")  
  
 主要な**影響**元の分析ツールでは、ターゲットの結果を含む列を選択すると、その結果に最も強い影響を与える要因がアルゴリズムによって決定されます。  
  
 このツールで作成される新規データ テーブルでは、個別の結果に関連付けられた要因が報告され、関係の可能性がグラフィカルに表示されます。 さまざまな要因および結果によってテーブルをフィルタリングして、結果を詳しく調べることができます。  
  
 可能性のある結果のペアを選択して比較することもできます。 たとえば、可能な意思決定要因を特定するために、異なる消費者グループを比較します。  
  
## <a name="using-the-analyze-key-influencers-tool"></a>主要な影響元の分析ツールの使用  
  
1.  Excel データ テーブルを開きます。  
  
2.  [**テーブルツール**] の [**分析**] リボンで、[主要影響元の分析] をクリックし**ます。**  
  
3.  分析のターゲットとして 1 つの列を選択します。  
  
4.  必要に応じ**て、[分析に使用する列の選択**] をクリックします。 **[高度な列の選択**] ダイアログボックスで、関連するデータを格納する可能性が最も高い列を選択します。 高いパフォーマンスと精度を確保するため、ID や名前などのパターン分析に重要ではない列を選択解除します。 [ **OK** ] をクリックして、[**高度な列の選択**] ダイアログボックスを閉じます。  
  
5.  **[実行]** をクリックします。  
  
     **主要な影響**元の分析ツールは、データの分析を行い、最適な設定を決定し、すべてのパラメーターを自動的に設定します。  
  
6.  パターンが検出されなかった場合は、問題の説明を含む新しいワークシートが作成されます。  
  
7.  パターンが検出されると、新しいワークシートにレポートが作成されて、そのパターンが表示されます。 このレポートには、**の主要 \<column> な影響**元という名前が付けられます。 この後の手順に従ってレポートをカスタマイズすることもできます。  
  
#### <a name="create-a-custom-report"></a>カスタム レポートの作成  
  
1.  **[主要な影響元に基づく識別**] ダイアログボックスで、[**値 1** ] と [**値 2** ] のドロップダウンリストから比較する2つの値を選択します。 たとえば、購入者と非購入者を比較できます。  
  
2.  [**レポートの追加**] をクリックします。  
  
     このウィザードは、新規ワークシートを作成し、主要な要因の比較の各ペアに対するテーブルを追加します。  
  
3.  比較が完了したら、[**閉じる**] をクリックします。  
  
## <a name="understanding-the-key-influencers-report"></a>主要な影響元レポートについて  
 データモデルが作成されると、主要な影響元の**分析**ツールによってレポートが作成され、主要な影響元を調査して比較するのに役立ちます。  
  
-   左側にあるレポートは、既定で生成されるレポートです。 結果の列 (従属変数) で最も強力な予測子を示します。  
  
-   右側にあるレポートはオプションで、2 つの特定の結果値を比較することで作成できます。 このレポートは、購入者と非購入者を比較します。  
  
-   作成したレポートごとに新しいワークシートが追加されることに注意してください。 テーブルは作成後に移動することができます。ここでは、比較のためにテーブルを並べて配置しています。  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **相対的影響**  
 最初のレポートの網掛けされたバーは、この属性と結果とのアソシエーションの強さを示します。  
  
 バーの長さは、要因が結果に影響する可能性を示しており、網掛けされたバーが長いほど、アソシエーションが強いことを表しています。  
  
 **ライター**  
 2 つ目のレポートでは、比較するターゲット値が 2 列に表示され、関連要因が信頼スコアの降順に並べられます。  
  
-   **青色**のバーは、結果に寄与する属性を示します。 "No" (= は購入されませんでした)。  
  
-   **赤色**のバーは、"Yes" (自転車を購入) という結果に貢献する属性を示しています。  
  
 網掛けされたバーの色は任意です。 Excel でテーブル デザインのオプションを設定すると色を変更できます。  
  
 2 つの値を比較するレポートの場合、その 2 つ目のレポートでは、ターゲット値に対する影響の強さで主要な影響元が順位付けされます。  
  
 すべてのグラフは Excel のテーブルを基にしているため、フィルター処理と並べ替えによって特定の要因または結果に注目することができます。  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>主要な影響元の分析ツールの詳細  
 **主要影響**元の分析ツールによってデータが分析されると、次のようになります。  
  
-   データの分布に関する主要な情報を格納するデータ構造を作成します。  
  
-   Microsoft Na&amp;#239;&lt;/ph&gt;ve Bayes アルゴリズムを使用して、モデルが作成されます。  
  
-   データの各列を指定した結果に関連付ける予測を作成します。  
  
-   予測ごとの信頼スコアを使用して、目標の結果を得るうえで最も影響を与える要因を識別します。  
  
-   信頼スコア順に並べ替えて、主要な影響元を記述したレポートを作成します。  
  
### <a name="requirements"></a>必要条件  
 ターゲット列に連続する数値が含まれている場合、このツールは自動的に数値をグループにセグメント化します。 これらのグループは、類似の特性を持つケースのクラスターを表します。 ただし、ユーザーにとってわかりやすいグループになるとは限りません。 たとえば、レポートに "12.85701" などのグループが含まれているとし \< ます。一方、通常、レポートユーザーは、10-19、20-29 など、整数を使用するグループを表示します。  
  
 数値データを異なる方法でグループ化する場合は、分析を作成する前にデータを必要な形にセグメント化しておく必要があります。 たとえば、Excel 用のデータマイニングクライアントのラベルの[書き換え](relabel-sql-server-data-mining-add-ins.md)ツールを使用して、別の列に新しいグループ化ラベルを作成し、その新しい列のみを分析で使用できます。  
  
### <a name="related-tools"></a>関連ツール  
 [**データマイニング**] リボンには、データマイニングモデルをカスタマイズする機能など、より高度なツールが用意されています。  
  
 **主要な影響**元の分析ツールを使用してモデルを保存する場合は、データマイニングクライアントを使用して、モデルを参照し、リレーションシップを詳細に調べることができます。 詳細については、「 [Excel でのモデルの参照 &#40;SQL Server データマイニングアドイン&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)」を参照してください。 Microsoft Office Visio を使用し、関係をクラスターまたは依存関係ネットワークとして示すグラフおよびダイアグラムを作成することもできます。 詳細については、「 [SQL Server データマイニングアドイン&#41;&#40;Visio データマイニング図のトラブルシューティング](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)」を参照してください。  
  
> [!NOTE]  
>  テーブル分析ツールを使用しているときに作成されたモデルは、ワークシートを閉じたとき、または、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーとの接続を終了したときに削除されます。 したがって、それらのモデルを参照できるのは、接続が開いている間だけです。 接続を閉じたりワークシートを閉じたりすると、モデルを Visio で表示することもできなくなります。  
  
 **主要な影響**元の分析ツールで使用されるアルゴリズムの詳細については、SQL Server オンラインブックの「Microsoft の単純な Bayes アルゴリズム」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Excel 用のテーブル分析ツール](table-analysis-tools-for-excel.md)   
 [データ マイニング モデルの作成](creating-a-data-mining-model.md)  
  
  