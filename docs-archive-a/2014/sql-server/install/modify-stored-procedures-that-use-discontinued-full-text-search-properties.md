---
title: 廃止されたフルテキスト検索プロパティを使用するストアドプロシージャの変更 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- discontinued properties [Full-Text Search]
- stored procedures [Full-Text Search]
ms.assetid: 8d9392d9-a9ba-4378-84e4-59f516b67ddb
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 12262a588742f0e3be094e32a2a0208a85b6f28a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640434"
---
# <a name="modify-stored-procedures-that-use-discontinued-full-text-search-properties"></a>廃止されたフルテキスト検索プロパティを使用するストアド プロシージャを変更する
  ストアド プロシージャが正しく実行されるようにするには、既存のプロシージャを編集し、削除または非推奨とされたフルテキスト関連のプロパティおよび設定を削除する必要があります。  
  
## <a name="component"></a>コンポーネント  
 フルテキスト検索  
  
## <a name="description"></a>説明  
 以下のフルテキスト検索関連のプロパティおよび設定が削除されています。  
  
-   **DataTimeout**  
  
-   **ConnectTimeout**  
  
-   **Clean_up**  
  
-   **LogSize**  
  
 以下のフルテキスト検索関連のプロパティおよび設定が削除または非推奨とされています：  
  
-   フルテキスト カタログの "パス"。 フルテキスト カタログは、システムでの特定のファイル パスを持たない論理オブジェクトになります。  
  
-   [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] ではデータベースがフルテキスト検索に対して常に既定で有効になっているので、SP_FULLTEXT_DATABASE の有効化/無効化は効力がありません。  
  
## <a name="corrective-action"></a>修正措置  
 お使いのストアド プロシージャを変更して、これらのプロパティを削除してください。  
  
## <a name="see-also"></a>参照  
 [アップグレード アドバイザーの使用](../../../2014/sql-server/install/working-with-upgrade-advisor.md)  
  
  
