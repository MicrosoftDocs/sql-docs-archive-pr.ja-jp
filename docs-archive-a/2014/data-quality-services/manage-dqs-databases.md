---
title: DQS データベースの管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7228021dd3fe0af61312eeb891081cc24e1aa95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644650"
---
# <a name="manage-dqs-databases"></a><span data-ttu-id="8165b-102">Manage DQS Databases</span><span class="sxs-lookup"><span data-stu-id="8165b-102">Manage DQS Databases</span></span>
  <span data-ttu-id="8165b-103">ここでは、バックアップ/復元またはデタッチ/アタッチなど DQS のデータベースに対して実行できるデータベース管理アクティビティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8165b-103">This section provides information about database management activities that can be performed on the DQS databases such as backup/restore or detach/attach.</span></span>  
  
##  <a name="backup-and-restore-the-dqs-databases"></a><a name="BackupRestore"></a> <span data-ttu-id="8165b-104">DQS データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="8165b-104">Backup and Restore the DQS Databases</span></span>  
 <span data-ttu-id="8165b-105">SQL Server データベースのバックアップと復元は、バックアップ データベースからデータを復旧して災害時のデータの損失を防ぐためにデータベース管理者が実行する一般的な操作です。</span><span class="sxs-lookup"><span data-stu-id="8165b-105">Backup and restore of SQL Server databases are common operations that database administrators perform for preventing loss of data in a case of disaster by recovering data from the backup databases.</span></span> [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] <span data-ttu-id="8165b-106">は、主に DQS_MAIN と DQS_PROJECTS の 2 つの SQL Server データベースにより実装されます。</span><span class="sxs-lookup"><span data-stu-id="8165b-106">is primarily implemented by two SQL Server databases: DQS_MAIN and DQS_PROJECTS.</span></span> <span data-ttu-id="8165b-107">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) データベースのバックアップと復元の手順は、他の SQL Server データベースの手順と似ています。DQS データベースのバックアップと復元に関連付けられている次の 3 つの問題があります。</span><span class="sxs-lookup"><span data-stu-id="8165b-107">The backup and restore procedures of the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) databases are similar to any other SQL Server databases.There are three challenges that are associated with backup and restore of the DQS databases:</span></span>  
  
-   <span data-ttu-id="8165b-108">DQS データベースのバックアップと復元の操作を同期する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8165b-108">The backup and restore operations of the DQS databases must be synchronized.</span></span> <span data-ttu-id="8165b-109">同期しない場合、復元された [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] は機能しません。</span><span class="sxs-lookup"><span data-stu-id="8165b-109">Otherwise the restored [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] will not be functional.</span></span>  
  
-   <span data-ttu-id="8165b-110">2 つの DQS データベース (DQS_MAIN および DQS_PROJECTS) には、単純なデータベース オブジェクト (テーブルやストアド プロシージャなど) だけではなく、アセンブリおよびその他の複雑なオブジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8165b-110">The two DQS databases, DQS_MAIN and DQS_PROJECTS, contain assemblies and other complex objects, apart from just simple database objects (such as tables and stored procedures).</span></span>  
  
