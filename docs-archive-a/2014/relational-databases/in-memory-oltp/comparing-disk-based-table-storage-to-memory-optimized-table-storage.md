---
title: ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: eacf443c-001a-445f-ad1c-5f5a45eca6f4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 47cf84427b2f4f26a29f732575530b384d9c4fc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741010"
---
# <a name="comparing-disk-based-table-storage-to-memory-optimized-table-storage"></a><span data-ttu-id="1b4dd-102">ディスク ベース テーブル ストレージとメモリ最適化テーブル ストレージの比較</span><span class="sxs-lookup"><span data-stu-id="1b4dd-102">Comparing Disk-Based Table Storage to Memory-Optimized Table Storage</span></span>
  
  
|<span data-ttu-id="1b4dd-103">Categories</span><span class="sxs-lookup"><span data-stu-id="1b4dd-103">Categories</span></span>|<span data-ttu-id="1b4dd-104">ディスク ベース テーブル</span><span class="sxs-lookup"><span data-stu-id="1b4dd-104">Disk-based Table</span></span>|<span data-ttu-id="1b4dd-105">持続性のあるメモリ最適化テーブル</span><span class="sxs-lookup"><span data-stu-id="1b4dd-105">Durable Memory-Optimized Table</span></span>|  
|----------------|-----------------------|-------------------------------------|  
|<span data-ttu-id="1b4dd-106">DDL (DDL)</span><span class="sxs-lookup"><span data-stu-id="1b4dd-106">DDL</span></span>|<span data-ttu-id="1b4dd-107">メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-107">Metadata information is stored in system tables in the primary filegroup of the database and is accessible through catalog views.</span></span>|<span data-ttu-id="1b4dd-108">メタデータ情報は、データベースのプライマリ ファイル グループのシステム テーブルに格納され、カタログ ビューを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-108">Metadata information is stored in system tables in the primary filegroup of the database and is accessible through catalog views.</span></span>|  
|<span data-ttu-id="1b4dd-109">構造体</span><span class="sxs-lookup"><span data-stu-id="1b4dd-109">Structure</span></span>|<span data-ttu-id="1b4dd-110">行は 8 KB 単位のページに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-110">Rows are stored in 8K pages.</span></span> <span data-ttu-id="1b4dd-111">1 ページには同じテーブルの行だけが格納されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-111">A page stores only rows from the same table.</span></span>|<span data-ttu-id="1b4dd-112">行は個別の行として格納されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-112">Rows are stored as individual rows.</span></span> <span data-ttu-id="1b4dd-113">ページ構造はありません。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-113">There is no page structure.</span></span> <span data-ttu-id="1b4dd-114">データ ファイル内の連続する 2 行はそれぞれ別のメモリ最適化テーブルに属することができます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-114">Two consecutive rows in a data file can belong to different memory-optimized tables.</span></span>|  
|<span data-ttu-id="1b4dd-115">インデックス</span><span class="sxs-lookup"><span data-stu-id="1b4dd-115">Indexes</span></span>|<span data-ttu-id="1b4dd-116">インデックスは、データ行と同様のページ構造に格納されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-116">Indexes are stored in a page structure similar to data rows.</span></span>|<span data-ttu-id="1b4dd-117">(インデックス行ではなく) インデックス定義のみが保存されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-117">Only the index definition is persisted (not index rows).</span></span> <span data-ttu-id="1b4dd-118">インデックスはメモリ内に保持され、データベース再起動の一部としてメモリ最適化テーブルがメモリに読み込まれるときに再生成されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-118">Indexes are maintained in-memory and are regenerated when the memory-optimized table is loaded into memory as part of restarting a database.</span></span> <span data-ttu-id="1b4dd-119">インデックス行は持続しないので、インデックスの変更に対してログ記録は実行されません。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-119">Since index rows are not persisted, no logging is done for index changes.</span></span>|  
|<span data-ttu-id="1b4dd-120">DML 操作</span><span class="sxs-lookup"><span data-stu-id="1b4dd-120">DML operation</span></span>|<span data-ttu-id="1b4dd-121">最初の手順は、ページを見つけてバッファー プールに読み込むことです。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-121">The first step is to find the page and then load it into buffer-pool.</span></span><br /><br /> <span data-ttu-id="1b4dd-122">挿入</span><span class="sxs-lookup"><span data-stu-id="1b4dd-122">Insert</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1b4dd-123">は、クラスター化インデックスの場合に行の順序を考慮して、ページ上に行を挿入します。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-123">inserts the row on the page accounting for row ordering in case of clustered index.</span></span><br /><br /> <span data-ttu-id="1b4dd-124">削除</span><span class="sxs-lookup"><span data-stu-id="1b4dd-124">Delete</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1b4dd-125">は、ページ上の削除する行を検索し、削除のマークを付けます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-125">locates the row to be deleted on the page and marks it deleted.</span></span><br /><br /> <span data-ttu-id="1b4dd-126">更新</span><span class="sxs-lookup"><span data-stu-id="1b4dd-126">Update</span></span><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="1b4dd-127">は、ページ上の行を検索します。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-127">locates the row on the page.</span></span> <span data-ttu-id="1b4dd-128">更新は非キー列に対してインプレースで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-128">The update is done in-place for non-key columns.</span></span> <span data-ttu-id="1b4dd-129">キー列の更新は削除と挿入操作によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-129">Key-column update is done by a delete and insert operation.</span></span><br /><br /> <span data-ttu-id="1b4dd-130">DML 操作の完了後、影響を受けるページは、最小ログ記録操作に関するバッファー プール ポリシー、チェックポイント、またはトランザクションのコミットの一部としてディスクにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-130">After the DML operation completes, the affected pages are flushed to disk as part of buffer pool policy, checkpoint or transaction commit for minimally-logged operations.</span></span> <span data-ttu-id="1b4dd-131">ページに対する読み取り/書き込みの両方が不要な I/O につながります。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-131">Both read/write operations on pages leads to unnecessary I/O.</span></span>|<span data-ttu-id="1b4dd-132">メモリ最適化テーブルの場合、データがメモリに格納されるので、DML 操作はメモリ内で直接実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-132">For memory-optimized tables, since the data resides in memory, the DML operations are done directly in memory.</span></span> <span data-ttu-id="1b4dd-133">メモリ最適化テーブルのログ レコードを読み取ってデータ ファイルとデルタ ファイルに保存するバックグラウンド スレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-133">There is a background thread that reads the log records for memory-optimized tables and persist them into data and delta files.</span></span> <span data-ttu-id="1b4dd-134">更新では新しい行バージョンが生成されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-134">An update generates a new row version.</span></span> <span data-ttu-id="1b4dd-135">ただし、更新は削除としてログに記録され、その後に挿入が続きます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-135">But an update is logged as a delete followed by an insert.</span></span>|  
|<span data-ttu-id="1b4dd-136">データの断片化</span><span class="sxs-lookup"><span data-stu-id="1b4dd-136">Data Fragmentation</span></span>|<span data-ttu-id="1b4dd-137">データ操作のフラグメント データにより、一部分しか入力されていないページや、ディスクでは連続していない論理的に連続するページが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-137">Data manipulation fragments data leading to partially filled pages and logically consecutive pages that are not contiguous on disk.</span></span> <span data-ttu-id="1b4dd-138">これにより、データ アクセスのパフォーマンスが低下するため、データのデフラグが必要になります。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-138">This degrades data access performance and requires you to defragment data.</span></span>|<span data-ttu-id="1b4dd-139">メモリ最適化データはページに格納されないので、データの断片化はありません。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-139">Memory-optimized data is not stored in pages so there is no data fragmentation.</span></span> <span data-ttu-id="1b4dd-140">ただし、行が更新または削除されると、データ ファイルとデルタ ファイルは圧縮が必要になります。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-140">However, as rows are updated and deleted, the data and delta files need to be compacted.</span></span> <span data-ttu-id="1b4dd-141">これは、マージ ポリシーに基づいて、バックグラウンドの MERGE スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="1b4dd-141">This is done by a background MERGE thread based on a merge policy.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b4dd-142">参照</span><span class="sxs-lookup"><span data-stu-id="1b4dd-142">See Also</span></span>  
 [<span data-ttu-id="1b4dd-143">メモリ最適化オブジェクト用ストレージの作成と管理</span><span class="sxs-lookup"><span data-stu-id="1b4dd-143">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  