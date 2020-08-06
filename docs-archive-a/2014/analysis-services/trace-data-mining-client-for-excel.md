---
title: トレース (Excel 用のデータマイニングクライアント) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tracer
- connections
ms.assetid: 4aea3e17-cd0f-48dd-8f22-b54a6c716426
author: minewiskan
ms.author: owend
ms.openlocfilehash: 74e1a5be21aa6981ccefa76f7bb1892d8d517be5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738773"
---
# <a name="trace-data-mining-client-for-excel"></a><span data-ttu-id="a2b4e-102">トレース (Excel 用のデータ マイニング クライアント)</span><span class="sxs-lookup"><span data-stu-id="a2b4e-102">Trace (Data Mining Client for Excel)</span></span>
  <span data-ttu-id="a2b4e-103">![[トレース] ボタン](media/misc-trace.gif "[トレース] ボタン")</span><span class="sxs-lookup"><span data-stu-id="a2b4e-103">![Trace button](media/misc-trace.gif "Trace button")</span></span>

 <span data-ttu-id="a2b4e-104">[**トレーサー** ] ダイアログボックスは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データマイニングに使用しているのインスタンスに送信されるステートメントを監視するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-104">The **Tracer** dialog box helps you monitor the statements that are sent to the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you are using for data mining.</span></span> <span data-ttu-id="a2b4e-105">のインスタンスへの接続を作成すると [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 、クライアントとサーバー間のすべての対話が [**トレーサー** ] ペインに記録されます。これには、構造を作成したり、マイニングモデルを追加したり、予測を行ったり、サーバーから返されるメッセージを含めます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-105">After you have created a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], all interactions between the client and the server are logged in the **Tracer** pane, including statements that create structures, add mining models, and make predictions, as well as some messages returning from the server.</span></span>

 <span data-ttu-id="a2b4e-106">要求されるアクションに応じて、ステートメントは、データ マイニング拡張機能 (DMX) のデータ定義クエリやデータ操作クエリ、Analysis Services スクリプト言語 (ASSL) パケット、または Analysis Services ストアド プロシージャの呼び出しになります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-106">Depending on the action that is requested, the statement might be a Data Mining Extensions (DMX) data definition query or data manipulation query, an Analysis Services Scripting Language (ASSL) packet, or a call to an Analysis Services stored procedure.</span></span> <span data-ttu-id="a2b4e-107">ただし、実際の数値で表される結果やデータ値は表示されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-107">Actual numerical results and data values are not shown, however.</span></span>

 <span data-ttu-id="a2b4e-108">**トレース**は現在の接続のみを監視し、[**トレーサー** ] ダイアログボックスの内容は保存されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-108">**Trace** monitors only the current connection, and the contents of the **Tracer** dialog box are not stored.</span></span>

## <a name="options"></a><span data-ttu-id="a2b4e-109">Options</span><span class="sxs-lookup"><span data-stu-id="a2b4e-109">Options</span></span>
 <span data-ttu-id="a2b4e-110">[トレーサー] ペインには、Excel クライアントからサーバーに送信されるすべてのステートメントが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-110">Tracer pane Lists all statements sent from the Excel client to the server.</span></span>

 <span data-ttu-id="a2b4e-111">要求されるアクションに応じて、ステートメントは、DMX データ操作ステートメントやデータ定義ステートメント、Analysis Services ストアド プロシージャの呼び出し、または XML/A パケットになります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-111">Depending on the action that is being requested, the statement might be a DMX data manipulation or data definition statement, a call to an Analysis Services stored procedure, or an XML/A packet.</span></span>

 <span data-ttu-id="a2b4e-112">**現在の接続**現在の接続の定義を表示する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-112">**Current Connection** Click to display the definition of the current connection.</span></span> <span data-ttu-id="a2b4e-113">定義には、接続の名前、プロバイダー、データ ソース、カタログ、トランザクションのために接続が最後に使用された時間、および現在の状態 ([オープン]、[非アクティブ]) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-113">The definition includes the name of the connection, the provider, data source, and catalog, the time the connection was last used for a transaction, and the current state (Open, Inactive).</span></span>

 <span data-ttu-id="a2b4e-114">**セッションモデルを使用する**データマイニングモデルおよび構造を一時オブジェクトとしてサーバーに格納する場合は、このチェックボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-114">**Use session models** Select this check box to store data mining models and structures as temporary objects on the server.</span></span> <span data-ttu-id="a2b4e-115">作成するモデルと構造は、現在のセッションが確立されている間のみ使用可能となります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-115">The models and structures that you create will be available only for the duration of the current session.</span></span>

 <span data-ttu-id="a2b4e-116">モデルまたは構造を Analysis Services サーバーに格納する場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-116">Deselect this option to save your models or structures by storing them on an Analysis Services server.</span></span>

 <span data-ttu-id="a2b4e-117">**メモ**一時オブジェクトを使用する機能は、Excel 用のテーブル分析ツールを使用している場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-117">**Note** The ability to use temporary objects is available only when you are using the Table Analysis Tools for Excel.</span></span> <span data-ttu-id="a2b4e-118">Visio データ マイニング テンプレートおよび Excel 用のデータ マイニング クライアントでは、構造とモデルをサーバーに格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-118">The Visio Data Mining templates and the Data Mining Client for Excel require structures and models to be stored on the server.</span></span>

