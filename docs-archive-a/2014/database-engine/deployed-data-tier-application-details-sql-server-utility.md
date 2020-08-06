---
title: 配置されたデータ層アプリケーションの詳細 (SQL Server ユーティリティ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.UE.dac.details.F1
helpviewer_keywords:
- utility, management
- Utility
- SQL Server Utility [SQL Server]
- data-tier application [SQL Server], utility details
- Multi-server management [SQL Server]
ms.assetid: 79c41dd9-abcb-434e-9326-00a341d5c867
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 58d0933dcb7682210dde24c3c6d3a9a539d02b1d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634021"
---
# <a name="deployed-data-tier-application-details-sql-server-utility"></a>配置済みのデータ層アプリケーションの詳細 (SQL Server ユーティリティ)
  ユーティリティ エクスプローラーの [配置済みのデータ層アプリケーション] ビュー内の情報では、個々のデータ層アプリケーションの使用率に関するデータ、CPU 使用率の履歴、ファイル レベルでの記憶域使用率の詳細を確認できるほか、ポリシーのしきい値を表示および更新できます。 ポリシーのしきい値は、データ層アプリケーション レベルで CPU 使用率やデータベース データ ファイルおよびログ ファイルを対象に制御できます。 個々のデータ層アプリケーションについて、プロパティの詳細を表示することもできます。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 リスト ビュー  
 上部ペインのリスト ビューには、個々のデータ層アプリケーションに関するデータが表示されます。 正常性状態アイコンにより、各データ層アプリケーションの状態が使用率カテゴリごとに示されます。  
  
-   緑のチェック - ![](../../2014/database-engine/media/well-utilized.gif "Well_utilized") - リソース使用率のポリシーに違反していないデータ層アプリケーションの数。 リソースは適正使用です。  
  
-   緑の下向き矢印 - ![](../../2014/database-engine/media/utility-down-arrow.gif "Utility_down_arrow") - リソースは過小使用です。  
  
-   赤の上向き矢印 - ![](../../2014/database-engine/media/utility-up-arrow.gif "Utility_up_arrow") - リソースは過大使用です。  
  
 リスト ビュー内で列を左右にドラッグすると、列の順番を変更できます。 リスト ビューに列を追加したり、リスト ビューから列を削除したりするには、列見出しを右クリックして、目的の列を選択または選択解除します。 右クリック メニューには、並べ替えオプションもあります。 並べ替えは、列名の上部をクリックして有効にすることもできます。  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティのリスト ビューのフィルター オプションにアクセスするには、ユーティリティ エクスプローラーのナビゲーション ペインで **[配置済みのデータ層アプリケーション]** ノードを右クリックし、 **[フィルター]** を選択します。 フィルターの設定が実装されると、ユーティリティ エクスプローラーの **[配置済みのデータ層アプリケーション]** ノードに **[配置済みのデータ層アプリケーション (フィルター選択)]** というラベルが付けられます。 詳細については、「[[フィルターの設定] &#40;オブジェクト エクスプローラーおよびユーティリティ エクスプローラー&#41;](../ssms/object/filter-settings-object-explorer-and-utility-explorer.md)」を参照してください。  
  
 既定では、次の列に各データ層アプリケーションに関する正常性状態の情報が表示されます。  
  
-   [名前] - データ層アプリケーション名。  
  
-   [アプリケーションの CPU] - このデータ層アプリケーションのプロセッサ使用率の正常性状態が表示されます。 このパラメーターの正常性状態は、データ層アプリケーション用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。 詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。  
  
     このデータ層アプリケーションのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。  
  
-   [コンピューターの CPU] - コンピューターのプロセッサ使用率の正常性状態が表示されます。 このパラメーターの正常性状態は、コンピューター用に設定された CPU 使用率ポリシーと、変動の多いリソースの評価ポリシーの構成設定に従って決定されます。 詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。  
  
     このデータ層アプリケーションのプロセッサ使用率の履歴を表示するか、またはポリシーの制限を表示または変更するには、 **[CPU 使用率]** タブをクリックします。  
  
-   [ファイル領域] - 各データ層アプリケーションに関するファイル領域使用率の正常性状態の概要が表示されます。  
  
    -   緑のチェック - すべてのファイル グループおよびログ ファイル グループの正常性状態が過大使用でも過小使用でもありません。  
  
    -   緑の下向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイル グループの正常性状態が過小使用であり、かつ、いずれのファイル グループまたはログ ファイル グループも過大使用ではありません。  
  
    -   赤の上向き矢印 - 少なくとも 1 つのファイル グループまたはログ ファイル グループの正常性状態が過大使用です。 データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。  
  
     ファイル領域ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。  
  
-   [ボリューム領域] - 選択したデータ層アプリケーションに属するデータベースを含むすべてのボリュームに関するボリューム領域使用率の正常性状態の概要が表示されます。 いずれかのボリュームの正常性状態が過大使用になっている場合、ボリューム領域の正常性状態は過大使用としてリスト ビューに報告されます。 いずれかのボリュームの正常性状態が過小使用になっており、かつ、いずれのボリュームも過大使用になっていない場合、ボリューム領域の正常性状態は過小使用としてリスト ビューに報告されます。 それ以外の場合、ボリューム領域の正常性状態は適正使用としてリスト ビューに報告されます。 ポリシーの制限を表示または変更するには、 **[ストレージの使用率]** タブをクリックします。  
  
-   [ポリシーの種類] - データ層アプリケーションに対して "グローバル" 既定ポリシーまたは "オーバーライド" カスタム ポリシーのいずれを有効にするかを示します。  
  
-   [インスタンス名] - データ層アプリケーションをホストする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。  
  
 リスト ビューの列見出し領域で右クリック メニューを使用すると、次に示すその他の列を表示できます。  
  
-   データベース名  
  
-   [配置日]  
  
-   信頼可能: (True または False)  
  
-   照合順序  
  
-   [互換性レベル]\([Version100] など)  
  
-   暗号化有効: (True または False)  
  
-   復旧モデル: (単純、完全、または一括ログ)  
  
-   [最終報告日時] この列には、UCP のローカル日時が datetime データ型を使用して表示されます。 詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。 ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。 詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。  
  
 [CPU 使用率] タブ  
 [CPU 使用率] タブには、データ層アプリケーションとコンピューターの CPU 使用率を示す履歴データのグラフが並んで表示されます。  
  
 表示領域の右側にあるオプション ボタンで対象期間を指定すると、その期間におけるプロセッサ使用率の履歴が表示されます。 表示間隔を変更してデータセットを更新するには、一覧にあるオプション ボタンを選択します。  
  
 間隔のオプションは次のとおりです。  
  
-   [1 日] : 15 分間隔で表示されます。  
  
-   [1 週間] : 1 日間隔で表示されます。  
  
-   [1 か月] : 1 週間間隔で表示されます。  
  
-   [1 年] : 1 か月間隔で表示されます。  
  
 [ストレージの使用率] タブ  
 [ストレージの使用率] タブには、リスト ビューで選択したデータ層アプリケーションに属するデータベース ファイルとログ ファイルに関する記憶域使用率の詳細が表示されるツリー ビューがあります。 時間データとして、UCP のローカル日時が datetime データ型で表示されることに注意してください。 詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。 ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。 詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。  
  
 表示内容は、ファイル グループまたはボリュームごとにグループ化できます。 ファイル グループ ツリー ビューを使用するには、 **[ファイルのグループ化]** の選択項目で **[ファイル グループ]** オプション ボタンをクリックします。  
  
 記憶域使用率の履歴のグラフに表示されるデータは、ツリー ビューで選択したノードに応じて変化します。  
  
-   ファイル グループ ノードを選択すると、選択したファイル グループに属するすべてのデータ ファイルによって使用されているファイル領域のグラフが表示されます。  
  
-   ログ ファイル ノードを選択すると、選択したデータベースに属するすべてのログ ファイルによって使用されているファイル領域のグラフが表示されます。  
  
-   データベース ノードを選択すると、選択したデータベースに属するすべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域を合計したグラフが表示されます。  
  
 個々のファイルの記憶域使用率の状態を表示するには、ツリー ビューでファイル名の横にあるプラス記号をクリックします。  
  
 正常性状態のアイコンにより、ポリシーのしきい値と比較した各ファイル グループの状態がひとめでわかります。  
  
-   緑のチェック - ファイル グループにある少なくとも 1 つのデータ ファイルのファイル領域使用率が過大使用でも過小使用でもありません。  
  
-   緑の下向き矢印 - ファイル グループにある少なくとも 1 つのデータ ファイルのファイル領域使用率が過小使用であり、かつ、ファイル グループにあるいずれのファイルも過大使用ではありません。  
  
-   赤の上向き矢印 - ファイル グループにあるすべてのデータ ファイルのファイル領域使用率が過大使用です。 データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。  
  
 ボリュームごとにファイルを表示するには、 **[ファイルのグループ化]** の選択項目で **[ボリューム]** オプション ボタンをクリックします。 記憶域使用率の履歴のグラフに、記憶域ボリューム上ですべてのデータ ファイルとすべてのログ ファイルによって使用されているファイル領域が表示されます。 ツリーを展開すると、個々のデータベース データ ファイルとログ ファイルの詳細を表示できます。  
  
 各ボリュームの状態は、状態アイコンによって示されます。  
  
-   緑のチェック - リソースは適正使用です。  
  
-   緑の下向き矢印 - リソースは過小使用です。  
  
-   赤の上向き矢印 - リソースは過大使用です。  
  
 [ストレージの使用率] タブ上の各ファイル名の横にあるゲージは、ファイルによって使用されている領域のサイズを、ファイルの有効容量と比較して表します。 ゲージの横に表示されるパーセントの値は、ファイルによって使用されている領域のサイズとファイルの有効容量の比率です。 ツールヒントでは、各ボリュームおよび各ファイルと有効容量の比較によるパーセント計算に使用されたデータを確認できます。  
  
 ファイルが自動拡張するように構成されていない場合は、ファイルに割り当てられている領域のサイズが有効容量になります。 ファイルが自動拡張するように構成されている場合は、現在ファイルに割り当てられている領域のサイズと、現在ボリューム上で利用できる空き領域のサイズの合計が有効容量になります。  
  
 データ ファイル用およびログ ファイル用に、記憶域使用率のポリシーを構成できます。 ファイルの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ファイル ポリシー]** リンクをクリックします。 記憶域ボリュームの記憶域使用率ポリシーのしきい値を表示または変更するには、[ストレージの使用率] ペインの下部にある **[ボリューム ポリシー]** リンクをクリックします。  
  
 既定のポリシーのしきい値をオーバーライドするには、 **[既定のポリシーをオーバーライド]** のオプション ボタンをクリックして上限と下限の値を指定し、 **[OK]** をクリックします。  
  
 ポリシー違反の許容範囲変更の詳細については、「[CPU 使用率のポリシーにおけるノイズの軽減 &#40;SQL Server ユーティリティ&#41;](../relational-databases/manage/reduce-noise-in-cpu-utilization-policies-sql-server-utility.md)」を参照してください。  
  
 [プロパティの詳細] タブ  
 データ層アプリケーションで一覧表示されるプロパティの詳細には、次のカテゴリがあります。  
  
-   データベース名  
  
-   [配置日]  
  
-   信頼可能: (True または False)  
  
-   照合順序  
  
-   [互換性レベル]\([Version100] など)  
  
-   暗号化有効: (True または False)  
  
-   復旧モデル: (単純、完全、または一括ログ)  
  
-   [最終報告日時] この列には、UCP のローカル日時が datetime データ型を使用して表示されます。 詳細については、SQL Server オンライン ブックの「 [datetime (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=164071) 」を参照してください。 ユーティリティ オブジェクト モデルを使用する場合は、SSMS で datetimeoffset データ型が使用されることに注意してください。 詳細については、SQL Server オンライン ブックの「 [datetimeoffset (Transact-SQL)](https://go.microsoft.com/fwlink/?LinkId=141713) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Managed Instance の詳細 &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/managed-instance-details-sql-server-utility.md)   
 [ユーティリティダッシュボード &#40;SQL Server ユーティリティ&#41;](../../2014/database-engine/utility-dashboard-sql-server-utility.md)   
 [SQL Server ユーティリティでの SQL Server のインスタンスの監視](../relational-databases/manage/monitor-instances-of-sql-server-in-the-sql-server-utility.md)   
 [SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  