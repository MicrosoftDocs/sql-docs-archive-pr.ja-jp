---
title: AlwaysOn 可用性グループの構成のトラブルシューティング (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 01/31/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting [SQL Server], deploying
- Availability Groups [SQL Server], troubleshooting
- Availability Groups [SQL Server], configuring
ms.assetid: 8c222f98-7392-4faf-b7ad-5fb60ffa237e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 165036ba539c3392b1944282bd9d6126eb471a97
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741281"
---
# <a name="troubleshoot-alwayson-availability-groups-configuration-sql-server"></a><span data-ttu-id="0ed59-102">AlwaysOn 可用性グループの構成のトラブルシューティング (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0ed59-102">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)</span></span>
  <span data-ttu-id="0ed59-103">このトピックでは、サーバー インスタンスでの [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-103">This topic provides information to help you troubleshoot typical problems with configuring server instances for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="0ed59-104">構成に関する一般的な問題には、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] が無効になっている、アカウントが適切に構成されていない、データベース ミラーリング エンドポイントが存在しない、エンドポイントにアクセスできない (SQL Server エラー 1418)、ネットワーク アクセスが存在しない、データベース参加コマンドが失敗する (SQL Server エラー 35250) などがあります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-104">Typical configuration problems include [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] is disabled, accounts are incorrectly configured, the database mirroring endpoint does not exist, the endpoint is inaccessible (SQL Server Error 1418), network access does not exist, and a join database command fails (SQL Server Error 35250).</span></span>

> [!NOTE]
>  <span data-ttu-id="0ed59-105">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] の前提条件を満たしていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-105">Ensure that you are meeting the [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="0ed59-106">詳細については、「[AlwaysOn 可用性グループの前提条件、制限事項、および推奨事項 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-106">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>

 <span data-ttu-id="0ed59-107">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="0ed59-107">**In This Topic:**</span></span>

|<span data-ttu-id="0ed59-108">Section</span><span class="sxs-lookup"><span data-stu-id="0ed59-108">Section</span></span>|<span data-ttu-id="0ed59-109">説明</span><span class="sxs-lookup"><span data-stu-id="0ed59-109">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ed59-110">AlwaysOn 可用性グループが有効になっていない</span><span class="sxs-lookup"><span data-stu-id="0ed59-110">AlwaysOn Availability Groups Is Not Enabled</span></span>](#IsHadrEnabled)|<span data-ttu-id="0ed59-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスで [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]が有効になっていない場合、そのインスタンスでは可用性グループの作成がサポートされず、可用性レプリカをホストできません。</span><span class="sxs-lookup"><span data-stu-id="0ed59-111">If an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is not enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], the instance does not support availability group creation and cannot host any availability replicas.</span></span>|
|[<span data-ttu-id="0ed59-112">Accounts</span><span class="sxs-lookup"><span data-stu-id="0ed59-112">Accounts</span></span>](#Accounts)|<span data-ttu-id="0ed59-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を実行しているアカウントを適切に構成するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-113">Discusses requirements for correctly configuring the accounts under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running.</span></span>|
|[<span data-ttu-id="0ed59-114">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="0ed59-114">Endpoints</span></span>](#Endpoints)|<span data-ttu-id="0ed59-115">サーバー インスタンスのデータベース ミラーリング エンドポイントに関する問題の診断方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-115">Discusses how to diagnose issues with the database mirroring endpoint of a server instance.</span></span>|
|[<span data-ttu-id="0ed59-116">システム名</span><span class="sxs-lookup"><span data-stu-id="0ed59-116">System name</span></span>](#SystemName)|<span data-ttu-id="0ed59-117">エンドポイントの URL でサーバー インスタンスのシステム名を指定するためのその他の方法について概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-117">Summarizes the alternatives for specifying the system name of a server instance in an endpoint URL.</span></span>|
|[<span data-ttu-id="0ed59-118">ネットワーク アクセス</span><span class="sxs-lookup"><span data-stu-id="0ed59-118">Network access</span></span>](#NetworkAccess)|<span data-ttu-id="0ed59-119">可用性レプリカをホストしている各サーバー インスタンスが TCP で他の各サーバー インスタンスのポートにアクセスできる必要があるという要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-119">Documents the requirement that each server instance that is hosting an availability replica must be able to access the port of each of the other server instances over TCP.</span></span>|
|[<span data-ttu-id="0ed59-120">エンドポイント アクセス (SQLServer エラー 1418)</span><span class="sxs-lookup"><span data-stu-id="0ed59-120">Endpoint Access (SQL Server Error 1418)</span></span>](#Msg1418)|<span data-ttu-id="0ed59-121">この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] エラー メッセージに関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-121">Contains information about this [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] error message.</span></span>|
|[<span data-ttu-id="0ed59-122">データベースの参加の失敗 (SQL Server エラー 35250)</span><span class="sxs-lookup"><span data-stu-id="0ed59-122">Join Database Fails (SQL Server Error 35250)</span></span>](#JoinDbFails)|<span data-ttu-id="0ed59-123">プライマリ レプリカへの接続がアクティブでないためにセカンダリ データベースを可用性グループに参加させることができない問題について、考え得る原因と解決策について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-123">Discusses the possible causes and resolution of a failure to join secondary databases to an availability group because the connection to the primary replica is not active.</span></span>|
|[<span data-ttu-id="0ed59-124">読み取り専用ルーティングが正常に動作しない</span><span class="sxs-lookup"><span data-stu-id="0ed59-124">Read-Only Routing is Not Working Correctly</span></span>](#ROR)||
|[<span data-ttu-id="0ed59-125">関連タスク</span><span class="sxs-lookup"><span data-stu-id="0ed59-125">Related Tasks</span></span>](#RelatedTasks)|<span data-ttu-id="0ed59-126">[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] オンライン ブックの中の、可用性グループ構成のトラブルシューティングに特に関連するタスク指向のトピックの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-126">Contains a list of task-oriented topics in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] Books Online that are particularly relevant to troubleshooting an availability group configuration.</span></span>|
|[<span data-ttu-id="0ed59-127">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ed59-127">Related Content</span></span>](#RelatedContent)|<span data-ttu-id="0ed59-128">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] オンライン ブックの外部にある関連したリソースの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-128">Contains a list of relevant resources that are external to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Books Online.</span></span>|

##  <a name="alwayson-availability-groups-is-not-enabled"></a><a name="IsHadrEnabled"></a><span data-ttu-id="0ed59-129">AlwaysOn 可用性グループが有効になっていません</span><span class="sxs-lookup"><span data-stu-id="0ed59-129">AlwaysOn Availability Groups Is Not Enabled</span></span>
 <span data-ttu-id="0ed59-130">[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 機能は、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]の各インスタンスで有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-130">The [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] feature must be enabled on each of the instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="0ed59-131">詳細については、「[AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-131">For more information, see [Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md).</span></span>

##  <a name="accounts"></a><a name="Accounts"></a> <span data-ttu-id="0ed59-132">Accounts</span><span class="sxs-lookup"><span data-stu-id="0ed59-132">Accounts</span></span>
 <span data-ttu-id="0ed59-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の実行に使用するアカウントは、正しく構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-133">The accounts under which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running must be correctly configured.</span></span>

1.  <span data-ttu-id="0ed59-134">アカウントに適切な権限が与えられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-134">Do the accounts have the correct permissions?</span></span>

    1.  <span data-ttu-id="0ed59-135">パートナーを同じドメイン ユーザー アカウントで実行している場合は、両方の **master** データベースに正しいユーザー ログインが自動的に存在します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-135">If the partners run as the same domain user account, the correct user logins exist automatically in both **master** databases.</span></span> <span data-ttu-id="0ed59-136">この場合は、データベースのセキュリティ構成が単純になるため、望ましいといえます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-136">This simplifies the security configuration the database and is recommended.</span></span>

    2.  <span data-ttu-id="0ed59-137">2 つのサーバー インスタンスが別々のアカウントで実行されている場合、リモート サーバー インスタンスの **master** にそれぞれのアカウントのログインを作成する必要があります。また、そのログインには、対応するサーバー インスタンスのデータベース ミラーリング エンドポイントに接続するための CONNECT 権限を付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-137">If two server instances run as different accounts, the login each account must be created in **master** on the remote server instance, and that login must be granted CONNECT permissions to connect to the database mirroring endpoint of that server instance.</span></span> <span data-ttu-id="0ed59-138">詳細については、「[データベースミラーリングのログインアカウントの設定」または「AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-138">For more information, see[Set Up Login Accounts for Database Mirroring or AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-mirroring/set-up-login-accounts-database-mirroring-always-on-availability.md).</span></span>

2.  <span data-ttu-id="0ed59-139">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] がビルトイン アカウント (Local System、Local Service、Network Service など) で実行されている場合または非ドメイン アカウントで実行されている場合は、エンドポイント認証に証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-139">If [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is running as a built-in account, such as Local System, Local Service, or Network Service, or a nondomain account, you must use certificates for endpoint authentication.</span></span> <span data-ttu-id="0ed59-140">サービス アカウントで同じドメインのドメイン アカウントを使用している場合は、すべてのレプリカの場所の各サービス アカウントに対して CONNECT アクセスを付与するか、証明書を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-140">If your service accounts are using domain accounts in the same domain, you can choose to grant CONNECT access for each service account on all the replica locations or you can use certificates.</span></span> <span data-ttu-id="0ed59-141">詳細については、「[データベース ミラーリング エンドポイントでの証明書の使用 &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-141">For more information, see[Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md).</span></span>

##  <a name="endpoints"></a><a name="Endpoints"></a> <span data-ttu-id="0ed59-142">Endpoints</span><span class="sxs-lookup"><span data-stu-id="0ed59-142">Endpoints</span></span>
 <span data-ttu-id="0ed59-143">エンドポイントが正しく構成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-143">Endpoints must be correctly configured.</span></span>

1.  <span data-ttu-id="0ed59-144">可用性レプリカ (各 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリカの場所 *) をホストする*の各インスタンスにデータベース ミラーリング エンドポイントがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-144">Make sure that each instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is going to host an availability replica (each *replica location*) has a database mirroring endpoint.</span></span> <span data-ttu-id="0ed59-145">データベース ミラーリング エンドポイントが特定のサーバー インスタンスに存在するかどうかを確認するには、[sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) カタログ ビューを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-145">To determine whether a database mirroring endpoint exists on a given server instance, use the [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql) catalog view.</span></span> <span data-ttu-id="0ed59-146">詳細については、「[Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)」または「[データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-146">For more information, see either [Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md) or [Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md).</span></span>

2.  <span data-ttu-id="0ed59-147">ポート番号が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-147">Check that the port numbers are correct.</span></span>

     <span data-ttu-id="0ed59-148">サーバー インスタンスのデータベース ミラーリング エンドポイントに現在関連付けられているポートを識別するには、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-148">To identify the port currently associated with database mirroring endpoint of a server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>

    ```
    SELECT type_desc, port FROM sys.tcp_endpoints;
    GO
    ```

3.  <span data-ttu-id="0ed59-149">説明が困難な [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のセットアップに関する問題については、各サーバー インスタンスを調査して、それぞれが正しいポートでリッスンしているかどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="0ed59-149">For [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] setup issues that are difficult to explain, we recommend that you inspect each server instance to determine whether it is listening on the correct ports.</span></span> <span data-ttu-id="0ed59-150">ポートの可用性の検証については、「 [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-150">For information about verifying port availability, see [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>

4.  <span data-ttu-id="0ed59-151">エンドポイントが開始されていること (STATE = STARTED) を確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-151">Make sure that the endpoints are started (STATE=STARTED).</span></span> <span data-ttu-id="0ed59-152">各サーバー インスタンスで、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-152">On each server instance, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>

    ```
    SELECT state_desc FROM sys.database_mirroring_endpoints
    ```

     <span data-ttu-id="0ed59-153">**state_desc** 列の詳細については、「[sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-153">For more information about the **state_desc** column, see [sys.database_mirroring_endpoints &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql).</span></span>

     <span data-ttu-id="0ed59-154">エンドポイントを開始するには、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-154">To start an endpoint, use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>

    ```
    ALTER ENDPOINT Endpoint_Mirroring 
    STATE = STARTED 
    AS TCP (LISTENER_PORT = <port_number>)
    FOR database_mirroring (ROLE = ALL);
    GO
    ```

     <span data-ttu-id="0ed59-155">詳細については、「 [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-155">For more information, see [ALTER ENDPOINT &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql).</span></span>

5.  <span data-ttu-id="0ed59-156">他のサーバーからのログインに、CONNECT 権限があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-156">Make sure that the login from the other server has CONNECT permission.</span></span> <span data-ttu-id="0ed59-157">あるエンドポイントに対して CONNECT 権限のあるユーザーを確認するには、各サーバー インスタンスで、次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-157">To determine who has CONNECT permission for an endpoint, on each server instance use the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement:</span></span>

    ```
    SELECT 'Metadata Check';
    SELECT EP.name, SP.STATE, 
       CONVERT(nvarchar(38), suser_name(SP.grantor_principal_id)) 
          AS GRANTOR, 
       SP.TYPE AS PERMISSION,
       CONVERT(nvarchar(46),suser_name(SP.grantee_principal_id)) 
          AS GRANTEE 
       FROM sys.server_permissions SP , sys.endpoints EP
       WHERE SP.major_id = EP.endpoint_id
       ORDER BY Permission,grantor, grantee; 
    GO

    ```

##  <a name="system-name"></a><a name="SystemName"></a> <span data-ttu-id="0ed59-158">System Name</span><span class="sxs-lookup"><span data-stu-id="0ed59-158">System Name</span></span>
 <span data-ttu-id="0ed59-159">エンドポイントの URL におけるサーバー インスタンスのシステム名には、システムを明確に識別できる任意の名前を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-159">For the system name of a server instance in an endpoint URL, you can use any name that unambiguously identifies the system.</span></span> <span data-ttu-id="0ed59-160">サーバー アドレスには、システム名 (システムが同じドメインに存在する場合)、完全修飾ドメイン名、または IP アドレス (可能であれば静的 IP アドレス) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-160">The server address can be a system name (if the systems are in the same domain), a fully qualified domain name, or an IP address (preferably, a static IP address).</span></span> <span data-ttu-id="0ed59-161">完全修飾ドメイン名を使用すると動作が保証されます。</span><span class="sxs-lookup"><span data-stu-id="0ed59-161">Using the fully qualified domain name is guaranteed to work.</span></span> <span data-ttu-id="0ed59-162">詳細については、「 [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-162">For more information, see [Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md).</span></span>

##  <a name="network-access"></a><a name="NetworkAccess"></a> <span data-ttu-id="0ed59-163">Network Access</span><span class="sxs-lookup"><span data-stu-id="0ed59-163">Network Access</span></span>
 <span data-ttu-id="0ed59-164">可用性レプリカをホストしている各サーバー インスタンスは、TCP で他の各サーバー インスタンスのポートにアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-164">Each server instance that is hosting an availability replica must be able to access the port of each of the other server instance over TCP.</span></span> <span data-ttu-id="0ed59-165">これは、サーバー インスタンスが相互に信頼関係を持たない別のドメイン (信頼されていないドメイン) に存在する場合に特に重要になります。</span><span class="sxs-lookup"><span data-stu-id="0ed59-165">This is especially important if the server instances are in different domains that do not trust each other (untrusted domains).</span></span>

##  <a name="endpoint-access-sql-server-error-1418"></a><a name="Msg1418"></a> <span data-ttu-id="0ed59-166">エンドポイント アクセス (SQLServer エラー 1418)</span><span class="sxs-lookup"><span data-stu-id="0ed59-166">Endpoint Access (SQL Server Error 1418)</span></span>
 <span data-ttu-id="0ed59-167">この [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] メッセージは、エンドポイントの URL で指定されたサーバー ネットワーク アドレスに到達できないか、そのアドレスが存在しないことを意味し、ネットワーク アドレス名を確認してコマンドを再実行するように示しています。</span><span class="sxs-lookup"><span data-stu-id="0ed59-167">This [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] message indicates that the server network address specified in the endpoint URL cannot be reached or does not exist, and it suggests that you verify the network address name and reissue the command.</span></span> <span data-ttu-id="0ed59-168">詳細については、「 [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ed59-168">For more information, see [MSSQLSERVER_1418](../../../relational-databases/errors-events/mssqlserver-1418-database-engine-error.md).</span></span>

##  <a name="join-database-fails-sql-server-error-35250"></a><a name="JoinDbFails"></a> <span data-ttu-id="0ed59-169">データベースの参加の失敗 (SQL Server エラー 35250)</span><span class="sxs-lookup"><span data-stu-id="0ed59-169">Join Database Fails (SQL Server Error 35250)</span></span>
 <span data-ttu-id="0ed59-170">ここでは、プライマリ レプリカへの接続がアクティブでないためにセカンダリ データベースを可用性グループに参加させることができない問題について、考え得る原因と解決策について説明します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-170">This section discusses the possible causes and resolution of a failure to join secondary databases to the availability group because the connection to the primary replica is not active.</span></span>

 <span data-ttu-id="0ed59-171">**解決策:**</span><span class="sxs-lookup"><span data-stu-id="0ed59-171">**Resolution:**</span></span>

1.  <span data-ttu-id="0ed59-172">ファイアウォールの設定を調べて、プライマリ レプリカをホストするサーバー インスタンスとセカンダリ レプリカをホストするサーバー インスタンス (既定ではポート 5022) の間でエンドポイント ポート通信が許可されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-172">Check the firewall setting to see if whether allows the endpoint port communication between the server instances that host primary replica and the secondary replica (port 5022 by default).</span></span>

2.  <span data-ttu-id="0ed59-173">ネットワーク サービス アカウントにエンドポイントへの接続権限があるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-173">Check whether the network service account has connect permission to the endpoint.</span></span>

##  <a name="read-only-routing-is-not-working-correctly"></a><a name="ROR"></a> <span data-ttu-id="0ed59-174">読み取り専用ルーティングが正常に動作しない</span><span class="sxs-lookup"><span data-stu-id="0ed59-174">Read-Only Routing is Not Working Correctly</span></span>
 <span data-ttu-id="0ed59-175">次の構成値の設定を確認し、必要に応じて修正します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-175">Verify the following configuration values settings and correct them if necessary.</span></span>

||<span data-ttu-id="0ed59-176">対象</span><span class="sxs-lookup"><span data-stu-id="0ed59-176">On...</span></span>|<span data-ttu-id="0ed59-177">アクション</span><span class="sxs-lookup"><span data-stu-id="0ed59-177">Action</span></span>|<span data-ttu-id="0ed59-178">説明</span><span class="sxs-lookup"><span data-stu-id="0ed59-178">Comments</span></span>|<span data-ttu-id="0ed59-179">Link</span><span class="sxs-lookup"><span data-stu-id="0ed59-179">Link</span></span>|
|------|---------|------------|--------------|----------|
|<span data-ttu-id="0ed59-180">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-180">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-181">現在のプライマリ レプリカ</span><span class="sxs-lookup"><span data-stu-id="0ed59-181">Current primary replica</span></span>|<span data-ttu-id="0ed59-182">可用性グループ リスナーがオンラインであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-182">Ensure that the availability group listener is online.</span></span>|<span data-ttu-id="0ed59-183">**リスナーがオンラインになっているかどうかを確認するには:**</span><span class="sxs-lookup"><span data-stu-id="0ed59-183">**To verify whether the listener is online:**</span></span><br /><br /> `SELECT * FROM sys.dm_tcp_listener_states;`<br /><br /> <span data-ttu-id="0ed59-184">**オフラインのリスナーを再起動するには:**</span><span class="sxs-lookup"><span data-stu-id="0ed59-184">**To restart an offline listener:**</span></span><br /><br /> `ALTER AVAILABILITY GROUP myAG RESTART LISTENER 'myAG_Listener';`|[<span data-ttu-id="0ed59-185">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-185">sys.dm_tcp_listener_states &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql)<br /><br /> [<span data-ttu-id="0ed59-186">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-186">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|<span data-ttu-id="0ed59-187">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-187">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-188">現在のプライマリ レプリカ</span><span class="sxs-lookup"><span data-stu-id="0ed59-188">Current primary replica</span></span>|<span data-ttu-id="0ed59-189">READ_ONLY_ROUTING_LIST に、読み取り可能なセカンダリ レプリカをホストしているサーバー インスタンスだけが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-189">Ensure that the READ_ONLY_ROUTING_LIST contains only server instances that are hosting a readable secondary replica.</span></span>|<span data-ttu-id="0ed59-190">**読み取り可能なセカンダリ レプリカを識別するには:** sys.availability_replicas  (**secondary_role_allow_connections_desc** 列)</span><span class="sxs-lookup"><span data-stu-id="0ed59-190">**To identify readable secondary replicas:** sys.availability_replicas  (**secondary_role_allow_connections_desc** column)</span></span><br /><br /> <span data-ttu-id="0ed59-191">**読み取り専用ルーティング リストを表示するには:** sys.availability_read_only_routing_lists</span><span class="sxs-lookup"><span data-stu-id="0ed59-191">**To view a read-only routing list:** sys.availability_read_only_routing_lists</span></span><br /><br /> <span data-ttu-id="0ed59-192">**読み取り専用ルーティング リストを変更するには:** ALTER AVAILABILITY GROUP</span><span class="sxs-lookup"><span data-stu-id="0ed59-192">**To change a read-only routing list:** ALTER AVAILABILITY GROUP</span></span>|[<span data-ttu-id="0ed59-193">sys.availability_replicas &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-193">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)<br /><br /> [<span data-ttu-id="0ed59-194">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-194">sys.availability_read_only_routing_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-read-only-routing-lists-transact-sql)<br /><br /> [<span data-ttu-id="0ed59-195">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-195">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|<span data-ttu-id="0ed59-196">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-196">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-197">read_only_routing_list にあるすべてのレプリカ</span><span class="sxs-lookup"><span data-stu-id="0ed59-197">Every replica in the read_only_routing_list</span></span>|<span data-ttu-id="0ed59-198">READ_ONLY_ROUTING_URL ポートが Windows ファイアウォールでブロックされていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-198">Ensure that the Windows firewall is not blocking the READ_ONLY_ROUTING_URL port.</span></span>|-|[<span data-ttu-id="0ed59-199">データベース エンジン アクセスを有効にするための Windows ファイアウォールを構成する</span><span class="sxs-lookup"><span data-stu-id="0ed59-199">Configure a Windows Firewall for Database Engine Access</span></span>](../../configure-windows/configure-a-windows-firewall-for-database-engine-access.md)|
|<span data-ttu-id="0ed59-200">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-200">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-201">read_only_routing_list にあるすべてのレプリカ</span><span class="sxs-lookup"><span data-stu-id="0ed59-201">Every replica in the read_only_routing_list</span></span>|<span data-ttu-id="0ed59-202">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 構成マネージャーで次のことを確認します:</span><span class="sxs-lookup"><span data-stu-id="0ed59-202">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Configuration Manager, verify that:</span></span><br /><br /> <span data-ttu-id="0ed59-203">SQL Server のリモート接続が有効になっている。</span><span class="sxs-lookup"><span data-stu-id="0ed59-203">SQL Server remote connectivity is enabled.</span></span><br /><br /> <span data-ttu-id="0ed59-204">TCP/IP が有効になっている。</span><span class="sxs-lookup"><span data-stu-id="0ed59-204">TCP/IP is enabled.</span></span><br /><br /> <span data-ttu-id="0ed59-205">IP アドレスが正しく構成されている。</span><span class="sxs-lookup"><span data-stu-id="0ed59-205">The IP addresses are configured correctly.</span></span>|-|[<span data-ttu-id="0ed59-206">サーバー プロパティの表示または変更 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-206">View or Change Server Properties &#40;SQL Server&#41;</span></span>](../../configure-windows/view-or-change-server-properties-sql-server.md)<br /><br /> [<span data-ttu-id="0ed59-207">特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-207">Configure a Server to Listen on a Specific TCP Port &#40;SQL Server Configuration Manager&#41;</span></span>](../../configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)|
|<span data-ttu-id="0ed59-208">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-208">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-209">read_only_routing_list にあるすべてのレプリカ</span><span class="sxs-lookup"><span data-stu-id="0ed59-209">Every replica in the read_only_routing_list</span></span>|<span data-ttu-id="0ed59-210">READ_ONLY_ROUTING_URL (TCP<strong>:// *`system-address`* :</strong>*ポート*) に正しい完全修飾ドメイン名 (FQDN) とポート番号が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-210">Ensure that the READ_ONLY_ROUTING_URL (TCP<strong>://*`system-address`*:</strong>*port*) contains the correct fully-qualified domain name (FQDN) and port number.</span></span>|-|[<span data-ttu-id="0ed59-211">AlwaysOn の read_only_routing_url の計算</span><span class="sxs-lookup"><span data-stu-id="0ed59-211">Calculating read_only_routing_url for AlwaysOn</span></span>](https://docs.microsoft.com/archive/blogs/mattn/calculating-read_only_routing_url-for-alwayson)<br /><br /> [<span data-ttu-id="0ed59-212">sys.availability_replicas &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-212">sys.availability_replicas &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)<br /><br /> [<span data-ttu-id="0ed59-213">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-213">ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-availability-group-transact-sql)|
|<span data-ttu-id="0ed59-214">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span><span class="sxs-lookup"><span data-stu-id="0ed59-214">![Checkbox](../../media/checkboxemptycenterxtraspacetopandright.gif "Checkbox")</span></span>|<span data-ttu-id="0ed59-215">クライアント システム</span><span class="sxs-lookup"><span data-stu-id="0ed59-215">Client system</span></span>|<span data-ttu-id="0ed59-216">クライアント ドライバーが読み取り専用のルーティングをサポートしていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0ed59-216">Verify that the client driver supports read-only routing.</span></span>|-|[<span data-ttu-id="0ed59-217">AlwaysOn クライアント接続 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0ed59-217">AlwaysOn Client Connectivity (SQL Server)</span></span>](always-on-client-connectivity-sql-server.md)|

##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="0ed59-218">関連タスク</span><span class="sxs-lookup"><span data-stu-id="0ed59-218">Related Tasks</span></span>

-   [<span data-ttu-id="0ed59-219">可用性グループの作成と構成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-219">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)

-   [<span data-ttu-id="0ed59-220">Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-220">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)

-   [<span data-ttu-id="0ed59-221">可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-221">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)

-   [<span data-ttu-id="0ed59-222">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-222">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)

-   [<span data-ttu-id="0ed59-223">失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-223">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)

-   [<span data-ttu-id="0ed59-224">可用性グループのデータベースのためのログインとジョブの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-224">Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;</span></span>](../../logins-and-jobs-for-availability-group-databases.md)

-   [<span data-ttu-id="0ed59-225">データベースを別のサーバー インスタンスで使用できるようにするときのメタデータの管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-225">Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;</span></span>](../../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)

##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="0ed59-226">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="0ed59-226">Related Content</span></span>

-   <span data-ttu-id="0ed59-227">[フェールオーバー クラスターのイベントおよびログを表示する](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0ed59-227">[View Events and Logs for a Failover Cluster](https://technet.microsoft.com/library/cc772342\(WS.10\).aspx)</span></span>

-   [<span data-ttu-id="0ed59-228">Get-ClusterLog フェールオーバー クラスター コマンドレット</span><span class="sxs-lookup"><span data-stu-id="0ed59-228">Get-ClusterLog Failover Cluster Cmdlet</span></span>](https://technet.microsoft.com/library/ee461045.aspx)

-   [<span data-ttu-id="0ed59-229">SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ</span><span class="sxs-lookup"><span data-stu-id="0ed59-229">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)

## <a name="see-also"></a><span data-ttu-id="0ed59-230">参照</span><span class="sxs-lookup"><span data-stu-id="0ed59-230">See Also</span></span>
 <span data-ttu-id="0ed59-231">[データベースミラーリングのトランスポートセキュリティと AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-mirroring/transport-security-database-mirroring-always-on-availability.md) [クライアントのネットワーク構成](../../configure-windows/client-network-configuration.md)の[前提条件、制限](prereqs-restrictions-recommendations-always-on-availability.md)事項、AlwaysOn 可用性グループ &#40;SQL Server に関する推奨事項&#41;</span><span class="sxs-lookup"><span data-stu-id="0ed59-231">[Transport Security for Database Mirroring and AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-mirroring/transport-security-database-mirroring-always-on-availability.md) [Client Network Configuration](../../configure-windows/client-network-configuration.md) [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)</span></span>