## <a name="tracing-temporary-structures-and-models"></a><span data-ttu-id="a2b4e-119">一時的な構造およびモデルのトレース</span><span class="sxs-lookup"><span data-stu-id="a2b4e-119">Tracing Temporary Structures and Models</span></span>
 <span data-ttu-id="a2b4e-120">テーブル分析ツールを使用する場合、既定では一時的な構造およびモデルが作成されます。この場合、サーバーとクライアントの間のアクティビティは監視されますが、作成されたモデルまたは構造はサーバーに永続的には保存されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-120">If you are using the Table Analysis Tools, which by default create temporary structures and models, the activity between the server and the client is monitored, but the models or structures that you create are not saved permanently to the server.</span></span>

 <span data-ttu-id="a2b4e-121">いずれかのテーブル分析ツールを使用して作業を保持する場合は、[**セッションモデルを使用**する] オプションをオフにして、モデルをサーバーに永続的に保存することができます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-121">If you want to preserve your work when using one of the Table Analysis Tools, you can deselect the option, **Use session models**, to cause your models to be permanently saved on the server.</span></span> <span data-ttu-id="a2b4e-122">また、[**トレーサー** ] ペインのステートメントをファイルにコピーして、後で作業を再作成できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-122">You can also copy the statements in the **Tracer** pane to a file so that you can re-create your work later.</span></span>

## <a name="understanding-sessions"></a><span data-ttu-id="a2b4e-123">セッションについて</span><span class="sxs-lookup"><span data-stu-id="a2b4e-123">Understanding Sessions</span></span>
 <span data-ttu-id="a2b4e-124">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスに接続すると、データ マイニング アドインによりセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-124">When you connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], the data mining add-in initiates a session.</span></span> <span data-ttu-id="a2b4e-125">それぞれのセッションは、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンス上の既存のセッションを識別するセッション識別子を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-125">Each session receives a session identifier that identifies an existing session on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="a2b4e-126">ただし、セッション識別子は、セッションが有効であることを保証するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-126">However, a session identifier does not guarantee that a session remains valid.</span></span> <span data-ttu-id="a2b4e-127">セッションは、タイムアウトした場合やセッションに関連付けられた接続が解除された場合に期限切れとなります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-127">The session can expire if the session times out or the connection associated with the session is disconnected.</span></span> <span data-ttu-id="a2b4e-128">セッションが期限切れとなり有効でなくなった場合、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] は、セッションを終了し、進行中のトランザクションをロールバックします。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-128">If the session expires and is no longer valid, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ends the session and rolls back any transactions that are in process.</span></span> <span data-ttu-id="a2b4e-129">無効になったセッション識別子でメッセージを送信した場合は、指定したセッションが見つからないことを示すエラーが発生して、そのメッセージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-129">If a message is sent with a session identifier that is no longer valid, the message fails with an error indicating that the specified session cannot be found.</span></span>

 <span data-ttu-id="a2b4e-130">一部のデータ マイニング モデルはサーバー上に明示的に格納されますが、セッション マイニング モデルおよび構造は格納されず、セッション データ マイニング アクティビティのレコードも保存されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-130">Although some data mining models are explicitly stored on the server, session mining models and structures are not, and no record is persisted of session data mining activity.</span></span> <span data-ttu-id="a2b4e-131">一時的なマイニング モデルおよび構造はセッションを終了するとすぐに削除されるため、必要な作業を保存するまでは Excel ブックを閉じないように注意してください。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-131">Because temporary mining models and structures are deleted as soon as you end the session, you should avoid closing your Excel workbook until after you have saved any work that you want to keep.</span></span>

