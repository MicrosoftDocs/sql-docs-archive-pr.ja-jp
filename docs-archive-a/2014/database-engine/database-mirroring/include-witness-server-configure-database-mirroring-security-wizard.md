---
title: ミラーリング監視サーバーを含める (データベース ミラーリング セキュリティ構成ウィザード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.inclwitness.f1
ms.assetid: f04b38a4-f4e2-4d4c-bdac-7cc70e5a5684
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 314d2205463436e2182b8d1a4cc0cc972213bd5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632656"
---
# <a name="include-witness-server-configure-database-mirroring-security-wizard"></a>[ミラーリング監視サーバーを含める] (データベース ミラーリング セキュリティ構成ウィザード)
  このページを使用すると、データベース ミラーリング用に、このセキュリティ構成にミラーリング監視サーバーを含めるかどうかを指定できます。  
  
 **SQL Server Management Studio を使用してデータベース ミラーリングを構成するには**  
  
-   [Windows 認証を使用してデータベース ミラーリング セッションを確立する &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [データベース ミラーリング セキュリティ構成ウィザードの起動 &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **はい**  
 ミラーリング監視サーバー インスタンスをセキュリティ構成に含めるには、これをクリックします。 ミラーリング監視サーバーは、自動フェールオーバーを伴う高い安全性モード (プリンシパル サーバー インスタンスで障害が発生した場合に、ミラー サーバー インスタンスへ自動的に処理をフェールオーバーするモード) に必要です。  
  
 **いいえ**  
 ミラーリング監視サーバーを使用せずにセキュリティを構成するには、これをクリックします。  
  
## <a name="see-also"></a>参照  
 [データベース プロパティ &#40;[ミラーリング] ページ&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [データベース ミラーリング &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [データベース ミラーリング監視サーバー](database-mirroring-witness.md)  
  
  
