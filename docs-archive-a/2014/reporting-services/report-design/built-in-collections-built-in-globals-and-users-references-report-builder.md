---
title: 組み込み Globals および Users 参照 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5f5e1149-c967-454d-9a63-18ec4a33d985
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8ada59244c2b1c49bc0be6f679b8eb4affc487ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644342"
---
# <a name="built-in-globals-and-users-references-report-builder-and-ssrs"></a><span data-ttu-id="97d81-102">組み込み Globals および Users 参照 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="97d81-102">Built-in Globals and Users References (Report Builder and SSRS)</span></span>
  <span data-ttu-id="97d81-103">組み込みフィールドのコレクションには、レポートの処理時に Reporting Services によって提供されるグローバルな値を表す `Globals` コレクションと `User` コレクションの両方が含まれています。</span><span class="sxs-lookup"><span data-stu-id="97d81-103">The Built-in fields collection, which includes both the `Globals` and the `User` collections, represent global values provided by Reporting Services when a report is processed.</span></span> <span data-ttu-id="97d81-104">`Globals` コレクションでは、レポート名、レポート処理の開始時刻、レポート ヘッダーまたはレポート フッターの現在のページ番号などの値が提供されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-104">The `Globals` collection provides values such as the name of the report, the time when report processing began, and current page numbers for the report header or footer.</span></span> <span data-ttu-id="97d81-105">`User` コレクションでは、ユーザー ID と言語設定が提供されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-105">The `User` collection provides the user identifier and language settings.</span></span> <span data-ttu-id="97d81-106">これらの値は、レポート内の結果をフィルター処理する際に式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-106">These values can be used in expressions to filter results in a report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="using-the-globals-collection"></a><span data-ttu-id="97d81-107">Globals コレクションの使用</span><span class="sxs-lookup"><span data-stu-id="97d81-107">Using the Globals Collection</span></span>  
 <span data-ttu-id="97d81-108">`Globals` コレクションには、レポートのグローバル変数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-108">The `Globals` collection contains the global variables for the report.</span></span> <span data-ttu-id="97d81-109">デザイン画面では、これらの変数は、`[&ReportName]` など、先頭に & (アンパサンド) が付いた状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-109">On the design surface, these variables appear prefixed by an & (ampersand), for example, `[&ReportName]`.</span></span> <span data-ttu-id="97d81-110">次の表では、`Globals` コレクションのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="97d81-110">The following table describes the members of the `Globals` collection.</span></span>  
  
