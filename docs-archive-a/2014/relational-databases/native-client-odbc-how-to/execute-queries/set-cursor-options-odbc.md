---
title: カーソルオプションの設定 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739865"
---
# <a name="set-cursor-options-odbc"></a>カーソル オプションの設定 (ODBC)
  カーソルオプションを設定するには、 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)を呼び出して、カーソルの動作を制御するステートメントオプションを設定または[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)に取得します。  
  
|*属性*|指定内容|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|カーソルの種類。順方向専用、静的、動的、キーセット ドリブンのいずれか|  
|SQL_ATTR_CONCURRENCY|コンカレンシー制御オプション。読み取り専用、ロック、タイムスタンプを使用するオプティミスティック、値を使用するオプティミスティックのいずれか|  
|SQL_ATTR_ROW_ARRAY_SIZE|フェッチごとに取得される行数|  
|SQL_ATTR_CURSOR_SENSITIVITY|他の接続によるカーソル行の更新を、カーソルで表示するかしないか|  
|SQL_ATTR_CURSOR_SCROLLABLE|カーソルを前後にスクロール可能|  
  
 これらの属性の既定値 (順方向専用、読み取り専用、行セット サイズ 1) では、サーバー カーソルを使用しません。 サーバー カーソルを使用するには、少なくともこれらの属性のいずれかを既定値以外に設定する必要があります。また、実行するステートメントを、単一の SELECT ステートメントか、単一の SELECT ステートメントを含むストアド プロシージャにする必要があります。 サーバー カーソルの使用時に、サーバー カーソルによってサポートされていない句 (COMPUTE、COMPUTE BY、FOR BROWSE、および INTO) を SELECT ステートメントで使用することはできません。  
  
 使用するカーソルの種類を制御するには、SQL_ATTR_CURSOR_TYPE と SQL_ATTR_CONCURRENCY を設定するか、SQL_ATTR_CURSOR_SENSITIVITY と SQL_ATTR_CURSOR_SCROLLABLE を設定します。 カーソルの動作を指定するこの 2 つの方法を組み合わせて実行しないでください。  
  
## <a name="example"></a>例  
 次のサンプルでは、ステートメント ハンドルを割り当て、行のバージョンに基づくオプティミスティック コンカレンシーを使用する動的カーソルを種類として設定してから、SELECT を実行します。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>例  
 次のサンプルでは、ステートメント ハンドルを割り当て、スクロール可能な反映型カーソルを設定してから、SELECT を実行します。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>参照  
 [クエリの実行方法に関するトピック &#40;ODBC&#41;](executing-queries-how-to-topics-odbc.md)  
  
  
