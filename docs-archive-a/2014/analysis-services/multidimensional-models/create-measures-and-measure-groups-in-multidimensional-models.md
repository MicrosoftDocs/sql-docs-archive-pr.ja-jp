---
title: 多次元モデルでのメジャーとメジャーグループの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- measure groups [Analysis Services], defining
ms.assetid: 1018bb2e-b89b-489e-aead-450dec5dca3b
author: minewiskan
ms.author: owend
ms.openlocfilehash: af111da66679edd034f43057fa5bdcb05cfb86ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738941"
---
# <a name="create-measures-and-measure-groups-in-multidimensional-models"></a><span data-ttu-id="fbcd0-102">多次元モデル内のメジャーおよびメジャー グループの作成</span><span class="sxs-lookup"><span data-stu-id="fbcd0-102">Create Measures and Measure Groups in Multidimensional Models</span></span>
  <span data-ttu-id="fbcd0-103">*メジャー* は、合計値、度数、最小値、最大値、平均値、または自ら作成したカスタム MDX 式のように、数値のデータ値を集計したものです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-103">A *measure* is an aggregation of numeric data values, such as sum, count, minimum, maximum, average, or a custom MDX expression that you create.</span></span> <span data-ttu-id="fbcd0-104">*メジャー グループ* は、1 つ以上のメジャーに対応するコンテナーです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-104">A *measure group* is a container for one or more measures.</span></span> <span data-ttu-id="fbcd0-105">すべてのメジャーは、メジャーが 1 つしかない場合を含め、1 つのメジャー グループ内に存在します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-105">All measures exist in a measure group, even if there is only one measure.</span></span> <span data-ttu-id="fbcd0-106">キューブには、少なくとも 1 つのメジャーとメジャー グループが必要です。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-106">A cube must have at least one measure and measure group.</span></span>

 <span data-ttu-id="fbcd0-107">このトピックのセクションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="fbcd0-108">メジャーを作成するための方法</span><span class="sxs-lookup"><span data-stu-id="fbcd0-108">Approaches for creating measures</span></span>](#bkmk_create)

-   [<span data-ttu-id="fbcd0-109">メジャーのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="fbcd0-109">Components of a measure</span></span>](#bkmk_comps)

-   [<span data-ttu-id="fbcd0-110">ファクトとファクト テーブルでのメジャーとメジャー グループのモデリング</span><span class="sxs-lookup"><span data-stu-id="fbcd0-110">Modeling measures and measure groups on facts and fact tables</span></span>](#bkmk_modeling)

-   [<span data-ttu-id="fbcd0-111">メジャー グループの粒度</span><span class="sxs-lookup"><span data-stu-id="fbcd0-111">Granularity of a measure group</span></span>](#bkmk_grain)

##  <a name="approaches-for-creating-measures"></a><a name="bkmk_create"></a><span data-ttu-id="fbcd0-112">メジャーを作成する方法</span><span class="sxs-lookup"><span data-stu-id="fbcd0-112">Approaches for creating measures</span></span>
 <span data-ttu-id="fbcd0-113">メジャーは、キューブの静的な要素になることができ、設計時に作成され、キューブがアクセスされるときは常に存在します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-113">Measures can be a static element of the cube, created at design time, always present whenever the cube is accessed.</span></span> <span data-ttu-id="fbcd0-114">ただし、多次元式 (MDX) を使用して *計算されるメンバー* としてメジャーを定義し、キューブ内の他のメジャーに基づいてメジャーの計算値を算出することもできます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-114">But you can also define a measure as a *calculated member* by using a MDX to provide a calculated value for a measure based on other measures in the cube.</span></span> <span data-ttu-id="fbcd0-115">計算されるメンバーは、セッションまたはユーザーにスコープすることができます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-115">A calculated member can be scoped to session or user.</span></span>

 <span data-ttu-id="fbcd0-116">メジャーまたはメジャー グループを作成するには、次の方法のいずれかを使用します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-116">To create a measure or a measure group, use one of these approaches:</span></span>

|||
|-|-|
|<span data-ttu-id="fbcd0-117">キューブ ウィザード</span><span class="sxs-lookup"><span data-stu-id="fbcd0-117">Cube Wizard</span></span>|<span data-ttu-id="fbcd0-118">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でキューブ ウィザードを実行してキューブを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-118">Run the Cube Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a cube.</span></span><br /><br /> <span data-ttu-id="fbcd0-119">ソリューション エクスプローラーで **[キューブ]** を右クリックし、 **[新しいキューブ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-119">In Solution Explorer, right-click **Cubes** and choose **New Cube**.</span></span> <span data-ttu-id="fbcd0-120">これらの手順については、「[多次元モデリング (Adventure Works チュートリアル)](../multidimensional-modeling-adventure-works-tutorial.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-120">See [Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](../multidimensional-modeling-adventure-works-tutorial.md) if you need help with these steps.</span></span><br /><br /> <span data-ttu-id="fbcd0-121">既存のデータ ウェアハウスのテーブルに基づいてキューブを作成すると、メジャーおよびメジャー グループの定義がキューブの作成プロセスの一部として具体化されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-121">When you create a cube based on tables from an existing data warehouse, definitions for the measures and measure group materialize as part of the cube creation process.</span></span> <span data-ttu-id="fbcd0-122">ウィザードで、キューブ内のメジャーとメジャー グループのオブジェクトのベースとして使用するファクトとファクト テーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-122">In the wizard, you'll choose which facts and fact tables to use as the basis for the measure and measure group objects in your cube.</span></span>|
|<span data-ttu-id="fbcd0-123">[新しいメジャー] ダイアログ</span><span class="sxs-lookup"><span data-stu-id="fbcd0-123">New Measure dialog</span></span>|<span data-ttu-id="fbcd0-124">キューブが既に [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]に存在していることを前提に、キューブ デザイナーでソリューション エクスプローラー内のキューブ名をダブルクリックして開きます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-124">Assuming the cube already exists in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], double-click the cube name in Solution Explorer to open it in Cube Designer.</span></span> <span data-ttu-id="fbcd0-125">[メジャー] ペインで、ソース テーブル、列、集計の型を指定し、最上位のノードを右クリックして新しいメジャー グループまたは新しいメジャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-125">In the Measures pane, right-click the top node to create a new measure group, or new measures, by specifying a source table, column, and aggregation type.</span></span> <span data-ttu-id="fbcd0-126">この方法を使用するには、構築済みの関数の固定リストから集計の方法を選択することが必要です。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-126">Using this approach requires that you choose the aggregation method from a fixed list of prebuilt functions.</span></span> <span data-ttu-id="fbcd0-127">より一般的に使用されている集計の説明については、「 [Use Aggregate Functions](use-aggregate-functions.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-127">See [Use Aggregate Functions](use-aggregate-functions.md) for a discussion of the more commonly used aggregations.</span></span>|
|<span data-ttu-id="fbcd0-128">計算されるメンバー</span><span class="sxs-lookup"><span data-stu-id="fbcd0-128">Calculated member</span></span>|<span data-ttu-id="fbcd0-129">計算されるメンバーについては、いつどのように作成するかを制御できるため、それにより [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でキューブに柔軟性と分析機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-129">Calculated members add flexibility and analysis capability to a cube in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] because you can control when and how they are created.</span></span> <span data-ttu-id="fbcd0-130">ユーザー セッションの期間中、または調査の一部としての Management Studio では、一時的にのみメジャーが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-130">Sometimes you only need a measure temporarily, for the duration of a user session, or in Management Studio as part of an investigation.</span></span><br /><br /> <span data-ttu-id="fbcd0-131">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、[計算] タブを開いて計算されるメンバーを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-131">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the Calculations tab to create a new calculated member.</span></span><br /><br /> <span data-ttu-id="fbcd0-132">メジャーを MDX 式のベースにする場合は、この方法を選択します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-132">Choose this approach when basing a measure on an MDX expression.</span></span> <span data-ttu-id="fbcd0-133">詳細については次のトピックを参照してください: 「[MDX 内でのメジャーの作成](mdx/mdx-building-measures.md)」、「[計算](../multidimensional-models-olap-logical-cube-objects/calculations.md)」、[多次元モデルの計算](calculations-in-multidimensional-models.md)」、「[MDX スクリプティングの基礎 (Analysis Services)](mdx/mdx-scripting-fundamentals-analysis-services.md)」。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-133">See these topics for more information: [Building Measures in MDX](mdx/mdx-building-measures.md), [Calculations](../multidimensional-models-olap-logical-cube-objects/calculations.md), [Calculations in Multidimensional Models](calculations-in-multidimensional-models.md) and [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx/mdx-scripting-fundamentals-analysis-services.md).</span></span>|
|<span data-ttu-id="fbcd0-134">MDX または XMLA</span><span class="sxs-lookup"><span data-stu-id="fbcd0-134">MDX or XMLA</span></span>|<span data-ttu-id="fbcd0-135">計算される新しいメジャーを含めるには、SQL Server Management Studio で、MDX または XMLA を実行してデータベースを変更します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-135">In SQL Server Management Studio, you can execute MDX or XMLA to alter a database to include a new calculated measure.</span></span> <span data-ttu-id="fbcd0-136">この方法は、ソリューションをサーバーに配置した後の、データのアドホック テストに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-136">This approach is useful for ad hoc testing of data, after the solution is deployed to a server.</span></span> <span data-ttu-id="fbcd0-137">「 [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-137">See [Document and Script an Analysis Services Database](document-and-script-an-analysis-services-database.md).</span></span>|

##  <a name="components-of-a-measure"></a><a name="bkmk_comps"></a><span data-ttu-id="fbcd0-138">メジャーのコンポーネント</span><span class="sxs-lookup"><span data-stu-id="fbcd0-138">Components of a measure</span></span>
 <span data-ttu-id="fbcd0-139">メジャーは、プロパティを持つオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-139">A measure is an object with properties.</span></span> <span data-ttu-id="fbcd0-140">メジャーは、名前だけでなく、集計の種類と、ソース列またはデータがあるメジャーの読み込みに使用する式が必要です。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-140">In addition to its name, a measure must have an aggregation type and a source column or an expression used to load the measure with data.</span></span> <span data-ttu-id="fbcd0-141">メジャーの定義を変更するには、プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-141">You can modify the measure definition by setting its properties.</span></span>

|||
|-|-|
|<span data-ttu-id="fbcd0-142">**source**</span><span class="sxs-lookup"><span data-stu-id="fbcd0-142">**source**</span></span>|<span data-ttu-id="fbcd0-143">ほとんどのメジャーは、AdventureWorks データ ウェアハウス内の Internet Sales (インターネット売上) や Reseller Sales (販売店売上) テーブルにある Sales Amount 列など、外部データ ウェアハウス内のファクト テーブルの数値列に由来していますが、定義する計算全体に基づいてメジャーを新規作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-143">Most measures come from numeric columns in fact tables in an external data warehouse, such as the Sales Amount column in the Internet Sales and Reseller Sales tables in the AdventureWorks data warehouse, but you can also create new measures based entirely on calculations that you define.</span></span><br /><br /> <span data-ttu-id="fbcd0-144">ディメンション テーブルの属性列は、メジャーの定義に使用できますが、これらのメジャーの集計動作は、通常、準加法または非加法です。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-144">Attribute columns from dimension tables can be used to define measures, but such measures are typically semiadditive or nonadditive in terms of their aggregation behavior.</span></span> <span data-ttu-id="fbcd0-145">準加法の動作の詳細については、「 [準加法の動作の定義](define-semiadditive-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-145">For more information about semiadditive behavior, see [Define Semiadditive Behavior](define-semiadditive-behavior.md).</span></span>|
|<span data-ttu-id="fbcd0-146">**集計**</span><span class="sxs-lookup"><span data-stu-id="fbcd0-146">**aggregation**</span></span>|<span data-ttu-id="fbcd0-147">既定では、各ディメンションに従ってメジャーが集計されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-147">By default, measures are summed along each dimension.</span></span> <span data-ttu-id="fbcd0-148">ただし、`AggregateFunction` プロパティを使用するとこの動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-148">However, the `AggregateFunction` property lets you modify this behavior.</span></span> <span data-ttu-id="fbcd0-149">一覧については [Use Aggregate Functions](use-aggregate-functions.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-149">See [Use Aggregate Functions](use-aggregate-functions.md) for a list.</span></span>|
|<span data-ttu-id="fbcd0-150">**プロパティ**</span><span class="sxs-lookup"><span data-stu-id="fbcd0-150">**Properties**</span></span>|<span data-ttu-id="fbcd0-151">プロパティの追加説明については [Configure Measure Properties](configure-measure-properties.md) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-151">See [Configure Measure Properties](configure-measure-properties.md) for additional property descriptions.</span></span>|

##  <a name="modeling-measures-and-measure-groups-on-facts-and-fact-tables"></a><a name="bkmk_modeling"></a><span data-ttu-id="fbcd0-152">ファクトテーブルとファクトテーブルでのメジャーとメジャーグループのモデリング</span><span class="sxs-lookup"><span data-stu-id="fbcd0-152">Modeling measures and measure groups on facts and fact tables</span></span>
 <span data-ttu-id="fbcd0-153">ウィザードを実行する前に、メジャーの定義の背後にあるモデリングの原則を理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-153">Before you run a wizard, it helps to understand the modeling principles behind measure definition.</span></span>

 <span data-ttu-id="fbcd0-154">メジャーとメジャー グループは、外部データ ウェアハウスにあるファクトとファクト テーブルを表す多次元オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-154">Measures and measure groups are the multidimensional objects that represent facts and fact tables in an external data warehouse.</span></span> <span data-ttu-id="fbcd0-155">ほとんどの場合、メジャーとメジャー グループはデータ ソース ビュー内のオブジェクトに基づくものになります。このオブジェクトは基になるデータ ウェアハウスから作成されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-155">In most cases, measures and measure groups will be based on objects in a data source view, which in turn are created from the underlying data warehouse.</span></span>

 <span data-ttu-id="fbcd0-156">次の図は、 **FactSalesQuota** ファクト テーブルと、このテーブルに関連する **DimTime** および **DimEmployee**という 2 つのディメンション テーブルを表しています。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-156">The following diagram represents the **FactSalesQuota** fact table and the two dimension tables associated with it, **DimTime** and **DimEmployee**.</span></span> <span data-ttu-id="fbcd0-157">Adventure Works のサンプル キューブにおいて、これらのテーブルは Sales Quotas メジャー グループの基礎として、および時間と従業員のディメンションの基礎として使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-157">In the Adventure Works sample cube, these tables are used as the basis of the Sales Quotas measure group, and the Time and Employee dimensions.</span></span>

 <span data-ttu-id="fbcd0-158">![2 つのディメンション テーブルを持つ FactSalesQuota テーブル](../media/factsalesquota.gif "2 つのディメンション テーブルを持つ FactSalesQuota テーブル")</span><span class="sxs-lookup"><span data-stu-id="fbcd0-158">![FactSalesQuota table with two dimension tables](../media/factsalesquota.gif "FactSalesQuota table with two dimension tables")</span></span>

 <span data-ttu-id="fbcd0-159">ファクト テーブルには、属性列とメジャー列という 2 つの種類の列が含まれています。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-159">The fact table contains two basic types of columns: attribute columns and measure columns.</span></span>

-   <span data-ttu-id="fbcd0-160">属性列は、ディメンション テーブルに外部キー リレーションシップを作成するために使用されます。これにより、ディメンション テーブルに含まれるデータに基づいてメジャー列の定量化可能なデータが編成されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-160">Attribute columns are used to create foreign key relationships to dimension tables, so that the quantifiable data in the measure columns can be organized by the data contained in the dimension tables.</span></span> <span data-ttu-id="fbcd0-161">属性列は、ファクト テーブルとそのメジャー グループの粒度を定義するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-161">Attribute columns are also used to define the granularity of a fact table and its measure group.</span></span>

-   <span data-ttu-id="fbcd0-162">メジャー列によって、メジャー グループに含まれるメジャーが定義されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-162">Measure columns define the measures contained by a measure group.</span></span>

 <span data-ttu-id="fbcd0-163">キューブウィザードを実行すると、外部キーはフィルターで除外されます。選択する残りの列の一覧には、メジャー列と、外部キーとして識別されない属性列が表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-163">When you run the Cube Wizard, the foreign keys are filtered out. In the list of remaining columns to choose from, you will see measure columns, plus attribute columns that are not identified as a foreign key.</span></span> <span data-ttu-id="fbcd0-164">**FactSalesQuote** の例では、 **CalendarYear** 、 **CalendarQuarter** 、および **SalesAmountQuota**がウィザードにより表示されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-164">In the **FactSalesQuote** example, the wizard will offer **CalendarYear** and **CalendarQuarter** in addition to **SalesAmountQuota**.</span></span> <span data-ttu-id="fbcd0-165">多次元モデルの場合、実行可能なメジャーは **SalesAmountQuota** メジャー列だけとなります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-165">Only the **SalesAmountQuota** measure column will result in a workable measure for your multidimensional model.</span></span> <span data-ttu-id="fbcd0-166">日付に基づくその他の列は、各クォータの金額を修飾するために存在します。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-166">The other date-based columns exist to qualify each quota amount.</span></span> <span data-ttu-id="fbcd0-167">キューブ ウィザードのメジャーの一覧から他の列、つまり **CalendarYear** と **CalendarQuarter**を除外する (または後ほど、デザイナーでメジャー グループから削除する) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-167">You should exclude the other columns, **CalendarYear** and **CalendarQuarter**, from the measure list in the Cube Wizard (or remove them from the measure group later in the designer).</span></span>

 <span data-ttu-id="fbcd0-168">この説明から除外すべき点は、ウィザードによって提供されるすべての列がメジャーとして役立つわけではないということです。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-168">The point to take away from this discussion is that not all columns offered by the wizard are useful as a measure.</span></span> <span data-ttu-id="fbcd0-169">どの列をメジャーとして使用するかを決定する際は、データの理解とデータの使用方法を信頼して決定してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-169">Rely on your understanding of the data and how it will be used when deciding which columns to use as measures.</span></span> <span data-ttu-id="fbcd0-170">データを調べるには、データ ソース ビュー内のテーブルを右クリックしてください。メジャーとして使用する列を特定するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-170">Remember that you can right-click a table in the data source view to explore the data, which can help you identify which columns to use as measures.</span></span> <span data-ttu-id="fbcd0-171">詳細については、「[Explore Data in a Data Source View (Analysis Services)](explore-data-in-a-data-source-view-analysis-services.md)」 (データ ソース ビューでのデータの検索 (Analysis Services)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-171">See [Explore Data in a Data Source View &#40;Analysis Services&#41;](explore-data-in-a-data-source-view-analysis-services.md) for more information.</span></span>

> [!NOTE]
>  <span data-ttu-id="fbcd0-172">すべてのメジャーがファクト テーブルの列に格納されている値から直接派生するわけではありません。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-172">Not all measures are derived directly from a value stored in a column of the fact table.</span></span> <span data-ttu-id="fbcd0-173">たとえば、Adventure Works DW サンプル キューブの **Sales Quota** メジャー グループに定義されている **Sales Person Count** メジャーは、 **FactSalesQuota** ファクト テーブルの **EmployeeKey** 列にある一意の値のカウント (または個別のカウント) に実際に基づいています。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-173">For example, the **Sales Person Count** measure defined in the **Sales Quota** measure group of the Adventure Works sample cube is actually based on the count of unique values (or distinct count) in the **EmployeeKey** column of the **FactSalesQuota** fact table.</span></span>

##  <a name="granularity-of-a-measure-group"></a><a name="bkmk_grain"></a><span data-ttu-id="fbcd0-174">メジャーグループの粒度</span><span class="sxs-lookup"><span data-stu-id="fbcd0-174">Granularity of a measure group</span></span>
 <span data-ttu-id="fbcd0-175">メジャー グループには、ファクト テーブルによってサポートされている詳細のレベルを参照する、関連付けられている粒度があります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-175">Measure groups have an associated granularity that refers to the level of detail supported by a fact table.</span></span> <span data-ttu-id="fbcd0-176">粒度は、ディメンションへの外部キーのリレーションシップを介して設定されます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-176">The granularity is set through the foreign key relationship to a dimension.</span></span>

 <span data-ttu-id="fbcd0-177">たとえば、 **FactSalesQuota** ファクト テーブルには、 **DimEmployee** テーブルとの外部キーのリレーションシップがあり、 **FactSalesQuota** テーブルの各レコードは、1 人の従業員と関係付けられます。こうして、Employee ディメンションから表示されたメジャー グループの粒度は個々の従業員のレベルとなります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-177">For example, the **FactSalesQuota** fact table has a foreign key relationship with the **DimEmployee** table, each record in the **FactSalesQuota** table is related to a single employee, and thus the granularity of the measure group as viewed from the Employee dimension is at the individual employee level.</span></span>

 <span data-ttu-id="fbcd0-178">メジャー グループの粒度は、メジャー グループを表示するためのディメンションの最も低いレベルより詳細なレベルには設定できません。ただし、属性を追加して、粒度を荒くすることは可能です。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-178">The granularity of a measure group can never be set finer than the lowest level of the dimension from which the measure group is viewed, but the granularity can be made coarser by using additional attributes.</span></span> <span data-ttu-id="fbcd0-179">たとえば、 **FactSalesQuota** ファクト テーブルでは、 **DimTime**テーブルとのリレーションシップの粒度を確立するために **TimeKey**、 **CalendarYear**、および **CalendarQuarter** の 3 列が使用されています。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-179">For example, the **FactSalesQuota** fact table uses three columns, **TimeKey**, **CalendarYear**, and **CalendarQuarter**, to establish the granularity of the relationship with the **DimTime** table.</span></span> <span data-ttu-id="fbcd0-180">結果として、時間ディメンションから見たメジャー グループの粒度は、時間ディメンションの最も低いレベルである "日" ではなく、カレンダー四半期になります。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-180">As a result, the granularity of the measure group as viewed from the Time dimension is by calendar quarter, and not by day, which is the lowest level of the Time dimension.</span></span>

 <span data-ttu-id="fbcd0-181">キューブ デザイナーの **[ディメンションの使用法]** タブを使用すると、特定のディメンションに関してメジャー グループの粒度を指定できます。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-181">You can specify the granularity of a measure group with relation to a specific dimension by using the **Dimension Usage** tab of the Cube Designer.</span></span> <span data-ttu-id="fbcd0-182">ディメンションのリレーションシップの詳細については、「 [Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fbcd0-182">For more information about dimension relationships, see [Dimension Relationships](../multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fbcd0-183">参照</span><span class="sxs-lookup"><span data-stu-id="fbcd0-183">See Also</span></span>
 <span data-ttu-id="fbcd0-184">[多次元モデルの](cubes-in-multidimensional-models.md)[メジャーおよびメジャーグループ](measures-and-measure-groups.md)内のキューブ</span><span class="sxs-lookup"><span data-stu-id="fbcd0-184">[Cubes in Multidimensional Models](cubes-in-multidimensional-models.md) [Measures and Measure Groups](measures-and-measure-groups.md)</span></span>

