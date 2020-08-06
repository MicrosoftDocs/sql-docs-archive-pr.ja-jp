---
title: カーソル | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- results [SQL Server], cursors
- Transact-SQL cursors, about cursors
- cursors [SQL Server]
- data access [SQL Server], cursors
- result sets [SQL Server], cursors
- requesting cursors
- cursors [SQL Server], about cursors
ms.assetid: e668b40c-bd4d-4415-850d-20fc4872ee72
author: rothja
ms.author: jroth
ms.openlocfilehash: 055482a8cf64527f58ed983b449121a99960f566
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645646"
---
# <a name="cursors"></a><span data-ttu-id="26cf0-102">カーソル</span><span class="sxs-lookup"><span data-stu-id="26cf0-102">Cursors</span></span>
  <span data-ttu-id="26cf0-103">リレーショナル データベースで操作を実行する場合、行の完全なセットが操作の対象になります。</span><span class="sxs-lookup"><span data-stu-id="26cf0-103">Operations in a relational database act on a complete set of rows.</span></span> <span data-ttu-id="26cf0-104">たとえば、SELECT ステートメントでは、WHERE 句で指定した条件を満たすすべての行のセットが返されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-104">For example, the set of rows returned by a SELECT statement consists of all the rows that satisfy the conditions in the WHERE clause of the statement.</span></span> <span data-ttu-id="26cf0-105">このステートメントが返す行の完全なセットを結果セットと呼びます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-105">This complete set of rows returned by the statement is known as the result set.</span></span> <span data-ttu-id="26cf0-106">アプリケーション、特に対話型のオンライン アプリケーションでは、必ずしも、結果セット全体をひとまとめに使用して作業することが効率的であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-106">Applications, especially interactive online applications, cannot always work effectively with the entire result set as a unit.</span></span> <span data-ttu-id="26cf0-107">そのため、このようなアプリケーションでは、一度に 1 行または少数の行のブロックを使用するためのメカニズムが必要になります。</span><span class="sxs-lookup"><span data-stu-id="26cf0-107">These applications need a mechanism to work with one row or a small block of rows at a time.</span></span> <span data-ttu-id="26cf0-108">カーソルはそのメカニズムを提供する結果セットの拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="26cf0-108">Cursors are an extension to result sets that provide that mechanism.</span></span>  
  
 <span data-ttu-id="26cf0-109">カーソルでは、次のように結果の処理が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-109">Cursors extend result processing by:</span></span>  
  
-   <span data-ttu-id="26cf0-110">結果セット内の特定の行に位置付けることができます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-110">Allowing positioning at specific rows of the result set.</span></span>  
  
-   <span data-ttu-id="26cf0-111">結果セット内の現在位置から 1 行または 1 ブロックの行を取得します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-111">Retrieving one row or block of rows from the current position in the result set.</span></span>  
  
-   <span data-ttu-id="26cf0-112">結果セット内の現在位置の行データを修正できます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-112">Supporting data modifications to the rows at the current position in the result set.</span></span>  
  
-   <span data-ttu-id="26cf0-113">結果セット内のデータベース データに対して他のユーザーが行った変更をさまざまなレベルで表示できます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-113">Supporting different levels of visibility to changes made by other users to the database data that is presented in the result set.</span></span>  
  
-   <span data-ttu-id="26cf0-114">スクリプト、ストアド プロシージャ、およびトリガー内の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントから、結果セット内のデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-114">Providing [!INCLUDE[tsql](../includes/tsql-md.md)] statements in scripts, stored procedures, and triggers access to the data in a result set.</span></span>  
  
