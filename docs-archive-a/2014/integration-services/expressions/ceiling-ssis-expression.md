---
title: CEILING (SSIS 式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645751"
---
# <a name="ceiling-ssis-expression"></a>CEILING (SSIS 式)
  数値式以上で最小の整数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a>引数  
 *numeric_expression*  
 有効な数値式です。  
  
## <a name="result-types"></a>戻り値の型  
 関数に送信された数値式のデータ型です。  
  
## <a name="remarks"></a>解説  
 引数が NULL の場合、CEILING は NULL を返します。  
  
## <a name="expression-examples"></a>式の例  
 この例では、正の値、負の値、および 0 に CEILING 関数を適用します。  
  
```  
CEILING(123.74)  
```  
  
 124.00 を返します。  
  
```  
CEILING(-124.27)  
```  
  
 -124.00 を返します  
  
```  
CEILING(0.00)  
```  
  
 0\.00 を返します。  
  
## <a name="see-also"></a>参照  
 [FLOOR &#40;SSIS 式&#41;](floor-ssis-expression.md)   
 [関数 (SSIS 式)](functions-ssis-expression.md)  
  
  
