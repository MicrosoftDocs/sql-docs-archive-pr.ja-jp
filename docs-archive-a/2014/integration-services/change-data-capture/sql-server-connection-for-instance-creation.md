---
title: インスタンスの作成のための SQL Server 接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 81d0e7e2-d8f0-4bd9-9565-218ce996f28e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cdff17b763257c2a3280981c1f5c16040cc61413
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633270"
---
# <a name="sql-server-connection-for-instance-creation"></a>インスタンスの作成のための SQL サーバー接続
  Oracle CDC インスタンスを作成するときの最初の手順の 1 つは、ターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CDC データベースを作成することです。 この CDC データベースは、SQL Server CDC に対して有効になります。このように有効にするには、ログインが `sysadmin` 固定サーバー ロールのメンバーである必要があります。  
  
 **Oracle CDC インスタンスの作成** ウィザードを開始したユーザーが `sysadmin` 固定サーバー ロールのメンバーではない場合、 **[SQL Server への接続]** ダイアログ ボックスが表示され、SQL Server CDC に対してデータベースを有効にするタスクを実行するために `sysadmin` ロールのメンバーの資格情報を入力するよう求められます。 CDC データベースが作成されると、 `sysadmin` ログインは破棄され、Oracle デザイナー コンソールが入力されたときに使用された元の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインで作業が再開されます。  
  
## <a name="task-list"></a>タスク一覧  
 **[SQL Server への接続]** ダイアログ ボックスに次の情報を入力します。  
  
 **[サーバー名]**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が存在するサーバーの名前を入力します。  
  
 **認証**  
 次のいずれかを選択してください。  
  
-   **[Windows 認証]**  
  
-   **[SQL Server 認証]** : このオプションを選択する場合、接続先の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のユーザーの **[ログイン]** と **[パスワード]** を入力する必要があります。  
  
 ログインには、MSXCDCDB データベースへのアクセスを許可するデータベース ロールが必要です。 また、使用する追加のデータベースへのアクセスがログインに含まれていることも推奨されます。このアクセスが含まれていない場合、ユーザーはそれらのデータベース内のデータを表示できません。  
  
 **[オプション]**  
 矢印をクリックして、構成するオプションを表示します。 これらのオプションを既定値のままにすることもできます。 使用可能なオプションは次のとおりです。  
  
-   **[接続タイムアウト]** : CDC Service for Oracle が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は **15**です。  
  
-   **[実行タイムアウト]** : Oracle CDC Windows Service がコマンドの実行を待機する時間 (秒単位) を入力します。この時間を超過するとタイムアウトとなります。既定値は、 **30**です。  
  
-   **[暗号化接続]** : Oracle CDC Service とターゲットの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの間の暗号化された接続を使用した通信に対しては、 **[暗号化接続]** を選択します。  
  
-   **[詳細設定]** :必要に応じて、 **[詳細設定]** をクリックし、[高度な接続プロパティ] ダイアログ ボックスに追加の接続プロパティを入力します。  
  
     [高度な接続プロパティ] ダイアログ ボックスの詳細については、「 [高度な接続プロパティ](advanced-connection-properties.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server 変更データベースの作成](create-the-sql-server-change-database.md)   
 [CDC デザイナーで使用する SQL Server 接続に必要なアクセス許可](sql-server-connection-required-permissions-for-the-cdc-designer.md)  
  
  
