---
title: ネイティブ モードのレポート サーバーに対するアクセス許可の許可 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 22967a7c9c6b8cc3e14ecffed117d1ab821788f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644828"
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a><span data-ttu-id="6bd62-102">ネイティブ モードのレポート サーバーに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="6bd62-102">Granting Permissions on a Native Mode Report Server</span></span>
  <span data-ttu-id="6bd62-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では、ロールベースの承認および認証サブシステムを使用して、操作の実行およびレポート サーバーのアイテムへのアクセスを行えるユーザーを決定します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses role-based authorization and an authentication subsystem to determine who can perform operations and access items on a report server.</span></span> <span data-ttu-id="6bd62-104">ロールベースの承認では、ユーザーまたはグループが実行できる一連のアクションがロールに分類されます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-104">Role-based authorization categorizes into roles the set of actions that a user or group can perform.</span></span> <span data-ttu-id="6bd62-105">認証は、組み込みの Windows 認証、または指定したカスタム認証モジュールに基づいて行われます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-105">Authentication is based on built-in Windows Authentication or a custom authentication module that you provide.</span></span> <span data-ttu-id="6bd62-106">どちらの種類の認証でも、定義済みロールまたはカスタム ロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-106">You can use predefined or custom roles with either authentication type.</span></span>  
  
## <a name="using-roles-to-grant-report-server-access"></a><span data-ttu-id="6bd62-107">ロールを使用したレポート サーバーへのアクセス許可</span><span class="sxs-lookup"><span data-stu-id="6bd62-107">Using Roles to Grant Report Server Access</span></span>  
 <span data-ttu-id="6bd62-108">すべてのユーザーは、特定のレベルのアクセスを定義するロールのコンテキスト内でレポート サーバーと対話します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-108">All users interact with a report server within the context of a role that defines a specific level of access.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6bd62-109">には、レポート サーバーにすぐにアクセスできるように、ユーザーおよびグループに割り当てることのできる定義済みロールが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6bd62-109">includes predefined roles that you can assign to users and groups to provide immediate access to a report server.</span></span> <span data-ttu-id="6bd62-110">**コンテンツ マネージャー**、 **パブリッシャー**、および **閲覧者** は、定義済みロールの例です。</span><span class="sxs-lookup"><span data-stu-id="6bd62-110">**ContentManager**, **Publisher**, and **Browser** are examples of predefined roles.</span></span> <span data-ttu-id="6bd62-111">各ロールでは、関連するタスクのコレクションを定義します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-111">Each role defines a collection of related tasks.</span></span> <span data-ttu-id="6bd62-112">たとえば、 **パブリッシャー** には、レポートを追加して、そのレポートを格納するフォルダーを作成する権限があります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-112">For example, a **Publisher** has permission to add reports and create folders for storing those reports.</span></span>  
  
 <span data-ttu-id="6bd62-113">通常、ロールの割り当ては親ノードから継承されますが、特定のアイテムに対する新しいロールの割り当てを作成することで権限の継承を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-113">Role assignments are typically inherited from a parent node, but you can break permission inheritance by creating a new role assignment for a particular item.</span></span> <span data-ttu-id="6bd62-114">あるレポートの **コンテンツ マネージャー** ロールのメンバーは、別のレポートの **閲覧者** ロールのメンバーである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-114">A user who is a member of the **Content Manager** role for one report may be a member of the **Browser** role for another report.</span></span>  
  
 <span data-ttu-id="6bd62-115">レポート サーバーのアイテムおよび操作へのアクセスを許可するには、次のガイドラインに従います。</span><span class="sxs-lookup"><span data-stu-id="6bd62-115">To grant access to report server items and operations, follow these guidelines:</span></span>  
  
