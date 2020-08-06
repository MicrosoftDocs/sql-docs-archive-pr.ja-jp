---
title: '&lt;AgentName&gt; エージェント セキュリティ | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.agentnameagentsecurity.f1
ms.assetid: d34c7ef8-cf77-4ffd-887f-3c4214dfd71e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fc72d4380b4d1980da30b8445596e1919a859e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645560"
---
# <a name="ltagentnamegt-agent-security"></a><span data-ttu-id="38cfc-102">&lt;AgentName&gt; エージェント セキュリティ</span><span class="sxs-lookup"><span data-stu-id="38cfc-102">&lt;AgentName&gt; Agent Security</span></span>
  <span data-ttu-id="38cfc-103">**[\<AgentName> エージェント セキュリティ]** ページを使用すると、ディストリビューション エージェント (トランザクション レプリケーションおよびスナップショット レプリケーションの場合) またはマージ エージェント (マージ レプリケーションの場合) が実行されるアカウントを指定し、レプリケーション トポロジ内のコンピューターへの接続を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-103">The **\<AgentName> Agent Security** page allows you to specify the accounts under which the Distribution Agent (for transactional and snapshot replication) or Merge Agent (for merge replication) run and make connections to the computers in a replication topology.</span></span> <span data-ttu-id="38cfc-104">エージェントで必要とされる権限と、レプリケーション セキュリティの推奨事項については、「[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md)」と「[レプリケーション セキュリティの推奨事項](security/replication-security-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="38cfc-104">For information on permissions required by agents and best practices for replication security, see [Replication Agent Security Model](security/replication-agent-security-model.md) and [Replication Security Best Practices](security/replication-security-best-practices.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="38cfc-105">Options</span><span class="sxs-lookup"><span data-stu-id="38cfc-105">Options</span></span>  
 <span data-ttu-id="38cfc-106">**[ディストリビューション エージェント セキュリティ]** ダイアログ ボックスまたは **[マージ エージェント セキュリティ]** ダイアログ ボックスにアクセスするには、各サブスクライバーの行でプロパティ ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="38cfc-106">Click the properties button (**...**) in the row for each Subscriber to access the **Distribution Agent Security** or **Merge Agent Security** dialog box.</span></span> <span data-ttu-id="38cfc-107">ダイアログ ボックスの **[ヘルプ]** をクリックすると、エージェントによって使用されるアカウントに必要な権限の詳細を参照できます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-107">Click **Help** on the dialog box that is launched for more information on the permissions required for accounts used by the agents.</span></span>  
  
 <span data-ttu-id="38cfc-108">ダイアログ ボックスの 1 つに設定を入力すると、サブスクライバーの接続情報がグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-108">After settings have been entered in one of the dialog boxes, connection information for the Subscriber is displayed in the grid.</span></span>  
  
 <span data-ttu-id="38cfc-109">**[サブスクライバーのエージェント]**</span><span class="sxs-lookup"><span data-stu-id="38cfc-109">**Agent for Subscriber**</span></span>  
 <span data-ttu-id="38cfc-110">各サブスクライバーの名前です。</span><span class="sxs-lookup"><span data-stu-id="38cfc-110">The name of each Subscriber.</span></span>  
  
 <span data-ttu-id="38cfc-111">**[ディストリビューターへの接続]**</span><span class="sxs-lookup"><span data-stu-id="38cfc-111">**Connection to Distributor**</span></span>  
 <span data-ttu-id="38cfc-112">トランザクション レプリケーションおよびスナップショット レプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-112">Displayed for transactional and snapshot replication.</span></span> <span data-ttu-id="38cfc-113">ディストリビューターに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="38cfc-113">The context under which the connection to the Distributor is made.</span></span> <span data-ttu-id="38cfc-114">ローカル接続は常に、エージェントを実行する [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アカウントのコンテキストを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-114">Local connections are always made using the context of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="38cfc-115">プッシュ サブスクリプションの場合、ローカル接続はディストリビューターへの接続であるため、このフィールドには常に次が表示されます。 **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** (プッシュ サブスクリプションの場合)。</span><span class="sxs-lookup"><span data-stu-id="38cfc-115">For push subscriptions, the local connection is the connection to the Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="38cfc-116">プル サブスクリプションの場合、接続は [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-116">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="38cfc-117">このフィールドには、次のいずれかが表示されます。 **[ログイン '\<Login>' を使用する]** 、 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="38cfc-117">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="38cfc-118">では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38cfc-118">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="38cfc-119">**[パブリッシャーおよびディストリビューターへの接続]**</span><span class="sxs-lookup"><span data-stu-id="38cfc-119">**Connection to Publisher & Distributor**</span></span>  
 <span data-ttu-id="38cfc-120">マージ レプリケーションの場合に表示されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-120">Displayed for merge replication.</span></span> <span data-ttu-id="38cfc-121">パブリッシャーおよびディストリビューターに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="38cfc-121">The context under which the connections to the Publisher and Distributor are made.</span></span> <span data-ttu-id="38cfc-122">ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-122">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="38cfc-123">プッシュ サブスクリプションの場合、ローカル接続はパブリッシャーとディストリビューターへの接続であるため、このフィールドには常に次が表示されます。 **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** (プッシュ サブスクリプションの場合)。</span><span class="sxs-lookup"><span data-stu-id="38cfc-123">For push subscriptions, the local connection is the connection to the Publisher and Distributor, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="38cfc-124">プル サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-124">For pull subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="38cfc-125">このフィールドには、次のいずれかが表示されます。 **[ログイン '\<Login>' を使用する]** 、 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="38cfc-125">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="38cfc-126">では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38cfc-126">recommends that all connections be made using the context of the Windows account.</span></span>  
  
 <span data-ttu-id="38cfc-127">**[サブスクライバーへの接続]**</span><span class="sxs-lookup"><span data-stu-id="38cfc-127">**Connection to Subscriber**</span></span>  
 <span data-ttu-id="38cfc-128">サブスクライバーに接続するコンテキストを作成します。</span><span class="sxs-lookup"><span data-stu-id="38cfc-128">The context under which the connection to the Subscriber is made.</span></span> <span data-ttu-id="38cfc-129">ローカル接続は常に、エージェントを実行する Windows アカウントのコンテキストを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-129">Local connections are always made using the context of the Windows account under which the agent runs:</span></span>  
  
-   <span data-ttu-id="38cfc-130">プル サブスクリプションの場合、ローカル接続はサブスクライバーへの接続であるため、このフィールドには常に次が表示されます。 **['\<Domain>\\<Login\>' の権限を借用する]** または **['\<Computer>\\<Login\>' の権限を借用する]** (プッシュ サブスクリプションの場合)。</span><span class="sxs-lookup"><span data-stu-id="38cfc-130">For pull subscriptions, the local connection is the connection to the Subscriber, so this field will always display: **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'** for push subscriptions.</span></span>  
  
-   <span data-ttu-id="38cfc-131">プッシュ サブスクリプションの場合、接続は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインのコンテキストでも作成できます。</span><span class="sxs-lookup"><span data-stu-id="38cfc-131">For push subscriptions, the connection can also be made under the context of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] login.</span></span> <span data-ttu-id="38cfc-132">このフィールドには、次のいずれかが表示されます。 **[ログイン '\<Login>' を使用する]** 、 **['\<Domain>\\<Login\>' の権限を借用する]** 、または **['\<Computer>\\<Login\>' の権限を借用する]** 。</span><span class="sxs-lookup"><span data-stu-id="38cfc-132">The field displays one of the following: **Use login '\<Login>'**, **Impersonate '\<Domain>\\<Login\>'** or **Impersonate '\<Computer>\\<Login\>'**.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="38cfc-133">では、Windows アカウントのコンテキストを使用して、すべての接続を作成することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="38cfc-133">recommends that all connections be made using the context of the Windows account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38cfc-134">参照</span><span class="sxs-lookup"><span data-stu-id="38cfc-134">See Also</span></span>  
 <span data-ttu-id="38cfc-135">[プル サブスクリプションのプロパティの表示または変更](view-and-modify-pull-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="38cfc-135">[View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md) </span></span>  
 <span data-ttu-id="38cfc-136">[プッシュ サブスクリプションのプロパティの表示または変更](view-and-modify-push-subscription-properties.md) </span><span class="sxs-lookup"><span data-stu-id="38cfc-136">[View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) </span></span>  
 <span data-ttu-id="38cfc-137">[レプリケーションのログインとパスワードの管理](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span><span class="sxs-lookup"><span data-stu-id="38cfc-137">[Manage Logins and Passwords in Replication](security/identity-and-access-control-replication.md#manage-logins-and-passwords-in-replication) </span></span>  
 <span data-ttu-id="38cfc-138">[レプリケーション エージェントのセキュリティ モデル](security/replication-agent-security-model.md) </span><span class="sxs-lookup"><span data-stu-id="38cfc-138">[Replication Agent Security Model](security/replication-agent-security-model.md) </span></span>  
 [<span data-ttu-id="38cfc-139">SQL Server レプリケーションのセキュリティ</span><span class="sxs-lookup"><span data-stu-id="38cfc-139">SQL Server Replication Security</span></span>](security/view-and-modify-replication-security-settings.md)  
  
  