---
title: テーブル値パラメーターを構成する列の記述子フィールド |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), descriptor fields for constituent columns
ms.assetid: 944b3968-fd47-4847-98d6-b87e8ef2acdc
author: rothja
ms.author: jroth
ms.openlocfilehash: 7474a4a80309f6ce9754fefabfd0080c89f803b3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643822"
---
# <a name="descriptor-fields-for-table-valued-parameter-constituent-columns"></a><span data-ttu-id="1a5f2-102">テーブル値パラメーターを構成する列の記述子フィールド</span><span class="sxs-lookup"><span data-stu-id="1a5f2-102">Descriptor Fields for Table-Valued Parameter Constituent Columns</span></span>
  <span data-ttu-id="1a5f2-103">このセクションで説明するテーブル値パラメーターの記述子フィールドは、実装パラメーター記述子 (IPD) のハンドルと共に[SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md)と[SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md)を使用して操作します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-103">The table-valued parameter descriptor fields described in this section are manipulated by using [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) and [SQLSetDescField](../native-client-odbc-api/sqlsetdescfield.md) with the handle for the implementation parameter descriptor (IPD).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a5f2-104">解説</span><span class="sxs-lookup"><span data-stu-id="1a5f2-104">Remarks</span></span>  
 <span data-ttu-id="1a5f2-105">SQL_DESC_AUTO_UNIQUE_VALUE は、その他の機能と同様にテーブル値パラメーターで使用されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-105">SQL_DESC_AUTO_UNIQUE_VALUE is used for table-valued parameters as well as other features.</span></span>  
  
|<span data-ttu-id="1a5f2-106">属性名</span><span class="sxs-lookup"><span data-stu-id="1a5f2-106">Attribute name</span></span>|<span data-ttu-id="1a5f2-107">Type</span><span class="sxs-lookup"><span data-stu-id="1a5f2-107">Type</span></span>|<span data-ttu-id="1a5f2-108">説明</span><span class="sxs-lookup"><span data-stu-id="1a5f2-108">Description</span></span>|  
|--------------------|----------|-----------------|  
|<span data-ttu-id="1a5f2-109">SQL_DESC_AUTO_UNIQUE_VALUE</span><span class="sxs-lookup"><span data-stu-id="1a5f2-109">SQL_DESC_AUTO_UNIQUE_VALUE</span></span>|<span data-ttu-id="1a5f2-110">SQLINTEGER</span><span class="sxs-lookup"><span data-stu-id="1a5f2-110">SQLINTEGER</span></span>|<span data-ttu-id="1a5f2-111">SQL_TRUE はこの列が ID 列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-111">SQL_TRUE indicates that this column is an identity column.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1a5f2-112">では、この情報を使用してパフォーマンスを最適化できますが、id 列に対してアプリケーションを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-112">can use this information to optimize performance, but applications are not required to set it for identity columns.</span></span>|  
  
 <span data-ttu-id="1a5f2-113">アプリケーション パラメーター記述子 (APD) および実装パラメーター記述子 (IPD) のすべてのパラメーターの型に追加される属性を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-113">The following attributes are added to all parameter types in the application parameter descriptor (APD) and implementation parameter descriptor (IPD):</span></span>  
  
