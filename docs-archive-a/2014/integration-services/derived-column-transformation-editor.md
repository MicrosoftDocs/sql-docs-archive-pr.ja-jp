---
title: 派生列変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.derivedcolumntransformation.f1
helpviewer_keywords:
- Derived Column Transformation Editor
ms.assetid: ff73923e-d245-43d8-bf24-af3bdc942e51
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 41a0f0dcd253473f78f2f38426b5fbd3d2ac2812
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644571"
---
# <a name="derived-column-transformation-editor"></a>派生列変換エディター
  **[派生列変換エディター]** ダイアログ ボックスを使用すると、新しい列または置換列を作成する式を作成できます。  
  
 派生列変換の詳細については、「 [派生列変換](data-flow/transformations/derived-column-transformation.md)」をご覧ください。  
  
## <a name="options"></a>Options  
 **[変数] と [列]**  
 使用可能な変数と列の一覧から、下のペインにある既存のテーブル行または一覧の下の新しい行へドラッグすることによって、変数または入力列を使用する式を作成します。  
  
 **[関数] と [演算子]**  
 関数と演算子を一覧から下のペインにドラッグすることによって、入力データおよび直接出力データを評価する関数または演算子を使用する式を作成します。  
  
 **派生列名**  
 派生列名を指定します。 既定は派生列の番号付けされた一覧ですが、一意のわかりやすい名前を付けることもできます。  
  
 **[派生列]**  
 一覧から派生列を選択します。 派生列を新しい出力列として追加するか、既存の列のデータを置き換えるかを選択します。  
  
 **[式]**  
 式を入力するか、前述の使用可能な列、変数、関数、および演算子の一覧からドラッグすることによって式を作成します。  
  
 このプロパティの値は、プロパティ式を使用して指定することができます。  
  
 **関連トピック**: [Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)、[ &#40;SSIS の式&#41;](expressions/operators-ssis-expression.md)、[ &#40;SSIS の式&#41;](expressions/functions-ssis-expression.md)  
  
 **[データ型]**  
 新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって自動的に式が評価され、データ型が適切に設定されます。 この列の値は読み取り専用です。 詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。  
  
 **[データ型]**  
 新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって自動的に式が評価され、文字列データに対する列の長さが設定されます。 この列の値は読み取り専用です。  
  
 **[精度]**  
 新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、データ型に基づく数値データの有効桁数が自動的に設定されます。 この列の値は読み取り専用です。  
  
 **スケール**  
 新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、データ型に基づく数値データの小数点以下桁数が自動的に設定されます。 この列の値は読み取り専用です。  
  
 **コードページ**  
 新しい列にデータを追加すると、 **[派生列変換エディター]** ダイアログ ボックスによって、DT_STR データ型のコード ページが自動的に設定されます。 **[コード ページ]** は必要に応じて更新できます。  
  
 **エラー出力の構成**  
 [[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [派生列変換を使用して列の値を取得する](data-flow/transformations/derive-column-values-by-using-the-derived-column-transformation.md)  
  
  