## <a name="concepts"></a><span data-ttu-id="26cf0-115">概念</span><span class="sxs-lookup"><span data-stu-id="26cf0-115">Concepts</span></span>  
 <span data-ttu-id="26cf0-116">カーソルの実装</span><span class="sxs-lookup"><span data-stu-id="26cf0-116">Cursor Implementations</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="26cf0-117">では、3 つのカーソルの実装がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="26cf0-117">supports three cursor implementations.</span></span>  
  
 <span data-ttu-id="26cf0-118">Transact-SQL カーソル</span><span class="sxs-lookup"><span data-stu-id="26cf0-118">Transact-SQL cursors</span></span>  
 <span data-ttu-id="26cf0-119">DECLARE CURSOR 構文に基づいていて、主に [!INCLUDE[tsql](../includes/tsql-md.md)] スクリプト、ストアド プロシージャ、およびトリガーで使用されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-119">Are based on the DECLARE CURSOR syntax and are used mainly in [!INCLUDE[tsql](../includes/tsql-md.md)] scripts, stored procedures, and triggers.</span></span> [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="26cf0-120">カーソルはサーバー上で実装され、クライアントからサーバーに送信される [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントによって管理されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-120">cursors are implemented on the server and are managed by [!INCLUDE[tsql](../includes/tsql-md.md)] statements sent from the client to the server.</span></span> <span data-ttu-id="26cf0-121">また、バッチ、ストアド プロシージャ、またはトリガーにも含まれている場合があります。</span><span class="sxs-lookup"><span data-stu-id="26cf0-121">They may also be contained in batches, stored procedures, or triggers.</span></span>  
  
 <span data-ttu-id="26cf0-122">アプリケーション プログラミング インターフェイス (API) サーバー カーソル</span><span class="sxs-lookup"><span data-stu-id="26cf0-122">Application programming interface (API) server cursors</span></span>  
 <span data-ttu-id="26cf0-123">OLE DB および ODBC の API カーソル関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="26cf0-123">Support the API cursor functions in OLE DB and ODBC.</span></span> <span data-ttu-id="26cf0-124">API サーバー カーソルはサーバー上に実装されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-124">API server cursors are implemented on the server.</span></span> <span data-ttu-id="26cf0-125">クライアント アプリケーションから API カーソル関数が呼び出されるたびに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client の OLE DB プロバイダーまたは ODBC ドライバーによって、API サーバー カーソルに対するアクションの要求がサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-125">Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client OLE DB provider or ODBC driver transmits the request to the server for action against the API server cursor.</span></span>  
  
 <span data-ttu-id="26cf0-126">クライアント カーソル</span><span class="sxs-lookup"><span data-stu-id="26cf0-126">Client cursors</span></span>  
 <span data-ttu-id="26cf0-127">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーおよび ADO API を実装する DLL によって、内部的に実装されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-127">Are implemented internally by the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC driver and by the DLL that implements the ADO API.</span></span> <span data-ttu-id="26cf0-128">クライアント カーソルは、結果セットのすべての行をクライアント上でキャッシュすることによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-128">Client cursors are implemented by caching all the result set rows on the client.</span></span> <span data-ttu-id="26cf0-129">クライアント アプリケーションによって API カーソル関数が呼び出されるたびに、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client の ODBC ドライバーまたは ADO DLL によって、クライアント上にキャッシュされた結果セットの行に対してカーソル操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-129">Each time a client application calls an API cursor function, the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client ODBC driver or the ADO DLL performs the cursor operation on the result set rows cached on the client.</span></span>  
  
 <span data-ttu-id="26cf0-130">カーソルの種類</span><span class="sxs-lookup"><span data-stu-id="26cf0-130">Type of Cursors</span></span>  
 <span data-ttu-id="26cf0-131">順方向専用</span><span class="sxs-lookup"><span data-stu-id="26cf0-131">Forward-only</span></span>  
 <span data-ttu-id="26cf0-132">順方向専用カーソルは、スクロールをサポートしていません。カーソル内の最初から最後まで順次に行をフェッチする機能だけをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="26cf0-132">A forward-only cursor does not support scrolling; it supports only fetching the rows serially from the start to the end of the cursor.</span></span> <span data-ttu-id="26cf0-133">行はフェッチされるまで、データベースから取得されません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-133">The rows are not retrieved from the database until they are fetched.</span></span> <span data-ttu-id="26cf0-134">現在のユーザーが作成または別のユーザーがコミットした INSERT、UPDATE、および DELETE ステートメントが、結果セット内の行に与えた影響は、カーソルから行をフェッチした際に確認できます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-134">The effects of all INSERT, UPDATE, and DELETE statements made by the current user or committed by other users that affect rows in the result set are visible as the rows are fetched from the cursor.</span></span>  
  
 <span data-ttu-id="26cf0-135">カーソルは後方にスクロールできないので、データベース内の行のフェッチ後にその行に対して行われた変更内容の大部分は、カーソル内で確認できません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-135">Because the cursor cannot be scrolled backward, most changes made to rows in the database after the row was fetched are not visible through the cursor.</span></span> <span data-ttu-id="26cf0-136">クラスター化インデックスに含まれる列の更新など、結果セット内の行の位置の判定に使用する値が変更されるような場合は、変更された値がカーソル内で表示されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-136">In cases where a value used to determine the location of the row within the result set is modified, such as updating a column covered by a clustered index, the modified value is visible through the cursor.</span></span>  
  
 <span data-ttu-id="26cf0-137">データベース API カーソル モデルでは、順方向専用カーソルが特殊な種類のカーソルと見なされますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では違います。</span><span class="sxs-lookup"><span data-stu-id="26cf0-137">Although the database API cursor models consider a forward-only cursor to be a distinct type of cursor, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not.</span></span> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="26cf0-138">では、順方向専用とスクロールの両方が静的カーソル、キーセット ドリブン カーソル、および動的カーソルに適用できるオプションと見なされます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-138">considers both forward-only and scroll as options that can be applied to static, keyset-driven, and dynamic cursors.</span></span> [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="26cf0-139">カーソルは、順方向専用の静的カーソル、キーセット ドリブン カーソル、および動的カーソルをサポートします。</span><span class="sxs-lookup"><span data-stu-id="26cf0-139">cursors support forward-only static, keyset-driven, and dynamic cursors.</span></span> <span data-ttu-id="26cf0-140">データベース API カーソル モデルでは、静的カーソル、キーセット ドリブン カーソル、および動的カーソルが常にスクロール可能であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="26cf0-140">The database API cursor models assume that static, keyset-driven, and dynamic cursors are always scrollable.</span></span> <span data-ttu-id="26cf0-141">データベース API カーソルの属性またはプロパティを順方向専用に設定すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] により、カーソルは順方向専用の動的カーソルとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-141">When a database API cursor attribute or property is set to forward-only, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] implements this as a forward-only dynamic cursor.</span></span>  
  
 <span data-ttu-id="26cf0-142">静的</span><span class="sxs-lookup"><span data-stu-id="26cf0-142">Static</span></span>  
 <span data-ttu-id="26cf0-143">静的カーソルを開くと、そのカーソルの完全な結果セットが **tempdb** に作成されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-143">The complete result set of a static cursor is built in **tempdb** when the cursor is opened.</span></span> <span data-ttu-id="26cf0-144">静的カーソルは常に、カーソルを開いた時点の結果セットの状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-144">A static cursor always displays the result set as it was when the cursor was opened.</span></span> <span data-ttu-id="26cf0-145">静的カーソルは変更をほとんど検出しませんが、スクロール中に消費するリソースは比較的少なくなります。</span><span class="sxs-lookup"><span data-stu-id="26cf0-145">Static cursors detect few or no changes, but consume relatively few resources while scrolling.</span></span>  
  
 <span data-ttu-id="26cf0-146">このカーソルは、結果セットのメンバーシップに影響を与えるデータベース内の変更や、結果セットを構成する行の列内の値に対する変更を反映しません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-146">The cursor does not reflect any changes made in the database that affect either the membership of the result set or changes to the values in the columns of the rows that make up the result set.</span></span> <span data-ttu-id="26cf0-147">静的カーソルを開いた後にデータベースに新しい行が挿入されると、カーソルの SELECT ステートメントの検索条件に一致していても、静的カーソルにそれらの行は表示されません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-147">A static cursor does not display new rows inserted in the database after the cursor was opened, even if they match the search conditions of the cursor SELECT statement.</span></span> <span data-ttu-id="26cf0-148">結果セットを構成する行が他のユーザーによって更新された場合、その新しいデータ値は静的カーソルに表示されません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-148">If rows making up the result set are updated by other users, the new data values are not displayed in the static cursor.</span></span> <span data-ttu-id="26cf0-149">静的カーソルを開いた後にデータベースから削除された行は、静的カーソルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-149">The static cursor displays rows deleted from the database after the cursor was opened.</span></span> <span data-ttu-id="26cf0-150">UPDATE、INSERT、または DELETE による操作は、静的カーソルを閉じてから再度開かない限り、静的カーソルに反映されません。これは、その静的カーソルを開いたのと同じ接続を使用して変更を行った場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="26cf0-150">No UPDATE, INSERT, or DELETE operations are reflected in a static cursor (unless the cursor is closed and reopened), not even modifications made using the same connection that opened the cursor.</span></span>  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="26cf0-151">の静的カーソルは常に読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="26cf0-151">static cursors are always read-only.</span></span>  
  
 <span data-ttu-id="26cf0-152">静的カーソルの結果セットは **tempdb**の作業テーブルに格納されるので、結果セット内の行のサイズを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テーブルの最大行サイズよりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-152">Because the result set of a static cursor is stored in a work table in **tempdb**, the size of the rows in the result set cannot exceed the maximum row size for a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] table.</span></span>  
  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="26cf0-153">では、静的カーソルは非反映型カーソルとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-153">uses the term insensitive for static cursors.</span></span> <span data-ttu-id="26cf0-154">一部のデータベース API ではスナップショット カーソルとも呼びます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-154">Some database APIs identify them as snapshot cursors.</span></span>  
  
 <span data-ttu-id="26cf0-155">Keyset</span><span class="sxs-lookup"><span data-stu-id="26cf0-155">Keyset</span></span>  
 <span data-ttu-id="26cf0-156">キーセット ドリブン カーソルの構成要素と行の順序は、カーソルを開いたときに固定されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-156">The membership and order of rows in a keyset-driven cursor are fixed when the cursor is opened.</span></span> <span data-ttu-id="26cf0-157">キーセット ドリブン カーソルは、キーセットという一意の識別子 (キー) のセットにより制御されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-157">Keyset-driven cursors are controlled by a set of unique identifiers, keys, known as the keyset.</span></span> <span data-ttu-id="26cf0-158">これらのキーは、結果セットの行を一意に識別する列のセットから構築されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-158">The keys are built from a set of columns that uniquely identify the rows in the result set.</span></span> <span data-ttu-id="26cf0-159">キーセットは、カーソルを開いた時点で SELECT ステートメントにより限定されたすべての行から取り出したキー値のセットです。</span><span class="sxs-lookup"><span data-stu-id="26cf0-159">The keyset is the set of the key values from all the rows that qualified for the SELECT statement at the time the cursor was opened.</span></span> <span data-ttu-id="26cf0-160">キーセット ドリブン カーソルのキーセットは、カーソルを開いたときに **tempdb** に構築されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-160">The keyset for a keyset-driven cursor is built in **tempdb** when the cursor is opened.</span></span>  
  
 <span data-ttu-id="26cf0-161">動的</span><span class="sxs-lookup"><span data-stu-id="26cf0-161">Dynamic</span></span>  
 <span data-ttu-id="26cf0-162">動的カーソルは静的カーソルと対照的です。</span><span class="sxs-lookup"><span data-stu-id="26cf0-162">Dynamic cursors are the opposite of static cursors.</span></span> <span data-ttu-id="26cf0-163">動的カーソルは、スクロールされるときに、結果セット内の行に対して行われたすべての変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-163">Dynamic cursors reflect all changes made to the rows in their result set when scrolling through the cursor.</span></span> <span data-ttu-id="26cf0-164">結果セット内の行のデータ値、順序、およびメンバーシップは、フェッチを実行するたびに変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="26cf0-164">The data values, order, and membership of the rows in the result set can change on each fetch.</span></span> <span data-ttu-id="26cf0-165">UPDATE、INSERT、および DELETE ステートメントをどのユーザーが実行しても、その実行結果はすべてカーソルに表示されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-165">All UPDATE, INSERT, and DELETE statements made by all users are visible through the cursor.</span></span> <span data-ttu-id="26cf0-166">更新が **SQLSetPos** などの API 関数または [!INCLUDE[tsql](../includes/tsql-md.md)] の WHERE CURRENT OF 句のいずれかを使用してカーソルによって行われた場合、それらの更新結果はすぐに表示されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-166">Updates are visible immediately if they are made through the cursor using either an API function such as **SQLSetPos** or the [!INCLUDE[tsql](../includes/tsql-md.md)] WHERE CURRENT OF clause.</span></span> <span data-ttu-id="26cf0-167">カーソルの外部から行った更新は、コミットされるまで表示されません。ただし、カーソルのトランザクション分離レベルが READ UNCOMMITTED に設定されている場合は、その限りではありません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-167">Updates made outside the cursor are not visible until they are committed, unless the cursor transaction isolation level is set to read uncommitted.</span></span> <span data-ttu-id="26cf0-168">動的カーソル プランが空間インデックスを使用することはありません。</span><span class="sxs-lookup"><span data-stu-id="26cf0-168">Dynamic cursor plans never use spatial indexes.</span></span>  
  
