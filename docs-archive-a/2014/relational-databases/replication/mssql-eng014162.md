---
title: MSSQL_ENG014162 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG014162 error
ms.assetid: a15eef3f-219f-45d3-8286-6a864c85a723
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 78c6eb13087a7f7d5b2711af4484df7a384d7835
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645553"
---
# <a name="mssql_eng014162"></a><span data-ttu-id="8df88-102">MSSQL_ENG014162</span><span class="sxs-lookup"><span data-stu-id="8df88-102">MSSQL_ENG014162</span></span>
    
## <a name="message-details"></a><span data-ttu-id="8df88-103">メッセージの詳細</span><span class="sxs-lookup"><span data-stu-id="8df88-103">Message Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8df88-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8df88-104">Product Name</span></span>|<span data-ttu-id="8df88-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8df88-105">SQL Server</span></span>|  
|<span data-ttu-id="8df88-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8df88-106">Event ID</span></span>|<span data-ttu-id="8df88-107">14162</span><span class="sxs-lookup"><span data-stu-id="8df88-107">14162</span></span>|  
|<span data-ttu-id="8df88-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8df88-108">Event Source</span></span>|<span data-ttu-id="8df88-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8df88-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8df88-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8df88-110">Component</span></span>|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|<span data-ttu-id="8df88-111">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8df88-111">Symbolic Name</span></span>||  
|<span data-ttu-id="8df88-112">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8df88-112">Message Text</span></span>|<span data-ttu-id="8df88-113">パブリケーション [%s] のしきい値 [%s:%s] が設定されています。</span><span class="sxs-lookup"><span data-stu-id="8df88-113">The threshold [%s:%s] for the publication [%s] has been set.</span></span> <span data-ttu-id="8df88-114">マージ エージェントが実行されており、必要な要件に適合することを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8df88-114">Please make sure that the merge agent is running and can match the expected requirement.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8df88-115">説明</span><span class="sxs-lookup"><span data-stu-id="8df88-115">Explanation</span></span>  
 <span data-ttu-id="8df88-116">レプリケーションでは、いくつかの条件に対して警告を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="8df88-116">Replication lets you enable warnings for several conditions.</span></span> <span data-ttu-id="8df88-117">たとえば、マージ パブリッシャーとサブスクライバーの間で変更を同期する時間が指定の長さを超えた場合などです。</span><span class="sxs-lookup"><span data-stu-id="8df88-117">This includes exceeding a specified length of time for synchronizing changes between a merge Publisher and Subscriber.</span></span> <span data-ttu-id="8df88-118">LAN 接続とダイヤルアップ接続には異なる時間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="8df88-118">Different times can be specified for LAN connections and dial-up connections.</span></span>  
  
 <span data-ttu-id="8df88-119">レプリケーション モニターまたは [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql)を使用して警告を有効にするときは、警告を表示するタイミングを決定するしきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="8df88-119">When you enable a warning by using Replication Monitor or [sp_replmonitorchangepublicationthreshold](/sql/relational-databases/system-stored-procedures/sp-replmonitorchangepublicationthreshold-transact-sql), you specify a threshold that determines when a warning is triggered.</span></span> <span data-ttu-id="8df88-120">指定したしきい値に達するか、そのしきい値を超えた場合、警告がレプリケーション モニターに表示され、イベントが Windows イベント ログに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="8df88-120">When that threshold is met or exceeded, a warning is displayed in Replication Monitor, and an event is written to the Windows event log.</span></span> <span data-ttu-id="8df88-121">しきい値に達した時点で、SQL Server エージェントの警告を表示させることもできます。</span><span class="sxs-lookup"><span data-stu-id="8df88-121">Reaching a threshold can also trigger a SQL Server Agent alert.</span></span> <span data-ttu-id="8df88-122">詳細については、「[レプリケーション モニターのしきい値と警告の設定](monitor/set-thresholds-and-warnings-in-replication-monitor.md)」および「[プログラムによるレプリケーションの監視](monitoring-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df88-122">For more information, see [Set Thresholds and Warnings in Replication Monitor](monitor/set-thresholds-and-warnings-in-replication-monitor.md) and [Programmatically Monitor Replication](monitoring-replication.md).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8df88-123">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8df88-123">User Action</span></span>  
 <span data-ttu-id="8df88-124">サブスクリプションが期間のしきい値を超えた場合は、システムでパフォーマンスの問題が発生しているかどうか、またはしきい値を調整する必要があるかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8df88-124">If a subscription exceeds a duration threshold, you must determine whether there is a performance issue with the system or whether the threshold should be adjusted.</span></span> <span data-ttu-id="8df88-125">レプリケーションを構成したら、パフォーマンス基準を策定します。これにより、アプリケーションおよびトポロジにおける通常のワークロードに対するレプリケーションの動作方法について判断できるようになります。</span><span class="sxs-lookup"><span data-stu-id="8df88-125">After you configure replication, develop a performance baseline that will let you determine how replication behaves with a workload that is typical for your applications and topology.</span></span> <span data-ttu-id="8df88-126">このパフォーマンス基準には同期の期間を組み入れ、適切なしきい値を設定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="8df88-126">Include duration of synchronization in this baseline so that you can set an appropriate value for the threshold.</span></span>  
  
 <span data-ttu-id="8df88-127">しきい値が適切でも、その値を超えた場合は、システム内のパフォーマンスのボトルネックになる部分を特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8df88-127">If the threshold value is appropriate, but it is being exceeded, you must determine where the performance bottleneck is in the system.</span></span> <span data-ttu-id="8df88-128">レプリケーション パフォーマンスの監視とトラブルシューティングを行う方法の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="8df88-128">For more information about how to monitor and troubleshoot replication performance, see the following topics:</span></span>  
  
-   <span data-ttu-id="8df88-129">[レプリケーション モニターを使用したパフォーマンスの監視](monitor/monitor-performance-with-replication-monitor.md) (特に、「マージ レプリケーションの詳細な同期パフォーマンスの表示」)</span><span class="sxs-lookup"><span data-stu-id="8df88-129">[Monitor Performance with Replication Monitor](monitor/monitor-performance-with-replication-monitor.md) (especially the section "Viewing Detailed Synchronization Performance for Merge Replication")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8df88-130">参照</span><span class="sxs-lookup"><span data-stu-id="8df88-130">See Also</span></span>  
 [<span data-ttu-id="8df88-131">エラーとイベントのリファレンス &#40;レプリケーション&#41;</span><span class="sxs-lookup"><span data-stu-id="8df88-131">Errors and Events Reference &#40;Replication&#41;</span></span>](errors-and-events-reference-replication.md)  
  
  