|<span data-ttu-id="1a5f2-114">属性名</span><span class="sxs-lookup"><span data-stu-id="1a5f2-114">Attribute name</span></span>|<span data-ttu-id="1a5f2-115">Type</span><span class="sxs-lookup"><span data-stu-id="1a5f2-115">Type</span></span>|<span data-ttu-id="1a5f2-116">説明</span><span class="sxs-lookup"><span data-stu-id="1a5f2-116">Description</span></span>|  
|--------------------|----------|-----------------|  
|<span data-ttu-id="1a5f2-117">SQL_CA_SS_COLUMN_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="1a5f2-117">SQL_CA_SS_COLUMN_COMPUTED</span></span>|<span data-ttu-id="1a5f2-118">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="1a5f2-118">SQLSMALLINT</span></span>|<span data-ttu-id="1a5f2-119">SQL_TRUE はこの列が計算列であることを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-119">SQL_TRUE indicates that this column is computed.</span></span><br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1a5f2-120">では、この情報を使用してパフォーマンスを最適化できますが、計算列にアプリケーションを設定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-120">can use this information to optimize performance, but applications are not required to set it for computed columns.</span></span><br /><br /> <span data-ttu-id="1a5f2-121">テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-121">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span>|  
|<span data-ttu-id="1a5f2-122">SQL_CA_SS_COLUMN_IN_UNIQUE_KEY</span><span class="sxs-lookup"><span data-stu-id="1a5f2-122">SQL_CA_SS_COLUMN_IN_UNIQUE_KEY</span></span>|<span data-ttu-id="1a5f2-123">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="1a5f2-123">SQLSMALLINT</span></span>|<span data-ttu-id="1a5f2-124">SQL_TRUE はテーブル値パラメーターの列が一意キーに参加することを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-124">SQL_TRUE indicates that a table-valued parameter column participates in a unique key.</span></span> <span data-ttu-id="1a5f2-125">これにより、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-125">This can result in better query performance.</span></span> <span data-ttu-id="1a5f2-126">テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-126">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span>|  
|<span data-ttu-id="1a5f2-127">SQL_CA_SS_COLUMN_SORT_ORDER</span><span class="sxs-lookup"><span data-stu-id="1a5f2-127">SQL_CA_SS_COLUMN_SORT_ORDER</span></span>|<span data-ttu-id="1a5f2-128">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="1a5f2-128">SQLSMALLINT</span></span>|<span data-ttu-id="1a5f2-129">テーブル値パラメーターの列の並べ替え順を示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-129">Indicates the sort order of a table-valued parameter column.</span></span> <span data-ttu-id="1a5f2-130">これにより、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-130">This can result in better query performance.</span></span> <span data-ttu-id="1a5f2-131">テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-131">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span> <span data-ttu-id="1a5f2-132">使用できる値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-132">The possible values are the following:</span></span><br /><br /> <span data-ttu-id="1a5f2-133">-SQL_SS_ASCENDING_ORDER</span><span class="sxs-lookup"><span data-stu-id="1a5f2-133">-   SQL_SS_ASCENDING_ORDER</span></span><br /><span data-ttu-id="1a5f2-134">-SQL_SS_DESCENDING_ORDER</span><span class="sxs-lookup"><span data-stu-id="1a5f2-134">-   SQL_SS_DESCENDING_ORDER</span></span><br /><span data-ttu-id="1a5f2-135">-SQL_SS_ORDER_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="1a5f2-135">-   SQL_SS_ORDER_UNSPECIFIED</span></span><br /><br /> <span data-ttu-id="1a5f2-136">SQL_SS_ASCENDING_ORDER および SQL_SS_DESCENDING_ORDER 以外の値の場合、"属性の値が正しくありません" というメッセージで SQLSTATE HY024 のエラーが生成され、この値は SQL_SS_ORDER_UNSPECIFIED (この属性の既定値) として扱われます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-136">Values other than SQL_SS_ASCENDING_ORDER and SQL_SS_DESCENDING_ORDER generate an error with SQLSTATE HY024 and message 'Invalid attribute value' and are treated as SQL_SS_ORDER_UNSPECIFIED, which is the default value for this attribute.</span></span>|  
|<span data-ttu-id="1a5f2-137">SQL_CA_SS_COLUMN_SORT_ORDINAL</span><span class="sxs-lookup"><span data-stu-id="1a5f2-137">SQL_CA_SS_COLUMN_SORT_ORDINAL</span></span>|<span data-ttu-id="1a5f2-138">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="1a5f2-138">SQLSMALLINT</span></span>|<span data-ttu-id="1a5f2-139">テーブル値パラメーターの全体的な順序を定義する列セット内における、テーブル値パラメーター列の序数を示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-139">Indicates the ordinal of a table-valued parameter column in the set of columns that define the overall ordering for a table-valued parameter.</span></span> <span data-ttu-id="1a5f2-140">これにより、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-140">This can result in better query performance.</span></span> <span data-ttu-id="1a5f2-141">テーブル値パラメーターの列以外のバインドでは、この属性は無視されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-141">This attribute is ignored for bindings that are not table-valued parameter columns.</span></span> <span data-ttu-id="1a5f2-142">並べ替えの序数は 1 から始まります。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-142">Sort ordinals start at 1.</span></span> <span data-ttu-id="1a5f2-143">値が 0 (既定値) の場合は、テーブル値パラメーターの列に列の順序が設定されていないことを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-143">A value of 0, the default, indicates that a table-valued parameter column does not have column ordering.</span></span>|  
|<span data-ttu-id="1a5f2-144">SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE</span><span class="sxs-lookup"><span data-stu-id="1a5f2-144">SQL_CA_SS_COLUMN_HAS_DEFAULT_VALUE</span></span>|<span data-ttu-id="1a5f2-145">SQLSMALLINT</span><span class="sxs-lookup"><span data-stu-id="1a5f2-145">SQLSMALLINT</span></span>|<span data-ttu-id="1a5f2-146">テーブル値パラメーターのすべての行にこの列の既定値が設定されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-146">Indicates whether all rows in the table-valued parameter will have the default value for this column.</span></span> <span data-ttu-id="1a5f2-147">テーブル値パラメーターの場合、行ごとに既定値を選択できません。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-147">For table-valued parameters, it is not possible to select the default value on a row-by-row basis.</span></span> <span data-ttu-id="1a5f2-148">値が SQL_FALSE の場合は、行に既定値以外の値が設定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-148">A value of SQL_FALSE indicates that rows will have non-default values.</span></span> <span data-ttu-id="1a5f2-149">既定値です。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-149">This is the default.</span></span> <span data-ttu-id="1a5f2-150">値が SQL_TRUE の場合は、この列のすべての行に既定値が設定されることを示します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-150">A value of SQL_TRUE indicates that this column will have default values for all rows.</span></span><br /><br /> <span data-ttu-id="1a5f2-151">SQL_TRUE に設定されている場合、データはサーバーに送信されません。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-151">If set to SQL_TRUE, no data will be sent to the server.</span></span><br /><br /> <span data-ttu-id="1a5f2-152">列の値がサーバー処理で不要な場合、このフィールドは ID 列または計算列でも使用することができます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-152">This field can also be used with identity or computed columns if the column values are not required for server processing.</span></span>|  
  
 <span data-ttu-id="1a5f2-153">これらの属性は、テーブル値パラメーターの列に対してのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-153">These attributes are only valid for table-valued parameter columns.</span></span> <span data-ttu-id="1a5f2-154">他のパラメーターでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-154">They are ignored for other parameters.</span></span>  
  
 <span data-ttu-id="1a5f2-155">テーブル値パラメーターの列に SQL_CA_SS_COL_HAS_DEFAULT_VALUE を設定する場合は、その列の SQL_DESC_DATA_PTR が NULL ポインターである必要があります。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-155">If SQL_CA_SS_COL_HAS_DEFAULT_VALUE is set for a table-valued parameter column, SQL_DESC_DATA_PTR for that column must be a null pointer.</span></span> <span data-ttu-id="1a5f2-156">それ以外の場合は、SQLExecute または SQLExecDirect は SQL_ERROR を返します。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-156">Otherwise, SQLExecute or SQLExecDirect will return SQL_ERROR.</span></span> <span data-ttu-id="1a5f2-157">SQLSTATE = 07S01 というメッセージが表示され、"パラメーターの既定のパラメーターが正しく使用されていません" というメッセージが表示されます \<p> \<c> 。ここで、 \<p> はパラメーター序数で、 \<c> は列序数です。</span><span class="sxs-lookup"><span data-stu-id="1a5f2-157">A diagnostic record will be generated with SQLSTATE=07S01 and the message "Invalid use of default parameter for parameter \<p>, column \<c>", where \<p> is the parameter ordinal and \<c> is the column ordinal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a5f2-158">参照</span><span class="sxs-lookup"><span data-stu-id="1a5f2-158">See Also</span></span>  
 [<span data-ttu-id="1a5f2-159">テーブル値パラメーター &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="1a5f2-159">Table-Valued Parameters &#40;ODBC&#41;</span></span>](table-valued-parameters-odbc.md)  
  
  