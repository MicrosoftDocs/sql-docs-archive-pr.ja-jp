---
title: Web アプリケーションの要件 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9455d3cf-c1b7-4d48-8aff-7dc636ed5dc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fc24095019d19ebcb656a2cccf86621dd78b30b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738496"
---
# <a name="web-application-requirements-master-data-services"></a><span data-ttu-id="aa3cc-102">Web アプリケーションの要件 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-102">Web Application Requirements (Master Data Services)</span></span>
  [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="aa3cc-103">は、インターネット インフォメーション サービス (IIS) によってホストされる Web アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-103">is a web application hosted by Internet Information Services (IIS).</span></span> [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] <span data-ttu-id="aa3cc-104">は Internet Explorer (IE) 7 以降でのみ動作します。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-104">works only in Internet Explorer (IE) 7 or later.</span></span> <span data-ttu-id="aa3cc-105">IE 7 以前のバージョン、Microsoft Edge、Chrome はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-105">IE 7 and earlier versions, Microsoft Edge and Chrome are not supported.</span></span>  
  
 <span data-ttu-id="aa3cc-106">[!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] Web アプリケーションを作成および構成するには、 [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] を使用します。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-106">Use [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] to create and configure the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application.</span></span> [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)] <span data-ttu-id="aa3cc-107">は、ローカル コンピューター上の IIS を構成するので、最初に Web 構成タスクを行う場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-107">configures IIS on the local computer, so it is best for initial web configuration tasks.</span></span> <span data-ttu-id="aa3cc-108">たとえば、1 つの [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションを使用して [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] 環境を構成したり、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)]のスケールアウト配置の最初の Web アプリケーションを構成したりします。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-108">For example, configure a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] environment with a single [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, or configure the first web application in a scale-out deployment of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)].</span></span> <span data-ttu-id="aa3cc-109">スケールアウト配置の複数の Web サーバーの構成など、より複雑なタスクを実行する場合は、IIS ツールを使用します。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-109">Use IIS tools to perform more complex tasks, such as configuring multiple web servers in a scale-out deployment.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3cc-110">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] のコンポーネントをインストールするコンピューターはすべてライセンス供与を受けている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-110">Any computer on which you install components of [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] must be licensed.</span></span> <span data-ttu-id="aa3cc-111">詳細については、使用許諾契約書 (EULA) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-111">For more information, refer to the End User License Agreement (EULA).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa3cc-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="aa3cc-112">Requirements</span></span>  
  
