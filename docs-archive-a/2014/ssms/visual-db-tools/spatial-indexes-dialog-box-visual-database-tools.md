---
title: '[空間インデックス] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.spatialindexes
ms.assetid: 4d84239a-68c7-4aa2-8602-2b51dd07260f
author: stevestein
ms.author: sstein
ms.openlocfilehash: e401b7f93a8376b1c6dc0c75ca29cbdc8a39863d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640317"
---
# <a name="spatial-indexes-dialog-box-visual-database-tools"></a>[空間インデックス] ダイアログ ボックス (Visual Database Tools)
  **[インデックス/キー]** ダイアログ ボックスを使用してインデックスを作成できない **geometry** データ型や **geography** データ型の列 (*空間列*) のインデックスを作成するには、 **[空間インデックス]** を使用します。 各空間列に複数の空間インデックスを作成できますが、空間インデックスは一度に 1 つずつ作成する必要があります。  
  
 空間インデックスの作成の制限については、「 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[選択された空間インデックス]**  
 既存の空間インデックスを一覧表示します。 特定の空間インデックスのプロパティを表示するには、そのインデックスをクリックします。 この一覧が空の場合、テーブルには空間インデックスがまったく定義されていません。  
  
 **追加**  
 新しい空間インデックスを作成します。  
  
 **削除**  
 **[選択された空間インデックス]** ボックスの一覧で選択した空間インデックスを削除します。  
  
 **[オブジェクトごとのセル数]**  
 インデックスの単一の空間オブジェクトに使用できるオブジェクトごとのテセレーション セル数を示します。 1 ～ 8192 の整数を指定できます。 既定値は 16 です。  
  
 1 つのオブジェクトが *n*で指定されたセル数よりも多くのセルを使用する場合、インデックス作成では、必要なだけの数のセルが使用され、完全な最上位レベルのテセレーションが提供されます。 その場合、オブジェクトには指定されたセル数よりも多くのセルが割り当てられることがあります。 このとき、最大数は、 **[レベル 1]** の密度に応じて最上位レベルのグリッドで生成されたセルの数となります。  
  
 **[列]**  
 列名と並べ替え順序を示します。  
  
 **[IsSpatialIndex]**  
 空間インデックスが選択されていることを示します。  
  
 **Level 1 (レベル 1)**  
 第 1 レベル (最上位) グリッドの密度を示します。  
  
 **Level 2 (レベル 2)**  
 第 2 レベルのグリッドの密度を示します。  
  
 **Level 3 (レベル 3)**  
 第 3 レベルのグリッドの密度を示します。  
  
 **[レベル 4]**  
 第 4 レベルのグリッドの密度を示します。  
  
 **[テセレーション スキーム]**  
 テセレーション スキームを指定します。  
  
 **[ジオメトリ]** 列のオプション:  
  
-   geometry 列の場合は **[ジオメトリ グリッド]** になります。  
  
-   geography 列の場合は **[地理グリッド]** になります。  
  
 **Type**  
 空間インデックスが選択されていることを示します。  
  
 **[X の最大値]**  
 境界ボックスの右上隅の x 座標を指定します。 このプロパティは、 **[テセレーション スキーム]** が **[地理グリッド]** の場合、淡色表示になります。  
  
 **[X の最小値]**  
 境界ボックスの左下隅の x 座標を指定します。 このプロパティは、 **[テセレーション スキーム]** が **[地理グリッド]** の場合、淡色表示になります。  
  
 **[Y の最大値]**  
 境界ボックスの右上隅の y 座標を指定します。 このプロパティは、 **[テセレーション スキーム]** が **[地理グリッド]** の場合、淡色表示になります。  
  
 **[Y の最小値]**  
 境界ボックスの左下隅の y 座標を指定します。 このプロパティは、 **[テセレーション スキーム]** が **[地理グリッド]** の場合、淡色表示になります。  
  
 **[ID]**  
 展開して、 **[オブジェクト名]** プロパティ フィールドと **[説明]** プロパティ フィールドを表示します。  
  
 **[(名前)]**  
 空間インデックスの名前を表示します。 新しいインデックスを作成した場合、このプロパティには、テーブル デザイナーのアクティブ ウィンドウのテーブルに基づいて、既定の名前が設定されます。 名前はいつでも変更できます。  
  
 **説明**  
 インデックスの説明です。 より詳細な説明を記述する場合は、 **[説明]** をクリックしてから、プロパティ フィールドの右に表示される省略記号ボタン ( **[...]** ) をクリックします。 これにより、テキストを書くことができる領域が大きくなります。  
  
 **[テーブル デザイナー] カテゴリ**  
 展開してこの空間インデックスのプロパティに関する情報を表示します。  
  
 **[FILL の指定]**  
 展開して **[FILL FACTOR]** および **[インデックスの埋め込み]** の情報を表示します。  
  
 **[FILL FACTOR]**  
 システムが使用できるインデックス ページの割合を指定します。 ページがいっぱいになった場合、新しいデータが追加されると、システムはそのページを分割する必要があります。これによりパフォーマンスが低下します。  
  
-   値 100 は、ページがいっぱいになることを示しています。必要な記憶領域は最小限ですが、最も非効率的です。 この設定は、データに変更がない (たとえば読み取り専用テーブルのデータ) 場合にだけ使用します。  
  
-   値が小さいほどデータ ページ上の空き領域が大きくなり、インデックスが増大したときにデータ ページを分割する必要性が小さくなります。 ただし、より大きな記憶領域が必要になります。 この設定は、テーブル内のデータに変更が生じることが予想される場合に適しています。  
  
 **[インデックスの埋め込み]**  
 **[FILL FACTOR]** で指定されている空き領域 (埋め込み) の割合と同じ比率で、このインデックスにページを提供します。  
  
 **[ページのロックを許可]**  
 該当するインデックスでページレベルのロックを許可するかどうかを指定します。 ページレベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。  
  
 **統計の再計算**  
 インデックスの作成時に、統計情報を新たに計算するかどうかを指定します。 統計情報の再計算により、インデックスの構築には前よりも時間がかかりますが、通常はクエリのパフォーマンスが向上します。  
  
 **[行のロックを許可]**  
 該当するインデックスで行レベルのロックを許可するかどうかを指定します。 行レベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。  
  
## <a name="see-also"></a>参照  
 [空間インデックスの概要](../../relational-databases/spatial/spatial-indexes-overview.md)  
  
  