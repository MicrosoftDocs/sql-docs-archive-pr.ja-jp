---
title: インデックス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- index types [SQL Server]
ms.assetid: 00863b10-e77c-44c5-8ac2-bb4ac454eec6
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8ff8bb6c4ecad08b76fe5118119b5fd04ee31ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739973"
---
# <a name="indexes"></a><span data-ttu-id="ea8ee-102">インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-102">Indexes</span></span>
  <span data-ttu-id="ea8ee-103">次の表に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で使用できるインデックスの種類および追加情報へのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-103">The following table lists the types of indexes available in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and provides links to additional information.</span></span>  
  
|<span data-ttu-id="ea8ee-104">インデックスの種類</span><span class="sxs-lookup"><span data-stu-id="ea8ee-104">Index type</span></span>|<span data-ttu-id="ea8ee-105">説明</span><span class="sxs-lookup"><span data-stu-id="ea8ee-105">Description</span></span>|<span data-ttu-id="ea8ee-106">追加情報</span><span class="sxs-lookup"><span data-stu-id="ea8ee-106">Additional information</span></span>|  
|----------------|-----------------|----------------------------|  
|<span data-ttu-id="ea8ee-107">ハッシュ インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-107">Hash</span></span>|<span data-ttu-id="ea8ee-108">ハッシュ インデックスの場合は、インメモリ ハッシュ テーブルを通じてデータにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-108">With a hash index, data is accessed through an in-memory hash table.</span></span> <span data-ttu-id="ea8ee-109">ハッシュ インデックスは、バケット数の関数である固定量のメモリを消費します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-109">Hash indexes consume a fixed amount of memory, which is a function of the bucket count.</span></span>|[<span data-ttu-id="ea8ee-110">メモリ最適化テーブルでのインデックス使用のガイドライン</span><span class="sxs-lookup"><span data-stu-id="ea8ee-110">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)|  
|<span data-ttu-id="ea8ee-111">メモリ最適化された非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-111">memory-optimized nonclustered indexes</span></span>|<span data-ttu-id="ea8ee-112">メモリ最適化された非クラスター化インデックスの場合、メモリ消費量はインデックス キー列の行数とサイズによって決まります。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-112">For memory-optimized nonclustered indexes, memory consumption is a function of the row count and the size of the index key columns</span></span>|[<span data-ttu-id="ea8ee-113">メモリ最適化テーブルでのインデックス使用のガイドライン</span><span class="sxs-lookup"><span data-stu-id="ea8ee-113">Guidelines for Using Indexes on Memory-Optimized Tables</span></span>](../in-memory-oltp/memory-optimized-tables.md)|  
|<span data-ttu-id="ea8ee-114">クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-114">Clustered</span></span>|<span data-ttu-id="ea8ee-115">クラスター化インデックス キーを基準に、テーブルまたはビューのデータ行を並べ替えて格納します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-115">A clustered index sorts and stores the data rows of the table or view in order based on the clustered index key.</span></span> <span data-ttu-id="ea8ee-116">クラスター化インデックスは、クラスター化インデックス キーの値を基にして行を高速に取得できる B ツリー インデックス構造として実装されます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-116">The clustered index is implemented as a B-tree index structure that supports fast retrieval of the rows, based on their clustered index key values.</span></span>|[<span data-ttu-id="ea8ee-117">クラスター化インデックスと非クラスター化インデックスの概念</span><span class="sxs-lookup"><span data-stu-id="ea8ee-117">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)<br /><br /> [<span data-ttu-id="ea8ee-118">クラスター化インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-118">Create Clustered Indexes</span></span>](create-clustered-indexes.md)|  
|<span data-ttu-id="ea8ee-119">非クラスター化インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-119">Nonclustered</span></span>|<span data-ttu-id="ea8ee-120">非クラスター化インデックスが設定されたテーブルやビュー、またはヒープ上に定義できます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-120">A nonclustered index can be defined on a table or view with a clustered index or on a heap.</span></span> <span data-ttu-id="ea8ee-121">非クラスター化インデックスの各インデックス行には、非クラスター化キーの値および行ロケーターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-121">Each index row in the nonclustered index contains the nonclustered key value and a row locator.</span></span> <span data-ttu-id="ea8ee-122">このロケーターは、キー値があるクラスター化インデックスまたはヒープのデータ行を指します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-122">This locator points to the data row in the clustered index or heap having the key value.</span></span> <span data-ttu-id="ea8ee-123">インデックスの行はインデックス キーの値順に格納されますが、データ行は、クラスター化インデックスをテーブルに作成している場合以外は特定の順序に並ぶ保証はありません。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-123">The rows in the index are stored in the order of the index key values, but the data rows are not guaranteed to be in any particular order unless a clustered index is created on the table.</span></span>|[<span data-ttu-id="ea8ee-124">クラスター化インデックスと非クラスター化インデックスの概念</span><span class="sxs-lookup"><span data-stu-id="ea8ee-124">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)<br /><br /> [<span data-ttu-id="ea8ee-125">非クラスター化インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-125">Create Nonclustered Indexes</span></span>](create-nonclustered-indexes.md)|  
|<span data-ttu-id="ea8ee-126">一意</span><span class="sxs-lookup"><span data-stu-id="ea8ee-126">Unique</span></span>|<span data-ttu-id="ea8ee-127">インデックス キーの値が重複することがないので、テーブルまたはビューのすべての行をなんらかの方法で一意にすることができます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-127">A unique index ensures that the index key contains no duplicate values and therefore every row in the table or view is in some way unique.</span></span><br /><br /> <span data-ttu-id="ea8ee-128">クラスター化インデックスと非クラスター化インデックスは、どちらも一意にできます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-128">Uniqueness can be a property of both clustered and nonclustered indexes.</span></span>|[<span data-ttu-id="ea8ee-129">一意のインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-129">Create Unique Indexes</span></span>](create-unique-indexes.md)|  
|<span data-ttu-id="ea8ee-130">列ストア</span><span class="sxs-lookup"><span data-stu-id="ea8ee-130">Columnstore</span></span>|<span data-ttu-id="ea8ee-131">インメモリ columnstore インデックスは、列ベースのデータ ストレージと列ベースのクエリ処理を使用して、データを格納および管理します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-131">An in-memory columnstore index stores and manages data by using column-based data storage and column-based query processing.</span></span><br /><br /> <span data-ttu-id="ea8ee-132">列ストア インデックスは、主に一括読み込みと読み取り専用のクエリを実行するデータ ウェアハウスのワークロードで適切に動作します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-132">Columnstore indexes work well for data warehousing workloads that primarily perform bulk loads and read-only queries.</span></span> <span data-ttu-id="ea8ee-133">従来の行指向ストレージの最大 **10 倍のクエリ パフォーマンス** と、非圧縮データ サイズの最大 **7 倍のデータ圧縮** を達成するために列ストア インデックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-133">Use the columnstore index to achieve up to **10x query performance** gains over traditional row-oriented storage, and up to **7x data compression** over the uncompressed data size.</span></span>|[<span data-ttu-id="ea8ee-134">Columnstore Indexes Described</span><span class="sxs-lookup"><span data-stu-id="ea8ee-134">Columnstore Indexes Described</span></span>](columnstore-indexes-described.md)<br /><br /> [<span data-ttu-id="ea8ee-135">非クラスター化列ストア インデックスの使用</span><span class="sxs-lookup"><span data-stu-id="ea8ee-135">Using Nonclustered Columnstore Indexes</span></span>](../../database-engine/using-nonclustered-columnstore-indexes.md)<br /><br /> [<span data-ttu-id="ea8ee-136">クラスター化列ストア インデックスの使用</span><span class="sxs-lookup"><span data-stu-id="ea8ee-136">Using Clustered Columnstore Indexes</span></span>](../../database-engine/using-clustered-columnstore-indexes.md)|  
|<span data-ttu-id="ea8ee-137">付加列インデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-137">Index with included columns</span></span>|<span data-ttu-id="ea8ee-138">キー列に加えて非キー列を付加できるように拡張した非クラスター化インデックスです。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-138">A nonclustered index that is extended to include nonkey columns in addition to the key columns.</span></span>|[<span data-ttu-id="ea8ee-139">付加列インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-139">Create Indexes with Included Columns</span></span>](create-indexes-with-included-columns.md)|  
|<span data-ttu-id="ea8ee-140">計算列のインデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-140">Index on computed columns</span></span>|<span data-ttu-id="ea8ee-141">その他の列の値 (複数可) から、または特定の決定的入力から導かれる列のインデックスです。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-141">An index on a column that is derived from the value of one or more other columns, or certain deterministic inputs.</span></span>|[<span data-ttu-id="ea8ee-142">計算列のインデックス</span><span class="sxs-lookup"><span data-stu-id="ea8ee-142">Indexes on Computed Columns</span></span>](indexes-on-computed-columns.md)|  
|<span data-ttu-id="ea8ee-143">Filtered</span><span class="sxs-lookup"><span data-stu-id="ea8ee-143">Filtered</span></span>|<span data-ttu-id="ea8ee-144">最適化された非クラスター化インデックスです。このインデックスは、適切に定義されたデータのサブセットから選択するクエリに対応する際に特に適しています。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-144">An optimized nonclustered index, especially suited to cover queries that select from a well-defined subset of data.</span></span> <span data-ttu-id="ea8ee-145">フィルター選択されたインデックスは、フィルター述語を使用して、テーブル内の一部の行にインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-145">It uses a filter predicate to index a portion of rows in the table.</span></span> <span data-ttu-id="ea8ee-146">フィルター選択されたインデックスを適切にデザインすると、クエリのパフォーマンスが向上し、インデックスのメンテナンス コストを削減して、テーブル全体のインデックスと比較してインデックスのストレージ コストを削減することができます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-146">A well-designed filtered index can improve query performance, reduce index maintenance costs, and reduce index storage costs compared with full-table indexes.</span></span>|[<span data-ttu-id="ea8ee-147">フィルター選択されたインデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-147">Create Filtered Indexes</span></span>](create-filtered-indexes.md)|  
|<span data-ttu-id="ea8ee-148">Spatial</span><span class="sxs-lookup"><span data-stu-id="ea8ee-148">Spatial</span></span>|<span data-ttu-id="ea8ee-149">空間インデックスを使用すると、*geometry*データ型の列に含まれる空間オブジェクト ( **空間データ** ) に対する一部の操作をより効率的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-149">A spatial index provides the ability to perform certain operations more efficiently on spatial objects (*spatial data*) in a column of the **geometry** data type.</span></span> <span data-ttu-id="ea8ee-150">空間インデックスにより、比較的コストの高い空間操作を適用するオブジェクトの数を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-150">The spatial index reduces the number of objects on which relatively costly spatial operations need to be applied.</span></span>|[<span data-ttu-id="ea8ee-151">空間インデックスの概要</span><span class="sxs-lookup"><span data-stu-id="ea8ee-151">Spatial Indexes Overview</span></span>](../spatial/spatial-indexes-overview.md)|  
|<span data-ttu-id="ea8ee-152">XML</span><span class="sxs-lookup"><span data-stu-id="ea8ee-152">XML</span></span>|<span data-ttu-id="ea8ee-153">`xml` データ型列内の XML BLOB (binary large object) を細分化および永続化した表現です。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-153">A shredded, and persisted, representation of the XML binary large objects (BLOBs) in the `xml` data type column.</span></span>|[<span data-ttu-id="ea8ee-154">XML インデックス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ea8ee-154">XML Indexes &#40;SQL Server&#41;</span></span>](../xml/xml-indexes-sql-server.md)|  
|<span data-ttu-id="ea8ee-155">フルテキスト</span><span class="sxs-lookup"><span data-stu-id="ea8ee-155">Full-text</span></span>|<span data-ttu-id="ea8ee-156">Microsoft Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]により構築および管理されるトークンベースの特殊な機能インデックスです。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-156">A special type of token-based functional index that is built and maintained by the Microsoft Full-Text Engine for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="ea8ee-157">文字列データに対する高度な単語検索を効率的にサポートします。</span><span class="sxs-lookup"><span data-stu-id="ea8ee-157">It provides efficient support for sophisticated word searches in character string data.</span></span>|[<span data-ttu-id="ea8ee-158">フルテキスト インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="ea8ee-158">Populate Full-Text Indexes</span></span>](../search/populate-full-text-indexes.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="ea8ee-159">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="ea8ee-159">Related Tasks</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="ea8ee-160">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="ea8ee-160">Related Content</span></span>  
 [<span data-ttu-id="ea8ee-161">インデックスの SORT_IN_TEMPDB オプション</span><span class="sxs-lookup"><span data-stu-id="ea8ee-161">SORT_IN_TEMPDB Option For Indexes</span></span>](sort-in-tempdb-option-for-indexes.md)  
  
 [<span data-ttu-id="ea8ee-162">インデックスと制約の無効化</span><span class="sxs-lookup"><span data-stu-id="ea8ee-162">Disable Indexes and Constraints</span></span>](disable-indexes-and-constraints.md)  
  
 [<span data-ttu-id="ea8ee-163">インデックスと制約の有効化</span><span class="sxs-lookup"><span data-stu-id="ea8ee-163">Enable Indexes and Constraints</span></span>](enable-indexes-and-constraints.md)  
  
 [<span data-ttu-id="ea8ee-164">インデックスの名前変更</span><span class="sxs-lookup"><span data-stu-id="ea8ee-164">Rename Indexes</span></span>](rename-indexes.md)  
  
 [<span data-ttu-id="ea8ee-165">インデックス オプションの設定</span><span class="sxs-lookup"><span data-stu-id="ea8ee-165">Set Index Options</span></span>](set-index-options.md)  
  
 [<span data-ttu-id="ea8ee-166">Disk Space Requirements for Index DDL Operations</span><span class="sxs-lookup"><span data-stu-id="ea8ee-166">Disk Space Requirements for Index DDL Operations</span></span>](disk-space-requirements-for-index-ddl-operations.md)  
  
 [<span data-ttu-id="ea8ee-167">インデックスの再編成と再構築</span><span class="sxs-lookup"><span data-stu-id="ea8ee-167">Reorganize and Rebuild Indexes</span></span>](reorganize-and-rebuild-indexes.md)  
  
 [<span data-ttu-id="ea8ee-168">インデックスの FILL FACTOR の指定</span><span class="sxs-lookup"><span data-stu-id="ea8ee-168">Specify Fill Factor for an Index</span></span>](specify-fill-factor-for-an-index.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea8ee-169">参照</span><span class="sxs-lookup"><span data-stu-id="ea8ee-169">See Also</span></span>  
 [<span data-ttu-id="ea8ee-170">クラスター化インデックスと非クラスター化インデックスの概念</span><span class="sxs-lookup"><span data-stu-id="ea8ee-170">Clustered and Nonclustered Indexes Described</span></span>](clustered-and-nonclustered-indexes-described.md)  
  
  