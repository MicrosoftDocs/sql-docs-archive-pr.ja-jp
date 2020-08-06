---
title: 多次元モデルアセンブリ管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Analysis Services], assemblies
- calling user-defined functions
- user impersonation [Analysis Services]
- impersonation [Analysis Services]
- Data Mining Extensions [Analysis Services], assemblies
- MDX [Analysis Services], assemblies
- user-defined functions [Analysis Services]
- Analysis Services objects, assemblies
- assemblies [Analysis Services]
- application domains [Analysis Services]
ms.assetid: b2645d10-6d17-444e-9289-f111ec48bbfb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b95a3171b3b194e84f10809f71eb72fefb07172b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712554"
---
# <a name="multidimensional-model-assemblies-management"></a><span data-ttu-id="0a58b-102">多次元モデルのアセンブリの管理</span><span class="sxs-lookup"><span data-stu-id="0a58b-102">Multidimensional Model Assemblies Management</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="0a58b-103">で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、多次元式 (MDX) 言語およびデータマイニング拡張機能 (DMX) 言語で使用するための多数の組み込み関数が用意されています。これは、標準の統計計算から階層内のメンバーを走査するためのすべての機能を実現するためのものです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] supplies lots of intrinsic functions for use with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages, designed to accomplish everything from standard statistical calculations to traversing members in a hierarchy.</span></span> <span data-ttu-id="0a58b-104">ただし、他のすべての複雑で強力な製品がそうであるように、この製品も常に機能の拡張を求められています。</span><span class="sxs-lookup"><span data-stu-id="0a58b-104">But, as with any other complex and robust product, there is always the need to extend the functionality of such a product further.</span></span>  
  
 <span data-ttu-id="0a58b-105">このため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスまたはデータベースにアセンブリを追加するための機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="0a58b-105">Therefore, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lets you add assemblies to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance or database.</span></span> <span data-ttu-id="0a58b-106">アセンブリを使用すると、Microsoft Visual Basic .NET や Microsoft Visual C# など、任意の共通言語ランタイム (CLR) 言語を使用する外部ユーザー定義関数を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-106">Assemblies let you create external, user-defined functions using any common language runtime (CLR) language, such as Microsoft Visual Basic .NET or Microsoft Visual C#.</span></span> <span data-ttu-id="0a58b-107">Microsoft Visual Basic や Microsoft Visual C++ など、コンポーネント オブジェクト モデル (COM) オートメーション言語を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-107">You can also use Component Object Model (COM) Automation languages such as Microsoft Visual Basic or Microsoft Visual C++.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a58b-108">COM アセンブリにより、セキュリティ上のリスクが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-108">COM assemblies might pose a security risk.</span></span> <span data-ttu-id="0a58b-109">このリスクやその他の考慮事項により、[!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)] では、COM アセンブリが非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="0a58b-109">Due to this risk and other considerations, COM assemblies were deprecated in [!INCLUDE[ssASversion10](../../includes/ssasversion10-md.md)].</span></span> <span data-ttu-id="0a58b-110">COM アセンブリは、今後のリリースではサポートされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-110">COM assemblies might not be supported in future releases.</span></span>  
  
 <span data-ttu-id="0a58b-111">アセンブリにより、MDX と DMX のビジネス機能が拡張されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-111">Assemblies let you extend the business functionality of MDX and DMX.</span></span> <span data-ttu-id="0a58b-112">必要な機能はダイナミック リンク ライブラリ (DLL) などのライブラリに作成し、このライブラリはアセンブリとして [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-112">You build the functionality that you want into a library, such as a dynamic link library (DLL) and add the library as an assembly to an instance of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="0a58b-113">ライブラリ内のパブリック メソッドは、ユーザー定義関数として、MDX および DMX 式、プロシージャ、計算、動作、およびクライアント アプリケーションに公開されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-113">The public methods in the library are then exposed as user-defined functions to MDX and DMX expressions, procedures, calculations, actions, and client applications.</span></span>  
  
 <span data-ttu-id="0a58b-114">新しいプロシージャや関数を使用したアセンブリをサーバーに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-114">An assembly with new procedures and functions can be added to the server.</span></span> <span data-ttu-id="0a58b-115">アセンブリを使用して、サーバーによって提供されていない独自の機能を拡張または追加できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-115">You can use assemblies to enhance or add custom functionality that is not provided by the server.</span></span> <span data-ttu-id="0a58b-116">アセンブリを使用することにより、多次元式 (MDX)、データ マイニング拡張機能 (DMX)、またはストアド プロシージャに新しい関数を追加できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-116">By using assemblies, you can add new functions to Multidimensional Expressions (MDX), Data Mining Extensions (DMX), or stored procedures.</span></span> <span data-ttu-id="0a58b-117">カスタム アプリケーションの実行場所からアセンブリが読み込まれ、アセンブリ バイナリ ファイルのコピーは、データベースのデータと共にサーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-117">Assemblies are loaded from the location where the custom application is run, and a copy of the assembly binary file is saved along with the database data in the server.</span></span> <span data-ttu-id="0a58b-118">アセンブリを削除すると、そのアセンブリのコピーもサーバーから削除されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-118">When an assembly is removed, the copied assembly is also removed from the server.</span></span>  
  
 <span data-ttu-id="0a58b-119">アセンブリには、COM と CLR の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-119">Assemblies can be of two different types: COM and CLR.</span></span> <span data-ttu-id="0a58b-120">CLR アセンブリとは、C#、Visual Basic .NET、マネージド C++ など、.NET Framework プログラミング言語で開発されたアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-120">CLR assemblies are assemblies developed in .NET Framework programming languages such as C#, Visual Basic .NET, managed C++.</span></span> <span data-ttu-id="0a58b-121">COM アセンブリとは、サーバーに登録する必要がある COM ライブラリです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-121">COM assemblies are COM libraries that must be registered in the server</span></span>  
  
 <span data-ttu-id="0a58b-122">アセンブリは、 <xref:Microsoft.AnalysisServices.Server> オブジェクトまたは <xref:Microsoft.AnalysisServices.Database> オブジェクトに追加できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-122">Assemblies can be added to <xref:Microsoft.AnalysisServices.Server> or <xref:Microsoft.AnalysisServices.Database> objects.</span></span> <span data-ttu-id="0a58b-123">サーバー アセンブリは、サーバーまたはサーバー内の任意のオブジェクトに接続している任意のユーザーが呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-123">Server assemblies can be called by any user connected to the server or any object in the server.</span></span> <span data-ttu-id="0a58b-124">データベース アセンブリは、 <xref:Microsoft.AnalysisServices.Database> オブジェクトまたはデータベースに接続しているユーザーのみが呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-124">Database assemblies can be called only by <xref:Microsoft.AnalysisServices.Database> objects or users connected to the database.</span></span>  
  
 <span data-ttu-id="0a58b-125">単純な <xref:Microsoft.AnalysisServices.Assembly> オブジェクトは、基本情報 (名前と ID)、ファイル コレクション、およびセキュリティの仕様で構成されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-125">A simple <xref:Microsoft.AnalysisServices.Assembly> object is composed of basic information (Name and Id), file collection, and security specifications.</span></span>  
  
 <span data-ttu-id="0a58b-126">デバッグ ファイルがアセンブリ ファイルと共に読み込まれた場合、ファイル コレクションは、読み込まれたアセンブリ ファイルとそれらに対応するデバッグ (.pdb) ファイルを参照します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-126">The file collection refers to the loaded assembly files and their corresponding debugging (.pdb) files, if the debugging files were loaded with the assembly files.</span></span> <span data-ttu-id="0a58b-127">アセンブリ ファイルは、アプリケーションがファイルを定義した場所から読み込まれ、コピーは、データと共にサーバーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-127">Assembly files are loaded from the location where the application defined the files to, and a copy is saved in the server along with the data.</span></span> <span data-ttu-id="0a58b-128">アセンブリ ファイルのコピーは、サービスが開始されるたびにアセンブリを読み込むために使用されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-128">The copy of the assembly file is used to load the assembly every time the service is started.</span></span>  
  
 <span data-ttu-id="0a58b-129">セキュリティの仕様には、アセンブリを実行するために使用される権限セットと権限の借用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-129">Security specifications include the permission set and the impersonation used to run the assembly.</span></span>  
  
