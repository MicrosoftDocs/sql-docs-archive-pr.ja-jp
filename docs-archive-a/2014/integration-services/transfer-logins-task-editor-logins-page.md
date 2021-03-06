---
title: '[ログイン転送タスクエディター] ([ログイン] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferloginstask.logins.f1
helpviewer_keywords:
- Transfer Logins Task Editor
ms.assetid: bf244c24-bd45-4ece-b66b-78b488f35c5b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b33fea6c78df75b7eebe8987f952dce33bdc4407
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646208"
---
# <a name="transfer-logins-task-editor-logins-page"></a>[ログイン転送タスク エディター] ([ログイン] ページ)
  **[ログイン転送タスク エディター]** ダイアログ ボックスの **[ログイン]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスから別のインスタンスへと [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインをコピーする際のプロパティを指定できます。 このタスクの詳細については、「 [ログイン転送タスク](control-flow/transfer-logins-task.md)」を参照してください。  
  
> [!IMPORTANT]  
>  ログイン転送タスクを実行すると、転送先のサーバー上でランダムなパスワードを使用してログインが作成され、パスワードが無効になります。 このログインを使用するには、 **sysadmin** 固定サーバー ロールのメンバーでパスワードを変更し、そのパスワードを有効にする必要があります。 **sa** ログインは転送できません。  
  
## <a name="options"></a>オプション  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。  
  
 **[LoginsToTransfer]**  
 転送元サーバーから転送先サーバーにコピーされる [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインを選択します。 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**[AllLogins]**|転送元サーバーのすべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ログインが転送先サーバーにコピーされます。|  
|**[SelectedLogins]**|**[LoginsList]** に指定されているログインのみが転送先サーバーにコピーされます。|  
|**[AllLoginsFromSelectedDatabases]**|**[DatabasesList]** で指定されているデータベース内のすべてのログインが転送先サーバーにコピーされます。|  
  
 **[LoginsList]**  
 転送先サーバーにコピーする、転送元サーバーのログインを選択します。 このオプションは、 **[LoginsToTransfer]** を **[SelectedLogins]** に設定した場合のみ使用できます。  
  
 **[DatabasesList]**  
 転送先サーバーにコピーするログインが含まれる、転送元サーバー上のデータベースを選択します。 このオプションは、 **[LoginsToTransfer]** を **[AllLoginsFromSelectedDatabases]** に設定した場合のみ使用できます。  
  
 **[IfObjectExists]**  
 転送先サーバーに同じ名前のログインが既に存在していた場合の処理方法を選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**[FailTask]**|転送先サーバーに同じ名前のログインが既に存在していた場合、タスクが失敗します。|  
|**Overwrite**|転送先サーバーにある同じ名前のログインは上書きされます。|  
|**Skip**|転送先サーバーにある同じ名前のログインはスキップされます。|  
  
 **[CopySids]**  
 ログインに関連付けられたセキュリティ識別子を転送先サーバーにコピーするかどうかを選択します。 ログイン転送タスクをデータベース転送タスクと同時に使用する場合、 **[CopySids]** を **[True]** に設定する必要があります。 そのように設定しなかった場合、コピーされたログインは転送されたデータベースで認識されなくなります。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [[ログイン転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)   
 [強力なパスワード](../relational-databases/security/strong-passwords.md)   
 [SQL Server インストールにおけるセキュリティの考慮事項](../../2014/sql-server/install/security-considerations-for-a-sql-server-installation.md)  
  
  
