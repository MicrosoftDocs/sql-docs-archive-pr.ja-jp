---
title: コマンドプロンプトユーティリティリファレンス (データベースエンジン) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- command prompt utilities [SQL Server]
- command prompt utilities [SQL Server], about command prompt utilities
- command prompt [SQL Server]
- utilities [SQL Server], command prompt
- command prompt [SQL Server], utilities
ms.assetid: 48364bd9-6ea7-45e9-a332-acf3d81bbfae
author: stevestein
ms.author: sstein
ms.openlocfilehash: ffb5f15bb37bd4e15dd93404be3df47ce359586b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712685"
---
# <a name="command-prompt-utility-reference-database-engine"></a><span data-ttu-id="2e4a4-102">コマンド プロンプト ユーティリティ リファレンス (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="2e4a4-102">Command Prompt Utility Reference (Database Engine)</span></span>
  <span data-ttu-id="2e4a4-103">コマンド プロンプト ユーティリティを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の操作のスクリプトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-103">Command prompt utilities enable you to script [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] operations.</span></span> <span data-ttu-id="2e4a4-104">次の表は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に付属するコマンド プロンプト ユーティリティの一覧です。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-104">The following table contains a list of command prompt utilities that ship with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="2e4a4-105">**Utility**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-105">**Utility**</span></span>|<span data-ttu-id="2e4a4-106">**説明**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-106">**Description**</span></span>|<span data-ttu-id="2e4a4-107">**インストール先**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-107">**Installed in**</span></span>|  
