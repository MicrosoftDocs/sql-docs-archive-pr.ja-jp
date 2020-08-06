---
title: '[オプション] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10020"
ms.assetid: 43e50133-45ef-47a2-b575-34dfcc28ec98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77f9c61f4cf1e71c9cad71f06c66ae2cbc95b45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712774"
---
# <a name="dataset-properties-dialog-box-options-report-builder"></a><span data-ttu-id="4a325-102">[オプション] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)</span><span class="sxs-lookup"><span data-stu-id="4a325-102">Dataset Properties Dialog Box, Options (Report Builder)</span></span>
  <span data-ttu-id="4a325-103">**[データセットのプロパティ]** ダイアログ ボックスの **[オプション]** を選択すると、照合順序オプションや小計を詳細行として処理するオプションなど、クエリのデータ オプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="4a325-103">Select **Options** on the **DatasetProperties** dialog box to change data options, such as collation options and treating subtotals as detail data, for the query.</span></span> <span data-ttu-id="4a325-104">照合順序の詳細については、 [SQL Server オンライン ブック](../../relational-databases/collations/collation-and-unicode-support.md) の「 [照合順序と Unicode のサポート](https://go.microsoft.com/fwlink/?linkid=98335)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4a325-104">For more information about collations, see [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md) in [SQL Server Books Online](https://go.microsoft.com/fwlink/?linkid=98335).</span></span>  
  
 <span data-ttu-id="4a325-105">レポート サーバー上の共有データセット定義の一部であるデータ オプションは、共有データセットを使用するすべてのレポートに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="4a325-105">Data options that are part of a shared dataset definition on the report server affect all reports that use the shared dataset.</span></span> <span data-ttu-id="4a325-106">共有データセットのオプションは、レポートに追加した後にオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="4a325-106">You can override options for the shared dataset after it is added to a report.</span></span> <span data-ttu-id="4a325-107">これらの変更は、オプションが定義されているレポートのみに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="4a325-107">These changes affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="4a325-108">埋め込みデータセットのデータ オプションは、オプションが定義されているレポートのみに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="4a325-108">Data options for an embedded dataset affect only the report in which they are defined.</span></span>  
  
 <span data-ttu-id="4a325-109">詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4a325-109">For more information, see [Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="4a325-110">Options</span><span class="sxs-lookup"><span data-stu-id="4a325-110">Options</span></span>  
 <span data-ttu-id="4a325-111">**Collation**</span><span class="sxs-lookup"><span data-stu-id="4a325-111">**Collation**</span></span>  
 <span data-ttu-id="4a325-112">データの並べ替えに使用される照合順序を決めるロケールを選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-112">Select a locale that determines the collation sequence to be used for sorting data.</span></span> <span data-ttu-id="4a325-113">**[既定]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-113">**Default** indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="4a325-114">値を取得できない場合、既定値はコンピューターのロケール設定から取得されます。</span><span class="sxs-lookup"><span data-stu-id="4a325-114">If the value cannot be derived, the default value is derived from the locale setting of the computer.</span></span>  
  
 <span data-ttu-id="4a325-115">**大文字と小文字の区別**</span><span class="sxs-lookup"><span data-stu-id="4a325-115">**Case sensitivity**</span></span>  
 <span data-ttu-id="4a325-116">大文字と小文字の区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-116">Select a value that determines case sensitivity.</span></span> <span data-ttu-id="4a325-117">データが大文字と小文字を区別するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-117">This option indicates whether the data is case-sensitive.</span></span> <span data-ttu-id="4a325-118">**[大文字と小文字の区別]** は、 **[True]** 、 **[False]** 、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-118">You can set **Case Sensitivity** to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="4a325-119">データ プロバイダーが大文字と小文字の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a325-119">If the data provider does not support the case-sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="4a325-120">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-120">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="4a325-121">**[アクセントの区別]**</span><span class="sxs-lookup"><span data-stu-id="4a325-121">**Accent sensitivity**</span></span>  
 <span data-ttu-id="4a325-122">アクセントの区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-122">Select a value that determines accent sensitivity.</span></span> <span data-ttu-id="4a325-123">**[アクセントの区別]** は、データでアクセントを区別するかどうかを示します。 **[True]** 、 **[False]** 、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-123">**Accent Sensitivity** indicates whether the data is accent sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report is run.</span></span> <span data-ttu-id="4a325-124">データ プロバイダーがアクセントの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a325-124">If the data provider does not support the accent sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="4a325-125">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-125">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="4a325-126">**[かなの区別]**</span><span class="sxs-lookup"><span data-stu-id="4a325-126">**Kanatype sensitivity**</span></span>  
 <span data-ttu-id="4a325-127">かなの区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-127">Select a value that determines kanatype sensitivity.</span></span> <span data-ttu-id="4a325-128">データでかなを区別するかどうかを示します。 **[True]** 、 **[False]** 、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-128">This option indicates whether the data is kanatype sensitive; it can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="4a325-129">データ プロバイダーがかなの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a325-129">If the data provider does not support the kanatype sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="4a325-130">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-130">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="4a325-131">**[文字幅の区別]**</span><span class="sxs-lookup"><span data-stu-id="4a325-131">**Width sensitivity**</span></span>  
 <span data-ttu-id="4a325-132">文字幅の区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-132">Select a value that determines width sensitivity.</span></span> <span data-ttu-id="4a325-133">データで文字幅を区別するかどうかを示します。 **[True]** 、 **[False]** 、または **[自動]** に設定できます。既定値の **[自動]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-133">This option indicates whether the data is width-sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="4a325-134">データ プロバイダーが文字幅の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="4a325-134">If the data provider does not support the width sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="4a325-135">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-135">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="4a325-136">**[小計を詳細行として解釈]**</span><span class="sxs-lookup"><span data-stu-id="4a325-136">**Interpret subtotals as detail rows**</span></span>  
 <span data-ttu-id="4a325-137">集計行ではなく詳細行として小計行を解釈するかどうかを示す値を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-137">Select a value that indicates whether you want subtotal rows to be interpreted as detail rows instead of aggregate rows.</span></span> <span data-ttu-id="4a325-138">既定値の [**自動**] は、レポートで `Aggregate` データセット内のフィールドにアクセスするために () 関数が使用されていない場合に、小計行を詳細行として処理することを示します。</span><span class="sxs-lookup"><span data-stu-id="4a325-138">The default value, **Auto**, indicates that the subtotal rows should be treated as detail rows if the report does not use the `Aggregate`() function to access any fields in the data set.</span></span> <span data-ttu-id="4a325-139">小計行を集計行として解釈する必要がある場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-139">If you want subtotal rows to be interpreted as aggregate rows, choose **False**.</span></span> <span data-ttu-id="4a325-140">小計行を詳細行として解釈し、その行が () 関数を使用しないことがわかっている場合は `Aggregate` 、[ **True**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="4a325-140">If you want the subtotal rows to be interpreted as detail rows and you know that they do not use the `Aggregate`() function, choose **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a325-141">参照</span><span class="sxs-lookup"><span data-stu-id="4a325-141">See Also</span></span>  
 <span data-ttu-id="4a325-142">[ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="4a325-142">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="4a325-143">[集計関数 &#40;レポートビルダーと SSRS&#41;](../report-design/report-builder-functions-aggregate-function.md) </span><span class="sxs-lookup"><span data-stu-id="4a325-143">[Aggregate Function &#40;Report Builder and SSRS&#41;](../report-design/report-builder-functions-aggregate-function.md) </span></span>  
 <span data-ttu-id="4a325-144">[データのフィルター処理、グループ化、並べ替え &#40;レポートビルダーと SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a325-144">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](../report-design/filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a325-145">[レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="4a325-145">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="4a325-146">[[クエリ] ([データセットのプロパティ] ダイアログ ボックス) (レポート ビルダー)](dataset-properties-dialog-box-query-report-builder.md)</span><span class="sxs-lookup"><span data-stu-id="4a325-146">[Dataset Properties Dialog Box, Query &#40;Report Builder&#41;](dataset-properties-dialog-box-query-report-builder.md)</span></span>  
  
  