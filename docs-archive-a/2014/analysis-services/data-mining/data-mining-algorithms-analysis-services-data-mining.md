---
title: データマイニングアルゴリズム (Analysis Services-データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- segmentation algorithms [Analysis Services]
- clustering [Data Mining]
- learning algorithms
- data mining [Analysis Services], models
- algorithms [data mining]
- mining models [Analysis Services], algorithms
- inductive learning
- mining models [Analysis Services], creating
- data mining [Analysis Services], algorithms
- machine learning algorithms [Analysis Services]
ms.assetid: ed1fc83b-b98c-437e-bf53-4ff001b92d64
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3e6a653132da045d111cebc43972dfbfb368a2be
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644235"
---
# <a name="data-mining-algorithms-analysis-services---data-mining"></a><span data-ttu-id="4cf5f-102">データ マイニング アルゴリズム (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="4cf5f-102">Data Mining Algorithms (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="4cf5f-103">*データマイニングアルゴリズム*は、データからデータマイニングモデルを作成する一連のヒューリスティックと計算です。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-103">A *data mining algorithm* is a set of heuristics and calculations that creates a data mining model from data.</span></span> <span data-ttu-id="4cf5f-104">モデルを作成するために、データ マイニング アルゴリズムは、まず提供されたデータを分析し、特定の種類のパターンまたは傾向を探します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-104">To create a model, the algorithm first analyzes the data you provide, looking for specific types of patterns or trends.</span></span> <span data-ttu-id="4cf5f-105">この分析の結果は、マイニング モデルを作成するための最適化されたパラメーターを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-105">The algorithm uses the results of this analysis to define the optimal parameters for creating the mining model.</span></span> <span data-ttu-id="4cf5f-106">これらのパラメーターはデータセット全体に適用され、実用的なパターンおよび詳細な統計情報が抽出されます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-106">These parameters are then applied across the entire data set to extract actionable patterns and detailed statistics.</span></span>  
  
 <span data-ttu-id="4cf5f-107">アルゴリズムによってデータから作成されるマイニング モデルは、次のようにさまざまな形式を取ります。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-107">The mining model that an algorithm creates from your data can take various forms, including:</span></span>  
  
-   <span data-ttu-id="4cf5f-108">データセット内のケースの関係を説明するクラスターのセット</span><span class="sxs-lookup"><span data-stu-id="4cf5f-108">A set of clusters that describe how the cases in a dataset are related.</span></span>  
  
-   <span data-ttu-id="4cf5f-109">結果を予測し、基準を変更するとその結果がどのように影響を受けるのかを示すデシジョン ツリー</span><span class="sxs-lookup"><span data-stu-id="4cf5f-109">A decision tree that predicts an outcome, and describes how different criteria affect that outcome.</span></span>  
  
-   <span data-ttu-id="4cf5f-110">売上を予想する数学的モデル</span><span class="sxs-lookup"><span data-stu-id="4cf5f-110">A mathematical model that forecasts sales.</span></span>  
  
-   <span data-ttu-id="4cf5f-111">複数の製品を 1 つのトランザクションにグループ化する方法、およびそれらの製品がまとめて購入される確率を示すルールのセット</span><span class="sxs-lookup"><span data-stu-id="4cf5f-111">A set of rules that describe how products are grouped together in a transaction, and the probabilities that products are purchased together.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="4cf5f-112">に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、データマイニングソリューションで使用する複数のアルゴリズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides multiple algorithms for use in your data mining solutions.</span></span> <span data-ttu-id="4cf5f-113">これらのアルゴリズムは、データ マイニングで使用される最も人気のある方法論のうちのいくつかを実装したものです。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-113">These algorithms are implementations of some of the most popular methodologies used in data mining.</span></span> <span data-ttu-id="4cf5f-114">どの Microsoft データ マイニング アルゴリズムも、カスタマイズ可能であり、用意されている API または SQL Server Integration Services のデータ マイニング コンポーネントを使用して十分にプログラムできます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-114">All of the Microsoft data mining algorithms can be customized and are fully programmable using the provided APIs, or by using the data mining components in SQL Server Integration Services.</span></span>  
  
 <span data-ttu-id="4cf5f-115">また、OLE DB for Data Mining 仕様に準拠するサードパーティ製アルゴリズムを使用することも、またはサービスとして登録してから SQL Server データ マイニング フレームワーク内で使用できるカスタム アルゴリズムを開発することもできます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-115">You can also use third-party algorithms that comply with the OLE DB for Data Mining specification, or develop custom algorithms that can be registered as services and then used within the SQL Server Data Mining framework.</span></span>  
  
## <a name="choosing-the-right-algorithm"></a><span data-ttu-id="4cf5f-116">適切なアルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="4cf5f-116">Choosing the Right Algorithm</span></span>  
 <span data-ttu-id="4cf5f-117">特定の分析タスクに使用する最適なアルゴリズムを選択するのが困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-117">Choosing the best algorithm to use for a specific analytical task can be a challenge.</span></span> <span data-ttu-id="4cf5f-118">異なるアルゴリズムを使用して同じビジネス タスクを実行できる一方、各アルゴリズムによって異なる結果が生成されたり、一部のアルゴリズムでは複数の種類の結果が生成されたりする場合があります。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-118">While you can use different algorithms to perform the same business task, each algorithm produces a different result, and some algorithms can produce more than one type of result.</span></span> <span data-ttu-id="4cf5f-119">たとえば、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] デシジョン ツリー アルゴリズムは、予測だけでなく、データセット内の列の数を減らす方法としても使用できます。これは、デシジョン ツリーが、最終的なマイニング モデルに影響を与えない列を識別できるためです。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-119">For example, you can use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm not only for prediction, but also as a way to reduce the number of columns in a dataset, because the decision tree can identify columns that do not affect the final mining model.</span></span>  
  
