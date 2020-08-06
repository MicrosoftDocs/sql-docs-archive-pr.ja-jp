---
title: プログラム変数からの一括コピー |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bcp_bind function
- mapping data types [ODBC]
- SQL Server Native Client ODBC driver, bulk copy
- data types [ODBC], bulk copying
- ODBC, bulk copy operations
- program variables [ODBC]
ms.assetid: e4284a1b-7534-4b34-8488-b8d05ed67b8c
author: rothja
ms.author: jroth
ms.openlocfilehash: 5a50e8e104d63c63138a1ae14e27104181e6d9fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645590"
---
# <a name="bulk-copying-from-program-variables"></a><span data-ttu-id="5960d-102">プログラム変数からの一括コピー</span><span class="sxs-lookup"><span data-stu-id="5960d-102">Bulk Copying from Program Variables</span></span>
  <span data-ttu-id="5960d-103">プログラム変数から直接一括コピーできます。</span><span class="sxs-lookup"><span data-stu-id="5960d-103">You can bulk copy directly from program variables.</span></span> <span data-ttu-id="5960d-104">行のデータを保持し、 [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を呼び出して一括コピーを開始する変数を割り当てた後、各列に対して[bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)を呼び出して、列に関連付けられるプログラム変数の場所と形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-104">After allocating variables to hold the data for a row and calling [bcp_init](../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to start the bulk copy, call [bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for each column to specify the location and format of the program variable to be associated with the column.</span></span> <span data-ttu-id="5960d-105">各変数にデータを入力し、 [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)を呼び出して、サーバーに1行のデータを送信します。</span><span class="sxs-lookup"><span data-stu-id="5960d-105">Fill each variable with data, then call [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) to send one row of data to the server.</span></span> <span data-ttu-id="5960d-106">すべての行がサーバーに送信されるまで、変数の入力と**bcp_sendrow**の呼び出しを繰り返します。次に、 [bcp_done](../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)を呼び出して、操作が完了したことを指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-106">Repeat the process of filling the variables and calling **bcp_sendrow** until all the rows have been sent to the server, then call [bcp_done](../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) to specify that the operation is complete.</span></span>  
  
 <span data-ttu-id="5960d-107">**Bcp_bind**_pData_パラメーターには、列にバインドされている変数のアドレスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="5960d-107">The **bcp_bind**_pData_ parameter contains the address of the variable being bound to the column.</span></span> <span data-ttu-id="5960d-108">各列のデータは、次の 2 つの方法のいずれかを使用して格納できます。</span><span class="sxs-lookup"><span data-stu-id="5960d-108">The data for each column can be stored in one of two ways:</span></span>  
  
-   <span data-ttu-id="5960d-109">データを保持する変数を 1 つ割り当てる</span><span class="sxs-lookup"><span data-stu-id="5960d-109">Allocate one variable to hold the data.</span></span>  
  
-   <span data-ttu-id="5960d-110">データ変数の直前にインジケーター変数を割り当てる</span><span class="sxs-lookup"><span data-stu-id="5960d-110">Allocate an indicator variable followed immediately by the data variable.</span></span>  
  
 <span data-ttu-id="5960d-111">インジケーター変数は、可変長列のデータの長さを示します。列で NULL 値を許容している場合は NULL 値も示します。</span><span class="sxs-lookup"><span data-stu-id="5960d-111">The indicator variable indicates the length of the data for variable-length columns, and also indicates NULL values if the column allows NULLs.</span></span> <span data-ttu-id="5960d-112">データ変数のみが使用されている場合は、この変数のアドレスが**bcp_bind**_pData_パラメーターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5960d-112">If only a data variable is used, then the address of this variable is stored in the **bcp_bind**_pData_ parameter.</span></span> <span data-ttu-id="5960d-113">インジケーター変数が使用されている場合は、インジケーター変数のアドレスが**bcp_bind**_pData_パラメーターに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5960d-113">If an indicator variable is used, the address of the indicator variable is stored in the **bcp_bind**_pData_ parameter.</span></span> <span data-ttu-id="5960d-114">一括コピー関数は、 **bcp_bind**_Cbindicator_パラメーターと*pData*パラメーターを追加することで、データ変数の場所を計算します。</span><span class="sxs-lookup"><span data-stu-id="5960d-114">The bulk copy functions calculate the location of the data variable by adding the **bcp_bind**_cbIndicator_ and *pData* parameters.</span></span>  
  
 <span data-ttu-id="5960d-115">**bcp_bind**は、可変長データを処理する3つの方法をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="5960d-115">**bcp_bind** supports three methods for dealing with variable-length data:</span></span>  
  
-   <span data-ttu-id="5960d-116">データ変数のみを含む*Cbdata*を使用します。</span><span class="sxs-lookup"><span data-stu-id="5960d-116">Use *cbData* with only a data variable.</span></span> <span data-ttu-id="5960d-117">データの長さを*cbdata*に配置します。</span><span class="sxs-lookup"><span data-stu-id="5960d-117">Place the length of the data in *cbData*.</span></span> <span data-ttu-id="5960d-118">一括コピーされるデータの長さが変わるたびに、 [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)を呼び出して*cbdata*をリセットします。</span><span class="sxs-lookup"><span data-stu-id="5960d-118">Each time the length of the data to be bulk copied changes, call [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)to reset *cbData*.</span></span> <span data-ttu-id="5960d-119">他の2つの方法のいずれかを使用している場合は、 *Cbdata*の SQL_VARLEN_DATA を指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-119">If one of the other two methods is being used, specify SQL_VARLEN_DATA for *cbData*.</span></span> <span data-ttu-id="5960d-120">列に指定されているすべてのデータ値が NULL の場合は、 *Cbdata*の SQL_NULL_DATA を指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-120">If all the data values being supplied for a column are NULL, specify SQL_NULL_DATA for *cbData*.</span></span>  
  
-   <span data-ttu-id="5960d-121">インジケーター変数を使用します。</span><span class="sxs-lookup"><span data-stu-id="5960d-121">Use indicator variables.</span></span> <span data-ttu-id="5960d-122">新しい各データ値をデータ変数に移動するときに、その値の長さをインジケーター変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="5960d-122">As each new data value is moved into the data variable, store the length of the value in the indicator variable.</span></span> <span data-ttu-id="5960d-123">他の2つのメソッドのいずれかを使用している場合は、 *Cbindicator*に0を指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-123">If one of the other two methods is being used, specify 0 for *cbIndicator*.</span></span>  
  
-   <span data-ttu-id="5960d-124">ターミネータ ポインターを使用します。</span><span class="sxs-lookup"><span data-stu-id="5960d-124">Use terminator pointers.</span></span> <span data-ttu-id="5960d-125">データを終了するビットパターンのアドレスを使用して**bcp_bind**_pterm_パラメーターを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5960d-125">Load the **bcp_bind**_pTerm_ parameter with the address of the bit pattern that terminates the data.</span></span> <span data-ttu-id="5960d-126">他の2つのメソッドのいずれかを使用している場合は、 *Pterm*に NULL を指定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-126">If one of the other two methods is being used, specify NULL for *pTerm*.</span></span>  
  
 <span data-ttu-id="5960d-127">これら3つのメソッドはすべて同じ**bcp_bind**呼び出しで使用できます。その場合、コピーされるデータ量が最小になる仕様が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5960d-127">All three of these methods can be used on the same **bcp_bind** call, in which case the specification that results in the smallest amount of data being copied is used.</span></span>  
  
 <span data-ttu-id="5960d-128">**Bcp_bind**_type_パラメーターは、ODBC データ型識別子ではなく、db-library データ型識別子を使用します。</span><span class="sxs-lookup"><span data-stu-id="5960d-128">The **bcp_bind**_type_ parameter uses DB-Library data type identifiers, not ODBC data type identifiers.</span></span> <span data-ttu-id="5960d-129">DB-LIBRARY のデータ型識別子は、ODBC **bcp_bind**関数で使用するために sqlncli で定義されています。</span><span class="sxs-lookup"><span data-stu-id="5960d-129">DB-Library data type identifiers are defined in sqlncli.h for use with the ODBC **bcp_bind** function.</span></span>  
  
 <span data-ttu-id="5960d-130">一括コピー関数では、すべての ODBC C データ型をサポートしているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="5960d-130">Bulk copy functions do not support all ODBC C data types.</span></span> <span data-ttu-id="5960d-131">たとえば、一括コピー関数では ODBC SQL_C_TYPE_TIMESTAMP 構造がサポートされていないため、 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)または[SQLGetData](../native-client-odbc-api/sqlgetdata.md)を使用して odbc SQL_TYPE_TIMESTAMP データを SQL_C_CHAR 変数に変換します。</span><span class="sxs-lookup"><span data-stu-id="5960d-131">For example, the bulk copy functions do not support the ODBC SQL_C_TYPE_TIMESTAMP structure, so use [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) or [SQLGetData](../native-client-odbc-api/sqlgetdata.md) to convert ODBC SQL_TYPE_TIMESTAMP data to a SQL_C_CHAR variable.</span></span> <span data-ttu-id="5960d-132">その後**bcp_bind**を sqlcharacter の*型*パラメーターと共に使用して、変数を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime**列にバインドすると、一括コピー関数は、文字変数内の timestamp エスケープ句を適切な datetime 形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="5960d-132">If you then use **bcp_bind** with a *type* parameter of SQLCHARACTER to bind the variable to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **datetime** column, the bulk copy functions convert the timestamp escape clause in the character variable to the proper datetime format.</span></span>  
  
 <span data-ttu-id="5960d-133">次の表に、ODBC SQL データ型から [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型へのマッピングを行う際に使用が推奨されるデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="5960d-133">The following table lists the recommended data types to use in mapping from an ODBC SQL data type to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type.</span></span>  
  
|<span data-ttu-id="5960d-134">ODBC SQL データ型</span><span class="sxs-lookup"><span data-stu-id="5960d-134">ODBC SQLdata type</span></span>|<span data-ttu-id="5960d-135">ODBC C データ型</span><span class="sxs-lookup"><span data-stu-id="5960d-135">ODBC C data type</span></span>|<span data-ttu-id="5960d-136">bcp_bind*型*パラメーター</span><span class="sxs-lookup"><span data-stu-id="5960d-136">bcp_bind *type* parameter</span></span>|<span data-ttu-id="5960d-137">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="5960d-137">SQL Server data type</span></span>|  
|-----------------------|----------------------|--------------------------------|--------------------------|  
|<span data-ttu-id="5960d-138">SQL_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-138">SQL_CHAR</span></span>|<span data-ttu-id="5960d-139">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-139">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-140">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-140">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-141">**記号**</span><span class="sxs-lookup"><span data-stu-id="5960d-141">**character**</span></span><br /><br /> <span data-ttu-id="5960d-142">**char**</span><span class="sxs-lookup"><span data-stu-id="5960d-142">**char**</span></span>|  
|<span data-ttu-id="5960d-143">SQL_VARCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-143">SQL_VARCHAR</span></span>|<span data-ttu-id="5960d-144">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-144">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-145">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-145">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-146">**varchar**</span><span class="sxs-lookup"><span data-stu-id="5960d-146">**varchar**</span></span><br /><br /> <span data-ttu-id="5960d-147">**文字の変化**</span><span class="sxs-lookup"><span data-stu-id="5960d-147">**character varying**</span></span><br /><br /> <span data-ttu-id="5960d-148">**char varying**</span><span class="sxs-lookup"><span data-stu-id="5960d-148">**char varying**</span></span><br /><br /> <span data-ttu-id="5960d-149">**sysname**</span><span class="sxs-lookup"><span data-stu-id="5960d-149">**sysname**</span></span>|  
|<span data-ttu-id="5960d-150">SQL_LONGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-150">SQL_LONGVARCHAR</span></span>|<span data-ttu-id="5960d-151">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-151">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-152">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-152">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-153">**text**</span><span class="sxs-lookup"><span data-stu-id="5960d-153">**text**</span></span>|  
|<span data-ttu-id="5960d-154">SQL_WCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-154">SQL_WCHAR</span></span>|<span data-ttu-id="5960d-155">SQL_C_WCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-155">SQL_C_WCHAR</span></span>|<span data-ttu-id="5960d-156">SQLNCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-156">SQLNCHAR</span></span>|<span data-ttu-id="5960d-157">**nchar**</span><span class="sxs-lookup"><span data-stu-id="5960d-157">**nchar**</span></span>|  
|<span data-ttu-id="5960d-158">SQL_WVARCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-158">SQL_WVARCHAR</span></span>|<span data-ttu-id="5960d-159">SQL_C_WCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-159">SQL_C_WCHAR</span></span>|<span data-ttu-id="5960d-160">SQLNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-160">SQLNVARCHAR</span></span>|<span data-ttu-id="5960d-161">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="5960d-161">**nvarchar**</span></span>|  
|<span data-ttu-id="5960d-162">SQL_WLONGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-162">SQL_WLONGVARCHAR</span></span>|<span data-ttu-id="5960d-163">SQL_C_WCHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-163">SQL_C_WCHAR</span></span>|<span data-ttu-id="5960d-164">SQLNTEXT</span><span class="sxs-lookup"><span data-stu-id="5960d-164">SQLNTEXT</span></span>|<span data-ttu-id="5960d-165">**ntext**</span><span class="sxs-lookup"><span data-stu-id="5960d-165">**ntext**</span></span>|  
|<span data-ttu-id="5960d-166">SQL_DECIMAL</span><span class="sxs-lookup"><span data-stu-id="5960d-166">SQL_DECIMAL</span></span>|<span data-ttu-id="5960d-167">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-167">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-168">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-168">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-169">**decimal**</span><span class="sxs-lookup"><span data-stu-id="5960d-169">**decimal**</span></span><br /><br /> <span data-ttu-id="5960d-170">**alpha**</span><span class="sxs-lookup"><span data-stu-id="5960d-170">**dec**</span></span><br /><br /> <span data-ttu-id="5960d-171">**money**</span><span class="sxs-lookup"><span data-stu-id="5960d-171">**money**</span></span><br /><br /> <span data-ttu-id="5960d-172">**smallmoney**</span><span class="sxs-lookup"><span data-stu-id="5960d-172">**smallmoney**</span></span>|  
|<span data-ttu-id="5960d-173">SQL_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="5960d-173">SQL_NUMERIC</span></span>|<span data-ttu-id="5960d-174">SQL_C_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="5960d-174">SQL_C_NUMERIC</span></span>|<span data-ttu-id="5960d-175">SQLNUMERICN</span><span class="sxs-lookup"><span data-stu-id="5960d-175">SQLNUMERICN</span></span>|<span data-ttu-id="5960d-176">**numeric**</span><span class="sxs-lookup"><span data-stu-id="5960d-176">**numeric**</span></span>|  
|<span data-ttu-id="5960d-177">SQL_BIT</span><span class="sxs-lookup"><span data-stu-id="5960d-177">SQL_BIT</span></span>|<span data-ttu-id="5960d-178">SQL_C_BIT</span><span class="sxs-lookup"><span data-stu-id="5960d-178">SQL_C_BIT</span></span>|<span data-ttu-id="5960d-179">SQLBIT</span><span class="sxs-lookup"><span data-stu-id="5960d-179">SQLBIT</span></span>|<span data-ttu-id="5960d-180">**bit**</span><span class="sxs-lookup"><span data-stu-id="5960d-180">**bit**</span></span>|  
|<span data-ttu-id="5960d-181">SQL_TINYINT (符号付き)</span><span class="sxs-lookup"><span data-stu-id="5960d-181">SQL_TINYINT (signed)</span></span>|<span data-ttu-id="5960d-182">SQL_C_SSHORT</span><span class="sxs-lookup"><span data-stu-id="5960d-182">SQL_C_SSHORT</span></span>|<span data-ttu-id="5960d-183">SQLINT2</span><span class="sxs-lookup"><span data-stu-id="5960d-183">SQLINT2</span></span>|<span data-ttu-id="5960d-184">**smallint**</span><span class="sxs-lookup"><span data-stu-id="5960d-184">**smallint**</span></span>|  
|<span data-ttu-id="5960d-185">SQL_TINYINT (符号なし)</span><span class="sxs-lookup"><span data-stu-id="5960d-185">SQL_TINYINT (unsigned)</span></span>|<span data-ttu-id="5960d-186">SQL_C_UTINYINT</span><span class="sxs-lookup"><span data-stu-id="5960d-186">SQL_C_UTINYINT</span></span>|<span data-ttu-id="5960d-187">SQLINT1</span><span class="sxs-lookup"><span data-stu-id="5960d-187">SQLINT1</span></span>|<span data-ttu-id="5960d-188">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="5960d-188">**tinyint**</span></span>|  
|<span data-ttu-id="5960d-189">SQL_SMALL_INT (符号付き)</span><span class="sxs-lookup"><span data-stu-id="5960d-189">SQL_SMALL_INT (signed)</span></span>|<span data-ttu-id="5960d-190">SQL_C_SSHORT</span><span class="sxs-lookup"><span data-stu-id="5960d-190">SQL_C_SSHORT</span></span>|<span data-ttu-id="5960d-191">SQLINT2</span><span class="sxs-lookup"><span data-stu-id="5960d-191">SQLINT2</span></span>|<span data-ttu-id="5960d-192">**smallint**</span><span class="sxs-lookup"><span data-stu-id="5960d-192">**smallint**</span></span>|  
|<span data-ttu-id="5960d-193">SQL_SMALL_INT (符号なし)</span><span class="sxs-lookup"><span data-stu-id="5960d-193">SQL_SMALL_INT (unsigned)</span></span>|<span data-ttu-id="5960d-194">SQL_C_SLONG</span><span class="sxs-lookup"><span data-stu-id="5960d-194">SQL_C_SLONG</span></span>|<span data-ttu-id="5960d-195">SQLINT4</span><span class="sxs-lookup"><span data-stu-id="5960d-195">SQLINT4</span></span>|<span data-ttu-id="5960d-196">**int**</span><span class="sxs-lookup"><span data-stu-id="5960d-196">**int**</span></span><br /><br /> <span data-ttu-id="5960d-197">**integer**</span><span class="sxs-lookup"><span data-stu-id="5960d-197">**integer**</span></span>|  
|<span data-ttu-id="5960d-198">SQL_INTEGER (符号付き)</span><span class="sxs-lookup"><span data-stu-id="5960d-198">SQL_INTEGER (signed)</span></span>|<span data-ttu-id="5960d-199">SQL_C_SLONG</span><span class="sxs-lookup"><span data-stu-id="5960d-199">SQL_C_SLONG</span></span>|<span data-ttu-id="5960d-200">SQLINT4</span><span class="sxs-lookup"><span data-stu-id="5960d-200">SQLINT4</span></span>|<span data-ttu-id="5960d-201">**int**</span><span class="sxs-lookup"><span data-stu-id="5960d-201">**int**</span></span><br /><br /> <span data-ttu-id="5960d-202">**integer**</span><span class="sxs-lookup"><span data-stu-id="5960d-202">**integer**</span></span>|  
|<span data-ttu-id="5960d-203">SQL_INTEGER (符号なし)</span><span class="sxs-lookup"><span data-stu-id="5960d-203">SQL_INTEGER (unsigned)</span></span>|<span data-ttu-id="5960d-204">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-204">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-205">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-205">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-206">**decimal**</span><span class="sxs-lookup"><span data-stu-id="5960d-206">**decimal**</span></span><br /><br /> <span data-ttu-id="5960d-207">**alpha**</span><span class="sxs-lookup"><span data-stu-id="5960d-207">**dec**</span></span>|  
|<span data-ttu-id="5960d-208">SQL_BIGINT (符号付きと符号なし)</span><span class="sxs-lookup"><span data-stu-id="5960d-208">SQL_BIGINT (signed and unsigned)</span></span>|<span data-ttu-id="5960d-209">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-209">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-210">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-210">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-211">**bigint**</span><span class="sxs-lookup"><span data-stu-id="5960d-211">**bigint**</span></span>|  
|<span data-ttu-id="5960d-212">SQL_REAL</span><span class="sxs-lookup"><span data-stu-id="5960d-212">SQL_REAL</span></span>|<span data-ttu-id="5960d-213">SQL_C_FLOAT</span><span class="sxs-lookup"><span data-stu-id="5960d-213">SQL_C_FLOAT</span></span>|<span data-ttu-id="5960d-214">SQLFLT4</span><span class="sxs-lookup"><span data-stu-id="5960d-214">SQLFLT4</span></span>|<span data-ttu-id="5960d-215">**real**</span><span class="sxs-lookup"><span data-stu-id="5960d-215">**real**</span></span>|  
|<span data-ttu-id="5960d-216">SQL_FLOAT</span><span class="sxs-lookup"><span data-stu-id="5960d-216">SQL_FLOAT</span></span>|<span data-ttu-id="5960d-217">SQL_C_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="5960d-217">SQL_C_DOUBLE</span></span>|<span data-ttu-id="5960d-218">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="5960d-218">SQLFLT8</span></span>|<span data-ttu-id="5960d-219">**float**</span><span class="sxs-lookup"><span data-stu-id="5960d-219">**float**</span></span>|  
|<span data-ttu-id="5960d-220">SQL_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="5960d-220">SQL_DOUBLE</span></span>|<span data-ttu-id="5960d-221">SQL_C_DOUBLE</span><span class="sxs-lookup"><span data-stu-id="5960d-221">SQL_C_DOUBLE</span></span>|<span data-ttu-id="5960d-222">SQLFLT8</span><span class="sxs-lookup"><span data-stu-id="5960d-222">SQLFLT8</span></span>|<span data-ttu-id="5960d-223">**float**</span><span class="sxs-lookup"><span data-stu-id="5960d-223">**float**</span></span>|  
|<span data-ttu-id="5960d-224">SQL_BINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-224">SQL_BINARY</span></span>|<span data-ttu-id="5960d-225">SQL_C_BINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-225">SQL_C_BINARY</span></span>|<span data-ttu-id="5960d-226">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-226">SQLBINARY</span></span>|<span data-ttu-id="5960d-227">**[バイナリ]**</span><span class="sxs-lookup"><span data-stu-id="5960d-227">**binary**</span></span><br /><br /> <span data-ttu-id="5960d-228">**timestamp**</span><span class="sxs-lookup"><span data-stu-id="5960d-228">**timestamp**</span></span>|  
|<span data-ttu-id="5960d-229">SQL_VARBINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-229">SQL_VARBINARY</span></span>|<span data-ttu-id="5960d-230">SQL_C_BINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-230">SQL_C_BINARY</span></span>|<span data-ttu-id="5960d-231">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-231">SQLBINARY</span></span>|<span data-ttu-id="5960d-232">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="5960d-232">**varbinary**</span></span><br /><br /> <span data-ttu-id="5960d-233">**バイナリの変化**</span><span class="sxs-lookup"><span data-stu-id="5960d-233">**binary varying**</span></span>|  
|<span data-ttu-id="5960d-234">SQL_LONGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-234">SQL_LONGVARBINARY</span></span>|<span data-ttu-id="5960d-235">SQL_C_BINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-235">SQL_C_BINARY</span></span>|<span data-ttu-id="5960d-236">SQLBINARY</span><span class="sxs-lookup"><span data-stu-id="5960d-236">SQLBINARY</span></span>|<span data-ttu-id="5960d-237">**image**</span><span class="sxs-lookup"><span data-stu-id="5960d-237">**image**</span></span>|  
|<span data-ttu-id="5960d-238">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="5960d-238">SQL_TYPE_DATE</span></span>|<span data-ttu-id="5960d-239">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-239">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-240">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-240">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-241">**datetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-241">**datetime**</span></span><br /><br /> <span data-ttu-id="5960d-242">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-242">**smalldatetime**</span></span>|  
|<span data-ttu-id="5960d-243">SQL_TYPE_TIME</span><span class="sxs-lookup"><span data-stu-id="5960d-243">SQL_TYPE_TIME</span></span>|<span data-ttu-id="5960d-244">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-244">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-245">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-245">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-246">**datetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-246">**datetime**</span></span><br /><br /> <span data-ttu-id="5960d-247">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-247">**smalldatetime**</span></span>|  
|<span data-ttu-id="5960d-248">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="5960d-248">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="5960d-249">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-249">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-250">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-250">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-251">**datetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-251">**datetime**</span></span><br /><br /> <span data-ttu-id="5960d-252">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="5960d-252">**smalldatetime**</span></span>|  
|<span data-ttu-id="5960d-253">SQL_GUID</span><span class="sxs-lookup"><span data-stu-id="5960d-253">SQL_GUID</span></span>|<span data-ttu-id="5960d-254">SQL_C_GUID</span><span class="sxs-lookup"><span data-stu-id="5960d-254">SQL_C_GUID</span></span>|<span data-ttu-id="5960d-255">SQLUNIQUEID</span><span class="sxs-lookup"><span data-stu-id="5960d-255">SQLUNIQUEID</span></span>|<span data-ttu-id="5960d-256">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="5960d-256">**uniqueidentifier**</span></span>|  
|<span data-ttu-id="5960d-257">SQL_INTERVAL_</span><span class="sxs-lookup"><span data-stu-id="5960d-257">SQL_INTERVAL_</span></span>|<span data-ttu-id="5960d-258">SQL_C_CHAR</span><span class="sxs-lookup"><span data-stu-id="5960d-258">SQL_C_CHAR</span></span>|<span data-ttu-id="5960d-259">SQLCHARACTER</span><span class="sxs-lookup"><span data-stu-id="5960d-259">SQLCHARACTER</span></span>|<span data-ttu-id="5960d-260">**char**</span><span class="sxs-lookup"><span data-stu-id="5960d-260">**char**</span></span>|  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="5960d-261">に、符号付きの**tinyint**、unsigned **smallint**、または unsigned **int**データ型がありません。</span><span class="sxs-lookup"><span data-stu-id="5960d-261">does not have signed **tinyint**, unsigned **smallint**, or unsigned **int** data types.</span></span> <span data-ttu-id="5960d-262">これらのデータ型を変換するときにデータ値が失われないようにするには、2 番目に大きい整数データ型を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] テーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="5960d-262">To prevent the loss of data values when migrating these data types, create the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table with the next largest integer data type.</span></span> <span data-ttu-id="5960d-263">ユーザーが元のデータ型で許容されている範囲外の値を後から追加しないようにするには、次のようにルールを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 列に適用し、ソースのデータ型でサポートされる範囲内に許容値を限定します。</span><span class="sxs-lookup"><span data-stu-id="5960d-263">To prevent users from later adding values outside the range allowed by the original data type, apply a rule to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] column to restrict the allowable values to the range supported by the data type in the original source:</span></span>  
  
