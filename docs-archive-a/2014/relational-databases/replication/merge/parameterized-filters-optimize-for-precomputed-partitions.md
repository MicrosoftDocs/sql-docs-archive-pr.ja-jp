---
title: 事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- precomputed partitions [SQL Server replication]
- merge replication precomputed partitions [SQL Server replication]
- merge replication precomputed partitions [SQL Server replication], about precomputed partitions
ms.assetid: 85654bf4-e25f-4f04-8e34-bbbd738d60fa
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4ad0a33f0a5951256ff94bc78e7f09a88c05f227
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740838"
---
# <a name="optimize-parameterized-filter-performance-with-precomputed-partitions"></a><span data-ttu-id="ce327-102">事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化</span><span class="sxs-lookup"><span data-stu-id="ce327-102">Optimize Parameterized Filter Performance with Precomputed Partitions</span></span>
  <span data-ttu-id="ce327-103">事前計算済みパーティションは、フィルター選択されたマージ パブリケーションのパフォーマンス最適化に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce327-103">Precomputed partitions is a performance optimization that can be used with filtered merge publications.</span></span> <span data-ttu-id="ce327-104">フィルター選択されたパブリケーションで論理レコードを使用する場合にも事前計算済みパーティションが必要になります。</span><span class="sxs-lookup"><span data-stu-id="ce327-104">Precomputed partitions is also a requirement for using logical records on filtered publications.</span></span> <span data-ttu-id="ce327-105">論理レコードの詳細については、「[論理レコードによる関連行への変更をグループ化](group-changes-to-related-rows-with-logical-records.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-105">For more information about logical records, see [Group Changes to Related Rows with Logical Records](group-changes-to-related-rows-with-logical-records.md).</span></span>  
  
 <span data-ttu-id="ce327-106">サブスクライバーがパブリッシャーに同期するとき、パブリッシャーはサブスクライバーのフィルターを評価して、サブスクライバーのパーティションまたはデータセットに属する行を識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce327-106">When a Subscriber synchronizes with a Publisher, the Publisher must evaluate the Subscriber's filters to determine which rows belong to that Subscriber's partition, or data set.</span></span> <span data-ttu-id="ce327-107">フィルター選択されたデータセットを受け取る各サブスクライバーに対して、パブリッシャーの変更内容のパーティション メンバーシップを決定する処理を *パーティション評価*と呼びます。</span><span class="sxs-lookup"><span data-stu-id="ce327-107">This process of determining partition membership of changes at the Publisher for each Subscriber receiving a filtered dataset is referred to as *partition evaluation*.</span></span> <span data-ttu-id="ce327-108">事前計算済みパーティションがない場合は、特定のサブスクライバーに対する最後のマージ エージェントの実行以降、パブリッシャーのフィルター選択された列に対して加えられた変更ごとにパーティション評価を実行する必要があります。さらに、パブリッシャーと同期するすべてのサブスクライバーについて、この処理を繰り返し行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ce327-108">Without precomputed partitions, partition evaluation must be performed for each change made to a filtered column at the Publisher since the last time the Merge Agent ran for a specific Subscriber, and this process has to be repeated for every Subscriber that synchronizes with the Publisher.</span></span>  
  
 <span data-ttu-id="ce327-109">ただし、パブリッシャーとサブスクライバーが以降のバージョンで実行されていて、事前計算済みパーティションを使用している場合、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] パブリッシャーでのすべての変更に対するパーティションメンバーシップは事前計算済みされ、変更が行われた時点で保持されます。</span><span class="sxs-lookup"><span data-stu-id="ce327-109">However, if the Publisher and Subscriber are running on [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] or a later version and you use precomputed partitions, partition membership for all changes at the Publisher is precomputed and persisted at the time that the changes are made.</span></span> <span data-ttu-id="ce327-110">その結果、サブスクライバーはパブリッシャーとの同期時に、パーティションに関連する変更内容のダウンロードを即座に開始できます。パーティションの評価処理が実行されることはありません。</span><span class="sxs-lookup"><span data-stu-id="ce327-110">As a result, when a Subscriber synchronizes with the Publisher, it can immediately start to download changes relevant to its partition without having to go through the partition evaluation process.</span></span> <span data-ttu-id="ce327-111">パブリケーションに変更点、サブスクライバー、およびアーティクルが多数存在する場合は、この機能によってパフォーマンスの大幅な向上が期待できます。</span><span class="sxs-lookup"><span data-stu-id="ce327-111">This can lead to significant performance gains when a publication has a large number of changes, Subscribers, or articles in the publication.</span></span>  
  
 <span data-ttu-id="ce327-112">事前計算済みパーティションを使用するだけでなく、スナップショットを事前に生成するか、最初の同期時にサブスクライバーからスナップショットの生成および適用を要求できるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="ce327-112">In addition to using precomputed partitions, pre-generate snapshots and/or allow Subscribers to request snapshot generation and application the first time they synchronize.</span></span> <span data-ttu-id="ce327-113">これらのオプションの両方またはどちらかを使用して、パラメーター化されたフィルターを使用するパブリケーションに対するスナップショットを提供します。</span><span class="sxs-lookup"><span data-stu-id="ce327-113">Use one or both of these options to provide snapshots for publications that use parameterized filters.</span></span> <span data-ttu-id="ce327-114">これらのオプションのどちらかを指定しないと、 **bcp** ユーティリティを使用するのではなく、一連の SELECT ステートメントおよび INSERT ステートメントを使用してサブスクリプションが初期化されます。この処理は、かなり低速で実行されます。</span><span class="sxs-lookup"><span data-stu-id="ce327-114">If you do not specify one of these options, subscriptions are initialized using a series of SELECT and INSERT statements, rather than using the **bcp** utility; this process is much slower.</span></span> <span data-ttu-id="ce327-115">詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ce327-115">For more information, see [Snapshots for Merge Publications with Parameterized Filters](../snapshots-for-merge-publications-with-parameterized-filters.md).</span></span>  
  
 <span data-ttu-id="ce327-116">**事前計算済みパーティションを使用するには**</span><span class="sxs-lookup"><span data-stu-id="ce327-116">**To use precomputed partitions**</span></span>  
  
 <span data-ttu-id="ce327-117">上記のガイドラインに準拠するすべての新規および既存パブリケーションでは、事前計算済みパーティションが既定で有効になっています。</span><span class="sxs-lookup"><span data-stu-id="ce327-117">Precomputed partitions are enabled by default on all new and existing publications that adhere to the guidelines described above.</span></span> <span data-ttu-id="ce327-118">この設定は [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して変更することもできますし、プログラムを使用して変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="ce327-118">The setting can be changed through [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or programmatically.</span></span> <span data-ttu-id="ce327-119">詳細については、「 [Optimize Parameterized Row Filters](../publish/optimize-parameterized-row-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-119">For more information, see [Optimize Parameterized Row Filters](../publish/optimize-parameterized-row-filters.md).</span></span>  
  
## <a name="requirements-for-using-precomputed-partitions"></a><span data-ttu-id="ce327-120">事前計算済みパーティションを使用するための要件</span><span class="sxs-lookup"><span data-stu-id="ce327-120">Requirements for Using Precomputed Partitions</span></span>  
 <span data-ttu-id="ce327-121">以下の要件が満たされる場合、新規に作成されるマージ パブリケーションは既定で事前計算済みパーティションが有効になります。また、既存のパブリケーションは自動的にこの機能が使用できるようにアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="ce327-121">If the following requirements are met, new merge publications are, by default, created with precomputed partitions enabled, and existing publications are automatically upgraded to use the feature.</span></span> <span data-ttu-id="ce327-122">パブリケーションが要件を満たさない場合は、事前計算済みパーティションを使用できるようにパブリケーションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="ce327-122">If a publication does not meet the requirements, it can be changed, and then precomputed partitions can be enabled.</span></span> <span data-ttu-id="ce327-123">要件を満たすアーティクルと要件を満たさないアーティクルが混在している場合は、パブリケーションを 2 つ作成し、そのうちの 1 つで事前計算済みパーティションを有効にすることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-123">If some articles meet these requirements and some do not, consider creating two publications, with one enabled for precomputed partitions.</span></span>  
  
### <a name="requirements-for-filter-clauses"></a><span data-ttu-id="ce327-124">フィルター句の必要要件</span><span class="sxs-lookup"><span data-stu-id="ce327-124">Requirements for Filter Clauses</span></span>  
  
-   <span data-ttu-id="ce327-125">HOST_NAME() や SUSER_SNAME() など、パラメーター化された行フィルターで使用する関数はパラメーター化されたフィルター句に直接記述してください。ビューまたは動的関数の内部で入れ子にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce327-125">Any functions used in parameterized row filters, such as HOST_NAME() and SUSER_SNAME(), should appear directly in the parameterized filter clause and not be nested inside of a view or dynamic function.</span></span> <span data-ttu-id="ce327-126">これらの関数の詳細については、「[HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql)、「[SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql)」、および「[パラメーター化された行フィルター](parameterized-filters-parameterized-row-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-126">For more information about these functions, see [HOST_NAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/host-name-transact-sql), [SUSER_SNAME &#40;Transact-SQL&#41;](/sql/t-sql/functions/suser-sname-transact-sql), and [Parameterized Row Filters](parameterized-filters-parameterized-row-filters.md).</span></span>  
  
-   <span data-ttu-id="ce327-127">パーティションの作成後、各サブスクライバーに返される値を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce327-127">The values returned for each Subscriber should not change after the partition is created.</span></span> <span data-ttu-id="ce327-128">たとえば、フィルターで HOST_NAME() を使用する場合 (および HOST_NAME() の値をオーバーライドしない場合)、サブスクライバーでコンピューター名を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="ce327-128">For example, if you use HOST_NAME() in a filter (and do not override the HOST_NAME() value) do not change the computer name at the Subscriber.</span></span>  
  
-   <span data-ttu-id="ce327-129">結合フィルターに動的関数 (HOST_NAME() や SUSER_SNAME() など、同期するサブスクライバーによって異なる値に評価される関数) を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce327-129">Join filters should not contain dynamic functions (functions such as HOST_NAME() and SUSER_SNAME() that evaluate to a different value depending upon the Subscriber that is synchronizing).</span></span> <span data-ttu-id="ce327-130">動的関数はパラメーター化された行フィルターでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ce327-130">Only parameterized row filters should contain dynamic functions.</span></span>  
  
-   <span data-ttu-id="ce327-131">非決定的関数はフィルター句の中では使用できません。</span><span class="sxs-lookup"><span data-stu-id="ce327-131">Nondeterministic functions cannot be used in a filter clause.</span></span> <span data-ttu-id="ce327-132">非決定的関数の詳細については、「 [Deterministic and Nondeterministic Functions](../../user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-132">For more information about nondeterministic functions, see [Deterministic and Nondeterministic Functions](../../user-defined-functions/deterministic-and-nondeterministic-functions.md).</span></span>  
  
-   <span data-ttu-id="ce327-133">結合フィルター句またはパラメーター化されたフィルター句で参照されるビューに動的関数を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ce327-133">Views referenced in join filter clauses or parameterized filter clauses should not contain dynamic functions.</span></span>  
  
-   <span data-ttu-id="ce327-134">循環結合フィルターのリレーションシップをパブリケーションに格納することはできません。</span><span class="sxs-lookup"><span data-stu-id="ce327-134">There should be no circular join filter relationships in the publication.</span></span>  
  
### <a name="database-collation"></a><span data-ttu-id="ce327-135">データベースの照合順序</span><span class="sxs-lookup"><span data-stu-id="ce327-135">Database Collation</span></span>  
  
-   <span data-ttu-id="ce327-136">事前計算済みパーティションを使用する場合、比較を行う際にはテーブルや列ではなくデータベースの照合順序が常に使用されます。</span><span class="sxs-lookup"><span data-stu-id="ce327-136">When precomputed partitions are used, the collation of the database is always used when making comparisons, rather than the collation of the table or column.</span></span> <span data-ttu-id="ce327-137">次のシナリオについて検討してください。</span><span class="sxs-lookup"><span data-stu-id="ce327-137">Consider the following scenario:</span></span>  
  
    -   <span data-ttu-id="ce327-138">大文字と小文字が区別される照合順序のデータベースに、大文字と小文字が区別されない照合順序のテーブルが格納されています。</span><span class="sxs-lookup"><span data-stu-id="ce327-138">A database with a case-sensitive collation contains a table with a case-insensitive collation.</span></span>  
  
    -   <span data-ttu-id="ce327-139">テーブルに **ComputerName**列が含まれており、パラメーター化されたフィルター内でサブスクライバーのホスト名と比較されます。</span><span class="sxs-lookup"><span data-stu-id="ce327-139">The table contains a column **ComputerName**, which is compared against the host name of the Subscriber in a parameterized filter.</span></span>  
  
    -   <span data-ttu-id="ce327-140">この列が "MYCOMPUTER" という値の行と "mycomputer" という値の行が 1 つずつテーブルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="ce327-140">The table contains one row with the value "MYCOMPUTER" and one row with the value "mycomputer" in this column.</span></span>  
  
     <span data-ttu-id="ce327-141">サブスクライバーが "mycomputer" というホスト名で同期する場合、このサブスクライバーが受け取る行は 1 行のみです。データベースの照合順序により、大文字と小文字を区別して比較されるからです。</span><span class="sxs-lookup"><span data-stu-id="ce327-141">If the Subscriber synchronizes with a host name of "mycomputer", the Subscriber receives only one row because the comparison is case-sensitive (the collation of the database).</span></span> <span data-ttu-id="ce327-142">事前計算済みパーティションを使用しない場合、サブスクライバーは両方の行を受け取ります。テーブルの照合順序により、大文字と小文字は区別されないからです。</span><span class="sxs-lookup"><span data-stu-id="ce327-142">If precomputed partitions are not used, the Subscriber receives both rows, because the table has a case-insensitive collation.</span></span>  
  
## <a name="performance-of-precomputed-partitions"></a><span data-ttu-id="ce327-143">事前計算済みパーティションのパフォーマンス</span><span class="sxs-lookup"><span data-stu-id="ce327-143">Performance of Precomputed Partitions</span></span>  
 <span data-ttu-id="ce327-144">事前計算済みパーティションを使用する場合、サブスクライバーからパブリッシャーに変更内容をアップロードするときに若干のパフォーマンス コストがかかります。ただし、マージ処理に必要な時間の大部分は、パーティションの評価とパブリッシャーからサブスクライバーへの変更内容のダウンロードに費やされます。したがって、全体としてはパフォーマンスが大きく向上します。</span><span class="sxs-lookup"><span data-stu-id="ce327-144">There is a small performance cost with precomputed partitions when changes are uploaded from the Subscriber to the Publisher, but the bulk of merge processing time is spent evaluating partitions and downloading changes from the Publisher to the Subscriber, so the net gain can still be significant.</span></span> <span data-ttu-id="ce327-145">パフォーマンスがどの程度向上するかは、同時に同期するサブスクライバーの数、およびあるパーティションから別のパーティションに行を移動する同期ごとの更新数によって異なります。</span><span class="sxs-lookup"><span data-stu-id="ce327-145">The performance benefit will vary, depending on the number of Subscribers synchronizing concurrently and the number of updates per synchronization that move rows from one partition to another.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce327-146">参照</span><span class="sxs-lookup"><span data-stu-id="ce327-146">See Also</span></span>  
 [<span data-ttu-id="ce327-147">パラメーター化された行フィルター</span><span class="sxs-lookup"><span data-stu-id="ce327-147">Parameterized Row Filters</span></span>](parameterized-filters-parameterized-row-filters.md)  
  
  