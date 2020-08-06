---
title: 可用性レプリカでのバックアップの構成 (SQLServer) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91a781d957eb2f5a81d323fc3c65c93e34945c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741309"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a><span data-ttu-id="f9987-102">可用性レプリカでのバックアップの構成 (SQLServer)</span><span class="sxs-lookup"><span data-stu-id="f9987-102">Configure Backup on Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="f9987-103">このトピックでは、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]で [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]、または PowerShell を使用して、AlwaysOn 可用性グループのセカンダリ レプリカでバックアップを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f9987-103">This topic describes how to configure backup on secondary replicas for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f9987-104">セカンダリレプリカでのバックアップの概要については、「[アクティブなセカンダリ: セカンダリレプリカでのバックアップ (AlwaysOn 可用性グループ)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9987-104">For an introduction to backup on secondary replicas, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f9987-105">はじめに</span><span class="sxs-lookup"><span data-stu-id="f9987-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="f9987-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="f9987-106">Prerequisites</span></span>  
 <span data-ttu-id="f9987-107">プライマリ レプリカをホストするサーバー インスタンスに接続されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-107">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f9987-108">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="f9987-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f9987-109">Permissions</span><span class="sxs-lookup"><span data-stu-id="f9987-109">Permissions</span></span>  
  
|<span data-ttu-id="f9987-110">タスク</span><span class="sxs-lookup"><span data-stu-id="f9987-110">Task</span></span>|<span data-ttu-id="f9987-111">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="f9987-111">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="f9987-112">可用性グループの作成時にセカンダリ レプリカでバックアップを構成するには</span><span class="sxs-lookup"><span data-stu-id="f9987-112">To configure backup on secondary replicas when creating an availability group</span></span>|<span data-ttu-id="f9987-113">**sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。</span><span class="sxs-lookup"><span data-stu-id="f9987-113">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="f9987-114">可用性グループまたは可用性レプリカを変更するには</span><span class="sxs-lookup"><span data-stu-id="f9987-114">To modify an availability group or availability replica</span></span>|<span data-ttu-id="f9987-115">可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="f9987-115">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f9987-116">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="f9987-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f9987-117">**セカンダリ レプリカでバックアップを構成するには**</span><span class="sxs-lookup"><span data-stu-id="f9987-117">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="f9987-118">オブジェクト エクスプローラーで、プライマリ レプリカをホストするサーバー インスタンスに接続し、サーバー名をクリックしてサーバー ツリーを展開します。</span><span class="sxs-lookup"><span data-stu-id="f9987-118">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f9987-119">**[AlwaysOn 高可用性]** ノードと **[可用性グループ]** ノードを展開します。</span><span class="sxs-lookup"><span data-stu-id="f9987-119">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="f9987-120">バックアップ優先設定を構成する可用性グループをクリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9987-120">Click the availability group whose backup preferences you want to configure, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="f9987-121">**[可用性グループのプロパティ]** ダイアログ ボックスで、 **[バックアップの設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9987-121">In the **Availability Group Properties** dialog box, select **Backup Preferences** page.</span></span>  
  
