---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 704b847bde2d7b4da9da91b4b24bfe2b9e2afa07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643911"
---
# <a name="mssqlserver_1462"></a>MSSQLSERVER_1462
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|1462|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|メッセージ テキスト|やり直し操作の失敗により、データベース ミラーリングが無効になっています。 再開できません。|  
  
## <a name="explanation"></a>説明  
 データベース ミラーリングで、ミラーでのログ レコードの再実行に失敗しました。  
  
### <a name="possible-causes"></a>考えられる原因  
 最も可能性が高い原因は、プリンシパル データベースでファイルの追加操作が完了しても、ファイル名またはディレクトリ構造がプリンシパル サーバーとミラー サーバーで異なるために、ミラー データベースで失敗したことです。  
  
## <a name="user-action"></a>ユーザーの操作  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラー ログで、このエラーの原因を調べます。 原因を解決してデータベースでミラーリングを再開します。  
  
## <a name="see-also"></a>参照  
 [データベース ミラーリング構成のトラブルシューティング &#40;SQL Server&#41;](../../database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
  