|<span data-ttu-id="97d81-111">**メンバー**</span><span class="sxs-lookup"><span data-stu-id="97d81-111">**Member**</span></span>|<span data-ttu-id="97d81-112">**Type**</span><span class="sxs-lookup"><span data-stu-id="97d81-112">**Type**</span></span>|<span data-ttu-id="97d81-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="97d81-113">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|<span data-ttu-id="97d81-114">ExecutionTime</span><span class="sxs-lookup"><span data-stu-id="97d81-114">ExecutionTime</span></span>|`DateTime`|<span data-ttu-id="97d81-115">レポートの実行を開始した日付と時刻です。</span><span class="sxs-lookup"><span data-stu-id="97d81-115">The date and time that the report began to run.</span></span>|  
|<span data-ttu-id="97d81-116">PageNumber</span><span class="sxs-lookup"><span data-stu-id="97d81-116">PageNumber</span></span>|`Integer`|<span data-ttu-id="97d81-117">ページ番号をリセットした改ページを基準とする現在のページ番号です。</span><span class="sxs-lookup"><span data-stu-id="97d81-117">The current page number relative to page breaks that reset the page number.</span></span> <span data-ttu-id="97d81-118">レポート処理の開始時、初期値は 1 に設定されています。</span><span class="sxs-lookup"><span data-stu-id="97d81-118">At the beginning of report processing, the initial value is set to 1.</span></span> <span data-ttu-id="97d81-119">ページ番号は、表示されるページごとに増えます。</span><span class="sxs-lookup"><span data-stu-id="97d81-119">The page number increments for each rendered page.</span></span><br /><br /> <span data-ttu-id="97d81-120">四角形、データ領域、データ領域グループ、またはマップの改ページ内のページ数を指定するには、[改ページ] プロパティの値をに設定し `True` ます。</span><span class="sxs-lookup"><span data-stu-id="97d81-120">To number pages within page breaks for a rectangle, a data region, a data region group, or a map, on the PageBreak property, set the ResetPageNumber property to `True`.</span></span> <span data-ttu-id="97d81-121">Tablix 列階層グループではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="97d81-121">Not supported on tablix column hierarchy groups.</span></span><br /><br /> <span data-ttu-id="97d81-122">PageNumber は、ページ ヘッダーまたはページ フッターの式でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-122">PageNumber can only be used in an expression in a page header or page footer.</span></span>|  
|<span data-ttu-id="97d81-123">ReportFolder</span><span class="sxs-lookup"><span data-stu-id="97d81-123">ReportFolder</span></span>|`String`|<span data-ttu-id="97d81-124">レポートを含んでいるフォルダーへの完全なパスです。</span><span class="sxs-lookup"><span data-stu-id="97d81-124">The full path to the folder containing the report.</span></span> <span data-ttu-id="97d81-125">これには、レポート サーバーの URL は含まれません。</span><span class="sxs-lookup"><span data-stu-id="97d81-125">This does not include the report server URL.</span></span>|  
|<span data-ttu-id="97d81-126">ReportName</span><span class="sxs-lookup"><span data-stu-id="97d81-126">ReportName</span></span>|`String`|<span data-ttu-id="97d81-127">レポート サーバー データベースに格納されているとおりのレポートの名前です。</span><span class="sxs-lookup"><span data-stu-id="97d81-127">The name of the report as it is stored in the report server database.</span></span>|  
|<span data-ttu-id="97d81-128">ReportServerUrl</span><span class="sxs-lookup"><span data-stu-id="97d81-128">ReportServerUrl</span></span>|`String`|<span data-ttu-id="97d81-129">レポートが実行されるレポート サーバーの URL です。</span><span class="sxs-lookup"><span data-stu-id="97d81-129">The URL of the report server on which the report is being run.</span></span>|  
|<span data-ttu-id="97d81-130">TotalPages</span><span class="sxs-lookup"><span data-stu-id="97d81-130">TotalPages</span></span>|`Integer`|<span data-ttu-id="97d81-131">PageNumber をリセットした改ページを基準とする合計ページ数です。</span><span class="sxs-lookup"><span data-stu-id="97d81-131">The total number of pages relative to page breaks that reset PageNumber.</span></span> <span data-ttu-id="97d81-132">改ページを設定しない場合、この値は OverallTotalPages と同じです。</span><span class="sxs-lookup"><span data-stu-id="97d81-132">If no page breaks are set, this value is the same as OverallTotalPages.</span></span><br /><br /> <span data-ttu-id="97d81-133">TotalPages は、ページ ヘッダーまたはページ フッターの式でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-133">TotalPages can only be used in an expression in a page header or page footer.</span></span>|  
|<span data-ttu-id="97d81-134">PageName</span><span class="sxs-lookup"><span data-stu-id="97d81-134">PageName</span></span>|`String`|<span data-ttu-id="97d81-135">ページの名前です。</span><span class="sxs-lookup"><span data-stu-id="97d81-135">The name of the page.</span></span> <span data-ttu-id="97d81-136">レポート処理の開始時、初期値はレポート プロパティの InitialPageName から設定されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-136">At the beginning of report processing, the initial value is set from InitialPageName, a report property.</span></span> <span data-ttu-id="97d81-137">各レポート アイテムが処理されると、この値は四角形、データ領域、データ領域グループ、またはマップの PageName の対応する値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="97d81-137">As each report item is processed, this value is replaced by the corresponding value of PageName from a rectangle, a data region, a data region group, or a map.</span></span> <span data-ttu-id="97d81-138">Tablix 列階層グループではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="97d81-138">Not supported on tablix column hierarchy groups.</span></span><br /><br /> <span data-ttu-id="97d81-139">PageName は、ページ ヘッダーまたはページ フッターの式でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-139">PageName can only be used in an expression in a page header or page footer.</span></span>|  
|<span data-ttu-id="97d81-140">OverallPageNumber</span><span class="sxs-lookup"><span data-stu-id="97d81-140">OverallPageNumber</span></span>|`Integer`|<span data-ttu-id="97d81-141">レポート全体に対する現在のページのページ番号です。</span><span class="sxs-lookup"><span data-stu-id="97d81-141">The page number of the current page for the entire report.</span></span> <span data-ttu-id="97d81-142">この値は ResetPageNumber の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="97d81-142">This value is not affected by ResetPageNumber.</span></span><br /><br /> <span data-ttu-id="97d81-143">OverallPageNumber は、ページ ヘッダーまたはページ フッターの式でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-143">OverallPageNumber can only be used in an expression in a page header or page footer.</span></span>|  
|<span data-ttu-id="97d81-144">OverallTotalPages</span><span class="sxs-lookup"><span data-stu-id="97d81-144">OverallTotalPages</span></span>|`Integer`|<span data-ttu-id="97d81-145">レポート全体の合計ページ数です。</span><span class="sxs-lookup"><span data-stu-id="97d81-145">The total number pages for the entire report.</span></span> <span data-ttu-id="97d81-146">この値は ResetPageNumber の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="97d81-146">This value is not affected by ResetPageNumber.</span></span><br /><br /> <span data-ttu-id="97d81-147">OverallTotalPages は、ページ ヘッダーまたはページ フッターの式でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-147">OverallTotalPages can only be used in an expression in a page header or page footer.</span></span>|  
|<span data-ttu-id="97d81-148">RenderFormat</span><span class="sxs-lookup"><span data-stu-id="97d81-148">RenderFormat</span></span>|`RenderFormat`|<span data-ttu-id="97d81-149">現在の表示要求に関する情報です。</span><span class="sxs-lookup"><span data-stu-id="97d81-149">Information about the current rendering request.</span></span><br /><br /> <span data-ttu-id="97d81-150">詳細については、次のセクションの「RenderFormat」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d81-150">For more information, see "RenderFormat" in the next section.</span></span>|  
  
 <span data-ttu-id="97d81-151">`Globals` コレクションのメンバーからは、Variant 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-151">Members of the `Globals` collection return a variant.</span></span> <span data-ttu-id="97d81-152">特定のデータ型を必要とする、このコレクションのメンバーを式で使用する場合は、先に変数をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d81-152">If you want to use a member of this collection in an expression that requires a specific data type, you must first cast the variable.</span></span> <span data-ttu-id="97d81-153">たとえば、バリアント型の実行時間を Date 形式に変換するには、 `=CDate(Globals!ExecutionTime)`を使用します。</span><span class="sxs-lookup"><span data-stu-id="97d81-153">For example, to convert the execution time variant into a Date format, use `=CDate(Globals!ExecutionTime)`.</span></span> <span data-ttu-id="97d81-154">詳細については、「 [式で使用されるデータ型 (レポート ビルダーおよび SSRS)](expressions-report-builder-and-ssrs.md)など、先頭に &amp; (アンパサンド) が付いた状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-154">For more information, see [Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