5.  <span data-ttu-id="f9987-122">**[バックアップを実行する場所]** パネルで、可用性グループの自動バックアップ設定を選択します。次のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f9987-122">On the **Where should backups occur?** panel, select the automated backup preference for the availability group, one of:</span></span>  
  
     <span data-ttu-id="f9987-123">**[セカンダリを優先]**</span><span class="sxs-lookup"><span data-stu-id="f9987-123">**Prefer Secondary**</span></span>  
     <span data-ttu-id="f9987-124">オンラインのレプリカがプライマリ レプリカのみである場合を除き、セカンダリ レプリカでバックアップを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-124">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="f9987-125">オンラインのレプリカがプライマリ レプリカのみである場合は、プライマリ レプリカでバックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-125">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="f9987-126">既定のオプションです。</span><span class="sxs-lookup"><span data-stu-id="f9987-126">This is the default option.</span></span>  
  
     <span data-ttu-id="f9987-127">**[セカンダリのみ]**</span><span class="sxs-lookup"><span data-stu-id="f9987-127">**Secondary only**</span></span>  
     <span data-ttu-id="f9987-128">バックアップをプライマリ レプリカでは実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-128">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="f9987-129">オンラインのレプリカがプライマリ レプリカだけの場合、バックアップは実行されません。</span><span class="sxs-lookup"><span data-stu-id="f9987-129">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Primary`  
     <span data-ttu-id="f9987-130">バックアップを常にプライマリ レプリカで実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-130">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="f9987-131">このオプションは、差分バックアップの作成など、バックアップがセカンダリ レプリカで実行されたときにはサポートされないバックアップ機能が必要な場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="f9987-131">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9987-132">ログ配布を使用して可用性グループのセカンダリ データベースを準備する場合は、すべてのセカンダリ データベースの準備が完了し、それらを可用性グループに参加させるまで、自動バックアップ設定を  `Primary` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-132">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     <span data-ttu-id="f9987-133">**[任意のレプリカ]**</span><span class="sxs-lookup"><span data-stu-id="f9987-133">**Any Replica**</span></span>  
     <span data-ttu-id="f9987-134">バックアップを実行するレプリカを選択するときにバックアップ ジョブが可用性レプリカのロールを無視するように指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-134">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="f9987-135">バックアップ ジョブは、動作状態および接続状態と組み合わせて、各可用性レプリカのバックアップ優先順位などの他の要素を評価する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-135">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9987-136">自動バックアップ設定の適用はありません。</span><span class="sxs-lookup"><span data-stu-id="f9987-136">There is no enforcement of the automated backup preference setting.</span></span> <span data-ttu-id="f9987-137">この優先設定の解釈は、特定の可用性グループのデータベースに対するバックアップ ジョブのスクリプトでのロジックに依存します (ロジックが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="f9987-137">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="f9987-138">自動バックアップ設定はアドホック バックアップには影響しません。</span><span class="sxs-lookup"><span data-stu-id="f9987-138">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="f9987-139">詳細については、このトピックの「 [補足情報: セカンダリ レプリカでバックアップを構成した後](#FollowUp) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9987-139">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
6.  <span data-ttu-id="f9987-140">**[レプリカのバックアップの優先順位]** グリッドを使用して、可用性レプリカのバックアップの優先順位を変更します。</span><span class="sxs-lookup"><span data-stu-id="f9987-140">Use the **Replica backup priorities** grid to change the backup priority of the availability replicas.</span></span> <span data-ttu-id="f9987-141">このグリッドには、可用性グループのレプリカをホストする各サーバー インスタンスの現在のバックアップの優先順位が表示されます。</span><span class="sxs-lookup"><span data-stu-id="f9987-141">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="f9987-142">グリッドの列は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f9987-142">The grid columns are as follows:</span></span>  
  
     <span data-ttu-id="f9987-143">**サーバー インスタンス**</span><span class="sxs-lookup"><span data-stu-id="f9987-143">**Server Instance**</span></span>  
     <span data-ttu-id="f9987-144">可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="f9987-144">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
     <span data-ttu-id="f9987-145">**[バックアップ優先度 (最小 = 1、最高 = 100)]**</span><span class="sxs-lookup"><span data-stu-id="f9987-145">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
     <span data-ttu-id="f9987-146">同じ可用性グループ内の他のレプリカと比較して、このレプリカでバックアップを実行する優先順位を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-146">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="f9987-147">値は 0 ～ 100 の範囲の整数です。</span><span class="sxs-lookup"><span data-stu-id="f9987-147">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="f9987-148">1 は最も低い優先順位を示し、100 は最も高い優先順位を示します。</span><span class="sxs-lookup"><span data-stu-id="f9987-148">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="f9987-149">たとえば、 **Backup Priority** = 1 の場合、現在使用可能な可用性レプリカにそれより高い優先順位のものがない場合にのみ、その可用性レプリカがバックアップの実行に対して選択されます。</span><span class="sxs-lookup"><span data-stu-id="f9987-149">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
     <span data-ttu-id="f9987-150">**[レプリカの除外]**</span><span class="sxs-lookup"><span data-stu-id="f9987-150">**Exclude Replica**</span></span>  
     <span data-ttu-id="f9987-151">バックアップの実行時にこの可用性レプリカを選択しない場合に選択します。</span><span class="sxs-lookup"><span data-stu-id="f9987-151">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="f9987-152">これは、たとえば、バックアップをフェールオーバーすることがないリモート可用性レプリカのような場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="f9987-152">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