1.  <span data-ttu-id="6bd62-116">定義済みロールを確認して、これらのロールをそのまま使用できるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-116">Review the predefined roles to determine whether you can use them as is.</span></span> <span data-ttu-id="6bd62-117">タスクを調整したり追加のロールを定義したりする必要がある場合は、この手順を実行してから、ユーザーを特定のロールに割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-117">If you need to adjust the tasks or define additional roles, you should do this before you begin assigning users to specific roles.</span></span> <span data-ttu-id="6bd62-118">各ロールの詳細については、「 [定義済みロール](role-definitions-predefined-roles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd62-118">For more information about each role, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
2.  <span data-ttu-id="6bd62-119">レポート サーバーへのアクセス権を必要とするユーザーやグループ、およびそのレベルを特定します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-119">Identify which users and groups require access to the report server, and at what level.</span></span> <span data-ttu-id="6bd62-120">**閲覧者** ロールまたは **レポート ビルダー** ロールには、大半のユーザーを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-120">Most users should be assigned to the **Browser** role or the **Report Builder** role.</span></span> <span data-ttu-id="6bd62-121">**パブリッシャー** ロールには、少数のユーザーしか割り当てる必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6bd62-121">A smaller number of users should be assigned to the **Publisher** role.</span></span> <span data-ttu-id="6bd62-122">また、 **コンテンツ マネージャー**に割り当てる必要があるのは、ごく限られたユーザーです。</span><span class="sxs-lookup"><span data-stu-id="6bd62-122">Very few users should be assigned to **Content Manager**.</span></span>  
  
3.  <span data-ttu-id="6bd62-123">レポート マネージャーを使用して、[ホーム] フォルダー (レポート サーバーのフォルダー階層の最上位フォルダー) で、アクセス権を必要とする各ユーザーまたはグループにロールを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-123">Use Report Manager to assign roles on the Home folder (this is the top-level folder of the report server folder hierarchy) for each user or group who requires access.</span></span>  
  
4.  <span data-ttu-id="6bd62-124">サイト レベルでは、レポート マネージャーの [サイトの設定] ページで、 **システム ユーザー** および **システム管理者**という定義済みロールを使用して、各ユーザーまたはグループにシステムレベルのロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-124">At the site level, on the Site Settings page in Report Manager, create a system-level role assignment for each user and group using the predefined roles **System User** and **System Administrator**.</span></span>  
  
5.  <span data-ttu-id="6bd62-125">特定のフォルダー、レポートなどのアイテムに対し、必要に応じて、追加のロールの割り当てを作成します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-125">Create additional role assignments as needed for specific folders, reports, and other items.</span></span> <span data-ttu-id="6bd62-126">ロールの割り当てを作成しすぎないようにします。</span><span class="sxs-lookup"><span data-stu-id="6bd62-126">Avoid creating a large number of role assignments.</span></span> <span data-ttu-id="6bd62-127">作成したロールの割り当てが多すぎると、各ユーザーの権限レベルが多岐にわたり、追跡が困難になります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-127">If you create too many, it will be difficult to keep track of the different permission levels for each user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6bd62-128">SharePoint 統合モードで実行するようにレポート サーバーを構成した場合、SharePoint サイトに対する権限を、レポート サーバー アイテムへのアクセスを許可するように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-128">If you configured a report server to run in SharePoint integrated mode, you must set permissions on the SharePoint site to grant access to report server items.</span></span> <span data-ttu-id="6bd62-129">詳細については、「 [SharePoint サイトのレポート サーバー アイテムに対する権限の付与](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd62-129">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
## <a name="who-sets-permissions"></a><span data-ttu-id="6bd62-130">権限の設定者</span><span class="sxs-lookup"><span data-stu-id="6bd62-130">Who Sets Permissions</span></span>  
 <span data-ttu-id="6bd62-131">初期状態では、レポート サーバーにアクセスできるのは、ローカルの Administrators グループのメンバーであるユーザーだけです。</span><span class="sxs-lookup"><span data-stu-id="6bd62-131">Initially, only users who are members of the local administrators group can access a report server.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="6bd62-132">は、ローカルの Administrators グループのメンバーにアイテムレベルおよびシステムレベルのアクセスを許可する 2 つの既定のロールの割り当てと共にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-132">is installed with two default role assignments that grant item-level and system-level access to members of the local administrators group.</span></span> <span data-ttu-id="6bd62-133">ローカル管理者は、これらの組み込みのロールの割り当てを使用して、レポートサーバーへのアクセスを他のユーザーに許可したり、レポートサーバーアイテムを管理したりできます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-133">Local Administrators can use these built-in role assignments to grant report server access to other users and manage report server items.</span></span> <span data-ttu-id="6bd62-134">組み込みのロールの割り当ては削除できません。</span><span class="sxs-lookup"><span data-stu-id="6bd62-134">The built-in role assignments cannot be deleted.</span></span> <span data-ttu-id="6bd62-135">ローカル管理者は、常に、レポート サーバー インスタンスを完全に管理する権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="6bd62-135">A local administrator always has permission to fully manage a report server instance.</span></span>  
 
 <span data-ttu-id="6bd62-136">Windows Vista または Windows Server 2008 を実行しているローカル コンピューター上のレポート サーバー インスタンスを管理するには、追加の構成が必要となります。</span><span class="sxs-lookup"><span data-stu-id="6bd62-136">Additional configuration is required before you can administer a report server instance on a local computer that runs Windows Vista or Windows Server 2008.</span></span> <span data-ttu-id="6bd62-137">詳細については、「 [ローカル管理用のネイティブ モードのレポート サーバー &#40;SSRS&#41; の構成](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd62-137">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="how-permissions-are-stored"></a><span data-ttu-id="6bd62-138">権限が格納されるしくみ</span><span class="sxs-lookup"><span data-stu-id="6bd62-138">How Permissions are Stored</span></span>  
 <span data-ttu-id="6bd62-139">ロールの割り当てと定義はレポート サーバー データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-139">Role assignments and definitions are stored in the report server database.</span></span> <span data-ttu-id="6bd62-140">さまざまなクライアント ツールやプログラム インターフェイスを使用している場合、すべてのアクセスは、レポート サーバー インスタンス全体を対象として定義されている権限に従います。</span><span class="sxs-lookup"><span data-stu-id="6bd62-140">If you are using variety of client tools or programmatic interfaces, all access is subject to the permissions that are defined for the report server instance as a whole.</span></span> <span data-ttu-id="6bd62-141">スケールアウト配置で複数のレポート サーバーを構成している場合、あるインスタンスで定義したロールの割り当ては共有データベースに格納され、同じスケールアウト配置内のその他すべてのインスタンスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-141">If you are configuring multiple report servers in a scale-out-deployment, the role assignments that you define on one instance are stored in a shared database and used by all the other instances in the same scale-out deployment.</span></span> <span data-ttu-id="6bd62-142">ロールの割り当てはセキュリティで保護されているアイテムと共に格納されるので、定義した権限を維持したまま、データベースを別のレポート サーバーに移動することができます。</span><span class="sxs-lookup"><span data-stu-id="6bd62-142">Because role assignments are stored with the items they secure, you can move the database to another report server instance without losing the permissions you defined.</span></span>  
  
## <a name="tasks-and-tools-for-managing-permissions"></a><span data-ttu-id="6bd62-143">権限を管理するためのタスクとツール</span><span class="sxs-lookup"><span data-stu-id="6bd62-143">Tasks and tools for Managing Permissions</span></span>  
 <span data-ttu-id="6bd62-144">ロールの定義と割り当てを管理するには、次のツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-144">Use the following tools to manage role definitions and assignments.</span></span>  
  
|<span data-ttu-id="6bd62-145">ツール</span><span class="sxs-lookup"><span data-stu-id="6bd62-145">Tool</span></span>|<span data-ttu-id="6bd62-146">タスク</span><span class="sxs-lookup"><span data-stu-id="6bd62-146">Tasks</span></span>|  
|----------|-----------|  
|<span data-ttu-id="6bd62-147">Management Studio - ロールの定義を表示、変更、作成、および削除する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-147">Management Studio - Used to view, modify, create, and delete role definitions.</span></span>|[<span data-ttu-id="6bd62-148">ロールを作成、削除、または変更する (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="6bd62-148">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](role-definitions-create-delete-or-modify.md)|  
|<span data-ttu-id="6bd62-149">レポート マネージャー - ユーザーおよびグループをロールに割り当てる場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="6bd62-149">Report Manager - Used to assign users and groups to roles.</span></span>|[<span data-ttu-id="6bd62-150">レポート サーバーへのユーザー アクセスを許可する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="6bd62-150">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](grant-user-access-to-a-report-server.md)<br /><br /> [<span data-ttu-id="6bd62-151">ロールの割り当てを変更または削除する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="6bd62-151">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a><span data-ttu-id="6bd62-152">参照</span><span class="sxs-lookup"><span data-stu-id="6bd62-152">See Also</span></span>  
 <span data-ttu-id="6bd62-153">[定義済みロール](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="6bd62-153">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="6bd62-154">[SharePoint サイト上のレポートサーバーアイテムに対する権限の許可](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="6bd62-154">[Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="6bd62-155">[レポート サーバーでの認証](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="6bd62-155">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="6bd62-156">(create-and-manage-role-assignments.md)</span><span class="sxs-lookup"><span data-stu-id="6bd62-156">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="6bd62-157">[Reporting Services のセキュリティと保護](reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="6bd62-157">[Reporting Services Security and Protection](reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="6bd62-158">レポート サーバー コンテンツの管理 &#40;SSRS ネイティブ モード&#41;</span><span class="sxs-lookup"><span data-stu-id="6bd62-158">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  