### <a name="renderformat"></a><span data-ttu-id="97d81-155">RenderFormat</span><span class="sxs-lookup"><span data-stu-id="97d81-155">RenderFormat</span></span>  
 <span data-ttu-id="97d81-156">次の表では、`RenderFormat` のメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="97d81-156">The following table describes the members for `RenderFormat`.</span></span>  
  
|<span data-ttu-id="97d81-157">メンバー</span><span class="sxs-lookup"><span data-stu-id="97d81-157">Member</span></span>|<span data-ttu-id="97d81-158">種類</span><span class="sxs-lookup"><span data-stu-id="97d81-158">Type</span></span>|<span data-ttu-id="97d81-159">説明</span><span class="sxs-lookup"><span data-stu-id="97d81-159">Description</span></span>|  
|------------|----------|-----------------|  
|<span data-ttu-id="97d81-160">名前</span><span class="sxs-lookup"><span data-stu-id="97d81-160">Name</span></span>|`String`|<span data-ttu-id="97d81-161">RSReportServer 構成ファイルに登録されているレンダラーの名前です。</span><span class="sxs-lookup"><span data-stu-id="97d81-161">The name of the renderer as registered in the RSReportServer configuration file.</span></span><br /><br /> <span data-ttu-id="97d81-162">レポート処理または表示サイクルの特定の部分で使用できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-162">Available during specific parts of the report processing/rendering cycle.</span></span>|  
|<span data-ttu-id="97d81-163">IsInteractive</span><span class="sxs-lookup"><span data-stu-id="97d81-163">IsInteractive</span></span>|`Boolean`|<span data-ttu-id="97d81-164">現在の表示要求で対話型の表示形式を使用するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="97d81-164">Whether the current rendering request uses an interactive rendering format.</span></span>|  
|<span data-ttu-id="97d81-165">DeviceInfo</span><span class="sxs-lookup"><span data-stu-id="97d81-165">DeviceInfo</span></span>|<span data-ttu-id="97d81-166">読み取り専用の名前/値のコレクションです。</span><span class="sxs-lookup"><span data-stu-id="97d81-166">Read-only name/value collection</span></span>|<span data-ttu-id="97d81-167">現在の表示要求の deviceinfo パラメーターのキーと値のペアです。</span><span class="sxs-lookup"><span data-stu-id="97d81-167">Key/value pairs for deviceinfo parameters for the current rendering request.</span></span><br /><br /> <span data-ttu-id="97d81-168">キーまたはインデックスを使用して、コレクションに文字列値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-168">String values can be specified by using either the key or an index into the collection.</span></span>|  
  
