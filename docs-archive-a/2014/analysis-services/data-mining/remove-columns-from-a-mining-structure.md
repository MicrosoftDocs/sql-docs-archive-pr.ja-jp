---
title: マイニング構造からの列の削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], columns
- removing columns
- deleting columns
- columns [data mining], mining structure columns
ms.assetid: 41073ffe-9351-416b-9f0c-62634bc213f9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44ad1de08d57d00fd9798e1ceeddb85d146d7111
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631350"
---
# <a name="remove-columns-from-a-mining-structure"></a>マイニング構造からの列の削除
  データ マイニング デザイナーを使用して、マイニング構造の作成後に構造から列を削除できます。 マイニング構造列を削除する理由には、次のようなものがあります。  
  
-   マイニング構造に列の複数のコピーが格納されており、モデルで重複データを使用しないようにする。  
  
-   データを保護する必要があるが、ドリルスルーが有効になっている。  
  
-   データがモデリングで使用されておらず、処理する必要がない。  
  
 マイニング構造から列を削除しても、データ ソース ビュー内の列または外部データ内の列は変更されません。メタデータのみ削除されます。 ただし、マイニング構造で使用される列を変更する場合は、構造およびその構造に基づくモデルを再処理する必要があります。  
  
### <a name="to-remove-a-column-from-the-mining-structure"></a>マイニング構造から列を削除するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造のツリーを展開し、すべての列を表示します。  
  
3.  削除する列を右クリックして、 **[削除]** をクリックします。  
  
4.  **[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](mining-structure-tasks-and-how-tos.md)  
  
  