## <a name="calling-user-defined-functions"></a><span data-ttu-id="0a58b-130">ユーザー定義関数の呼び出し</span><span class="sxs-lookup"><span data-stu-id="0a58b-130">Calling User-Defined Functions</span></span>  
 <span data-ttu-id="0a58b-131">アセンブリでのユーザー定義関数の呼び出しは、完全修飾名を使用する必要があるという点を除いて、固有の関数の呼び出しと同じように行われます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-131">Calling a user-defined function in an assembly is performed just like calling an intrinsic function, except that you must use a fully qualified name.</span></span> <span data-ttu-id="0a58b-132">たとえば、次の例に示すように、MDX によって予期される型を返すユーザー定義関数は MDX クエリに含まれます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-132">For example, a user-defined function that returns a type expected by MDX is included in an MDX query, as shown in the following example:</span></span>  
  
```  
Select MyAssembly.MyClass.MyStoredProcedure(a, b, c) on 0 from Sales  
```  
  
 <span data-ttu-id="0a58b-133">ユーザー定義関数は、CALL キーワードを使用して呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-133">User-defined functions can also be called using the CALL keyword.</span></span> <span data-ttu-id="0a58b-134">レコードセットまたは void 値を返すユーザー定義関数には CALL キーワードを使用する必要があります。また、ユーザー定義関数が、現在のキューブやデータ マイニング モデルなどの、MDX または DMX のステートメントやスクリプトのコンテキスト内のオブジェクトに依存する場合は、CALL キーワードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-134">You must use the CALL keyword for user-defined functions which return recordsets or void values, and you cannot use the CALL keyword if the user-defined function depends on an object in the context of the MDX or DMX statement or script, such as the current cube or data mining model.</span></span> <span data-ttu-id="0a58b-135">MDX または DMX クエリの外部で呼び出される関数の一般的な使用方法は、AMO オブジェクト モデルを使用して管理機能を実行することです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-135">A common use for a function called outside an MDX or DMX query is to use the AMO object model to perform administrative functions.</span></span> <span data-ttu-id="0a58b-136">たとえば、MDX ステートメントで `MyVoidProcedure(a, b, c)` 関数を使用する場合、次の構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-136">If, for example, you wanted to use the function `MyVoidProcedure(a, b, c)` in an MDX statement, the following syntax would be employed:</span></span>  
  
