---
title: 統計名の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- renaming statistics
- statistics [SQL Server], renaming
ms.assetid: a3bed7b7-3dc5-4b33-b1c6-67c27f573764
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1528dcec50a662524531065d597b004fe7f59e5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644375"
---
# <a name="rename-statistics"></a>統計名の変更
  を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で統計オブジェクトの名前を変更できます。 [!INCLUDE[tsql](../../includes/tsql-md.md)]  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **統計オブジェクトの名前を変更するために使用するもの:**  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 既定では、インデックスの作成によって、インデックスのキー列に統計が作成されます。 そのため、インデックスの名前を変更すると、統計オブジェクトの名前も自動的に変更されます。逆の場合も同様です。  
  
 オブジェクト名の一部または全部を変更すると、スクリプトおよびストアド プロシージャが壊れる可能性があります。 名前を変更するのではなく、統計オブジェクトを削除してから新しい名前で作成し直すことをお勧めします。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 テーブルまたはビューに対する ALTER 権限が必要です。  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-rename-a-statistics-object"></a>統計オブジェクトの名前を変更するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    EXEC sp_rename N'AK_Employee_LoginID', N'AK_Emp_Login', N'STATISTICS';   
    GO  
    ```  
  
 詳細については、「[sp_rename &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-rename-transact-sql)」を参照してください。  
  
  
