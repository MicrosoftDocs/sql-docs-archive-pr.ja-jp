---
title: テーブル値パラメーターの ODBC SQL 型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL_SS_TABLE
ms.assetid: 6725bfb9-5f10-4115-be09-fd9c9f5779ea
author: rothja
ms.author: jroth
ms.openlocfilehash: c8ed46bf117c9158ae5b60c10ebd89e3d348f77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643819"
---
# <a name="odbc-sql-type-for-table-valued-parameters"></a>テーブル値パラメーター用の ODBC SQL 型
  テーブル値パラメーターは、新しい ODBC SQL 型である SQL_SS_TABLE でサポートされます。  
  
## <a name="remarks"></a>解説  
 SQL_SS_TABLE は、他の ODBC データ型または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型に変換できません。  
  
 SQL_SS_TABLE が SQLBindParameter の*ValueType*パラメーターで C データ型として使用されている場合、またはアプリケーションパラメーター記述子 (APD) レコードの SQL_DESC_TYPE を SQL_SS_TABLE に設定しようとした場合、SQL_ERROR が返され、"アプリケーションバッファーの種類が無効です" という内容の診断レコードが生成されます。  
  
 IPD レコードで SQL_DESC_TYPE を SQL_SS_TABLE に設定し、対応するアプリケーション パラメーター記述子レコードが SQL_C_DEFAULT ではない場合、SQL_ERROR が返され、"アプリケーションのバッファー型が無効です" というメッセージで SQLSTATE=HY003 の診断レコードが生成されます。 これは、SQLSetDescField、SQLSetDescRec、または SQLBindParameter の*ParameterType*で発生する可能性があります。  
  
 SQLGetData を呼び出すときに*TargetType*パラメーターが SQL_SS_TABLE 場合、SQL_ERROR が返され、"アプリケーションバッファーの種類が無効です" という SQLSTATE = HY003 の診断レコードが生成されます。  
  
 テーブル値パラメーターの列は、SQL_SS_TABLE 型としてバインドできません。 `SQLBindParameter` *ParameterType*を SQL_SS_TABLE に設定してを呼び出した場合、SQL_ERROR が返され、"SQL データ型が無効です" という SQLSTATE = HY004 の診断レコードが生成されます。 これは、SQLSetDescField および SQLSetDescRec でも発生する可能性があります。  
  
 テーブル値パラメーターの列の値には、パラメーターおよび結果列と同じデータ変換オプションが設定されています。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 以降では、テーブル値パラメーターは入力パラメーターのみに使用できます。 SQLBindParameter または SQLSetDescField を介して SQL_PARAM_INPUT 以外の値に SQL_DESC_PARAMETER_TYPE を設定しようとすると、SQL_ERROR が返され、SQLSTATE = HY105 のステートメントに診断レコードが追加され、"パラメーターの型が無効です" というメッセージが表示されます。  
  
 テーブル値パラメーターでは、行ごとの既定値はサポートされていないので、テーブル値パラメーターの列は*StrLen_or_IndPtr*で SQL_DEFAULT_PARAM を使用できません。 代わりに、アプリケーションで列の属性 SQL_CA_SS_COL_HAS_DEFAULT_VALUE を 1 に設定できます。 つまり、この列にすべての行の既定値が含まれます。 *StrLen_or_IndPtr*が SQL_DEFAULT_PARAM に設定されている場合、sqlexecute または SQLExecDirect は SQL_ERROR を返し、メッセージ "文字列またはバッファーの長さが無効です" というメッセージで SQLSTATE = HY090 のステートメントに診断レコードが追加されます。  
  
## <a name="see-also"></a>参照  
 [テーブル値パラメーター &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