-   <span data-ttu-id="8165b-111">DQS データベースが [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]として機能するために必要な DQS データベース以外のいくつかのエンティティがあります。具体的には、2 つの SQL Server ログイン (##MS_dqs_db_owner_login## と ##MS_dqs_service_login##)、およびマスター データベースの初期化ストアド プロシージャ (DQInitDQS_MAIN) です。</span><span class="sxs-lookup"><span data-stu-id="8165b-111">There are some entities outside of the DQS databases that must exist for the DQS databases to be functional as [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], specifically the two SQL Server logins (##MS_dqs_db_owner_login## and ##MS_dqs_service_login##), and an initialization stored procedure (DQInitDQS_MAIN) in the master database.</span></span>  
  
 <span data-ttu-id="8165b-112">SQL Server でのデータベースのバックアップと復元の詳細については、「 [SQL Server データベースのバックアップと復元](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8165b-112">For detailed information about backup and restore in SQL Server, see [Back Up and Restore of SQL Server Databases](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a><span data-ttu-id="8165b-113">DQS データベースの既定の自動拡張サイズと復旧モデル</span><span class="sxs-lookup"><span data-stu-id="8165b-113">Default Autogrowth Size and Recovery Model for the DQS Databases</span></span>  
 <span data-ttu-id="8165b-114">DQS データベースおよびトランザクション ログが無限に拡張してハード ディスクがいっぱいになるのを防ぐためには</span><span class="sxs-lookup"><span data-stu-id="8165b-114">To prevent DQS databases and transaction logs to grow infinitely and potentially fill the hard disk:</span></span>  
  
-   <span data-ttu-id="8165b-115">DQS データベースの既定の **[自動拡張]** のサイズを 10% に設定します。</span><span class="sxs-lookup"><span data-stu-id="8165b-115">The default **Autogrowth** size of the DQS databases is set to 10%.</span></span>  
  
-   <span data-ttu-id="8165b-116">DQS データベースの既定の復旧モデルを、 **[単純]** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8165b-116">The default recovery model of the DQS databases is set to **Simple**.</span></span> <span data-ttu-id="8165b-117">単純復旧モデルでは、トランザクションのログへの記録は最小限になり、トランザクションの完了後にログが自動的に切り捨てられて、トランザクション ログ (.ldf ファイル) の領域が解放されます。</span><span class="sxs-lookup"><span data-stu-id="8165b-117">In the Simple recovery model, transactions are minimally logged, and the log truncation happens automatically after the transaction is complete to free up space in the transaction log (.ldf file).</span></span> <span data-ttu-id="8165b-118">単純復旧モデルについて詳しくは、「[データベースの完全バックアップ &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8165b-118">For detailed information about the simple recovery model, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="8165b-119">単純復旧モデルでは、ログ レコードが長い間アクティブなままになると (長く、時間のかかるトランザクションの場合など)、ログの切り捨てが遅れて、トランザクション ログがいっぱいになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8165b-119">In the Simple recovery model, when log records remain active for a long time (for example, a long and time-consuming transaction), log truncation can be delayed, and therefore can result in the filling up of transaction log.</span></span> <span data-ttu-id="8165b-120">また、ログの切り捨てを行っても、物理ログ ファイル (.ldf ファイル) のサイズは縮小されません。</span><span class="sxs-lookup"><span data-stu-id="8165b-120">Also, log truncation does not reduce the size of the physical log file (.ldf file).</span></span> <span data-ttu-id="8165b-121">物理ログ ファイルのサイズを削減するには、ログ ファイルを圧縮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8165b-121">To reduce the size of a physical log file, you need to shrink the log file.</span></span> <span data-ttu-id="8165b-122">トランザクション ログに関する問題のトラブルシューティングについては、「[トランザクション ログ &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md)」または Microsoft サポート技術情報 ([https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446)) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8165b-122">For information about troubleshooting issues around transaction log, see [The Transaction Log &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) or the Microsoft Support article at [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).</span></span>  
> -   <span data-ttu-id="8165b-123">DQS データベースの全体のバックアップまたは差分バックアップ、およびトランザクション ログのバックアップを定期的に実行して、データを特定の時点に復旧する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8165b-123">You must regularly perform a Full or Differential backup of the DQS databases and back up the transaction log as well to perform point-in-time recovery of data.</span></span> <span data-ttu-id="8165b-124">詳しくは、「[データベースの完全バックアップ &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md)」および「[トランザクション ログのバックアップ &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8165b-124">For more information, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) and [Back Up a Transaction Log &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
##  <a name="detachattach-the-dqs-databases"></a><a name="DetachAttach"></a> <span data-ttu-id="8165b-125">DQS データベースのデタッチ/アタッチ</span><span class="sxs-lookup"><span data-stu-id="8165b-125">Detach/Attach the DQS Databases</span></span>  
 <span data-ttu-id="8165b-126">DQS データベースを同じコンピューターの別の SQL Server インスタンスに変更する、またはデータベースを移動する場合は、DQS データベースのデータ ファイルおよびトランザクション ログ ファイルをデタッチし、その後 SQL Server の同じインスタンスまたは別のインスタンスにデータベースを再度アタッチします。</span><span class="sxs-lookup"><span data-stu-id="8165b-126">You can detach the data and transaction log files of the DQS databases, and then reattach the databases to the same or another instance of SQL Server if you want to change the DQS databases to a different instance of SQL Server on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="8165b-127">SQL Server でのデータベースのデタッチとアタッチの実行前と実行中の考慮事項について詳しくは、「[データベースのデタッチとアタッチ &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="8165b-127">For detailed information about things to consider before and during detaching and attaching databases in SQL Server, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="8165b-128">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="8165b-128">Related Tasks</span></span>  
  
|<span data-ttu-id="8165b-129">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="8165b-129">Task Description</span></span>|<span data-ttu-id="8165b-130">トピック</span><span class="sxs-lookup"><span data-stu-id="8165b-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="8165b-131">DQS データベースでのバックアップと復元の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8165b-131">Describes how to back up and restore the DQS databases.</span></span>|[<span data-ttu-id="8165b-132">DQS データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="8165b-132">Backing Up and Restoring DQS Databases</span></span>](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|<span data-ttu-id="8165b-133">DQS データベースをデタッチおよびアタッチする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8165b-133">Describes how to detach and attach the DQS databases.</span></span>|[<span data-ttu-id="8165b-134">DQS データベースのデタッチとアタッチ</span><span class="sxs-lookup"><span data-stu-id="8165b-134">Detaching and Attaching DQS Databases</span></span>](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a><span data-ttu-id="8165b-135">参照</span><span class="sxs-lookup"><span data-stu-id="8165b-135">See Also</span></span>  
 [<span data-ttu-id="8165b-136">DQS 管理</span><span class="sxs-lookup"><span data-stu-id="8165b-136">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  