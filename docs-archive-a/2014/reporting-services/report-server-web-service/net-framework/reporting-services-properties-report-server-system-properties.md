---
title: レポート サーバー システムのプロパティ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- report servers [Reporting Services], properties
- system-specific properties [Reporting Services]
ms.assetid: cd874117-00e5-4ae6-8629-eb9ba9f40478
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f8351417b716de362a993aeac26ac848c0da16de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713793"
---
# <a name="report-server-system-properties"></a><span data-ttu-id="43ecd-102">レポート サーバーのシステム プロパティ</span><span class="sxs-lookup"><span data-stu-id="43ecd-102">Report Server System Properties</span></span>
  <span data-ttu-id="43ecd-103">次のシステム プロパティ名は予約されています。</span><span class="sxs-lookup"><span data-stu-id="43ecd-103">The following system property names are reserved.</span></span> <span data-ttu-id="43ecd-104">同じ名前のユーザー定義プロパティは作成できません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-104">You cannot create user-defined properties of the same name.</span></span> <span data-ttu-id="43ecd-105">Web サービス メソッドを使用すると、これらのプロパティの多くの読み取りや修正ができます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-105">You can read or modify many of these properties using the Web service methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43ecd-106">Properties</span><span class="sxs-lookup"><span data-stu-id="43ecd-106">Properties</span></span>  
  
