---
title: 書き込み許可パーティション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storage [Analysis Services], partitions
- write-enabled partitions [Analysis Services]
- partitions [Analysis Services], write-enabled
- partitions [Analysis Services], storage
- writeback [Analysis Services], partitions
- storing data [Analysis Services], partitions
ms.assetid: 46e7683f-03ce-4af2-bd99-a5203733d723
author: minewiskan
ms.author: owend
ms.openlocfilehash: bd4bd012847c3aee231767e94bead86a507ecc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716914"
---
# <a name="write-enabled-partitions"></a><span data-ttu-id="46d24-102">書き込み許可パーティション</span><span class="sxs-lookup"><span data-stu-id="46d24-102">Write-Enabled Partitions</span></span>
  <span data-ttu-id="46d24-103">キューブ内のデータは通常、読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="46d24-103">The data in a cube is generally read-only.</span></span> <span data-ttu-id="46d24-104">ただし、シナリオによっては、パーティションに書き込み許可を設定する必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="46d24-104">However, for certain scenarios, you may want to write-enable a partition.</span></span> <span data-ttu-id="46d24-105">書き込み許可パーティションを使用すると、ビジネス ユーザーは、セル値を変更し、その変更がキューブ データに与える影響を分析して、シナリオを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="46d24-105">Write-enabled partitions are used to enable business users to explore scenarios by changing cell values and analyzing the effects of the changes on cube data.</span></span> <span data-ttu-id="46d24-106">パーティションを書き込み許可にすると、クライアント アプリケーションは、パーティションのデータへの変更内容を記録できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-106">When you write-enable a partition, client applications can record changes to the data in the partition.</span></span> <span data-ttu-id="46d24-107">これらの変更内容は、書き戻しデータとして知られており、個別のテーブルに格納され、メジャー グループの既存のデータは上書きされません。</span><span class="sxs-lookup"><span data-stu-id="46d24-107">These changes, known as writeback data, are stored in a separate table and do not overwrite any existing data in a measure group.</span></span> <span data-ttu-id="46d24-108">ただし、キューブ データの一部のように、クエリ結果に組み込まれます。</span><span class="sxs-lookup"><span data-stu-id="46d24-108">However, they are incorporated into query results as if they are part of the cube data.</span></span>  
  
 <span data-ttu-id="46d24-109">キューブ全体を書き込み許可にすることも、キューブ内の特定のパーティションのみを書き込み許可にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="46d24-109">You can write-enable an entire cube or only certain partitions in the cube.</span></span> <span data-ttu-id="46d24-110">書き込み許可ディメンションは、互いに異なりますが補完的です。</span><span class="sxs-lookup"><span data-stu-id="46d24-110">Write-enabled dimensions are different but complementary.</span></span> <span data-ttu-id="46d24-111">書き込み許可パーティションではパーティション セルを更新でき、書き込み許可ディメンションではディメンション メンバーを更新できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-111">A write-enabled partition lets users update partition cells, whereas a write-enabled dimension lets users update dimension members.</span></span> <span data-ttu-id="46d24-112">また、これらの 2 つの機能を組み合わせて使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="46d24-112">You can also use these two features in combination.</span></span> <span data-ttu-id="46d24-113">たとえば、書き込み許可キューブまたは書き込み可能パーティションには、書き込み許可ディメンションを含める必要はありません。</span><span class="sxs-lookup"><span data-stu-id="46d24-113">For example, a write-enabled cube or a write-enabled partition does not have to include any write-enabled dimensions.</span></span> <span data-ttu-id="46d24-114">**関連トピック:**[書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)。</span><span class="sxs-lookup"><span data-stu-id="46d24-114">**Related topic:**[Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46d24-115">データ ソースとして Microsoft Access データベースを持つキューブを書き込み許可にするときは、キューブ、パーティション、またはディメンションのデータ ソース定義に Microsoft OLE DB Provider for ODBC Drivers を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="46d24-115">If you want to write-enable a cube that has a Microsoft Access database as a data source, do not use Microsoft OLE DB Provider for ODBC Drivers in the data source definitions for the cube, its partitions, or its dimensions.</span></span> <span data-ttu-id="46d24-116">代わりに、Microsoft Jet 4.0 OLE DB Provider、または Jet 4.0 OLE を含む任意のバージョンの Jet Service Pack を使用できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-116">Instead, you can use Microsoft Jet 4.0 OLE DB Provider, or any version of the Jet Service Pack that includes Jet 4.0 OLE.</span></span> <span data-ttu-id="46d24-117">詳細については、マイクロソフトサポート技術情報の記事「 [Microsoft Jet 4.0 データベースエンジンの最新の Service Pack を取得する方法](https://support.microsoft.com/?kbid=239114)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46d24-117">For more information, see the Microsoft Knowledge Base article [How to obtain the latest service pack for the Microsoft Jet 4.0 Database Engine](https://support.microsoft.com/?kbid=239114).</span></span>  
  
 <span data-ttu-id="46d24-118">キューブを書き込み許可にできるのは、そのすべてのメジャーに `Sum` 集計関数が使用されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="46d24-118">A cube can be write-enabled only if all its measures use the `Sum` aggregate function.</span></span> <span data-ttu-id="46d24-119">リンク メジャー グループとローカル キューブは書き込み許可にできません。</span><span class="sxs-lookup"><span data-stu-id="46d24-119">Linked measure groups and local cubes cannot be write-enabled.</span></span>  
  
## <a name="writeback-storage"></a><span data-ttu-id="46d24-120">書き戻しストレージ</span><span class="sxs-lookup"><span data-stu-id="46d24-120">Writeback Storage</span></span>  
 <span data-ttu-id="46d24-121">ビジネス ユーザーによるすべての変更は、現在表示中の値との差分として書き戻しテーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="46d24-121">Any change made by the business user is stored in the writeback table as a difference from the currently displayed value.</span></span> <span data-ttu-id="46d24-122">たとえば、エンド ユーザーがあるセル値を 90 から 100 に変更した場合、書き戻しテーブルには値 `+10` が格納されます。このとき、変更時刻および変更を行ったビジネス ユーザーに関する情報も格納されます。</span><span class="sxs-lookup"><span data-stu-id="46d24-122">For example, if an end user changes a cell value from 90 to 100, the value `+10` is stored in the writeback table, together with the time of the change and information about the business user who made it.</span></span> <span data-ttu-id="46d24-123">クライアント アプリケーションには、蓄積された変更の最終結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="46d24-123">The net effect of accumulated changes is displayed to client applications.</span></span> <span data-ttu-id="46d24-124">キューブにある元の値はそのまま維持され、変更の監査記録は書き戻しテーブルに記録されます。</span><span class="sxs-lookup"><span data-stu-id="46d24-124">The original value in the cube is preserved, and an audit trail of changes is recorded in the writeback table.</span></span>  
  
 <span data-ttu-id="46d24-125">リーフ セルおよび非リーフ セルへの変更の処理は異なります。</span><span class="sxs-lookup"><span data-stu-id="46d24-125">Changes to leaf and nonleaf cells are handled differently.</span></span> <span data-ttu-id="46d24-126">リーフ セルは、メジャー グループによって参照されるすべてのディメンションのメジャーとリーフ メンバーの交差部分を表します。</span><span class="sxs-lookup"><span data-stu-id="46d24-126">A leaf cell represents an intersection of a measure and a leaf member from every dimension referenced by the measure group.</span></span> <span data-ttu-id="46d24-127">リーフ セルの値は、ファクト テーブルから直接取得されるものであり、ドリル ダウンでそれ以上分割することはできません。</span><span class="sxs-lookup"><span data-stu-id="46d24-127">The value of a leaf cell is taken directly from the fact table, and cannot be divided further by drilling down.</span></span> <span data-ttu-id="46d24-128">キューブまたはいずれかのパーティションが書き込み可能であれば、リーフ セルに変更を加えることができます。</span><span class="sxs-lookup"><span data-stu-id="46d24-128">If a cube or any partition is write-enabled, changes can be made to a leaf cell.</span></span> <span data-ttu-id="46d24-129">非リーフ セルに変更を加えることができるのは、その非リーフ セルを構成するリーフ セル間で変更を配布する方法がクライアント アプリケーションに用意されている場合だけです。</span><span class="sxs-lookup"><span data-stu-id="46d24-129">Changes can be made to a nonleaf cell only if the client application provides a way of distributing the changes among the leaf cells that make up the nonleaf cell.</span></span> <span data-ttu-id="46d24-130">このプロセスは、"割り当て" と呼ばれ、多元式 (MDX) の UPDATE CUBE ステートメントを介して管理されます。</span><span class="sxs-lookup"><span data-stu-id="46d24-130">This process, called allocation, is managed through the UPDATE CUBE statement in Multidimensional Expressions (MDX).</span></span> <span data-ttu-id="46d24-131">ビジネス インテリジェンスの開発者は、UPDATE CUBE ステートメントを使用して、割り当て機能を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="46d24-131">Business intelligence developers can use the UPDATE CUBE statement to include allocation functionality.</span></span> <span data-ttu-id="46d24-132">詳細については、「 [UPDATE CUBE ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46d24-132">For more information, see [UPDATE CUBE Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-update-cube).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46d24-133">更新されるセルが重ならない場合は、`Update Isolation Level` 接続文字列プロパティを使用して、UPDATE CUBE のパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="46d24-133">When updated cells do not overlap, the `Update Isolation Level` connection string property can be used to enhance performance for UPDATE CUBE.</span></span> <span data-ttu-id="46d24-134">詳細については、「<xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46d24-134">For more information, see <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection.ConnectionString%2A>.</span></span>  
  
 <span data-ttu-id="46d24-135">非リーフ セルに加えられた変更がクライアント アプリケーションによって配布されるかどうかに関係なく、クエリが評価されるときは必ず、書き戻しテーブル内の変更がリーフ セルと非リーフ セルの両方に適用されるため、ビジネス ユーザーは変更がキューブ全体に与える影響を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="46d24-135">Regardless of whether a client application distributes changes that were made to nonleaf cells, whenever queries are evaluated, changes in the writeback table are applied to both leaf and nonleaf cells so that business users can view the effects of the changes throughout the cube.</span></span>  
  
 <span data-ttu-id="46d24-136">ビジネス ユーザーが行った変更は、独立した書き戻しテーブルに保持されます。このテーブルを使用して、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-136">Changes that were made by the business user are kept in a separate writeback table that you can work with as follows:</span></span>  
  
-   <span data-ttu-id="46d24-137">パーティションに変換して、変更を永続的にキューブに組み込む。</span><span class="sxs-lookup"><span data-stu-id="46d24-137">Convert to a partition to permanently incorporate changes into the cube.</span></span> <span data-ttu-id="46d24-138">このアクションはメジャー グループを読み取り専用にします。</span><span class="sxs-lookup"><span data-stu-id="46d24-138">This action makes the measure group read-only.</span></span> <span data-ttu-id="46d24-139">フィルター式を指定して、変換する変更を選択できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-139">You can specify a filter expression to select the changes you want to convert.</span></span>  
  
-   <span data-ttu-id="46d24-140">破棄して、パーティションを元の状態に戻す。</span><span class="sxs-lookup"><span data-stu-id="46d24-140">Discard to return the partition to its original state.</span></span> <span data-ttu-id="46d24-141">このアクションはパーティションを読み取り専用にします。</span><span class="sxs-lookup"><span data-stu-id="46d24-141">This action makes the partition read-only.</span></span>  
  
## <a name="security"></a><span data-ttu-id="46d24-142">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="46d24-142">Security</span></span>  
 <span data-ttu-id="46d24-143">ビジネス ユーザーは、属しているロールにキューブのセルへの読み取り/書き込み権限が割り当てられている場合にのみキューブの書き戻しテーブルに変更内容を記録できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-143">A business user is permitted to record changes in a cube's writeback table only if the business user belongs to a role that has read/write permission to the cube's cells.</span></span> <span data-ttu-id="46d24-144">ロールごとに、更新できるキューブ セルと更新できないキューブ セルを管理できます。</span><span class="sxs-lookup"><span data-stu-id="46d24-144">For each role, you can control which cube cells can and cannot be updated.</span></span> <span data-ttu-id="46d24-145">詳細については、「 [Grant cube or model permissions &#40;Analysis Services&#41;](../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46d24-145">For more information, see [Grant cube or model permissions &#40;Analysis Services&#41;](../multidimensional-models/grant-cube-or-model-permissions-analysis-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d24-146">参照</span><span class="sxs-lookup"><span data-stu-id="46d24-146">See Also</span></span>  
 <span data-ttu-id="46d24-147">[書き込み許可ディメンション](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md) </span><span class="sxs-lookup"><span data-stu-id="46d24-147">[Write-Enabled Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md) </span></span>  
 <span data-ttu-id="46d24-148">[集計と集計のデザイン](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span><span class="sxs-lookup"><span data-stu-id="46d24-148">[Aggregations and Aggregation Designs](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md) </span></span>  
 <span data-ttu-id="46d24-149">[パーティション &#40;Analysis Services-多次元データ&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="46d24-149">[Partitions &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="46d24-150">書き込み許可ディメンション</span><span class="sxs-lookup"><span data-stu-id="46d24-150">Write-Enabled Dimensions</span></span>](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  