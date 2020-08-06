---
title: 実行時データパラメーターの使用 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data-at-execution
ms.assetid: 2a738aef-c991-4f62-bdab-a5221c335f31
author: rothja
ms.author: jroth
ms.openlocfilehash: cf87309f1e325b94ff455d446fbd2e76d5c06ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738310"
---
# <a name="use-data-at-execution-parameters-odbc"></a><span data-ttu-id="c8279-102">実行時データ パラメーターの使用 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="c8279-102">Use Data-at-Execution Parameters (ODBC)</span></span>
    
### <a name="to-use-data-at-execution-text-ntext-or-image-parameters"></a><span data-ttu-id="c8279-103">実行時データ text パラメーター、ntext パラメーター、または image パラメーターを使用するには</span><span class="sxs-lookup"><span data-stu-id="c8279-103">To use data-at-execution text, ntext, or image parameters</span></span>  
  
1.  <span data-ttu-id="c8279-104">[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) を呼び出してプログラム バッファーをステートメント パラメーターにバインドするときに、次のように指定します。</span><span class="sxs-lookup"><span data-stu-id="c8279-104">When calling [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) to bind a program buffer to the statement parameter:</span></span>  
  
    -   <span data-ttu-id="c8279-105">最後のパラメーターには、SQL_LEN_DATA_AT_EXEC (*length*) を*length*使用し `text` ます。 length は、、 `ntext` 、またはパラメーターデータの合計長 `image` (バイト単位) です。</span><span class="sxs-lookup"><span data-stu-id="c8279-105">For the last parameter, use SQL_LEN_DATA_AT_EXEC(*length*) where *length* is the total length of the `text`, `ntext`, or `image` parameter data in bytes.</span></span>  
  
    -   <span data-ttu-id="c8279-106">プログラム定義のパラメーター識別子として `rgbValue` (8 番目のパラメーター) を使用します。</span><span class="sxs-lookup"><span data-stu-id="c8279-106">Use an `rgbValue` (eighth parameter) of a program-defined parameter identifier.</span></span>  
  
2.  <span data-ttu-id="c8279-107">[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) または [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) を呼び出すと、SQL_NEED_DATA が返されます。これは、実行時データ パラメーターを処理する準備が整っていることを示します。</span><span class="sxs-lookup"><span data-stu-id="c8279-107">Calling [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) or [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) returns SQL_NEED_DATA, which indicates that data-at-execution parameters are ready for processing.</span></span>  
  
3.  <span data-ttu-id="c8279-108">実行時データの各パラメーターに対して次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="c8279-108">For each data-at-execution parameter:</span></span>  
  
    -   <span data-ttu-id="c8279-109">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) を呼び出して、プログラム定義のパラメーター ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="c8279-109">Call [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) to get the program-defined parameter ID.</span></span> <span data-ttu-id="c8279-110">実行時データ パラメーターが他にもある場合は、SQL_NEED_DATA が返されます。</span><span class="sxs-lookup"><span data-stu-id="c8279-110">It will return SQL_NEED_DATA if there is another data-at-execution parameter.</span></span>  
  
    -   <span data-ttu-id="c8279-111">[SQLPutData](../native-client-odbc-api/sqlputdata.md) を 1 回以上呼び出して、パラメーター データを length の長さまで送信します。</span><span class="sxs-lookup"><span data-stu-id="c8279-111">Call [SQLPutData](../native-client-odbc-api/sqlputdata.md) one or more times, to send the parameter data, until length is sent.</span></span>  
  
4.  <span data-ttu-id="c8279-112">[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) を呼び出して、最後の実行時データ パラメーターのデータがすべて送信されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="c8279-112">Call [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) to indicate that all the data for the final data-at-execution parameter is sent.</span></span> <span data-ttu-id="c8279-113">SQL_NEED_DATA は返されません。</span><span class="sxs-lookup"><span data-stu-id="c8279-113">It will not return SQL_NEED_DATA.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8279-114">例</span><span class="sxs-lookup"><span data-stu-id="c8279-114">Example</span></span>  
 <span data-ttu-id="c8279-115">このサンプルでは、SQLParamData と SQLPutData を使用して、SQL_LONG 変数の文字データを読み込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c8279-115">The sample shows how to read SQL_LONG variable character data using SQLParamData and SQLPutData.</span></span> <span data-ttu-id="c8279-116">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c8279-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="c8279-117">AdventureWorks と呼ばれる ODBC データ ソース (既定のデータベースは AdventureWorks サンプル データベース) が必要です </span><span class="sxs-lookup"><span data-stu-id="c8279-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="c8279-118">(AdventureWorks サンプルデータベースは、 [Microsoft SQL Server のサンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホームページからダウンロードできます)。このデータソースは、オペレーティングシステムによって提供される ODBC ドライバーに基づいている必要があります (ドライバー名は "SQL Server")。</span><span class="sxs-lookup"><span data-stu-id="c8279-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="c8279-119">このサンプルを 64 ビット オペレーティング システムで 32 ビット アプリケーションとしてビルドし、実行する場合、%windir%\SysWOW64\odbcad32.exe の ODBC アドミニストレーターを使用して ODBC データ ソースを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c8279-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="c8279-120">このサンプルでは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="c8279-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="c8279-121">名前付きインスタンスに接続するには、ODBC データ ソースの定義を変更し、server\namedinstance 形式でそのインスタンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="c8279-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="c8279-122">[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="c8279-122">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="c8279-123">1 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストを実行して、サンプルで使用するテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="c8279-123">Execute the first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to create the table used by the sample.</span></span>  
  
 <span data-ttu-id="c8279-124">odbc32.lib を使用して 2 つ目の (C++) コード リストをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="c8279-124">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="c8279-125">次に、プログラムを実行します。</span><span class="sxs-lookup"><span data-stu-id="c8279-125">Then execute the program.</span></span>  
  
 <span data-ttu-id="c8279-126">3 つ目の ([!INCLUDE[tsql](../../includes/tsql-md.md)]) コード リストを実行して、サンプルで使用したテーブルを削除します。</span><span class="sxs-lookup"><span data-stu-id="c8279-126">Execute the third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to delete the table used by the sample.</span></span>  
  
```  
use AdventureWorks  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'emp4')  
     DROP TABLE emp4  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="c8279-127">参照</span><span class="sxs-lookup"><span data-stu-id="c8279-127">See Also</span></span>  
 [<span data-ttu-id="c8279-128">Text 列と image 列の管理方法に関するトピック &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="c8279-128">Managing text and image Columns How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/managing-text-and-image-columns-how-to-topics-odbc.md)  
  
  