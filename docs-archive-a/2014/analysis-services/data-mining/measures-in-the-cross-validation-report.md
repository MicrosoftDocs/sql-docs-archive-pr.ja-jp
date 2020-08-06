---
title: 相互検証レポートのメジャー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- root mean square error [data mining]
- cross-validation [data mining]
- mean absolute error [data mining]
- log score [data mining]
- likelihood [data mining]
ms.assetid: a07b1665-7f72-4266-82a4-43a91ae2571d
author: minewiskan
ms.author: owend
ms.openlocfilehash: b71c04551efc17b52f969a9a632241e7d235afd3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645919"
---
# <a name="measures-in-the-cross-validation-report"></a><span data-ttu-id="876ef-102">相互検証レポートのメジャー</span><span class="sxs-lookup"><span data-stu-id="876ef-102">Measures in the Cross-Validation Report</span></span>
  <span data-ttu-id="876ef-103">相互検証では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はマイニング構造のデータを複数のセクションにパーティション分割し、構造および関連マイニング モデルのテストを反復的に実行します。</span><span class="sxs-lookup"><span data-stu-id="876ef-103">During cross-validation, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] divides the data in a mining structure into multiple cross-sections and then iteratively tests the structure and any associated mining models.</span></span> <span data-ttu-id="876ef-104">この分析に基づき、構造および各モデルの標準の精度のメジャーを出力します。</span><span class="sxs-lookup"><span data-stu-id="876ef-104">Based on this analysis, it outputs a set of standard accuracy measures for the structure and each model.</span></span>  
  
 <span data-ttu-id="876ef-105">レポートでは、データ内のフォールドの数や各フォールド内のデータの量に関するいくつかの基本情報に加えて、データの分布を示す一連の一般的な基準が表示されます。</span><span class="sxs-lookup"><span data-stu-id="876ef-105">The report contains some basic information about the number of folds in the data and the amount of data in each fold, and a set of general metrics that describe data distribution.</span></span> <span data-ttu-id="876ef-106">それぞれのセクションに対する一般的な基準を比較することで、構造またはモデルの信頼性を評価できます。</span><span class="sxs-lookup"><span data-stu-id="876ef-106">By comparing the general metrics for each cross-section, you can assess the reliability of the structure or model.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="876ef-107">には、マイニング モデルの一連の詳細メジャーも表示されます。</span><span class="sxs-lookup"><span data-stu-id="876ef-107">also displays a set of detailed measures for mining models.</span></span> <span data-ttu-id="876ef-108">これらのメジャーは、分析するモデルの種類や、不連続であるか連続であるかなど属性の型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="876ef-108">These measures depend on the model type and on the type of attribute that is being analyzed: for example, whether it is discrete or continuous.</span></span>  
  
 <span data-ttu-id="876ef-109">ここでは、 **[相互検証]** レポートに含まれるメジャーおよびその意味の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-109">This section provides a list of the measures that are contained in the **Cross-Validation** report, and what they mean.</span></span> <span data-ttu-id="876ef-110">各メジャーの計算方法の詳細については、「 [クロス検証の式](cross-validation-formulas.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="876ef-110">For details on how each measure is calculated, see [Cross-Validation Formulas](cross-validation-formulas.md).</span></span>  
  
## <a name="list-of-measures-in-the-cross-validation-report"></a><span data-ttu-id="876ef-111">相互検証レポートのメジャーの一覧</span><span class="sxs-lookup"><span data-stu-id="876ef-111">List of Measures in the Cross-Validation Report</span></span>  
 <span data-ttu-id="876ef-112">次の表は、相互検証レポートに表示されるメジャーの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-112">The following table lists the measures that appear in the cross-validation report.</span></span> <span data-ttu-id="876ef-113">メジャーは、表の左の列に表示されている *テストの種類*でグループ化されています。</span><span class="sxs-lookup"><span data-stu-id="876ef-113">The measures are grouped by *test type*, which is provided in the left-hand column of the following table.</span></span> <span data-ttu-id="876ef-114">右の列には、レポートに表示されるメジャーの名前、および意味に関する簡単な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-114">The right-hand column lists the name of the measure as it appears in the report, and provides a brief explanation of what it means.</span></span>  
  