## <a name="changing-connections"></a><span data-ttu-id="a2b4e-132">接続の変更</span><span class="sxs-lookup"><span data-stu-id="a2b4e-132">Changing Connections</span></span>
 <span data-ttu-id="a2b4e-133">接続を変更した場合でも、以前の接続からトレースは削除されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-133">Changing connections does not delete traces from previous connections.</span></span> <span data-ttu-id="a2b4e-134">ブックを閉じた場合のみ、セッションが消去されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-134">Only closing the workbook erases the session.</span></span>

 <span data-ttu-id="a2b4e-135">Excel ブックでの作業中に接続を変更した場合、接続の変更は [**トレーサー** ] ペインに記録されません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-135">If you change connections while working in an Excel workbook, the change of connections is not recorded in the **Tracer** pane.</span></span> <span data-ttu-id="a2b4e-136">現在の接続の名前と状態を明示的に表示するには、[**現在の接続**] をクリックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-136">To explicitly display the name and status of the current connection, you must click **Current Connection**.</span></span>

## <a name="understanding-statements-in-the-tracer"></a><span data-ttu-id="a2b4e-137">トレーサーのステートメントについて</span><span class="sxs-lookup"><span data-stu-id="a2b4e-137">Understanding Statements in the Tracer</span></span>
 <span data-ttu-id="a2b4e-138">DMX は、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のデータ マイニング モデルを作成および操作するための言語です。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-138">DMX is a language that you can use to create and work with data mining models in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="a2b4e-139">DMX を使用して、新しいデータ マイニング モデルの構造の作成、これらのモデルのトレーニング、およびモデルの参照、管理、予測を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-139">You can use DMX to create the structure of new data mining models, train these models, and to browse, manage, and predict against them.</span></span> <span data-ttu-id="a2b4e-140">DMX は、データ定義言語 (DDL) ステートメント、データ操作言語 (DML) ステートメント、および関数と演算子で構成されています。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-140">DMX is composed of data definition language (DDL) statements, data manipulation language (DML) statements, and functions and operators.</span></span>

 <span data-ttu-id="a2b4e-141">ここでは、DMX ステートメントとその構文を詳しく説明しません。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-141">A complete discussion of DMX statements and their syntax is beyond the scope of this topic.</span></span> <span data-ttu-id="a2b4e-142">ただし、[**トレーサー** ] ペインの情報を使用して、DMX ステートメントの動作に関する詳細情報を確認することができます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-142">However, you can use the information in the **Tracer** pane to find detailed information about the behavior of a DMX statement.</span></span> <span data-ttu-id="a2b4e-143">また、Excel 用のデータ マイニング アドインを使用すると、複雑な DMX ステートメントを作成したり、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] サーバーを操作したりできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-143">The Data Mining Add-ins for Excel can also help you build complex DMX statements and interact with an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="a2b4e-144">詳細については、「[クエリ &#40;SQL Server データマイニングアドイン&#41;](query-sql-server-data-mining-add-ins.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-144">For more information, see [Query &#40;SQL Server Data Mining Add-ins&#41;](query-sql-server-data-mining-add-ins.md).</span></span>

> [!NOTE]
>  <span data-ttu-id="a2b4e-145">多くの DMX ステートメントはパラメーター化されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-145">Many DMX statements are parameterized.</span></span> <span data-ttu-id="a2b4e-146">単純型の場合、ステートメントの下にパラメーターの値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-146">For simple types, the values of the parameters are listed under the statement.</span></span> <span data-ttu-id="a2b4e-147">一方、複合型の場合は、パラメーターの型のみが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-147">However, for complex types, only the type of the parameter is listed.</span></span>

 <span data-ttu-id="a2b4e-148">SQL Server Analysis Services では、さらに XML for Analysis (XMLA) プロトコルを使用して、Excel 用のデータ マイニング クライアントおよび [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスを含む、クライアント アプリケーション間のすべての通信を処理します。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-148">SQL Server Analysis Services also uses the XML for Analysis (XMLA) protocol to handle all communications between client applications, including the Data Mining Client for Excel and an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>

 <span data-ttu-id="a2b4e-149">DMX 構文、および XMLA のコマンドや要素の詳細については、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-149">For more information about DMX syntax, and about the commands and elements in XMLA, see [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>

 <span data-ttu-id="a2b4e-150">サーバーに送信される一部のステートメントには、Analysis Services システム ストアド プロシージャを呼び出すクエリが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-150">Some of the statements sent to the server may include queries that call Analysis Services system stored procedures.</span></span> <span data-ttu-id="a2b4e-151">詳細については、SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2b4e-151">For more information, see SQL Server Books Online.</span></span>

