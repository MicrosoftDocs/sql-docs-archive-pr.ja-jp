---
title: '[行サンプリング変換エディター] ([サンプリング] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- SQL12.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1
- sql12.dts.designer.rowsamplingtransformation.f1
helpviewer_keywords:
- Row Sampling Transformation Editor
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 26d0c0439e548172225f02220d8f6814a1168ea9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713261"
---
# <a name="row-sampling-transformation-editor-sampling-page"></a>行サンプリング変換エディター ([サンプリング] ページ)
  **[行サンプリング変換エディター]** ダイアログ ボックスを使用すると、指定された行数を使用して、入力の一部をサンプルに分割できます。 この変換は、入力を 2 つの別個の出力に分割します。  
  
 行サンプリング変換の詳細については、「 [Row Sampling Transformation](data-flow/transformations/row-sampling-transformation.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **行数**  
 サンプルとして使用する入力における行数を指定します。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 **[サンプル出力名]**  
 サンプリングされた行を含める出力の一意な名前を指定します。 指定した名前は、SSIS デザイナー内に表示されます。  
  
 **[選択されていない出力名]**  
 サンプリングから除外された行を含む出力の一意な名前を指定します。 指定した名前は、SSIS デザイナー内に表示されます。  
  
 **[次のランダム シードを使用する]**  
 変換でサンプルを作成するために使用する乱数ジェネレーターのサンプリング シードを指定します。 このオプションは、開発およびテスト用にのみ使用することをお勧めします。 ランダム シードを指定しなかった場合は、Microsoft Windows のティック数がシードとして使用されます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [比率サンプリング変換](data-flow/transformations/percentage-sampling-transformation.md)  
  
  