```  
Call MyAssembly.MyClass.MyVoidProcedure(a, b, c)  
```  
  
 <span data-ttu-id="0a58b-137">アセンブリは、一度共通のコードを開発して単一の場所に格納することで、データベースの開発を簡略化します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-137">Assemblies simplify database development by enabling common code to be developed once and stored in a single location.</span></span> <span data-ttu-id="0a58b-138">クライアント ソフトウェア開発者は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の関数ライブラリを作成して、アプリケーションと共に配布することができます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-138">Client software developers can create libraries of functions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] and distribute them with their applications.</span></span>  
  
 <span data-ttu-id="0a58b-139">アセンブリおよびユーザー定義関数は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 関数ライブラリまたは他のアセンブリの関数名と重複させることができます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-139">Assemblies and user-defined functions can duplicate the function names of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] function library or of other assemblies.</span></span> <span data-ttu-id="0a58b-140">完全修飾名を使用してユーザー定義関数を呼び出す限り、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は正しいプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-140">As long as you call the user-defined function by using its fully qualified name, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will use the correct procedure.</span></span> <span data-ttu-id="0a58b-141">セキュリティ目的と、異なるクラス ライブラリで重複する名前を呼び出す可能性を排除するため、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではストアド プロシージャに対して完全修飾名のみを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-141">For security purposes, and to eliminate the chance of calling a duplicate name in a different class library, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] requires that you use only fully qualified names for stored procedures.</span></span>  
  
 <span data-ttu-id="0a58b-142">特定の CLR アセンブリからユーザー定義関数を呼び出すには、次に示すように、ユーザー定義関数の前にアセンブリ名、完全なクラス名、プロシージャ名を付けます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-142">To call a user-defined function from a specific CLR assembly, the user-defined function is preceded by the assembly name, full class name, and procedure name, as demonstrated here:</span></span>  
  
 <span data-ttu-id="0a58b-143">*AssemblyName*。*Fullclassname*。*ProcedureName*(*引数 1*,*引数 2*,...)</span><span class="sxs-lookup"><span data-stu-id="0a58b-143">*AssemblyName*.*FullClassName*.*ProcedureName*(*Argument1*, *Argument2*, ...)</span></span>  
  
 <span data-ttu-id="0a58b-144">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の旧バージョンとの互換性のため、次の構文を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-144">For backward compatibility with earlier versions of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the following syntax is also acceptable:</span></span>  
  
 <span data-ttu-id="0a58b-145">*AssemblyName*!*FullClassName*!*ProcedureName*(*Argument1*, *Argument2*, ...)</span><span class="sxs-lookup"><span data-stu-id="0a58b-145">*AssemblyName*!*FullClassName*!*ProcedureName*(*Argument1*, *Argument2*, ...)</span></span>  
  
 <span data-ttu-id="0a58b-146">COM ライブラリが複数のインターフェイスをサポートしている場合は、次に示すように、インターフェイス ID を使用してプロシージャ名を解決することもできます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-146">If a COM library supports multiple interfaces, the interface ID can also be used to resolve the procedure name, as demonstrated here:</span></span>  
  
 <span data-ttu-id="0a58b-147">*AssemblyName*!*InterfaceID*!*ProcedureName*(*Argument1*, *Argument2*, ...)</span><span class="sxs-lookup"><span data-stu-id="0a58b-147">*AssemblyName*!*InterfaceID*!*ProcedureName*(*Argument1*, *Argument2*, ...)</span></span>  
  
