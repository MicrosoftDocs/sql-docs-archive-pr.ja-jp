---
title: Microsoft 線形回帰アルゴリズム |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- algorithms [data mining]
- linear regression algorithms [Analysis Services]
- linear regression [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 50a4abb8-c0b0-4380-ba5e-c49b305b9d22
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6d03f4d60131471d1a978fd66306cc73f274a536
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645265"
---
# <a name="microsoft-linear-regression-algorithm"></a><span data-ttu-id="7f16e-102">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="7f16e-102">Microsoft Linear Regression Algorithm</span></span>
  <span data-ttu-id="7f16e-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの一種であり、従属変数と独立変数の間の線形の関係を計算し、その関係を予測に使用するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-103">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm that helps you calculate a linear relationship between a dependent and independent variable, and then use that relationship for prediction.</span></span>

 <span data-ttu-id="7f16e-104">この関係は、一連のデータを最もよく表す直線の式の形になります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-104">The relationship takes the form of an equation for a line that best represents a series of data.</span></span> <span data-ttu-id="7f16e-105">たとえば、次の図の直線は、データの最適な線形表現です。</span><span class="sxs-lookup"><span data-stu-id="7f16e-105">For example, the line in the following diagram is the best possible linear representation of the data.</span></span>

 <span data-ttu-id="7f16e-106">![データ セットをモデル化した直線](../media/linear-regression.gif "データ セットをモデル化した直線")</span><span class="sxs-lookup"><span data-stu-id="7f16e-106">![A line that models a set of data](../media/linear-regression.gif "A line that models a set of data")</span></span>

 <span data-ttu-id="7f16e-107">図の各データ ポイントには、回帰直線からの距離に関する誤差があります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-107">Each data point in the diagram has an error associated with its distance from the regression line.</span></span> <span data-ttu-id="7f16e-108">回帰式の係数 a および b により、回帰直線の角度と位置が調整されます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-108">The coefficients a and b in the regression equation adjust the angle and location of the regression line.</span></span> <span data-ttu-id="7f16e-109">すべてのデータ ポイントに関する誤差の合計が最小になるまで、a および b を調整して、回帰式を取得できます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-109">You can obtain the regression equation by adjusting a and b until the sum of the errors that are associated with all the points reaches its minimum.</span></span>

 <span data-ttu-id="7f16e-110">複数の変数を使用するその他の種類の回帰や、線形でない回帰の方法もあります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-110">There are other kinds of regression that use multiple variables, and also nonlinear methods of regression.</span></span> <span data-ttu-id="7f16e-111">線形回帰は、何らかの基になっている要因の変更に対する反応をモデル化するための、便利でよく知られた方法です。</span><span class="sxs-lookup"><span data-stu-id="7f16e-111">However, linear regression is a useful and well-known method for modeling a response to a change in some underlying factor.</span></span>

## <a name="example"></a><span data-ttu-id="7f16e-112">例</span><span class="sxs-lookup"><span data-stu-id="7f16e-112">Example</span></span>
 <span data-ttu-id="7f16e-113">線形回帰を使用して、2 つの連続した列の関係を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-113">You can use linear regression to determine a relationship between two continuous columns.</span></span> <span data-ttu-id="7f16e-114">たとえば、線形回帰を使用して、製造データまたは売上データから傾向線を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-114">For example, you can use linear regression to compute a trend line from manufacturing or sales data.</span></span> <span data-ttu-id="7f16e-115">また、線形回帰をより複雑なデータ マイニング モデルの開発の前段階として使用し、データ列間の関係を評価することもできます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-115">You could also use the linear regression as a precursor to development of more complex data mining models, to assess the relationships among data columns.</span></span>

 <span data-ttu-id="7f16e-116">データ マイニング ツールを必要としない線形回帰の計算方法は多数ありますが、このタスクに [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを使用することの利点は、変数間の考えられるすべての関係が自動的に計算され、テストされるということです。</span><span class="sxs-lookup"><span data-stu-id="7f16e-116">Although there are many ways to compute linear regression that do not require data mining tools, the advantage of using the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm for this task is that all the possible relationships among the variables are automatically computed and tested.</span></span> <span data-ttu-id="7f16e-117">最小二乗法の解決などの計算方法を選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7f16e-117">You do not have to select a computation method, such as solving for least squares.</span></span> <span data-ttu-id="7f16e-118">ただし、線形回帰では、結果に影響を与える要因が複数存在するシナリオで、関係が過剰に簡素化される場合があります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-118">However, linear regression might oversimplify the relationships in scenarios where multiple factors affect the outcome.</span></span>

## <a name="how-the-algorithm-works"></a><span data-ttu-id="7f16e-119">アルゴリズムの動作</span><span class="sxs-lookup"><span data-stu-id="7f16e-119">How the Algorithm Works</span></span>
 <span data-ttu-id="7f16e-120">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの一種です。</span><span class="sxs-lookup"><span data-stu-id="7f16e-120">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm is a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="7f16e-121">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを選択すると、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムの特殊なケースが、アルゴリズムの動作を制約して特定の入力データ型を要求するパラメーターを使用して起動されます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-121">When you select the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, a special case of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm is invoked, with parameters that constrain the behavior of the algorithm and require certain input data types.</span></span> <span data-ttu-id="7f16e-122">さらに、標準のデシジョン ツリー モデルではデータが小さなサブセットまたはツリーに反復的に分割されるのに対し、線形回帰モデルではデータセット全体が最初のパスでの関係の計算に使用されます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-122">Moreover, in a linear regression model, the whole data set is used for computing relationships in the initial pass, whereas a standard decision trees model splits the data repeatedly into smaller subsets or trees.</span></span>

## <a name="data-required-for-linear-regression-models"></a><span data-ttu-id="7f16e-123">線形回帰モデルに必要なデータ</span><span class="sxs-lookup"><span data-stu-id="7f16e-123">Data Required for Linear Regression Models</span></span>
 <span data-ttu-id="7f16e-124">線形回帰モデルで使用するデータを用意する際には、特定のアルゴリズムの要件を把握しておいてください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-124">When you prepare data for use in a linear regression model, you should understand the requirements for the particular algorithm.</span></span> <span data-ttu-id="7f16e-125">これには、必要なデータ量やデータの使用方法が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-125">This includes how much data is needed, and how the data is used.</span></span> <span data-ttu-id="7f16e-126">このモデルの種類の要件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7f16e-126">The requirements for this model type are as follows:</span></span>

-   <span data-ttu-id="7f16e-127">**単一キー列** : それぞれのモデルには、各レコードを一意に識別する数値列またはテキスト列が 1 つ含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-127">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="7f16e-128">複合キーは使用できません。</span><span class="sxs-lookup"><span data-stu-id="7f16e-128">Compound keys are not permitted.</span></span>

-   <span data-ttu-id="7f16e-129">**予測可能列** : 少なくとも 1 つの予測可能列が必要です。</span><span class="sxs-lookup"><span data-stu-id="7f16e-129">**A predictable column** Requires at least one predictable column.</span></span> <span data-ttu-id="7f16e-130">1 つのモデルに対し、複数の予測可能属性を含めることができます。ただし、予測可能属性は連続する数値データ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-130">You can include multiple predictable attributes in a model, but the predictable attributes must be continuous numeric data types.</span></span> <span data-ttu-id="7f16e-131">データのネイティブ ストレージが数値であっても、datetime データ型を予測可能属性として使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="7f16e-131">You cannot use a datetime data type as a predictable attribute even if the native storage for the data is numeric.</span></span>

-   <span data-ttu-id="7f16e-132">**入力列** 入力列は連続する数値データを含み、適切なデータ型が割り当てられている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7f16e-132">**Input columns** Input columns must contain continuous numeric data and be assigned the appropriate data type.</span></span>

 <span data-ttu-id="7f16e-133">詳細については、「 [Microsoft 線形回帰アルゴリズム テクニカル リファレンス](microsoft-linear-regression-algorithm-technical-reference.md)」の「必要条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-133">For more information, see the Requirements section of [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md).</span></span>

## <a name="viewing-a-linear-regression-model"></a><span data-ttu-id="7f16e-134">線形回帰モデルの表示</span><span class="sxs-lookup"><span data-stu-id="7f16e-134">Viewing a Linear Regression Model</span></span>
 <span data-ttu-id="7f16e-135">モデルを参照するには、 **Microsoft ツリー ビューアー**を使用します。</span><span class="sxs-lookup"><span data-stu-id="7f16e-135">To explore the model, you use the **Microsoft Tree Viewer**.</span></span> <span data-ttu-id="7f16e-136">線形回帰モデルのツリー構造は非常に単純であり、回帰式に関するすべての情報が単一のノードに含まれています。</span><span class="sxs-lookup"><span data-stu-id="7f16e-136">The tree structure for a linear regression model is very simple, with all the information about the regression equation contained in a single node.</span></span> <span data-ttu-id="7f16e-137">詳細については、「 [Microsoft ツリー ビューアーを使用したモデルの参照](browse-a-model-using-the-microsoft-tree-viewer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-137">For more information, see [Browse a Model Using the Microsoft Tree Viewer](browse-a-model-using-the-microsoft-tree-viewer.md).</span></span>

 <span data-ttu-id="7f16e-138">式の詳細を調べる場合は、 [Microsoft 汎用コンテンツ ツリー ビューアー](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)で係数およびその他の詳細を参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-138">If you want to know more detail about the equation, you can also view the coefficients and other details by using the [Microsoft Generic Content Tree Viewer](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>

 <span data-ttu-id="7f16e-139">線形回帰モデルの場合、モデル コンテンツには、メタデータ、回帰式、および入力値の分布に関する統計が含まれます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-139">For a linear regression model, the model content includes metadata, the regression formula, and statistics about the distribution of input values.</span></span> <span data-ttu-id="7f16e-140">詳細については、 [線形回帰モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)」の「必要条件」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-140">For more information, see [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md).</span></span>

## <a name="creating-predictions"></a><span data-ttu-id="7f16e-141">予測の作成</span><span class="sxs-lookup"><span data-stu-id="7f16e-141">Creating Predictions</span></span>
 <span data-ttu-id="7f16e-142">モデルの処理後、結果が統計のセットとして線形回帰式と共に保存されます。これを使用して、将来の傾向を計算することができます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-142">After the model has been processed, the results are stored as a set of statistics together with the linear regression formula, which you can use to compute future trends.</span></span> <span data-ttu-id="7f16e-143">線形回帰モデルで使用するクエリの例については、「 [線形回帰モデルのクエリ例](linear-regression-model-query-examples.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-143">For examples of queries to use with a linear regression model, see [Linear Regression Model Query Examples](linear-regression-model-query-examples.md).</span></span>

 <span data-ttu-id="7f16e-144">マイニング モデルに対するクエリの作成方法については、「 [データ マイニング クエリ](data-mining-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-144">For general information about how to create queries against mining models, see [Data Mining Queries](data-mining-queries.md).</span></span>

 <span data-ttu-id="7f16e-145">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 線形回帰アルゴリズムを選択して線形回帰モデルを作成することに加えて、予測可能属性が連続する数値データ型である場合は、回帰を含むデシジョン ツリー モデルを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-145">In addition to creating a linear regression model by selecting the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, if the predictable attribute is a continuous numeric data type, you can create a decision tree model that contains regressions.</span></span> <span data-ttu-id="7f16e-146">この場合、アルゴリズムが適切な分離ポイントを見つけたときにデータは分割されますが、データの一部の領域では、代わりに回帰式が作成されます。</span><span class="sxs-lookup"><span data-stu-id="7f16e-146">In this case, the algorithm will split the data when it finds appropriate separation points, but for some regions of data, will create a regression formula instead.</span></span> <span data-ttu-id="7f16e-147">デシジョン ツリー モデル内の回帰ツリーの詳細については、「[デシジョン ツリー モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7f16e-147">For more information about regression trees within a decision trees model, see [Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="7f16e-148">解説</span><span class="sxs-lookup"><span data-stu-id="7f16e-148">Remarks</span></span>

-   <span data-ttu-id="7f16e-149">Predictive Model Markup Language (PMML) を使用したマイニング モデルの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7f16e-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>

-   <span data-ttu-id="7f16e-150">データ マイニング ディメンションの作成はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="7f16e-150">Does not support the creation of data mining dimensions.</span></span>

-   <span data-ttu-id="7f16e-151">ドリルスルーがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7f16e-151">Supports drillthrough.</span></span>

-   <span data-ttu-id="7f16e-152">OLAP マイニング モデルの使用がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="7f16e-152">Supports the use of OLAP mining models.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f16e-153">参照</span><span class="sxs-lookup"><span data-stu-id="7f16e-153">See Also</span></span>
 <span data-ttu-id="7f16e-154">[データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft 線形回帰アルゴリズムテクニカルリファレンス](microsoft-linear-regression-algorithm-technical-reference.md)[線形回帰モデルのクエリ例](linear-regression-model-query-examples.md)[線形回帰モデルのマイニングモデルコンテンツ &#40;Analysis Services データマイニング&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="7f16e-154">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Microsoft Linear Regression Algorithm Technical Reference](microsoft-linear-regression-algorithm-technical-reference.md) [Linear Regression Model Query Examples](linear-regression-model-query-examples.md) [Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)</span></span>

