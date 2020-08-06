---
title: レプリケーションの全般的パフォーマンスの向上 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- designing databases [SQL Server], replication performance
- Snapshot Agent, performance
- snapshots [SQL Server replication], performance considerations
- merge replication performance [SQL Server replication]
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- performance [SQL Server replication], general considerations
- transactional replication, performance
ms.assetid: 895b1ad7-ffb9-4a5c-bda6-e1dfbd56d9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a85519a947e7d5d03f324b71984d2ffb40bcefe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741878"
---
# <a name="enhance-general-replication-performance"></a><span data-ttu-id="a3351-102">レプリケーションの全般的パフォーマンスの向上</span><span class="sxs-lookup"><span data-stu-id="a3351-102">Enhance General Replication Performance</span></span>
  <span data-ttu-id="a3351-103">このトピックで解説するガイドラインに従うことによって、アプリケーションおよびネットワーク上にある全種類のレプリケーションの全般的なパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a3351-103">You can enhance the general performance for all types of replication in your application and on your network by using the guidelines described in this topic.</span></span>  
  
## <a name="server-and-network"></a><span data-ttu-id="a3351-104">サーバーおよびネットワーク</span><span class="sxs-lookup"><span data-stu-id="a3351-104">Server and Network</span></span>  
  
-   <span data-ttu-id="a3351-105">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] に割り当てるメモリの最大容量と最小容量を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3351-105">Set the minimum and maximum amount of memory allocated to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
     <span data-ttu-id="a3351-106">既定では、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] は使用できるシステム リソースに基づいて、そのメモリ要求を動的に変更します。</span><span class="sxs-lookup"><span data-stu-id="a3351-106">By default, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] changes its memory requirements dynamically based on available system resources.</span></span> <span data-ttu-id="a3351-107">レプリケーション作業中に使用できるメモリ容量が少なくなるのを防ぐには、 **min server memory** オプションを使用して最小メモリ容量を設定します。</span><span class="sxs-lookup"><span data-stu-id="a3351-107">To avoid low memory availability during replication activities, use the **min server memory** option to set the minimum available memory.</span></span> <span data-ttu-id="a3351-108">オペレーティング システムによるディスクへのメモリ書き出しを防ぐために、 **max server memory** オプションを使用して最大メモリ容量を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a3351-108">To avoid having the operating system page to disc for memory, you can also set a maximum amount of memory with the **max server memory** option.</span></span> <span data-ttu-id="a3351-109">詳細については、「[サーバー メモリに関するサーバー構成オプション](../../../database-engine/configure-windows/server-memory-server-configuration-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-109">For more information, see [Server Memory Server Configuration Options](../../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
-   <span data-ttu-id="a3351-110">データベースのデータ ファイルおよびログ ファイルを適切に配置する。</span><span class="sxs-lookup"><span data-stu-id="a3351-110">Ensure proper allocation of database data files and log files.</span></span> <span data-ttu-id="a3351-111">レプリケーションに関係するすべてのデータベースのトランザクション ログを、別のディスク ドライブに格納します。</span><span class="sxs-lookup"><span data-stu-id="a3351-111">Use a separate disk drive for the transaction log for all databases involved in replication.</span></span>  
  
     <span data-ttu-id="a3351-112">データベースの格納に使用するものとは別のディスク ドライブにログ ファイルを保存することで、トランザクションの書き込みにかかる時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-112">You can decrease the time it takes to write transactions by storing the log files on a disk drive different than the one used to store the database.</span></span> <span data-ttu-id="a3351-113">フォールト トレランスが必要な場合は、Redundant Array of Inexpensive Disks (RAID)-1 を使用して、そのドライブをミラー化できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-113">You can mirror that drive, using a Redundant Array of Inexpensive Disks (RAID)-1, if you require fault tolerance.</span></span> <span data-ttu-id="a3351-114">他のデータベース ファイルには RAID 0 または 0+1 (フォールト トレランスの必要性によって異なります) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-114">Use RAID 0 or 0+1 (depending on your need for fault tolerance) for other database files.</span></span> <span data-ttu-id="a3351-115">これは、レプリケーションを使用するかどうかとは無関係に、良い方法です。</span><span class="sxs-lookup"><span data-stu-id="a3351-115">This is a good practice regardless of whether or not replication is being used.</span></span>  
  
-   <span data-ttu-id="a3351-116">レプリケーションで使用するサーバー、特にディストリビューターにメモリを追加する。</span><span class="sxs-lookup"><span data-stu-id="a3351-116">Consider adding memory to servers used in replication, particularly the Distributor.</span></span>  
  
-   <span data-ttu-id="a3351-117">マルチプロセッサ コンピューターを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-117">Use multiprocessor computers.</span></span>  
  
     <span data-ttu-id="a3351-118">レプリケーション エージェントはサーバー上の追加プロセッサを利用できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-118">Replication agents can take advantage of additional processors on the server.</span></span> <span data-ttu-id="a3351-119">実行時の CPU 使用量が高いレベルにある場合、より高速の CPU または複数の CPU のインストールを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-119">If you are running at high CPU usage, consider installing a faster CPU or multiple CPUs.</span></span>  
  
-   <span data-ttu-id="a3351-120">高速ネットワークを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-120">Use a fast network.</span></span>  
  
     <span data-ttu-id="a3351-121">特にトランザクション レプリケーションでは、ネットワークがパフォーマンスの重大なボトルネックになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-121">The network can be a significant performance bottleneck, particularly for transactional replication.</span></span> <span data-ttu-id="a3351-122">サブスクライバーへの変更の反映は、100 メガバイト/秒 (Mbps) 以上の高速ネットワークを使用することで大幅に高速化されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-122">The propagation of changes to Subscribers can be significantly enhanced by using a fast network of 100 megabits per second (Mbps) or faster.</span></span> <span data-ttu-id="a3351-123">ネットワークが低速な場合は、適切なネットワーク設定とエージェント パラメーターを指定してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-123">If the network is slow, specify appropriate network settings and agent parameters.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="a3351-124">データベースの設計</span><span class="sxs-lookup"><span data-stu-id="a3351-124">Database Design</span></span>  
  
-   <span data-ttu-id="a3351-125">データベース設計の推奨事項に従う。</span><span class="sxs-lookup"><span data-stu-id="a3351-125">Follow best practices for database design.</span></span>  
  
     <span data-ttu-id="a3351-126">レプリケートされたデータベースにおけるパフォーマンス最適化の手順は、レプリケートされていないデータベースの場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="a3351-126">A replicated database generally benefits from the same performance optimizations as a non-replicated database.</span></span> <span data-ttu-id="a3351-127">ただし、サブスクライバーでインデックスを作成する場合は注意が必要です。サブスクライバーの主キー列にはインデックスを作成しますが、その他の列にインデックスを作成すると、挿入、更新、および削除処理のパフォーマンスに影響する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-127">However, indexes should be used with caution at the Subscriber: the primary key column at the Subscriber should be indexed, but additional indexes can affect insert, update, and delete performance.</span></span>  
  
-   <span data-ttu-id="a3351-128">READ_COMMITTED_SNAPSHOT データベース オプションを設定する。</span><span class="sxs-lookup"><span data-stu-id="a3351-128">Consider setting the READ_COMMITTED_SNAPSHOT database option.</span></span>  
  
     <span data-ttu-id="a3351-129">ユーザーの処理とレプリケーション エージェントの処理との競合を削減するには、パブリケーションおよびサブスクリプション データベースに対してこのオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="a3351-129">To help reduce contention between user activity and replication agent activity, set this option for the publication and subscription databases:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks  
    SET READ_COMMITTED_SNAPSHOT ON  
    ```  
  
     <span data-ttu-id="a3351-130">詳細については、「[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-130">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="a3351-131">トリガーのアプリケーション ロジックに注意する。</span><span class="sxs-lookup"><span data-stu-id="a3351-131">Be cautious with application logic in triggers.</span></span>  
  
     <span data-ttu-id="a3351-132">サブスクライバーのユーザー定義トリガー内のビジネス ロジックによって、サブスクライバーへの変更のレプリケーション速度が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-132">Business logic in user-defined triggers at the Subscriber can slow down the replication of changes to the Subscriber:</span></span>  
  
    -   <span data-ttu-id="a3351-133">トランザクション レプリケーションでは、レプリケートされたコマンドの適用に使用されるカスタム ストアド プロシージャにこのようなロジックを含める方がより効率的です。</span><span class="sxs-lookup"><span data-stu-id="a3351-133">For transactional replication, it can be more efficient to include this logic in custom stored procedures used to apply the replicated commands.</span></span> <span data-ttu-id="a3351-134">詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-134">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
    -   <span data-ttu-id="a3351-135">マージ レプリケーションの場合には、ビジネス ロジック ハンドラーを使用する方がより効率的です。</span><span class="sxs-lookup"><span data-stu-id="a3351-135">For merge replication, it can be more efficient to use business logic handlers.</span></span> <span data-ttu-id="a3351-136">詳細については、「[Execute Business Logic During Merge Synchronization](../merge/execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3351-136">For more information, see [Execute Business Logic During Merge Synchronization](../merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
     <span data-ttu-id="a3351-137">マージ レプリケーションにパブリッシュされるテーブルの参照整合性を維持する目的でトリガーを使用する場合は、テーブルの処理順序を指定してマージ エージェントが必要とする再試行の回数を削減します。</span><span class="sxs-lookup"><span data-stu-id="a3351-137">If you use triggers to maintain referential integrity in tables published for merge replication, specify the processing order of tables to reduce the number of retries required for the Merge Agent.</span></span> <span data-ttu-id="a3351-138">詳細については、「[Specify Merge Replication properties](../publish/specify-merge-replication-properties.md)」 (マージ レプリケーションのプロパティの指定) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-138">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="a3351-139">Large Object (LOB) データ型の使用を制限する。</span><span class="sxs-lookup"><span data-stu-id="a3351-139">Limit the use of Large Object (LOB) data types.</span></span>  
  
     <span data-ttu-id="a3351-140">列の他のデータ型と比較して、LOB はより大きな記憶域とより多くの処理を必要とします。</span><span class="sxs-lookup"><span data-stu-id="a3351-140">LOBs require more storage space and processing than other column data types.</span></span> <span data-ttu-id="a3351-141">アプリケーションで必要でない限り、LOB 型の列をアーティクルに含めないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a3351-141">Do not include these columns in articles unless necessary for your application.</span></span> <span data-ttu-id="a3351-142">`text`、`ntext`、および `image` の各データ型は非推奨です。</span><span class="sxs-lookup"><span data-stu-id="a3351-142">The data types `text`, `ntext`, and `image` are deprecated.</span></span> <span data-ttu-id="a3351-143">LOB が必要な場合は、`varchar(max)`、`nvarchar(max)`、および `varbinary(max)` の各データ型を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3351-143">If you do include LOBs, we recommend that you use the data types `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, respectively.</span></span>  
  
     <span data-ttu-id="a3351-144">トランザクション レプリケーションの場合は、 **OLEDB ストリームのディストリビューション プロファイル**と呼ばれるディストリビューション エージェント プロファイルの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-144">For transactional replication, consider using the Distribution Agent profile called **Distribution Profile for OLEDB streaming**.</span></span> <span data-ttu-id="a3351-145">詳しくは、「 [レプリケーション エージェント プロファイル](../agents/replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3351-145">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="a3351-146">パブリケーションの設計</span><span class="sxs-lookup"><span data-stu-id="a3351-146">Publication Design</span></span>  
  
-   <span data-ttu-id="a3351-147">必要なデータのみをパブリッシュする。</span><span class="sxs-lookup"><span data-stu-id="a3351-147">Publish only the data required.</span></span>  
  
     <span data-ttu-id="a3351-148">レプリケーションは簡単にセットアップできるので、実際に必要なデータ以外もパブリッシュされる傾向があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-148">Because replication is easy to set up, there is a tendency to publish more data than is actually required.</span></span> <span data-ttu-id="a3351-149">これによって、ディストリビューション データベースとスナップショット ファイル内でリソースが余計に消費され、必要なデータに対するスループットが低下する恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="a3351-149">This can consume additional resources within the distribution databases and snapshot files, and can lower the throughput for required data.</span></span> <span data-ttu-id="a3351-150">不要なテーブルのパブリッシュを避け、パブリケーションの更新頻度を低くすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-150">Avoid publishing unnecessary tables and consider updating publications less frequently.</span></span>  
  
-   <span data-ttu-id="a3351-151">パブリケーションの設計とアプリケーションの動作により競合を最小化する。</span><span class="sxs-lookup"><span data-stu-id="a3351-151">Minimize conflicts through publication design and application behavior.</span></span>  
  
     <span data-ttu-id="a3351-152">マージ レプリケーション、更新可能なサブスクリプションを使用したトランザクション レプリケーション、およびピア ツー ピア トランザクション レプリケーションでは、サブスクライバーでデータを変更できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-152">The following types of replication allow data to be changed at Subscribers: merge replication, transactional replication with updatable subscriptions, and peer-to-peer transactional replication.</span></span> <span data-ttu-id="a3351-153">マージ レプリケーションおよび更新可能なサブスクリプションを使用したトランザクション レプリケーションは、指定した行が同期中に複数のノードで更新された場合のデータの競合をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a3351-153">Merge replication and transactional replication with updatable subscriptions support data conflicts if a given row is updated at more than one node between synchronizations.</span></span> <span data-ttu-id="a3351-154">ピア ツー ピア トランザクション レプリケーションはデータの競合をサポートしていません。データの変更はパーティション分割されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-154">Peer-to-peer replication does not support data conflicts; data changes must be partitioned.</span></span> <span data-ttu-id="a3351-155">使用するレプリケーションの種類にかかわらず、できる限りデータの変更をパーティション分割することをお勧めします。これにより、競合の検出と解決に必要な処理を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="a3351-155">Regardless of the type of replication used, we recommend that you partition changes whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span>  
  
     <span data-ttu-id="a3351-156">変更をパーティション分割するには、各サブスクライバーにデータのサブセットをパブリッシュするか、またはアプリケーションを使用して、指定した行の変更を所定のノードに転送します。</span><span class="sxs-lookup"><span data-stu-id="a3351-156">Changes can be partitioned by publishing subsets of data to each Subscriber or by having an application direct changes for a given row to a given node:</span></span>  
  
    -   <span data-ttu-id="a3351-157">マージ レプリケーションは、単一パブリケーションで、パラメーター化されたフィルターを使用したデータのサブセットのパブリッシュをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a3351-157">Merge replication supports publishing subsets of data using parameterized filters with a single publication.</span></span> <span data-ttu-id="a3351-158">詳しくは、「 [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3351-158">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
    -   <span data-ttu-id="a3351-159">トランザクション レプリケーションは、複数のパブリケーションで、静的フィルターを使用したデータのサブセットのパブリッシュをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a3351-159">Transactional replication supports publishing subsets of data using static filters with multiple publications.</span></span> <span data-ttu-id="a3351-160">詳細については、「[パブリッシュされたデータのフィルター選択](../publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-160">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="a3351-161">行フィルターの使用は慎重に行う。</span><span class="sxs-lookup"><span data-stu-id="a3351-161">Use row filters judiciously.</span></span>  
  
     <span data-ttu-id="a3351-162">トランザクション パブリケーションに行フィルターを使用したアーティクルが 1 つ以上格納されている場合、ログ リーダー エージェントはトランザクション ログをスキャンする際に、テーブルの更新の影響を受ける各行にフィルターを適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-162">When a transactional publication includes one or more articles that use row filters, the Log Reader Agent must apply the filter to each row affected by an update to the table as it scans the transaction log.</span></span> <span data-ttu-id="a3351-163">このため、ログ リーダー エージェントのスループットが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="a3351-163">The throughput of the Log Reader Agent is therefore affected.</span></span>  
  
     <span data-ttu-id="a3351-164">同様に、マージ レプリケーションは、変更または削除された行を評価して、これらの行をどのサブスクライバーが受け取るかを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-164">Similarly, merge replication must evaluate changed or deleted rows to determine which Subscribers should receive those rows.</span></span> <span data-ttu-id="a3351-165">サブスクライバーで要求されるデータを減らすために行フィルターを使用する場合、この処理はテーブルのすべての行をパブリッシュする場合よりも複雑になり、速度が低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-165">When row filters are employed to reduce the data required at a Subscriber, this processing is more complex and can be slower than when you publish all rows in a table.</span></span> <span data-ttu-id="a3351-166">各サブスクライバーに必要な記憶域の削減と、最高スループット達成の間でのトレードオフを慎重に検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-166">Consider carefully the tradeoff between reduced storage requirements at each Subscriber and the need for achieving maximum throughput.</span></span> <span data-ttu-id="a3351-167">フィルター選択の詳細については、「[パブリッシュされたデータのフィルター選択](../publish/filter-published-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-167">For more information on filtering, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="a3351-168">サブスクリプションに関する注意点</span><span class="sxs-lookup"><span data-stu-id="a3351-168">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="a3351-169">サブスクライバーの数が多い場合はプル サブスクリプションを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-169">Use pull subscriptions when there are a large number of Subscribers.</span></span>  
  
     <span data-ttu-id="a3351-170">ディストリビューション エージェントとマージ エージェントは、プッシュ サブスクリプションの場合はディストリビューター側で、プル サブスクリプションの場合はサブスクライバー側で実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-170">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, and at Subscribers for pull subscriptions.</span></span> <span data-ttu-id="a3351-171">プル サブスクリプションを使用して、エージェントの処理をディストリビューターからサブスクライバーに移動すると、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="a3351-171">Using pull subscriptions can improve performance by moving agent processing from the Distributor to Subscribers.</span></span> <span data-ttu-id="a3351-172">詳細については、「[パブリケーションのサブスクライブ](../subscribe-to-publications.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a3351-172">For more information, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="a3351-173">サブスクライバーの処理が遅すぎる場合はサブスクリプションを再初期化する。</span><span class="sxs-lookup"><span data-stu-id="a3351-173">Consider reinitialization of the subscription if Subscribers are too far behind.</span></span>  
  
     <span data-ttu-id="a3351-174">大量の変更をサブスクライバーに送信する必要があるときには、サブスクライバーを新しいスナップショットで再初期化する方が、レプリケーションを使用して個々の変更を移動するよりも高速な場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-174">When large amounts of changes need to be sent to Subscribers, reinitializing them with a new snapshot might be faster than using replication to move the individual changes.</span></span> <span data-ttu-id="a3351-175">詳細については、「 [サブスクリプションの再初期化](../reinitialize-subscriptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
     <span data-ttu-id="a3351-176">トランザクション レプリケーションの場合は、レプリケーション モニターの **[未配布のコマンド]** タブに、サブスクライバーにまだ配布されていないディストリビューション データベース内のトランザクションの数と、これらのトランザクションの予測配布時間が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-176">For transactional replication, Replication Monitor displays on the **Undistributed Commands** tab information about: the number of transactions in the distribution database that have not yet been distributed to a Subscriber; and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="a3351-177">詳細については、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](../monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-177">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="snapshot-considerations"></a><span data-ttu-id="a3351-178">スナップショットに関する注意点</span><span class="sxs-lookup"><span data-stu-id="a3351-178">Snapshot Considerations</span></span>  
  
-   <span data-ttu-id="a3351-179">必要に応じて、データベースの利用状況が少ないときにのみスナップショット エージェントを実行する。</span><span class="sxs-lookup"><span data-stu-id="a3351-179">Run the Snapshot Agent only when necessary and at off-peak times.</span></span>  
  
     <span data-ttu-id="a3351-180">スナップショット エージェントは、パブリッシャーでパブリッシュされたテーブルから、ディストリビューターのスナップショット フォルダーにあるファイルにデータを一括コピーします。</span><span class="sxs-lookup"><span data-stu-id="a3351-180">The Snapshot Agent bulk copies data from the published table on the Publisher to a file in the snapshot folder on the Distributor.</span></span> <span data-ttu-id="a3351-181">スナップショットの生成には大量のリソースが必要となる場合があるため、利用状況が少ないときにスケジュールするのが最適です。</span><span class="sxs-lookup"><span data-stu-id="a3351-181">Generating a snapshot can be a resource intensive process and is best scheduled during off-peak times.</span></span>  
  
-   <span data-ttu-id="a3351-182">キャラクター モードのスナップショットが必要ない場合は、ネイティブ モードのスナップショットを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-182">Use a native mode snapshot unless a character mode snapshot is required.</span></span>  
  
     <span data-ttu-id="a3351-183">すべてのサブスクライバーに対して既定のネイティブ モードのスナップショットを使用します。ただし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 以外のサブスクライバーと [!INCLUDE[ssEW](../../../includes/ssew-md.md)]が動作しているサブスクライバーは除きます。これらのサブスクライバーでは、キャラクター モードのスナップショットを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-183">Use the default native mode snapshot for all Subscribers except non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and Subscribers running [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which require a character mode snapshot.</span></span>  
  
-   <span data-ttu-id="a3351-184">パブリケーションごとに単一のスナップショット フォルダーを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-184">Use a single snapshot folder for a publication.</span></span>  
  
     <span data-ttu-id="a3351-185">スナップショットの場所に関係するパブリケーション プロパティを指定するときには、既定のスナップショット フォルダーにスナップショット ファイルを生成するか、別のスナップショット フォルダーに生成するか、またはその両方を選択できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-185">When specifying the publication properties related to snapshot location, you can choose to generate snapshot files to the default snapshot folder, to an alternate snapshot folder, or to both.</span></span> <span data-ttu-id="a3351-186">両方の場所にスナップショット ファイルを生成する場合は、スナップショット エージェントを実行するときに追加のディスク領域と処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a3351-186">Generating snapshot files in both locations requires additional disk space and more processing when the Snapshot Agent runs.</span></span>  
  
-   <span data-ttu-id="a3351-187">データベースまたはログ ファイルの格納に使用しないディストリビューターのローカル ドライブにスナップショット フォルダーを配置する。</span><span class="sxs-lookup"><span data-stu-id="a3351-187">Place the snapshot folder on a drive local to the Distributor that is not used to store database or log files.</span></span>  
  
     <span data-ttu-id="a3351-188">スナップショット エージェントは、スナップショット フォルダーに対してデータの順次書き込みを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3351-188">The Snapshot Agent performs a sequential write of data to the snapshot folder.</span></span> <span data-ttu-id="a3351-189">データベースやログ ファイルとは別のドライブにスナップショット フォルダーを配置することによって、ディスク間の競合が減少し、スナップショット処理がより高速に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-189">Placing the snapshot folder on a separate drive from any database or log files reduces contention among the disks and helps the snapshot process complete faster.</span></span>  
  
-   <span data-ttu-id="a3351-190">サブスクライバーにサブスクリプション データベースを作成する場合は、単純復旧モデルまたは一括ログ復旧モデルを指定する。</span><span class="sxs-lookup"><span data-stu-id="a3351-190">When you create the subscription database at the Subscriber, consider specifying a recovery model of simple or bulk-logged.</span></span> <span data-ttu-id="a3351-191">これによって、サブスクライバーでのスナップショットの適用中に実行される一括挿入のログを最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="a3351-191">This allows minimal logging of the bulk inserts performed during the application of the snapshot at the Subscriber.</span></span> <span data-ttu-id="a3351-192">スナップショットがサブスクリプション データベースに適用されたら、必要に応じて別の復旧モデルに変更できます (レプリケートされたデータベースでは、すべての復旧モデルを使用できます)。</span><span class="sxs-lookup"><span data-stu-id="a3351-192">After the snapshot has been applied to the subscription database, you can change to a different recovery model if necessary (replicated databases can use any of the recovery models).</span></span> <span data-ttu-id="a3351-193">復旧モデルの選択の詳細については、「[復元と復旧の概要 (SQL Server)](../../backup-restore/restore-and-recovery-overview-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-193">For more information about selecting a recovery model, see [Restore and Recovery Overview &#40;SQL Server&#41;](../../backup-restore/restore-and-recovery-overview-sql-server.md).</span></span>  
  
-   <span data-ttu-id="a3351-194">低帯域ネットワークでは、リムーバブル メディア上での代替スナップショット フォルダーおよび圧縮スナップショットを使用する。</span><span class="sxs-lookup"><span data-stu-id="a3351-194">Consider using the alternate snapshot folder and compressed snapshots on removable media for low-bandwidth networks.</span></span>  
  
     <span data-ttu-id="a3351-195">代替スナップショット フォルダーに圧縮スナップショット ファイルを格納することにより、スナップショットに必要なディスク領域を節約して、スナップショット ファイルをリムーバブル メディアに容易に移動できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a3351-195">Compressing snapshot files in the alternate snapshot folder can reduce snapshot disk storage requirements and make it easier to transfer snapshot files on removable media.</span></span>  
  
     <span data-ttu-id="a3351-196">圧縮スナップショットを使用すると、ネットワーク経由でスナップショット ファイルを移動する際のパフォーマンスが向上する場合があります。</span><span class="sxs-lookup"><span data-stu-id="a3351-196">Compressed snapshots can, in some cases, improve the performance of transferring snapshot files across the network.</span></span> <span data-ttu-id="a3351-197">ただし、スナップショットを圧縮すると、スナップショット ファイル生成時のスナップショット エージェント、およびスナップショット ファイル適用時のディストリビューション エージェントまたはマージ エージェントで、追加の処理が必要になります。</span><span class="sxs-lookup"><span data-stu-id="a3351-197">However, compressing the snapshot requires additional processing by the Snapshot Agent when generating the snapshot files, and by the Distribution Agent or Merge Agent when applying the snapshot files.</span></span> <span data-ttu-id="a3351-198">これにより、スナップショット生成が遅くなり、スナップショットを適用するための時間が延びることもあります。</span><span class="sxs-lookup"><span data-stu-id="a3351-198">This may slow down snapshot generation and increase the time it takes to apply a snapshot in some cases.</span></span> <span data-ttu-id="a3351-199">また、ネットワークに障害が発生した場合、圧縮スナップショットを復旧することはできません。したがって、信頼性の低いネットワークには向いていません。</span><span class="sxs-lookup"><span data-stu-id="a3351-199">Additionally, compressed snapshots cannot be resumed if a network failure occurs; therefore they are not suitable for unreliable networks.</span></span> <span data-ttu-id="a3351-200">ネットワーク経由で圧縮スナップショットを使用するときは、これらのトレードオフを慎重に検討してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-200">Consider these tradeoffs carefully when using compressed snapshots across a network.</span></span> <span data-ttu-id="a3351-201">詳細については、「 [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) 」および「 [Compressed Snapshots](../compressed-snapshots.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-201">For more information, see [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) and [Compressed Snapshots](../compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="a3351-202">サブスクリプションを手作業で初期化する。</span><span class="sxs-lookup"><span data-stu-id="a3351-202">Consider initializing a subscription manually.</span></span>  
  
     <span data-ttu-id="a3351-203">巨大な初期データセットを扱うようなシナリオでは、スナップショット以外の方法を使用して、サブスクリプションを初期化することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="a3351-203">In some scenarios, such as those involving large initial datasets, it is preferable to initialize a subscription using a method other than a snapshot.</span></span> <span data-ttu-id="a3351-204">詳細については、「 [スナップショットを使用しないトランザクション サブスクリプションの初期化](../initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a3351-204">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
## <a name="agent-parameters"></a><span data-ttu-id="a3351-205">エージェント パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3351-205">Agent Parameters</span></span>  
  
-   <span data-ttu-id="a3351-206">初期テスト、監視、またはデバッグの間を除いて、レプリケーション エージェントの冗長レベルを低く設定する。</span><span class="sxs-lookup"><span data-stu-id="a3351-206">Reduce the verbose levels of replication agents except during initial testing, monitoring, or debugging.</span></span>  
  
     <span data-ttu-id="a3351-207">ディストリビューション エージェントまたはマージ エージェントの **-HistoryVerboseLevel** パラメーターおよび **-OutputVerboseLevel** パラメーターを低く設定します。</span><span class="sxs-lookup"><span data-stu-id="a3351-207">Reduce the **-HistoryVerboseLevel** parameter and the **-OutputVerboseLevel** parameter of the Distribution Agents or Merge Agents.</span></span> <span data-ttu-id="a3351-208">これにより、エージェントの履歴および出力を追跡するために挿入される新しい行の数を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="a3351-208">This reduces the number of new rows inserted to track agent history and output.</span></span> <span data-ttu-id="a3351-209">代わりに、同じ状態の既存の履歴メッセージが、新しい履歴情報に更新されます。</span><span class="sxs-lookup"><span data-stu-id="a3351-209">Instead, previous history messages with the same status are updated to the new history information.</span></span> <span data-ttu-id="a3351-210">テスト、監視、およびデバッグを行うときには、冗長レベルを高く設定して、エージェントの動作に関する情報をできるだけ多く得られるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="a3351-210">Increase the verbose levels for testing, monitoring, and debugging so that you have as much information about agent activity as possible.</span></span>  
  
-   <span data-ttu-id="a3351-211">スナップショット エージェント、マージ エージェント、およびディストリビューション エージェントの **-MaxBCPThreads** パラメーターを使用します (コンピューターのプロセッサ数を超えるスレッド数は指定できません)。</span><span class="sxs-lookup"><span data-stu-id="a3351-211">Use the **-MaxBCPThreads** parameter of the Snapshot Agent, Merge Agent, and Distribution Agent (the number of threads specified should not exceed the number of processors on the computer).</span></span> <span data-ttu-id="a3351-212">このパラメーターには、スナップショットの作成および適用時に並列実行できる一括コピーの操作数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a3351-212">This parameter specifies the number of bulk copy operations that can be performed in parallel when the snapshot is created and applied.</span></span>  
  
-   <span data-ttu-id="a3351-213">ディストリビューション エージェントおよびマージ エージェントの **-UseInprocLoader** パラメーターを使用します (パブリッシュされたテーブルに XML 列が含まれる場合、このパラメーターは使用できません)。</span><span class="sxs-lookup"><span data-stu-id="a3351-213">Use the **-UseInprocLoader** parameter of the Distribution Agent and the Merge Agent (this parameter cannot be used if published tables include XML columns).</span></span> <span data-ttu-id="a3351-214">このパラメーターを指定すると、スナップショットの適用時にエージェントが BULK INSERT コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="a3351-214">This parameter causes the agent to use the BULK INSERT command when the snapshot is applied.</span></span>  
  
 <span data-ttu-id="a3351-215">エージェント パラメーターは、エージェント プロファイルおよびコマンド ラインで指定できます。</span><span class="sxs-lookup"><span data-stu-id="a3351-215">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="a3351-216">詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3351-216">For more information, see:</span></span>  
  
-   [<span data-ttu-id="a3351-217">レプリケーション エージェント プロファイルの操作</span><span class="sxs-lookup"><span data-stu-id="a3351-217">Work with Replication Agent Profiles</span></span>](../agents/work-with-replication-agent-profiles.md)  
  
-   [<span data-ttu-id="a3351-218">レプリケーション エージェント コマンド プロンプト パラメーターを表示および変更する &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="a3351-218">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   <span data-ttu-id="a3351-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)に割り当てるメモリの最大容量と最小容量を設定する。</span><span class="sxs-lookup"><span data-stu-id="a3351-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
  