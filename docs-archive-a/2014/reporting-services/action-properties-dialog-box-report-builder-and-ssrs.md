---
title: '[アクションプロパティ] ダイアログボックス (レポートビルダーおよび SSRS) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.shared.action.f1
- "10413"
- "10504"
- sql12.rtp.rptdesigner.calculatedseriesproperties.action.f1
- sql12.rtp.rptdesigner.pictureproperties.action.f1
- sql12.rtp.rptdesigner.actionproperties.f1
- sql12.rtp.rptdesigner.charttitleproperties.action.f1
- "10133"
- "10052"
- "10147"
- sql12.rtp.rptdesigner.chartproperties.action.f1
- "10122"
- sql12.rtp.rptdesigner.serieslabelproperties.action.f1
- sql12.rtp.rptdesigner.textboxproperties.action.f1
- "10162"
- "10168"
- sql12.rtp.rptdesigner.textproperties.action.f1
- sql12.rtp.rptdesigner.placeholderproperties.action.f1
- "10250"
- "10129"
- "10244"
- sql12.rtp.rptdesigner.seriesproperties.action.f1
ms.assetid: 2c5d915b-4f97-42cf-b8f1-49ca3ff3d0f9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77b51af0763010676b95fcedb433ab963fc7fcdf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642624"
---
# <a name="action-properties-dialog-box-report-builder-and-ssrs"></a>[アクション プロパティ] ダイアログ ボックス (レポート ビルダーおよび SSRS)
  **[アクション]** ダイアログ ボックスでは、グラフ、ゲージ、およびリンクをサポートするマップ要素に対してハイパーリンク オプションを有効にできます。 ユーザーがレポート上でクリックして、URL、同じレポート サーバーまたはレポート サーバーと統合されている SharePoint サイト上の他のレポート、または同じレポート内の他の場所にリンクできるようにアクションを定義します。  
  
## <a name="options"></a>Options  
 **アクションとして有効にする**  
 ユーザーがアイテムをクリックしたときに実行するアクションを示すオプションを選択します。  
  
 **なし**  
 アイテムに対するアクションがないことを示します。  
  
 **[レポートに移動する]**  
 レポート サーバー上にある詳細レポートへのリンクを作成します。 **[レポートに移動する]** をクリックすると、次のオプションが表示されます。  
  
 **[レポートの指定]**  
 詳細レポートとして使用するレポート名を入力または選択します。 詳細レポートはこのレポートと同じレポート サーバーに存在する必要があります。  
  
 ネイティブ モード用に構成されているレポート サーバーにレポートをパブリッシュする場合は、ファイル名の拡張子を含まない完全パスまたは相対パスを指定します。 レポートが現在のレポートと同じフォルダーに保存されている場合は、レポートの名前のみを使用します。 レポートが、同じレポート サーバー上の別のフォルダーに保存されている場合は、相対パスまたは完全パスを使用します。 相対パスは、現在のフォルダーから始まり、フォルダー階層を上に移動します (例: ../Folder2/Report1)。 完全パスは Home フォルダー「/」から始まります。 たとえば、「/Reports/Report1」のように指定します。  
  
 SharePoint 統合モードで構成されているレポート サーバーにレポートをパブリッシュする場合は、ファイル名の拡張子 (.rdl) を含めた完全修飾 URL を指定します。 たとえば、http:// *\<SharePointservername>/\<site>* /documents/report1.rdl」 相対パスはサポートされません。  
  
 詳細については、msdn.microsoft.com の[レポート ビルダーに関するドキュメント](https://go.microsoft.com/fwlink/?LinkId=154494)の「[外部アイテムへのパスの指定 (レポート ビルダーおよび SSRS)](report-design/specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。  
  
 **[レポートの実行に以下のパラメーターを使用]**  
 詳細レポートに渡すパラメーターの一覧を追加します。 パラメーター名は、対象のレポートで定義されているパラメーターと一致する必要があります。 パラメーターを追加または削除するには **[追加]** ボタンまたは **[削除]** ボタンを使用し、パラメーターの一覧の順序を設定するには上矢印および下矢印を使用します。  
  
 **[追加]**  
 詳細レポートに渡す新しいパラメーターを追加します。  
  
 **削除**  
 詳細レポートのパラメーターを削除します。  
  
 **上矢印**  
 パラメーターを一覧内で上に移動します。  
  
 **下方向キー**  
 パラメーターを一覧内で下に移動します。  
  
 **名前**  
 詳細レポートで定義されているパラメーターの名前のテキストを入力します。  
  
 **Value**  
 詳細レポート内の名前付きパラメーターに渡す値を入力または選択します。 式を編集するには、**式**([*fx*]) ボタンをクリックします。  
  
 **[省略]**  
 パラメーターを実行しないようにする場合にオンにします。 既定では、このチェック ボックスはオフになっており、アクティブではありません。 このチェックボックスをオンにするには、**式**([*fx*]) ボタンをクリックし、「 **True** 」と入力するか、式を作成します。 このチェック ボックスは、 **[式]** ダイアログ ボックスで **[OK]** をクリックするとオンになります。  
  
 **[ブックマークに移動する]**  
 現在のレポート内のブックマークへのリンクを定義します。 **[ブックマークに移動する]** をクリックすると、次のオプションが表示されます。  
  
 **[ブックマークの選択]**  
 レポートのブックマーク ID を入力または選択し、ユーザーがリンクをクリックしたときに、そのブックマークに移動するようにします。 式を変更するには、式 ([**fx**]) ボタンをクリックします。 ブックマーク ID には、静的 ID、または結果がブックマーク ID になる式のいずれかを指定できます。 式には、ブックマーク ID を含むフィールドを含めることができます。  
  
 ブックマークにリンクするには、まずレポート アイテムの Bookmark プロパティを設定する必要があります。 Bookmark プロパティを設定するには、レポート アイテムを選択し、プロパティ ペインでブックマーク ID の値または式 (SalesChart、5TopSales など) を入力します。  
  
 **[URL に移動する]**  
 Web ページへのリンクを定義します。 Web ページの URL、または結果が Web ページの URL になる式を入力または選択します。 式を変更するには、**式**([*fx*]) ボタンをクリックします。 この式には、URL が格納されているフィールドを含めることができます。 **[URL に移動する]** をクリックすると、次のオプションが表示されます。  
  
 **[URL の選択]**  
 アイテムの URL を入力します。 ネイティブ モード用に構成されているレポート サーバーにアイテムをパブリッシュする場合は、完全パスまたは相対パスを指定します。 たとえば、http:// *\<servername>* /images/image1.jpg します。 SharePoint 統合モードで構成されているレポートサーバーにアイテムをパブリッシュする場合は、完全修飾 URL を使用します (たとえば、http:// *\<SharePointservername>/\<site>* /Documents/images/image1.jpg)。  
  
## <a name="see-also"></a>参照  
 [グラフ &#40;レポートビルダーと SSRS&#41;](report-design/charts-report-builder-and-ssrs.md)   
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [レポートパラメーター &#40;レポートビルダーとレポートデザイナー&#41;](report-design/report-parameters-report-builder-and-report-designer.md)   
 [サブレポートとパラメーター &#40;レポートビルダーと SSRS に追加&#41;](report-design/add-a-subreport-and-parameters-report-builder-and-ssrs.md)   
 [対話的な並べ替え、ドキュメント マップ、およびリンク &#40;レポート ビルダーおよび SSRS&#41;](report-design/interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)  
  
  