|<span data-ttu-id="876ef-115">テストの種類</span><span class="sxs-lookup"><span data-stu-id="876ef-115">Test Type</span></span>|<span data-ttu-id="876ef-116">基準と説明</span><span class="sxs-lookup"><span data-stu-id="876ef-116">Measures and Descriptions</span></span>|  
|---------------|-------------------------------|  
|<span data-ttu-id="876ef-117">クラスタリング</span><span class="sxs-lookup"><span data-stu-id="876ef-117">Clustering</span></span>|<span data-ttu-id="876ef-118">クラスターモデルに適用されるメジャー:</span><span class="sxs-lookup"><span data-stu-id="876ef-118">Measures that apply to clustering models:</span></span><br /><br /> <span data-ttu-id="876ef-119">**ケースの確率**: このメジャーは、通常、ケースが特定のクラスターに属している可能性を示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-119">**Case likelihood**: This measure usually indicates how likely it is that a case belongs to a particular cluster.</span></span> <br />                      <span data-ttu-id="876ef-120">相互検証の場合、スコアが集計された後、ケースの数で割られます。スコアは、ケースの平均確率となります。</span><span class="sxs-lookup"><span data-stu-id="876ef-120">For cross-validation, the scores are summed and then divided by the number of cases, so here the score is an average case likelihood.</span></span>|  
|<span data-ttu-id="876ef-121">分類</span><span class="sxs-lookup"><span data-stu-id="876ef-121">Classification</span></span>|<span data-ttu-id="876ef-122">分類モデルに適用されるメジャー:</span><span class="sxs-lookup"><span data-stu-id="876ef-122">Measures that apply to classification models:</span></span><br /><br /> <span data-ttu-id="876ef-123">**真陽性**/</span><span class="sxs-lookup"><span data-stu-id="876ef-123">**True Positive**/</span></span><br />                      <span data-ttu-id="876ef-124">**真の負の値** / **偽陽性** / **False 陽性**: 予測された状態が対象の状態と一致するパーティション内の行または値の数と、予測確率が指定したしきい値を超えています。</span><span class="sxs-lookup"><span data-stu-id="876ef-124">**True Negative**/ **False Positive**/ **False Positive**: Count of rows or values in the partition where the predicted state matches the target state, and the predict probability is greater than the specified threshold.</span></span> <span data-ttu-id="876ef-125">対象の属性の不足値があるケースは除外されます。つまり、すべての値のカウントが加算されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="876ef-125">Cases that have missing values for the target attribute are excluded, meaning the counts of all values might not add up</span></span>|  
||<span data-ttu-id="876ef-126">**成功/失敗**: 予測された状態が対象の状態と一致し、予測確率値が0より大きいパーティション内の行または値の数。</span><span class="sxs-lookup"><span data-stu-id="876ef-126">**Pass/Fail**: Count of rows or values in the partition where the predicted state matches the target state, and where the predict probability value is greater than 0.</span></span>|  
|<span data-ttu-id="876ef-127">Likelihood</span><span class="sxs-lookup"><span data-stu-id="876ef-127">Likelihood</span></span>|<span data-ttu-id="876ef-128">複数のモデルの種類に適用される確率メジャー:</span><span class="sxs-lookup"><span data-stu-id="876ef-128">Likelihood measures apply to multiple model types:</span></span><br /><br /> <span data-ttu-id="876ef-129">**リフト**: テストケースの確率に対する実際の予測確率の比率。</span><span class="sxs-lookup"><span data-stu-id="876ef-129">**Lift**: The ratio of the actual prediction probability to the marginal probability in the test cases.</span></span> <span data-ttu-id="876ef-130">対象の属性の不足値があるケースは除外されます。</span><span class="sxs-lookup"><span data-stu-id="876ef-130">Rows that have missing values for the target attribute are excluded.</span></span> <span data-ttu-id="876ef-131">通常、モデルが使用されるときに対象の結果の確率がどれだけ向上するかを示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-131">This measure generally shows how much the probability of the target outcome improves when the model is used.</span></span><br /><br /> <span data-ttu-id="876ef-132">**平方根平均二乗誤差**: パーティション内のケースの数で割った、すべてのパーティションケースの平均誤差の平方根。対象の属性の不足値がある行は除外されます。</span><span class="sxs-lookup"><span data-stu-id="876ef-132">**Root Mean Square Error**: Square root of the mean error for all partition cases, divided by the number of cases in the partition, excluding rows that have missing values for the target attribute.</span></span> <span data-ttu-id="876ef-133">RMSE は、予測モデルの一般的な推定機能です。</span><span class="sxs-lookup"><span data-stu-id="876ef-133">RMSE is a popular estimator for predictive models.</span></span> <span data-ttu-id="876ef-134">スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。</span><span class="sxs-lookup"><span data-stu-id="876ef-134">The score averages the residuals for each case to yield a single indicator of model error.</span></span><br /><br /> <span data-ttu-id="876ef-135">**ログスコア**: 集計された各ケースの実際の確率の対数。入力データセットの行数で割った値 (対象の属性の欠損値がある行は除く)。</span><span class="sxs-lookup"><span data-stu-id="876ef-135">**Log score**: The logarithm of the actual probability for each case, summed, and then divided by the number of rows in the input dataset, excluding rows that have missing values for the target attribute.</span></span> <span data-ttu-id="876ef-136">確率は小数で表されるので、ログ スコアは常に負の数値になります。</span><span class="sxs-lookup"><span data-stu-id="876ef-136">Because probability is represented as a decimal fraction, log scores are always negative numbers.</span></span> <span data-ttu-id="876ef-137">0 に近い数値ほど、良いスコアになります。</span><span class="sxs-lookup"><span data-stu-id="876ef-137">A number closer to 0 is a better score.</span></span> <span data-ttu-id="876ef-138">生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。</span><span class="sxs-lookup"><span data-stu-id="876ef-138">Whereas raw scores can have very irregular or skewed distributions, a log score is similar to a percentage.</span></span>|  
|<span data-ttu-id="876ef-139">推定</span><span class="sxs-lookup"><span data-stu-id="876ef-139">Estimation</span></span>|<span data-ttu-id="876ef-140">連続する数値属性を予測する推定モデルにのみ適用されるメジャー:</span><span class="sxs-lookup"><span data-stu-id="876ef-140">Measures that apply only to estimation models, which predict a continuous numeric attribute:</span></span><br /><br /> <span data-ttu-id="876ef-141">**平方根平均二乗誤差**: 予測値が実際の値と比較されるときの平均誤差。</span><span class="sxs-lookup"><span data-stu-id="876ef-141">**Root Mean Square Error**: Average error when the predicted value is compared to the actual value.</span></span> <span data-ttu-id="876ef-142">RMSE は、予測モデルの一般的な推定機能です。</span><span class="sxs-lookup"><span data-stu-id="876ef-142">RMSE is a popular estimator for predictive models.</span></span> <span data-ttu-id="876ef-143">スコアは各ケースの残差を平均し、モデル誤差の 1 つのインジケーターを生成します。</span><span class="sxs-lookup"><span data-stu-id="876ef-143">The score averages the residuals for each case to yield a single indicator of model error.</span></span><br /><br /> <span data-ttu-id="876ef-144">**平均絶対誤差**: 予測値が実際の値と比較されるときの平均誤差。誤差の絶対合計の平均として計算されます。</span><span class="sxs-lookup"><span data-stu-id="876ef-144">**Mean Absolute Error**: Average error when predicted values are compared to actual values, calculated as the mean of the absolute sum of errors.</span></span> <span data-ttu-id="876ef-145">平均絶対誤差は、予測全体が実際の値にどの程度近いかを判断するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="876ef-145">Mean absolute error is useful for understanding how close overall the predictions were to actual values.</span></span> <span data-ttu-id="876ef-146">小さいスコアは、予測が正確だったことを意味します。</span><span class="sxs-lookup"><span data-stu-id="876ef-146">A smaller score means predictions were more accurate.</span></span><br /><br /> <span data-ttu-id="876ef-147">**ログスコア**: 集計された各ケースの実際の確率の対数。入力データセットの行数で割った値 (対象の属性の欠損値がある行は除く)。</span><span class="sxs-lookup"><span data-stu-id="876ef-147">**Log Score**: The logarithm of the actual probability for each case, summed, and then divided by the number of rows in the input dataset, excluding rows that have missing values for the target attribute.</span></span> <span data-ttu-id="876ef-148">確率は小数で表されるので、ログ スコアは常に負の数値になります。</span><span class="sxs-lookup"><span data-stu-id="876ef-148">Because probability is represented as a decimal fraction, log scores are always negative numbers.</span></span> <span data-ttu-id="876ef-149">0 に近い数値ほど、良いスコアになります。</span><span class="sxs-lookup"><span data-stu-id="876ef-149">A number closer to 0 is a better score.</span></span> <span data-ttu-id="876ef-150">生のスコアが非常に不規則な分布またはゆがんだ分布を持つのに対し、ログ スコアは割合に似ています。</span><span class="sxs-lookup"><span data-stu-id="876ef-150">Whereas raw scores can have very irregular or skewed distributions, a log score is similar to a percentage.</span></span>|  
|<span data-ttu-id="876ef-151">集計</span><span class="sxs-lookup"><span data-stu-id="876ef-151">Aggregates</span></span>|<span data-ttu-id="876ef-152">集計メジャーは、各パーティションの結果における分散を示します。</span><span class="sxs-lookup"><span data-stu-id="876ef-152">Aggregate measures provide an indication of the variance in the results for each partition:</span></span><br /><br /> <span data-ttu-id="876ef-153">**平均**: 特定のメジャーのパーティション値の平均。</span><span class="sxs-lookup"><span data-stu-id="876ef-153">**Mean**: Average of the partition values for a particular measure.</span></span><br /><br /> <span data-ttu-id="876ef-154">**標準偏差**: モデル内のすべてのパーティションにわたる、特定のメジャーの平均値からの偏差の平均です。</span><span class="sxs-lookup"><span data-stu-id="876ef-154">**Standard Deviation**: Average of the deviation from the mean for a specific measure, across all the partitions in a model.</span></span> <span data-ttu-id="876ef-155">相互検証の場合、このスコアの値が高いことは、フォールドの間の変動が大きいことを意味します。</span><span class="sxs-lookup"><span data-stu-id="876ef-155">For cross-validation, a higher value for this score implies substantial variation between the folds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="876ef-156">参照</span><span class="sxs-lookup"><span data-stu-id="876ef-156">See Also</span></span>  
 [<span data-ttu-id="876ef-157">テストおよび検証 &#40;データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="876ef-157">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  