### <a name="choosing-an-algorithm-by-type"></a><span data-ttu-id="4cf5f-120">種類別アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="4cf5f-120">Choosing an Algorithm by Type</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="4cf5f-121">には、次の種類のアルゴリズムが含まれます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-121">includes the following algorithm types:</span></span>  
  
-   <span data-ttu-id="4cf5f-122">**分類アルゴリズム** 。データセット内の他の属性に基づいて、1 つまたは複数の離散変数を予測します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-122">**Classification algorithms** predict one or more discrete variables, based on the other attributes in the dataset.</span></span>  
  
-   <span data-ttu-id="4cf5f-123">**回帰アルゴリズム**では、データセット内の他の属性に基づいて、利益や損失などの1つ以上の連続変数を予測します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-123">**Regression algorithms** predict one or more continuous variables, such as profit or loss, based on other attributes in the dataset.</span></span>  
  
-   <span data-ttu-id="4cf5f-124">**分割アルゴリズム** 。データを、類似したプロパティを持つアイテムのグループまたはクラスターに分割します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-124">**Segmentation algorithms** divide data into groups, or clusters, of items that have similar properties.</span></span>  
  
-   <span data-ttu-id="4cf5f-125">**アソシエーション アルゴリズム** 。データセット内の異なる属性間の相関関係を検出します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-125">**Association algorithms** find correlations between different attributes in a dataset.</span></span> <span data-ttu-id="4cf5f-126">この種類のアルゴリズムの最も一般的な使用例は、マーケット バスケット分析で使用するアソシエーション ルールの作成です。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-126">The most common application of this kind of algorithm is for creating association rules, which can be used in a market basket analysis.</span></span>  
  
-   <span data-ttu-id="4cf5f-127">**シーケンス分析アルゴリズム**は、Web パスフローなど、データ内の頻度の高いシーケンスまたはエピソードを要約します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-127">**Sequence analysis algorithms** summarize frequent sequences or episodes in data, such as a Web path flow.</span></span>  
  
 <span data-ttu-id="4cf5f-128">ただし、ソリューションが複数ある中で、1 つのアルゴリズムに限定される必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-128">However, there is no reason that you should be limited to one algorithm in your solutions.</span></span> <span data-ttu-id="4cf5f-129">経験豊富なアナリストであれば、ある 1 つのアルゴリズムを使用して最も効果的な入力 (つまり変数) を判断し、次に別のアルゴリズムを適用してそのデータに基づいて特定の結果を予測するものです。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-129">Experienced analysts will sometimes use one algorithm to determine the most effective inputs (that is, variables), and then apply a different algorithm to predict a specific outcome based on that data.</span></span> <span data-ttu-id="4cf5f-130">SQL Server データ マイニングでは、1 つのマイニング構造上に複数のモデルを構築できます。そのため、1 つのデータ マイニング ソリューション内でクラスタリング アルゴリズム、デシジョン ツリー モデル、および Naïve Bayes モデルを使用して、データに関するさまざまなビューを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-130">SQL Server data mining lets you build multiple models on a single mining structure, so within a single data mining solution you might use a clustering algorithm, a decision trees model, and a naïve Bayes model to get different views on your data.</span></span> <span data-ttu-id="4cf5f-131">また、1 つのソリューション内で複数のアルゴリズムを使用して、個別のタスクを実行することもできます。たとえば、回帰を使用して財務予測を取得したり、ニューラル ネットワーク アルゴリズムを使用して売上に影響を及ぼす因子を分析したりできます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-131">You might also use multiple algorithms within a single solution to perform separate tasks: for example, you could use regression to obtain financial forecasts, and use a neural network algorithm to perform an analysis of factors that influence sales.</span></span>  
  
