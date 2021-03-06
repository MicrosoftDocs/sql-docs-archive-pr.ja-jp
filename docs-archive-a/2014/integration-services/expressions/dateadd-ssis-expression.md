---
title: DATEADD (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9feb288318bdf9705928cb930f175f5c170c384e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736637"
---
# <a name="dateadd-ssis-expression"></a>DATEADD (SSIS 式)
  指定された日付要素に、日付または期間を示す数値を加算して、新しい DT_DBTIMESTAMP の値を返します。 数値のパラメーターは整数に、日付のパラメーターは有効な日付に評価される必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a>引数  
 *datepart*  
 日付の要素のうち、数値を追加する部分を指定するパラメーターです。  
  
 *number*  
 *datepart*に加算される値です。 式が解析される際、値は既知の整数である必要があります。  
  
 *date*  
 有効な日付または日付形式の文字列を返す式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_DBTIMESTAMP  
  
## <a name="remarks"></a>解説  
 次の表に、式エバリュエーターで認識される日付要素 (datepart) と省略形を示します。 日付要素の名前では大文字と小文字が区別されません。  
  
|datepart|省略形|  
|--------------|-------------------|  
|年|yy、yyyy|  
|Quarter|qq、q|  
|Month|mm、m|  
|Dayofyear|dy、y|  
|日|dd、d|  
|Week|wk、ww|  
|平日|dw、w|  
|時|Hh|  
|分|mi、n|  
|秒|ss、s|  
|Millisecond|Ms|  
  
 式が解析される際、 *number* 引数が使用できる必要があります。 引数には定数または変数を指定できます。 式が解析される際に既知の値が提供されないため、列の値を使用することはできません。  
  
 *datepart* 引数は引用符で囲む必要があります。  
  
 日付リテラルは、日付データ型のいずれかに明示的にキャストされる必要があります。 詳細については、「 [Integration Services Data Types](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 引数が NULL の場合、DATEADD は NULL を返します。  
  
 日付が無効の場合、日付または時間の単位が文字列でない場合、または増分が静的な整数でない場合は、エラーが発生します。  
  
## <a name="ssis-expression-examples"></a>SSIS 式の例  
 この例では、現在の日付に 1 か月追加した値を返します。  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 この例では、 **ModifiedDate** 列の日付に 21 日を追加します。  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 この例では、リテラルの日付に 2 年を追加します。  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a>参照  
 [DATEDIFF &#40;SSIS 式&#41;](datediff-ssis-expression.md)   
 [DATEPART &#40;SSIS 式&#41;](datepart-ssis-expression.md)   
 [DAY &#40;SSIS 式&#41;](day-ssis-expression.md)   
 [MONTH &#40;SSIS 式&#41;](month-ssis-expression.md)   
 [YEAR &#40;SSIS 式&#41;](year-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
