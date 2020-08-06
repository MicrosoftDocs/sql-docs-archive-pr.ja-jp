---
title: レプリケーション管理の推奨事項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- administering replication, best practices
- replication [SQL Server], administering
ms.assetid: 850e8a87-b34c-4934-afb5-a1104f118ba8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 16652561fa873c5d8a33d8826372837744543e70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736253"
---
# <a name="best-practices-for-replication-administration"></a><span data-ttu-id="b0fbb-102">レプリケーション管理の推奨事項</span><span class="sxs-lookup"><span data-stu-id="b0fbb-102">Best Practices for Replication Administration</span></span>
  <span data-ttu-id="b0fbb-103">レプリケーションを構成したら、レプリケーション トポロジの管理方法について理解することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-103">After you have configured replication, it is important to understand how to administer a replication topology.</span></span> <span data-ttu-id="b0fbb-104">このトピックでは、さまざまな分野における推奨事項について説明し、また各分野の詳細情報へのリンクも提供します。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-104">This topic provides basic best practice guidance in a number of areas with links to more information for each area.</span></span> <span data-ttu-id="b0fbb-105">このトピックで説明するベスト プラクティスのガイダンスに従うだけでなく、次のよく寄せられる質問のトピックに目を通し、一般的な疑問や問題について理解することをお勧めします: 「[レプリケーションの管理者に関してよく寄せられる質問](frequently-asked-questions-for-replication-administrators.md)」。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-105">In addition to following the best practice guidance presented in this topic, consider reading through the frequently asked questions topic to acquaint yourself with common questions and issues: [Frequently Asked Questions for Replication Administrators](frequently-asked-questions-for-replication-administrators.md).</span></span>  
  
 <span data-ttu-id="b0fbb-106">推奨事項について理解するには、以下の 2 つの分野に分けて行うのが効果的です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-106">It is useful to divide the best practice guidance into two areas:</span></span>  
  
-   <span data-ttu-id="b0fbb-107">以下の情報は、すべてのレプリケーション トポロジについて実装する必要のある推奨事項を示しています。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-107">The following information covers best practices that should be implemented for all replication topologies:</span></span>  
  
    -   <span data-ttu-id="b0fbb-108">バックアップと復元方法の開発およびテスト</span><span class="sxs-lookup"><span data-stu-id="b0fbb-108">Develop and test a backup and restore strategy.</span></span>  
  
    -   <span data-ttu-id="b0fbb-109">レプリケーション トポロジ スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="b0fbb-109">Script the replication topology.</span></span>  
  
    -   <span data-ttu-id="b0fbb-110">しきい値および警告の作成</span><span class="sxs-lookup"><span data-stu-id="b0fbb-110">Create thresholds and alerts.</span></span>  
  
    -   <span data-ttu-id="b0fbb-111">レプリケーション トポロジの監視</span><span class="sxs-lookup"><span data-stu-id="b0fbb-111">Monitor the replication topology.</span></span>  
  
    -   <span data-ttu-id="b0fbb-112">パフォーマンス基準の確立と必要に応じたレプリケーションの調整</span><span class="sxs-lookup"><span data-stu-id="b0fbb-112">Establish performance baselines and tune replication if necessary.</span></span>  
  
-   <span data-ttu-id="b0fbb-113">以下の情報は、レプリケーション トポロジについて、必須ではないが、考慮すべき推奨事項を示しています。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-113">The following information covers best practices that should be considered, but might not be required for your topology:</span></span>  
  
    -   <span data-ttu-id="b0fbb-114">定期的なデータの検証</span><span class="sxs-lookup"><span data-stu-id="b0fbb-114">Validate data periodically.</span></span>  
  
    -   <span data-ttu-id="b0fbb-115">プロファイルを使用したエージェント パラメーターの調整</span><span class="sxs-lookup"><span data-stu-id="b0fbb-115">Adjust agent parameters through profiles.</span></span>  
  
    -   <span data-ttu-id="b0fbb-116">パブリケーションおよびディストリビューションの保有期間の調整</span><span class="sxs-lookup"><span data-stu-id="b0fbb-116">Adjust publication and distribution retention periods.</span></span>  
  
    -   <span data-ttu-id="b0fbb-117">アプリケーション要件が変更された場合のアーティクルおよびパブリケーションのプロパティの変更方法についての理解</span><span class="sxs-lookup"><span data-stu-id="b0fbb-117">Understand how to change article and publication properties if application requirements change.</span></span>  
  
    -   <span data-ttu-id="b0fbb-118">アプリケーション要件が変更された場合のスキーマの変更方法についての理解</span><span class="sxs-lookup"><span data-stu-id="b0fbb-118">Understand how to make schema changes if application requirements change.</span></span>  
  
