---
title: HTML デバイス情報設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- HTML [Reporting Services], rendering
- device information settings [Reporting Services], HTML rendering
ms.assetid: f505f478-dd6d-444a-957c-34f7cfb98911
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: fe4180ef1697e1ba8c78842e670029cb9c8a4131
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743029"
---
# <a name="html-device-information-settings"></a><span data-ttu-id="a08a0-102">HTML デバイス情報設定</span><span class="sxs-lookup"><span data-stu-id="a08a0-102">HTML Device Information Settings</span></span>
  <span data-ttu-id="a08a0-103">次の表は、HTML 形式で表示するデバイス情報設定を示しています。</span><span class="sxs-lookup"><span data-stu-id="a08a0-103">The following table lists the device information settings for rendering in HTML format.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a08a0-104">次の表に示す **(\*)** の付いたデバイス情報設定は非推奨になっているため、新しいアプリケーションでは使用できません。</span><span class="sxs-lookup"><span data-stu-id="a08a0-104">The device information settings listed in the table below with a **(\*)** have been deprecated and they should not be used in new applications.</span></span> <span data-ttu-id="a08a0-105">詳細については、 [SQL Server 2014 の「SQL Server Reporting Services の非推奨の機能](deprecated-features-in-sql-server-reporting-services-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a08a0-105">For more information, see [Deprecated Features in SQL Server Reporting Services in SQL Server 2014](deprecated-features-in-sql-server-reporting-services-ssrs.md).</span></span>  
  