### <a name="examples"></a><span data-ttu-id="97d81-169">例</span><span class="sxs-lookup"><span data-stu-id="97d81-169">Examples</span></span>  
 <span data-ttu-id="97d81-170">`Globals` コレクションへの参照を式で使用する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="97d81-170">The following examples show how to use a reference to the `Globals` collection in an expression:</span></span>  
  
-   <span data-ttu-id="97d81-171">レポートのフッター内のテキスト ボックスで次の式を使用すると、ページ番号およびレポートの総ページ数が返されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-171">This expression, placed in a text box in the footer of a report, provides the page number and total pages in the report:</span></span>  
  
     `=Globals.PageNumber & " of " & Globals.TotalPages`  
  
-   <span data-ttu-id="97d81-172">次の式は、レポート名およびレポートが実行された時間を返します。</span><span class="sxs-lookup"><span data-stu-id="97d81-172">This expression provides the name of the report and the time it was run.</span></span> <span data-ttu-id="97d81-173">時刻は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 短い日付の書式設定文字列を使用して書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-173">The time is formatted with the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] formatting string for short date:</span></span>  
  
     `=Globals.ReportName & ", dated " & Format(Globals.ExecutionTime, "d")`  
  
-   <span data-ttu-id="97d81-174">選択した列の **[列表示]** ダイアログ ボックスで次の式を使用すると、レポートが Excel にエクスポートされているときにのみ列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-174">This expression, placed in the **Column Visibility** dialog box for a selected column, displays the column only when the report is exported to Excel.</span></span> <span data-ttu-id="97d81-175">それ以外の場合、列は非表示になります。</span><span class="sxs-lookup"><span data-stu-id="97d81-175">Otherwise, the column is hidden.</span></span>  
  
     <span data-ttu-id="97d81-176">`EXCELOPENXML` は、Office 2007 に含まれる Excel 形式を参照します。</span><span class="sxs-lookup"><span data-stu-id="97d81-176">`EXCELOPENXML` refers to the format of Excel that is included in Office 2007.</span></span> <span data-ttu-id="97d81-177">`EXCEL` は、Office 2003 に含まれる Excel 形式を参照します。</span><span class="sxs-lookup"><span data-stu-id="97d81-177">`EXCEL` refers to the format of Excel that is included in Office 2003.</span></span>  
  
     `=IIF(Globals!RenderFormat.Name = "EXCELOPENXML" OR Globals!RenderFormat.Name = "EXCEL", false, true)`  
  
