---
title: データベース ミラーリング セッションからのミラーリング監視の削除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- witness [SQL Server], turning off
- witness [SQL Server], removing
- database mirroring [SQL Server], witness
ms.assetid: f3ce7afc-8936-4d35-80ce-d0f8fbc318d3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5ede54aca3588a6fcd7cee8759112b606eac752
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716753"
---
# <a name="remove-the-witness-from-a-database-mirroring-session-sql-server"></a>データベース ミラーリング セッションからのミラーリング監視の削除 (SQL Server)
  このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../includes/tsql-md.md)]でデータベース ミラーリング セッションからミラーリング監視サーバーを削除する方法について説明します。 データベース ミラーリング セッション中のどの時点でも、データベース所有者は、データベース ミラーリング セッションのミラーリング監視サーバーを無効にできます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **ミラーリング監視サーバーの削除に使用するツール:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **補足情報:**  [ミラーリング監視サーバーを削除した後](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 データベースに対する ALTER 権限が必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-remove-the-witness"></a>ミラーリング監視サーバーを削除するには  
  
1.  プリンシパル サーバー インスタンスに接続し、 **[オブジェクト エクスプローラー]** ペインでサーバー名をクリックして、サーバー ツリーを展開します。  
  
2.  **[データベース]** を展開し、削除するミラーリング監視が設定されているデータベースをクリックします。  
  
3.  データベースを右クリックして **[タスク]** を選択し、 **[ミラー]** をクリックします。 **[データベースのプロパティ]** ダイアログ ボックスの **[ミラーリング]** ページが開きます。  
  
4.  ミラーリング監視サーバーを削除するには、 **[ミラーリング監視]** フィールドからそのサーバー ネットワーク アドレスを削除します。  
  
    > [!NOTE]  
    >  自動フェールオーバーを伴う高い安全性モードから高パフォーマンス モードに切り替えると、 **[ミラーリング監視]** フィールドの内容は自動的に消去されます。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-remove-the-witness"></a>ミラーリング監視サーバーを削除するには  
  
1.  パートナー サーバー インスタンスで [!INCLUDE[ssDE](../../includes/ssde-md.md)] に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次のステートメントを実行します。  
  
     [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) *database_name* SET WITNESS OFF  
  
     *database_name* はミラー化されたデータベースの名前です。  
  
     次の例では、 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースからミラーリング監視サーバーを削除します。  
  
    ```  
    ALTER DATABASE AdventureWorks2012 SET WITNESS OFF ;  
    ```  
  
##  <a name="follow-up-after-removing-the-witness"></a><a name="FollowUp"></a>補足情報: ミラーリング監視サーバーを削除した後  
 ミラーリング監視を無効にすると、 [動作モード](database-mirroring-operating-modes.md)トランザクションの安全性の設定に応じて変更されます。  
  
-   トランザクションの安全性の設定が FULL (既定値) の場合、セッションは自動フェールオーバーを伴わない高い安全性の同期モードで動作します。  
  
-   トランザクションの安全性が OFF に設定されている場合、セッションは非同期 (高パフォーマンス モード) で動作し、クォーラムを必要としません。 ただし、トランザクションの安全性を OFF に設定した場合は常に、WITNESS も OFF に設定することを強くお勧めします。  
  
> [!TIP]  
>  データベースのトランザクションの安全性設定は、各パートナーについて [sys.database_mirroring](/sql/relational-databases/system-catalog-views/sys-database-mirroring-transact-sql) カタログ ビューの **mirroring_safety_level** 列と **mirroring_safety_level_desc** 列に記録されます。  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
  
-   [Windows 認証を使用してデータベースのミラーリング監視を追加する &#40;Transact-SQL&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
-   [データベース ミラーリング監視サーバーを追加または置き換える方法 &#40;SQL Server Management Studio&#41;](../database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE データベース ミラーリング &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)   
 [データベースミラーリングセッションでのトランザクションの安全性の変更 Transact-sql&#41;の &#40;](change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)   
 [Windows 認証 &#40;使用してデータベースミラーリング監視サーバーを追加する Transact-sql&#41;](add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)   
 [データベース ミラーリング監視サーバー](database-mirroring-witness.md)  
  
  
