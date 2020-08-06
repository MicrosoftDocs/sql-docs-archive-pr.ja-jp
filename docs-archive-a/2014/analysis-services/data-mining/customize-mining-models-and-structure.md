---
title: マイニングモデルと構造のカスタマイズ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- mining models [Analysis Services], properties
- algorithms [data mining]
- mining models [Analysis Services], creating
- mining models [Analysis Services], modifying
- mining models [Analysis Services], about data mining models
ms.assetid: 32c17b4f-e090-45f9-b3aa-ffa7084e928e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3dcf0a854b454a997b89f95917e7bfae474a06d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645283"
---
# <a name="customize-mining-models-and-structure"></a><span data-ttu-id="483e5-102">マイニング モデルとマイニング構造のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="483e5-102">Customize Mining Models and Structure</span></span>
  <span data-ttu-id="483e5-103">現在のビジネス ニーズに合ったアルゴリズムを選択した後、マイニング モデルを次の方法でカスタマイズできます。モデルをカスタマイズすると、より良い結果を得られる場合があります。</span><span class="sxs-lookup"><span data-stu-id="483e5-103">After you have selected an algorithm that meets your business needs, you can customize the mining model in the following ways to potentially improve results.</span></span>

-   <span data-ttu-id="483e5-104">モデルで使用するデータ列、または列の使用法や、コンテンツの種類、分離メソッドを変更する。</span><span class="sxs-lookup"><span data-stu-id="483e5-104">Use different columns of data in the model, or change the usage, content type, or discretization method for the columns.</span></span>

-   <span data-ttu-id="483e5-105">マイニング モデルに対するフィルターを作成して、モデルのトレーニングに使用するデータを制限する。</span><span class="sxs-lookup"><span data-stu-id="483e5-105">Create filters on the mining model to restrict the data used in training the model.</span></span>

-   <span data-ttu-id="483e5-106">データを分析するために使用されたアルゴリズムを変更する。</span><span class="sxs-lookup"><span data-stu-id="483e5-106">Change the algorithm that was used to analyze data.</span></span>

-   <span data-ttu-id="483e5-107">アルゴリズム パラメーターを設定して、しきい値やツリーの分割などの重要な条件を制御する。</span><span class="sxs-lookup"><span data-stu-id="483e5-107">Set algorithm parameters to control thresholds, tree splits, and other important conditions.</span></span>

 <span data-ttu-id="483e5-108">このトピックでは、これらのオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="483e5-108">This topic describes these options.</span></span>

## <a name="changing-data-used-by-the-model"></a><span data-ttu-id="483e5-109">モデルで使用するデータの変更</span><span class="sxs-lookup"><span data-stu-id="483e5-109">Changing Data Used by the Model</span></span>
 <span data-ttu-id="483e5-110">モデルで使用するデータ列や、そのデータの使用方法および処理方法に関する決定は、分析の結果に大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="483e5-110">The decisions that you make about which columns of data to use in the model, and how to use and process that data, greatly affect the results of analysis.</span></span> <span data-ttu-id="483e5-111">以下のトピックには、それらの選択に役立つ情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="483e5-111">The following topics provide information to help you understand these choices.</span></span>

