---
title: Server Memory Change イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Server Memory Change event class
ms.assetid: c9836484-39c5-4a89-b080-3567783b6fff
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4dfa610b7632455c5d7d7a84efcb6101ffc7575b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645620"
---
# <a name="server-memory-change-event-class"></a><span data-ttu-id="0baec-102">Server Memory Change イベント クラス</span><span class="sxs-lookup"><span data-stu-id="0baec-102">Server Memory Change Event Class</span></span>
  <span data-ttu-id="0baec-103">**Server Memory Change** イベント クラスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用率が 1 MB または最大サーバー メモリ容量の 5 % のどちらか大きい方を超えて増加または減少したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="0baec-103">The **Server Memory Change** event class occurs when [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] memory usage has increased or decreased by either 1 megabyte (MB) or 5 percent of the maximum server memory, whichever is greater.</span></span>  
  
## <a name="server-memory-change-event-class-data-columns"></a><span data-ttu-id="0baec-104">Server Memory Change イベント クラスのデータ列</span><span class="sxs-lookup"><span data-stu-id="0baec-104">Server Memory Change Event Class Data Columns</span></span>  
  
|<span data-ttu-id="0baec-105">データ列名</span><span class="sxs-lookup"><span data-stu-id="0baec-105">Data column name</span></span>|<span data-ttu-id="0baec-106">データ型</span><span class="sxs-lookup"><span data-stu-id="0baec-106">Data type</span></span>|<span data-ttu-id="0baec-107">説明</span><span class="sxs-lookup"><span data-stu-id="0baec-107">Description</span></span>|<span data-ttu-id="0baec-108">列 ID</span><span class="sxs-lookup"><span data-stu-id="0baec-108">Column ID</span></span>|<span data-ttu-id="0baec-109">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-109">Yes</span></span>|  
|----------------------|---------------|-----------------|---------------|---------|  
|<span data-ttu-id="0baec-110">**EventClass**</span><span class="sxs-lookup"><span data-stu-id="0baec-110">**EventClass**</span></span>|<span data-ttu-id="0baec-111">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-111">**int**</span></span>|<span data-ttu-id="0baec-112">イベントの種類 = 81。</span><span class="sxs-lookup"><span data-stu-id="0baec-112">Type of event = 81.</span></span>|<span data-ttu-id="0baec-113">27</span><span class="sxs-lookup"><span data-stu-id="0baec-113">27</span></span>|<span data-ttu-id="0baec-114">いいえ</span><span class="sxs-lookup"><span data-stu-id="0baec-114">No</span></span>|  
|<span data-ttu-id="0baec-115">**EventSequence**</span><span class="sxs-lookup"><span data-stu-id="0baec-115">**EventSequence**</span></span>|<span data-ttu-id="0baec-116">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-116">**int**</span></span>|<span data-ttu-id="0baec-117">要求内の特定のイベントのシーケンス。</span><span class="sxs-lookup"><span data-stu-id="0baec-117">Sequence of a given event within the request.</span></span>|<span data-ttu-id="0baec-118">51</span><span class="sxs-lookup"><span data-stu-id="0baec-118">51</span></span>|<span data-ttu-id="0baec-119">いいえ</span><span class="sxs-lookup"><span data-stu-id="0baec-119">No</span></span>|  
|<span data-ttu-id="0baec-120">**EventSubClass**</span><span class="sxs-lookup"><span data-stu-id="0baec-120">**EventSubClass**</span></span>|<span data-ttu-id="0baec-121">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-121">**int**</span></span>|<span data-ttu-id="0baec-122">イベント サブクラスの種類。</span><span class="sxs-lookup"><span data-stu-id="0baec-122">Type of event subclass.</span></span><br /><br /> <span data-ttu-id="0baec-123">1 = メモリ増加</span><span class="sxs-lookup"><span data-stu-id="0baec-123">1=Memory Increase</span></span><br /><br /> <span data-ttu-id="0baec-124">2 = メモリ減少</span><span class="sxs-lookup"><span data-stu-id="0baec-124">2=Memory Decrease</span></span>|<span data-ttu-id="0baec-125">21</span><span class="sxs-lookup"><span data-stu-id="0baec-125">21</span></span>|<span data-ttu-id="0baec-126">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-126">Yes</span></span>|  
|<span data-ttu-id="0baec-127">**IntegerData**</span><span class="sxs-lookup"><span data-stu-id="0baec-127">**IntegerData**</span></span>|<span data-ttu-id="0baec-128">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-128">**int**</span></span>|<span data-ttu-id="0baec-129">メガバイト (MB) 単位の新しいメモリ サイズ。</span><span class="sxs-lookup"><span data-stu-id="0baec-129">New memory size, in megabytes (MB).</span></span>|<span data-ttu-id="0baec-130">25</span><span class="sxs-lookup"><span data-stu-id="0baec-130">25</span></span>|<span data-ttu-id="0baec-131">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-131">Yes</span></span>|  
|<span data-ttu-id="0baec-132">**IsSystem**</span><span class="sxs-lookup"><span data-stu-id="0baec-132">**IsSystem**</span></span>|<span data-ttu-id="0baec-133">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-133">**int**</span></span>|<span data-ttu-id="0baec-134">イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。</span><span class="sxs-lookup"><span data-stu-id="0baec-134">Indicates whether the event occurred on a system process or a user process.</span></span> <span data-ttu-id="0baec-135">1 はシステム、0 はユーザーです。</span><span class="sxs-lookup"><span data-stu-id="0baec-135">1 = system, 0 = user.</span></span>|<span data-ttu-id="0baec-136">60</span><span class="sxs-lookup"><span data-stu-id="0baec-136">60</span></span>|<span data-ttu-id="0baec-137">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-137">Yes</span></span>|  
|<span data-ttu-id="0baec-138">**RequestID**</span><span class="sxs-lookup"><span data-stu-id="0baec-138">**RequestID**</span></span>|<span data-ttu-id="0baec-139">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-139">**int**</span></span>|<span data-ttu-id="0baec-140">ステートメントが含まれている要求の ID。</span><span class="sxs-lookup"><span data-stu-id="0baec-140">ID of the request containing the statement.</span></span>|<span data-ttu-id="0baec-141">49</span><span class="sxs-lookup"><span data-stu-id="0baec-141">49</span></span>|<span data-ttu-id="0baec-142">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-142">Yes</span></span>|  
|<span data-ttu-id="0baec-143">**ServerName**</span><span class="sxs-lookup"><span data-stu-id="0baec-143">**ServerName**</span></span>|<span data-ttu-id="0baec-144">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0baec-144">**nvarchar**</span></span>|<span data-ttu-id="0baec-145">トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。</span><span class="sxs-lookup"><span data-stu-id="0baec-145">Name of the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] being traced.</span></span>|<span data-ttu-id="0baec-146">26</span><span class="sxs-lookup"><span data-stu-id="0baec-146">26</span></span>|<span data-ttu-id="0baec-147">いいえ</span><span class="sxs-lookup"><span data-stu-id="0baec-147">No</span></span>|  
|<span data-ttu-id="0baec-148">**SessionLoginName**</span><span class="sxs-lookup"><span data-stu-id="0baec-148">**SessionLoginName**</span></span>|<span data-ttu-id="0baec-149">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="0baec-149">**nvarchar**</span></span>|<span data-ttu-id="0baec-150">セッションを開始したユーザーのログイン名。</span><span class="sxs-lookup"><span data-stu-id="0baec-150">The login name of the user who originated the session.</span></span> <span data-ttu-id="0baec-151">たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0baec-151">For example, if you connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using Login1 and execute a statement as Login2, **SessionLoginName** shows Login1 and **LoginName** shows Login2.</span></span> <span data-ttu-id="0baec-152">この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0baec-152">This column displays both [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and Windows logins.</span></span>|<span data-ttu-id="0baec-153">64</span><span class="sxs-lookup"><span data-stu-id="0baec-153">64</span></span>|<span data-ttu-id="0baec-154">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-154">Yes</span></span>|  
|<span data-ttu-id="0baec-155">**SPID**</span><span class="sxs-lookup"><span data-stu-id="0baec-155">**SPID**</span></span>|<span data-ttu-id="0baec-156">**int**</span><span class="sxs-lookup"><span data-stu-id="0baec-156">**int**</span></span>|<span data-ttu-id="0baec-157">イベントが発生したセッションの ID。</span><span class="sxs-lookup"><span data-stu-id="0baec-157">ID of the session on which the event occurred.</span></span>|<span data-ttu-id="0baec-158">12</span><span class="sxs-lookup"><span data-stu-id="0baec-158">12</span></span>|<span data-ttu-id="0baec-159">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-159">Yes</span></span>|  
|<span data-ttu-id="0baec-160">**StartTime**</span><span class="sxs-lookup"><span data-stu-id="0baec-160">**StartTime**</span></span>|<span data-ttu-id="0baec-161">**datetime**</span><span class="sxs-lookup"><span data-stu-id="0baec-161">**datetime**</span></span>|<span data-ttu-id="0baec-162">イベントの開始時刻 (取得できた場合)。</span><span class="sxs-lookup"><span data-stu-id="0baec-162">Time at which the event started, if available.</span></span>|<span data-ttu-id="0baec-163">14</span><span class="sxs-lookup"><span data-stu-id="0baec-163">14</span></span>|<span data-ttu-id="0baec-164">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-164">Yes</span></span>|  
|<span data-ttu-id="0baec-165">**TransactionID**</span><span class="sxs-lookup"><span data-stu-id="0baec-165">**TransactionID**</span></span>|<span data-ttu-id="0baec-166">**bigint**</span><span class="sxs-lookup"><span data-stu-id="0baec-166">**bigint**</span></span>|<span data-ttu-id="0baec-167">システムによって割り当てられたトランザクション ID。</span><span class="sxs-lookup"><span data-stu-id="0baec-167">System-assigned ID of the transaction.</span></span>|<span data-ttu-id="0baec-168">4</span><span class="sxs-lookup"><span data-stu-id="0baec-168">4</span></span>|<span data-ttu-id="0baec-169">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-169">Yes</span></span>|  
|<span data-ttu-id="0baec-170">**XactSequence**</span><span class="sxs-lookup"><span data-stu-id="0baec-170">**XactSequence**</span></span>|<span data-ttu-id="0baec-171">**bigint**</span><span class="sxs-lookup"><span data-stu-id="0baec-171">**bigint**</span></span>|<span data-ttu-id="0baec-172">現在のトランザクションを説明するトークン。</span><span class="sxs-lookup"><span data-stu-id="0baec-172">Token that describes the current transaction.</span></span>|<span data-ttu-id="0baec-173">50</span><span class="sxs-lookup"><span data-stu-id="0baec-173">50</span></span>|<span data-ttu-id="0baec-174">はい</span><span class="sxs-lookup"><span data-stu-id="0baec-174">Yes</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0baec-175">参照</span><span class="sxs-lookup"><span data-stu-id="0baec-175">See Also</span></span>  
 <span data-ttu-id="0baec-176">[拡張イベント](../extended-events/extended-events.md) </span><span class="sxs-lookup"><span data-stu-id="0baec-176">[Extended Events](../extended-events/extended-events.md) </span></span>  
 <span data-ttu-id="0baec-177">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0baec-177">[sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql) </span></span>  
 [<span data-ttu-id="0baec-178">サーバー メモリに関するサーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="0baec-178">Server Memory Server Configuration Options</span></span>](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  