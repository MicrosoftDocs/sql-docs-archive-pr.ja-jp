---
title: サーバー ロールの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverrole.members.f1
- SQL12.SWB.SERVERROLE.GENERAL.F1
- sql12.swb.serverrole.memberships.f1
helpviewer_keywords:
- SERVER ROLE, creating
ms.assetid: 74f19992-8082-4ed7-92a1-04fe676ee82d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45c3d5bb9c9c7fdae9abe18ab3cb808cae4c1fa1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643747"
---
# <a name="create-a-server-role"></a>サーバー ロールの作成
  このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] または [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]で新しいサーバー ロールを作成する方法について説明します。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [制限事項と制約事項](#Restrictions)  
  
     [Security](#Security)  
  
-   **新しいサーバー ロールを作成する方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> 制限事項と制約事項  
 データベース レベルのセキュリティ保護可能なリソースに対する権限をサーバー ロールに付与することはできません。 データベース ロールを作成するには、「[CREATE ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-role-transact-sql)」を参照してください。  
  
###  <a name="security"></a><a name="Security"></a> セキュリティ  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
  
-   CREATE SERVER ROLE 権限、または sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
-   さらに、ログインのための *server_principal* に対する IMPERSONATE 権限、 *server_principal*として使用されるサーバー ロールのための ALTER 権限、または server_principal として使用される Windows グループのメンバーシップも必要です。  
  
-   AUTHORIZATION オプションを使用してサーバー ロールの所有権を割り当てる場合は、次の権限も必要です。  
  
    -   サーバー ロールの所有権を別のログインに割り当てるには、そのログインに対する IMPERSONATE 権限が必要です。  
  
    -   サーバー ロールの所有権を別のサーバー ロールに割り当てるには、割り当て先のサーバー ロールのメンバーシップまたはそのサーバー ロールに対する ALTER 権限が必要です。  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-create-a-new-server-role"></a>新しいサーバー ロールを作成するには  
  
1.  オブジェクト エクスプローラーで、新しいサーバー ロールを作成するサーバーを展開します。  
  
2.  **[セキュリティ]** フォルダーを展開します。  
  
3.  **[サーバー ロール]** フォルダーを右クリックし、 **[新しいサーバー ロール]** を選択します。  
  
4.  [**新しいサーバーロール-**_server_role_name_ ] ダイアログボックスの **[全般**] ページで、[**サーバーロール名**] ボックスに新しいサーバーロールの名前を入力します。  
  
5.  **[所有者]** ボックスに、新しいサーバー ロールを所有するサーバー プリンシパルの名前を入力します。 または、省略記号 **[...]** をクリックして **[サーバー ログインまたはロールの選択]** ダイアログ ボックスを開きます。  
  
6.  **[セキュリティ保護可能なリソース]** で、1 つ以上のサーバーレベルのセキュリティ保護可能なリソースを選択します。 セキュリティ保護可能なリソースを選択すると、サーバー ロールに、そのセキュリティ保護可能なリソースに対する権限を許可または拒否できます。  
  
7.  **[権限: 明示的]** ボックスで、選択されたセキュリティ保護可能なリソースに対するこのサーバー ロールの権限について、許可、許可の許可、または拒否を行います。 選択されたセキュリティ保護可能なリソースすべてに対して権限を許可または拒否できない場合、権限は部分的に選択された形で表されます。  
  
8.  **[メンバー]** ページで **[追加]** ボタンを使用して、新しいサーバー ロールに個人またはグループを表すログインを追加します。  
  
9. ユーザー定義のサーバー ロールを、別のサーバー ロールのメンバーにすることができます。 現在のユーザー定義のサーバー ロールを、選択したサーバー ロールのメンバーにする場合は、 **[メンバーシップ]** ページでチェック ボックスをオンにします。  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-create-a-new-server-role"></a>新しいサーバー ロールを作成するには  
  
1.  **オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]のインスタンスに接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。  
  
    ```  
    --Creates the server role auditors that is owned the securityadmin fixed server role.  
    USE master;  
    CREATE SERVER ROLE auditors AUTHORIZATION securityadmin;  
    GO  
    ```  
  
 詳細については、「[CREATE SERVER ROLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-server-role-transact-sql)」を参照してください。  
  
  