## <a name="using-the-user-collection"></a><span data-ttu-id="97d81-178">User コレクションの使用</span><span class="sxs-lookup"><span data-stu-id="97d81-178">Using the User Collection</span></span>  
 <span data-ttu-id="97d81-179">`User` コレクションには、レポートを実行しているユーザーのデータが保持されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-179">The `User` collection contains data about the user who is running the report.</span></span> <span data-ttu-id="97d81-180">このコレクションを使用すると、現在のユーザーのデータのみを表示するなど、レポートに表示されるデータをフィルター選択することも、レポート タイトルなどに UserID を表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="97d81-180">You can use this collection to filter the data that appears in a report, for example, showing only the data of the current user, or to display the UserID, for example, in a report title.</span></span> <span data-ttu-id="97d81-181">デザイン画面では、これらの変数は、`[&UserID]` など、先頭に & (アンパサンド) が付いた状態で表示されます。</span><span class="sxs-lookup"><span data-stu-id="97d81-181">On the design surface, these variables appear prefixed by an & (ampersand), for example, `[&UserID]`.</span></span>  
  
 <span data-ttu-id="97d81-182">次の表では、`User` コレクションのメンバーについて説明します。</span><span class="sxs-lookup"><span data-stu-id="97d81-182">The following table describes the members of the `User` collection.</span></span>  
  
