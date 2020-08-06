---
title: '[オプション] ([環境]: [フォントおよび色] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea3aa222-538d-485f-99dc-01eb02cdcfea
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2056ac91544efb2942fc223730efada136ad14be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719347"
---
# <a name="options-environment-fonts-and-colors-page"></a>[オプション] ([環境]:[フォントおよび色] ページ)
  **[オプション]** ダイアログ ボックスを使用すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] のさまざまなユーザー インターフェイス要素にカスタム フォントや配色を設定できます。 **[ツール]** メニューの **[オプション]** をクリックし、 **[環境]** フォルダーを展開して、 **[フォントおよび色]** を選択します。  
  
 配色を変更するセッション中は、変更は適用されません。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の別のインスタンスを開き、変更が適用されると思われる条件を作ることで、色の変更を確認できます。  
  
## <a name="ui-element-list"></a>UI 要素の一覧  
 **[設定の表示]**  
 フォントと配色を変更できるユーザー インターフェイス要素がすべて一覧表示されます。 この一覧で項目を選択した後、選択した項目の色設定を **[表示項目]** でカスタマイズします。  
  
|期間|定義|  
|----------|----------------|  
|[テキスト エディター]|[テキスト エディター] のフォント スタイル、フォント サイズ、フォント色を変更すると、既定のテキスト エディターに表示されるテキストの外観が変更されます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] の外部のテキスト エディターで開いたドキュメントは、この設定の影響を受けません。|  
|[プリンター]|[プリンター] のフォント スタイル、フォント サイズ、色の表示設定を変更すると、印刷されるドキュメント内のテキストの外観が変更されます。<br /><br /> ヒント: 必要に応じて、テキストエディターでの表示に使用するのとは別の既定のフォントを印刷用に選択できます。 これは、1 バイト文字と 2 バイト文字の両方を含むコードを印刷する場合に役立ちます。|  
|[すべてのテキスト ツール ウィンドウ **]**|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で出力ペインを持つツール ウィンドウ内のテキストの外観が変更されます。 これには、たとえば [出力] ウィンドウや [結果のテキスト表示] ウィンドウなどが該当します。<br /><br /> 注: [すべてのテキスト ツール ウィンドウ] 項目のテキストを変更するセッション中は、変更は適用されません。 変更を確認するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の別のインスタンスを開きます。|  
|[検索結果ウィンドウ]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、検索結果ウィンドウ内のテキストの外観が変更されます。|  
|[出力ウィンドウ]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、[出力] ウィンドウ内のテキストの外観が変更されます。|  
|[結果のグリッド表示]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、クエリ ウィンドウの **[結果のグリッド表示]** 領域のテキストの外観が変更されます。|  
|[実行プラン]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] および [!INCLUDE[ssEW](../../includes/ssew-md.md)] のクエリの実行プランのテキストの外観が変更されます。|  
|[結果のテキスト表示]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、クエリ ウィンドウの **[結果のテキスト表示]** 領域のテキストの外観が変更されます。|  
|[ビジネス インテリジェンス デザイナー]|この項目のフォント スタイル、フォント サイズ、色の表示設定を変更すると、[ビジネス インテリジェンス デザイナー] ウィンドウ内のテキストの外観が変更されます。|  
  
 **既定値を設定する**  
 **[既定値を使用]** ボタンをクリックすると、 **[設定の表示]** の一覧で選択した項目のフォントとカラー値が既定値にリセットされます。  
  
 **[フォント (太字は固定幅フォントを示します)]**  
 システムにインストールされているフォントがすべて一覧表示されます。 このドロップダウン リストを開くと、最初は **[設定の表示]** の一覧で選択した要素の現在のフォントが選択されています。 固定フォント (エディターでの行揃えが簡単です) は太字で表示されます。  
  
 **[サイズ]**  
 選択したフォントに適用できるポイント サイズが一覧表示されます。 フォントのサイズを変更すると、 **[設定の表示]** の一覧で選択したすべての **[表示項目]** エントリのフォント サイズが変更されます。  
  
 **[表示項目]**  
 文字色と背景色を変更できる項目が一覧表示されます。  
  
> [!NOTE]  
>  既定の表示項目は、[テキスト形式] です。 [テキスト形式] に割り当てたプロパティは、他の表示項目に割り当てられたプロパティによってオーバーライドされます。 たとえば **[テキスト形式]** に青色を割り当て、[識別子] に緑色を割り当てると、識別子はすべて緑色で表示されます。 この例では、[テキスト形式] プロパティを [識別子] プロパティがオーバーライドします。  
  
 次のような表示項目があります。  
  
-   インジケーター マージン: コード エディターの左端で、ブレークポイントとブックマークのアイコンが表示される余白の部分。  
  
-   「縮小可能テキスト」: コード エディターで、表示と非表示を切り替えられるテキストまたはコードのブロック (XML のみ)。  
  
 **[前景アイテム]**  
 **[表示項目]** で選択した項目の文字色に選択できる色が一覧表示されます。 一部の項目は関連しているため、配色を一貫させる必要があります。たとえば、テキストの文字色を変更すると、文字列などの要素の文字色も変更されます。  
  
 **Custom**  
 **[色の設定]** ダイアログ ボックスを表示します。ここで、 **[表示項目]** の一覧で選択した項目にカスタム色を設定できます。  
  
> [!NOTE]  
>  カスタム色の定義は、コンピューターの表示の色設定による制限を受ける場合があります。 たとえば、コンピューターの表示が 256 色に設定されているときに **[色の設定]** ダイアログ ボックスでカスタム色を選択すると、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] では既定で **[基本色]** 内の最も近い色が選択され、 **[色の設定]** ダイアログ ボックスには黒が表示されます。  
  
 **[背景アイテム]**  
 カラー パレットが表示されます。ここで、 **[表示項目]** で選択した項目の背景色を選択します。 一部の項目は関連しているため、配色を一貫させる必要があります。たとえば、テキストの背景色を変更すると、SQL 文字列などの要素の背景色も変更されます。  
  
 **Custom**  
 **[色の設定]** ダイアログ ボックスを表示します。ここで、 **[表示項目]** の一覧で選択した項目にカスタム色を設定できます。  
  
 **太字**  
 このチェック ボックスをオンにすると、選択した表示項目のテキストが太字のフォントで表示されます。 テキストを太字にすると、エディターで見つけやすくなります。  
  
 **サンプル**  
 **[設定の表示]** と **[表示項目]** で選択した値のフォント スタイル、フォント サイズ、配色のサンプルを表示します。 このテキスト ボックスを使用して、さまざまな形式オプションを指定した場合の結果をプレビューできます。  
  
## <a name="see-also"></a>参照  
 [クエリエディターでのコードの色分け](../../relational-databases/scripting/color-coding-in-query-editors.md)   
 [[オプション &#40;テキストエディター]: [エディターのタブとステータスバー] ページ&#41;](../../database-engine/options-text-editor-editor-tab-and-status-bar-page.md)  
  
  