## <a name="requesting-a-cursor"></a><span data-ttu-id="26cf0-169">カーソルの要求</span><span class="sxs-lookup"><span data-stu-id="26cf0-169">Requesting a Cursor</span></span>  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="26cf0-170">では、カーソルの要求方法として、次の 2 つの方法がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-170">supports two methods for requesting a cursor:</span></span>  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)]  
  
     <span data-ttu-id="26cf0-171">[!INCLUDE[tsql](../includes/tsql-md.md)] 言語では、ISO カーソル構文以降にモデル化されたカーソルを使用するための構文がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-171">The [!INCLUDE[tsql](../includes/tsql-md.md)] language supports a syntax for using cursors modeled after the ISO cursor syntax.</span></span>  
  
-   <span data-ttu-id="26cf0-172">データベース API (アプリケーション プログラミング インターフェイス) のカーソル機能</span><span class="sxs-lookup"><span data-stu-id="26cf0-172">Database application programming interface (API) cursor functions</span></span>  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="26cf0-173">では、次のデータベース API のカーソル機能がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-173">supports the cursor functionality of these database APIs:</span></span>  
  
    -   <span data-ttu-id="26cf0-174">ADO ([!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX データ オブジェクト)</span><span class="sxs-lookup"><span data-stu-id="26cf0-174">ADO ([!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX Data Object)</span></span>  
  
    -   <span data-ttu-id="26cf0-175">OLE DB (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="26cf0-175">OLE DB</span></span>  
  
    -   <span data-ttu-id="26cf0-176">ODBC (Open Database Connectivity)</span><span class="sxs-lookup"><span data-stu-id="26cf0-176">ODBC (Open Database Connectivity)</span></span>  
  
 <span data-ttu-id="26cf0-177">アプリケーションでは、カーソルを要求するこれら 2 つの方法を混在して使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="26cf0-177">An application should never mix these two methods of requesting a cursor.</span></span> <span data-ttu-id="26cf0-178">また、API を使用してカーソル動作を指定するアプリケーションでは、 [!INCLUDE[tsql](../includes/tsql-md.md)] の DECLARE CURSOR ステートメントを実行して [!INCLUDE[tsql](../includes/tsql-md.md)] カーソルを要求しないでください。</span><span class="sxs-lookup"><span data-stu-id="26cf0-178">An application that has used the API to specify cursor behaviors should not then execute a [!INCLUDE[tsql](../includes/tsql-md.md)] DECLARE CURSOR statement to also request a [!INCLUDE[tsql](../includes/tsql-md.md)] cursor.</span></span> <span data-ttu-id="26cf0-179">アプリケーションで DECLARE CURSOR ステートメントを実行できるのは、API カーソル属性をすべて既定値に戻した場合だけです。</span><span class="sxs-lookup"><span data-stu-id="26cf0-179">An application should only execute DECLARE CURSOR if it has set all the API cursor attributes back to their defaults.</span></span>  
  
 <span data-ttu-id="26cf0-180">[!INCLUDE[tsql](../includes/tsql-md.md)] カーソルも API カーソルも要求されない場合、既定では、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] によって既定の結果セットと呼ばれる完全な結果セットがアプリケーションに返されます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-180">If neither a [!INCLUDE[tsql](../includes/tsql-md.md)] nor API cursor has been requested, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] defaults to returning a complete result set, known as a default result set, to the application.</span></span>  
  
## <a name="cursor-process"></a><span data-ttu-id="26cf0-181">カーソル処理</span><span class="sxs-lookup"><span data-stu-id="26cf0-181">Cursor Process</span></span>  
 [!INCLUDE[tsql](../includes/tsql-md.md)] <span data-ttu-id="26cf0-182">カーソルと API カーソルでは構文が異なりますが、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のどのカーソルでも、以下の一般的な処理を行います。</span><span class="sxs-lookup"><span data-stu-id="26cf0-182">cursors and API cursors have different syntax, but the following general process is used with all [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cursors:</span></span>  
  
1.  <span data-ttu-id="26cf0-183">カーソルを [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントの結果セットに関連付け、カーソル内の行を更新可能にするかどうかなど、そのカーソルの特性を定義します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-183">Associate a cursor with the result set of a [!INCLUDE[tsql](../includes/tsql-md.md)] statement, and define characteristics of the cursor, such as whether the rows in the cursor can be updated.</span></span>  
  
2.  <span data-ttu-id="26cf0-184">カーソルを設定する [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-184">Execute the [!INCLUDE[tsql](../includes/tsql-md.md)] statement to populate the cursor.</span></span>  
  
3.  <span data-ttu-id="26cf0-185">参照するカーソル内の行を取得します。</span><span class="sxs-lookup"><span data-stu-id="26cf0-185">Retrieve the rows in the cursor you want to see.</span></span> <span data-ttu-id="26cf0-186">カーソルから 1 行または 1 ブロックの行を取得する操作をフェッチと言います。</span><span class="sxs-lookup"><span data-stu-id="26cf0-186">The operation to retrieve one row or one block of rows from a cursor is called a fetch.</span></span> <span data-ttu-id="26cf0-187">フェッチを連続して実行し、順方向または逆方向に行を取得することをスクロールと呼びます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-187">Performing a series of fetches to retrieve rows in either a forward or backward direction is called scrolling.</span></span>  
  
4.  <span data-ttu-id="26cf0-188">必要に応じて、カーソル内の現在位置の行に対して、更新または削除の変更操作を行います。</span><span class="sxs-lookup"><span data-stu-id="26cf0-188">Optionally, perform modification operations (update or delete) on the row at the current position in the cursor.</span></span>  
  
5.  <span data-ttu-id="26cf0-189">カーソルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="26cf0-189">Close the cursor.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="26cf0-190">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="26cf0-190">Related Content</span></span>  
 <span data-ttu-id="26cf0-191">[カーソル動作](native-client-odbc-cursors/cursor-behaviors.md) [カーソルの実装方法](native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)</span><span class="sxs-lookup"><span data-stu-id="26cf0-191">[Cursor Behaviors](native-client-odbc-cursors/cursor-behaviors.md) [How Cursors Are Implemented](native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26cf0-192">参照</span><span class="sxs-lookup"><span data-stu-id="26cf0-192">See Also</span></span>  
 <span data-ttu-id="26cf0-193">[Transact-sql&#41;&#40;カーソルの宣言](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26cf0-193">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="26cf0-194">[カーソル &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/cursors-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26cf0-194">[Cursors &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/cursors-transact-sql) </span></span>  
 <span data-ttu-id="26cf0-195">[カーソル関数 &#40;Transact-sql&#41;](/sql/t-sql/functions/cursor-functions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="26cf0-195">[Cursor Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/cursor-functions-transact-sql) </span></span>  
 [<span data-ttu-id="26cf0-196">カーソル ストアド プロシージャ &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="26cf0-196">Cursor Stored Procedures &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql)  
  
  