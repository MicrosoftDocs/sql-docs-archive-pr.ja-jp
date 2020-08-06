---
title: '[オプション] ([データセットのプロパティ] ダイアログボックス)Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10130"
- sql12.rtp.rptdesigner.datasetproperties.options.f1
ms.assetid: 95299049-71ba-427f-b723-775cb696243f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 778365e8fc7f40700b0f8c1683260f15c860a32a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645411"
---
# <a name="dataset-properties-dialog-box-options"></a><span data-ttu-id="2a360-102">[オプション] ([データセットのプロパティ] ダイアログ ボックス)</span><span class="sxs-lookup"><span data-stu-id="2a360-102">Dataset Properties Dialog Box, Options</span></span>
  <span data-ttu-id="2a360-103">[ **Datasetproperties** ] ダイアログボックスの [**オプション**] を選択すると、クエリの照合順序オプションや小計などのデータオプションを変更できます。</span><span class="sxs-lookup"><span data-stu-id="2a360-103">Select **Options** on the **DatasetProperties** dialog box to change data options, such as collation options and subtotals, for the query.</span></span> <span data-ttu-id="2a360-104">詳細については、「 [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a360-104">For more information, see [Collation and Unicode Support](../relational-databases/collations/collation-and-unicode-support.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a360-105">Options</span><span class="sxs-lookup"><span data-stu-id="2a360-105">Options</span></span>  
 <span data-ttu-id="2a360-106">**Collation**</span><span class="sxs-lookup"><span data-stu-id="2a360-106">**Collation**</span></span>  
 <span data-ttu-id="2a360-107">データの並べ替えに使用される照合順序を決めるロケールを選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-107">Select a locale that determines the collation sequence to be used for sorting data.</span></span> <span data-ttu-id="2a360-108">**[既定]** は、レポート サーバーが、レポートの実行時にデータ プロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-108">**Default** indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="2a360-109">値を取得できない場合、既定値はコンピューターのロケール設定から取得されます。</span><span class="sxs-lookup"><span data-stu-id="2a360-109">If the value cannot be derived, the default value is derived from the locale setting of the computer.</span></span>  
  
 <span data-ttu-id="2a360-110">**大文字と小文字の区別**</span><span class="sxs-lookup"><span data-stu-id="2a360-110">**Case sensitivity**</span></span>  
 <span data-ttu-id="2a360-111">大文字と小文字の区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-111">Select a value that determines case sensitivity.</span></span> <span data-ttu-id="2a360-112">データが大文字と小文字を区別するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-112">This option indicates whether the data is case-sensitive.</span></span> <span data-ttu-id="2a360-113">**大文字と小文字の区別**は、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-113">You can set **Case Sensitivity** to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="2a360-114">データ プロバイダーが大文字と小文字の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a360-114">If the data provider does not support the case-sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="2a360-115">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-115">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="2a360-116">**[アクセントの区別]**</span><span class="sxs-lookup"><span data-stu-id="2a360-116">**Accent sensitivity**</span></span>  
 <span data-ttu-id="2a360-117">アクセントの区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-117">Select a value that determines accent sensitivity.</span></span> <span data-ttu-id="2a360-118">**アクセントの区別**は、データがアクセントを区別するかどうかを示し、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-118">**Accent Sensitivity** indicates whether the data is accent sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report is run.</span></span> <span data-ttu-id="2a360-119">データ プロバイダーがアクセントの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a360-119">If the data provider does not support the accent sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="2a360-120">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-120">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="2a360-121">**[かなの区別]**</span><span class="sxs-lookup"><span data-stu-id="2a360-121">**Kanatype sensitivity**</span></span>  
 <span data-ttu-id="2a360-122">かなの区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-122">Select a value that determines kanatype sensitivity.</span></span> <span data-ttu-id="2a360-123">このオプションは、データがかな区別機微であるかどうかを示します。この値は、 **True**、 **False**、または**Auto**に設定できます。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-123">This option indicates whether the data is kanatype sensitive; it can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="2a360-124">データ プロバイダーがかなの区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a360-124">If the data provider does not support the kanatype sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="2a360-125">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-125">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="2a360-126">**[文字幅の区別]**</span><span class="sxs-lookup"><span data-stu-id="2a360-126">**Width sensitivity**</span></span>  
 <span data-ttu-id="2a360-127">文字幅の区別を決める値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-127">Select a value that determines width sensitivity.</span></span> <span data-ttu-id="2a360-128">このオプションは、データが文字幅を区別し、 **True**、 **False**、または**Auto**に設定できるかどうかを示します。既定値の [**自動**] は、レポートサーバーがレポートの実行時にデータプロバイダーから値の取得を試みる必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-128">This option indicates whether the data is width-sensitive and can be set to **True**, **False**, or **Auto**. The default value, **Auto**, indicates that the report server should attempt to derive the value from the data provider when the report runs.</span></span> <span data-ttu-id="2a360-129">データ プロバイダーが文字幅の区別をサポートしない場合、レポートは値が **[False]** の場合と同じように実行されます。</span><span class="sxs-lookup"><span data-stu-id="2a360-129">If the data provider does not support the width sensitivity type, the report runs as though the value were **False**.</span></span> <span data-ttu-id="2a360-130">値を正確に把握しており、その値が確実にサポートされる場合は、 **[True]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-130">If you know the value and you know it is supported, choose **True**.</span></span>  
  
 <span data-ttu-id="2a360-131">**[小計を詳細行として解釈]**</span><span class="sxs-lookup"><span data-stu-id="2a360-131">**Interpret subtotals as detail rows**</span></span>  
 <span data-ttu-id="2a360-132">集計行ではなく詳細行として小計行を解釈するかどうかを示す値を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-132">Select a value that indicates whether you want subtotal rows to be interpreted as detail rows instead of aggregate rows.</span></span> <span data-ttu-id="2a360-133">既定値の [**自動**] は、レポートで `Aggregate` データセット内のフィールドにアクセスするために () 関数が使用されていない場合に、小計行を詳細行として処理することを示します。</span><span class="sxs-lookup"><span data-stu-id="2a360-133">The default value, **Auto**, indicates that the subtotal rows should be treated as detail rows if the report does not use the `Aggregate`() function to access any fields in the data set.</span></span> <span data-ttu-id="2a360-134">小計行を集計行として解釈する必要がある場合は、 **[False]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-134">If you want subtotal rows to be interpreted as aggregate rows, choose **False**.</span></span> <span data-ttu-id="2a360-135">小計行を詳細行として解釈し、その行が () 関数を使用しないことがわかっている場合は `Aggregate` 、[ **True**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="2a360-135">If you want the subtotal rows to be interpreted as detail rows and you know that they do not use the `Aggregate`() function, choose **True**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a360-136">参照</span><span class="sxs-lookup"><span data-stu-id="2a360-136">See Also</span></span>  
 <span data-ttu-id="2a360-137">[レポートまたはテキストボックスのロケールを &#40;Reporting Services に設定&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="2a360-137">[Set the Locale for a Report or Text Box &#40;Reporting Services&#41;](report-design/set-the-locale-for-a-report-or-text-box-reporting-services.md) </span></span>  
 <span data-ttu-id="2a360-138">[レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する](report-data/report-datasets-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="2a360-138">[Add Data to a Report &#40;Report Builder and SSRS&#41;](report-data/report-datasets-ssrs.md) </span></span>  
 <span data-ttu-id="2a360-139">[Windows 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a360-139">[Windows Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/windows-collation-name-transact-sql) </span></span>  
 <span data-ttu-id="2a360-140">[SQL Server 照合順序名 &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2a360-140">[SQL Server Collation Name &#40;Transact-SQL&#41;](/sql/t-sql/statements/sql-server-collation-name-transact-sql) </span></span>  
 [<span data-ttu-id="2a360-141">集計関数 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="2a360-141">Aggregate Function &#40;Report Builder and SSRS&#41;</span></span>](report-design/report-builder-functions-aggregate-function.md)  
  
  