## <a name="develop-and-test-a-backup-and-restore-strategy"></a><span data-ttu-id="b0fbb-119">バックアップと復元方法の開発およびテスト</span><span class="sxs-lookup"><span data-stu-id="b0fbb-119">Develop and test a backup and restore strategy</span></span>  
 <span data-ttu-id="b0fbb-120">すべてのデータベースは定期的にバックアップする必要があります。また、バックアップの復元機能についても定期的にテストする必要があります。これらの要件は、レプリケートされたデータベースの場合についても同様です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-120">All databases should be backed up on a regular basis, and the ability to restore those backups should be tested periodically; replicated databases are no different.</span></span> <span data-ttu-id="b0fbb-121">以下のデータベースは定期的にバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-121">The following databases should be backed up regularly:</span></span>  
  
-   <span data-ttu-id="b0fbb-122">パブリケーション データベース</span><span class="sxs-lookup"><span data-stu-id="b0fbb-122">Publication database</span></span>  
  
-   <span data-ttu-id="b0fbb-123">ディストリビューション データベース</span><span class="sxs-lookup"><span data-stu-id="b0fbb-123">Distribution database</span></span>  
  
-   <span data-ttu-id="b0fbb-124">サブスクリプション データベース</span><span class="sxs-lookup"><span data-stu-id="b0fbb-124">Subscription databases</span></span>  
  
-   <span data-ttu-id="b0fbb-125">パブリッシャー、ディストリビューター、すべてのサブスクライバーの**msdb** データベースおよび **master** データベース</span><span class="sxs-lookup"><span data-stu-id="b0fbb-125">**msdb** database and **master** database at the Publisher, Distributor, and all Subscribers</span></span>  
  
 <span data-ttu-id="b0fbb-126">レプリケートされたデータベースでは、データのバックアップと復元に対する特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-126">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="b0fbb-127">詳細については、「 [レプリケートされたデータベースのバックアップと復元](back-up-and-restore-replicated-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-127">For more information, see [Back Up and Restore Replicated Databases](back-up-and-restore-replicated-databases.md).</span></span>  
  