### <a name="using-feature-selection"></a><span data-ttu-id="483e5-112">機能の選択の使用</span><span class="sxs-lookup"><span data-stu-id="483e5-112">Using Feature Selection</span></span>
 <span data-ttu-id="483e5-113">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のほとんどのデータ マイニング アルゴリズムでは、 *機能の選択* というプロセスを使用して、最も役に立つ属性のみを選択してモデルに追加します。</span><span class="sxs-lookup"><span data-stu-id="483e5-113">Most data mining algorithms in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] use a process called *feature selection* to select only the most useful attributes for addition to a model.</span></span> <span data-ttu-id="483e5-114">列や属性の数を減らすと、パフォーマンスやモデルの品質を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="483e5-114">Reducing the number of columns and attributes can improve performance and the quality of the model.</span></span> <span data-ttu-id="483e5-115">使用できる機能の選択の方法は、選択するアルゴリズムによって異なります。</span><span class="sxs-lookup"><span data-stu-id="483e5-115">The feature selection methods that are available differ depending on the algorithm that you choose.</span></span>

 <span data-ttu-id="483e5-116">[機能の選択 (データ マイニング)](feature-selection-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="483e5-116">[Feature Selection &#40;Data Mining&#41;](feature-selection-data-mining.md).</span></span>

### <a name="changing-usage"></a><span data-ttu-id="483e5-117">使用方法の変更</span><span class="sxs-lookup"><span data-stu-id="483e5-117">Changing Usage</span></span>
 <span data-ttu-id="483e5-118">マイニング モデルに含まれる列と各列の使用方法を変更できます。</span><span class="sxs-lookup"><span data-stu-id="483e5-118">You can change which columns are included in a mining model and how each column is used.</span></span> <span data-ttu-id="483e5-119">予期したとおりの結果が得られない場合は、入力として使用した列を調べて、選択した列が適切かどうかを検討する必要があります。さらに、データの処理を向上させるためにできることがあるかどうかについても検討します。たとえば、次のようなことが考えられます。</span><span class="sxs-lookup"><span data-stu-id="483e5-119">If you do not get the results you expect, you should example the columns you used as input, and ask yourself whether the columns are a good choice, and whether there is anything you can do to improve the handling of data, including:</span></span>

-   <span data-ttu-id="483e5-120">誤って数値としてラベルが付けられたカテゴリ変数を特定する。</span><span class="sxs-lookup"><span data-stu-id="483e5-120">Identifying categorical variables that have mistakenly labeled as numbers.</span></span>

-   <span data-ttu-id="483e5-121">カテゴリを追加して、属性の数を減らし、相関関係をわかりやすくする。</span><span class="sxs-lookup"><span data-stu-id="483e5-121">Adding categories to collapse the number of attributes and make it easier t find correlations.</span></span>

-   <span data-ttu-id="483e5-122">数値をビン分割または分離する方法を変更する。</span><span class="sxs-lookup"><span data-stu-id="483e5-122">Changing the way that numbers are binned, or discretized.</span></span>

-   <span data-ttu-id="483e5-123">一意の値が多数含まれている列や実際には参照データであるが分析に適さない列 (住所、ミドル ネームなど) を削除する。</span><span class="sxs-lookup"><span data-stu-id="483e5-123">Removing columns that have a lot of unique values, or columns that are really reference data and not useful for analysis, such as addresses or middle names.</span></span>

 <span data-ttu-id="483e5-124">マイニング構造から列を物理的に削除する必要はありません。列に**Ignore**というフラグを付けるだけです。</span><span class="sxs-lookup"><span data-stu-id="483e5-124">You don't need to physically remove columns from the mining structure; you can just flag the column as **Ignore**.</span></span> <span data-ttu-id="483e5-125">列はマイニング モデルから削除されますが、その列は引き続き構造内の他のマイニング モデルで使用することや、ドリルスルー クエリで参照することができます。</span><span class="sxs-lookup"><span data-stu-id="483e5-125">The column is removed from the mining model, but can still be used by other mining models in the structure, ore referenced in a drillthrough query.</span></span>

### <a name="creating-aliases-for-model-columns"></a><span data-ttu-id="483e5-126">モデル列の別名の作成</span><span class="sxs-lookup"><span data-stu-id="483e5-126">Creating Aliases for Model Columns</span></span>
 <span data-ttu-id="483e5-127">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でマイニング モデルを作成すると、マイニング構造内の列と同じ名前が使用されます。</span><span class="sxs-lookup"><span data-stu-id="483e5-127">When [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] creates the mining model, it uses the same column names that are in the mining structure.</span></span> <span data-ttu-id="483e5-128">マイニング モデルのすべての列に、別名を追加できます。</span><span class="sxs-lookup"><span data-stu-id="483e5-128">You can add an alias to any column in the mining model.</span></span> <span data-ttu-id="483e5-129">こうすると、列の内容や使用法がわかりやすくなったり、名前が短くなるためクエリを作成しやすくなったりします。</span><span class="sxs-lookup"><span data-stu-id="483e5-129">This might make it easier to understand the column contents or usage, or make the name shorter for convenience in creating queries.</span></span> <span data-ttu-id="483e5-130">別名は、列のコピーを作成し、わかりやすい名前を付ける場合にも便利です。</span><span class="sxs-lookup"><span data-stu-id="483e5-130">Aliases are also helpful when you want to create a copy of a column and name it something descriptive.</span></span>

 <span data-ttu-id="483e5-131">別名を作成するには、マイニング モデル列の `Name` プロパティを編集します。</span><span class="sxs-lookup"><span data-stu-id="483e5-131">You create an alias by editing the `Name` property of the mining model column.</span></span> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="483e5-132">は引き続き元の名前を列の ID として使用し、に入力した新しい値が `Name` 列の別名になり、列の使用法の横にかっこで囲まれたグリッドに表示されます。</span><span class="sxs-lookup"><span data-stu-id="483e5-132">continues to use the original name as the ID of the column, and the new value that you type for `Name` becomes the column alias, and appears in the grid in parentheses next to the column usage.</span></span>

 <span data-ttu-id="483e5-133">![マイニング モデル列の別名](../media/modelcolumnalias-income.gif "マイニング モデル列の別名")</span><span class="sxs-lookup"><span data-stu-id="483e5-133">![aliases on mining model columns](../media/modelcolumnalias-income.gif "aliases on mining model columns")</span></span>

 <span data-ttu-id="483e5-134">この図には、すべて収入に関連したマイニング構造列の複数のコピーを持つ関連モデルを示しています。</span><span class="sxs-lookup"><span data-stu-id="483e5-134">The graphic shows related models that have multiple copies of a mining structure column, all related to Income.</span></span> <span data-ttu-id="483e5-135">構造列のコピーは、それぞれ異なる方法で分離されています。</span><span class="sxs-lookup"><span data-stu-id="483e5-135">Each copy of the structure column has been discretized in a different way.</span></span> <span data-ttu-id="483e5-136">図のモデルでは、それぞれ異なる列をマイニング構造から使用していますが、モデル間で列を比較しやすくするため、各モデルの列名を [**収入**] に変更しました。</span><span class="sxs-lookup"><span data-stu-id="483e5-136">The models in the diagram each use a different column from the mining structure; however, for convenience in comparing the columns across the models, the column in each model has been renamed to [**Income**].</span></span>

### <a name="adding-filters"></a><span data-ttu-id="483e5-137">フィルターの追加</span><span class="sxs-lookup"><span data-stu-id="483e5-137">Adding Filters</span></span>
 <span data-ttu-id="483e5-138">マイニング モデルにはフィルターを追加できます。</span><span class="sxs-lookup"><span data-stu-id="483e5-138">You can add a filter to a mining model.</span></span> <span data-ttu-id="483e5-139">フィルターは、モデル ケース内のデータをあるサブセットに制限する一連の WHERE 条件です。</span><span class="sxs-lookup"><span data-stu-id="483e5-139">A filter is a set of WHERE conditions that restrict the data in the model cases to some subset.</span></span> <span data-ttu-id="483e5-140">フィルターは、モデルのトレーニング時に使用します。必要に応じて、モデルのテスト時や、精度チャートの作成時にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="483e5-140">The filter is used when training the model, and can optionally be used when you test the model or create accuracy charts.</span></span>

 <span data-ttu-id="483e5-141">フィルターを追加することによって、マイニング構造を再利用して、広範なデータのサブセットに基づくモデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="483e5-141">By adding filters, you can reuse mining structures but create models based on very different subsets of the data.</span></span> <span data-ttu-id="483e5-142">また、フィルターを使用して、特定の行を除外し、分析の質を高めることもできます。</span><span class="sxs-lookup"><span data-stu-id="483e5-142">Or, you can simply use filters to eliminate certain rows and improve the quality of analysis.</span></span>

 <span data-ttu-id="483e5-143">詳細については、「[マイニング モデルのフィルター選択 (Analysis Services - データ マイニング)](mining-models-analysis-services-data-mining.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="483e5-143">For more information, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md).</span></span>

## <a name="changing-the-algorithm"></a><span data-ttu-id="483e5-144">アルゴリズムの変更</span><span class="sxs-lookup"><span data-stu-id="483e5-144">Changing the Algorithm</span></span>
 <span data-ttu-id="483e5-145">マイニング構造に追加した新しいモデルが同じデータ セットを共有していても、(データでサポートされている) 別のアルゴリズムを使用することや、アルゴリズムのパラメーターを変更することで、異なる結果を得ることができます。</span><span class="sxs-lookup"><span data-stu-id="483e5-145">Although new models that you add to a mining structure share the same data set, you can get different results by using a different algorithm (if the data supports it), or by changing the parameters for the algorithm.</span></span> <span data-ttu-id="483e5-146">また、モデリング フラグを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="483e5-146">You can also set modeling flags.</span></span>

 <span data-ttu-id="483e5-147">アルゴリズムの選択によって、どのような結果が得られるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="483e5-147">The choice of algorithm determines what kind of results you will get.</span></span> <span data-ttu-id="483e5-148">特定のアルゴリズムがどのように動作し、どのようなビジネス シナリオで役立つかについては、「 [データ マイニング アルゴリズム (Analysis Services - データ マイニング)](data-mining-algorithms-analysis-services-data-mining.md)というフラグを列に設定するだけです。</span><span class="sxs-lookup"><span data-stu-id="483e5-148">For general information about how a specific algorithm works, or the business scenarios where you would benefit from using a particular algorithm, see [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>

 <span data-ttu-id="483e5-149">各アルゴリズムの要件、制限、およびサポートされているカスタマイズの詳細については、各アルゴリズムのテクニカル リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="483e5-149">See the technical reference topic for each algorithm for a description of the requirements and restrictions, as well as detailed information about the customizations that each algorithm supports.</span></span>

|||
|-|-|
|[<span data-ttu-id="483e5-150">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-150">Microsoft Decision Trees Algorithm</span></span>](microsoft-decision-trees-algorithm.md)|[<span data-ttu-id="483e5-151">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-151">Microsoft Time Series Algorithm</span></span>](microsoft-time-series-algorithm.md)|
|[<span data-ttu-id="483e5-152">Microsoft クラスタリングアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-152">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)|[<span data-ttu-id="483e5-153">Microsoft ニューラル ネットワーク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-153">Microsoft Neural Network Algorithm</span></span>](microsoft-neural-network-algorithm.md)|
|[<span data-ttu-id="483e5-154">Microsoft Naive Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-154">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)|[<span data-ttu-id="483e5-155">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-155">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)|
|[<span data-ttu-id="483e5-156">Microsoft アソシエーション アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-156">Microsoft Association Algorithm</span></span>](microsoft-association-algorithm.md)|[<span data-ttu-id="483e5-157">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-157">Microsoft Linear Regression Algorithm</span></span>](microsoft-linear-regression-algorithm.md)|
|[<span data-ttu-id="483e5-158">Microsoft シーケンス クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="483e5-158">Microsoft Sequence Clustering Algorithm</span></span>](microsoft-sequence-clustering-algorithm.md)||

## <a name="customizing-algorithm-parameters"></a><span data-ttu-id="483e5-159">アルゴリズム パラメーターのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="483e5-159">Customizing Algorithm Parameters</span></span>
 <span data-ttu-id="483e5-160">各アルゴリズムでは、アルゴリズムの動作をカスタマイズしたり、モデルの結果を細かく調整したりするために使用できるパラメーターがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="483e5-160">Each algorithm supports parameters that you can use to customize the behavior of the algorithm and fine-tune the results of your model.</span></span> <span data-ttu-id="483e5-161">各パラメーターの使用方法については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="483e5-161">For a description of how to use each parameter, see the following topics:</span></span>

 <span data-ttu-id="483e5-162">これらのトピックには、それぞれのアルゴリズムに基づくモデルで使用できる予測関数の一覧も含まれています。</span><span class="sxs-lookup"><span data-stu-id="483e5-162">The topic for each algorithm type also lists the prediction functions that can be used with models based on that algorithm.</span></span>

|<span data-ttu-id="483e5-163">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="483e5-163">Property name</span></span>|<span data-ttu-id="483e5-164">適用対象</span><span class="sxs-lookup"><span data-stu-id="483e5-164">Applies to</span></span>|
|-------------------|----------------|
|<span data-ttu-id="483e5-165">AUTO_DETECT_PERIODICITY</span><span class="sxs-lookup"><span data-stu-id="483e5-165">AUTO_DETECT_PERIODICITY</span></span>|[<span data-ttu-id="483e5-166">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-166">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-167">CLUSTER_COUNT</span><span class="sxs-lookup"><span data-stu-id="483e5-167">CLUSTER_COUNT</span></span>|[<span data-ttu-id="483e5-168">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-168">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-169">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-169">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>](microsoft-sequence-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-170">CLUSTER_SEED</span><span class="sxs-lookup"><span data-stu-id="483e5-170">CLUSTER_SEED</span></span>|[<span data-ttu-id="483e5-171">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-171">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-172">CLUSTERING_METHOD</span><span class="sxs-lookup"><span data-stu-id="483e5-172">CLUSTERING_METHOD</span></span>|[<span data-ttu-id="483e5-173">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-173">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-174">COMPLEXITY_PENALTY</span><span class="sxs-lookup"><span data-stu-id="483e5-174">COMPLEXITY_PENALTY</span></span>|[<span data-ttu-id="483e5-175">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-175">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-176">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-176">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-177">FORCE_REGRESSOR</span><span class="sxs-lookup"><span data-stu-id="483e5-177">FORCE_REGRESSOR</span></span>|[<span data-ttu-id="483e5-178">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-178">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-179">Microsoft 線形回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-179">Microsoft Linear Regression Algorithm Technical Reference</span></span>](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-180">モデリング フラグ (データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="483e5-180">Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|
|<span data-ttu-id="483e5-181">FORECAST_METHOD</span><span class="sxs-lookup"><span data-stu-id="483e5-181">FORECAST_METHOD</span></span>|[<span data-ttu-id="483e5-182">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-182">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-183">HIDDEN_NODE_RATIO</span><span class="sxs-lookup"><span data-stu-id="483e5-183">HIDDEN_NODE_RATIO</span></span>|[<span data-ttu-id="483e5-184">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-184">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-185">HISTORIC_MODEL_COUNT</span><span class="sxs-lookup"><span data-stu-id="483e5-185">HISTORIC_MODEL_COUNT</span></span>|[<span data-ttu-id="483e5-186">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-186">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-187">HISTORICAL_MODEL_GAP</span><span class="sxs-lookup"><span data-stu-id="483e5-187">HISTORICAL_MODEL_GAP</span></span>|[<span data-ttu-id="483e5-188">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-188">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-189">HOLDOUT_PERCENTAGE</span><span class="sxs-lookup"><span data-stu-id="483e5-189">HOLDOUT_PERCENTAGE</span></span>|[<span data-ttu-id="483e5-190">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-190">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-191">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-191">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> <span data-ttu-id="483e5-192">注: このパラメーターは、マイニング構造に適用される提示データ割合値とは異なります。</span><span class="sxs-lookup"><span data-stu-id="483e5-192">Note: This parameter is different from the holdout percentage value that applies to a mining structure.</span></span>|
|<span data-ttu-id="483e5-193">HOLDOUT_SEED</span><span class="sxs-lookup"><span data-stu-id="483e5-193">HOLDOUT_SEED</span></span>|[<span data-ttu-id="483e5-194">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-194">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-195">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-195">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> <span data-ttu-id="483e5-196">注: このパラメーターは、マイニング構造に適用される提示データのシード値とは異なります。</span><span class="sxs-lookup"><span data-stu-id="483e5-196">Note: This parameter is different from the holdout seed value that applies to a mining structure.</span></span>|
|<span data-ttu-id="483e5-197">INSTABILITY_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="483e5-197">INSTABILITY_SENSITIVITY</span></span>|[<span data-ttu-id="483e5-198">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-198">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-199">MAXIMUM_INPUT_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="483e5-199">MAXIMUM_INPUT_ATTRIBUTES</span></span>|[<span data-ttu-id="483e5-200">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-200">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-201">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-201">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-202">Microsoft 線形回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-202">Microsoft Linear Regression Algorithm Technical Reference</span></span>](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-203">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-203">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-204">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-204">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-205">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-205">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-206">MAXIMUM_ITEMSET_COUNT</span><span class="sxs-lookup"><span data-stu-id="483e5-206">MAXIMUM_ITEMSET_COUNT</span></span>|[<span data-ttu-id="483e5-207">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-207">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-208">MAXIMUM_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="483e5-208">MAXIMUM_ITEMSET_SIZE</span></span>|[<span data-ttu-id="483e5-209">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-209">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-210">MAXIMUM_OUTPUT_ATTRIBUTES</span><span class="sxs-lookup"><span data-stu-id="483e5-210">MAXIMUM_OUTPUT_ATTRIBUTES</span></span>|[<span data-ttu-id="483e5-211">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-211">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-212">Microsoft 線形回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-212">Microsoft Linear Regression Algorithm Technical Reference</span></span>](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-213">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-213">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-214">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-214">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-215">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-215">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-216">MAXIMUM_SEQUENCE_STATES</span><span class="sxs-lookup"><span data-stu-id="483e5-216">MAXIMUM_SEQUENCE_STATES</span></span>|[<span data-ttu-id="483e5-217">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-217">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>](microsoft-sequence-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-218">MAXIMUM_SERIES_VALUE</span><span class="sxs-lookup"><span data-stu-id="483e5-218">MAXIMUM_SERIES_VALUE</span></span>|[<span data-ttu-id="483e5-219">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-219">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-220">MAXIMUM_STATES</span><span class="sxs-lookup"><span data-stu-id="483e5-220">MAXIMUM_STATES</span></span>|[<span data-ttu-id="483e5-221">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-221">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-222">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-222">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-223">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-223">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>](microsoft-sequence-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-224">MAXIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="483e5-224">MAXIMUM_SUPPORT</span></span>|[<span data-ttu-id="483e5-225">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-225">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-226">MINIMUM_IMPORTANCE</span><span class="sxs-lookup"><span data-stu-id="483e5-226">MINIMUM_IMPORTANCE</span></span>|[<span data-ttu-id="483e5-227">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-227">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-228">MINIMUM_ITEMSET_SIZE</span><span class="sxs-lookup"><span data-stu-id="483e5-228">MINIMUM_ITEMSET_SIZE</span></span>|[<span data-ttu-id="483e5-229">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-229">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-230">MINIMUM_DEPENDENCY_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="483e5-230">MINIMUM_DEPENDENCY_PROBABILITY</span></span>|[<span data-ttu-id="483e5-231">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-231">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](microsoft-naive-bayes-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-232">MINIMUM_PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="483e5-232">MINIMUM_PROBABILITY</span></span>|[<span data-ttu-id="483e5-233">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-233">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-234">MINIMUM_SERIES_VALUE</span><span class="sxs-lookup"><span data-stu-id="483e5-234">MINIMUM_SERIES_VALUE</span></span>|[<span data-ttu-id="483e5-235">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-235">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-236">MINIMUM_SUPPORT</span><span class="sxs-lookup"><span data-stu-id="483e5-236">MINIMUM_SUPPORT</span></span>|[<span data-ttu-id="483e5-237">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-237">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-238">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-238">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-239">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-239">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-240">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-240">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>](microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-241">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-241">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-242">MISSING_VALUE_SUBSTITUTION</span><span class="sxs-lookup"><span data-stu-id="483e5-242">MISSING_VALUE_SUBSTITUTION</span></span>|[<span data-ttu-id="483e5-243">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-243">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-244">MODELLING_CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="483e5-244">MODELLING_CARDINALITY</span></span>|[<span data-ttu-id="483e5-245">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-245">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-246">PERIODICITY_HINT</span><span class="sxs-lookup"><span data-stu-id="483e5-246">PERIODICITY_HINT</span></span>|[<span data-ttu-id="483e5-247">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-247">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-248">PREDICTION_SMOOTHING</span><span class="sxs-lookup"><span data-stu-id="483e5-248">PREDICTION_SMOOTHING</span></span>|[<span data-ttu-id="483e5-249">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-249">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-250">SAMPLE_SIZE</span><span class="sxs-lookup"><span data-stu-id="483e5-250">SAMPLE_SIZE</span></span>|[<span data-ttu-id="483e5-251">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-251">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-252">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-252">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="483e5-253">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="483e5-253">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-254">SCORE_METHOD</span><span class="sxs-lookup"><span data-stu-id="483e5-254">SCORE_METHOD</span></span>|[<span data-ttu-id="483e5-255">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-255">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-256">SPLIT_METHOD</span><span class="sxs-lookup"><span data-stu-id="483e5-256">SPLIT_METHOD</span></span>|[<span data-ttu-id="483e5-257">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-257">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)|
|<span data-ttu-id="483e5-258">STOPPING_TOLERANCE</span><span class="sxs-lookup"><span data-stu-id="483e5-258">STOPPING_TOLERANCE</span></span>|[<span data-ttu-id="483e5-259">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="483e5-259">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)|

## <a name="see-also"></a><span data-ttu-id="483e5-260">参照</span><span class="sxs-lookup"><span data-stu-id="483e5-260">See Also</span></span>
 <span data-ttu-id="483e5-261">データマイニング[アルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining-algorithms-analysis-services-data-mining.md) [物理アーキテクチャ &#40;Analysis Services データマイニング&#41;](physical-architecture-analysis-services-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="483e5-261">[Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md) [Physical Architecture &#40;Analysis Services - Data Mining&#41;](physical-architecture-analysis-services-data-mining.md)</span></span>

