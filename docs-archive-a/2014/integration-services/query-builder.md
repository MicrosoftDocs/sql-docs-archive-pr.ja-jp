---
title: クエリビルダー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.querybuilder.f1
helpviewer_keywords:
- Query Builder dialog box
ms.assetid: 780752c9-6e3c-4f44-aaff-4f4d5e5a45c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81be066d92ef1e19a141414dad4359b60efca2f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713282"
---
# <a name="query-builder"></a>[クエリ ビルダー]
  **[クエリ ビルダー]** ダイアログ ボックスを使用すると、SQL 実行タスク、OLE DB 変換元と OLE DB 変換先、および参照変換で使用するクエリを作成できます。  
  
 クエリ ビルダーを使用すると、次のタスクを実行できます。  
  
-   **クエリのグラフィカルな表現と SQL コマンドの操作** クエリ ビルダーには、クエリをグラフィカルに表示するペインと、クエリの SQL テキストを表示するペインがあります。 グラフィカル ペインとテキスト ペインのどちらでも作業ができます。 クエリ ビルダーでは、ビューの同期をとっているため、どちらにも常に最新の状態が表示されます。  
  
-   **関連テーブルの結合** クエリに複数のテーブルを追加する場合、クエリ ビルダーはテーブル間の関係を自動的に認識し、適切な結合コマンドを作成します。  
  
-   **データベースのクエリまたは更新** クエリ ビルダーでは、Transact-SQL の SELECT ステートメントを使用してデータを返すことができます。また、データベースのレコードの更新、追加、削除を行うクエリを作成できます。  
  
-   **結果の即時の表示と編集** クエリを実行し、グリッドのレコードセットを使用して、データベースのレコードをスクロールし、編集できます。  
  
 **[クエリ ビルダー]** ダイアログ ボックスのグラフィカル ツールにより、ドラッグ アンド ドロップ操作でクエリを作成できます。 既定では、[クエリ ビルダー] ダイアログ ボックスは SELECT クエリを構築しますが、INSERT、UPDATE、または DELETE クエリも作成できます。 **[クエリ ビルダー]** ダイアログ ボックスで、すべての種類の SQL ステートメントを解析して実行できます。 パッケージの SQL ステートメントの詳細については、「[Integration Services (SSIS) のクエリ](integration-services-ssis-queries.md)」を参照してください。  
  
 Transact-SQL 言語およびその構文の詳細については、「[Transact-SQL リファレンス (データベース エンジン)](/sql/t-sql/language-reference)」を参照してください。  
  
 クエリで変数を使用して、入力パラメーターへの値の指定、出力パラメーターの値の取得、およびリターン コードの格納を行うこともできます。 パッケージで使用するクエリでの変数の使用の詳細については、「[SQL 実行タスク](control-flow/execute-sql-task.md)」、「[OLE DB ソース](data-flow/ole-db-source.md)」、および「[Integration Services (SSIS) のクエリ](integration-services-ssis-queries.md)」を参照してください。 SQL 実行タスクでの変数の使用の詳細については、「 [SQL 実行タスクのパラメーターとリターン コード](../../2014/integration-services/parameters-and-return-codes-in-the-execute-sql-task.md) 」および「 [SQL 実行タスクにおける結果セット](../../2014/integration-services/result-sets-in-the-execute-sql-task.md)」を参照してください。  
  
 参照変換およびあいまい参照変換でも、パラメーターとリターン コードに変数を使用できます。 OLE DB ソースに関する情報は、これら 2 つの変換にも適用されます。  
  
## <a name="options"></a>Options  
 **ツール バー**  
 ツール バーは、データセットの管理、表示するペインの選択、クエリ機能の制御に使用します。  
  
|値|説明|  
|-----------|-----------------|  
|**[ダイアグラム ペインの表示/非表示]**|**[ダイアグラム]** ペインの表示と非表示を切り替えます。|  
|**[グリッド ペインの表示/非表示]**|**[グリッド]** ペインの表示と非表示を切り替えます。|  
|**[SQL ペインの表示/非表示]**|**SQL**ペインの表示と非表示を切り替えます。|  
|**[結果ペインの表示/非表示]**|**[結果]** ペインの表示と非表示を切り替えます。|  
|**実行**|クエリを実行します。 結果は結果ペインに表示されます。|  
|**[SQL の確認]**|SQL ステートメントが有効であることを確認します。|  
|**昇順で並べ替え**|[グリッド] ペインで選択した列の出力行を昇順で並べ替えます。|  
|**降順で並べ替え**|[グリッド] ペインで選択した列の出力行を降順で並べ替えます。|  
|**フィルターの削除**|[グリッド] ペインの列名を選択してから、 **[フィルターの削除]** をクリックして列の並べ替え条件を削除します。|  
|**[Group By の使用]**|クエリに GROUP BY 機能を追加します。|  
|**[テーブルの追加]**|新しいテーブルをクエリに追加します。|  
  
 **クエリ定義**  
 クエリ定義は、クエリの定義およびテストを行うツール バーおよびペインを提供します。  
  
|ペイン|説明|  
|----------|-----------------|  
|**ダイアグラム**ペイン|クエリをダイアグラムに表示します。 このダイアグラムには、クエリに含まれるテーブルと、その結合状態が表示されます。 テーブルの列の横にあるチェック ボックスをオンにすると、クエリの出力にその列が追加されます。オフにすると、削除されます。<br /><br /> テーブルをクエリに追加すると、クエリ ビルダーにより、テーブルのキーに応じてテーブル間の結合が行われます。 結合を追加するには、あるテーブルのフィールドを別のテーブルのフィールドにドラッグします。 結合を管理するには、結合を右クリックしてからメニュー オプションを選択します。<br /><br /> **ダイアグラム**ペインを右クリックすると、テーブルの追加や削除、すべてのテーブルの選択、ペインの表示と非表示の切り替えを行うことができます。|  
|**グリッド**ペイン|クエリをグリッドに表示します。 このペインを使用して、クエリの列の追加や削除を行うことができます。また、各列の設定も変更できます。|  
|**SQL**ペイン|クエリを SQL テストとして表示します。 **[ダイアグラム]** ペインおよび **[グリッド]** ペインで行われた変更がここに表示されます。このペインで行われた変更は、 **[ダイアグラム]** ペインおよび **[グリッド]** ペインに表示されます。|  
|**[結果]** ペイン|ツール バーの **[実行]** をクリックしたときに、クエリの結果が表示されます。|  
  
## <a name="see-also"></a>参照  
 [SQL 実行タスク](control-flow/execute-sql-task.md)   
 [OLE DB ソース](data-flow/ole-db-source.md)   
 [OLE DB 変換先](data-flow/ole-db-destination.md)   
 [参照変換](data-flow/transformations/lookup-transformation.md)   
 [SSIS&#41; クエリ &#40;Integration Services](integration-services-ssis-queries.md)   
 [Integration Services パッケージで MERGE を実行する](control-flow/merge-in-integration-services-packages.md)  
  
  