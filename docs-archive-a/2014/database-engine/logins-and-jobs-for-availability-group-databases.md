---
title: 可用性グループのデータベースのログインとジョブの管理 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover
- failover [SQL Server], AlwaysOn Availability Groups
ms.assetid: d7da14d3-848c-44d4-8e49-d536a1158a61
author: rothja
ms.author: jroth
ms.openlocfilehash: 457f3ef946b5cfaf86a4a19774af63c5d7635882
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645787"
---
# <a name="management-of-logins-and-jobs-for-the-databases-of-an-availability-group-sql-server"></a><span data-ttu-id="9e9cc-102">可用性グループのデータベースのためのログインとジョブの管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9e9cc-102">Management of Logins and Jobs for the Databases of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="9e9cc-103">AlwaysOn 可用性グループのすべてのプライマリ データベースとその対応するセカンダリ データベース上で、ユーザー ログインと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブの同じセットを定期的に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-103">You should routinely maintain the same set of user logins and [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs on every primary database of an AlwaysOn availability group and the corresponding secondary databases.</span></span> <span data-ttu-id="9e9cc-104">可用性グループの可用性レプリカをホストする [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のすべてのインスタンス上でログインとジョブを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-104">The logins and jobs must be reproduced on every instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] that hosts an availability replica for the availability group.</span></span>  
  
