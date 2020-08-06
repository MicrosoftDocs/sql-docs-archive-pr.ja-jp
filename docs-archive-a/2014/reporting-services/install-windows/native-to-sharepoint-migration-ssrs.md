---
title: ネイティブ モードから SharePoint モードへの移行 (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: c5b15bec-6fde-4174-bcde-d043307244dd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2377a3cb8c267c083cec6985f57fa07a734f875f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742953"
---
# <a name="native-to-sharepoint-migration-ssrs"></a><span data-ttu-id="95736-102">ネイティブ モードから SharePoint モードへの移行 (SSRS)</span><span class="sxs-lookup"><span data-stu-id="95736-102">Native to SharePoint Migration (SSRS)</span></span>
  <span data-ttu-id="95736-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のサーバー モードを別のモードにアップグレードまたは変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="95736-103">You cannot upgrade or convert from one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] server mode to another.</span></span> <span data-ttu-id="95736-104">たとえば、ネイティブ モードのレポート サーバーを SharePoint モードにアップグレードまたは変換することはできません。</span><span class="sxs-lookup"><span data-stu-id="95736-104">For example, you cannot upgrade or convert a Native mode report server to SharePoint mode.</span></span> <span data-ttu-id="95736-105">モードが異なると使用されるデータベース スキーマも異なるため、モード間でレポート サーバー データベースをコピーすることはできません。</span><span class="sxs-lookup"><span data-stu-id="95736-105">You cannot copy the report server databases between modes because they use different database schemas.</span></span> <span data-ttu-id="95736-106">コンテンツはレポート サーバー間で移行できます。</span><span class="sxs-lookup"><span data-stu-id="95736-106">You can migrate the content from one report server to another.</span></span> <span data-ttu-id="95736-107">使用するツールは、移行元サーバーと移行先サーバーに対して構成されたレポート サーバー モードの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="95736-107">The tools you use depend on the type of report server mode that is configured for the source and destination servers.</span></span>  
  
 <span data-ttu-id="95736-108">**[!INCLUDE[applies](../../includes/applies-md.md)]** [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ネイティブ モード | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint モード</span><span class="sxs-lookup"><span data-stu-id="95736-108">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Native mode | [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>  
  
##  <a name="reporting-services-migration-tool"></a><a name="bkmk_native_to_sharepoint"></a> <span data-ttu-id="95736-109">Reporting Services 移行ツール</span><span class="sxs-lookup"><span data-stu-id="95736-109">Reporting Services Migration tool</span></span>  
 <span data-ttu-id="95736-110">このツールでは、ネイティブ モードの配置から SharePoint モードの配置へのコンテンツの移行がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="95736-110">The tool supports content migration from a native mode Deployment to a SharePoint mode deployment.</span></span> <span data-ttu-id="95736-111">SharePoint モードから SharePoint モードまたは SharePoint モードからネイティブ モードへの移行はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="95736-111">The tool does not support migration from SharePoint mode to SharePoint mode or from SharePoint mode to Native mode.</span></span>  
  
 <span data-ttu-id="95736-112">詳細については、「[Reporting Services 移行ツール](https://www.microsoft.com/download/details.aspx?id=29560)」(https://www.microsoft.com/download/details.aspx?id=29560) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95736-112">For more information, see [Reporting Services Migration Tool](https://www.microsoft.com/download/details.aspx?id=29560) (https://www.microsoft.com/download/details.aspx?id=29560).</span></span>  
  
## <a name="use-script-to-migrate-content"></a><span data-ttu-id="95736-113">スクリプトを使用したコンテンツの移行</span><span class="sxs-lookup"><span data-stu-id="95736-113">Use Script to migrate content</span></span>  
 <span data-ttu-id="95736-114">移行ツールが目的に合わない場合は、レポート サーバー データを手動で移行できます。</span><span class="sxs-lookup"><span data-stu-id="95736-114">If the migration tool does not meet your needs, you can manually migrate the report server data.</span></span> <span data-ttu-id="95736-115">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 間でのレポート アイテムの移行を完了するための手順の概要を次に示します。</span><span class="sxs-lookup"><span data-stu-id="95736-115">The following is a summary of the steps to complete to migrate report items from a one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] deployment ot another.</span></span> <span data-ttu-id="95736-116">この方法では、移行元サーバーまたは移行先サーバーとしてネイティブ モードまたは SharePoint モードをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="95736-116">The approach supports either Native or SharePoint mode as the source or destination servers.</span></span>  
  
1.  <span data-ttu-id="95736-117">暗号化キーをバックアップおよび復元します。</span><span class="sxs-lookup"><span data-stu-id="95736-117">Backup and restore encryption keys.</span></span> <span data-ttu-id="95736-118">これは、データの暗号化に使用されるキーです。</span><span class="sxs-lookup"><span data-stu-id="95736-118">This is the key that is used to encrypt data.</span></span> <span data-ttu-id="95736-119">暗号化キーは、パスワード (データ ソース接続用に保存されているパスワードなど) を暗号化するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="95736-119">The encryption key is also used to encrypt passwords such as the passwords stored for data source connections.</span></span> <span data-ttu-id="95736-120">ただし、パスワードを移行することはできないため、移行先の環境で再度入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="95736-120">However, passwords cannot be migrated and you will need to enter them again in the destination environment.</span></span>  
  
2.  <span data-ttu-id="95736-121">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] RSS スクリプト:** レポート サーバー Web サービスの SOAP メソッドを呼び出してデータベース間でデータをコピーする Visual Basic スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="95736-121">**[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] RSS scripts:** Write a Visual Basic script that calls Report Server Web service SOAP methods to copy data between databases.</span></span> <span data-ttu-id="95736-122">スクリプトを実行するには、 **RS.exe** ユーティリティを使用します。</span><span class="sxs-lookup"><span data-stu-id="95736-122">Use the **RS.exe** utility to run the script.</span></span> <span data-ttu-id="95736-123">RS.exe は [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]と共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="95736-123">Rs.exe is installed with [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].</span></span>  
  
    -   <span data-ttu-id="95736-124">[サンプル Reporting Services rs.exe レポートサーバー間でコンテンツを移行するためのスクリプト](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)です。</span><span class="sxs-lookup"><span data-stu-id="95736-124">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](../tools/sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span> <span data-ttu-id="95736-125">このトピックでは、CodePlex からダウンロードできるサンプル スクリプトの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="95736-125">The topics explains how to use the sample script you can download from CodePlex.</span></span>  
  
    -   <span data-ttu-id="95736-126">CodePlex にあるサンプル RSS スクリプト ( [レポート サーバー間でコンテンツを移行する Reporting Services RS.exe スクリプト](https://azuresql.codeplex.com/releases/view/115207))。</span><span class="sxs-lookup"><span data-stu-id="95736-126">The sample rss script on CodePlex, [Reporting Services RS.exe script that migrates content from one report server to another](https://azuresql.codeplex.com/releases/view/115207)</span></span>  
  
    -   [<span data-ttu-id="95736-127">Reporting Services を使ったスクリプトの作成と PowerShell</span><span class="sxs-lookup"><span data-stu-id="95736-127">Scripting and PowerShell with Reporting Services</span></span>](../tools/scripting-and-powershell-with-reporting-services.md)  
  
 <span data-ttu-id="95736-128">次の表は、スクリプトを使用して移行できる [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] オブジェクトをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="95736-128">The following table summarizes the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] objects you can migrate with scripts:</span></span>  
  
|<span data-ttu-id="95736-129">Object</span><span class="sxs-lookup"><span data-stu-id="95736-129">Object</span></span>|<span data-ttu-id="95736-130">スクリプト化の可否</span><span class="sxs-lookup"><span data-stu-id="95736-130">Can be Scripted</span></span>|<span data-ttu-id="95736-131">説明</span><span class="sxs-lookup"><span data-stu-id="95736-131">Comments</span></span>|  
|------------|---------------------|--------------|  
|<span data-ttu-id="95736-132">Reports</span><span class="sxs-lookup"><span data-stu-id="95736-132">Reports</span></span>|<span data-ttu-id="95736-133">はい</span><span class="sxs-lookup"><span data-stu-id="95736-133">Yes</span></span>|<span data-ttu-id="95736-134">移行後にデータソースのパスワードを再入力します。</span><span class="sxs-lookup"><span data-stu-id="95736-134">Following migration, to re-enter passwords for datasources.</span></span>|  
|<span data-ttu-id="95736-135">データソース</span><span class="sxs-lookup"><span data-stu-id="95736-135">Datasources</span></span>|<span data-ttu-id="95736-136">はい</span><span class="sxs-lookup"><span data-stu-id="95736-136">Yes</span></span>|<span data-ttu-id="95736-137">移行後にレポートとデータソースとの間のリンクを再設定します。</span><span class="sxs-lookup"><span data-stu-id="95736-137">Following migration, Re-link reports to datasources.</span></span>|  
|<span data-ttu-id="95736-138">モデル</span><span class="sxs-lookup"><span data-stu-id="95736-138">Models</span></span>|<span data-ttu-id="95736-139">はい</span><span class="sxs-lookup"><span data-stu-id="95736-139">Yes</span></span>||  
|<span data-ttu-id="95736-140">データセット</span><span class="sxs-lookup"><span data-stu-id="95736-140">Datasets</span></span>|<span data-ttu-id="95736-141">はい</span><span class="sxs-lookup"><span data-stu-id="95736-141">Yes</span></span>||  
|<span data-ttu-id="95736-142">レポート パーツ</span><span class="sxs-lookup"><span data-stu-id="95736-142">Report Parts</span></span>||<span data-ttu-id="95736-143">移行後にレポート パーツへのパスを確認または更新します。</span><span class="sxs-lookup"><span data-stu-id="95736-143">Following migration, verify or update the path to the report parts.</span></span>|  
|<span data-ttu-id="95736-144">スケジュール</span><span class="sxs-lookup"><span data-stu-id="95736-144">Schedules</span></span>|<span data-ttu-id="95736-145">はい</span><span class="sxs-lookup"><span data-stu-id="95736-145">Yes</span></span>|<span data-ttu-id="95736-146">ListSchedules メソッドに関する説明 (「 [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md)」) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95736-146">See the ListSchedules method [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md)</span></span>|  
|<span data-ttu-id="95736-147">サブスクリプション</span><span class="sxs-lookup"><span data-stu-id="95736-147">Subscriptions</span></span>|<span data-ttu-id="95736-148">はい</span><span class="sxs-lookup"><span data-stu-id="95736-148">yes</span></span>|<span data-ttu-id="95736-149">サブスクリプションの一覧表示メソッドの[サブスクリプションおよび配信方法](../report-server-web-service/methods/subscription-and-delivery-methods.md)と ChangeSubscriptionOwner メソッドを参照してください。<xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span><span class="sxs-lookup"><span data-stu-id="95736-149">See the List Subscriptions method [Subscription and Delivery Methods](../report-server-web-service/methods/subscription-and-delivery-methods.md) and the ChangeSubscriptionOwner method <xref:ReportService2010.ReportingService2010.ChangeSubscriptionOwner%2A></span></span>|  
|<span data-ttu-id="95736-150">スナップショット</span><span class="sxs-lookup"><span data-stu-id="95736-150">Snapshots</span></span>|||  
||||  
  