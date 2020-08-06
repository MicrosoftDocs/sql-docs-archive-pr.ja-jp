---
title: 拡張機能のセキュリティに関する考慮事項 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- security [Reporting Services], extensions
- extensions [Reporting Services], security
- permissions [Reporting Services], extensions
ms.assetid: 58cbdfeb-1105-4a7d-a3b8-b897ff95f367
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e7819f4d6de2003c9982d33ab00cfa0d4030aa36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645398"
---
# <a name="security-considerations-for-extensions"></a><span data-ttu-id="fce55-102">拡張機能のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="fce55-102">Security Considerations for Extensions</span></span>
  <span data-ttu-id="fce55-103">共通言語ランタイム (CLR) をターゲットとするすべてのアプリケーションは、CLR セキュリティ システムと対話する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fce55-103">Every application that targets the common language runtime (CLR) must interact with the CLR security system.</span></span> <span data-ttu-id="fce55-104">このようなアプリケーションを実行すると、CLR によってアプリケーションが自動的に評価され、権限のセットが付与されます。</span><span class="sxs-lookup"><span data-stu-id="fce55-104">When such an application runs, it is automatically evaluated and given a set of permissions by the CLR.</span></span> <span data-ttu-id="fce55-105">アプリケーションに付与された権限に応じて、実行が継続されるかセキュリティ例外が生成されます。</span><span class="sxs-lookup"><span data-stu-id="fce55-105">Depending on the permissions that the application receives, it either continues running or generates a security exception.</span></span> <span data-ttu-id="fce55-106">特定のレポート サーバーのセキュリティ ポリシー構成ファイルのローカル セキュリティ設定とポリシーによって、アセンブリが受け取るコード権限が定義されます。</span><span class="sxs-lookup"><span data-stu-id="fce55-106">The local security settings and policies in the security policy configuration files for a particular report server define the code permissions that an assembly receives.</span></span>  
  
 <span data-ttu-id="fce55-107">権限を要求する前に、拡張コードが使用するリソースと保護された操作を認識すると共に、そのリソースと操作を保護する権限について知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="fce55-107">Before requesting permissions, you need to be aware of the resources and protected operations your extension code is planning to use, and you also need to know which permissions protect those resources and operations.</span></span> <span data-ttu-id="fce55-108">拡張機能コンポーネントによって呼び出されるクラス ライブラリ メソッドがアクセスするリソースを継続的に追跡することも必要です。</span><span class="sxs-lookup"><span data-stu-id="fce55-108">In addition, you need to keep track of any resources accessed by any class library methods that are called by the extension components.</span></span> <span data-ttu-id="fce55-109">詳細については、『[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 開発者ガイド』の「アクセス許可の要求」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fce55-109">For more information, see "Requesting Permissions" in the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
 <span data-ttu-id="fce55-110">レポート サーバーに配置される拡張機能は、完全に信頼されて実行する必要があります。つまり、拡張機能は **FullTrust** アクセス許可セットを付与されたコード グループの一部である必要があります。</span><span class="sxs-lookup"><span data-stu-id="fce55-110">Extensions deployed to a report server must run as fully trusted, meaning that your extension needs to be part of a code group that is granted the **FullTrust** permission set.</span></span> <span data-ttu-id="fce55-111">これは、特定のレポートに対してユーザーが承認されているかどうかに応じて、CLR を通して使用できる特定のサーバー リソースと操作に、拡張機能がアクセス権を持つことができることも意味します。</span><span class="sxs-lookup"><span data-stu-id="fce55-111">This also means that your extension may have access to certain server resources and operations available through the CLR depending on the user that is being authenticated for a particular report.</span></span> <span data-ttu-id="fce55-112">コード グループと拡張機能の詳細については、「[Reporting Services のコード アクセス セキュリティ](secure-development/code-access-security-in-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fce55-112">For more information about code groups and extensions, see [Code Access Security in Reporting Services](secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="fce55-113">は、その拡張機能のすべてに [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] セキュリティを適用します。</span><span class="sxs-lookup"><span data-stu-id="fce55-113">enforces [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security for all of its extensions.</span></span>  
  
 <span data-ttu-id="fce55-114">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のデータ処理、配信、表示、およびセキュリティの各拡張機能の配置には、次の条件が適用されます。</span><span class="sxs-lookup"><span data-stu-id="fce55-114">The following conditions apply to the deployment of data processing, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="fce55-115">ローカル管理者のみが拡張機能を配置する権限を持ちます。</span><span class="sxs-lookup"><span data-stu-id="fce55-115">Only the local administrator has permission to deploy an extension.</span></span>  
  
-   <span data-ttu-id="fce55-116">適切な読み取りおよび書き込み権限を持つユーザーのみが、拡張する [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] コンポーネントの構成ファイルを変更できます。</span><span class="sxs-lookup"><span data-stu-id="fce55-116">Only users with the appropriate read/write permissions can change the configuration files for the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] component that is being extended.</span></span>  
  
-   <span data-ttu-id="fce55-117">特権ユーザーのみが、セキュリティ ポリシー ファイルを編集して拡張機能のコード アクセス セキュリティを有効にする権限を持ちます。</span><span class="sxs-lookup"><span data-stu-id="fce55-117">Only privileged users have permission to edit the security policy files and enable code access security for an extension.</span></span>  
  
 <span data-ttu-id="fce55-118">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のコード アクセス セキュリティの詳細については、「[セキュリティで保護された配置 &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fce55-118">For more information about code access security in [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], see [Secure Development &#40;Reporting Services&#41;](secure-development/secure-development-reporting-services.md).</span></span>  
  
 <span data-ttu-id="fce55-119">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] セキュリティの詳細については、『[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 開発者ガイド』の「.NET Framework セキュリティ」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fce55-119">For more information about [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] security, see ".NET Framework Security" in your [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Developer's Guide.</span></span>  
  
## <a name="initialization-of-extension-assemblies"></a><span data-ttu-id="fce55-120">拡張機能アセンブリの初期化</span><span class="sxs-lookup"><span data-stu-id="fce55-120">Initialization of Extension Assemblies</span></span>  
 <span data-ttu-id="fce55-121">レポート サーバーで拡張機能を最初にメモリに読み込むときに、サービス アカウントの資格情報が使用されます。一部の拡張機能アセンブリでは、システム リソースへのアクセス、構成ファイルの読み込み、およびその他の依存するアセンブリの読み込みに特定の権限が必要であるためです。</span><span class="sxs-lookup"><span data-stu-id="fce55-121">When extensions are first loaded into memory by the report server, they use the service account credentials, because some extension assemblies require specific permissions to access system resources, to read configuration files, and to load other, dependent assemblies.</span></span> <span data-ttu-id="fce55-122">ただし、アセンブリが読み込まれ、初期化された後は、拡張機能アセンブリのすべての呼び出しに、現在ログオンしているユーザー アカウントの資格情報が使用されます。</span><span class="sxs-lookup"><span data-stu-id="fce55-122">After an assembly has been loaded and initialized, however, all subsequent calls to extension assemblies use the credentials of the user account that is currently logged on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fce55-123">参照</span><span class="sxs-lookup"><span data-stu-id="fce55-123">See Also</span></span>  
 <span data-ttu-id="fce55-124">[Reporting Services の拡張機能](reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="fce55-124">[Reporting Services Extensions](reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="fce55-125">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="fce55-125">Reporting Services Extension Library</span></span>](reporting-services-extension-library.md)  
  
  