|<span data-ttu-id="43ecd-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="43ecd-107">Property</span></span>|<span data-ttu-id="43ecd-108">説明</span><span class="sxs-lookup"><span data-stu-id="43ecd-108">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="43ecd-109">SiteName</span><span class="sxs-lookup"><span data-stu-id="43ecd-109">SiteName</span></span>|<span data-ttu-id="43ecd-110">ユーザー インターフェイスに表示されるレポート サーバー サイトの名前。</span><span class="sxs-lookup"><span data-stu-id="43ecd-110">The name of the report server site displayed on the user interface.</span></span> <span data-ttu-id="43ecd-111">既定値は `Microsoft Report Server` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-111">The default value is `Microsoft Report Server`.</span></span> <span data-ttu-id="43ecd-112">このプロパティには空の文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-112">This property can be an empty string.</span></span> <span data-ttu-id="43ecd-113">最大長は 8,000 文字です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-113">The maximum length is 8,000 characters.</span></span>|  
|<span data-ttu-id="43ecd-114">SystemSnapshotLimit</span><span class="sxs-lookup"><span data-stu-id="43ecd-114">SystemSnapshotLimit</span></span>|<span data-ttu-id="43ecd-115">レポートに格納されるスナップショットの最大数。</span><span class="sxs-lookup"><span data-stu-id="43ecd-115">The maximum number of snapshots that are stored for a report.</span></span> <span data-ttu-id="43ecd-116">有効値は `-1` ～ `2`、`147`、`483`、`647` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-116">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="43ecd-117">値が `-1` の場合、スナップショットに制限はありません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-117">If the value is `-1`, there is no snapshot limit.</span></span>|  
|<span data-ttu-id="43ecd-118">SystemReportTimeout</span><span class="sxs-lookup"><span data-stu-id="43ecd-118">SystemReportTimeout</span></span>|<span data-ttu-id="43ecd-119">レポート サーバー名前空間で管理されているすべてのレポートの既定のレポート処理タイムアウト値 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="43ecd-119">The default report processing timeout value, in seconds, for all reports managed in the report server namespace.</span></span> <span data-ttu-id="43ecd-120">この値はレポート レベルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-120">This value can be overridden at the report level.</span></span> <span data-ttu-id="43ecd-121">このプロパティを設定すると、レポート サーバーは指定された時間が経過した後、レポートの処理を停止しようとします。</span><span class="sxs-lookup"><span data-stu-id="43ecd-121">If this property is set, the report server attempts to stop the processing of a report when the specified time has expired.</span></span> <span data-ttu-id="43ecd-122">有効値は `-1` ～ `2`、`147`、`483`、`647` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-122">Valid values are `-1` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="43ecd-123">値に `-1` を設定すると、名前空間内のレポートが処理中にタイムアウトしません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-123">If the value is `-1`, reports in the namespace do not time out during processing.</span></span> <span data-ttu-id="43ecd-124">既定値は `1800` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-124">The default value is `1800`.</span></span>|  
|<span data-ttu-id="43ecd-125">UseSessionCookies</span><span class="sxs-lookup"><span data-stu-id="43ecd-125">UseSessionCookies</span></span>|<span data-ttu-id="43ecd-126">レポート サーバーがクライアント ブラウザーとの通信時にセッションクッキーを使用する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-126">Indicates whether the report server should use session cookies when communicating with client browsers.</span></span> <span data-ttu-id="43ecd-127">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-127">The default value is `true`.</span></span>|  
|<span data-ttu-id="43ecd-128">SessionTimeout</span><span class="sxs-lookup"><span data-stu-id="43ecd-128">SessionTimeout</span></span>|<span data-ttu-id="43ecd-129">セッションがアクティブな状態になっている期間 (秒単位)。</span><span class="sxs-lookup"><span data-stu-id="43ecd-129">The length of time, in seconds, that a session remains active.</span></span> <span data-ttu-id="43ecd-130">既定値は `600` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-130">The default value is `600`.</span></span>|  
|<span data-ttu-id="43ecd-131">EnableMyReports</span><span class="sxs-lookup"><span data-stu-id="43ecd-131">EnableMyReports</span></span>|<span data-ttu-id="43ecd-132">個人用レポート機能が有効になっているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-132">Indicates whether the My Reports feature is enabled.</span></span> <span data-ttu-id="43ecd-133">値 `true` は、機能が有効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-133">A value of `true` indicates that the feature is enabled.</span></span>|  
|<span data-ttu-id="43ecd-134">MyReportsRole</span><span class="sxs-lookup"><span data-stu-id="43ecd-134">MyReportsRole</span></span>|<span data-ttu-id="43ecd-135">ユーザーの個人用レポート フォルダーに、セキュリティ ポリシーを作成する際に使用するロールの名前。</span><span class="sxs-lookup"><span data-stu-id="43ecd-135">The name of the role used when creating security policies on user's My Reports folders.</span></span> <span data-ttu-id="43ecd-136">既定値は `My Reports Role` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-136">The default value is `My Reports Role`.</span></span>|  
|<span data-ttu-id="43ecd-137">EnableExecutionLogging</span><span class="sxs-lookup"><span data-stu-id="43ecd-137">EnableExecutionLogging</span></span>|<span data-ttu-id="43ecd-138">レポート実行のログ記録が有効になっているかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-138">Indicates whether report execution logging is enabled.</span></span> <span data-ttu-id="43ecd-139">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-139">The default value is `true`.</span></span>|  
|<span data-ttu-id="43ecd-140">ExecutionLogDaysKept</span><span class="sxs-lookup"><span data-stu-id="43ecd-140">ExecutionLogDaysKept</span></span>|<span data-ttu-id="43ecd-141">レポート実行情報を実行ログに保持する日数。</span><span class="sxs-lookup"><span data-stu-id="43ecd-141">The number of days to keep report execution information in the execution log.</span></span> <span data-ttu-id="43ecd-142">このプロパティの有効値は `0` ～ `2`、`147`、`483`、`647` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-142">Valid values for this property include `0` through `2`,`147`,`483`,`647`.</span></span> <span data-ttu-id="43ecd-143">値が `0` の場合、エントリは実行ログ テーブルから削除されません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-143">If the value is `0` entries are not deleted from the Execution Log table.</span></span> <span data-ttu-id="43ecd-144">既定値は `60` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-144">The default value is `60`.</span></span>|  
|<span data-ttu-id="43ecd-145">SnapshotCompression</span><span class="sxs-lookup"><span data-stu-id="43ecd-145">SnapshotCompression</span></span>|<span data-ttu-id="43ecd-146">スナップショットの圧縮方法を定義します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-146">Defines how snapshots are compressed.</span></span> <span data-ttu-id="43ecd-147">既定値は `SQL` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-147">The default value is `SQL`.</span></span> <span data-ttu-id="43ecd-148">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="43ecd-148">The valid values are as follows:</span></span><br /><br /> <span data-ttu-id="43ecd-149">`SQL` = スナップショットは、レポート サーバー データベースへの格納時に圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-149">`SQL` = Snapshots are compressed when stored in the report server database.</span></span> <span data-ttu-id="43ecd-150">これは現在の動作です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-150">This is the current behavior.</span></span><br /><br /> <span data-ttu-id="43ecd-151">**なし** = スナップショットは圧縮されません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-151">**None** = Snapshots are not compressed.</span></span><br /><br /> <span data-ttu-id="43ecd-152">`All` = すべてのストレージ オプションのスナップショットが圧縮されます。このオプションには、レポート サーバー データベースやファイル システムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-152">`All` = Snapshots are compressed for all storage options, which include the report server database or the file system.</span></span>|  
|<span data-ttu-id="43ecd-153">EnableClientPrinting</span><span class="sxs-lookup"><span data-stu-id="43ecd-153">EnableClientPrinting</span></span>|<span data-ttu-id="43ecd-154">レポート サーバーからのダウンロードに RSClientPrint ActiveX コントロールが使用可能かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-154">Determines whether the RSClientPrint ActiveX control is available for download from the report server.</span></span> <span data-ttu-id="43ecd-155">有効な値は、 `true` と `false` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-155">The valid values are `true` and `false`.</span></span> <span data-ttu-id="43ecd-156">既定値は `true` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-156">The default value is `true`.</span></span> <span data-ttu-id="43ecd-157">このコントロールに必要な追加設定に関する詳細については、「 [Reporting Services のクライアント側印刷機能の有効化と無効化](../../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43ecd-157">For more information about additional settings that are required for this control, see [Enable and Disable Client-Side Printing for Reporting Services](../../report-server/enable-and-disable-client-side-printing-for-reporting-services.md).</span></span>|  
|<span data-ttu-id="43ecd-158">EnableIntegratedSecurity</span><span class="sxs-lookup"><span data-stu-id="43ecd-158">EnableIntegratedSecurity</span></span>|<span data-ttu-id="43ecd-159">統合セキュリティをレポート データ ソース接続でサポートするかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="43ecd-159">Determines whether integrated security is supported for report data source connections.</span></span> <span data-ttu-id="43ecd-160">既定では、 `True`です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-160">The default is `True`.</span></span> <span data-ttu-id="43ecd-161">有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="43ecd-161">The valid values are as follows:</span></span><br /><br /> <span data-ttu-id="43ecd-162">`True` = 統合セキュリティが有効になります。</span><span class="sxs-lookup"><span data-stu-id="43ecd-162">`True` = Integrated security is enabled.</span></span><br /><br /> <span data-ttu-id="43ecd-163">`False` = 統合セキュリティが有効になりません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-163">`False` = Integrated security is not enabled.</span></span> <span data-ttu-id="43ecd-164">統合セキュリティを使用するように構成されているレポート データ ソースは実行されません。</span><span class="sxs-lookup"><span data-stu-id="43ecd-164">Report data sources that are configured to use integrated security will not run.</span></span>|  
|<span data-ttu-id="43ecd-165">EnableRemoteErrors</span><span class="sxs-lookup"><span data-stu-id="43ecd-165">EnableRemoteErrors</span></span>|<span data-ttu-id="43ecd-166">リモート コンピューターからレポートを要求したユーザーに返されるエラー メッセージに、外部エラー情報 (レポート データ ソースに関するエラー情報など) を含めます。</span><span class="sxs-lookup"><span data-stu-id="43ecd-166">Includes external error information (for example, error information about report data sources) with the error messages that are returned for users who request reports from remote computers.</span></span> <span data-ttu-id="43ecd-167">有効な値は `true` と `false` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-167">Valid values are `true` and `false`.</span></span> <span data-ttu-id="43ecd-168">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="43ecd-168">The default value is `false`.</span></span> <span data-ttu-id="43ecd-169">詳細については、「[リモート エラーの有効化 (Reporting Services)](../../report-server/enable-remote-errors-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="43ecd-169">For more information, see [Enable Remote Errors &#40;Reporting Services&#41;](../../report-server/enable-remote-errors-reporting-services.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43ecd-170">参照</span><span class="sxs-lookup"><span data-stu-id="43ecd-170">See Also</span></span>  
 <xref:ReportService2010.ReportingService2010.GetSystemProperties%2A>   
 <xref:ReportService2010.ReportingService2010.SetSystemProperties%2A>   
 <span data-ttu-id="43ecd-171">[Web サービスと .NET Framework を使用してのアプリケーションの構築](building-applications-using-the-web-service-and-the-net-framework.md) </span><span class="sxs-lookup"><span data-stu-id="43ecd-171">[Building Applications Using the Web Service and the .NET Framework](building-applications-using-the-web-service-and-the-net-framework.md) </span></span>  
 <span data-ttu-id="43ecd-172">[レポート サーバー Web サービス](../report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="43ecd-172">[Report Server Web Service](../report-server-web-service.md) </span></span>  
 [<span data-ttu-id="43ecd-173">テクニカル リファレンス (SSRS)</span><span class="sxs-lookup"><span data-stu-id="43ecd-173">Technical Reference &#40;SSRS&#41;</span></span>](../../technical-reference-ssrs.md)  
  
  