7.  <span data-ttu-id="f9987-153">変更をコミットするには、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f9987-153">To commit your changes, click **OK**.</span></span>  
  
 <span data-ttu-id="f9987-154">**別の方法で [バックアップの設定] ページにアクセスする**</span><span class="sxs-lookup"><span data-stu-id="f9987-154">**Alternative ways to access the Backup Preferences page**</span></span>  
  
-   <span data-ttu-id="f9987-155">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="f9987-155">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="f9987-156">可用性グループへのレプリカ追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f9987-156">Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
-   <span data-ttu-id="f9987-157">[[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="f9987-157">[Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f9987-158">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="f9987-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="f9987-159">**セカンダリ レプリカでバックアップを構成するには**</span><span class="sxs-lookup"><span data-stu-id="f9987-159">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="f9987-160">プライマリ レプリカをホストするサーバー インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="f9987-160">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f9987-161">新しい可用性グループの場合は、[CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-161">For a new availability group, use the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) statement.</span></span> <span data-ttu-id="f9987-162">既存の可用性グループを変更する場合は、[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-162">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a><span data-ttu-id="f9987-163">PowerShell の使用</span><span class="sxs-lookup"><span data-stu-id="f9987-163">Using PowerShell</span></span>  

### <a name="to-configure-backup-on-secondary-replicas"></a><span data-ttu-id="f9987-164">セカンダリ レプリカでバックアップを構成するには</span><span class="sxs-lookup"><span data-stu-id="f9987-164">To configure backup on secondary replicas</span></span>
  
1.  <span data-ttu-id="f9987-165">既定 (`cd`) を、プライマリ レプリカをホストするサーバー インスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-165">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f9987-166">必要に応じて、追加または変更する各可用性レプリカのバックアップの優先順位を構成します。</span><span class="sxs-lookup"><span data-stu-id="f9987-166">Optionally, configure the backup priority of each availability replica that you are adding or modifying.</span></span> <span data-ttu-id="f9987-167">この優先順位は、プライマリ レプリカをホストするサーバー インスタンスによって使用され、可用性グループ内のデータベースで自動バックアップ要求を処理するレプリカを決定します (優先順位の高いレプリカが選択されます)。</span><span class="sxs-lookup"><span data-stu-id="f9987-167">This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group (the replica with highest priority is chosen).</span></span> <span data-ttu-id="f9987-168">この優先順位には、0 ～ 100 の数値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f9987-168">This priority can be any number between 0 and 100, inclusive.</span></span> <span data-ttu-id="f9987-169">優先順位が 0 の場合は、レプリカがバックアップ要求を処理する対象と見なされないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f9987-169">A priority of 0 indicates that the replica should not be considered as a candidate for servicing backup requests.</span></span>  <span data-ttu-id="f9987-170">既定の設定は 50 です。</span><span class="sxs-lookup"><span data-stu-id="f9987-170">The default setting is 50.</span></span>  
  
     <span data-ttu-id="f9987-171">可用性グループに可用性レプリカを追加する場合は、`New-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-171">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="f9987-172">既存の可用性レプリカを変更する場合は、`Set-SqlAvailabilityReplica` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-172">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="f9987-173">どちらの場合も、 `BackupPriority` *n*パラメーターを指定します。 *n*は 0 ~ 100 の値です。</span><span class="sxs-lookup"><span data-stu-id="f9987-173">In either case, specify the `BackupPriority`*n* parameter, where *n* is a value from 0 to 100.</span></span>  
  
     <span data-ttu-id="f9987-174">たとえば、次のコマンドは、可用性レプリカ `MyReplica` のバックアップの優先順位を `60` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-174">For example, the following command sets the backup priority of the availability replica `MyReplica` to `60`.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -BackupPriority 60 -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  <span data-ttu-id="f9987-175">必要に応じて、作成または変更している可用性グループの自動バックアップ設定を構成します。</span><span class="sxs-lookup"><span data-stu-id="f9987-175">Optionally, configure the automated backup preference for the availability group that you are creating  or modifying.</span></span> <span data-ttu-id="f9987-176">この優先設定は、バックアップを実行する場所を選択するときにバックアップ ジョブがプライマリ レプリカを評価する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-176">This preference indicates how a backup job should evaluate the primary replica when choosing where to perform backups.</span></span> <span data-ttu-id="f9987-177">既定の設定では、セカンダリ レプリカが優先されます。</span><span class="sxs-lookup"><span data-stu-id="f9987-177">The default setting is to prefer secondary replicas.</span></span>  
  
     <span data-ttu-id="f9987-178">可用性グループを作成する場合は、`New-SqlAvailabilityGroup` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-178">When creating an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="f9987-179">既存の可用性グループを変更する場合は、`Set-SqlAvailabilityGroup` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-179">When modifying an existing availability group, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="f9987-180">どちらの場合も `AutomatedBackupPreference` パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-180">In either case, specify the `AutomatedBackupPreference` parameter.</span></span>  
  
     <span data-ttu-id="f9987-181">パラメーターの説明</span><span class="sxs-lookup"><span data-stu-id="f9987-181">where,</span></span>  
  
     `Primary`  
     <span data-ttu-id="f9987-182">バックアップを常にプライマリ レプリカで実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-182">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="f9987-183">このオプションは、差分バックアップの作成など、バックアップがセカンダリ レプリカで実行されたときにはサポートされないバックアップ機能が必要な場合に役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="f9987-183">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9987-184">ログ配布を使用して可用性グループのセカンダリ データベースを準備する場合は、すべてのセカンダリ データベースの準備が完了し、それらを可用性グループに参加させるまで、自動バックアップ設定を  `Primary` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-184">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     `SecondaryOnly`  
     <span data-ttu-id="f9987-185">バックアップをプライマリ レプリカでは実行しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-185">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="f9987-186">オンラインのレプリカがプライマリ レプリカだけの場合、バックアップは実行されません。</span><span class="sxs-lookup"><span data-stu-id="f9987-186">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Secondary`  
     <span data-ttu-id="f9987-187">オンラインのレプリカがプライマリ レプリカのみである場合を除き、セカンダリ レプリカでバックアップを実行することを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-187">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="f9987-188">オンラインのレプリカがプライマリ レプリカのみである場合は、プライマリ レプリカでバックアップを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-188">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="f9987-189">これは既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="f9987-189">This is the default behavior.</span></span>  
  
     `None`  
     <span data-ttu-id="f9987-190">バックアップを実行するレプリカを選択するときにバックアップ ジョブが可用性レプリカのロールを無視するように指定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-190">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="f9987-191">バックアップ ジョブは、動作状態および接続状態と組み合わせて、各可用性レプリカのバックアップ優先順位などの他の要素を評価する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-191">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and  connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="f9987-192">`AutomatedBackupPreference` は適用されません。</span><span class="sxs-lookup"><span data-stu-id="f9987-192">There is no enforcement of `AutomatedBackupPreference`.</span></span> <span data-ttu-id="f9987-193">この優先設定の解釈は、特定の可用性グループのデータベースに対するバックアップ ジョブのスクリプトでのロジックに依存します (ロジックが存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="f9987-193">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="f9987-194">自動バックアップ設定はアドホック バックアップには影響しません。</span><span class="sxs-lookup"><span data-stu-id="f9987-194">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="f9987-195">詳細については、このトピックの「 [補足情報: セカンダリ レプリカでバックアップを構成した後](#FollowUp) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9987-195">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
     <span data-ttu-id="f9987-196">たとえば、次のコマンドは、可用性グループ `MyAg` の `AutomatedBackupPreference` プロパティを `SecondaryOnly` に設定します。</span><span class="sxs-lookup"><span data-stu-id="f9987-196">For example, the following command sets the `AutomatedBackupPreference` property on the availability group `MyAg` to `SecondaryOnly`.</span></span> <span data-ttu-id="f9987-197">この可用性グループ内のデータベースの自動バックアップはプライマリ レプリカでは行われませんが、バックアップの優先度設定が最も高いセカンダリ レプリカにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="f9987-197">Automated backups of databases in this availability group will never occur on the primary replica, but will be redirected to the secondary replica with the highest backup priority setting.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroup -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
     -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="f9987-198">コマンドレットの構文を表示するには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 環境で `Get-Help` コマンドレットを使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-198">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="f9987-199">詳細については、「 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9987-199">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="f9987-200">SQL Server PowerShell プロバイダーを設定して使用するには、「 [SQL Server PowerShell プロバイダー](../../../powershell/sql-server-powershell-provider.md) 」と「[ヘルプの表示 SQL Server PowerShell](../../../powershell/sql-server-powershell.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9987-200">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
##  <a name="follow-up-after-configuring-backup-on-secondary-replicas"></a><a name="FollowUp"></a><span data-ttu-id="f9987-201">補足情報: セカンダリレプリカでバックアップを構成した後</span><span class="sxs-lookup"><span data-stu-id="f9987-201">Follow Up: After Configuring Backup on Secondary Replicas</span></span>  
 <span data-ttu-id="f9987-202">特定の可用性グループの自動バックアップ設定を考慮に入れるには、バックアップ優先度が 0 を超える (>0) 可用性レプリカをホストする各サーバー インスタンスで、可用性グループのデータベースのバックアップ ジョブを実行するスクリプトを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f9987-202">To take the automated backup preference into account for a given availability group, on each server instance that hosts an availability replica whose backup priority is greater than zero (>0), you need to script backup jobs for the databases in the availability group.</span></span> <span data-ttu-id="f9987-203">現在のレプリカが優先バックアップ レプリカかどうかを確認すには、バックアップ スクリプトで [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f9987-203">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function in your backup script.</span></span> <span data-ttu-id="f9987-204">現在のサーバー インスタンスでホストされている可用性レプリカがバックアップ用の優先レプリカである場合、この関数は 1 を返します。</span><span class="sxs-lookup"><span data-stu-id="f9987-204">If the availability replica that is hosted by the current server instance is the preferred replica for backups, this function returns 1.</span></span> <span data-ttu-id="f9987-205">そうでない場合、関数は 0 を返します。</span><span class="sxs-lookup"><span data-stu-id="f9987-205">If not, the function returns 0.</span></span> <span data-ttu-id="f9987-206">この関数に対してクエリを実行する各可用性レプリカを対象にしてシンプルなスクリプトを実行することによって、特定のバックアップ ジョブの実行に適したレプリカを特定できます。</span><span class="sxs-lookup"><span data-stu-id="f9987-206">By running a simple script on each availability replica that queries this function, you can determine which replica should run a given backup job.</span></span> <span data-ttu-id="f9987-207">たとえば、バックアップ ジョブ スクリプトの典型的なスニペットは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="f9987-207">For example, a typical snippet of a backup-job script would look like:</span></span>  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select 'This is not the preferred replica, exiting with success';  
      RETURN 0 - This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 <span data-ttu-id="f9987-208">このロジックを使用してバックアップ ジョブのスクリプトを作成することにより、各可用性レプリカで同じスケジュールでジョブを実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="f9987-208">Scripting a backup job with this logic enables you to schedule the job to run on every availability replica on the same schedule.</span></span> <span data-ttu-id="f9987-209">これらの各ジョブは同じデータを参照してジョブを実行する必要があるかどうかを判断するので、実際にバックアップ ステージに進むことができるのは、スケジュールされているジョブのうち 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="f9987-209">Each of these jobs looks at the same data to determine which job should run, so only one of the scheduled job actually proceeds to the backup stage.</span></span>  <span data-ttu-id="f9987-210">フェールオーバーが発生した場合に、どのスクリプトやジョブも変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="f9987-210">In the event of a failover, none of the scripts or jobs needs to be modified.</span></span> <span data-ttu-id="f9987-211">また、可用性グループを再構成して可用性レプリカを追加する場合、バックアップ ジョブの管理で必要な操作は、バックアップ ジョブのコピーまたはスケジュールのみです。</span><span class="sxs-lookup"><span data-stu-id="f9987-211">Also, if you reconfigure an availability group to add an availability replica, managing the backup job requires simply copying or scheduling the backup job.</span></span> <span data-ttu-id="f9987-212">可用性レプリカを削除する場合は、レプリカをホストするサーバー インスタンスからバックアップ ジョブを削除する操作のみです。</span><span class="sxs-lookup"><span data-stu-id="f9987-212">If you remove an availability replica, simply delete the backup job from the server instance that hosted that replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="f9987-213">[メンテナンス プラン ウィザード](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)を使用してバックアップ ジョブを作成すると、 **sys.fn_hadr_backup_is_preferred_replica** 関数の呼び出しと確認を行うスクリプト作成ロジックがそのジョブに自動的に含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9987-213">If you use the[Maintenance Plan Wizard](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)to create a given backup job, the job will automatically include the scripting logic that calls and checks the **sys.fn_hadr_backup_is_preferred_replica** function.</span></span> <span data-ttu-id="f9987-214">ただし、バックアップ ジョブによって、"これは優先レプリカではありません" というメッセージが返されることはありません。可用性グループの可用性レプリカをホストする各サーバー インスタンスで、各可用性データベースのジョブを必ず作成します。</span><span class="sxs-lookup"><span data-stu-id="f9987-214">However, the backup job will not return the "This is not the preferred replica..." message.Be sure to create the job(s) for each availability database on every server instance that hosts an availability replica for the availability group.</span></span>  
  
##  <a name="to-obtain-information-about-backup-preference-settings"></a><a name="ForInfoAboutBuPref"></a><span data-ttu-id="f9987-215">バックアップ設定の設定に関する情報を取得するには</span><span class="sxs-lookup"><span data-stu-id="f9987-215">To Obtain Information About Backup Preference Settings</span></span>  
 <span data-ttu-id="f9987-216">次の表は、セカンダリでのバックアップに関連する情報を取得するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="f9987-216">The following are useful for obtaining information that is relevant for backup on secondary.</span></span>  
  
|<span data-ttu-id="f9987-217">表示</span><span class="sxs-lookup"><span data-stu-id="f9987-217">View</span></span>|<span data-ttu-id="f9987-218">情報</span><span class="sxs-lookup"><span data-stu-id="f9987-218">Information</span></span>|<span data-ttu-id="f9987-219">関連する列</span><span class="sxs-lookup"><span data-stu-id="f9987-219">Relevant Columns</span></span>|  
|----------|-----------------|----------------------|  
|[<span data-ttu-id="f9987-220">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="f9987-220">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|<span data-ttu-id="f9987-221">現在のレプリカが優先されるバックアップ レプリカであるかどうか</span><span class="sxs-lookup"><span data-stu-id="f9987-221">Is the current replica the preferred backup replica?</span></span>|<span data-ttu-id="f9987-222">該当なし。</span><span class="sxs-lookup"><span data-stu-id="f9987-222">Not applicable.</span></span>|  
|[<span data-ttu-id="f9987-223">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="f9987-223">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|<span data-ttu-id="f9987-224">自動バックアップ設定</span><span class="sxs-lookup"><span data-stu-id="f9987-224">Automated backup preference</span></span>|<span data-ttu-id="f9987-225">**automated_backup_preference**</span><span class="sxs-lookup"><span data-stu-id="f9987-225">**automated_backup_preference**</span></span><br /><br /> <span data-ttu-id="f9987-226">**automated_backup_preference_desc**</span><span class="sxs-lookup"><span data-stu-id="f9987-226">**automated_backup_preference_desc**</span></span>|  
|[<span data-ttu-id="f9987-227">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="f9987-227">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|<span data-ttu-id="f9987-228">指定された可用性レプリカのバックアップの優先順位</span><span class="sxs-lookup"><span data-stu-id="f9987-228">Backup priority of a given availability replica</span></span>|<span data-ttu-id="f9987-229">**backup_priority**</span><span class="sxs-lookup"><span data-stu-id="f9987-229">**backup_priority**</span></span>|  
|[<span data-ttu-id="f9987-230">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="f9987-230">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|<span data-ttu-id="f9987-231">レプリカがこのサーバー インスタンスにローカルであるかどうか</span><span class="sxs-lookup"><span data-stu-id="f9987-231">Is replica local to the server instance?</span></span><br /><br /> <span data-ttu-id="f9987-232">現在のロール</span><span class="sxs-lookup"><span data-stu-id="f9987-232">Current role</span></span><br /><br /> <span data-ttu-id="f9987-233">操作状態</span><span class="sxs-lookup"><span data-stu-id="f9987-233">Operational state</span></span><br /><br /> <span data-ttu-id="f9987-234">接続状態</span><span class="sxs-lookup"><span data-stu-id="f9987-234">Connected state</span></span><br /><br /> <span data-ttu-id="f9987-235">可用性レプリカの同期の正常性</span><span class="sxs-lookup"><span data-stu-id="f9987-235">Synchronization health of an availability replica</span></span>|<span data-ttu-id="f9987-236">**is_local**</span><span class="sxs-lookup"><span data-stu-id="f9987-236">**is_local**</span></span><br /><br /> <span data-ttu-id="f9987-237">**ロール**, 、 **role_desc**</span><span class="sxs-lookup"><span data-stu-id="f9987-237">**role**, **role_desc**</span></span><br /><br /> <span data-ttu-id="f9987-238">**operational_state**、 **operational_state_desc**</span><span class="sxs-lookup"><span data-stu-id="f9987-238">**operational_state**, **operational_state_desc**</span></span><br /><br /> <span data-ttu-id="f9987-239">**connected_state**、 **connected_state_desc**</span><span class="sxs-lookup"><span data-stu-id="f9987-239">**connected_state**, **connected_state_desc**</span></span><br /><br /> <span data-ttu-id="f9987-240">**synchronization_health**、 **synchronization_health_desc**</span><span class="sxs-lookup"><span data-stu-id="f9987-240">**synchronization_health**, **synchronization_health_desc**</span></span>|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f9987-241">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="f9987-241">Related Content</span></span>  
  
-   [<span data-ttu-id="f9987-242">高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド</span><span class="sxs-lookup"><span data-stu-id="f9987-242">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="f9987-243">SQL Server AlwaysOn チームのブログ: AlwaysOn チームの公式 SQL Server のブログ</span><span class="sxs-lookup"><span data-stu-id="f9987-243">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="f9987-244">参照</span><span class="sxs-lookup"><span data-stu-id="f9987-244">See Also</span></span>  
 <span data-ttu-id="f9987-245">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f9987-245">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="f9987-246">アクティブなセカンダリ: セカンダリ レプリカでのバックアップ (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="f9987-246">Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 