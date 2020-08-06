---
title: マイニング構造 (Analysis Services-データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- mining structures [Analysis Services], about mining structures
- mining structures [Analysis Services]
- data mining [Analysis Services], structure
- Analysis Services objects, data mining objects
- data mining [Analysis Services], models
- algorithms [data mining]
- data mining [Analysis Services], objects
- mining models [Analysis Services]
- mining models [Analysis Services], about data mining models
ms.assetid: 39748290-c32a-48e6-92a6-0c3a9223773a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bca58767285718b733dd820970cc48a99d0ea14
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643602"
---
# <a name="mining-structures-analysis-services---data-mining"></a><span data-ttu-id="abae6-102">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="abae6-102">Mining Structures (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="abae6-103">マイニング構造には、マイニング モデルの作成元となる、データ ソース ビュー、列の数と型、トレーニング セットとテスト セットに分ける省略可能なパーティションなどのデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="abae6-103">The mining structure defines the data from which mining models are built: it specifies the source data view, the number and type of columns, and an optional partition into training and testing sets.</span></span> <span data-ttu-id="abae6-104">1 つのマイニング構造は、同じドメインを共有する複数のマイニング モデルをサポートできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-104">A single mining structure can support multiple mining models that share the same domain.</span></span> <span data-ttu-id="abae6-105">次の図は、データ マイニング構造とデータ ソースの関係、およびデータ マイニング構造とそれを構成するデータ マイニング モデルの関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="abae6-105">The following diagram illustrates the relationship of the data mining structure to the data source, and to its constituent data mining models.</span></span>  
  
 <span data-ttu-id="abae6-106">![データの処理: ソース、構造、モデル](../media/dmcon-modelarch.gif "データの処理: ソース、構造、モデル")</span><span class="sxs-lookup"><span data-stu-id="abae6-106">![Processing of data: source to structure to model](../media/dmcon-modelarch.gif "Processing of data: source to structure to model")</span></span>  
  
 <span data-ttu-id="abae6-107">図内のマイニング構造は、CustomerID フィールドで結合された複数のテーブルまたはビューを含むデータ ソースを基にしています。</span><span class="sxs-lookup"><span data-stu-id="abae6-107">The mining structure in the diagram is based on a data source that contains multiple tables or views, joined on the CustomerID field.</span></span> <span data-ttu-id="abae6-108">1 つのテーブルには顧客に関する情報 (地理的な領域、年齢、収入、性別など) が格納され、入れ子になった関連テーブルには各顧客の追加情報 (顧客が購入した製品など) を含む複数の行が格納されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-108">One table contains information about customers, such as the geographical region, age, income and gender, while the related nested table contains multiple rows of additional information about each customer, such as products the customer has purchased.</span></span> <span data-ttu-id="abae6-109">この図は、同じマイニング構造から複数のモデルを作成し、それぞれのモデルに構造からさまざまな列を採用できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="abae6-109">The diagram shows that multiple models can be built on one mining structure, and that the models can use different columns from the structure.</span></span>  
  
 <span data-ttu-id="abae6-110">**モデル 1** CustomerID、Income、Age、Region を使用し、Region でデータをフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="abae6-110">**Model 1** Uses CustomerID, Income, Age, Region, and filters the data on Region.</span></span>  
  
 <span data-ttu-id="abae6-111">**モデル 2** CustomerID、Income、Age、Region を使用し、Age でデータをフィルタリングします。</span><span class="sxs-lookup"><span data-stu-id="abae6-111">**Model 2** Uses CustomerID, Income, Age, Region and filters the data on Age.</span></span>  
  
 <span data-ttu-id="abae6-112">**モデル 3** CustomerID、Age、Gender と入れ子になったテーブルを使用し、フィルターは適用しません。</span><span class="sxs-lookup"><span data-stu-id="abae6-112">**Model 3** Uses CustomerID, Age, Gender, and the nested table, with no filter.</span></span>  
  
 <span data-ttu-id="abae6-113">それぞれのモデルは入力に異なる列を使用しており、うち 2 つのモデルはフィルター適用によってモデル内で使用するデータをさらに絞り込んでいるため、同じデータに基づいていても結果は著しく異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="abae6-113">Because the models use different columns for input, and because two of the models additionally restrict the data that is used in the model by applying a filter, the models might have very different results even though they are based on the same data.</span></span> <span data-ttu-id="abae6-114">CustomerID 列は、ケース キーとして使用できる唯一の有効な列であるため、すべてのモデルに必要となります。</span><span class="sxs-lookup"><span data-stu-id="abae6-114">Note that the CustomerID column is required in all models because it is the only available column that can be used as the case key.</span></span>  
  
 <span data-ttu-id="abae6-115">このセクションでは、データ マイニング構造の基本的なアーキテクチャについて説明します。マイニング構造の定義方法、その構造にデータを設定する方法、モデル作成のためにそれを使用する方法などが含まれます。</span><span class="sxs-lookup"><span data-stu-id="abae6-115">This section explains the basic architecture of data mining structures: how you define a mining structure, how you populate it with data, and how you use it to create models.</span></span> <span data-ttu-id="abae6-116">既存のデータ マイニング構造の管理方法またはエクスポート方法の詳細については、「 [データ マイニング ソリューションおよびオブジェクトの管理](management-of-data-mining-solutions-and-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-116">For more information about how to manage or export existing data mining structures, see [Management of Data Mining Solutions and Objects](management-of-data-mining-solutions-and-objects.md).</span></span>  
  
## <a name="defining-a-mining-structure"></a><span data-ttu-id="abae6-117">マイニング構造の定義</span><span class="sxs-lookup"><span data-stu-id="abae6-117">Defining a Mining Structure</span></span>  
 <span data-ttu-id="abae6-118">データ マイニング構造の設定は、次の手順で行います。</span><span class="sxs-lookup"><span data-stu-id="abae6-118">Setting up a data mining structure includes the following steps:</span></span>  
  
-   <span data-ttu-id="abae6-119">データ ソースを定義します。</span><span class="sxs-lookup"><span data-stu-id="abae6-119">Define a data source.</span></span>  
  
-   <span data-ttu-id="abae6-120">構造に含めるデータの列を選択し (モデルにはすべての列を含める必要はありません)、キーを定義します。</span><span class="sxs-lookup"><span data-stu-id="abae6-120">Select columns of data to include in the structure (not all columns need to be added to the model) and defining a key.</span></span>  
  
-   <span data-ttu-id="abae6-121">必要に応じて入れ子になったテーブルのキーも含めて、構造のキーを定義します。</span><span class="sxs-lookup"><span data-stu-id="abae6-121">Define a key for the structure, including the key for the bested table, if applicable.</span></span>  
  
-   <span data-ttu-id="abae6-122">ソース データをトレーニング セットとテスト セットに分割する必要があるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="abae6-122">Specify whether the source data should be separate into a training set and testing set.</span></span> <span data-ttu-id="abae6-123">この手順は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="abae6-123">This step is optional.</span></span>  
  
-   <span data-ttu-id="abae6-124">構造を処理します。</span><span class="sxs-lookup"><span data-stu-id="abae6-124">Process the structure.</span></span>  
  
 <span data-ttu-id="abae6-125">これらの手順は、以下のセクションで詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="abae6-125">These steps are described in more detail in the following sections.</span></span>  
  
### <a name="data-sources-for-mining-structures"></a><span data-ttu-id="abae6-126">マイニング構造のデータ ソース</span><span class="sxs-lookup"><span data-stu-id="abae6-126">Data Sources for Mining Structures</span></span>  
 <span data-ttu-id="abae6-127">マイニング構造を定義する際には、既存のデータ ソース ビューで使用できる列を指定します。</span><span class="sxs-lookup"><span data-stu-id="abae6-127">When you define a mining structure, you use columns that are available in an existing data source view.</span></span> <span data-ttu-id="abae6-128">データ ソース ビューは、複数のデータ ソースをまとめて 1 つのデータ ソースとして使用することができる共有オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="abae6-128">A data source view is a shared object that lets you combine multiple data sources and use them as a single source.</span></span> <span data-ttu-id="abae6-129">元のデータ ソースはクライアント アプリケーションでは表示されません。データ型の変更や、集計列またはエイリアス列の作成には、データ ソース ビューのプロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-129">The original data sources are not visible to client applications, and you can use the properties of the data source view to modify data types, create aggregations, or alias columns.</span></span>  
  
 <span data-ttu-id="abae6-130">同じマイニング構造から複数のマイニング モデルを作成する場合、それぞれのモデルに構造からさまざまな列を採用することができます。</span><span class="sxs-lookup"><span data-stu-id="abae6-130">If you build multiple mining models from the same mining structure, the models can use different columns from the structure.</span></span> <span data-ttu-id="abae6-131">たとえば、1 つの構造を作成してデシジョン ツリー モデルとクラスター モデルを別々に作成し、各モデルが別々の列を使用したり、異なる属性を予測したりできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-131">For example, you can create a single structure and then build separate decision tree and clustering models from it, with each model using different columns and predicting different attributes.</span></span>  
  
 <span data-ttu-id="abae6-132">また、各モデルでは、構造からさまざまな方法で列を使用できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-132">Moreover, each model can use the columns from the structure in different ways.</span></span> <span data-ttu-id="abae6-133">たとえば、データ ソース ビューに Income 列が含まれるとすると、それを異なるモデルに対して異なる方法でバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="abae6-133">For example, your data source view might contain an Income column, which you can bin in different ways for different models.</span></span>  
  
 <span data-ttu-id="abae6-134">データ マイニング構造には、データ ソースおよびそれに含まれる列の定義がソース データへの *バインド* という形で保存されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-134">The data mining structure stores the definition of the data source and the columns in it in the form of *bindings* to the source data.</span></span> <span data-ttu-id="abae6-135">データ ソースのバインドの詳細については、「[データ ソースとバインド (SSAS 多次元)](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-135">For more information about data source bindings, see [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).</span></span> <span data-ttu-id="abae6-136">ただし、DMX の [CREATE MINING STRUCTURE (DMX)](/sql/dmx/create-mining-structure-dmx) ステートメントを使用して、特定のデータ ソースにバインドせずにデータ マイニング構造を作成することもできることに留意してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-136">However, note that you can also create a data mining structure without binding it to a specific data source by using the DMX [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span>  
  
### <a name="mining-structure-columns"></a><span data-ttu-id="abae6-137">マイニング構造列</span><span class="sxs-lookup"><span data-stu-id="abae6-137">Mining Structure Columns</span></span>  
 <span data-ttu-id="abae6-138">マイニング構造の構成要素は、データ ソースに格納されているデータについて記述したマイニング構造列です。</span><span class="sxs-lookup"><span data-stu-id="abae6-138">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="abae6-139">マイニング構造列には、データ型、コンテンツの種類、データの配布方法などの情報が格納されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-139">These columns contain information such as data type, content type, and how the data is distributed.</span></span> <span data-ttu-id="abae6-140">マイニング構造には、特定のマイニング モデルに対する列の使用方法や、モデルを構築するために使用されるアルゴリズムの種類などの情報は含まれていません。これらの情報は、マイニング モデルの内部で定義されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-140">The mining structure does not contain information about how columns are used for a specific mining model, or about the type of algorithm that is used to build a model; this information is defined in the mining model itself.</span></span>  
  
 <span data-ttu-id="abae6-141">マイニング構造には、入れ子になったテーブルを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-141">A mining structure can also contain nested tables.</span></span> <span data-ttu-id="abae6-142">入れ子になったテーブルは、ケースのエンティティとその関連属性との間の一対多の関係を表します。</span><span class="sxs-lookup"><span data-stu-id="abae6-142">A nested table represents a one-to-many relationship between the entity of a case and its related attributes.</span></span> <span data-ttu-id="abae6-143">たとえば、顧客に関する情報と顧客の購入記録が別々のテーブルに格納されている場合は、入れ子になったテーブルを使用すると、これらの情報を単一のケースにまとめることができます。</span><span class="sxs-lookup"><span data-stu-id="abae6-143">For example, if the information that describes the customer resides in one table, and the customer's purchases reside in another table, you can use nested tables to combine the information into a single case.</span></span> <span data-ttu-id="abae6-144">この場合、顧客の識別子はエンティティで、購入記録は関連する属性となります。</span><span class="sxs-lookup"><span data-stu-id="abae6-144">The customer identifier is the entity, and the purchases are the related attributes.</span></span> <span data-ttu-id="abae6-145">入れ子になったテーブルを使用する場合詳細については、「[入れ子になったテーブル (Analysis Services - データ マイニング)](nested-tables-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-145">For more information about when to use nested tables, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](nested-tables-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="abae6-146">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でデータ マイニング モデルを作成するには、まずデータ マイニング構造を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abae6-146">To create a data mining model in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you must first create a data mining structure.</span></span> <span data-ttu-id="abae6-147">データ マイニング ウィザードを使用すると、マイニング構造の作成、データの選択、およびマイニング モデルの追加の手順を段階的に実行できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-147">The Data Mining wizard walks you through the process of creating a mining structure, choosing data, and adding a mining model.</span></span>  
  
 <span data-ttu-id="abae6-148">データ マイニング拡張機能 (DMX) を使用してマイニング モデルを作成する場合は、モデルとモデル内の列を指定すると、必要なマイニング構造が DMX によって自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-148">If you create a mining model by using Data Mining Extensions (DMX), you can specify the model and the columns in it, and DMX will automatically create the required mining structure.</span></span> <span data-ttu-id="abae6-149">詳細については、「[CREATE MINING MODEL (DMX)](/sql/dmx/create-mining-model-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-149">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="abae6-150">詳細については、「 [マイニング構造列](mining-structure-columns.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="abae6-150">For more information, see [Mining Structure Columns](mining-structure-columns.md).</span></span>  
  
### <a name="dividing-the-data-into-training-and-testing-sets"></a><span data-ttu-id="abae6-151">トレーニング セットとテスト セットへのデータの分割</span><span class="sxs-lookup"><span data-stu-id="abae6-151">Dividing the Data into Training and Testing Sets</span></span>  
 <span data-ttu-id="abae6-152">マイニング構造のデータを定義する際に、データの一部をトレーニング用に、一部をテスト用に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-152">When you define the data for the mining structure, you can also specify that some of the data be used for training, and some for testing.</span></span> <span data-ttu-id="abae6-153">そのため、データ マイニング構造を作成する前にデータを分割する必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="abae6-153">Therefore, it is no longer necessary to separate your data in advance of creating a data mining structure.</span></span> <span data-ttu-id="abae6-154">代わりに、モデルを作成する際にデータの一定の割合をテスト用、残りをトレーニング用として指定できます。また、テスト データセットとして使用するケースの数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-154">Instead, while you create your model, you can specify that a certain percentage of the data be held out for testing, and the rest used for training, or you can specify a certain number of cases to use as the test data set.</span></span> <span data-ttu-id="abae6-155">トレーニング データ セットとテスト データセットに関する情報は、マイニング構造と共にキャッシュも保存され、その結果、その構造に基づくすべてのモデルで同じテスト セットを使用できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-155">The information about the training and testing data sets is cached with the mining structure, and as a result, the same test set can be used with all models that are based on that structure.</span></span>  
  
 <span data-ttu-id="abae6-156">詳しくは、「 [Training and Testing Data Sets](training-and-testing-data-sets.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="abae6-156">For more information, see [Training and Testing Data Sets](training-and-testing-data-sets.md).</span></span>  
  
### <a name="enabling-drillthrough"></a><span data-ttu-id="abae6-157">ドリルスルーの有効化</span><span class="sxs-lookup"><span data-stu-id="abae6-157">Enabling Drillthrough</span></span>  
 <span data-ttu-id="abae6-158">特定のマイニング モデルで使用する予定がない列でも、マイニング構造に追加することができます。</span><span class="sxs-lookup"><span data-stu-id="abae6-158">You can add columns to the mining structure even if you do not plan to use the column in a specific mining model.</span></span> <span data-ttu-id="abae6-159">これは、分析プロセスで電子メール アドレスを使用せずに、クラスター モデルで顧客の電子メール アドレスを検索する場合などに便利です。</span><span class="sxs-lookup"><span data-stu-id="abae6-159">This is useful if, for example, you want to retrieve the e-mail addresses of customers in a clustering model, without using the e-mail address during the analysis process.</span></span> <span data-ttu-id="abae6-160">分析および予測のフェーズで列を無視するには、それを構造に追加しますが、使用法フラグを Ignore に設定するか、その列の使用を指定しません。</span><span class="sxs-lookup"><span data-stu-id="abae6-160">To ignore a column during the analysis and prediction phase, you add it to the structure but do not specify a usage for the column, or set the usage flag to Ignore.</span></span> <span data-ttu-id="abae6-161">マイニング モデルでドリルスルーが有効であり、ユーザーが適切な権限を持っている場合には、この方法でフラグを設定したデータをクエリで使用できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-161">Data flagged in this way can still be used in queries if drillthrough has been enabled on the mining model, and if you have the appropriate permissions.</span></span> <span data-ttu-id="abae6-162">たとえば、モデルの作成にそれらの列のデータが使用されなかった場合でも、すべての顧客の分析結果のクラスターを確認してから、ドリルスルー クエリを使用して特定のクラスターの顧客の名前と電子メールを取得できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-162">For example, you could review the clusters resulting from analysis of all customers, and then use a drillthrough query to get the names and e-mail addresses of customers in a particular cluster, even though those columns of data were not used to build the model.</span></span>  
  
 <span data-ttu-id="abae6-163">詳細については、「 [ドリルスルー クエリ (データ マイニング)](drillthrough-queries-data-mining.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="abae6-163">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
### <a name="processing-mining-structures"></a><span data-ttu-id="abae6-164">マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="abae6-164">Processing Mining Structures</span></span>  
 <span data-ttu-id="abae6-165">マイニング構造は、処理されるまでは単なるメタデータ コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="abae6-165">A mining structure is just a metadata container until it is processed.</span></span> <span data-ttu-id="abae6-166">マイニング構造を処理する際、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、データに関する統計値、連続属性を分離する方法に関する情報、および後でマイニング モデルが使用するその他の情報を格納するキャッシュを作成します。</span><span class="sxs-lookup"><span data-stu-id="abae6-166">When you process a mining structure, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] creates a cache that stores statistics about the data, information about how any continuous attributes are discretized, and other information that is later used by mining models.</span></span> <span data-ttu-id="abae6-167">マイニング モデル自体には、このサマリー情報は保存されませんが、代わりに、マイニング構造の処理時にキャッシュに保存された情報が参照されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-167">The mining model itself does not store this summary information, but instead references the information that was cached when the mining structure was processed.</span></span> <span data-ttu-id="abae6-168">したがって、既存の構造に新しいモデルを追加するたびに構造を再処理する必要はなく、モデルのみを処理できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-168">Therefore, you do not need to reprocess the structure each time you add a new model to an existing structure; you can process just the model.</span></span>  
  
 <span data-ttu-id="abae6-169">キャッシュが非常に大きい場合や詳細データを削除したい場合は、処理後にこのキャッシュを破棄することもできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-169">You can opt to discard this cache after processing, if the cache is very large or you want to remove detailed data.</span></span> <span data-ttu-id="abae6-170">データをキャッシュしない場合は、マイニング構造の `CacheMode` プロパティを `ClearAfterProcessing` に変更できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-170">If you do not want the data to be cached, you can change the `CacheMode` property of the mining structure to `ClearAfterProcessing`.</span></span> <span data-ttu-id="abae6-171">これにより、モデルを処理した後にキャッシュが破棄されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-171">This will destroy the cache after any models are processed.</span></span> <span data-ttu-id="abae6-172">`CacheMode` プロパティを `ClearAfterProcessing` に設定すると、マイニング モデルからのドリルスルーが無効になります。</span><span class="sxs-lookup"><span data-stu-id="abae6-172">Setting the `CacheMode` property to `ClearAfterProcessing` will disable drillthrough from the mining model.</span></span>  
  
 <span data-ttu-id="abae6-173">ただし、キャッシュを破棄した後は、マイニング構造に新しいモデルを追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="abae6-173">However, after you destroy the cache, you will not be able to add new models to the mining structure.</span></span> <span data-ttu-id="abae6-174">新しいマイニング モデルを追加したり、既存のモデルのプロパティを変更した場合は、マイニング構造を最初に再処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abae6-174">If you add a new mining model to the structure, or change the properties of existing models, you would need to reprocess the mining structure first.</span></span> <span data-ttu-id="abae6-175">詳細については、「[処理の要件および注意事項 (データ マイニング)](processing-requirements-and-considerations-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-175">For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).</span></span>  
  
### <a name="viewing-mining-structures"></a><span data-ttu-id="abae6-176">マイニング構造の表示</span><span class="sxs-lookup"><span data-stu-id="abae6-176">Viewing Mining Structures</span></span>  
 <span data-ttu-id="abae6-177">ビューアーを使用して、マイニング構造内のデータを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="abae6-177">You cannot use viewers to browse the data in a mining structure.</span></span> <span data-ttu-id="abae6-178">しかし、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、データ マイニング デザイナーの **[マイニング構造]** タブを使用して構造列とその定義を表示できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-178">However, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], you can use the **Mining Structure** tab of Data Mining Designer to view the structure columns and their definitions.</span></span> <span data-ttu-id="abae6-179">詳細については、「 [データ マイニング デザイナー](data-mining-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-179">For more information, see [Data Mining Designer](data-mining-designer.md).</span></span>  
  
 <span data-ttu-id="abae6-180">マイニング構造のデータを確認する場合、データ マイニング拡張機能 (DMX) を使用してクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-180">If you want to review the data in the mining structure, you can create queries by using Data Mining Extensions (DMX).</span></span> <span data-ttu-id="abae6-181">たとえば、 `SELECT * FROM <structure>.CASES` というステートメントでは、マイニング構造のすべてのデータが返されます。</span><span class="sxs-lookup"><span data-stu-id="abae6-181">For example, the statement `SELECT * FROM <structure>.CASES` returns all the data in the mining structure.</span></span> <span data-ttu-id="abae6-182">この情報を取得するには、マイニング構造が既に処理されていて、処理結果がキャッシュされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="abae6-182">To retrieve this information, the mining structure must have been processed, and the results of processing must be cached.</span></span>  
  
 <span data-ttu-id="abae6-183">`SELECT * FROM <model>.CASES` というステートメントでは同じ列が返されますが、特定のモデルのケースのみです。</span><span class="sxs-lookup"><span data-stu-id="abae6-183">The statement `SELECT * FROM <model>.CASES` returns the same columns, but only for the cases in that particular model.</span></span> <span data-ttu-id="abae6-184">詳細については、「[SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)」および「[SELECT FROM &#60;model&#62;.CASES (DMX)](/sql/dmx/select-from-model-content-dmx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-184">For more information, see [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases) and [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
## <a name="using-data-mining-models-with-mining-structures"></a><span data-ttu-id="abae6-185">データ マイニング モデルとマイニング構造の使用</span><span class="sxs-lookup"><span data-stu-id="abae6-185">Using Data Mining Models with Mining Structures</span></span>  
 <span data-ttu-id="abae6-186">データ マイニング モデルは、マイニング構造によって表されるデータにマイニング モデル アルゴリズムを適用します。</span><span class="sxs-lookup"><span data-stu-id="abae6-186">A data mining model applies a mining model algorithm to the data that is represented by a mining structure.</span></span> <span data-ttu-id="abae6-187">マイニング モデルは特定のマイニング構造に属するオブジェクトで、マイニング構造によって定義されるプロパティのすべての値を継承します。</span><span class="sxs-lookup"><span data-stu-id="abae6-187">A mining model is an object that belongs to a particular mining structure, and the model inherits all the values of the properties that are defined by the mining structure.</span></span> <span data-ttu-id="abae6-188">マイニング モデルは、マイニング構造に含まれているすべての列またはその一部を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="abae6-188">The model can use all the columns that the mining structure contains or a subset of the columns.</span></span> <span data-ttu-id="abae6-189">構造列の複数のコピーを構造に追加できます。</span><span class="sxs-lookup"><span data-stu-id="abae6-189">You can add multiple copies of a structure column to a structure.</span></span> <span data-ttu-id="abae6-190">構造列の複数のコピーをモデルに追加し、モデルの各構造列に異なる名前、つまり *別名*を割り当てることもできます。</span><span class="sxs-lookup"><span data-stu-id="abae6-190">You can also add multiple copies of a structure column to a model, and then assign different names, or *aliases*, to each structure column in the model.</span></span> <span data-ttu-id="abae6-191">構造列の別名定義の詳細については、「 [モデル列の別名の作成](create-an-alias-for-a-model-column.md) 」および「 [マイニング モデルのプロパティ](mining-model-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-191">For more information about aliasing structure columns, see [Create an Alias for a Model Column](create-an-alias-for-a-model-column.md) and [Mining Model Properties](mining-model-properties.md).</span></span>  
  
 <span data-ttu-id="abae6-192">データ マイニング モデルのアーキテクチャの詳細については、「 [マイニング モデル (Analysis Services - データ マイニング)](mining-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-192">For more information about the architecture of data mining models, see [Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="abae6-193">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="abae6-193">Related Tasks</span></span>  
 <span data-ttu-id="abae6-194">マイニング構造の定義、管理、使用の詳細については、次のリンクを使用してください。</span><span class="sxs-lookup"><span data-stu-id="abae6-194">Use the links provided her to learn more about how to define, manage, and use mining structures.</span></span>  
  
|<span data-ttu-id="abae6-195">タスク</span><span class="sxs-lookup"><span data-stu-id="abae6-195">Tasks</span></span>|<span data-ttu-id="abae6-196">リンク</span><span class="sxs-lookup"><span data-stu-id="abae6-196">Links</span></span>|  
|-----------|-----------|  
|<span data-ttu-id="abae6-197">リレーショナル マイニング構造の操作</span><span class="sxs-lookup"><span data-stu-id="abae6-197">Work with relational mining structures</span></span>|[<span data-ttu-id="abae6-198">新しいリレーショナル マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="abae6-198">Create a New Relational Mining Structure</span></span>](create-a-new-relational-mining-structure.md)<br /><br /> [<span data-ttu-id="abae6-199">マイニング構造への入れ子になったテーブルの追加</span><span class="sxs-lookup"><span data-stu-id="abae6-199">Add a Nested Table to a Mining Structure</span></span>](add-a-nested-table-to-a-mining-structure.md)|  
|<span data-ttu-id="abae6-200">OLAP キューブに基づくマイニング構造の操作</span><span class="sxs-lookup"><span data-stu-id="abae6-200">Work with mining structures based on OLAP cubes</span></span>|[<span data-ttu-id="abae6-201">新規の OLAP マイニング構造の作成</span><span class="sxs-lookup"><span data-stu-id="abae6-201">Create a New OLAP Mining Structure</span></span>](create-a-new-olap-mining-structure.md)<br /><br /> [<span data-ttu-id="abae6-202">マイニング構造のソース キューブのフィルター選択</span><span class="sxs-lookup"><span data-stu-id="abae6-202">Filter the Source Cube for a Mining Structure</span></span>](../filter-the-source-cube-for-a-mining-structure.md)|  
|<span data-ttu-id="abae6-203">マイニング構造内の列の操作</span><span class="sxs-lookup"><span data-stu-id="abae6-203">Work with columns in a  mining structure</span></span>|[<span data-ttu-id="abae6-204">マイニング構造への列の追加</span><span class="sxs-lookup"><span data-stu-id="abae6-204">Add Columns to a Mining Structure</span></span>](add-columns-to-a-mining-structure.md)<br /><br /> [<span data-ttu-id="abae6-205">マイニング構造からの列の削除</span><span class="sxs-lookup"><span data-stu-id="abae6-205">Remove Columns from a Mining Structure</span></span>](remove-columns-from-a-mining-structure.md)|  
|<span data-ttu-id="abae6-206">マイニング構造のプロパティおよびデータの変更またはクエリ</span><span class="sxs-lookup"><span data-stu-id="abae6-206">Change or query mining structure properties and data</span></span>|[<span data-ttu-id="abae6-207">マイニング構造のプロパティの変更</span><span class="sxs-lookup"><span data-stu-id="abae6-207">Change the Properties of a Mining Structure</span></span>](change-the-properties-of-a-mining-structure.md)|  
|<span data-ttu-id="abae6-208">基になるデータ ソースの操作とソース データの更新</span><span class="sxs-lookup"><span data-stu-id="abae6-208">Work with the underlying data sources and update source data</span></span>|[<span data-ttu-id="abae6-209">マイニング構造に使用されるデータ ソース ビューの編集</span><span class="sxs-lookup"><span data-stu-id="abae6-209">Edit the Data Source View used for a Mining Structure</span></span>](edit-the-data-source-view-used-for-a-mining-structure.md)<br /><br /> [<span data-ttu-id="abae6-210">マイニング構造の処理</span><span class="sxs-lookup"><span data-stu-id="abae6-210">Process a Mining Structure</span></span>](process-a-mining-structure.md)|  
  
## <a name="see-also"></a><span data-ttu-id="abae6-211">参照</span><span class="sxs-lookup"><span data-stu-id="abae6-211">See Also</span></span>  
 <span data-ttu-id="abae6-212">[データベースオブジェクト &#40;Analysis Services-多次元データ&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="abae6-212">[Database Objects &#40;Analysis Services - Multidimensional Data&#41;](../multidimensional-models/olap-logical/database-objects-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="abae6-213">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="abae6-213">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
  