|<span data-ttu-id="97d81-183">**Member**</span><span class="sxs-lookup"><span data-stu-id="97d81-183">**Member**</span></span>|<span data-ttu-id="97d81-184">**Type**</span><span class="sxs-lookup"><span data-stu-id="97d81-184">**Type**</span></span>|<span data-ttu-id="97d81-185">**説明**</span><span class="sxs-lookup"><span data-stu-id="97d81-185">**Description**</span></span>|  
|----------------|--------------|---------------------|  
|`Language`|`String`|<span data-ttu-id="97d81-186">レポートを実行しているユーザーの言語です。</span><span class="sxs-lookup"><span data-stu-id="97d81-186">The language of the user running the report.</span></span> <span data-ttu-id="97d81-187">たとえば、「 `en-US` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="97d81-187">For example, `en-US`.</span></span>|  
|`UserID`|`String`|<span data-ttu-id="97d81-188">レポートを実行しているユーザーの ID です。</span><span class="sxs-lookup"><span data-stu-id="97d81-188">The ID of the user running the report.</span></span> <span data-ttu-id="97d81-189">Windows 認証を使用している場合、この値は現在のユーザーのドメイン アカウントです。</span><span class="sxs-lookup"><span data-stu-id="97d81-189">If you are using Windows Authentication, this value is the domain account of the current user.</span></span> <span data-ttu-id="97d81-190">値は、Windows 認証またはカスタム認証を使用できる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] セキュリティ拡張機能によって決まります。</span><span class="sxs-lookup"><span data-stu-id="97d81-190">The value is determined by the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] security extension, which can use Windows Authentication or custom authentication.</span></span>|  
  
 <span data-ttu-id="97d81-191">レポートにおける複数言語のサポートの詳細については、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SQL Server オンライン ブック [にある](https://go.microsoft.com/fwlink/?LinkId=120955)のマニュアルの「多言語配置やグローバル配置のソリューション設計に関する考慮事項」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d81-191">For more information about supporting multiple languages in a report, see "Solution Design Considerations for Multi-Lingual or Global Deployments" in the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] documentation in [SQL Server Books Online](https://go.microsoft.com/fwlink/?LinkId=120955).</span></span>  
  
### <a name="using-locale-settings"></a><span data-ttu-id="97d81-192">ロケール設定の使用</span><span class="sxs-lookup"><span data-stu-id="97d81-192">Using Locale Settings</span></span>  
 <span data-ttu-id="97d81-193">式を使用し、`User.Language` 値でクライアント コンピューターのロケール設定を参照して、ユーザーに対してどのようにレポートを表示するかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-193">You can use expressions to refer to the locale settings on a client computer through the `User.Language` value to determine how a report appears to the user.</span></span> <span data-ttu-id="97d81-194">たとえば、ロケール値に基づいて異なるクエリ式を使用するレポートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-194">For example, you can create a report that uses a different query expression based on the locale value.</span></span> <span data-ttu-id="97d81-195">クエリは、返された言語に応じて異なる列からローカライズされた情報を取得するように変更できます。</span><span class="sxs-lookup"><span data-stu-id="97d81-195">The query may change to retrieve localized information from a different column depending on the language returned.</span></span> <span data-ttu-id="97d81-196">また、この変数を基にしてレポートまたはレポート アイテムの言語設定に式を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="97d81-196">You can also use an expression in the language settings of the report or report items based on this variable.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="97d81-197">レポートの言語設定は変更できますが、言語設定の変更により、表示に関する問題が発生する可能性があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="97d81-197">While you can change the language settings of a report, you must be careful about any display issues this may cause.</span></span> <span data-ttu-id="97d81-198">たとえば、レポートのロケール設定を変更すると、レポートの日付の書式が変更されますが、通貨の書式も変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97d81-198">For example, changing the locale setting of the report can change the date format in the report, but it can also change the currency format.</span></span> <span data-ttu-id="97d81-199">通貨用の変換処理が行われない場合は、これによりレポートに不適切な通貨記号が表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97d81-199">Unless there is a conversion process for the currency, this may cause the incorrect currency symbol to be displayed in the report.</span></span> <span data-ttu-id="97d81-200">これを回避するには、変更する各アイテムに関する言語情報を設定するか、通貨データを含むアイテムに特定の言語を設定します。</span><span class="sxs-lookup"><span data-stu-id="97d81-200">To avoid this, set the language information about the individual items that you want to change, or set the item with the currency data to a specific language.</span></span>  
  
### <a name="identifying-userid-for-snapshot-or-history-reports"></a><span data-ttu-id="97d81-201">スナップショット レポートまたは履歴レポートの UserID の識別</span><span class="sxs-lookup"><span data-stu-id="97d81-201">Identifying UserID for Snapshot or History Reports</span></span>  
 <span data-ttu-id="97d81-202">場合によっては、 *User!UserID* 変数を含むレポートは、レポートを参照している現在のユーザー固有のレポート データを表示することができません。</span><span class="sxs-lookup"><span data-stu-id="97d81-202">In some cases, reports that include the *User!UserID* variable will fail to show report data that is specific to the current user who is viewing the report.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d81-203">参照</span><span class="sxs-lookup"><span data-stu-id="97d81-203">See Also</span></span>  
 <span data-ttu-id="97d81-204">[式 &#40;レポート ビルダーおよび SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97d81-204">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97d81-205">[[式] ダイアログボックス &#40;レポートビルダー&#41;](../expression-dialog-box-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="97d81-205">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md) </span></span>  
 <span data-ttu-id="97d81-206">[式に含まれるデータ型 &#40;レポートビルダーと SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97d81-206">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="97d81-207">[&#40;レポートビルダーと SSRS&#41;の数値と日付の書式設定](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="97d81-207">[Formatting Numbers and Dates &#40;Report Builder and SSRS&#41;](formatting-numbers-and-dates-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="97d81-208">式の例 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="97d81-208">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  