### <a name="operating-system"></a><span data-ttu-id="aa3cc-113">オペレーティング システム</span><span class="sxs-lookup"><span data-stu-id="aa3cc-113">Operating System</span></span>  
 <span data-ttu-id="aa3cc-114">次の Windows オペレーティング システムには、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Web アプリケーションおよび Web サービスに必要なインターネット インフォメーション サービス (IIS) の機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-114">The following Windows operating systems include the Internet Information Services (IIS) functionality required for the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] web application and web service.</span></span>  
  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="aa3cc-115">Developer (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="aa3cc-115">Developer (64-bit) x64</span></span>|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="aa3cc-116">Enterprise (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="aa3cc-116">Enterprise (64-bit) x64</span></span>|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="aa3cc-117">Business Intelligence (64 ビット) x64</span><span class="sxs-lookup"><span data-stu-id="aa3cc-117">Business Intelligence (64-bit) x64</span></span>|  
|-------------------------------------------------------|--------------------------------------------------------|-------------------------------------------------------------------|  
|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="aa3cc-118">SP2</span><span class="sxs-lookup"><span data-stu-id="aa3cc-118">SP2</span></span><br /><br /> <span data-ttu-id="aa3cc-119">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="aa3cc-119">Windows Server 2008 R2 SP1</span></span><br /><br /> <span data-ttu-id="aa3cc-120">Windows 7 Professional、Enterprise、Ultimate</span><span class="sxs-lookup"><span data-stu-id="aa3cc-120">Windows 7 Professional, Enterprise, and Ultimate</span></span><br /><br /> <span data-ttu-id="aa3cc-121">Windows 8.0 Professional、Enterprise、および Ultimate</span><span class="sxs-lookup"><span data-stu-id="aa3cc-121">Windows 8.0 Professional, Enterprise, and Ultimate</span></span>|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="aa3cc-122">SP2</span><span class="sxs-lookup"><span data-stu-id="aa3cc-122">SP2</span></span><br /><br /> <span data-ttu-id="aa3cc-123">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="aa3cc-123">Windows Server 2008 R2 SP1</span></span><br /><br /> <span data-ttu-id="aa3cc-124">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="aa3cc-124">Windows Server 2012</span></span>|[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] <span data-ttu-id="aa3cc-125">SP2</span><span class="sxs-lookup"><span data-stu-id="aa3cc-125">SP2</span></span><br /><br /> <span data-ttu-id="aa3cc-126">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="aa3cc-126">Windows Server 2008 R2 SP1</span></span><br /><br /> <span data-ttu-id="aa3cc-127">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="aa3cc-127">Windows Server 2012</span></span>|  
  
 <span data-ttu-id="aa3cc-128">のエディションでサポートされている Windows オペレーティングシステムの完全な一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-128">For a full list of the Windows operating systems that are supported for your edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
### <a name="microsoft-silverlight"></a><span data-ttu-id="aa3cc-129">Microsoft Silverlight</span><span class="sxs-lookup"><span data-stu-id="aa3cc-129">Microsoft Silverlight</span></span>  
 <span data-ttu-id="aa3cc-130">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] Web アプリケーションで作業するには、Silverlight 5 をクライアント コンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-130">To work in the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application, Silverlight 5 must be installed on the client computer.</span></span> <span data-ttu-id="aa3cc-131">Silverlight の必要なバージョンがない場合、Web アプリケーションで Silverlight を使用する部分に移動したときに、Silverlight をインストールするよう要求されます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-131">If you do not have the required version of Silverlight, you will be prompted to install it when you navigate to an area of the web application that requires it.</span></span> <span data-ttu-id="aa3cc-132">Silverlight 5 は [ここ](https://go.microsoft.com/fwlink/?LinkId=243096)からインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-132">You can install Silverlight 5 from [here](https://go.microsoft.com/fwlink/?LinkId=243096).</span></span>  
  
### <a name="role-and-role-services-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a><span data-ttu-id="aa3cc-133">ロールとロール サービス (Windows Server 2008 または Windows Server 2008 R2、Windows 7 オペレーティング システム)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-133">Role and Role Services (Windows Server 2008 or Windows Server 2008 R2, Windows 7 operating systems)</span></span>  
 <span data-ttu-id="aa3cc-134">Windows Server 2008 R2 では、Microsoft 管理コンソール (MMC) にある **サーバー マネージャー**を使用して、 **Web サーバー (IIS)** ロールと、次に示す必要なロール サービスをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-134">On Windows Server 2008 R2, you can use **Server Manager**, which is available in the Microsoft Management Console (MMC), to install the **Web Server (IIS)** role and the following required role services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3cc-135">[!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] および Windows 7 オペレーティング システムでは、コントロール パネルの **[プログラムと機能]** を使用して、 **[Windows の機能]** ダイアログ ボックスに表示されるこれらのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-135">On [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] and Windows 7 operating systems, use **Programs and Features** in Control Panel to enable these options in the **Windows Features** dialog box.</span></span>  
  
||  
|-|  
|<span data-ttu-id="aa3cc-136">Web サーバー</span><span class="sxs-lookup"><span data-stu-id="aa3cc-136">Web Server</span></span><br /><br /> <span data-ttu-id="aa3cc-137">HTTP 基本機能</span><span class="sxs-lookup"><span data-stu-id="aa3cc-137">Common HTTP Features</span></span><br /><br /> <span data-ttu-id="aa3cc-138">静的なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-138">Static Content</span></span><br /><br /> <span data-ttu-id="aa3cc-139">既定のドキュメント</span><span class="sxs-lookup"><span data-stu-id="aa3cc-139">Default Document</span></span><br /><br /> <span data-ttu-id="aa3cc-140">ディレクトリの参照</span><span class="sxs-lookup"><span data-stu-id="aa3cc-140">Directory Browsing</span></span><br /><br /> <span data-ttu-id="aa3cc-141">HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="aa3cc-141">HTTP Errors</span></span><br /><br /> <span data-ttu-id="aa3cc-142">アプリケーション開発</span><span class="sxs-lookup"><span data-stu-id="aa3cc-142">Application Development</span></span><br /><br /> <span data-ttu-id="aa3cc-143">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="aa3cc-143">ASP.NET</span></span><br /><br /> <span data-ttu-id="aa3cc-144">.NET 拡張機能</span><span class="sxs-lookup"><span data-stu-id="aa3cc-144">.NET Extensibility</span></span><br /><br /> <span data-ttu-id="aa3cc-145">ISAPI 拡張</span><span class="sxs-lookup"><span data-stu-id="aa3cc-145">ISAPI Extensions</span></span><br /><br /> <span data-ttu-id="aa3cc-146">ISAPI フィルター</span><span class="sxs-lookup"><span data-stu-id="aa3cc-146">ISAPI Filters</span></span><br /><br /> <span data-ttu-id="aa3cc-147">状態と診断</span><span class="sxs-lookup"><span data-stu-id="aa3cc-147">Health and Diagnostics</span></span><br /><br /> <span data-ttu-id="aa3cc-148">HTTP ログ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-148">HTTP Logging</span></span><br /><br /> <span data-ttu-id="aa3cc-149">要求の監視</span><span class="sxs-lookup"><span data-stu-id="aa3cc-149">Request Monitor</span></span><br /><br /> <span data-ttu-id="aa3cc-150">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-150">Security</span></span><br /><br /> <span data-ttu-id="aa3cc-151">Windows 認証</span><span class="sxs-lookup"><span data-stu-id="aa3cc-151">Windows Authentication</span></span><br /><br /> <span data-ttu-id="aa3cc-152">要求フィルター</span><span class="sxs-lookup"><span data-stu-id="aa3cc-152">Request Filtering</span></span><br /><br /> <span data-ttu-id="aa3cc-153">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-153">Performance</span></span><br /><br /> <span data-ttu-id="aa3cc-154">静的なコンテンツの圧縮</span><span class="sxs-lookup"><span data-stu-id="aa3cc-154">Static Content Compression</span></span><br /><br /> <span data-ttu-id="aa3cc-155">管理ツール</span><span class="sxs-lookup"><span data-stu-id="aa3cc-155">Management Tools</span></span><br /><br /> <span data-ttu-id="aa3cc-156">IIS 管理コンソール</span><span class="sxs-lookup"><span data-stu-id="aa3cc-156">IIS Management Console</span></span>|  
  
### <a name="role-and-role-services-windows-server-2012-or-windows-8-operating-systems"></a><span data-ttu-id="aa3cc-157">ロールとロール サービス (Windows Server 2012 または Windows 8 オペレーティング システム)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-157">Role and Role Services (Windows Server 2012 or Windows 8 operating systems)</span></span>  
 <span data-ttu-id="aa3cc-158">Windows Server 2012 では、Microsoft 管理コンソール (MMC) にある **サーバー マネージャー**を使用して、 **Web サーバー (IIS)** ロールと、次に示す必要なロール サービスをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-158">On Windows Server 2012, you can use **Server Manager**, which is available in the Microsoft Management Console (MMC), to install the **Web Server (IIS)** role and the following required role services.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3cc-159">Windows 8 オペレーティング システムでは、コントロール パネルの **[プログラムと機能]** を使用して、 **[Windows の機能]** ダイアログ ボックスに表示されるこれらのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-159">On the Windows 8 operating system, use **Programs and Features** in Control Panel to enable these options in the **Windows Features** dialog box.</span></span>  
  
||  
|-|  
|<span data-ttu-id="aa3cc-160">インターネット インフォメーション サービス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-160">Internet Information Services</span></span><br /><br /> <span data-ttu-id="aa3cc-161">Web 管理ツール</span><span class="sxs-lookup"><span data-stu-id="aa3cc-161">Web Management Tools</span></span><br /><br /> <span data-ttu-id="aa3cc-162">IIS 管理コンソール</span><span class="sxs-lookup"><span data-stu-id="aa3cc-162">IIS Management Console</span></span><br /><br /> <span data-ttu-id="aa3cc-163">World Wide Web サービス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-163">World Wide Web Services</span></span><br /><br /> <span data-ttu-id="aa3cc-164">アプリケーション開発</span><span class="sxs-lookup"><span data-stu-id="aa3cc-164">Application Development</span></span><br /><br /> <span data-ttu-id="aa3cc-165">.NET Extensibility 3.5</span><span class="sxs-lookup"><span data-stu-id="aa3cc-165">.NET Extensibility 3.5</span></span><br /><br /> <span data-ttu-id="aa3cc-166">.NET Extensibility 4.5</span><span class="sxs-lookup"><span data-stu-id="aa3cc-166">.NET Extensibility 4.5</span></span><br /><br /> <span data-ttu-id="aa3cc-167">ASP.NET 3.5</span><span class="sxs-lookup"><span data-stu-id="aa3cc-167">ASP.NET 3.5</span></span><br /><br /> <span data-ttu-id="aa3cc-168">ASP.NET 4.5</span><span class="sxs-lookup"><span data-stu-id="aa3cc-168">ASP.NET 4.5</span></span><br /><br /> <span data-ttu-id="aa3cc-169">ISAPI 拡張</span><span class="sxs-lookup"><span data-stu-id="aa3cc-169">ISAPI Extensions</span></span><br /><br /> <span data-ttu-id="aa3cc-170">ISAPI フィルター</span><span class="sxs-lookup"><span data-stu-id="aa3cc-170">ISAPI Filters</span></span><br /><br /> <span data-ttu-id="aa3cc-171">HTTP 基本機能</span><span class="sxs-lookup"><span data-stu-id="aa3cc-171">Common HTTP Features</span></span><br /><br /> <span data-ttu-id="aa3cc-172">既定のドキュメント</span><span class="sxs-lookup"><span data-stu-id="aa3cc-172">Default Document</span></span><br /><br /> <span data-ttu-id="aa3cc-173">ディレクトリの参照</span><span class="sxs-lookup"><span data-stu-id="aa3cc-173">Directory Browsing</span></span><br /><br /> <span data-ttu-id="aa3cc-174">HTTP エラー</span><span class="sxs-lookup"><span data-stu-id="aa3cc-174">HTTP Errors</span></span><br /><br /> <span data-ttu-id="aa3cc-175">静的なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-175">Static Content</span></span><br /><br /> <span data-ttu-id="aa3cc-176">[注: WebDAV 発行はインストールしないでください]</span><span class="sxs-lookup"><span data-stu-id="aa3cc-176">[Note: Do not install WebDAV Publishing]</span></span><br /><br /> <span data-ttu-id="aa3cc-177">状態と診断</span><span class="sxs-lookup"><span data-stu-id="aa3cc-177">Health and Diagnostics</span></span><br /><br /> <span data-ttu-id="aa3cc-178">HTTP ログ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-178">HTTP Logging</span></span><br /><br /> <span data-ttu-id="aa3cc-179">要求の監視</span><span class="sxs-lookup"><span data-stu-id="aa3cc-179">Request Monitor</span></span><br /><br /> <span data-ttu-id="aa3cc-180">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-180">Performance</span></span><br /><br /> <span data-ttu-id="aa3cc-181">静的なコンテンツの圧縮</span><span class="sxs-lookup"><span data-stu-id="aa3cc-181">Static Content Compression</span></span><br /><br /> <span data-ttu-id="aa3cc-182">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="aa3cc-182">Security</span></span><br /><br /> <span data-ttu-id="aa3cc-183">要求フィルター</span><span class="sxs-lookup"><span data-stu-id="aa3cc-183">Request Filtering</span></span><br /><br /> <span data-ttu-id="aa3cc-184">Windows 認証</span><span class="sxs-lookup"><span data-stu-id="aa3cc-184">Windows Authentication</span></span>|  
  
### <a name="features-windows-server-2008-or-windows-server-2008-r2-windows-7-operating-systems"></a><span data-ttu-id="aa3cc-185">機能 (Windows Server 2008 または Windows Server 2008 R2、Windows 7 オペレーティング システム)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-185">Features (Windows Server 2008 or Windows Server 2008 R2, Windows 7 operating systems)</span></span>  
 <span data-ttu-id="aa3cc-186">[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] または Windows Server 2008 R2 では、 **サーバー マネージャー** を使用して、次に示す必要な機能をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-186">On [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] or Windows Server 2008 R2, you can use **Server Manager** to install the following required features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3cc-187">[!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] および Windows 7 オペレーティング システムでは、コントロール パネルの **[プログラムと機能]** を使用して、 **[Windows の機能]** ダイアログ ボックスに表示されるこれらのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-187">On [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] and Windows 7 operating systems, use **Programs and Features** in Control Panel to enable these options in the **Windows Features** dialog box.</span></span>  
  
||  
|-|  
|<span data-ttu-id="aa3cc-188">.NET Framework 3.0 の機能</span><span class="sxs-lookup"><span data-stu-id="aa3cc-188">.NET Framework 3.0 Features</span></span><br /><br /> <span data-ttu-id="aa3cc-189">WCF アクティブ化</span><span class="sxs-lookup"><span data-stu-id="aa3cc-189">WCF Activation</span></span><br /><br /> <span data-ttu-id="aa3cc-190">HTTP アクティブ化</span><span class="sxs-lookup"><span data-stu-id="aa3cc-190">HTTP Activation</span></span><br /><br /> <span data-ttu-id="aa3cc-191">非 HTTP アクティブ化</span><span class="sxs-lookup"><span data-stu-id="aa3cc-191">Non-HTTP Activation</span></span><br /><br /> <span data-ttu-id="aa3cc-192">Windows プロセス アクティブ化サービス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-192">Windows Process Activation Service</span></span><br /><br /> <span data-ttu-id="aa3cc-193">プロセス モデル</span><span class="sxs-lookup"><span data-stu-id="aa3cc-193">Process Model</span></span><br /><br /> <span data-ttu-id="aa3cc-194">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="aa3cc-194">.NET Environment</span></span><br /><br /> <span data-ttu-id="aa3cc-195">構成 API</span><span class="sxs-lookup"><span data-stu-id="aa3cc-195">Configuration APIs</span></span>|  
  
### <a name="features-windows-server-2012-or-windows-8-operating-systems"></a><span data-ttu-id="aa3cc-196">機能 (Windows Server 2012 または Windows 8 オペレーティング システム)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-196">Features (Windows Server 2012 or Windows 8 operating systems)</span></span>  
 <span data-ttu-id="aa3cc-197">Windows Server 2012 では、 **サーバー マネージャー** を使用して、次に示す必要な機能をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-197">On Windows Server 2012, you can use **Server Manager** to install the following required features.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="aa3cc-198">Windows 8 オペレーティング システムでは、コントロール パネルの **[プログラムと機能]** を使用して、 **[Windows の機能]** ダイアログ ボックスに表示されるこれらのオプションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-198">On the Windows 8 operating system, use **Programs and Features** in Control Panel to enable these options in the **Windows Features** dialog box.</span></span>  
  
||  
|-|  
|<span data-ttu-id="aa3cc-199">.NET Framework 3.5 (.NET 2.0 および 3.0 を含む)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-199">.NET Framework 3.5 (includes .NET 2.0 and 3.0)</span></span><br /><br /> <span data-ttu-id="aa3cc-200">.NET Framework 4.5 Advanced Services</span><span class="sxs-lookup"><span data-stu-id="aa3cc-200">.NET Framework 4.5 Advanced Services</span></span><br /><br /> <span data-ttu-id="aa3cc-201">ASP.NET 4.5</span><span class="sxs-lookup"><span data-stu-id="aa3cc-201">ASP.NET 4.5</span></span><br /><br /> <span data-ttu-id="aa3cc-202">WCF サービス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-202">WCF Services</span></span><br /><br /> <span data-ttu-id="aa3cc-203">HTTP アクティブ化 [注: これは必須です。]</span><span class="sxs-lookup"><span data-stu-id="aa3cc-203">HTTP Activation [Note: This is required.]</span></span><br /><br /> <span data-ttu-id="aa3cc-204">TCP ポート共有</span><span class="sxs-lookup"><span data-stu-id="aa3cc-204">TCP Port Sharing</span></span><br /><br /> <span data-ttu-id="aa3cc-205">Windows プロセス アクティブ化サービス</span><span class="sxs-lookup"><span data-stu-id="aa3cc-205">Windows Process Activation Service</span></span><br /><br /> <span data-ttu-id="aa3cc-206">プロセス モデル</span><span class="sxs-lookup"><span data-stu-id="aa3cc-206">Process Model</span></span><br /><br /> <span data-ttu-id="aa3cc-207">.NET 環境</span><span class="sxs-lookup"><span data-stu-id="aa3cc-207">.NET Environment</span></span><br /><br /> <span data-ttu-id="aa3cc-208">構成 API</span><span class="sxs-lookup"><span data-stu-id="aa3cc-208">Configuration APIs</span></span>|  
  
### <a name="accounts-and-permissions"></a><span data-ttu-id="aa3cc-209">アカウントと権限</span><span class="sxs-lookup"><span data-stu-id="aa3cc-209">Accounts and Permissions</span></span>  
  
|<span data-ttu-id="aa3cc-210">Type</span><span class="sxs-lookup"><span data-stu-id="aa3cc-210">Type</span></span>|<span data-ttu-id="aa3cc-211">説明</span><span class="sxs-lookup"><span data-stu-id="aa3cc-211">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="aa3cc-212">Windows アカウント</span><span class="sxs-lookup"><span data-stu-id="aa3cc-212">Windows account</span></span>|<span data-ttu-id="aa3cc-213">Windows のロール、ロール サービス、および機能を構成し、ローカル コンピューター上の IIS にあるアプリケーション プール、Web サイト、および Web アプリケーションを作成して管理する権限がある Windows アカウントを使用して Web サーバー コンピューターにログオンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-213">You must log on to the web server computer with a Windows account that has permission to configure Windows roles, role services, and features, and to create and manage application pools, web sites, and web applications in IIS on the local computer.</span></span>|  
|<span data-ttu-id="aa3cc-214">サービス アカウント</span><span class="sxs-lookup"><span data-stu-id="aa3cc-214">Service account</span></span>|<span data-ttu-id="aa3cc-215">[!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] で [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)]Web アプリケーションを作成するときは、アプリケーションが実行されるアプリケーション プールの ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-215">When you create the [!INCLUDE[ssMDSmdm](../../includes/ssmdsmdm-md.md)] web application in [!INCLUDE[ssMDScfgmgr](../../includes/ssmdscfgmgr-md.md)], you must specify an identity for the application pool that the application runs in.</span></span> <span data-ttu-id="aa3cc-216">このアカウントは、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースの作成時に指定したサービス アカウントと異なっていてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-216">This account can be different from the service account that was specified when the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database was created.</span></span><br /><br /> <span data-ttu-id="aa3cc-217">この ID はドメイン ユーザー アカウントである必要があり、データベースにアクセスするために [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] データベースの mds_exec データベース ロールに追加されます。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-217">This identity must be a domain user account, and it is added to the mds_exec database role in the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] database for database access.</span></span> <span data-ttu-id="aa3cc-218">詳細については、「[データベース ログイン、ユーザー、およびロール &#40;マスター データ サービス&#41;](../database-logins-users-and-roles-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-218">For more information, see [Database Logins, Users, and Roles &#40;Master Data Services&#41;](../database-logins-users-and-roles-master-data-services.md).</span></span> <span data-ttu-id="aa3cc-219">また、このアカウントは、 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Windows グループ **MDS_ServiceAccounts**にも追加されます。このグループには、ファイル システムの一時コンパイル ディレクトリ **MDSTempDir**に対する権限が与えられています。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-219">This account is also added to a [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] Windows group, **MDS_ServiceAccounts**, which is granted permission to the temporary compilation directory, **MDSTempDir**, in the file system.</span></span> <span data-ttu-id="aa3cc-220">詳細については、「[フォルダーとファイルの権限 &#40;マスター データ サービス&#41;](../folder-and-file-permissions-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-220">For more information, see [Folder and File Permissions &#40;Master Data Services&#41;](../folder-and-file-permissions-master-data-services.md).</span></span><br /><br /> <span data-ttu-id="aa3cc-221">サーバーのエラーを回避するには、アプリケーション プール アカウントに VIEW SERVER STATE 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-221">The application pool account needs the VIEW SERVER STATE permission, to avoid server errors.</span></span> <span data-ttu-id="aa3cc-222">たとえば、MDS Validate Version コマンドはサーバー エラーで失敗します。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-222">For example, the MDS Validate Version command fails with a server error.</span></span> <span data-ttu-id="aa3cc-223">詳細については、「 [SQL Server 2012 および SQL Server 2014 で MDS Validate Version コマンドがサーバー エラーで失敗する](https://go.microsoft.com/fwlink/p/?LinkId=526304)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa3cc-223">For more information, see [MDS Validate Version command fails with a server error in SQL Server 2012 and SQL Server 2014](https://go.microsoft.com/fwlink/p/?LinkId=526304)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa3cc-224">参照</span><span class="sxs-lookup"><span data-stu-id="aa3cc-224">See Also</span></span>  
 <span data-ttu-id="aa3cc-225">[マスターデータサービスのインストール](install-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa3cc-225">[Install Master Data Services](install-master-data-services.md) </span></span>  
 <span data-ttu-id="aa3cc-226">[マスターデータマネージャー Web アプリケーション &#40;マスターデータサービスを作成する&#41;](create-a-master-data-manager-web-application-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="aa3cc-226">[Create a Master Data Manager Web Application &#40;Master Data Services&#41;](create-a-master-data-manager-web-application-master-data-services.md) </span></span>  
 <span data-ttu-id="aa3cc-227">[[Web の構成] ページ &#40;マスター データ サービス構成マネージャー&#41;](../web-configuration-page-master-data-services-configuration-manager.md)</span><span class="sxs-lookup"><span data-stu-id="aa3cc-227">[Web Configuration Page &#40;Master Data Services Configuration Manager&#41;](../web-configuration-page-master-data-services-configuration-manager.md)</span></span>  
  
  