## <a name="security"></a><span data-ttu-id="0a58b-148">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="0a58b-148">Security</span></span>  
 <span data-ttu-id="0a58b-149">アセンブリのセキュリティは、コード アクセス セキュリティ モデルである、.NET Framework セキュリティ モデルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="0a58b-149">Security for assemblies is based on the .NET Framework security model, which is a code-access security model.</span></span> <span data-ttu-id="0a58b-150">.NET Framework は、ランタイムが完全に信頼されるコードと部分的に信頼されるコードの両方をホストできると仮定する、コード アクセス セキュリティ メカニズムをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="0a58b-150">.NET Framework supports a code-access security mechanism that assumes that the runtime can host both fully trusted and partially trusted code.</span></span> <span data-ttu-id="0a58b-151">.NET Framework コード アクセス セキュリティによって保護されるリソースは、通常、リソースへのアクセスを許可する前に対応する権限を要求する、マネージド コードによってラップされます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-151">The resources that are protected by .NET Framework code access security are typically wrapped by managed code which demands the corresponding permission before enabling access to the resource.</span></span> <span data-ttu-id="0a58b-152">権限の要求は、(アセンブリ レベルで) 呼び出し履歴内のすべての呼び出し側が、対応するリソース権限を持つ場合にのみ満たされます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-152">The demand for the permission is satisfied only if all the callers (at the assembly level) in the call stack have the corresponding resource permission.</span></span>  
  
 <span data-ttu-id="0a58b-153">アセンブリでは、実行権限は `PermissionSet` オブジェクトの `Assembly` プロパティを使用して渡されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-153">For assemblies, permission for execution is passed with the `PermissionSet` property on the `Assembly` object.</span></span> <span data-ttu-id="0a58b-154">マネージド コードが取得する権限は、有効なセキュリティ ポリシーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-154">The permissions that managed code receives are determined by the security policy in effect.</span></span> <span data-ttu-id="0a58b-155">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 以外によるホスト環境では、エンタープライズ、コンピューター、およびユーザーの 3 つの有効なポリシー レベルがあります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-155">There are already three levels of policy in effect in a non-[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] hosted environment: enterprise, computer and user.</span></span> <span data-ttu-id="0a58b-156">コードが取得する権限の有効なリストは、これら 3 つのレベルによって取得される権限の共通部分によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-156">The effective list of permissions that code receives is determined by the intersection of the permissions obtained by these three levels.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0a58b-157">によって、ホスト時の CLR にホスト レベルのセキュリティ ポリシー レベルが提供されます。このポリシーは、常に有効な 3 つのポリシー レベルよりも下位の、追加のポリシー レベルです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-157">supplies a host-level security policy level to the CLR while hosting it; this policy is an additional policy level below the three policy levels that are always in effect.</span></span> <span data-ttu-id="0a58b-158">このポリシーは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によって作成されるアプリケーション ドメインごとに設定されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-158">This policy is set for every application domain that is created by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0a58b-159">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ホスト レベル ポリシーは、システム アセンブリの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 固定ポリシーと、ユーザー アセンブリのユーザー指定ポリシーの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-159">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] host-level policy is a combination of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] fixed policy for system assemblies and user-specified policy for user assemblies.</span></span> <span data-ttu-id="0a58b-160">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ホスト ポリシーのユーザー指定部分は、各アセンブリの 3 つの権限バケットの 1 つを指定するアセンブリの所有者に基づいています。</span><span class="sxs-lookup"><span data-stu-id="0a58b-160">The user-specified piece of the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] host policy is based on the assembly owner specifying one of three permission buckets for each assembly:</span></span>  
  