|<span data-ttu-id="a08a0-106">設定</span><span class="sxs-lookup"><span data-stu-id="a08a0-106">Setting</span></span>|<span data-ttu-id="a08a0-107">値</span><span class="sxs-lookup"><span data-stu-id="a08a0-107">Value</span></span>|  
|-------------|-----------|  
|`AccessibleTablix`|<span data-ttu-id="a08a0-108">スクリーン リーダー用の追加のアクセシビリティ メタデータを使用して表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-108">Indicates whether to render with additional accessibility metadata for use with screen readers.</span></span> <span data-ttu-id="a08a0-109">このパラメーターは、単純なグループ化が行われる、単純なテーブル構造またはマトリックス構造を持つレポートにのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-109">This parameter is only applicable to reports that contain simple table or matrix structures with simple grouping.</span></span> <span data-ttu-id="a08a0-110">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-110">The default value is `false`.</span></span> <span data-ttu-id="a08a0-111">追加のアクセシビリティ メタデータを使用すると、「Electronic and Information Technology Accessibility Standards (電子/情報技術アクセシビリティ基準)」(Section 508 (第 508 条)) の「Web-based Intranet and Internet Information and Applications (Web ベースのイントラネットとインターネットの情報およびアプリケーション)」(1194.22) で定められている次の技術標準に準拠したレポートを表示できます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-111">The additional accessibility metadata causes the rendered report to be compliant with the following technical standards in the "Web-based Intranet and Internet Information and Applications" section (1194.22) of the Electronic and Information Technology Accessibility Standards (Section 508) document:</span></span><br /><br /> <span data-ttu-id="a08a0-112">(g) データ テーブルの行と列のヘッダーは、識別できるようにすること。</span><span class="sxs-lookup"><span data-stu-id="a08a0-112">(g) Row and column headers shall be identified for data tables.</span></span><br /><br /> <span data-ttu-id="a08a0-113">(h) データ テーブルの行または列のヘッダーの論理階層が 2 階層以上になる場合は、マークアップを使用してデータ セルとヘッダー セルを関連付けること。</span><span class="sxs-lookup"><span data-stu-id="a08a0-113">(h) Markup shall be used to associate data cells and header cells for data tables that have two or more logical levels of row or column headers.</span></span><br /><br /> <span data-ttu-id="a08a0-114">(i) 識別および移動しやすいように、フレームにはテキストによるタイトルを付けること。</span><span class="sxs-lookup"><span data-stu-id="a08a0-114">(i) Frames shall be titled with text that facilitates frame identification and navigation.</span></span><br /><br /> <span data-ttu-id="a08a0-115">このパラメーターはではサポートされていますが、ではサポートされて [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2010](../includes/sps2010-md.md)] いません [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2007](../includes/sps2007-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a08a0-115">This parameter is supported in [!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[SPS2010](../includes/sps2010-md.md)], but not in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[SPS2007](../includes/sps2007-md.md)].</span></span>|  
|<span data-ttu-id="a08a0-116">**ActionScript ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-116">**ActionScript(\*)**</span></span>|<span data-ttu-id="a08a0-117">ドリルスルーやブックマークのクリックなどのアクション イベントが発生したときに使用する JavaScript 関数の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-117">Specifies the name of the JavaScript function to use when an action event occurs, such as a drillthrough or bookmark click.</span></span> <span data-ttu-id="a08a0-118">このパラメーターを指定した場合、アクション イベントが発生すると、サーバーへのポストバックを行う代わりに、名前付き JavaScript 関数がトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-118">If this parameter is specified, an action event will trigger the named JavaScript function instead of a postback to the server.</span></span>|  
|<span data-ttu-id="a08a0-119">**BookmarkID**</span><span class="sxs-lookup"><span data-stu-id="a08a0-119">**BookmarkID**</span></span>|<span data-ttu-id="a08a0-120">レポート内のジャンプ先ブックマーク ID。</span><span class="sxs-lookup"><span data-stu-id="a08a0-120">The bookmark ID to jump to in the report.</span></span>|  
|<span data-ttu-id="a08a0-121">**DocMap**</span><span class="sxs-lookup"><span data-stu-id="a08a0-121">**DocMap**</span></span>|<span data-ttu-id="a08a0-122">レポートドキュメント マップの表示と非表示を切り替えます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-122">Indicates whether to show or hide the report document map.</span></span> <span data-ttu-id="a08a0-123">このパラメーターの既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-123">The default value of this parameter is `true`.</span></span>|  
|`ExpandContent`|<span data-ttu-id="a08a0-124">レポートを、水平方向のサイズを抑えたテーブル構造に収めるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-124">Indicates whether the report should be enclosed in a table structure which constricts horizontal size.</span></span>|  
|<span data-ttu-id="a08a0-125">**FindString**</span><span class="sxs-lookup"><span data-stu-id="a08a0-125">**FindString**</span></span>|<span data-ttu-id="a08a0-126">レポートの検索条件として使用する文字列。</span><span class="sxs-lookup"><span data-stu-id="a08a0-126">The text to search for in the report.</span></span> <span data-ttu-id="a08a0-127">このパラメーターの既定値は、空文字列です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-127">The default value of this parameter is an empty string.</span></span>|  
|<span data-ttu-id="a08a0-128">**GetImage ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-128">**GetImage (\*)**</span></span>|<span data-ttu-id="a08a0-129">HTML ビューアー ユーザー インターフェイス用の特定のアイコンを取得します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-129">Gets a particular icon for the HTML Viewer user interface.</span></span>|  
|`HTMLFragment`|<span data-ttu-id="a08a0-130">完全な HTML ドキュメントの代わりに HTML 断片を作成するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-130">Indicates whether an HTML fragment is created in place of a full HTML document.</span></span> <span data-ttu-id="a08a0-131">HTML 断片には TABLE 要素のレポート コンテンツが含まれ、HTML 要素と BODY 要素は省略されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-131">An HTML fragment includes the report content in a TABLE element and omits the HTML and BODY elements.</span></span> <span data-ttu-id="a08a0-132">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-132">The default value is `false`.</span></span> <span data-ttu-id="a08a0-133">`HTMLFragment` プロパティを `true` にして SOAP を使用して表示すると、画像の正しい要求に使用できるセッション情報が入った URL が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-133">Rendering using SOAP with the `HTMLFragment` property set to `true` creates URLs containing session information that can be used to properly request images.</span></span> <span data-ttu-id="a08a0-134">画像はレポート サーバー データベースのアップロードされたリソースである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a08a0-134">The images must be uploaded resources in the report server database.</span></span>|  
|`ImageConsolidation`|<span data-ttu-id="a08a0-135">表示するグラフ、マップ、ゲージ、およびインジケーターの画像を 1 つの大きな画像に結合するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-135">Indicates whether to consolidate the rendered chart, map, gauge, and indicator images into one large image.</span></span> <span data-ttu-id="a08a0-136">レポートに多数のデータ視覚化用アイテムが含まれている場合、画像を結合することで、クライアント ブラウザーでのレポートのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-136">The consolidation of images helps improve the performance of the report in the client browser when the report contains many data visualization items.</span></span> <span data-ttu-id="a08a0-137">最近のほとんどのブラウザーでの既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-137">The default value is `true` for most modern browsers.</span></span>|  
|<span data-ttu-id="a08a0-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="a08a0-138">**JavaScript**</span></span>|<span data-ttu-id="a08a0-139">表示レポートで JavaScript がサポートされるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-139">Indicates whether JavaScript is supported in the rendered report.</span></span> <span data-ttu-id="a08a0-140">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-140">The default value is `true`.</span></span>|  
|`LinkTarget`|<span data-ttu-id="a08a0-141">レポートのハイパーリンクの対象。</span><span class="sxs-lookup"><span data-stu-id="a08a0-141">The target for hyperlinks in the report.</span></span> <span data-ttu-id="a08a0-142">ウィンドウまたはフレームを対象にするには、window_name のようにウィンドウの名前を指定する `LinkTarget` = *window_name*か、= _blank を使用して新しいウィンドウを対象にすることができ `LinkTarget` ます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-142">You can target a window or frame by providing the name of the window, like `LinkTarget`=*window_name*, or you can target a new window using `LinkTarget`=_blank.</span></span> <span data-ttu-id="a08a0-143">他に有効な対象名には、_self、_parent、および _top があります。</span><span class="sxs-lookup"><span data-stu-id="a08a0-143">Other valid target names include _self, _parent, and _top.</span></span>|  
|<span data-ttu-id="a08a0-144">**OnlyVisibleStyles ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-144">**OnlyVisibleStyles(\*)**</span></span>|<span data-ttu-id="a08a0-145">現在レンダリングされているページの共有スタイルのみが生成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-145">Indicates that only shared styles for currently rendered page are generated.</span></span>|  
|`OutlookCompat`|<span data-ttu-id="a08a0-146">Outlook でレポートの外観をよくする追加のメタデータを使用して表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-146">Indicates whether to render with extra metadata that makes the report look better in Outlook.</span></span> <span data-ttu-id="a08a0-147">それ以外の場合、既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-147">For others, the default value is `false`.</span></span>|  
|<span data-ttu-id="a08a0-148">**パラメーター**</span><span class="sxs-lookup"><span data-stu-id="a08a0-148">**Parameters**</span></span>|<span data-ttu-id="a08a0-149">ツール バーのパラメーター領域を表示するか非表示にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-149">Indicates whether to show or hide the parameters area of the toolbar.</span></span> <span data-ttu-id="a08a0-150">このパラメーターの値を `true` に設定すると、ツール バーのパラメーター領域が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-150">If you set this parameter to a value of `true`, the parameters area of the toolbar is displayed.</span></span> <span data-ttu-id="a08a0-151">このパラメーターの既定値は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-151">The default value of this parameter is `true`.</span></span>|  
|`PrefixId`|<span data-ttu-id="a08a0-152">`HTMLFragment` と併用する場合、作成された HTML フラグメントのすべての `ID` 属性に指定したプレフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-152">When used with `HTMLFragment`, adds the specified prefix to all `ID` attributes in the HTML fragment that is created.</span></span>|  
|<span data-ttu-id="a08a0-153">**ReplacementRoot ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-153">**ReplacementRoot(\*)**</span></span>|<span data-ttu-id="a08a0-154">ReportViewer コントロールの外部に表示する場合、レポートのすべてのドリルスルー、トグル、およびブックマークのリンクの先頭に追加する文字列。</span><span class="sxs-lookup"><span data-stu-id="a08a0-154">The string to prepend to all drillthrough, toggle, and bookmark links in the report when rendered outside of the ReportViewer control.</span></span> <span data-ttu-id="a08a0-155">たとえば、ユーザーのクリックをカスタム ページにリダイレクトするために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-155">For example, this is used for redirecting a user's click to a custom page.</span></span>|  
|<span data-ttu-id="a08a0-156">**ResourceStreamRoot ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-156">**ResourceStreamRoot(\*)**</span></span>|<span data-ttu-id="a08a0-157">切り替えや並べ替え用の画像など、すべての画像リソースの URL の先頭に追加する文字列。</span><span class="sxs-lookup"><span data-stu-id="a08a0-157">The string to prepend to the URL for all image resources, such as images for toggle or sort.</span></span>|  
|<span data-ttu-id="a08a0-158">**セクション**</span><span class="sxs-lookup"><span data-stu-id="a08a0-158">**Section**</span></span>|<span data-ttu-id="a08a0-159">表示するレポートのページ番号。</span><span class="sxs-lookup"><span data-stu-id="a08a0-159">The page number of the report to render.</span></span> <span data-ttu-id="a08a0-160">`0` の値は、レポートのすべてのセクションが表示されることを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-160">A value of `0` indicates that all sections of the report are rendered.</span></span> <span data-ttu-id="a08a0-161">既定値は `1` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-161">The default value is `1`.</span></span>|  
|<span data-ttu-id="a08a0-162">**StreamRoot (\*)**</span><span class="sxs-lookup"><span data-stu-id="a08a0-162">**StreamRoot (\*)**</span></span>|<span data-ttu-id="a08a0-163">レポート サーバーが返す HTML レポートで IMG 要素の **src** 属性の値の前に付けるパス。</span><span class="sxs-lookup"><span data-stu-id="a08a0-163">The path used for prefixing the value of the **src** attribute of the IMG element in the HTML report returned by the report server.</span></span> <span data-ttu-id="a08a0-164">既定では、レポート サーバーがパスを提供します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-164">By default, the report server provides the path.</span></span> <span data-ttu-id="a08a0-165">この設定を使用して、レポート内の画像のルートパスを指定できます (たとえば、 **http:// \<servername> /企業イメージ**)。</span><span class="sxs-lookup"><span data-stu-id="a08a0-165">You can use this setting to specify a root path for the images in a report (for example, **http://\<servername>/resources/companyimages**).</span></span>|  
|<span data-ttu-id="a08a0-166">**StyleStream**</span><span class="sxs-lookup"><span data-stu-id="a08a0-166">**StyleStream**</span></span>|<span data-ttu-id="a08a0-167">スタイルとスクリプトがドキュメント内ではなく、異なるストリームとして作成されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-167">Indicates whether styles and scripts are created as a separate stream instead of in the document.</span></span> <span data-ttu-id="a08a0-168">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-168">The default value is `false`.</span></span>|  
|`Toolbar`|<span data-ttu-id="a08a0-169">ツール バーを表示するか非表示にするかを示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-169">Indicates whether to show or hide the toolbar.</span></span> <span data-ttu-id="a08a0-170">このパラメーターの既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-170">The default of this parameter is `true`.</span></span> <span data-ttu-id="a08a0-171">このパラメーターの値が `false` である場合は、残りのオプション (ドキュメント マップを除く) すべてが無視されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-171">If the value of this parameter is `false`, all remaining options (except the document map) are ignored.</span></span> <span data-ttu-id="a08a0-172">このパラメーターを省略すると、サポートされている表示形式でツール バーが自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-172">If you omit this parameter, the toolbar is automatically displayed for rendering formats that support it.</span></span><br /><br /> <span data-ttu-id="a08a0-173">URL アクセスを使用してレポートを表示すると、レポート ビューアー ツール バーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-173">The Report Viewer toolbar is rendered when you use URL access to render a report.</span></span> <span data-ttu-id="a08a0-174">ツール バーは SOAP API によっては表示されません。</span><span class="sxs-lookup"><span data-stu-id="a08a0-174">The toolbar is not rendered through the SOAP API.</span></span> <span data-ttu-id="a08a0-175">しかし、`Toolbar` デバイス情報設定は、SOAP の `Render` メソッドを使用したときにレポートの表示に反映されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-175">However, the `Toolbar` device information setting affects the way that the report is displayed when using the SOAP `Render` method.</span></span> <span data-ttu-id="a08a0-176">SOAP を使用して HTML を表示するときにこのパラメーターの値が `true` である場合、レポートの最初のセクションのみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-176">If the value of this parameter is `true` when using SOAP to render to HTML, only the first section of the report is rendered.</span></span> <span data-ttu-id="a08a0-177">値が `false` である場合、HTML レポート全体が単一の HTML ページとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-177">If the value is `false`, the entire HTML report is rendered as a single HTML page.</span></span>|  
|`UserAgent`|<span data-ttu-id="a08a0-178">要求元ブラウザーの `user-agent` 文字列。HTTP 要求に含まれています。</span><span class="sxs-lookup"><span data-stu-id="a08a0-178">The `user-agent` string of the browser that is making the request, which is found in the HTTP request.</span></span>|  
|<span data-ttu-id="a08a0-179">**Zoom ( \* )**</span><span class="sxs-lookup"><span data-stu-id="a08a0-179">**Zoom (\*)**</span></span>|<span data-ttu-id="a08a0-180">整数のパーセンテージまたは文字列定数としてのレポート ズーム値。</span><span class="sxs-lookup"><span data-stu-id="a08a0-180">The report zoom value as an integer percentage or a string constant.</span></span> <span data-ttu-id="a08a0-181">標準的な文字列値には `Page Width` と `Whole Page` などがあります。</span><span class="sxs-lookup"><span data-stu-id="a08a0-181">Standard string values include `Page Width` and `Whole Page`.</span></span> <span data-ttu-id="a08a0-182">Internet Explorer 5.0 よりも前の [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer および[!INCLUDE[msCoName](../includes/msconame-md.md)] 以外のすべてのブラウザーでは、このパラメーターが無視されます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-182">This parameter is ignored by versions of [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer earlier than Internet Explorer 5.0 and all non-[!INCLUDE[msCoName](../includes/msconame-md.md)] browsers.</span></span> <span data-ttu-id="a08a0-183">このパラメーターの既定値は、`100` です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-183">The default value of this parameter is `100`.</span></span>|  
|<span data-ttu-id="a08a0-184">**DataVisualizationFitSizing**</span><span class="sxs-lookup"><span data-stu-id="a08a0-184">**DataVisualizationFitSizing**</span></span>|<span data-ttu-id="a08a0-185">Tablix 内でのデータの視覚エフェクトの調整動作を示します。</span><span class="sxs-lookup"><span data-stu-id="a08a0-185">Indicates data visualization fit behavior when inside a tablix.</span></span> <span data-ttu-id="a08a0-186">これには、グラフ、ゲージ、およびマップが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a08a0-186">This includes chart, gauge, and map.</span></span><br /><br /> <span data-ttu-id="a08a0-187">有効な値は、 **Approximate** および **Exact**です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-187">The possible values are **Approximate** and **Exact**.</span></span><br /><br /> <span data-ttu-id="a08a0-188">既定値は **Approximate**です。</span><span class="sxs-lookup"><span data-stu-id="a08a0-188">The default value is **Approximate**.</span></span> <span data-ttu-id="a08a0-189">この設定を **rsreportserver.config** ファイルから削除すると、既定の動作は **Exact**になります。</span><span class="sxs-lookup"><span data-stu-id="a08a0-189">If the setting is removed from the **rsreportserver.config** file then the default behavior is **Exact**.</span></span><br /><br /> <span data-ttu-id="a08a0-190">**Exact** を有効にした場合は、正確なサイズを特定する処理に時間がかかることがあるため、パフォーマンスに影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a08a0-190">Enabling **Exact** may have performance impact because the processing to determine the exact size may take longer.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a08a0-191">参照</span><span class="sxs-lookup"><span data-stu-id="a08a0-191">See Also</span></span>  
 <span data-ttu-id="a08a0-192">[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="a08a0-192">[Passing Device Information Settings to Rendering Extensions](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md) </span></span>  
 <span data-ttu-id="a08a0-193">[RSReportServer.Configで表示拡張機能パラメーターをカスタマイズする](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="a08a0-193">[Customize Rendering Extension Parameters in RSReportServer.Config](customize-rendering-extension-parameters-in-rsreportserver-config.md) </span></span>  
 [<span data-ttu-id="a08a0-194">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="a08a0-194">Technical Reference &#40;SSRS&#41;</span></span>](../../2014/reporting-services/technical-reference-ssrs.md)  
  
  