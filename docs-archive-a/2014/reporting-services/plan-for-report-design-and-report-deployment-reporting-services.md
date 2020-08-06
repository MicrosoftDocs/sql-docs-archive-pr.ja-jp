---
title: レポートのデザインとレポートの配置を計画する (Reporting Services 2014) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 1c1e265e-52a2-4de3-96fd-ca4abae01c02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 33e48b88665d08f44414f57067115f62e6946439
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739505"
---
# <a name="plan-for-report-design-and-report-deployment-reporting-services-2014"></a><span data-ttu-id="7d532-102">レポート デザインとレポート配置の計画 (Reporting Services 2014)</span><span class="sxs-lookup"><span data-stu-id="7d532-102">Plan for Report Design and Report Deployment (Reporting Services 2014)</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<span data-ttu-id="7d532-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]には、レポートを作成および配置するためのいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7d532-103">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] provides several approaches for authoring and deploying reports.</span></span> <span data-ttu-id="7d532-104">このトピックは、使用するレポート作成環境とレポート サーバーの組み合わせを計画するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7d532-104">Use this topic to help plan a report authoring environment and report server that work together.</span></span> <span data-ttu-id="7d532-105">このトピックでは、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] のコンポーネントでサポートされているレポート定義の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="7d532-105">This topic is an overview of report definition support by [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] components.</span></span> <span data-ttu-id="7d532-106">レポート定義は、レポート定義言語 (RDL : Report Definition Language) またはクライアント向けレポート定義言語 (RDLC : Report Definition Language for Clients) で記述された XML ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7d532-106">A report definition is an XML file that is written in the Report Definition Language (RDL) or the Report Definition Language for Clients (RDLC).</span></span> <span data-ttu-id="7d532-107">どちらのレポート定義も、そのファイルの冒頭に指定された特定のスキーマ バージョンに準拠しています。</span><span class="sxs-lookup"><span data-stu-id="7d532-107">Each report definition conforms to a specific schema version that is listed at the beginning of the file.</span></span>  
  
 <span data-ttu-id="7d532-108">RDL ファイルは [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダー 3.0 で作成します。</span><span class="sxs-lookup"><span data-stu-id="7d532-108">RDL files are authored in Report Designer in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] projects, and in Report Builder 3.0.</span></span> <span data-ttu-id="7d532-109">RDLC ファイルは、 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]に搭載されている ReportViewer コントロールを使用して作成します。</span><span class="sxs-lookup"><span data-stu-id="7d532-109">RDLC files are authored by using the ReportViewer controls that are included in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="7d532-110">このトピックの内容:</span><span class="sxs-lookup"><span data-stu-id="7d532-110">In this topic:</span></span>  
  