-   <span data-ttu-id="9e9cc-105">**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]エージェントジョブ**</span><span class="sxs-lookup"><span data-stu-id="9e9cc-105">**[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Agent jobs**</span></span>  
  
     <span data-ttu-id="9e9cc-106">関連するジョブを、元のプライマリ レプリカをホストするサーバー インスタンスから元のセカンダリ レプリカをホストするサーバー インスタンスに手動でコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-106">You need to manually copy relevant jobs from the server instance that hosts the original primary replica to the server instances that host the original secondary replicas.</span></span> <span data-ttu-id="9e9cc-107">すべてのデータベースで、関連するジョブの先頭にロジックを追加して、そのジョブがプライマリ データベースでのみ実行されるようにする必要があります。つまり、ローカル レプリカがデータベースのプライマリ レプリカである場合のみ実行されるようにします。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-107">For all databases, you need to add logic at the beginning of each relevant job to make the job execute only on the primary database, that is, only when the local replica is the primary replica for the database.</span></span>  
  
     <span data-ttu-id="9e9cc-108">可用性グループの可用性レプリカをホストするサーバー インスタンスは、構成が異なる場合があります (別のテープ ドライブ文字など)。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-108">The server instances that host the availability replicas of an availability group might be configured differently, with different tape drive letters or such.</span></span> <span data-ttu-id="9e9cc-109">各可用性レプリカのジョブは、このような違いを考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-109">The jobs for each availability replica must allow for any such differences.</span></span>  
  
     <span data-ttu-id="9e9cc-110">バックアップ ジョブは、 [sys.fn_hadr_is_preferred_backup_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) 関数を使用し、可用性グループのバックアップ設定に従ってローカル レプリカがバックアップ用に推奨されるかどうかを識別できます。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-110">Notice that backup jobs can use the [sys.fn_hadr_is_preferred_backup_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function to identify whether the local replica is the preferred one for backups, according to the availability group backup preferences.</span></span> <span data-ttu-id="9e9cc-111">[メンテナンス プラン ウィザード](../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md) を使用して作成されたバックアップ ジョブは、ネイティブでこの関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-111">Backup jobs created using the [Maintenance Plan Wizard](../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md) natively use this function.</span></span> <span data-ttu-id="9e9cc-112">他のバックアップ ジョブでは、バックアップ ジョブの中でこの関数を条件として使用して、バックアップ ジョブが優先レプリカでのみ実行されるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-112">For other backup jobs, we recommend that you use this function as a condition in your backup jobs, so they execute only on the preferred replica.</span></span> <span data-ttu-id="9e9cc-113">詳細については、「[アクティブなセカンダリ: セカンダリレプリカでのバックアップ (AlwaysOn 可用性グループ)](availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-113">For more information, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
-   <span data-ttu-id="9e9cc-114">**ログイン**</span><span class="sxs-lookup"><span data-stu-id="9e9cc-114">**Logins**</span></span>  
  
     <span data-ttu-id="9e9cc-115">包含データベースを使用している場合は、データベースの包含ユーザーを構成でき、これらのユーザーにはセカンダリ レプリカをホストするサーバー インスタンス上のログインを作成する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-115">If you are using contained databases, you can configure contained users in the databases, and for these users, you do not need to create logins on the server instances that host a secondary replica.</span></span> <span data-ttu-id="9e9cc-116">非包含可用性データベースでは、可用性レプリカをホストするサーバー インスタンス上で、ログインするユーザーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-116">For a non-contained availability database, you will need to create users for the logins on the server instances that host the availability replicas.</span></span> <span data-ttu-id="9e9cc-117">詳細については、「[CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-117">For more information, see [CREATE USER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-user-transact-sql).</span></span>  
  
     <span data-ttu-id="9e9cc-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 認証またはローカル Windows ログインを使用するアプリケーションがある場合は、このトピックの「[SQL Server 認証またはローカル Windows ログインを使用するアプリケーションのログイン](../../2014/database-engine/logins-and-jobs-for-availability-group-databases.md#SSauthentication)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-118">If any of your applications use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication or a local Windows login, see [Logins Of Applications That Use SQL Server Authentication or a Local Windows Login](../../2014/database-engine/logins-and-jobs-for-availability-group-databases.md#SSauthentication), later in this topic.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9e9cc-119">SQL Server ログインが未定義のデータベース ユーザー、またはサーバー インスタンスで適切に定義されていないデータベース ユーザーは、インスタンスにログインできません。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-119">A database user for which the SQL Server login is undefined or is incorrectly defined on a server instance cannot log in to the instance.</span></span> <span data-ttu-id="9e9cc-120">このようなユーザーは、そのサーバー インスタンスのデータベースの *孤立ユーザー* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-120">Such a user is said to be an *orphaned user* of the database on that server instance.</span></span> <span data-ttu-id="9e9cc-121">ユーザーが特定のサーバー インスタンスで孤立している場合は、いつでもユーザー ログインをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-121">If a user is orphaned on a given server instance, you can set up the user logins at any time.</span></span> <span data-ttu-id="9e9cc-122">詳細については、「 [孤立ユーザーのトラブルシューティング &#40;SQL Server&#41;](../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md)を実行します。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-122">For more information, see [Troubleshoot Orphaned Users &#40;SQL Server&#41;](../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md).</span></span>  
  
-   <span data-ttu-id="9e9cc-123">**追加メタデータ**</span><span class="sxs-lookup"><span data-stu-id="9e9cc-123">**Additional metadata**</span></span>  
  
     <span data-ttu-id="9e9cc-124">ログインとジョブは、特定の可用性グループのセカンダリ レプリカをホストする各サーバー インスタンスで再作成する必要がある唯一の情報ではありません。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-124">Logins and jobs are not the only information that need to be recreated on each of the server instances that hosts an secondary replica for a given availability group.</span></span> <span data-ttu-id="9e9cc-125">たとえば、サーバー構成設定、資格情報、暗号化されたデータ、権限、サービス ブローカー アプリケーション、トリガー (サーバー レベル) などの再作成が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-125">For example, you might need to recreate server configuration settings, credentials, encrypted data, permissions, replication settings, service broker applications, triggers (at server level), and so forth.</span></span> <span data-ttu-id="9e9cc-126">詳細については、「 [データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-126">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
##  <a name="logins-of-applications-that-use-sql-server-authentication-or-a-local-windows-login"></a><a name="SSauthentication"></a> <span data-ttu-id="9e9cc-127">SQL Server 認証またはローカル Windows ログインを使用するアプリケーションのログイン</span><span class="sxs-lookup"><span data-stu-id="9e9cc-127">Logins Of Applications That Use SQL Server Authentication or a Local Windows Login</span></span>  
 <span data-ttu-id="9e9cc-128">アプリケーションで SQL Server 認証またはローカル Windows ログインを使用している場合、SID が一致しないと、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のリモート インスタンスでアプリケーションのログインを解決できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-128">If an application uses SQL Server Authentication or a local Windows login, mismatched SIDs can prevent the application's login from resolving on a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e9cc-129">SID が一致しないと、ログインはリモート サーバー インスタンスの孤立ユーザーになります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-129">The mismatched SIDs cause the login to become an orphaned user on the remote server instance.</span></span> <span data-ttu-id="9e9cc-130">この問題は、アプリケーションがフェールオーバー後にミラー化されたデータベースまたはログ配布データベース、またはバックアップから初期化されたレプリケーション サブスクライバー データベースに接続すると発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-130">This issue can occur when an application connects to a mirrored or log shipping database after a failover or to a replication subscriber database that was initialized from a backup.</span></span>  
  
 <span data-ttu-id="9e9cc-131">この問題を防ぐために、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のリモート インスタンスによってホストされているデータベースを使用するようにアプリケーションをセットアップする場合、予防策を講じることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-131">To prevent this issue, we recommend that you take preventative measures when you set up such an application to use a database that is hosted by a remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e9cc-132">予報策として、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のローカル インスタンスから [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のリモート インスタンスにログインとパスワードを転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-132">Prevention involves transferring the logins and the passwords from the local instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to the remote instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9e9cc-133">この問題を回避する方法の詳細については、サポート技術情報の記事 918992-「[SQL Server のインスタンス間でログインとパスワードを転送する方法](https://support.microsoft.com/kb/918992/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-133">For more information about how to prevent this issue, see KB article 918992-[How to transfer the logins and the passwords between instances of SQL Server](https://support.microsoft.com/kb/918992/)).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9e9cc-134">この問題は、さまざまなコンピューターの Windows ローカル アカウントに影響します。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-134">This problem affects Windows local accounts on different computers.</span></span> <span data-ttu-id="9e9cc-135">ただし、各コンピューターの SID は同じであるため、この問題はドメイン アカウントでは発生しません。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-135">However, this problem does not occur for domain accounts because the SID is the same on each of the computers.</span></span>  
  
 <span data-ttu-id="9e9cc-136">詳細については、「 [Orphaned Users with Database Mirroring and Log Shipping](https://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) 」(データベース ミラーリングとログ配布での孤立ユーザー) (データベース エンジンのブログ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-136">For more information, see [Orphaned Users with Database Mirroring and Log Shipping](https://blogs.msdn.com/b/sqlserverfaq/archive/2009/04/13/orphaned-users-with-database-mirroring-and-log-shipping.aspx) (a Database Engine blog).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="9e9cc-137">関連タスク</span><span class="sxs-lookup"><span data-stu-id="9e9cc-137">Related Tasks</span></span>  
  
-   [<span data-ttu-id="9e9cc-138">ログインの作成</span><span class="sxs-lookup"><span data-stu-id="9e9cc-138">Create a Login</span></span>](../relational-databases/security/authentication-access/create-a-login.md)  
  
-   <span data-ttu-id="9e9cc-139">[データベースユーザーを作成](../relational-databases/security/authentication-access/create-a-database-user.md)します。</span><span class="sxs-lookup"><span data-stu-id="9e9cc-139">[Create a Database User](../relational-databases/security/authentication-access/create-a-database-user.md).</span></span>  
  
-   [<span data-ttu-id="9e9cc-140">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="9e9cc-140">Create a Job</span></span>](../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="9e9cc-141">データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9e9cc-141">Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;</span></span>](../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e9cc-142">参照</span><span class="sxs-lookup"><span data-stu-id="9e9cc-142">See Also</span></span>  
 <span data-ttu-id="9e9cc-143">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9e9cc-143">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="9e9cc-144">[包含データベース](../relational-databases/databases/contained-databases.md) </span><span class="sxs-lookup"><span data-stu-id="9e9cc-144">[Contained Databases](../relational-databases/databases/contained-databases.md) </span></span>  
 [<span data-ttu-id="9e9cc-145">ジョブの作成</span><span class="sxs-lookup"><span data-stu-id="9e9cc-145">Create Jobs</span></span>](../ssms/agent/create-jobs.md)  
  
  