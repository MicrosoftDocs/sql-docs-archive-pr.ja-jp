---
title: データマイニングサービスとデータソース |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b26fd6e3-7d87-4f66-ab47-5303b51b87da
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4b86ff2603e58210a66e7b40401ff8da7c938b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643636"
---
# <a name="data-mining-services-and-data-sources"></a><span data-ttu-id="3df0c-102">データ マイニング サービスおよびデータ ソース</span><span class="sxs-lookup"><span data-stu-id="3df0c-102">Data Mining Services and Data Sources</span></span>
  <span data-ttu-id="3df0c-103">データ マイニングでは、SQL Server Analysis Services のインスタンスへの接続が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-103">Data mining requires a connection to an instance of SQL Server Analysis Services.</span></span> <span data-ttu-id="3df0c-104">キューブからのデータは、データ マイニングには必須ではなく、リレーショナル ソースの使用をお勧めします。ただし、データ マイニングでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] エンジンによって提供されるコンポーネントが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-104">Data from a cube is not required for data mining and the use of relational sources is recommended; however, data mining uses components provided by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] engine.</span></span>  
  
 <span data-ttu-id="3df0c-105">このトピックには、データ マイニング モデルの作成、処理、配置、またはクエリのために SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスに接続する際に知っておく必要がある情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3df0c-105">This topic provides information that you need to know when connecting to an instance of SQL Server [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to create, process, deploy, or query data mining models.</span></span>  
  
## <a name="data-mining-services"></a><span data-ttu-id="3df0c-106">データ マイニング サービス</span><span class="sxs-lookup"><span data-stu-id="3df0c-106">Data Mining Services</span></span>  
 <span data-ttu-id="3df0c-107">のサーバーコンポーネント [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は msmdsrv.exe アプリケーションであり、通常は Windows サービスとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-107">The server component of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is the msmdsrv.exe application, which ordinarily runs as a Windows service.</span></span> <span data-ttu-id="3df0c-108">このアプリケーションは、セキュリティ コンポーネント、XML for Analysis (XMLA) リスナー コンポーネント、クエリ プロセッサ コンポーネント、および次の機能を実行するその他多くの内部コンポーネントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="3df0c-108">This application consists of security components, an XML for Analysis (XMLA) listener component, a query processor component and numerous other internal components that perform the following functions:</span></span>  
  
-   <span data-ttu-id="3df0c-109">クライアントから受信したステートメントの解析</span><span class="sxs-lookup"><span data-stu-id="3df0c-109">Parsing statements received from clients</span></span>  
  
-   <span data-ttu-id="3df0c-110">メタデータの管理</span><span class="sxs-lookup"><span data-stu-id="3df0c-110">Managing metadata</span></span>  
  
-   <span data-ttu-id="3df0c-111">トランザクションの処理</span><span class="sxs-lookup"><span data-stu-id="3df0c-111">Handling transactions</span></span>  
  
-   <span data-ttu-id="3df0c-112">計算の処理</span><span class="sxs-lookup"><span data-stu-id="3df0c-112">Processing calculations</span></span>  
  
-   <span data-ttu-id="3df0c-113">ディメンションおよびセル データの格納</span><span class="sxs-lookup"><span data-stu-id="3df0c-113">Storing dimension and cell data</span></span>  
  
-   <span data-ttu-id="3df0c-114">集計の作成</span><span class="sxs-lookup"><span data-stu-id="3df0c-114">Creating aggregations</span></span>  
  
-   <span data-ttu-id="3df0c-115">クエリのスケジュール設定</span><span class="sxs-lookup"><span data-stu-id="3df0c-115">Scheduling queries</span></span>  
  
-   <span data-ttu-id="3df0c-116">オブジェクトのキャッシュ</span><span class="sxs-lookup"><span data-stu-id="3df0c-116">Caching objects</span></span>  
  
-   <span data-ttu-id="3df0c-117">サーバー リソースの管理</span><span class="sxs-lookup"><span data-stu-id="3df0c-117">Managing server resources</span></span>  
  
### <a name="xmla-listener"></a><span data-ttu-id="3df0c-118">XMLA リスナー</span><span class="sxs-lookup"><span data-stu-id="3df0c-118">XMLA Listener</span></span>  
 <span data-ttu-id="3df0c-119">XMLA リスナー コンポーネントでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] とそのクライアントの間のすべての XMLA 通信が処理されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-119">The XMLA listener component handles all XMLA communications between [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and its clients.</span></span> <span data-ttu-id="3df0c-120">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Port` msmdsrv.ini ファイルの構成設定を使用して、インスタンスがリッスンするポートを指定でき [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-120">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `Port` configuration setting in the msmdsrv.ini file can be used to specify a port on which an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance listens.</span></span> <span data-ttu-id="3df0c-121">このファイルの 0 の値は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が既定のポートをリッスンすることを示します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-121">A value of 0 in this file indicates that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] listen on the default port.</span></span> <span data-ttu-id="3df0c-122">特に指定がなければ、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では次の既定の TCP ポートが使用されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-122">Unless otherwise specified, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] uses the following default TCP ports:</span></span>  
  