|<span data-ttu-id="0a58b-161">設定する権限</span><span class="sxs-lookup"><span data-stu-id="0a58b-161">Permission Setting</span></span>|<span data-ttu-id="0a58b-162">説明</span><span class="sxs-lookup"><span data-stu-id="0a58b-162">Description</span></span>|  
|------------------------|-----------------|  
|`Safe`|<span data-ttu-id="0a58b-163">内部的な計算権限を提供します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-163">Provides internal computation permission.</span></span> <span data-ttu-id="0a58b-164">この権限バケットでは、.NET Framework 内の保護されたリソースにアクセスする権限は許可されません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-164">This permission bucket does not assign permissions to access any of the protected resources in the .NET Framework.</span></span> <span data-ttu-id="0a58b-165">これは、`PermissionSet` プロパティで何も指定されていない場合に、アセンブリに既定の権限バケットです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-165">This is the default permission bucket for an assembly if none is specified with the `PermissionSet` property.</span></span>|  
|`ExternalAccess`|<span data-ttu-id="0a58b-166">外部システム リソースにアクセスする追加機能と共に、`Safe` 設定と同じアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-166">Provides the same access as the `Safe` setting, with the additional ability to access external system resources.</span></span> <span data-ttu-id="0a58b-167">この権限バケットはセキュリティの保証を提供するものではありませんが、信頼性の保証は提供されます (このシナリオを保証するのは可能です)。</span><span class="sxs-lookup"><span data-stu-id="0a58b-167">This permission bucket does not offer security guarantees (although it is possible to secure this scenario), but it does give reliability guarantees.</span></span>|  
|`Unsafe`|<span data-ttu-id="0a58b-168">制限はありません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-168">Provides no restrictions.</span></span> <span data-ttu-id="0a58b-169">この権限セットで実行されるマネージド コードに対する、セキュリティあるいは信頼性の保証はありません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-169">No security or reliability guarantees can be made for managed code running under this permission set.</span></span> <span data-ttu-id="0a58b-170">管理者によって指定されたカスタム権限であっても、すべての権限が、この信頼性のレベルで実行されるコードに与えられます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-170">Any permission, even a custom permission included by the administrator, is granted to code running at this level of trust.</span></span>|  
  
 <span data-ttu-id="0a58b-171">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]によって CLR がホストされるとき、スタックウォーク ベースの権限チェックはネイティブの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] コードとの境界で停止されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-171">When CLR is hosted by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], the stack-walk based permission check stops at the boundary with native [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] code.</span></span> <span data-ttu-id="0a58b-172">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] アセンブリ内のすべてのマネージド コードは常に、上記の 3 つの権限カテゴリのいずれかに分類されます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-172">Any managed code in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] assemblies always falls into one of the three permission categories listed earlier.</span></span>  
  
 <span data-ttu-id="0a58b-173">COM (またはアンマネージ) アセンブリ ルーチンは、CLR セキュリティ モデルをサポートしません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-173">COM (or unmanaged) assembly routines do not support the CLR security model.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="0a58b-174">偽装</span><span class="sxs-lookup"><span data-stu-id="0a58b-174">Impersonation</span></span>  
 <span data-ttu-id="0a58b-175">マネージド コードが [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 外部のリソースにアクセスする場合、必ず適切な Windows セキュリティ コンテキスト内でアクセスが行われるようにするため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はアセンブリの `ImpersonationMode` プロパティ設定に関連付けられているルールに従います。</span><span class="sxs-lookup"><span data-stu-id="0a58b-175">Whenever managed code accesses any resource outside [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] follows the rules associated with the `ImpersonationMode` property setting of the assembly to make sure that the access occurs in an appropriate Windows security context.</span></span> <span data-ttu-id="0a58b-176">`Safe` 権限設定を使用するアセンブリは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 外部のリソースにアクセスできないため、これらのルールは `ExternalAccess` 権限設定および `Unsafe` 権限設定を使用するアセンブリにのみ適用可能です。</span><span class="sxs-lookup"><span data-stu-id="0a58b-176">Because assemblies using the `Safe` permission setting cannot access resources outside [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], these rules are applicable only for assemblies using the `ExternalAccess` and `Unsafe` permission settings.</span></span>  
  
-   <span data-ttu-id="0a58b-177">現在の実行コンテキストが Windows 認証ログインに対応しており、元の呼び出し側のコンテキストと同じ場合 (つまり、途中に EXECUTE AS が存在しない場合)、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は Windows 認証ログインの権限を借用してからリソースにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="0a58b-177">If the current execution context corresponds to Windows Authenticated login and is the same as the context of the original caller (that is, there is no EXECUTE AS in the middle), [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will impersonate the Windows Authenticated login before accessing the resource.</span></span>  
  
-   <span data-ttu-id="0a58b-178">元の呼び出し側のコンテキストを変更した中間の EXECUTE AS が存在する場合、外部リソースへのアクセスは失敗します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-178">If there is an intermediate EXECUTE AS that changed the context from that of the original caller), the attempt to access external resource will fail.</span></span>  
  
 <span data-ttu-id="0a58b-179">`ImpersonationMode` プロパティは、`ImpersonateCurrentUser` または `ImpersonateAnonymous` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-179">The `ImpersonationMode` property can be set to `ImpersonateCurrentUser` or `ImpersonateAnonymous`.</span></span> <span data-ttu-id="0a58b-180">既定の設定、`ImpersonateCurrentUser` は、現在のユーザーのネットワーク ログイン アカウントでアセンブリを実行します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-180">The default setting, `ImpersonateCurrentUser`, runs an assembly under the current user's network login account.</span></span> <span data-ttu-id="0a58b-181">この設定を使用する場合、 `ImpersonateAnonymous` 実行コンテキストは、サーバー上の Windows ログインユーザーアカウント IUSER_*servername*に対応します。</span><span class="sxs-lookup"><span data-stu-id="0a58b-181">If the `ImpersonateAnonymous` setting is used, the execution context is corresponds to the Windows login user account IUSER_*servername* on the server.</span></span> <span data-ttu-id="0a58b-182">これは、制限されたサーバー権限を持つ、インターネット ゲスト アカウントです。</span><span class="sxs-lookup"><span data-stu-id="0a58b-182">This is the Internet guest account, which has limited privileges on the server.</span></span> <span data-ttu-id="0a58b-183">このコンテキストで実行するアセンブリは、ローカル サーバーの制限されたリソースにのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-183">An assembly running in this context can only access limited resources on the local server.</span></span>  
  
### <a name="application-domains"></a><span data-ttu-id="0a58b-184">アプリケーション ドメイン</span><span class="sxs-lookup"><span data-stu-id="0a58b-184">Application Domains</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="0a58b-185">はアプリケーション ドメインを直接公開しません。</span><span class="sxs-lookup"><span data-stu-id="0a58b-185">does not expose application domains directly.</span></span> <span data-ttu-id="0a58b-186">各アプリケーション ドメインは、同じアプリケーション ドメイン内で実行される一連のアセンブリにより、.NET Framework の `System.Reflection` 名前空間または他の方法を使用して実行時に互いを検出し、遅延バインドで互いの呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0a58b-186">Because of a set of assemblies running in the same application domain, application domains can discover each other at execution time by using the `System.Reflection` namespace in the .NET Framework or in some other way, and can call into them in late-bound manner.</span></span> <span data-ttu-id="0a58b-187">このような呼び出しは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 認証ベース セキュリティによって使用される権限のチェック対象になります。</span><span class="sxs-lookup"><span data-stu-id="0a58b-187">Such calls will be subject to the permission checks used by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] authorization-based security.</span></span>  
  
 <span data-ttu-id="0a58b-188">アプリケーション ドメインの境界と各ドメインで実行されるアセンブリは実装ごとに定義されるため、同じアプリケーション ドメインからアセンブリを検出できるとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0a58b-188">You should not rely on finding assemblies in the same application domain, because the application domain boundary and the assemblies that go into each domain are defined by the implementation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a58b-189">参照</span><span class="sxs-lookup"><span data-stu-id="0a58b-189">See Also</span></span>  
 <span data-ttu-id="0a58b-190">[ストアドプロシージャのセキュリティの設定](../multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="0a58b-190">[Setting Security for Stored Procedures](../multidimensional-models-extending-olap-stored-procedures/setting-security-for-stored-procedures.md) </span></span>  
 [<span data-ttu-id="0a58b-191">ストアドプロシージャの定義</span><span class="sxs-lookup"><span data-stu-id="0a58b-191">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  