---
title: SQL Server レプリケーションパブリッシャーのプロパティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.configdistwizard.distpubproperties.f1
- sql12.rep.configdistwizard.pubproperties.general.f1
- sql12.rep.configdistwizard.pubproperties.pubdb.f1
- sql12.rep.configdistwizard.pubproperties.subscribers.f1
ms.assetid: 98df1aea-0406-40bf-a917-4bd80464125c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f3e14f82e855cc29f83859d85dfdaaf85a1bda37
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716253"
---
# <a name="sql-server-replication-publisher-properties"></a>SQL Server レプリケーションパブリッシャーのプロパティ
  ここでは、ディストリビューターおよびパブリッシャーで使用できるパブリッシャープロパティについて説明します。 

## <a name="general"></a>全般  
  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[全般]** ページでは、パブリッシャーが使用するディストリビューターおよびディストリビューション データベースの読み取り専用情報を表示します。 パブリッシャーのディストリビューターまたはディストリビューション データベースを変更するには、次の手順に従います。  
  
1.  パブリッシャーでのパブリッシングを無効にします。 詳細については、「[パブリッシングの無効化と配布](disable-publishing-and-distribution.md)」を参照してください。    
2.  パブリッシングおよびディストリビューションを再構成します。 詳細については、「 [Configure Publishing and Distribution](configure-publishing-and-distribution.md)」をご参照ください。  

## <a name="distributor"></a>ディストリビューター
  **[パブリッシャーのプロパティ]** ダイアログ ボックスを使用すると、パブリッシャーとそのディストリビューター間のリレーションシップに関連するプロパティの表示と修正を行うことができます。  
  
### <a name="options"></a>Options  
 **[パブリッシャーへのエージェント接続]**  
 次のエージェントがディストリビューターからパブリッシャーへの接続を確立するためのコンテキストを指定します。  
  
-   キュー リーダー エージェント (キュー更新サブスクリプションを許可するトランザクション パブリケーション用)  
  
-   スナップショット エージェントとログ リーダー エージェント (Oracle パブリケーション用)  
  
 **[エージェント プロセス アカウントを借用する]** を選択して、これらのエージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用してパブリッシャーへの接続を作成するか、 **[SQL Server 認証]** を指定して、 **[ログイン]** と **[パスワード]** に値を入力します。 **[エージェント プロセス アカウントを借用する]** を選択することをお勧めします。 エージェントのセキュリティの詳細については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」を参照してください。  
  
 これらのエージェントを実行する Windows アカウントは、パブリケーションの新規作成ウィザードで指定します。 これらのアカウントは次のダイアログ ボックスで変更できます。  
  
-   **[ディストリビューターのプロパティ]** ダイアログ ボックス (キュー リーダー エージェント)  
  
-   **[パブリケーションのプロパティ]** ダイアログ ボックス (スナップショット エージェントとログ リーダー エージェント)  
  
 **その他**  
 **[パブリッシャーの種類]** プロパティと **[ディストリビューション データベース名]** プロパティは読み取り専用です。 **[既定のスナップショット フォルダー]** プロパティは変更できます。 スナップショット フォルダーの詳細については、「[スナップショット フォルダーのセキュリティ保護](security/secure-the-snapshot-folder.md)」を参照してください。  
  

## <a name="publication-databases"></a>パブリケーション データベース
  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[パブリケーション データベース]** ページを使用すると、**sysadmin** 固定サーバー ロール内のユーザーはデータベースをレプリケーションに対して有効にすることができます。 データベースを有効にした場合、データベースはパブリッシュされませんが、そのデータベースの **db_owner** 固定データベース ロール内のすべてのユーザーが 1 つ以上のパブリケーションをデータベース上で作成できるようになります。  
  
### <a name="options"></a>Options  
 **トランザクション**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、スナップショット パブリケーションまたはトランザクション パブリケーションをそのデータベースに作成できるようになります。 
  
 **[マージ]**  
 このチェック ボックスをオンにすると、 **db_owner** 固定データベース ロール内のユーザーは、マージ パブリケーションをそのデータベースに作成できるようになります。  

## <a name="subscribers"></a>[サブスクライバー]

  **[パブリッシャーのプロパティ]** ダイアログ ボックスの **[サブスクライバー]** ページは、 以前の [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)][!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が実行されているパブリッシャーで使用します。 このページを使用すると、サブスクライバーがこのパブリッシャー上のパブリケーションからデータを受け取ることができます。 サブスクライバーがこのパブリッシャーからデータを受け取るだけでは、このパブリッシャー上のパブリケーションへのサブスクリプションは作成できません。 サブスクリプションを作成するには、サブスクリプションの新規作成ウィザードを使用します。  
  
### <a name="options"></a>Options  
 **[サブスクライバー]**  
 **[サブスクライバー]** プロパティ グリッドには、このパブリッシャー上のパブリケーションからデータを受け取るように設定されているサブスクライバーが表示されます。 その他のプロパティを表示し、設定するには、サブスクライバーの横にあるプロパティ ボタン (**[...]**) をクリックします。  
  
 **[追加]**  
 サブスクライバーを追加するには、 **[追加]** をクリックしてから、 **[SQL Server サブスクライバーの追加]** または **[SQL Server 以外のサブスクライバーの追加]** をクリックします。  

## <a name="see-also"></a>参照  
 [ディストリビューターとパブリッシャーのプロパティの表示および変更](view-and-modify-distributor-and-publisher-properties.md)   

  
  
