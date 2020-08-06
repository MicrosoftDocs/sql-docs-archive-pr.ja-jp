---
title: 機能の選択 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- feature selection, Setup
helpviewer_keywords:
- SQL Server Installation Wizard, Components to Install page
- Components to Install page [SQL Server Installation Wizard]
ms.assetid: 73182088-153b-4634-a060-d14d1fd23b70
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 3832715bb8b99fbaa44426f0de458da9eb87039a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740738"
---
# <a name="feature-selection"></a><span data-ttu-id="a709e-102">特徴選択</span><span class="sxs-lookup"><span data-stu-id="a709e-102">Feature Selection</span></span>
  <span data-ttu-id="a709e-103">**のインストールに含めるコンポーネントを選択するには、** インストール ウィザードの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [機能の選択] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ページのチェック ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="a709e-103">Use the check boxes on the **Feature Selection** page of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Installation wizard to select components for your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
## <a name="installing-ssnoversion-features"></a><span data-ttu-id="a709e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 機能のインストール</span><span class="sxs-lookup"><span data-stu-id="a709e-104">Installing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Features</span></span>  
 <span data-ttu-id="a709e-105">**[機能の選択]** ページには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能が、 **"インスタンス機能"** と **"共有機能"** という大きな 2 つのセクションに分かれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="a709e-105">On the **Feature Selection** page, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features are separated into two main sections: **Instance Features** and **Shared Features**.</span></span>  
  
 <span data-ttu-id="a709e-106">**インスタンス機能** は、各インスタンスにつき 1 回インストールされるコンポーネントを指します。つまり、特定のコンポーネントのコピーが複数 (インスタンスごとに 1 つ) 存在することになります。</span><span class="sxs-lookup"><span data-stu-id="a709e-106">**Instance Features** refers to the components that are installed once for each instance so that you have multiple copies of them (one for each instance).</span></span> <span data-ttu-id="a709e-107">インスタンスはそれぞれ独立して存在し、修正プログラムのレベルがインスタンスごとに異なる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a709e-107">Each instance can be a separate version that has a different patch level.</span></span> <span data-ttu-id="a709e-108">サービス パックや累積的な更新プログラムも含め、何かの修正プログラムをインストールすると、特定のコンピューター上の 1 つのインスタンスについてのみファイルが更新されます。その際、共有機能が未更新であった場合には、共有機能も更新されます。</span><span class="sxs-lookup"><span data-stu-id="a709e-108">When you install a patch, whether it is a service pack, a hotfix, or a cumulative update, it updates only the files for one instance on a given machine, plus the shared features if they have not already been updated.</span></span>  
  
 <span data-ttu-id="a709e-109">**共有機能** は、特定のコンピューター上のすべてのインスタンスに共通する機能をいいます。</span><span class="sxs-lookup"><span data-stu-id="a709e-109">**Shared Features** refers to features that are common across all instances on a given machine.</span></span> <span data-ttu-id="a709e-110">共有機能はそれぞれ、サイド バイ サイドでインストール可能なサポート対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のバージョン (サービス パック、累積的な更新プログラム、修正プログラム) との下位互換性を保つように設計されています。</span><span class="sxs-lookup"><span data-stu-id="a709e-110">Each of these shared features is designed to be backward compatible with supported [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] versions (service packs, cumulative updates, and hotfixes) that can install side by side.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a709e-111">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバークラスター:\*\* [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コンポーネントは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] フェールオーバークラスタリングをサポートする唯一の機能です。</span><span class="sxs-lookup"><span data-stu-id="a709e-111">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Clusters:** The [!INCLUDE[ssDE](../../includes/ssde-md.md)] and [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] components are the only [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] features that support failover clustering.</span></span> <span data-ttu-id="a709e-112">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]など、その他のコンポーネントは、フェールオーバー クラスター ノードにインストールできますが、クラスターに対応していないため、フェールオーバー クラスター ノードがオフラインになると、そのサービスはフェールオーバーしません。</span><span class="sxs-lookup"><span data-stu-id="a709e-112">You can install other components, like [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], on a failover cluster node, but they are not cluster-aware, and their services do not fail over if the failover cluster node goes offline.</span></span> <span data-ttu-id="a709e-113">詳細については、「[Always On フェールオーバー クラスター インスタンス &#40;SQL Server&#41;](../failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-113">For more information, see [AlwaysOn Failover Cluster Instances &#40;SQL Server&#41;](../failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md).</span></span>  
  
### <a name="instance-features"></a><span data-ttu-id="a709e-114">インスタンス機能</span><span class="sxs-lookup"><span data-stu-id="a709e-114">Instance Features</span></span>  
 <span data-ttu-id="a709e-115">コンポーネントを選択すると、 **[説明]** ペインに、各コンポーネント グループの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a709e-115">A description for each component group appears in the **Description** pane when you select it.</span></span> <span data-ttu-id="a709e-116">チェック ボックスはいくつでもオンにできます。</span><span class="sxs-lookup"><span data-stu-id="a709e-116">You can select any combination of check boxes.</span></span> <span data-ttu-id="a709e-117">続行するには、選択を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="a709e-117">To continue, you must make a selection.</span></span>  
  
|<span data-ttu-id="a709e-118">特徴</span><span class="sxs-lookup"><span data-stu-id="a709e-118">Features</span></span>|<span data-ttu-id="a709e-119">説明</span><span class="sxs-lookup"><span data-stu-id="a709e-119">Description</span></span>|  
|--------------|-----------------|  
|[!INCLUDE[ssDE](../../includes/ssde-md.md)] <span data-ttu-id="a709e-120">サービス</span><span class="sxs-lookup"><span data-stu-id="a709e-120">Services</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]<span data-ttu-id="a709e-121">には、データを格納、処理、およびセキュリティで保護するための主要サービスである[!INCLUDE[ssDE](../../includes/ssde-md.md)]、レプリケーション、フルテキスト検索、リレーショナル データと XML データの管理ツール、および [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-121">includes the [!INCLUDE[ssDE](../../includes/ssde-md.md)], the core service for storing, processing, and securing data, replication, full-text search, tools for managing relational and XML data, and the [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) server.</span></span> <span data-ttu-id="a709e-122">データベース エンジンの機能を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a709e-122">The following are features of the database engine:</span></span><br /><br /> <span data-ttu-id="a709e-123">[!INCLUDE[ssDE](../../includes/ssde-md.md)] は、データの格納、処理、セキュリティ確保のための中心的なサービスです。</span><span class="sxs-lookup"><span data-stu-id="a709e-123">The [!INCLUDE[ssDE](../../includes/ssde-md.md)] is the core service for storing, processing, and securing data.</span></span><br /><br /> <span data-ttu-id="a709e-124">レプリケーション : レプリケーションは、あるデータベースから別のデータベースへデータ オブジェクトやデータベース オブジェクトのコピーと配布を行い、一貫性を維持するためにデータベース間の同期を行う一連のテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="a709e-124">Replication: Optional: Replication is a set of technologies for copying and distributing data and database objects from one database to another and then synchronizing between databases to maintain consistency.</span></span><br /><br /> <span data-ttu-id="a709e-125">フルテキスト検索 : (オプション) フルテキスト検索は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルのプレーン文字ベースのデータに対してフルテキスト クエリを実行するための機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a709e-125">Full-Text Search: Optional: Full-Text Search provides functionality to issue full-text queries against plain character-based data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span><br /><br /> [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)]<span data-ttu-id="a709e-126">: (オプション): [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) は、データ ソース内で一貫性のない不適切なデータを発見できるデータ クレンジング ソリューションであり、データのクレンジングをコンピューター支援型のインタラクティブな方法で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a709e-126">: Optional: [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) is a data-cleansing solution that enables you to discover inconsistent and incorrect data in your data source, and provides computer-assisted and interactive ways to cleanse your data.</span></span> <span data-ttu-id="a709e-127">DQS サーバーをインストールするには、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a709e-127">Select this check box to install DQS server.</span></span> <span data-ttu-id="a709e-128">DQS サーバーのインストールを完了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]*するには、* のインストールを完了した後で、DQSInstaller.exe ファイルを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a709e-128">After the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation completes, you have to run the DQSInstaller.exe file to *complete* the DQS server installation.</span></span> <span data-ttu-id="a709e-129">SQL server の既定のインスタンスをインストールした場合、このファイルは C:\Program files \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] \MSSQL12. にあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]MSSQLSERVER\MSSQL\Binn.</span><span class="sxs-lookup"><span data-stu-id="a709e-129">If you installed the default instance of SQL server, this file is available at C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\MSSQL12.MSSQLSERVER\MSSQL\Binn.</span></span><br /><br /> <br /><br /> <span data-ttu-id="a709e-130">\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバークラスター:\*\* [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [データベースエンジンサービス] を選択した場合、レプリケーションとフルテキスト検索のコンポーネントは必須であり、フェールオーバークラスタリングのインストールのセットアップによって自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="a709e-130">**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Failover Clusters:** Replication and Full-Text Search components are required, and automatically selected by Setup for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover clustering installations when you select Database Engine Services.</span></span>|  
|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="a709e-131">には、オンライン分析処理 (OLAP) アプリケーションおよびデータ マイニング アプリケーションを作成および管理するためのツールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-131">includes the tools for creating and managing online analytical processing (OLAP) and data mining applications.</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]<span data-ttu-id="a709e-132">-ネイティブ</span><span class="sxs-lookup"><span data-stu-id="a709e-132">-Native</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-133">ネイティブ モードには、表形式、マトリックス形式、グラフィカル形式、および自由形式のレポートを作成、管理、配置するためのサーバー コンポーネントとクライアント コンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-133">Native mode includes server and client components for creating, managing, and deploying tabular, matrix, graphical, and free-form reports.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-134">は、レポート アプリケーション開発用の拡張可能プラットフォームとしても使用できます。</span><span class="sxs-lookup"><span data-stu-id="a709e-134">is also an extensible platform that you can use to develop report applications.</span></span>|  
  
> [!IMPORTANT]
>  1.  <span data-ttu-id="a709e-135">セットアップでは、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] スケールアウト配置の複数ノードに対して負荷分散と単一 URL アドレス指定が構成されません。</span><span class="sxs-lookup"><span data-stu-id="a709e-135">Setup does not configure load-balancing and single-URL addressing for multiple nodes in a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] scale-out deployment.</span></span> <span data-ttu-id="a709e-136">スケールアウト配置を完了するには、Windows Server、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Application Center、またはサード パーティ製クラスター管理ソフトウェアを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a709e-136">To complete a scale-out deployment, you must use Windows Server, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Application Center, or third-party cluster management software.</span></span> <span data-ttu-id="a709e-137">Web ファーム配置の設定の詳細については、「[スケールアウト配置の Reporting Services の構成](https://go.microsoft.com/fwlink/?LinkId=199448)」 (を参照してください https://go.microsoft.com/fwlink/?LinkId=199448) 。</span><span class="sxs-lookup"><span data-stu-id="a709e-137">For more information about setting up Web farm deployment, see [Configuring Reporting Services for Scale-Out Deployment](https://go.microsoft.com/fwlink/?LinkId=199448) (https://go.microsoft.com/fwlink/?LinkId=199448).</span></span>  
> 2.  <span data-ttu-id="a709e-138">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントのブラウザーの要件については、「[Reporting Services と Power View のブラウザー サポートの計画 &#40;Reporting Services 2014&#41;](../../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-138">For browser requirements of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] components, see [Planning for Reporting Services and Power View Browser Support &#40;Reporting Services 2014&#41;](../../../2014/reporting-services/browser-support-for-reporting-services-and-power-view.md).</span></span>  
> 3.  <span data-ttu-id="a709e-139">64 ビット プラットフォームと、64 ビット サーバーの 32 ビット サブシステム (WOW64) 上では、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] を並列構成で同時に実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a709e-139">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] is not supported in side-by-side configurations on the 64-bit platform and on the 32-bit subsystem (WOW64) of a 64-bit server at the same time.</span></span>  
  