|<span data-ttu-id="3df0c-123">Port</span><span class="sxs-lookup"><span data-stu-id="3df0c-123">Port</span></span>|<span data-ttu-id="3df0c-124">説明</span><span class="sxs-lookup"><span data-stu-id="3df0c-124">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="3df0c-125">2383</span><span class="sxs-lookup"><span data-stu-id="3df0c-125">2383</span></span>|<span data-ttu-id="3df0c-126">の既定のインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3df0c-126">Default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="3df0c-127">2382</span><span class="sxs-lookup"><span data-stu-id="3df0c-127">2382</span></span>|<span data-ttu-id="3df0c-128">の他のインスタンスのリダイレクター [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3df0c-128">Redirector for other instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
|<span data-ttu-id="3df0c-129">サーバーの起動時に動的に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-129">Dynamically assigned at server startup</span></span>|<span data-ttu-id="3df0c-130">の名前付きインスタンス [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3df0c-130">Named instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|  
  
 <span data-ttu-id="3df0c-131">このサービスが使用するポートを制御する方法の詳細については、「 [Analysis Services のアクセスを許可するための Windows ファイアウォールの構成](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-131">For more information about controlling the ports used by this service, see [Configure the Windows Firewall to Allow Analysis Services Access](../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md).</span></span>  
  
## <a name="connecting-to-data-sources"></a><span data-ttu-id="3df0c-132">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="3df0c-132">Connecting to Data Sources</span></span>  
 <span data-ttu-id="3df0c-133">データ マイニング構造やデータ マイニング モデルを作成したり更新したりする際には、データ ソースで定義されているデータを使用します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-133">Whenever you create or update a data mining structure or model, you use data that is defined by a data source.</span></span> <span data-ttu-id="3df0c-134">データ ソースには、Excel ブック、テキスト ファイル、SQL Server データベースなどのデータは含まれていません。接続情報が定義されているだけです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-134">The data source does not contain the data, which might include Excel workbooks, text files, and SQL Server databases; it only defines the connection information.</span></span>  <span data-ttu-id="3df0c-135">データ ソース ビュー (DSV) は、そのソース上の抽象化レイヤーとして機能し、ソースから取得されるデータの変更やマップを行います。</span><span class="sxs-lookup"><span data-stu-id="3df0c-135">A data source view (DSV) serves as an abstraction layer on top of that source, modifying or mapping the data that is obtained from the source.</span></span>  
  
 <span data-ttu-id="3df0c-136">これらの各ソースの接続要件については、このトピックでは説明していません。</span><span class="sxs-lookup"><span data-stu-id="3df0c-136">It is beyond the scope of this topic to describe the connection requirements for each of these sources.</span></span> <span data-ttu-id="3df0c-137">詳細については、プロバイダーのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-137">For more information, see the documentation for the provider.</span></span> <span data-ttu-id="3df0c-138">ただし、一般には、プロバイダーとのやり取りで、Analysis Services の次の要件に注意してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-138">However, in general, you should be aware of the following requirements of Analysis Services, when interacting with providers:</span></span>  
  
-   <span data-ttu-id="3df0c-139">データ マイニングはサーバーによって提供されるサービスなので、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスはデータ ソースへのアクセスを許可されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-139">Because data mining is a service provided by a server, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance must be given access to the data source.</span></span>  <span data-ttu-id="3df0c-140">アクセスには、場所とユーザー情報という、2 つの側面があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-140">There are two aspects to access: location and identity.</span></span>  
  
     <span data-ttu-id="3df0c-141">**場所** に関して問題になるのは、自分のコンピューターだけに格納されているデータを使用してモデルを作成し、それをサーバーに配置した場合、データ ソースが見つからないためにモデルの処理が失敗することです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-141">**Location** means that, if you build a model using data that is stored only on your computer and then deploy the model to a server, the model would fail to process because the data source cannot be found.</span></span> <span data-ttu-id="3df0c-142">この問題を解決するには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が実行されている同じ SQL Server インスタンスにデータを転送するか、ファイルを共有の場所に移動することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-142">To resolve this problem, you might need to transfer data into the same SQL Server instance where [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is running, or move files to a shared location.</span></span>  
  
     <span data-ttu-id="3df0c-143">**ユーザー情報** に関して問題になるのは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 上のサービスが適切な資格情報でデータ ファイルまたはデータ ソースを開くことができる必要があることです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-143">**Identity** means that the services on [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] must be able to open the data file or data source with the appropriate credentials.</span></span> <span data-ttu-id="3df0c-144">たとえば、モデルの作成者はデータを表示するための無制限の権限を持っているとしても、サーバー上のモデルを処理および更新するユーザーはデータへのアクセスが制限または禁止されている場合があるため、モデルのコンテンツの処理や変更が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-144">For example, when you built the model, you might have had unlimited permissions to view the data, but the user who is processing and updating the models on the server might have limited or no access to the data, which can cause failure to process or affect the contents of a model.</span></span> <span data-ttu-id="3df0c-145">少なくとも、リモート データ ソースへの接続に使用されるアカウントは、データの読み取り権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-145">At minimum, the account used for connecting to the remote data source must have read permissions to the data.</span></span>  
  
-   <span data-ttu-id="3df0c-146">モデルを移動するときには、同じ要件が適用されます。元のデータ ソースの場所への適切なアクセスをセットアップするか、データ ソースをコピーするか、新しいデータ ソースを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-146">When you move a model, the same requirements apply: you must set up appropriate access to the location of the old data source, copy the data sources, or configure a new data source.</span></span> <span data-ttu-id="3df0c-147">また、ログインおよびロールを転送するか、データ マイニング オブジェクトを新しい場所で処理および更新できるように権限をセットアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-147">Also, you must transfer logins and roles, or set up permissions to allow data mining objects to be processed and updated in the new location.</span></span>  
  
## <a name="configuring-permissions-and-server-properties"></a><span data-ttu-id="3df0c-148">権限とサーバー プロパティの構成</span><span class="sxs-lookup"><span data-stu-id="3df0c-148">Configuring Permissions and Server Properties</span></span>  
 <span data-ttu-id="3df0c-149">データ マイニングには、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに対する追加の権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="3df0c-149">Data mining requires additional permissions on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="3df0c-150">ほとんどのデータ マイニング プロパティは、[[分析サーバーのプロパティ] ダイアログ ボックス &#40;Analysis Services&#41;](../analysis-server-properties-dialog-box-analysis-services.md) を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-150">Most data mining properties can be set by using the [Analysis Server Properties Dialog Box &#40;Analysis Services&#41;](../analysis-server-properties-dialog-box-analysis-services.md).</span></span>  
  
 <span data-ttu-id="3df0c-151">構成できるプロパティの詳細については、「 [Analysis Services でのサーバープロパティの構成](../server-properties/server-properties-in-analysis-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-151">For more information about the properties that you can configure, see [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="3df0c-152">データ マイニングに関連するサーバー プロパティを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-152">The following server properties are of particular relevance to data mining:</span></span>  
  
-   <span data-ttu-id="3df0c-153">`AllowAdHocOpenRowsetQueries`サーバーのメモリ領域に直接読み込まれる OLE DB プロバイダーへのアドホックアクセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-153">`AllowAdHocOpenRowsetQueries` Controls ad hoc access to OLE DB providers, which are loaded directly into server memory space.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="3df0c-154">セキュリティを強化するため、このプロパティは `false` に設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3df0c-154">To improve security, we recommend that you set this property to `false`.</span></span> <span data-ttu-id="3df0c-155">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="3df0c-155">The default value is `false`.</span></span> <span data-ttu-id="3df0c-156">このプロパティが `false` に設定されていても、ユーザーは単一クエリを作成したり、許可されているデータ ソースに対して OPENQUERY を使用したりできます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-156">However, even if this property is set to `false`, users can continue to create singleton queries, and can use OPENQUERY on permitted data sources.</span></span>  
  
-   <span data-ttu-id="3df0c-157">**AllowedProvidersInOpenRowset** アドホック アクセスが有効な場合にプロバイダーを指定します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-157">**AllowedProvidersInOpenRowset** Specifies the provider, if ad hoc access is enabled.</span></span> <span data-ttu-id="3df0c-158">ProgID のコンマ区切りのリストを入力することにより、複数のプロバイダーを指定できます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-158">You can specify multiple providers, by entering a comma-separated list of ProgIDs.</span></span>  
  
-   <span data-ttu-id="3df0c-159">**MaxConcurrentPredictionQueries** 予測によるサーバーの負荷を制御します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-159">**MaxConcurrentPredictionQueries** Controls the load on the server caused by predictions.</span></span> <span data-ttu-id="3df0c-160">既定値は 0 で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise ではクエリが制限されず、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard では同時実行クエリが 5 つまで許可されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-160">The default value of 0 allows unlimited queries for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Enterprise, and a maximum of five concurrent queries for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Standard.</span></span> <span data-ttu-id="3df0c-161">制限を超えたクエリはシリアル化され、タイムアウトすることがあります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-161">Queries above the limit are serialized and may time out.</span></span>  
  
 <span data-ttu-id="3df0c-162">サーバーにはこの他に、使用できるデータ マイニング アルゴリズム (およびアルゴリズムに対する制限) や、すべてのデータ マイニング サービスの既定値を制御するプロパティもあります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-162">The server provides additional properties that control which data mining algorithms are available, including any restrictions on the algorithms, and the defaults for all data mining services.</span></span> <span data-ttu-id="3df0c-163">ただし、データ マイニング ストアド プロシージャへのアクセスを制御できる設定はありません。</span><span class="sxs-lookup"><span data-stu-id="3df0c-163">However, there are no settings that allow you to control access to data mining stored procedures specifically.</span></span> <span data-ttu-id="3df0c-164">詳細については、「 [データ マイニング プロパティ](../server-properties/data-mining-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-164">For more information, see [Data Mining Properties](../server-properties/data-mining-properties.md).</span></span>  
  
 <span data-ttu-id="3df0c-165">そのほか、サーバーをチューニングしたりクライアントの利用に関するセキュリティを制御したりするためのプロパティを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-165">You can also set properties that let you tune the server and control security for client usage.</span></span> <span data-ttu-id="3df0c-166">詳細については、「 [機能プロパティ](../server-properties/feature-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-166">For more information, see [Feature Properties](../server-properties/feature-properties.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3df0c-167">の各エディションによるプラグインアルゴリズムのサポートの詳細につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 () の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="3df0c-167">For more information about Support for plug-in algorithms by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="programmatic-access-to-data-mining-objects"></a><span data-ttu-id="3df0c-168">データ マイニング オブジェクトへのプログラムによるアクセス</span><span class="sxs-lookup"><span data-stu-id="3df0c-168">Programmatic Access to Data Mining Objects</span></span>  
 <span data-ttu-id="3df0c-169">以下のオブジェクト モデルを使用して、Analysis Services データベースへの接続を作成し、データ マイニング オブジェクトを操作できます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-169">You can use the following object models to create a connection to an Analysis Services database and work with data mining objects:</span></span>  
  
 <span data-ttu-id="3df0c-170">**ADO** OLE DB を使用して Analysis Services サーバーに接続します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-170">**ADO** Uses OLE DB to connect to an Analysis Services server.</span></span> <span data-ttu-id="3df0c-171">ADO を使用する場合は、クライアントがスキーマ行セットのクエリと DMX ステートメントのみに制限されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-171">When you use ADO, the client is limited to schema rowset queries and DMX statements.</span></span>  
  
 <span data-ttu-id="3df0c-172">**ADO.NET** 特に SQL Server プロバイダーとのやり取りに適しています。</span><span class="sxs-lookup"><span data-stu-id="3df0c-172">**ADO.NET** Interacts with SQL Server providers better than other providers.</span></span> <span data-ttu-id="3df0c-173">データ アダプターを使用して動的な行セットを格納したり、</span><span class="sxs-lookup"><span data-stu-id="3df0c-173">Uses data adaptors to store dynamic rowsets.</span></span> <span data-ttu-id="3df0c-174">データセット オブジェクトを使用したりできます。データセット オブジェクトは、XML として更新したり保存したりできるデータ テーブルとして格納されるサーバー データのキャッシュです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-174">Uses the dataset object, which is a cache of the server data stored as data tables that can be updated or saved as XML.</span></span>  
  
 <span data-ttu-id="3df0c-175">**ADOMD.NET** データ マイニングと OLAP の操作に最適化されたマネージド データ プロバイダーです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-175">**ADOMD.NET** A managed data provider that is optimized for working with data mining and OLAP.</span></span> <span data-ttu-id="3df0c-176">ADOMD.NET は ADO.NET より高速で、メモリ効率も ADO.NET より優れています。</span><span class="sxs-lookup"><span data-stu-id="3df0c-176">ADOMD.NET is faster and more memory-efficient than ADO.NET.</span></span> <span data-ttu-id="3df0c-177">サーバー オブジェクトに関するメタデータを取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-177">ADOMD.NET also lets you retrieve metadata about server objects.</span></span> <span data-ttu-id="3df0c-178">クライアント アプリケーションでは、.NET が使用できない場合以外は ADOMD.NET を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="3df0c-178">Recommended for client applications except when .NET is not available.</span></span>  
  
 <span data-ttu-id="3df0c-179">**Server ADOMD** サーバー上で直接 Analysis Services オブジェクトにアクセスするためのオブジェクト モデルです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-179">**Server ADOMD** Object model for accessing Analysis Services objects directly on the server.</span></span> <span data-ttu-id="3df0c-180">Analysis Services ストアド プロシージャで使用されます。クライアントでは使用しません。</span><span class="sxs-lookup"><span data-stu-id="3df0c-180">Used by Analysis Services stored procedures; not for client use.</span></span>  
  
 <span data-ttu-id="3df0c-181">**AMO** Decision Support オブジェクト (DSO) に代わる Analysis Services 用の管理インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-181">**AMO** Management interface for Analysis Services that replaces Decision Support Objects (DSO).</span></span> <span data-ttu-id="3df0c-182">オブジェクトの繰り返し処理などの操作では、他のインターフェイスを使用する場合に比べて高い権限が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-182">Operations such as iterating objects require higher permissions when using AMO than when using other interfaces.</span></span> <span data-ttu-id="3df0c-183">これは、AMO が直接メタデータにアクセスするためです。ADOMD.NET などの他のインターフェイスがアクセスするのはデータベース スキーマだけです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-183">That is because AMO accesses metadata directly, whereas ADOMD.NET and other interfaces access only the database schemas.</span></span>  
  
### <a name="browse-and-query-access-to-servers"></a><span data-ttu-id="3df0c-184">サーバーへの参照およびクエリ アクセス</span><span class="sxs-lookup"><span data-stu-id="3df0c-184">Browse and Query Access to Servers</span></span>  
 <span data-ttu-id="3df0c-185">OLAP/データ マイニング モードの Analysis Services のインスタンスを使用して、すべての種類の予測を実行できます。ただし、次の制限があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-185">You can perform all kinds of predictions by using a instance of Analysis Services in OLAP/Data Mining mode, with the following restrictions:</span></span>  
  
-   <span data-ttu-id="3df0c-186">Server ADOMD を使用する場合は、接続を作成せずに DMX を使用してサーバーにアクセスし、</span><span class="sxs-lookup"><span data-stu-id="3df0c-186">If you use server ADOMD, you can use DMX to access the server without making a connection.</span></span> <span data-ttu-id="3df0c-187">結果を直接データ テーブルにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-187">You can then copy the results directly into a data table.</span></span> <span data-ttu-id="3df0c-188">ただし、リモート インスタンスでは Server ADOMD は使用できません。クエリを実行できるのはローカル サーバーだけです。</span><span class="sxs-lookup"><span data-stu-id="3df0c-188">However, you cannot use Server ADOMD with remote instances; you can query only the local server.</span></span>  
  
-   <span data-ttu-id="3df0c-189">ADO.NET は、データ マイニングの名前付きパラメーターをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="3df0c-189">ADO.NET does not support named parameters for data mining.</span></span> <span data-ttu-id="3df0c-190">ADOMD.NET を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-190">You must use ADOMD.NET.</span></span>  
  
-   <span data-ttu-id="3df0c-191">ADOMD.NET では、テーブル全体をパラメーターとして渡すことができます。したがって、クライアント側のデータ (サーバーからは使用できないデータ) を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-191">ADOMD.NET lets you pass an entire table to use as the parameter; therefore, you can use data on the client, or data that is unavailable to the server.</span></span> <span data-ttu-id="3df0c-192">形が指定されたテーブルを予測の入力として使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-192">You can also use shaped tables as prediction input.</span></span>  
  
### <a name="using-data-mining-stored-procedures"></a><span data-ttu-id="3df0c-193">データ マイニング ストアド プロシージャの使用</span><span class="sxs-lookup"><span data-stu-id="3df0c-193">Using Data Mining Stored Procedures</span></span>  
 <span data-ttu-id="3df0c-194">ストアド プロシージャは、クエリを再利用に向けてカプセル化するために使用されるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="3df0c-194">A common use of stored procedures is to encapsulate queries for reuse.</span></span> <span data-ttu-id="3df0c-195">クライアントでは、CALL を使用してストアド プロシージャ ( [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のシステム ストアド プロシージャを含む) を実行できます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-195">The client can use CALL to run stored procedures, including [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] system stored procedures.</span></span>  
  
 <span data-ttu-id="3df0c-196">プロシージャがデータセットを返した場合、クライアントは、行を含む入れ子になったテーブルを持つデータセットまたはデータ テーブルを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-196">If the procedure returns a dataset, the client will receive a dataset or datatable with a nested table containing the rows.</span></span> <span data-ttu-id="3df0c-197">たとえば、モデル コンテンツに対するクエリを作成すると、そのクエリではモデル全体が返されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-197">For example, if you create a query against the model content, the query returns the entire model.</span></span> <span data-ttu-id="3df0c-198">あまり多くの行が返されないようにするには、ADOMD+ オブジェクト モデルを使用してストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="3df0c-198">To avoid bringing back too many rows, you can write stored procedures by using the ADOMD+ object model.</span></span>  
  
 <span data-ttu-id="3df0c-199">サーバー ストアド プロシージャを記述するには、Microsoft.AnalysisServices.AdomdServer 名前空間を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-199">To write a server stored procedure, you must reference the Microsoft.AnalysisServices.AdomdServer namespace.</span></span> <span data-ttu-id="3df0c-200">ストアド プロシージャを作成および使用する方法の詳細については、「 [ユーザー定義関数およびストアド プロシージャ](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3df0c-200">For more information about how to create and use stored procedures, see [User Defined Functions and Stored Procedures](https://docs.microsoft.com/analysis-services/adomd/multidimensional-models-adomd-net-server/user-defined-functions-and-stored-procedures).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3df0c-201">ストアド プロシージャを使用してデータ サーバー オブジェクトのセキュリティを変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3df0c-201">Stored procedures cannot be used to change security on data server objects.</span></span> <span data-ttu-id="3df0c-202">ストアド プロシージャの実行時には、ユーザーの現在のコンテキストを使用してすべてのサーバー オブジェクトへのアクセスが決定されます。</span><span class="sxs-lookup"><span data-stu-id="3df0c-202">When you execute a stored procedure, the user's current context is used to determine access to all server objects.</span></span> <span data-ttu-id="3df0c-203">したがって、ユーザーは、アクセスするすべてのデータベース オブジェクトに対する適切な権限を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3df0c-203">Therefore, users must have appropriate permissions on any database objects that they access.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df0c-204">参照</span><span class="sxs-lookup"><span data-stu-id="3df0c-204">See Also</span></span>  
 <span data-ttu-id="3df0c-205">[物理アーキテクチャ &#40;Analysis Services-多次元データ&#41;](../multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="3df0c-205">[Physical Architecture &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-physical/understanding-microsoft-olap-physical-architecture.md) </span></span>  
 <span data-ttu-id="3df0c-206">[物理アーキテクチャ &#40;Analysis Services-データマイニング&#41;](physical-architecture-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="3df0c-206">[Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="3df0c-207">データ マイニング ソリューションおよびオブジェクトの管理</span><span class="sxs-lookup"><span data-stu-id="3df0c-207">Management of Data Mining Solutions and Objects</span></span>](management-of-data-mining-solutions-and-objects.md)  
  
  