-   [<span data-ttu-id="7d532-111">RDL スキーマのバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-111">RDL Schema Versions</span></span>](#bkmk_rdl_schema_versions)  
  
-   [<span data-ttu-id="7d532-112">レポートサーバーと RDL スキーマのサポート</span><span class="sxs-lookup"><span data-stu-id="7d532-112">Report Server and RDL Schema Support</span></span>](#bkmk_report_server_rdl_schema_support)  
  
-   [<span data-ttu-id="7d532-113">レポートの作成と配置のサポート</span><span class="sxs-lookup"><span data-stu-id="7d532-113">Report Authoring and Deployment Support</span></span>](#bkmk_report_authoring_and_deployment)  
  
-   [<span data-ttu-id="7d532-114">ReportViewer コントロール</span><span class="sxs-lookup"><span data-stu-id="7d532-114">ReportViewer Controls</span></span>](#bkmk_reportviewer)  
  
##  <a name="rdl-schema-versions"></a><a name="bkmk_rdl_schema_versions"></a> <span data-ttu-id="7d532-115">RDL スキーマのバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-115">RDL Schema Versions</span></span>  
 <span data-ttu-id="7d532-116">次の表は、利用できるスキーマ バージョンとその省略形の対応表です。このトピックの説明には、以降、これらの省略形を使用します。</span><span class="sxs-lookup"><span data-stu-id="7d532-116">The following table lists each available schema version and the abbreviation that is used throughout the rest of this topic:</span></span>  
  
|<span data-ttu-id="7d532-117">省略形</span><span class="sxs-lookup"><span data-stu-id="7d532-117">Abbreviation</span></span>|<span data-ttu-id="7d532-118">スキーマ バージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-118">Schema version</span></span>|  
|------------------|--------------------|  
|<span data-ttu-id="7d532-119">2010 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-119">2010 RDL</span></span>|`https://schemas.microsoft.com/sqlserver/reporting/2010/01/reportdefinition`|  
|<span data-ttu-id="7d532-120">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-120">2008 RDL</span></span>|`https://schemas.microsoft.com/sqlserver/reporting/2008/01/reportdefinition`|  
|<span data-ttu-id="7d532-121">2005 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-121">2005 RDL</span></span><br /><br /> <span data-ttu-id="7d532-122">2005 RDLC</span><span class="sxs-lookup"><span data-stu-id="7d532-122">2005 RDLC</span></span>|`https://schemas.microsoft.com/sqlserver/reporting/2005/01/reportdefinition`|  
|<span data-ttu-id="7d532-123">2000 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-123">2000 RDL</span></span>|`https://schemas.microsoft.com/sqlserver/reporting/2003/10/reportdefinition`|  
  
 <span data-ttu-id="7d532-124">RDL と RDL スキーマの詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d532-124">For more information on RDL and RDL schemas, see the following:</span></span>  
  
-   [<span data-ttu-id="7d532-125">Microsoft SQL Server XML スキーマ</span><span class="sxs-lookup"><span data-stu-id="7d532-125">Microsoft SQL Server XML Schemas</span></span>](https://go.microsoft.com/fwlink/?LinkId=31850)  
  
-   [<span data-ttu-id="7d532-126">レポート定義言語の仕様</span><span class="sxs-lookup"><span data-stu-id="7d532-126">Report Definition Language Specifications</span></span>](https://go.microsoft.com/fwlink/?linkid=116865)  
  
-   [<span data-ttu-id="7d532-127">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7d532-127">Report Definition Language &#40;SSRS&#41;</span></span>](reports/report-definition-language-ssrs.md)  
  
 <span data-ttu-id="7d532-128">ReportViewer コントロールの詳細については、「[ReportViewer コントロール (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d532-128">For more information about ReportViewer controls, see [ReportViewer Controls (Visual Studio)](https://msdn.microsoft.com/library/ms251671.aspx).</span></span>  
  
##  <a name="report-server-and-rdl-schema-support"></a><a name="bkmk_report_server_rdl_schema_support"></a> <span data-ttu-id="7d532-129">レポート サーバーと RDL スキーマのサポート</span><span class="sxs-lookup"><span data-stu-id="7d532-129">Report Server and RDL Schema Support</span></span>  
 <span data-ttu-id="7d532-130">レポート定義ファイルは、次の方法で [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポート サーバーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="7d532-130">A report definition file can be deployed to a [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] report server in the following ways:</span></span>  
  
-   <span data-ttu-id="7d532-131">**レポート デザイナー:**[!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)]のレポート デザイナーからレポートを配置する。</span><span class="sxs-lookup"><span data-stu-id="7d532-131">**Report Designer:** Deploy a report from Report Designer in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)].</span></span>  
  
-   <span data-ttu-id="7d532-132">**レポート ビルダー:** レポート ビルダーからレポート サーバーにレポートを保存する。</span><span class="sxs-lookup"><span data-stu-id="7d532-132">**Report Builder:** Save a report to the report server from Report Builder.</span></span>  
  
-   <span data-ttu-id="7d532-133">**レポート マネージャー:** レポート マネージャーからネイティブ モード レポート サーバーにレポートをアップロードする。</span><span class="sxs-lookup"><span data-stu-id="7d532-133">**Report Manager:** Upload a report to a native mode report server from Report Manager.</span></span>  
  
-   <span data-ttu-id="7d532-134">**SharePoint:** SharePoint モード レポート サーバーで構成された SharePoint サイトにレポートをアップロードする。</span><span class="sxs-lookup"><span data-stu-id="7d532-134">**SharePoint:** Upload a report to a SharePoint site that is configured with a SharePoint mode report server.</span></span>  
  
-   <span data-ttu-id="7d532-135">**プログラムから:** プログラムから SOAP API インターフェイスを使用してレポート サーバーにレポートをパブリッシュする。</span><span class="sxs-lookup"><span data-stu-id="7d532-135">**Programmatically:** Programmatically publish a report by using the SOAP API interfaces to a report server.</span></span> <span data-ttu-id="7d532-136">詳細については、「 [Report Server Web Service](report-server-web-service/report-server-web-service.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d532-136">For more information, see [Report Server Web Service](report-server-web-service/report-server-web-service.md).</span></span>  
  
 <span data-ttu-id="7d532-137">次の表は、サポートされる RDL スキーマのバージョンをレポート サーバーのバージョン別に示したものです。</span><span class="sxs-lookup"><span data-stu-id="7d532-137">The following table lists the supported rdl schema version by version of the report server.</span></span>  
  
|<span data-ttu-id="7d532-138">レポート サーバーのバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-138">Report server version</span></span>|<span data-ttu-id="7d532-139">RDL スキーマのバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-139">RDL schema version</span></span>|  
|---------------------------|------------------------|  
|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> <span data-ttu-id="7d532-140">または</span><span class="sxs-lookup"><span data-stu-id="7d532-140">Or</span></span><br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> <span data-ttu-id="7d532-141">または</span><span class="sxs-lookup"><span data-stu-id="7d532-141">Or</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|<span data-ttu-id="7d532-142">2010 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-142">2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-143">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-143">2008 RDL</span></span><br /><br /> <span data-ttu-id="7d532-144">2005 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-144">2005 RDL</span></span><br /><br /> <span data-ttu-id="7d532-145">2000 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-145">2000 RDL</span></span>|  
|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|<span data-ttu-id="7d532-146">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-146">2008 RDL</span></span><br /><br /> <span data-ttu-id="7d532-147">2005 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-147">2005 RDL</span></span><br /><br /> <span data-ttu-id="7d532-148">2000 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-148">2000 RDL</span></span>|  
|[!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)]|<span data-ttu-id="7d532-149">2005 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-149">2005 RDL</span></span><br /><br /> <span data-ttu-id="7d532-150">2000 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-150">2000 RDL</span></span>|  
  
 <span data-ttu-id="7d532-151">レポート定義をレポート サーバーにアップロードするか、既存のレポートが保存されたレポート サーバーをアップグレードすると、レポート定義は元の形式のまま維持されます。</span><span class="sxs-lookup"><span data-stu-id="7d532-151">When you upload a report definition to the report server or upgrade a report server that contains existing reports, the report server preserves the report definition in the original format.</span></span> <span data-ttu-id="7d532-152">レポート サーバー データベース内のレポートは、**初回使用時に**レポート サーバーによってバイナリ形式へとアップグレードされて初めて、閲覧が可能となります。</span><span class="sxs-lookup"><span data-stu-id="7d532-152">**On first use**, the report server upgrades the report in the report server database to a binary format that is preserved for subsequent views.</span></span> <span data-ttu-id="7d532-153">レポート定義 (.rdl) そのものはアップグレードされません。</span><span class="sxs-lookup"><span data-stu-id="7d532-153">The report definition (.rdl) itself is not upgraded.</span></span>  
  
 <span data-ttu-id="7d532-154">レポート サーバーからレポート定義ファイル (.rdl) の読み取り専用コピーを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="7d532-154">You can extract from the report server a read-only copy of the report definition file (.rdl).</span></span> <span data-ttu-id="7d532-155">ネイティブ モード レポート サーバーで、レポート マネージャーを参照し、 **[ダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d532-155">On a native mode report server, browse to report manager, select the report and click **Download**.</span></span> <span data-ttu-id="7d532-156">SharePoint モードの配置で、ドキュメント ライブラリを参照し、レポートを選択して、 **[コピーのダウンロード]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7d532-156">In a SharePoint mode deployment, browse to the document library, select the report and click **Download a Copy**.</span></span>  
  
 <span data-ttu-id="7d532-157">レポート定義をアップグレードするには、アップグレードするレポートをレポート作成環境で開いて保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d532-157">To upgrade the report definition, you must open the report in a report authoring environment and then save it.</span></span>  
  
 <span data-ttu-id="7d532-158">レポートのアップグレードと、サポートされているスキーマ バージョンの詳細については、「 [レポートのアップグレード](install-windows/upgrade-reports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d532-158">For more information about report upgrades and the schema versions that are supported, see [Upgrade Reports](install-windows/upgrade-reports.md).</span></span>  
  
##  <a name="report-authoring-and-deployment-support"></a><a name="bkmk_report_authoring_and_deployment"></a> <span data-ttu-id="7d532-159">レポートの作成と配置のサポート</span><span class="sxs-lookup"><span data-stu-id="7d532-159">Report Authoring and Deployment Support</span></span>  
 <span data-ttu-id="7d532-160">レポート作成環境は [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] のレポート デザイナー、またはレポート ビルダーです。</span><span class="sxs-lookup"><span data-stu-id="7d532-160">Report authoring environments are Report Designer in [!INCLUDE[ss_dtbi](../includes/ss-dtbi-md.md)] projects, and Report Builder.</span></span> <span data-ttu-id="7d532-161">レポート作成環境には、レポートのアップグレード、レポート デザイン、ローカル モードでのレポート プレビュー、レポート サーバーでのレポート プレビュー、レポートの配置など、さまざまな機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7d532-161">Report authoring environments provide a variety of support for report upgrade, report design, report preview in local mode, report preview on the report server, and report deployment.</span></span>  
  
 <span data-ttu-id="7d532-162">次の表は、各種スキーマ バージョンのレポート定義の作成と配置に関するサポート状況をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="7d532-162">The following table summarizes support for authoring and deploying report definitions for different schema versions:</span></span>  
  
|<span data-ttu-id="7d532-163">作成環境</span><span class="sxs-lookup"><span data-stu-id="7d532-163">Authoring environment</span></span>|<span data-ttu-id="7d532-164">作成される RDL バージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-164">RDL version Authored</span></span>|<span data-ttu-id="7d532-165">配置用の RDL バージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-165">Deploy RDL version</span></span>|<span data-ttu-id="7d532-166">配置先レポート サーバーのバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-166">Deploy to report server versions</span></span>|  
|---------------------------|--------------------------|------------------------|--------------------------------------|  
|<span data-ttu-id="7d532-167">SQL Server 2014 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012 (Microsoft ダウンロード センターから入手)</span><span class="sxs-lookup"><span data-stu-id="7d532-167">Report Designer in SQL Server 2014 Data Tools - Business Intelligence for Microsoft Visual Studio 2012, on Microsoft download center.</span></span><br /><br /> <span data-ttu-id="7d532-168">または</span><span class="sxs-lookup"><span data-stu-id="7d532-168">Or</span></span><br /><br /> <span data-ttu-id="7d532-169">SQL Server 2012 Data Tools のレポート デザイナー - Business Intelligence for Microsoft Visual Studio 2012 (Microsoft ダウンロード センターから入手)</span><span class="sxs-lookup"><span data-stu-id="7d532-169">Report Designer in SQL Server 2012 Data Tools - Business Intelligence for Microsoft Visual Studio 2012, on Microsoft download center.</span></span><br /><br /> <span data-ttu-id="7d532-170">または</span><span class="sxs-lookup"><span data-stu-id="7d532-170">Or</span></span><br /><br /> <span data-ttu-id="7d532-171">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools のレポート デザイナーは [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]に含まれています。</span><span class="sxs-lookup"><span data-stu-id="7d532-171">Report Designer in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Data Tools, included in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)].</span></span>|<span data-ttu-id="7d532-172">作成者 2010 RDL。</span><span class="sxs-lookup"><span data-stu-id="7d532-172">Authors 2010 RDL.</span></span> <span data-ttu-id="7d532-173">既存の RDL を開いたとき:</span><span class="sxs-lookup"><span data-stu-id="7d532-173">On open of existing RDL:</span></span><br /><br /> <span data-ttu-id="7d532-174">2000 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-174">2000 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-175">2005 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-175">2005 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-176">2008 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-176">2008 RDL, upgrades to 2010 RDL</span></span>|<span data-ttu-id="7d532-177">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-177">2008 RDL</span></span><br /><br /> <span data-ttu-id="7d532-178">2010 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-178">2010 RDL</span></span>|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]<br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]<br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|<span data-ttu-id="7d532-179">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio のレポート デザイナー</span><span class="sxs-lookup"><span data-stu-id="7d532-179">Report Designer in [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Business Intelligence Development Studio</span></span>|<span data-ttu-id="7d532-180">作成者 2010 RDL。</span><span class="sxs-lookup"><span data-stu-id="7d532-180">Authors 2010 RDL.</span></span> <span data-ttu-id="7d532-181">既存の RDL を開いたとき:</span><span class="sxs-lookup"><span data-stu-id="7d532-181">On open of existing RDL:</span></span><br /><br /> <span data-ttu-id="7d532-182">2000 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-182">2000 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-183">2005 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-183">2005 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-184">2008 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-184">2008 RDL, upgrades to 2010 RDL</span></span>|<span data-ttu-id="7d532-185">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-185">2008 RDL</span></span><br /><br /> <span data-ttu-id="7d532-186">2010 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-186">2010 RDL</span></span>|[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]|  
|<span data-ttu-id="7d532-187">[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio のレポート デザイナー</span><span class="sxs-lookup"><span data-stu-id="7d532-187">Report Designer in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] Business Intelligence Development Studio</span></span>|<span data-ttu-id="7d532-188">作成者 2008 RDL。</span><span class="sxs-lookup"><span data-stu-id="7d532-188">Authors 2008 RDL.</span></span> <span data-ttu-id="7d532-189">既存の RDL を開いたとき:</span><span class="sxs-lookup"><span data-stu-id="7d532-189">On open of existing RDL:</span></span><br /><br /> <span data-ttu-id="7d532-190">2000 RDL、2008 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-190">2000 RDL, upgrades to 2008 RDL</span></span><br /><br /> <span data-ttu-id="7d532-191">2005 RDL、2008 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-191">2005 RDL, upgrades to 2008 RDL</span></span>|<span data-ttu-id="7d532-192">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-192">2008 RDL</span></span>|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]|  
|[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] <span data-ttu-id="7d532-193">レポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="7d532-193">Report Builder</span></span>|<span data-ttu-id="7d532-194">作成者 2010 RDL。</span><span class="sxs-lookup"><span data-stu-id="7d532-194">Authors 2010 RDL.</span></span> <span data-ttu-id="7d532-195">既存の RDL を開いたとき:</span><span class="sxs-lookup"><span data-stu-id="7d532-195">On open of existing RDL:</span></span><br /><br /> <span data-ttu-id="7d532-196">2000 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-196">2000 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-197">2005 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-197">2005 RDL, upgrades to 2010 RDL</span></span><br /><br /> <span data-ttu-id="7d532-198">2008 RDL、2010 RDL にアップグレード</span><span class="sxs-lookup"><span data-stu-id="7d532-198">2008 RDL, upgrades to 2010 RDL</span></span>|<span data-ttu-id="7d532-199">2010 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-199">2010 RDL</span></span>|[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] <span data-ttu-id="7d532-200">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d532-200">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span></span><br /><br /> [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] <span data-ttu-id="7d532-201">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d532-201">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span></span><br /><br /> [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] <span data-ttu-id="7d532-202">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d532-202">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]</span></span>|  
|<span data-ttu-id="7d532-203">Visual Studio の RDLC レポート デザイナー</span><span class="sxs-lookup"><span data-stu-id="7d532-203">Visual Studio RDLC Report Designer Report Designer</span></span>|<span data-ttu-id="7d532-204">2005 RDLC</span><span class="sxs-lookup"><span data-stu-id="7d532-204">2005 RDLC</span></span>|<span data-ttu-id="7d532-205">該当なし</span><span class="sxs-lookup"><span data-stu-id="7d532-205">N/A</span></span>|<span data-ttu-id="7d532-206">該当なし</span><span class="sxs-lookup"><span data-stu-id="7d532-206">N/A</span></span>|  
  
 <span data-ttu-id="7d532-207">[!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)]の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d532-207">For more information on [!INCLUDE[ss_dtbi_vs2013](../includes/ss-dtbi-vs2013-md.md)], see the following:</span></span>  
  
-   [<span data-ttu-id="7d532-208">SQL Server データ ツールの配置およびバージョン サポート (SSRS)</span><span class="sxs-lookup"><span data-stu-id="7d532-208">Deployment and Version Support in SQL Server Data Tools &#40;SSRS&#41;</span></span>](tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
-   <span data-ttu-id="7d532-209">[Microsoft SQL Server Data Tools-Visual Studio 2012 用のビジネスインテリジェンス](https://www.microsoft.com/download/details.aspx?id=36843)。</span><span class="sxs-lookup"><span data-stu-id="7d532-209">[Microsoft SQL Server Data Tools - Business Intelligence for Visual Studio 2012](https://www.microsoft.com/download/details.aspx?id=36843).</span></span>  
  
##  <a name="reportviewer-controls"></a><a name="bkmk_reportviewer"></a><span data-ttu-id="7d532-210">ReportViewer コントロール</span><span class="sxs-lookup"><span data-stu-id="7d532-210">ReportViewer Controls</span></span>  
 <span data-ttu-id="7d532-211">[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] の ReportViewer コントロールは、ローカル プレビュー モードまたはリモート モードで .rdlc レポートを表示できるほか、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーでホストされている .rdl ファイルを表示できます。</span><span class="sxs-lookup"><span data-stu-id="7d532-211">A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ReportViewer control can display an .rdlc report in local preview mode or in remote mode, the control can display an .rdl file hosted on a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="7d532-212">次の表は、ローカル処理 (.rdlc) 用の ReportViewer コントロールでサポートされている RDL バージョンの一覧です。</span><span class="sxs-lookup"><span data-stu-id="7d532-212">The following table provides the list of RDL versions supported by the ReportViewer controls for local processing (.rdlc).</span></span> <span data-ttu-id="7d532-213">サーバー側の RDL のサポートについて、 [レポート サーバーと RDL スキーマのサポート](#bkmk_report_server_rdl_schema_support)にまとめられています。</span><span class="sxs-lookup"><span data-stu-id="7d532-213">Server side RDL support is summarized in the section [Report Server and RDL Schema Support](#bkmk_report_server_rdl_schema_support).</span></span>  
  
|<span data-ttu-id="7d532-214">製品の ReportViewer コントロール</span><span class="sxs-lookup"><span data-stu-id="7d532-214">ReportViewer control in product</span></span>|<span data-ttu-id="7d532-215">ローカル プレビュー用の RDL のバージョン</span><span class="sxs-lookup"><span data-stu-id="7d532-215">Version of RDL for local preview</span></span>|  
|-------------------------------------|--------------------------------------|  
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="7d532-216">2013</span><span class="sxs-lookup"><span data-stu-id="7d532-216">2013</span></span><br /><br /> <span data-ttu-id="7d532-217">または</span><span class="sxs-lookup"><span data-stu-id="7d532-217">Or</span></span><br /><br /> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] <span data-ttu-id="7d532-218">2012</span><span class="sxs-lookup"><span data-stu-id="7d532-218">2012</span></span><br /><br /> <span data-ttu-id="7d532-219">または</span><span class="sxs-lookup"><span data-stu-id="7d532-219">Or</span></span><br /><br /> [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]|<span data-ttu-id="7d532-220">2008 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-220">2008 RDL</span></span>|  
|[!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)]<br /><br /> <span data-ttu-id="7d532-221">または</span><span class="sxs-lookup"><span data-stu-id="7d532-221">Or</span></span><br /><br /> [!INCLUDE[vsOrcas](../includes/vsorcas-md.md)]|<span data-ttu-id="7d532-222">2005 RDL</span><span class="sxs-lookup"><span data-stu-id="7d532-222">2005 RDL</span></span>|  
  
 <span data-ttu-id="7d532-223">詳細については、「</span><span class="sxs-lookup"><span data-stu-id="7d532-223">For more information, see the following:</span></span>  
  
-   [<span data-ttu-id="7d532-224">RDLC ファイルから RDL ファイルへの変換</span><span class="sxs-lookup"><span data-stu-id="7d532-224">Converting RDLC Files to RDL Files</span></span>](https://msdn.microsoft.com/library/ms252109.aspx)  
  
-   [<span data-ttu-id="7d532-225">ReportViewer コントロール (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="7d532-225">ReportViewer Controls (Visual Studio)</span></span>](https://msdn.microsoft.com/library/ms251671.aspx)  
  
-   [<span data-ttu-id="7d532-226">ReportViewer コントロールの追加と構成</span><span class="sxs-lookup"><span data-stu-id="7d532-226">Adding and Configuring the ReportViewer Controls</span></span>](https://msdn.microsoft.com/library/ms252104.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="7d532-227">参照</span><span class="sxs-lookup"><span data-stu-id="7d532-227">See Also</span></span>  
 <span data-ttu-id="7d532-228">[レポート、レポートパーツ、およびレポート定義 &#40;レポートビルダーと SSRS&#41;](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="7d532-228">[Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;](report-design/reports-report-parts-and-report-definitions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="7d532-229">[Reporting Services ツール](tools/reporting-services-tools.md) </span><span class="sxs-lookup"><span data-stu-id="7d532-229">[Reporting Services Tools](tools/reporting-services-tools.md) </span></span>  
 [<span data-ttu-id="7d532-230">レポート定義言語 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="7d532-230">Report Definition Language &#40;SSRS&#41;</span></span>](reports/report-definition-language-ssrs.md)  
  
  