### <a name="shared-features"></a><span data-ttu-id="a709e-140">共有機能</span><span class="sxs-lookup"><span data-stu-id="a709e-140">Shared Features</span></span>  
 <span data-ttu-id="a709e-141">1 つのコンピューター上のすべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスによって共有される機能は、単一のディレクトリにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a709e-141">Features shared by all instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on a single computer are installed to a single directory.</span></span> <span data-ttu-id="a709e-142">フォルダーには次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="a709e-142">They include the following:</span></span>  
  
|<span data-ttu-id="a709e-143">特徴量</span><span class="sxs-lookup"><span data-stu-id="a709e-143">Feature</span></span>|<span data-ttu-id="a709e-144">説明</span><span class="sxs-lookup"><span data-stu-id="a709e-144">Description</span></span>|  
|-------------|-----------------|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-145">- SharePoint</span><span class="sxs-lookup"><span data-stu-id="a709e-145">- SharePoint</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-146">SharePoint モードは、電子メール、複数のファイル形式、および対話的な Web ベースの形式でレポートの作成、管理、および配信を行う、サーバー ベースのアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="a709e-146">SharePoint mode is a server based application for creating, managing, and delivering reports to email, multiple file formats, and interactive Web-based formations.</span></span> <span data-ttu-id="a709e-147">SharePoint モードでは、レポートの表示と管理の機能を SharePoint 製品に統合します。</span><span class="sxs-lookup"><span data-stu-id="a709e-147">SharePoint mode integrates the report viewing and report management experience with SharePoint products.</span></span> <span data-ttu-id="a709e-148">詳細については、「[Reporting Services レポート サーバー &#40;SharePoint モード&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-148">For more information, see [Reporting Services Report Server &#40;SharePoint Mode&#41;](../../../2014/reporting-services/reporting-services-report-server-sharepoint-mode.md).</span></span>|  
|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-149">SharePoint 製品用アドイン</span><span class="sxs-lookup"><span data-stu-id="a709e-149">Add-in for SharePoint Products</span></span>|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="a709e-150">SharePoint 製品用アドインには、SharePoint 製品を SharePoint モードの [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] レポート サーバーと統合するための管理コンポーネントとユーザー インターフェイス コンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-150">Add-in for SharePoint products includes management and user interface components to integrate a SharePoint product with an [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server in SharePoint mode.</span></span> <span data-ttu-id="a709e-151">詳細については、「 [SharePoint 製品用 Reporting Services アドインの検索場所](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-151">For more information, see [Where to find the Reporting Services add-in for SharePoint Products](../../reporting-services/install-windows/where-to-find-the-reporting-services-add-in-for-sharepoint-products.md).</span></span>|  
|<span data-ttu-id="a709e-152">Data Quality クライアント</span><span class="sxs-lookup"><span data-stu-id="a709e-152">Data Quality Client</span></span>|<span data-ttu-id="a709e-153">Data Quality クライアントは、DQS サーバーに接続するスタンドアロン アプリケーションであり、直感的なグラフィカル ユーザー インターフェイスを使用して、データ クレンジング操作やデータ照合操作を実行したり、DQS の管理タスクを実行したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a709e-153">Data Quality Client is a standalone application that connects to the DQS server, and provides an intuitive graphical user interface to perform data-cleansing and data-matching operations, and to perform administrative tasks in DQS.</span></span>|  
|<span data-ttu-id="a709e-154">クライアント ツール接続</span><span class="sxs-lookup"><span data-stu-id="a709e-154">Client Tools Connectivity</span></span>|<span data-ttu-id="a709e-155">クライアント ツールには、DB-Library、OLEDB for OLAP、ODBC、ADODB、ADOMD+ 用のネットワーク ライブラリなど、クライアントとサーバー間の通信を行うためのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-155">Client Tools includes components for communication between clients and servers, including network libraries for DB-Library, OLEDB for OLAP, ODBC, ADODB, and ADOMD+.</span></span>|  
|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="a709e-156">は、データを移動、コピー、変換するためのグラフィカル ツールおよびプログラミング可能なオブジェクトのセットです。</span><span class="sxs-lookup"><span data-stu-id="a709e-156">is a set of graphical tools and programmable objects for moving, copying, and transforming data.</span></span>|  
|<span data-ttu-id="a709e-157">クライアント ツールの旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="a709e-157">Client Tools Backward Compatibility</span></span>|<span data-ttu-id="a709e-158">クライアント ツールの旧バージョンとの互換性には、次のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-158">Client Tools Backward Compatibility includes the following components:</span></span><br /><br /> <span data-ttu-id="a709e-159">SQL 分散管理オブジェクト (SQL-DMO)。</span><span class="sxs-lookup"><span data-stu-id="a709e-159">SQL Distributed Management Objects (SQL-DMO).</span></span> <span data-ttu-id="a709e-160">詳細については、「[SQL Server 2014 で提供が中止された機能](../../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-160">For more information, see [Discontinued SQL Server Features in SQL Server 2014](../../../2014/getting-started/discontinued-sql-server-features-in-sql-server-2014.md).</span></span><br /><br /> <span data-ttu-id="a709e-161">Decision Support オブジェクト (DSO)。</span><span class="sxs-lookup"><span data-stu-id="a709e-161">Decision Support Objects (DSO).</span></span> <span data-ttu-id="a709e-162">詳細については、「[SQL Server 2014 の Analysis Services 機能における重大な変更](../../../2014/analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-162">For more information, see [Breaking Changes to Analysis Services Features in SQL Server 2014](../../../2014/analysis-services/breaking-changes-to-analysis-services-features-in-sql-server-2014.md).</span></span>|  
|<span data-ttu-id="a709e-163">クライアント ツール SDK</span><span class="sxs-lookup"><span data-stu-id="a709e-163">Client Tools SDK</span></span>|<span data-ttu-id="a709e-164">プログラマのためのリソースを含むソフトウェア開発キットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a709e-164">Includes the software development kit containing resources for programmers.</span></span>|  
|<span data-ttu-id="a709e-165">Documentation コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a709e-165">Documentation Components</span></span>|<span data-ttu-id="a709e-166">Documentation コンポーネントには、ヘルプ コンテンツを表示および管理するためのコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-166">Documentation components include the components to view and manage help content.</span></span>|  
|<span data-ttu-id="a709e-167">管理ツール - 基本</span><span class="sxs-lookup"><span data-stu-id="a709e-167">Management Tools - Basic</span></span>|<span data-ttu-id="a709e-168">**管理ツール-基本:** これには次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-168">**Management Tools - Basic :** This includes the following:</span></span><br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]<span data-ttu-id="a709e-169">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]、、 [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] **sqlcmd**ユーティリティ、および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell プロバイダーのサポート</span><span class="sxs-lookup"><span data-stu-id="a709e-169">support for the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], **sqlcmd** utility, and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell provider</span></span><br /><br /> <span data-ttu-id="a709e-170">**管理ツール-完全:** これには、基本バージョンのコンポーネントに加えて、次のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-170">**Management Tools - Complete :** This includes the following components in addition to the components in the basic version:</span></span><br /><br /> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="a709e-171">による [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]、および [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のサポート</span><span class="sxs-lookup"><span data-stu-id="a709e-171">support for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], and [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]</span></span><br /><br /> [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]<br /><br /> <span data-ttu-id="a709e-172">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="a709e-172">Database Engine Tuning Advisor</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a709e-173">ユーティリティ管理</span><span class="sxs-lookup"><span data-stu-id="a709e-173">Utility management</span></span>|  
|<span data-ttu-id="a709e-174">分散再生コントローラー</span><span class="sxs-lookup"><span data-stu-id="a709e-174">Distributed Replay Controller</span></span>|<span data-ttu-id="a709e-175">分散再生コントローラーは、分散再生クライアントのアクションを統制します。</span><span class="sxs-lookup"><span data-stu-id="a709e-175">The Distributed Replay controller orchestrates the actions of the distributed replay clients.</span></span> <span data-ttu-id="a709e-176">各分散再生環境には、コントローラーのインスタンスを 1 つだけ置くことができます。</span><span class="sxs-lookup"><span data-stu-id="a709e-176">There can only be one controller instance in each Distributed Replay environment.</span></span> <span data-ttu-id="a709e-177">詳細については、「 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-177">For more information, see [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).</span></span>|  
|<span data-ttu-id="a709e-178">分散再生クライアント</span><span class="sxs-lookup"><span data-stu-id="a709e-178">Distributed Replay Client</span></span>|<span data-ttu-id="a709e-179">分散再生クライアントは、SQL Server のインスタンスに対するワークロードをシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="a709e-179">The Distributed Replay clients work together to simulate workloads against an instance of SQL Server.</span></span> <span data-ttu-id="a709e-180">各分散再生環境には、1 つまたは複数のクライアントを置くことができます。</span><span class="sxs-lookup"><span data-stu-id="a709e-180">There can be one or more clients in each Distributed Replay environment.</span></span> <span data-ttu-id="a709e-181">詳細については、「 [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-181">For more information, see [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md).</span></span>|  
|<span data-ttu-id="a709e-182">SQL クライアント接続 SDK</span><span class="sxs-lookup"><span data-stu-id="a709e-182">SQL Client Connectivity SDK</span></span>|<span data-ttu-id="a709e-183">データベース アプリケーション開発用の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC/OLE DB) SDK が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a709e-183">Includes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC/OLE DB) SDK for database application development.</span></span>|  
|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="a709e-184">は、情報の精度向上と監査を目的として、異種システムのデータを全社規模で単一のマスター データ ソースとして統合するプラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="a709e-184">is a platform for integrating data from disparate systems across an organization into a single source of master data for accuracy and auditing purposes.</span></span> <span data-ttu-id="a709e-185">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] を選択すると、 [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]、アセンブリ、Windows PowerShell スナップインのほか、Web アプリケーションおよび Web サービス用のフォルダーおよびファイルがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a709e-185">The [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] option installs [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], assemblies, a Windows PowerShell snap-in, and folders and files for Web applications and services.</span></span>|  
  
 <span data-ttu-id="a709e-186">既定では、共有コンポーネントは %Program Files%Microsoft SQL Server\\にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a709e-186">By default, shared components are installed to %Program Files%Microsoft SQL Server\\.</span></span> <span data-ttu-id="a709e-187">インストール パスを変更するには、 **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a709e-187">To change the installation path, click the **Browse** button.</span></span> <span data-ttu-id="a709e-188">1 つの共有コンポーネントのインストール パスを変更すると、他の共有コンポーネントのパスも変更されます。</span><span class="sxs-lookup"><span data-stu-id="a709e-188">If you change the installation path for one shared component, you also change it for other shared components.</span></span> <span data-ttu-id="a709e-189">以降のインストールでは、最初のインストールと同じ場所に共有コンポーネントがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a709e-189">Subsequent installations will install shared components to the same location as the original installation.</span></span>  
  
 <span data-ttu-id="a709e-190">**インスタンスルートディレクトリ**-既定では、インスタンスルートディレクトリは C:\Program files です \\ [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \\ 。</span><span class="sxs-lookup"><span data-stu-id="a709e-190">**Instance root directory** - By default, the instance root directory is C:\Program Files\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\.</span></span> <span data-ttu-id="a709e-191">既定以外のルート ディレクトリを指定するには、 **[参照]** ボタンをクリックするか、パス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="a709e-191">To specify a non-default root directory, click the **Browse** button, or provide a path name.</span></span>  
  
 <span data-ttu-id="a709e-192">x64 ベースのオペレーティング システムでは、64 ビット コンポーネントのインストール先と、32 ビット コンポーネントの WOW64 サブシステム上のインストール先を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a709e-192">On x64-based operating systems, you can specify where 64-bit components will be installed, and where on the WOW64 subsystem 32-bit components will be installed.</span></span>  
  
## <a name="disk-space-requirements"></a><span data-ttu-id="a709e-193">必要なディスク領域</span><span class="sxs-lookup"><span data-stu-id="a709e-193">Disk Space Requirements</span></span>  
 <span data-ttu-id="a709e-194">[ディスク コストの概要] ページを使用して、インストール対象として選択した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能に必要なディスク領域を調べます。</span><span class="sxs-lookup"><span data-stu-id="a709e-194">Use the Disk Cost Summary page to examine disk space requirements for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features that you selected for your installation.</span></span>  
  
### <a name="options"></a><span data-ttu-id="a709e-195">Options</span><span class="sxs-lookup"><span data-stu-id="a709e-195">Options</span></span>  
 <span data-ttu-id="a709e-196">必要なディスク領域が大きすぎる場合は、次の方法を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a709e-196">If required disk space is too high, consider the following options:</span></span>  
  
-   <span data-ttu-id="a709e-197">インストール ディレクトリを、ディスク領域の大きいディスクに変更します。</span><span class="sxs-lookup"><span data-stu-id="a709e-197">Change installation directories to a drive with more disk space.</span></span>  
  
-   <span data-ttu-id="a709e-198">インストールする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能を変更します。</span><span class="sxs-lookup"><span data-stu-id="a709e-198">Change the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] features for your installation.</span></span>  
  
-   <span data-ttu-id="a709e-199">他のファイルやアプリケーションを移動して、指定したドライブ上の空き領域を増やします。</span><span class="sxs-lookup"><span data-stu-id="a709e-199">Create more free space on the specified drive by moving other files or applications.</span></span>  
  
## <a name="installing-adventureworks-sample-databases"></a><span data-ttu-id="a709e-200">AdventureWorks サンプル データベースのインストール</span><span class="sxs-lookup"><span data-stu-id="a709e-200">Installing AdventureWorks Sample Databases</span></span>  
 <span data-ttu-id="a709e-201">既定では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のセットアップ時にサンプル データベースとサンプル コードはインストールされません。</span><span class="sxs-lookup"><span data-stu-id="a709e-201">By default, sample databases and sample code are not installed as part of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Setup.</span></span> <span data-ttu-id="a709e-202">サンプルデータベースとサンプルコードのインストールの詳細については、 [Microsoft SQL Server コミュニティプロジェクト & のサンプル](https://go.microsoft.com/fwlink/?LinkId=87843)(を参照してください https://go.microsoft.com/fwlink/?LinkId=87843) 。</span><span class="sxs-lookup"><span data-stu-id="a709e-202">For more information about installing sample databases and sample code, see the [Microsoft SQL Server Community Projects & Samples](https://go.microsoft.com/fwlink/?LinkId=87843) (https://go.microsoft.com/fwlink/?LinkId=87843).</span></span>  
  
 <span data-ttu-id="a709e-203">サンプルの詳細については、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] をインストールした後で確認できます。</span><span class="sxs-lookup"><span data-stu-id="a709e-203">Additional information about samples is available after [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] has been installed.</span></span> <span data-ttu-id="a709e-204">[**スタート**] メニューの [**すべてのプログラム**] をクリックし、[] **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]** 、[**ドキュメントとチュートリアル**] の順にクリックして、[ \*\* [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サンプルの概要\*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a709e-204">From the **Start** menu, click **All Programs**, click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**, click **Documentation and Tutorials**, and then click **[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Samples Overview**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a709e-205">参照</span><span class="sxs-lookup"><span data-stu-id="a709e-205">See Also</span></span>  
 [<span data-ttu-id="a709e-206">SQL Server 2014 のエディションとコンポーネント</span><span class="sxs-lookup"><span data-stu-id="a709e-206">Editions and Components of SQL Server 2014</span></span>](../editions-and-components-of-sql-server-2016.md)  
  
  