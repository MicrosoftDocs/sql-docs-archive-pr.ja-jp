---
title: ブレークポイントの位置の編集
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint location
ms.assetid: 5c28e411-0377-4210-a7ce-2a5c13dcdf74
author: rothja
ms.author: jroth
ms.openlocfilehash: 919e62d53d5c9e8898bf1d49c4b5e5aa4c0ed107
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630872"
---
# <a name="edit-a-breakpoint-location"></a>ブレークポイントの位置の編集
  ブレークポイントの位置では、ブレークポイントを設定する [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイル内の行や文字を指定します。 ブレークポイントの位置を編集して、ブレークポイントを別の位置や別のスクリプトに移動できます。  
  
## <a name="editing-a-location"></a>位置の編集  
 ブレークポイントの位置を編集すると、ブレークポイントはヒット カウント、条件などの既存のすべてのプロパティと共に新しい位置に移動します。  
  
#### <a name="to-edit-a-breakpoint-location"></a>ブレークポイントの位置を編集するには  
  
1.  エディター ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。  
  
     または  
  
     **[ブレークポイント]** ウィンドウで、ブレークポイント グリフを右クリックし、ショートカット メニューの **[場所]** をクリックします。  
  
2.  **[ファイルのブレークポイント]** ダイアログ ボックスで、新しいファイルを指定するには **[ファイル]** 、新しい行を指定するには **[行]** 、行内の新しい場所を指定するには **[文字]** の各項目を編集します。 指定した新しいファイルがクエリ エディター ウィンドウで既に開いている場合は、ブレークポイントがそのエディター ウィンドウに移動します。 ファイルが開いていない場合は、新しいクエリ エディター ウィンドウが開き、そのファイルが読み込まれ、ブレークポイントが新しい位置に移動します。  
  
     **をデバッグする場合、** [元のバージョンと異なるソース コードを許可する] [!INCLUDE[tsql](../../includes/tsql-md.md)]オプションは無効です。  
  
## <a name="see-also"></a>参照  
 [ヒットカウントの指定](specify-a-hit-count.md)   
 [ブレークポイントアクションの指定](specify-a-breakpoint-action.md)   
 [ブレークポイント条件の指定](specify-a-breakpoint-condition.md)   
 [ブレークポイント フィルターの指定](specify-a-breakpoint-filter.md)  
