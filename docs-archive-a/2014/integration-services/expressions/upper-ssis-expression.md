---
title: UPPER (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- UPPER function
- converting lowercase to uppercase
- uppercase characters [Integration Services]
- lowercase characters
ms.assetid: d33985f7-1048-4023-83e4-274090acda78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181e231d735a8e98cd2bce10c692e35668a686f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716433"
---
# <a name="upper-ssis-expression"></a>UPPER (SSIS 式)
  小文字が大文字に変換された状態の文字式を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
UPPER(character_expression)  
```  
  
## <a name="arguments"></a>引数  
 *character_expression*  
 大文字に変換する対象となる文字式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_WSTR  
  
## <a name="remarks"></a>解説  
 UPPER は、DT_WSTR データ型でのみ機能します。 *character_expression* 引数が DT_STR データ型の文字列リテラルまたはデータ列である場合は、UPPER による演算の実行前に、暗黙的に DT_WSTR データ型にキャストされます。 その他のデータ型は、明示的に DT_WSTR データ型にキャストされる必要があります。 詳しくは、「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」および「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。  
  
 引数が NULL の場合、UPPER は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、文字列リテラルを大文字に変換します。 返される結果は "HELLO" です。  
  
```  
UPPER("hello")  
```  
  
 この例では、 **FirstName** 列の最初の文字を大文字に変換します。 **FirstName** が anna の場合、返される結果は "A" です。 詳細については、「[SUBSTRING &#40;SSIS 式&#41;](substring-ssis-expression.md)」を参照してください。  
  
```  
UPPER(SUBSTRING(FirstName, 1, 1))  
```  
  
 この例では、 **PostalCode** 変数の値を大文字に変換します。 **PostalCode** が k4b1s2 の場合、返される結果は "K4B1S2" です。  
  
```  
UPPER(@PostalCode)  
```  
  
## <a name="see-also"></a>参照  
 [LOWER &#40;SSIS 式&#41;](lower-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