|-----------------|---------------------|----------------------|  
|[<span data-ttu-id="2e4a4-108">bcp ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-108">bcp Utility</span></span>](bcp-utility.md)|<span data-ttu-id="2e4a4-109">ユーザー指定の形式で、[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスとデータ ファイルとの間でデータをコピーします。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-109">Used to copy data between an instance of [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and a data file in a user-specified format.</span></span>|<span data-ttu-id="2e4a4-110">\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-110">\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-111">dta ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-111">dta Utility</span></span>](dta/dta-utility.md)|<span data-ttu-id="2e4a4-112">作業負荷の分析、およびその作業負荷に対してサーバー パフォーマンスを最適化するための推奨物理デザイン構造の分析を行います。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-112">Used to analyze a workload and recommend physical design structures to optimize server performance for that workload.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-113">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-113">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-114">dtexec ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-114">dtexec Utility</span></span>](../integration-services/packages/dtexec-utility.md)|<span data-ttu-id="2e4a4-115">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージを構成および実行します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-115">Used to configure and execute an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="2e4a4-116">このコマンド プロンプト ユーティリティのユーザー インターフェイス バージョンは **DTExecUI**と呼ばれ、パッケージ実行ユーティリティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-116">A user interface version of this command prompt utility is called **DTExecUI**, which brings up the Execute Package Utility.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-117">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-117">DTS\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-118">dtutil ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-118">dtutil Utility</span></span>](../integration-services/dtutil-utility.md)|<span data-ttu-id="2e4a4-119">SSIS パッケージを管理します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-119">Used to manage SSIS packages.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-120">DTS\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-120">DTS\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-121">配置ユーティリティを使用したモデル ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="2e4a4-121">Deploy Model Solutions with the Deployment Utility</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility)|<span data-ttu-id="2e4a4-122">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに配置します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-122">Used to deploy [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] projects to instances of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-123">Tools\Binn\VShell\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="2e4a4-123">Tools\Binn\VShell\Common7\IDE</span></span>|  
|[<span data-ttu-id="2e4a4-124">osql ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-124">osql Utility</span></span>](osql-utility.md)|<span data-ttu-id="2e4a4-125">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-125">Allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-126">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-126">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-127">Profiler ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-127">Profiler Utility</span></span>](profiler-utility.md)|<span data-ttu-id="2e4a4-128">コマンド プロンプトから [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-128">Used to start [!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] from a command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-129">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-129">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-130">RS.exe ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2e4a4-130">RS.exe Utility &#40;SSRS&#41;</span></span>](../reporting-services/tools/rs-exe-utility-ssrs.md)|<span data-ttu-id="2e4a4-131">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート サーバーを管理するために作成されたスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-131">Used to run scripts designed for managing [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report servers.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-132">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-132">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-133">rsconfig ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2e4a4-133">rsconfig Utility &#40;SSRS&#41;</span></span>](../reporting-services/tools/rsconfig-utility-ssrs.md)|<span data-ttu-id="2e4a4-134">レポート サーバー接続を構成します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-134">Used to configure a report server connection.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-135">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-135">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-136">rskeymgmt ユーティリティ &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="2e4a4-136">rskeymgmt Utility &#40;SSRS&#41;</span></span>](../reporting-services/tools/rskeymgmt-utility-ssrs.md)|<span data-ttu-id="2e4a4-137">レポート サーバー上の暗号化キーを管理します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-137">Used to manage encryption keys on a report server.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-138">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-138">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-139">sqlagent90 アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2e4a4-139">sqlagent90 Application</span></span>](sqlagent90-application.md)|<span data-ttu-id="2e4a4-140">コマンド プロンプトから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェントを開始します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-140">Used to start [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent from a command prompt.</span></span>|<span data-ttu-id="2e4a4-141">\<drive>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-141">\<drive>:\Program Files\Microsoft SQL Server\\<*instance_name*>\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-142">sqlcmd Utility</span><span class="sxs-lookup"><span data-stu-id="2e4a4-142">sqlcmd Utility</span></span>](sqlcmd-utility.md)|<span data-ttu-id="2e4a4-143">[!INCLUDE[tsql](../includes/tsql-md.md)] ステートメント、システム プロシージャ、およびスクリプト ファイルをコマンド プロンプトで入力できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-143">Allows you to enter [!INCLUDE[tsql](../includes/tsql-md.md)] statements, system procedures, and script files at the command prompt.</span></span>|<span data-ttu-id="2e4a4-144">\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-144">\<*drive*:>\Program Files\\[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]\Client SDK\ODBC\110\Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-145">SQLdiag ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-145">SQLdiag Utility</span></span>](sqldiag-utility.md)|<span data-ttu-id="2e4a4-146">[!INCLUDE[msCoName](../includes/msconame-md.md)] カスタマー サポート サービス用の診断情報を収集します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-146">Used to collect diagnostic information for [!INCLUDE[msCoName](../includes/msconame-md.md)] Customer Service and Support.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-147">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-147">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-148">sqllogship アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2e4a4-148">sqllogship Application</span></span>](sqllogship-application.md)|<span data-ttu-id="2e4a4-149">バックアップ、コピー、および復元ジョブを実行することなく、ログ配布構成のバックアップ、コピー、復元操作、および関連するクリーンアップ作業を行うために使用されます。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-149">Used by applications to perform backup, copy, and restore operations and associated clean-up tasks for a log shipping configuration without running the backup, copy, and restore jobs.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-150">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-150">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-151">SqlLocalDB ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-151">SqlLocalDB Utility</span></span>](sqllocaldb-utility.md)|<span data-ttu-id="2e4a4-152">プログラムの開発者を対象とした [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の実行モードです。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-152">An execution mode of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] targeted to program developers.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-153">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-153">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-154">sqlmaint ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-154">sqlmaint Utility</span></span>](sqlmaint-utility.md)|<span data-ttu-id="2e4a4-155">以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]で作成されたデータベース メンテナンス プランを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-155">Used to execute database maintenance plans created in previous versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>|<span data-ttu-id="2e4a4-156">\<drive>: Server\MSSQL12.: SQLMSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-156">\<drive>:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-157">sqlps ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-157">sqlps Utility</span></span>](sqlps-utility.md)|<span data-ttu-id="2e4a4-158">PowerShell コマンドおよびスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-158">Used to run PowerShell commands and scripts.</span></span> <span data-ttu-id="2e4a4-159">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell プロバイダーおよびコマンドレットの読み込みと登録を行います。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-159">Loads and registers the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell provider and cmdlets.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-160">Tools\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-160">Tools\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-161">sqlservr アプリケーション</span><span class="sxs-lookup"><span data-stu-id="2e4a4-161">sqlservr Application</span></span>](sqlservr-application.md)|<span data-ttu-id="2e4a4-162">トラブルシューティングを行うために、コマンド プロンプトから [!INCLUDE[ssDE](../includes/ssde-md.md)] インスタンスを開始および停止します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-162">Used to start and stop an instance of [!INCLUDE[ssDE](../includes/ssde-md.md)] from the command prompt for troubleshooting.</span></span>|<span data-ttu-id="2e4a4-163">\<drive>: Server\MSSQL12.: SQLMSSQLSERVER\MSSQL\Binn</span><span class="sxs-lookup"><span data-stu-id="2e4a4-163">\<drive>:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Binn</span></span>|  
|[<span data-ttu-id="2e4a4-164">Ssms ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-164">Ssms Utility</span></span>](../ssms/ssms-utility.md)|<span data-ttu-id="2e4a4-165">コマンド プロンプトから [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を起動します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-165">Used to start [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] from a command prompt.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-166">Tools\Binn\VSShell\Common7\IDE</span><span class="sxs-lookup"><span data-stu-id="2e4a4-166">Tools\Binn\VSShell\Common7\IDE</span></span>|  
|[<span data-ttu-id="2e4a4-167">tablediff ユーティリティ</span><span class="sxs-lookup"><span data-stu-id="2e4a4-167">tablediff Utility</span></span>](tablediff-utility.md)|<span data-ttu-id="2e4a4-168">2 つのテーブルのデータを比較し、非収束について調査します。これは、レプリケーション トポロジのトラブルシューティングを行う場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-168">Used to compare the data in two tables for non-convergence, which is useful when troubleshooting a replication topology.</span></span>|[!INCLUDE[ssInstallPathVar](../includes/ssinstallpathvar-md.md)]<span data-ttu-id="2e4a4-169">COM (COM)</span><span class="sxs-lookup"><span data-stu-id="2e4a4-169">COM</span></span>|  
  
 <span data-ttu-id="2e4a4-170">**[!INCLUDE[win8](../includes/win8-md.md)] を使用して [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーにアクセスするには**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-170">**To access [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager Using [!INCLUDE[win8](../includes/win8-md.md)]**</span></span>  
  
 <span data-ttu-id="2e4a4-171">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 構成マネージャーは [!INCLUDE[msCoName](../includes/msconame-md.md)] 管理コンソール プログラムのスナップインであり、スタンドアロン プログラムではありません。そのため、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] を実行している場合、 [!INCLUDE[win8](../includes/win8-md.md)]構成マネージャーはアプリケーションとして表示されません。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-171">Because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager is a snap-in for the [!INCLUDE[msCoName](../includes/msconame-md.md)] Management Console program and not a stand-alone program, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager not does not appear as an application when running [!INCLUDE[win8](../includes/win8-md.md)].</span></span> <span data-ttu-id="2e4a4-172">Configuration Manager を開くには [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、**検索**チャームで、[**アプリ**] の下に **「sqlservermanager12.msc」** (の場合) または「sqlservermanager11.msc」 (の場合) [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] と入力し、 **SQLServerManager11.msc** [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] **enter**キーを押します。</span><span class="sxs-lookup"><span data-stu-id="2e4a4-172">To open [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Configuration Manager, in the **Search** charm, under **Apps**, type **SQLServerManager12.msc** (for [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]) or **SQLServerManager11.msc** for ([!INCLUDE[ssSQL11](../includes/sssql11-md.md)]), and then press **Enter**.</span></span>  
  
## <a name="command-prompt-utilities-syntax-conventions"></a><span data-ttu-id="2e4a4-173">コマンド プロンプト ユーティリティで使用する構文表記規則</span><span class="sxs-lookup"><span data-stu-id="2e4a4-173">Command Prompt Utilities Syntax Conventions</span></span>  
  
|<span data-ttu-id="2e4a4-174">**規則**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-174">**Convention**</span></span>|<span data-ttu-id="2e4a4-175">**用途**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-175">**Used for**</span></span>|  
|--------------------|------------------|  
|<span data-ttu-id="2e4a4-176">UPPERCASE</span><span class="sxs-lookup"><span data-stu-id="2e4a4-176">UPPERCASE</span></span>|<span data-ttu-id="2e4a4-177">オペレーティング システム レベルで使用するステートメントと用語</span><span class="sxs-lookup"><span data-stu-id="2e4a4-177">Statements and terms used at the operating system level.</span></span>|  
|`monospace`|<span data-ttu-id="2e4a4-178">サンプルのコマンドとプログラム コード</span><span class="sxs-lookup"><span data-stu-id="2e4a4-178">Sample commands and program code.</span></span>|  
|<span data-ttu-id="2e4a4-179">*斜体*</span><span class="sxs-lookup"><span data-stu-id="2e4a4-179">*italic*</span></span>|<span data-ttu-id="2e4a4-180">ユーザーが指定するパラメーター</span><span class="sxs-lookup"><span data-stu-id="2e4a4-180">User-supplied parameters.</span></span>|  
|<span data-ttu-id="2e4a4-181">**太字**</span><span class="sxs-lookup"><span data-stu-id="2e4a4-181">**bold**</span></span>|<span data-ttu-id="2e4a4-182">示されたとおりに入力する必要があるコマンド、パラメーター、およびその他の構文</span><span class="sxs-lookup"><span data-stu-id="2e4a4-182">Commands, parameters, and other syntax that must be typed exactly as shown.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e4a4-183">参照</span><span class="sxs-lookup"><span data-stu-id="2e4a4-183">See Also</span></span>  
 <span data-ttu-id="2e4a4-184">[Replication Distribution Agent](../relational-databases/replication/agents/replication-distribution-agent.md) </span><span class="sxs-lookup"><span data-stu-id="2e4a4-184">[Replication Distribution Agent](../relational-databases/replication/agents/replication-distribution-agent.md) </span></span>  
 <span data-ttu-id="2e4a4-185">[Replication Log Reader Agent](../relational-databases/replication/agents/replication-log-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="2e4a4-185">[Replication Log Reader Agent](../relational-databases/replication/agents/replication-log-reader-agent.md) </span></span>  
 <span data-ttu-id="2e4a4-186">[Replication Merge Agent](../relational-databases/replication/agents/replication-merge-agent.md) </span><span class="sxs-lookup"><span data-stu-id="2e4a4-186">[Replication Merge Agent](../relational-databases/replication/agents/replication-merge-agent.md) </span></span>  
 <span data-ttu-id="2e4a4-187">[レプリケーション キュー リーダー エージェント](../relational-databases/replication/agents/replication-queue-reader-agent.md) </span><span class="sxs-lookup"><span data-stu-id="2e4a4-187">[Replication Queue Reader Agent](../relational-databases/replication/agents/replication-queue-reader-agent.md) </span></span>  
 [<span data-ttu-id="2e4a4-188">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="2e4a4-188">Replication Snapshot Agent</span></span>](../relational-databases/replication/agents/replication-snapshot-agent.md)  
  
  