```  
CREATE TABLE Sample_Ints(STinyIntCol   SMALLINT,  
USmallIntCol INT)  
GO  
CREATE RULE STinyInt_Rule  
AS   
@range >= -128 AND @range <= 127  
GO  
CREATE RULE USmallInt_Rule  
AS   
@range >= 0 AND @range <= 65535  
GO  
sp_bindrule STinyInt_Rule, 'Sample_Ints.STinyIntCol'  
GO  
sp_bindrule USmallInt_Rule, 'Sample_Ints.USmallIntCol'  
GO  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="5960d-264">では、interval データ型を直接サポートしません。</span><span class="sxs-lookup"><span data-stu-id="5960d-264">does not support interval data types directly.</span></span> <span data-ttu-id="5960d-265">ただしアプリケーションでは、interval 型のエスケープ シーケンスを文字列として [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 文字型列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="5960d-265">An application can, however, store interval escape sequences as character strings in a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] character column.</span></span> <span data-ttu-id="5960d-266">アプリケーションでは、後で使用するためにこれらのエスケープ シーケンスを読み取ることができますが、 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント内では使用できません。</span><span class="sxs-lookup"><span data-stu-id="5960d-266">The application can read them for later use, but they cannot be used in [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
 <span data-ttu-id="5960d-267">一括コピー関数を使用すると、ODBC データ ソースから読み取ったデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にすばやく読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="5960d-267">The bulk copy functions can be used to quickly load data into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that has been read from an ODBC data source.</span></span> <span data-ttu-id="5960d-268">[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)を使用して結果セットの列をプログラム変数にバインドした後、 **bcp_bind**を使用して、同じプログラム変数を一括コピー操作にバインドします。</span><span class="sxs-lookup"><span data-stu-id="5960d-268">Use [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) to bind the columns of a result set to program variables, then use **bcp_bind** to bind the same program variables to a bulk copy operation.</span></span> <span data-ttu-id="5960d-269">[Sqlfetchscroll](../native-client-odbc-api/sqlfetchscroll.md)または**sqlfetch**を呼び出すと、ODBC データソースからプログラム変数にデータの行がフェッチされ、 [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)を呼び出すと、プログラム変数からにデータが一括コピーされ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="5960d-269">Calling [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) or **SQLFetch** then fetches a row of data from the ODBC data source into the program variables, and calling [bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) bulk copies the data from the program variables to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .</span></span>  
  
 <span data-ttu-id="5960d-270">アプリケーションでは、 **bcp_bind** _pData_パラメーターに指定されたデータ変数のアドレスを変更する必要があるときに、いつでも[bcp_colptr](../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5960d-270">An application can use the [bcp_colptr](../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) function anytime it needs to change the address of the data variable originally specified in the **bcp_bind** _pData_ parameter.</span></span> <span data-ttu-id="5960d-271">アプリケーションでは、 **bcp_bind**_cbdata_パラメーターでもともと指定されていたデータ長を変更する必要がある場合、いつでも[bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)関数を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5960d-271">An application can use the [bcp_collen](../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md) function anytime it needs to change the data length originally specified in the **bcp_bind**_cbData_ parameter.</span></span>  
  
 <span data-ttu-id="5960d-272">"bcp_readrow" のような関数は用意されていないため、一括コピーを使用してデータを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からプログラム変数に読み取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="5960d-272">You cannot read data from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] into program variables using bulk copy; there is nothing like a "bcp_readrow" function.</span></span> <span data-ttu-id="5960d-273">実行できるのは、アプリケーションからサーバーへのデータの送信だけです。</span><span class="sxs-lookup"><span data-stu-id="5960d-273">You can only send data from the application to the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5960d-274">参照</span><span class="sxs-lookup"><span data-stu-id="5960d-274">See Also</span></span>  
 [<span data-ttu-id="5960d-275">ODBC&#41;&#40;の一括コピー操作の実行</span><span class="sxs-lookup"><span data-stu-id="5960d-275">Performing Bulk Copy Operations &#40;ODBC&#41;</span></span>](performing-bulk-copy-operations-odbc.md)  
  
  