### <a name="choosing-an-algorithm-by-task"></a><span data-ttu-id="4cf5f-132">タスク別アルゴリズムの選択</span><span class="sxs-lookup"><span data-stu-id="4cf5f-132">Choosing an Algorithm by Task</span></span>  
 <span data-ttu-id="4cf5f-133">特定のタスクで使用するアルゴリズムの選択の参考として、各アルゴリズムが長年使用されてきたタスクを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-133">To help you select an algorithm for use with a specific task, the following table provides suggestions for the types of tasks for which each algorithm is traditionally used.</span></span>  
  
|<span data-ttu-id="4cf5f-134">タスクの例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-134">Examples of tasks</span></span>|<span data-ttu-id="4cf5f-135">使用する Microsoft アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-135">Microsoft algorithms to use</span></span>|  
|-----------------------|---------------------------------|  
|<span data-ttu-id="4cf5f-136">**不連続属性の予測**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-136">**Predicting a discrete attribute**</span></span><br /><br /> <span data-ttu-id="4cf5f-137">見込み客リスト内の顧客について、見込みがあるかないかをフラグで示します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-137">Flag the customers in a prospective buyers list as good or poor prospects.</span></span><br /><br /> <span data-ttu-id="4cf5f-138">あるサーバーに半年以内に障害が発生する確率を計算します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-138">Calculate the probability that a server will fail within the next 6 months.</span></span><br /><br /> <span data-ttu-id="4cf5f-139">患者の転帰を分類し、関連因子を探ります。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-139">Categorize patient outcomes and explore related factors.</span></span>|[<span data-ttu-id="4cf5f-140">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-140">Microsoft Decision Trees Algorithm</span></span>](microsoft-decision-trees-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-141">Microsoft Naive Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-141">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-142">Microsoft クラスタリングアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-142">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-143">Microsoft ニューラル ネットワーク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-143">Microsoft Neural Network Algorithm</span></span>](microsoft-neural-network-algorithm.md)|  
|<span data-ttu-id="4cf5f-144">**連続属性の予測**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-144">**Predicting a continuous attribute**</span></span><br /><br /> <span data-ttu-id="4cf5f-145">翌年の売上を予測します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-145">Forecast next year's sales.</span></span><br /><br /> <span data-ttu-id="4cf5f-146">過去の歴史的、季節的傾向を考慮に入れて、来場者を予測します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-146">Predict site visitors given past historical and seasonal trends.</span></span><br /><br /> <span data-ttu-id="4cf5f-147">人口統計を考慮に入れて、リスク スコアを生成します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-147">Generate a risk score given demographics.</span></span>|[<span data-ttu-id="4cf5f-148">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-148">Microsoft Decision Trees Algorithm</span></span>](microsoft-decision-trees-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-149">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-149">Microsoft Time Series Algorithm</span></span>](microsoft-time-series-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-150">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-150">Microsoft Linear Regression Algorithm</span></span>](microsoft-linear-regression-algorithm.md)|  
|<span data-ttu-id="4cf5f-151">**シーケンスの予測**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-151">**Predicting a sequence**</span></span><br /><br /> <span data-ttu-id="4cf5f-152">ある企業の Web サイトのクリックストリーム分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-152">Perform clickstream analysis of a company's Web site.</span></span><br /><br /> <span data-ttu-id="4cf5f-153">サーバーの障害につながる要因を分析します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-153">Analyze the factors leading to server failure.</span></span><br /><br /> <span data-ttu-id="4cf5f-154">外来患者の来院中の一連の行動を把握し分析して、共通する行動に関するベスト プラクティスを組み立てます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-154">Capture and analyze sequences of activities during outpatient visits, to formulate best practices around common activities.</span></span>|[<span data-ttu-id="4cf5f-155">Microsoft シーケンス クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-155">Microsoft Sequence Clustering Algorithm</span></span>](microsoft-sequence-clustering-algorithm.md)|  
|<span data-ttu-id="4cf5f-156">**トランザクション内の共通アイテムのグループの検索**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-156">**Finding groups of common items in transactions**</span></span><br /><br /> <span data-ttu-id="4cf5f-157">マーケット バスケット分析を使用して、製品の配置を決定します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-157">Use market basket analysis to determine product placement.</span></span><br /><br /> <span data-ttu-id="4cf5f-158">ある顧客に追加購入を勧める製品を提案します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-158">Suggest additional products to a customer for purchase.</span></span><br /><br /> <span data-ttu-id="4cf5f-159">ある 1 件のイベントへの来場者の調査データを分析して、相関関係のある行動またはブースを特定し、今後の活動計画を立てます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-159">Analyze survey data from visitors to an event, to find which activities or booths were correlated, to plan future activities.</span></span>|[<span data-ttu-id="4cf5f-160">Microsoft アソシエーション アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-160">Microsoft Association Algorithm</span></span>](microsoft-association-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-161">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-161">Microsoft Decision Trees Algorithm</span></span>](microsoft-decision-trees-algorithm.md)|  
|<span data-ttu-id="4cf5f-162">**類似した項目のグループの検索**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-162">**Finding groups of similar items**</span></span><br /><br /> <span data-ttu-id="4cf5f-163">人口統計や行動などの属性に基づいて、患者リスク プロファイル グループを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-163">Create patient risk profiles groups based on attributes such as demographics and behaviors.</span></span><br /><br /> <span data-ttu-id="4cf5f-164">ユーザーを閲覧パターンと購買パターンで分析します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-164">Analyze users by browsing and buying patterns.</span></span><br /><br /> <span data-ttu-id="4cf5f-165">同じような使用状況特性を持つサーバーを特定します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-165">Identify servers that have similar usage characteristics.</span></span>|[<span data-ttu-id="4cf5f-166">Microsoft クラスタリングアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-166">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-167">Microsoft シーケンス クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-167">Microsoft Sequence Clustering Algorithm</span></span>](microsoft-sequence-clustering-algorithm.md)|  
  
## <a name="related-content"></a><span data-ttu-id="4cf5f-168">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="4cf5f-168">Related Content</span></span>  
 <span data-ttu-id="4cf5f-169">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に用意されている各データ マイニング アルゴリズムの学習用リソースのリンクを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-169">The following table provides links to learning resources for each of the data mining algorithms that are provided in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4cf5f-170">**基本的なアルゴリズムの説明**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-170">**Basic algorithm description**</span></span>|<span data-ttu-id="4cf5f-171">アルゴリズムが行うことと機能のしくみについて説明し、そのアルゴリズムが役に立つ可能性のあるビジネス シナリオの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-171">Explains what the algorithm does and how it works, and outlines possible business scenarios where the algorithm might be useful.</span></span>|  
||[<span data-ttu-id="4cf5f-172">Microsoft アソシエーション アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-172">Microsoft Association Algorithm</span></span>](microsoft-association-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-173">Microsoft クラスタリングアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-173">Microsoft Clustering Algorithm</span></span>](microsoft-clustering-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-174">Microsoft デシジョンツリーアルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-174">Microsoft Decision Trees Algorithm</span></span>](microsoft-decision-trees-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-175">Microsoft 線形回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-175">Microsoft Linear Regression Algorithm</span></span>](microsoft-linear-regression-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-176">Microsoft ロジスティック回帰アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-176">Microsoft Logistic Regression Algorithm</span></span>](microsoft-logistic-regression-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-177">Microsoft Naive Bayes アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-177">Microsoft Naive Bayes Algorithm</span></span>](microsoft-naive-bayes-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-178">Microsoft ニューラル ネットワーク アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-178">Microsoft Neural Network Algorithm</span></span>](microsoft-neural-network-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-179">Microsoft シーケンス クラスタリング アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-179">Microsoft Sequence Clustering Algorithm</span></span>](microsoft-sequence-clustering-algorithm.md)<br /><br /> [<span data-ttu-id="4cf5f-180">Microsoft Time Series アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-180">Microsoft Time Series Algorithm</span></span>](microsoft-time-series-algorithm.md)|  
|<span data-ttu-id="4cf5f-181">**テクニカル リファレンス**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-181">**Technical reference**</span></span>|<span data-ttu-id="4cf5f-182">アルゴリズムの実装について、必要に応じて学術的参考文献を示しながら、技術的詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-182">Provides technical detail about the implementation of the algorithm, with academic references as necessary.</span></span> <span data-ttu-id="4cf5f-183">アルゴリズムの動作を制御したり、モデルの結果をカスタマイズしたりするために設定できるパラメーターを列挙します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-183">Lists the parameters that you can set to control the behavior of the algorithm and customize the results in the model.</span></span> <span data-ttu-id="4cf5f-184">データ要件について説明し、可能であればパフォーマンスのヒントを提供します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-184">Describes data requirements and provides performance tips if possible.</span></span>|  
||[<span data-ttu-id="4cf5f-185">Microsoft アソシエーション アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-185">Microsoft Association Algorithm Technical Reference</span></span>](microsoft-association-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-186">Microsoft クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-186">Microsoft Clustering Algorithm Technical Reference</span></span>](microsoft-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-187">Microsoft デシジョン ツリー アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-187">Microsoft Decision Trees Algorithm Technical Reference</span></span>](microsoft-decision-trees-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-188">Microsoft 線形回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-188">Microsoft Linear Regression Algorithm Technical Reference</span></span>](microsoft-linear-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-189">Microsoft ロジスティック回帰アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-189">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](microsoft-logistic-regression-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-190">Microsoft Naive Bayes アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-190">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](microsoft-naive-bayes-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-191">Microsoft Neural Network Algorithm Technical Reference</span><span class="sxs-lookup"><span data-stu-id="4cf5f-191">Microsoft Neural Network Algorithm Technical Reference</span></span>](microsoft-neural-network-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-192">Microsoft シーケンス クラスタリング アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-192">Microsoft Sequence Clustering Algorithm Technical Reference</span></span>](microsoft-sequence-clustering-algorithm-technical-reference.md)<br /><br /> [<span data-ttu-id="4cf5f-193">Microsoft タイム シリーズ アルゴリズム テクニカル リファレンス</span><span class="sxs-lookup"><span data-stu-id="4cf5f-193">Microsoft Time Series Algorithm Technical Reference</span></span>](microsoft-time-series-algorithm-technical-reference.md)|  
|<span data-ttu-id="4cf5f-194">**モデル コンテンツ**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-194">**Model content**</span></span>|<span data-ttu-id="4cf5f-195">各種類のデータ マイニング モデル内で情報がどのように構造化されるのか、および各ノードに格納された情報を解釈する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-195">Explains how information is structured within each type of data mining model, and explains how to interpret the information stored in each of the nodes.</span></span>|  
||[<span data-ttu-id="4cf5f-196">アソシエーション モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-196">Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-association-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-197">クラスター モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-197">Mining Model Content for Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-clustering-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-198">デシジョン ツリー モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="4cf5f-198">Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-decision-tree-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-199">線形回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-199">Mining Model Content for Linear Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-linear-regression-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-200">ロジスティック回帰モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-200">Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-logistic-regression-models.md)<br /><br /> [<span data-ttu-id="4cf5f-201">Naive Bayes モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-201">Mining Model Content for Naive Bayes Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-naive-bayes-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-202">ニューラル ネットワーク モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-202">Mining Model Content for Neural Network Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-neural-network-models-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-203">シーケンス クラスター モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="4cf5f-203">Mining Model Content for Sequence Clustering Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-sequence-clustering-models.md)<br /><br /> [<span data-ttu-id="4cf5f-204">タイム シリーズ モデルのマイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;</span><span class="sxs-lookup"><span data-stu-id="4cf5f-204">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-model-content-for-time-series-models-analysis-services-data-mining.md)|  
|<span data-ttu-id="4cf5f-205">**データ マイニング クエリ**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-205">**Data mining queries**</span></span>|<span data-ttu-id="4cf5f-206">各モデルの種類で使用できる複数のクエリを紹介します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-206">Provides multiple queries that you can use with each model type.</span></span> <span data-ttu-id="4cf5f-207">たとえば、モデル内のパターンをさらに理解できるようにするコンテンツ クエリや、それらのパターンに基づいて予測できるよう支援する予測クエリなどがあります。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-207">Examples include content queries that let you learn more about the patterns in the model, and prediction queries to help you build predictions based on those patterns.</span></span>|  
||[<span data-ttu-id="4cf5f-208">結合モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-208">Association Model Query Examples</span></span>](association-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-209">クラスタリング モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-209">Clustering Model Query Examples</span></span>](clustering-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-210">デシジョン ツリー モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-210">Decision Trees Model Query Examples</span></span>](decision-trees-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-211">線形回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-211">Linear Regression Model Query Examples</span></span>](linear-regression-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-212">ロジスティック回帰モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-212">Logistic Regression Model Query Examples</span></span>](logistic-regression-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-213">Naive Bayes モデルのクエリ例</span><span class="sxs-lookup"><span data-stu-id="4cf5f-213">Naive Bayes Model Query Examples</span></span>](naive-bayes-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-214">Neural Network Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="4cf5f-214">Neural Network Model Query Examples</span></span>](neural-network-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-215">Sequence Clustering Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="4cf5f-215">Sequence Clustering Model Query Examples</span></span>](sequence-clustering-model-query-examples.md)<br /><br /> [<span data-ttu-id="4cf5f-216">Time Series Model Query Examples</span><span class="sxs-lookup"><span data-stu-id="4cf5f-216">Time Series Model Query Examples</span></span>](time-series-model-query-examples.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="4cf5f-217">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="4cf5f-217">Related Tasks</span></span>  
  
|<span data-ttu-id="4cf5f-218">**トピック**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-218">**Topic**</span></span>|<span data-ttu-id="4cf5f-219">**説明**</span><span class="sxs-lookup"><span data-stu-id="4cf5f-219">**Description**</span></span>|  
|---------------|---------------------|  
|<span data-ttu-id="4cf5f-220">あるデータ マイニング モデルで使用されるアルゴリズムを判断します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-220">Determine the algorithm used by a data mining model</span></span>|[<span data-ttu-id="4cf5f-221">マイニング モデルの作成に使用されたパラメーターのクエリ</span><span class="sxs-lookup"><span data-stu-id="4cf5f-221">Query the Parameters Used to Create a Mining Model</span></span>](query-the-parameters-used-to-create-a-mining-model.md)|  
|<span data-ttu-id="4cf5f-222">カスタム プラグイン アルゴリズムを作成します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-222">Create a Custom Plug-In Algorithm</span></span>|[<span data-ttu-id="4cf5f-223">プラグイン アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="4cf5f-223">Plugin Algorithms</span></span>](plugin-algorithms.md)|  
|<span data-ttu-id="4cf5f-224">アルゴリズム固有のビューアーを使用して、モデルを調査します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-224">Explore a model using an algorithm-specific viewer</span></span>|[<span data-ttu-id="4cf5f-225">データ マイニング モデル ビューアー</span><span class="sxs-lookup"><span data-stu-id="4cf5f-225">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)|  
|<span data-ttu-id="4cf5f-226">汎用のテーブル フォーマットを使用して、モデルのコンテンツを表示します。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-226">View the content of a model using a generic table format</span></span>|[<span data-ttu-id="4cf5f-227">Microsoft 汎用コンテンツ ツリー ビューアーを使用したモデルの参照</span><span class="sxs-lookup"><span data-stu-id="4cf5f-227">Browse a Model Using the Microsoft Generic Content Tree Viewer</span></span>](browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)|  
|<span data-ttu-id="4cf5f-228">データをセットアップし、アルゴリズムを使用してモデルを作成する方法について学びます。</span><span class="sxs-lookup"><span data-stu-id="4cf5f-228">Learn about how to set up your data and use algorithms to create models</span></span>|[<span data-ttu-id="4cf5f-229">マイニング構造 (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="4cf5f-229">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4cf5f-230">マイニング モデル (Analysis Services - データ マイニング)</span><span class="sxs-lookup"><span data-stu-id="4cf5f-230">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4cf5f-231">参照</span><span class="sxs-lookup"><span data-stu-id="4cf5f-231">See Also</span></span>  
 [<span data-ttu-id="4cf5f-232">データ マイニング ツール</span><span class="sxs-lookup"><span data-stu-id="4cf5f-232">Data Mining Tools</span></span>](data-mining-tools.md)  
  
  