## <a name="script-the-replication-topology"></a><span data-ttu-id="b0fbb-128">レプリケーション トポロジ スクリプトの作成</span><span class="sxs-lookup"><span data-stu-id="b0fbb-128">Script the replication topology</span></span>  
 <span data-ttu-id="b0fbb-129">トポロジ内のすべてのレプリケーション コンポーンネントは、ディザスター リカバリー計画の一部としてスクリプト化され、スクリプトはタスクの繰り返しの自動化にも使用することができます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-129">All replication components in a topology should be scripted as part of a disaster recovery plan, and scripts can also be used to automate repetitive tasks.</span></span> <span data-ttu-id="b0fbb-130">スクリプトには、パブリケーションやサブスクリプションなどスクリプト化されたレプリケーション コンポーネントを実装するために必要な [!INCLUDE[tsql](../../../includes/tsql-md.md)] システム ストアド プロシージャが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-130">A script contains the [!INCLUDE[tsql](../../../includes/tsql-md.md)] system stored procedures necessary to implement the replication component(s) scripted, such as a publication or subscription.</span></span> <span data-ttu-id="b0fbb-131">スクリプトはウィザード (パブリケーションの新規作成ウィザードなど) で作成することができ、コンポーネントの作成後、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-131">Scripts can be created in a wizard (such as the New Publication Wizard) or in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] after you create a component.</span></span> <span data-ttu-id="b0fbb-132">[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または **sqlcmd**を使用すると、スクリプトの表示、変更、および実行を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-132">You can view, modify, and run the script using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or **sqlcmd**.</span></span> <span data-ttu-id="b0fbb-133">スクリプトをバックアップ ファイルと共に保存して、レプリケーション トポロジの再構成が必要な場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-133">Scripts can be stored with backup files to be used in case a replication topology must be reconfigured.</span></span> <span data-ttu-id="b0fbb-134">詳細については、「[レプリケーションのスクリプト作成](../scripting-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-134">For more information, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
 <span data-ttu-id="b0fbb-135">プロパティが変更された場合は、コンポーネントのスクリプトを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-135">A component should be rescripted if any property changes are made.</span></span> <span data-ttu-id="b0fbb-136">トランザクション レプリケーションでカスタム ストアド プロシージャを使用している場合は、各プロシージャのコピーをスクリプトと共に保存しておく必要があります。プロシージャが変更された場合は、プロシージャのコピーも更新する必要があります (スキーマやアプリケーション要件が変更されると、通常、プロシージャが更新されます)。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-136">If you use custom stored procedures with transactional replication, a copy of each procedure should be stored with the scripts; the copy should be updated if the procedure changes (procedures are typically updated due to schema changes or changing application requirements).</span></span> <span data-ttu-id="b0fbb-137">カスタム プロシージャの詳細については、「[トランザクション アーティクルに変更を反映する方法の指定](../transactional/transactional-articles-specify-how-changes-are-propagated.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-137">For more information about custom procedures, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
## <a name="establish-performance-baselines-and-tune-replication-if-necessary"></a><span data-ttu-id="b0fbb-138">パフォーマンス基準の確立と必要に応じたレプリケーションの調整</span><span class="sxs-lookup"><span data-stu-id="b0fbb-138">Establish performance baselines and tune replication if necessary</span></span>  
 <span data-ttu-id="b0fbb-139">レプリケーションを構成する前に、レプリケーションのパフォーマンスに影響を及ぼす要因について理解しておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-139">Before replication is configured, it is recommended to familiarize yourself with the factors that affect replication performance:</span></span>  
  
-   <span data-ttu-id="b0fbb-140">サーバーおよびネットワークのハードウェア</span><span class="sxs-lookup"><span data-stu-id="b0fbb-140">Server and network hardware</span></span>  
  
-   <span data-ttu-id="b0fbb-141">データベースの設計</span><span class="sxs-lookup"><span data-stu-id="b0fbb-141">Database design</span></span>  
  
-   <span data-ttu-id="b0fbb-142">ディストリビューターの構成</span><span class="sxs-lookup"><span data-stu-id="b0fbb-142">Distributor configuration</span></span>  
  
-   <span data-ttu-id="b0fbb-143">パブリケーションの設計およびオプション</span><span class="sxs-lookup"><span data-stu-id="b0fbb-143">Publication design and options</span></span>  
  
-   <span data-ttu-id="b0fbb-144">フィルターの設計および使用方法</span><span class="sxs-lookup"><span data-stu-id="b0fbb-144">Filter design and use</span></span>  
  
-   <span data-ttu-id="b0fbb-145">サブスクリプション オプション</span><span class="sxs-lookup"><span data-stu-id="b0fbb-145">Subscription options</span></span>  
  
-   <span data-ttu-id="b0fbb-146">スナップショット オプション</span><span class="sxs-lookup"><span data-stu-id="b0fbb-146">Snapshot options</span></span>  
  
-   <span data-ttu-id="b0fbb-147">エージェント パラメーター</span><span class="sxs-lookup"><span data-stu-id="b0fbb-147">Agent parameters</span></span>  
  
-   <span data-ttu-id="b0fbb-148">メンテナンス</span><span class="sxs-lookup"><span data-stu-id="b0fbb-148">Maintenance</span></span>  
  
 <span data-ttu-id="b0fbb-149">レプリケーションの構成を終えたら、パフォーマンス基準を策定することをお勧めします。パフォーマンス基準を策定することによって、アプリケーションおよびトポロジにおける通常のワークロードに対するレプリケーションの動作方法について判断できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-149">After replication is configured, it is recommended to develop a performance baseline, which will allow you to determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="b0fbb-150">レプリケーション モニターおよびシステム モニターを使用し、以下に示すレプリケーション パフォーマンスの 5 つのディメンションについて標準となる数値を決定してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-150">Use Replication Monitor and System Monitor to determine typical numbers for the following five dimensions of replication performance:</span></span>  
  
-   <span data-ttu-id="b0fbb-151">待機時間 : レプリケーション トポロジにおいて、データの変更内容が各ノード間に反映されるまでの時間。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-151">Latency: the amount of time it takes for a data change to be propagated between nodes in a replication topology.</span></span>  
  
-   <span data-ttu-id="b0fbb-152">スループット : 長期間にわたってシステムが維持できるレプリケーションの総利用状況 (一定期間内に配信されたコマンドで測定されます)。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-152">Throughput: the amount of replication activity (measured in commands delivered over a period of time) a system can sustain over time.</span></span>  
  
-   <span data-ttu-id="b0fbb-153">コンカレンシー数 : システムにおいて同時に実行可能なレプリケーションのプロセス数。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-153">Concurrency: the number of replication processes that can operate on a system simultaneously.</span></span>  
  
-   <span data-ttu-id="b0fbb-154">同期の実行時間 : 同期処理が完了するまでに必要な時間。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-154">Duration of synchronization: how long it takes a given synchronization to complete.</span></span>  
  
-   <span data-ttu-id="b0fbb-155">リソース消費量 : レプリケーション プロセスの結果として使用されるハードウェアおよびネットワークのリソース。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-155">Resource consumption: hardware and network resources used as a result of replication processing.</span></span>  
  
 <span data-ttu-id="b0fbb-156">トランザクション レプリケーションに最も関連するのは待機時間およびスループットです。トランザクション レプリケーションを使用するシステムでは、一般的に短い待機時間と高いスループットが要求されるためです。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-156">Latency and throughput are most relevant to transactional replication, because systems built on transactional replication generally require low latency and high throughput.</span></span> <span data-ttu-id="b0fbb-157">マージ レプリケーションに最も関連するのはコンカレンシー数と同期の実行時間です。マージ レプリケーションを使用するシステムでは多数のサブスクライバーが存在することが多く、これらのサブスクライバーに対してパブリッシャーが同時に多数の同期を行うことがあるためです。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-157">Concurrency and duration of synchronization are most relevant to merge replication, because systems built on merge replication often have a large number of Subscribers, and a Publisher can have a significant number of concurrent synchronizations with these Subscribers.</span></span>  
  
 <span data-ttu-id="b0fbb-158">基準となる数値を設定したら、レプリケーション モニターでしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-158">After you have established baseline numbers, set thresholds in Replication Monitor.</span></span> <span data-ttu-id="b0fbb-159">詳細については、「[Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)」 (レプリケーション モニターのしきい値と警告の設定) と「[Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md)」 (レプリケーション エージェント イベントに対する警告の使用) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-159">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span> <span data-ttu-id="b0fbb-160">パフォーマンスに関する問題が発生した場合は、上記のパフォーマンスの向上に関するトピックに目を通し、問題の解決に役立つ変更を適用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-160">If you encounter a performance problem, it is recommended to read through the suggestions in the enhancing performance topics listed above and to apply changes in areas that affect the issues you are encountering.</span></span>  
  
## <a name="create-thresholds-and-alerts"></a><span data-ttu-id="b0fbb-161">しきい値および警告の作成</span><span class="sxs-lookup"><span data-stu-id="b0fbb-161">Create thresholds and alerts</span></span>  
 <span data-ttu-id="b0fbb-162">レプリケーション モニターを使用すると、ステータスやパフォーマンスに関連したさまざまなしきい値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-162">Replication Monitor allows you to set a number of thresholds related to status and performance.</span></span> <span data-ttu-id="b0fbb-163">トポロジに対する適切なしきい値を設定することをお勧めします。しきい値に到達した場合は警告が表示されます。また、オプションで電子メール アカウントやポケットベルなどのデバイスに警告を送信することもできます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-163">It is recommended to set the appropriate thresholds for your topology; if a threshold is reached, a warning is displayed, and, optionally, an alert can be sent to an e-mail account, a pager, or other device.</span></span> <span data-ttu-id="b0fbb-164">詳細については、「 [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-164">For more information, see [Set Thresholds and Warnings in Replication Monitor](../monitor/set-thresholds-and-warnings-in-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="b0fbb-165">レプリケーションでは、しきい値の監視に関連する警告に加えて、レプリケーション エージェント アクションに対応する定義済みの警告を多数利用できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-165">In addition to the alerts that can be associated with monitoring thresholds, replication provides a number of predefined alerts that respond to replication agent actions.</span></span> <span data-ttu-id="b0fbb-166">これらの警告を使用することで、管理者はレプリケーション トポロジの状態について常時把握することができます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-166">These alerts can be used by an administrator to stay informed about the state of the replication topology.</span></span> <span data-ttu-id="b0fbb-167">警告について説明したトピックに目を通し、管理ニーズに合った警告を使用することをお勧めします (必要に応じて新しい警告を追加することもできます)。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-167">It is recommended to read through the topic describing the alerts and to use any that fit your administration needs (it is also possible to create additional alerts if necessary).</span></span> <span data-ttu-id="b0fbb-168">詳細については、「[レプリケーション エージェント イベントに対する警告の使用](../agents/use-alerts-for-replication-agent-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-168">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
## <a name="monitor-the-replication-topology"></a><span data-ttu-id="b0fbb-169">レプリケーション トポロジの監視</span><span class="sxs-lookup"><span data-stu-id="b0fbb-169">Monitor the replication topology</span></span>  
 <span data-ttu-id="b0fbb-170">レプリケーション トポロジを配置し、しきい値と警告の構成を終えたら、レプリケーションを定期的に監視することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-170">After the replication topology is in place and thresholds and alerts have been configured, it is recommended to regularly monitor replication.</span></span> <span data-ttu-id="b0fbb-171">レプリケーション トポロジの監視は、レプリケーションの配置における重要な側面です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-171">Monitoring a replication topology is an important aspect of deploying replication.</span></span> <span data-ttu-id="b0fbb-172">レプリケーション処理は分散環境で行われるため、レプリケーションに関連するすべてのコンピューターについてその利用状況と状態を追跡することが不可欠です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-172">Because replication activity is distributed, it is essential to track activity and status across all computers involved in replication.</span></span> <span data-ttu-id="b0fbb-173">レプリケーションの監視には以下のツールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-173">The following tools can be used to monitor replication:</span></span>  
  
-   <span data-ttu-id="b0fbb-174">レプリケーション モニターは、レプリケーションの監視に最も重要なツールです。レプリケーション モニターを使用すると、レプリケーション トポロジ全体の状態を監視できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-174">Replication Monitor is the most important tool for monitoring replication, allowing you to monitor the overall health of a replication topology.</span></span> <span data-ttu-id="b0fbb-175">詳しくは、「 [Monitoring Replication](../monitoring-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-175">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   [!INCLUDE[tsql](../../../includes/tsql-md.md)] <span data-ttu-id="b0fbb-176">およびレプリケーション管理オブジェクト (RMO) には、レプリケーション監視用のインターフェイスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-176">and Replication Management Objects (RMO) provide interfaces for monitoring replication.</span></span> <span data-ttu-id="b0fbb-177">詳しくは、「 [Monitoring Replication](../monitoring-replication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-177">For more information, see [Monitoring Replication](../monitoring-replication.md).</span></span>  
  
-   <span data-ttu-id="b0fbb-178">レプリケーションのパフォーマンスの監視には、システム モニターも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-178">System Monitor can also be useful for monitoring replication performance.</span></span> <span data-ttu-id="b0fbb-179">詳細については、「 [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-179">For more information, see [Monitoring Replication with System Monitor](../monitor/monitoring-replication-with-system-monitor.md).</span></span>  
  
## <a name="validate-data-periodically"></a><span data-ttu-id="b0fbb-180">定期的なデータの検証</span><span class="sxs-lookup"><span data-stu-id="b0fbb-180">Validate data periodically</span></span>  
 <span data-ttu-id="b0fbb-181">レプリケーションでは検証は必須ではありませんが、トランザクション レプリケーションおよびマージ レプリケーションを行う場合には定期的に検証することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-181">Validation is not required by replication, but it is recommended to run validation periodically for transactional replication and merge replication.</span></span> <span data-ttu-id="b0fbb-182">検証を行うことによって、サブスクライバーのデータがパブリッシャーのデータに一致していることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-182">Validation allows you to verify that data at the Subscriber matches data at the Publisher.</span></span> <span data-ttu-id="b0fbb-183">検証が正常に行われるのは、パブリッシャーの変更内容がその時点ですべてサブスクライバーにレプリケートされていて (サブスクライバーでの更新がサポートされている場合は、サブスクライバーからパブリッシャーへも変更内容がレプリケートされ)、2 つのデータベースが同期している場合です。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-183">Successful validation indicates that at that point in time all changes from the Publisher have been replicated to the Subscriber (and from the Subscriber to the Publisher if updates are supported at the Subscriber) and that the two databases are in sync.</span></span>  
  
 <span data-ttu-id="b0fbb-184">パブリケーション データベースのバックアップ スケジュールに従って検証を行うことを推奨します。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-184">It is recommended that validation be performed according to the backup schedule of the publication database.</span></span> <span data-ttu-id="b0fbb-185">たとえば、パブリケーション データベースを週に 1 回完全バックアップする場合は、検証もバックアップの終了後、週に 1 回行います。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-185">For example, if the publication database has a full backup once per week, validation could be run once per week after the backup completes.</span></span> <span data-ttu-id="b0fbb-186">詳細については、「[レプリケートされたデータの検証](../validate-data-at-the-subscriber.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-186">For more information, see [Validate Replicated Data](../validate-data-at-the-subscriber.md).</span></span>  
  
## <a name="use-agent-profiles-to-change-agent-parameters-if-necessary"></a><span data-ttu-id="b0fbb-187">エージェント プロファイルによるエージェント パラメーターへの必要に応じた変更</span><span class="sxs-lookup"><span data-stu-id="b0fbb-187">Use agent profiles to change agent parameters if necessary</span></span>  
 <span data-ttu-id="b0fbb-188">エージェント プロファイルを使用すると、レプリケーション エージェントのパラメーターを簡単に設定できます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-188">Agent profiles provide a convenient method of setting replication agent parameters.</span></span> <span data-ttu-id="b0fbb-189">エージェントのコマンド ラインでパラメーターを指定することもできますが、通常は定義済みのエージェント プロファイルを使用するか、パラメーターの値の変更が必要な場合新規プロファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-189">Parameters can also be specified on the agent command line, but it is typically more appropriate to use a predefined agent profile or to create a new profile if you need to change the value of a parameter.</span></span> <span data-ttu-id="b0fbb-190">たとえば、マージ レプリケーションを使用中にサブスクライバーの接続をブロードバンドからダイヤルアップに変更する場合、マージ エージェントに対して **低速リンク** プロファイルの使用を検討してください。このプロファイルでは、低速通信リンクにより適したパラメーターのセットが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-190">For example, if you are using merge replication and a Subscriber moves from a broadband connection to a dialup connection, consider using the **slow link** profile for the Merge Agent; this profile uses a set of parameters that are better suited to the slower communications link.</span></span> <span data-ttu-id="b0fbb-191">詳しくは、「 [レプリケーション エージェント プロファイル](../agents/replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-191">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="adjust-publication-and-distribution-retention-periods-if-necessary"></a><span data-ttu-id="b0fbb-192">パブリケーションおよびディストリビューションの保有期間の必要に応じた調整</span><span class="sxs-lookup"><span data-stu-id="b0fbb-192">Adjust publication and distribution retention periods if necessary</span></span>  
 <span data-ttu-id="b0fbb-193">トランザクション レプリケーションとマージ レプリケーションでは、ディストリビューション データベースでのトランザクションの保有期間、およびサブスクリプションの同期頻度を決定する保有期間が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-193">Transactional replication and merge replication use retention periods to determine, respectively, how long transactions are stored in the distribution database, and how frequently a subscription must synchronize.</span></span> <span data-ttu-id="b0fbb-194">最初は既定の設定を使用することをお勧めしますが、トポロジを監視して、設定を調整する必要があるかどうかを確認することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-194">It is recommended to use the default settings initially, but to monitor your topology to determine if the settings require adjustment.</span></span> <span data-ttu-id="b0fbb-195">たとえば、マージ レプリケーションの場合、パブリケーションの保有期間 (既定では 14 日間) によって、システム テーブルにおけるメタデータの保有期間が決定されます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-195">For example, in the case of merge replication, the publication retention period (which defaults to 14 days) determines how long metadata is stored in system tables.</span></span> <span data-ttu-id="b0fbb-196">サブスクリプションを常に 5 日以内に同期する場合は、この期間を短くすることを検討してください。こうすることにより、メタデータが削減され、パフォーマンスの向上につながる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-196">If subscriptions always synchronize within five days, consider adjusting the setting to a lower number, which will reduce metadata and possibly provide better performance.</span></span> <span data-ttu-id="b0fbb-197">詳細については、「 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-197">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
## <a name="understand-how-to-modify-publications-if-application-requirements-change"></a><span data-ttu-id="b0fbb-198">アプリケーション要件が変更された場合のスキーマの変更方法についての理解</span><span class="sxs-lookup"><span data-stu-id="b0fbb-198">Understand how to modify publications if application requirements change</span></span>  
 <span data-ttu-id="b0fbb-199">パブリケーションの作成後、アーティクルの追加や削除、またはパブリケーションおよびアーティクルのプロパティの変更が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-199">After you have created a publication, it might be necessary to add or drop articles, or change publication and article properties.</span></span> <span data-ttu-id="b0fbb-200">ほとんどの変更はパブリケーションの作成後に行うことができますが、場合によっては、パブリケーションのスナップショットの新規生成やパブリケーションに対するサブスクリプションの再初期化が必要になります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-200">Most changes are allowed after a publication is created, but in some cases, it is necessary to generate a new snapshot for a publication and/or reinitialize subscriptions to the publication.</span></span> <span data-ttu-id="b0fbb-201">詳細については、「[Change Publication and Article Properties](../publish/change-publication-and-article-properties.md)」 (パブリケーションおよびアーティクルのプロパティの変更) と「[既存のパブリケーションでのアーティクルの追加および削除](../publish/add-articles-to-and-drop-articles-from-existing-publications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-201">For more information, see [Change Publication and Article Properties](../publish/change-publication-and-article-properties.md) and [Add Articles to and Drop Articles from Existing Publications](../publish/add-articles-to-and-drop-articles-from-existing-publications.md).</span></span>  
  
## <a name="understand-how-to-make-schema-changes-if-application-requirements-change"></a><span data-ttu-id="b0fbb-202">アプリケーション要件が変更された場合のスキーマの変更方法についての理解</span><span class="sxs-lookup"><span data-stu-id="b0fbb-202">Understand how to make schema changes if application requirements change</span></span>  
 <span data-ttu-id="b0fbb-203">アプリケーションの運用後、スキーマの変更が必要になる場合が多々あります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-203">In many cases, schema changes are required after an application is in production.</span></span> <span data-ttu-id="b0fbb-204">レプリケーション トポロジでは、多くの場合、このような変更をすべてのサブスクライバーに反映する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-204">In a replication topology, these changes must often be propagated to all Subscribers.</span></span> <span data-ttu-id="b0fbb-205">レプリケーションは、パブリッシュされたオブジェクトに対するさまざまなスキーマ変更をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-205">Replication supports a wide range of schema changes to published objects.</span></span> <span data-ttu-id="b0fbb-206">パブリッシュされた適切なオブジェクトに対して、以下に示すスキーマ変更を [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] パブリッシャーで行った場合、既定ではすべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] サブスクライバーにその変更が反映されます。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-206">When you make any of the following schema changes on the appropriate published object at a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Publisher, that change is propagated by default to all [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers:</span></span>  
  
-   <span data-ttu-id="b0fbb-207">ALTER TABLE</span><span class="sxs-lookup"><span data-stu-id="b0fbb-207">ALTER TABLE</span></span>  
  
-   <span data-ttu-id="b0fbb-208">ALTER VIEW</span><span class="sxs-lookup"><span data-stu-id="b0fbb-208">ALTER VIEW</span></span>  
  
-   <span data-ttu-id="b0fbb-209">ALTER PROCEDURE</span><span class="sxs-lookup"><span data-stu-id="b0fbb-209">ALTER PROCEDURE</span></span>  
  
-   <span data-ttu-id="b0fbb-210">ALTER FUNCTION</span><span class="sxs-lookup"><span data-stu-id="b0fbb-210">ALTER FUNCTION</span></span>  
  
-   <span data-ttu-id="b0fbb-211">ALTER TRIGGER</span><span class="sxs-lookup"><span data-stu-id="b0fbb-211">ALTER TRIGGER</span></span>  
  
 <span data-ttu-id="b0fbb-212">詳細については、「[パブリケーション データベースでのスキーマの変更](../publish/make-schema-changes-on-publication-databases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0fbb-212">For more information, see [Make Schema Changes on Publication Databases](../publish/make-schema-changes-on-publication-databases.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0fbb-213">参照</span><span class="sxs-lookup"><span data-stu-id="b0fbb-213">See Also</span></span>  
 [<span data-ttu-id="b0fbb-214">レプリケーション管理に関する FAQ</span><span class="sxs-lookup"><span data-stu-id="b0fbb-214">Replication Administration FAQ</span></span>](frequently-asked-questions-for-replication-administrators.md)  
  
  