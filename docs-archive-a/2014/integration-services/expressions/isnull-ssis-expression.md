---
title: ISNULL (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- null values [Integration Services]
- ISNULL function
ms.assetid: 88dbf49e-1307-4dda-b9db-ff1632053550
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 51eda21b5c9b85c5f9cfd613d0d92df9729fe620
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716509"
---
# <a name="isnull-ssis-expression"></a>ISNULL (SSIS 式)
  式が NULL かどうかに基づいてブール型の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
ISNULL(expression)  
```  
  
## <a name="arguments"></a>引数  
 *式 (expression)*  
 任意のデータ型の有効な式です。  
  
## <a name="result-types"></a>戻り値の型  
 DT_BOOL  
  
## <a name="expression-examples"></a>式の例  
 この例では、 **DiscontinuedDate** 列に NULL 値が含まれる場合、TRUE を返します。  
  
```  
ISNULL(DiscontinuedDate)  
```  
  
 この例では、 **LastName** 列の値が NULL の場合、"Unknown last name" を返し、NULL でない場合は **LastName**の値を返します。  
  
```  
ISNULL(LastName)? "Unknown last name":LastName  
```  
  
 この例では、変数 **AddDays** の値に関係なく、 **DaysToManufacture**列が NULL の場合は常に TRUE を返します。  
  
```  
ISNULL(DaysToManufacture + @AddDays)  
```  
  
## <a name="see-also"></a>参照  
 [関数 &#40;SSIS 式&#41;](functions-ssis-expression.md)   
 [COALESCE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/coalesce-transact-sql)  
  
  
