---
title: '[クラスターの識別] タブ (マイニングモデルビューアー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.clustering.discrimination.f1
ms.assetid: ae7cfff7-ab1c-4cf5-9a91-97b21d15d85f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 35435736bcdf1b1962de6babace2def953bbfff0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634147"
---
# <a name="cluster-discrimination-tab-mining-model-viewer"></a>[クラスターの識別] タブ (マイニング モデル ビューアー)
  **[クラスターの識別]** タブを使用すると、クラスター モデルに存在する 2 つのクラスターを比較できます。 異なる属性と値の組み合わせが、クラスター内でどのように表されているかを確認できます。  
  
 **詳細:** [Microsoft クラスター アルゴリズム](data-mining/microsoft-clustering-algorithm.md)、 [Microsoft クラスター ビューアーを使用したモデルの参照](data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
## <a name="options"></a>Options  
 **[ビューアーのコンテンツを最新状態に更新]**  
 ビューアーにマイニング モデルを再読み込みします。  
  
 **[マイニング モデル]**  
 現在のマイニング構造に含まれているマイニング モデルから選択します。 関連付けられているビューアーが開き、マイニング モデルが表示されます。  
  
 **Viewer**  
 選択したマイニング モデルを調べるために使用するビューアーを選択します。 クラスター モデル用のカスタム ビューアー、または [!INCLUDE[msCoName](../includes/msconame-md.md)] マイニング コンテンツ ビューアーを使用できます。 利用可能な場合プラグイン ビューアーを使用することもできます。  
  
 **クラスター 1**  
 クラスターを選択して、別のクラスターと比較できるようにします。  
  
 **Cluster 2**  
 **[クラスター 1]** と比較するために、マイニング モデルのクラスター リストから別のクラスターを選択します。 クラスターは、その補集合 (選択したクラスター内のケースを除くモデル内のすべてのケース) と比較することもできます。  
  
 **との識別スコア \<cluster 1>\<cluster 2>**  
 グラフの列は、選択した 2 つのクラスターに対して属性と値の各ペアがどのように関係しているかに関する情報を示します。  
  
|||  
|-|-|  
|**変数**|マイニング モデルの属性です。|  
|**値**|**[変数]** で選択された属性の値。|  
|**ライター\<cluster 1>**|左側の棒グラフは、選択した属性と値のペアが、**[クラスター 1]** で選択したクラスターの代表である確率を表します。 バーの上にマウス ポインターを置くことで、パーセントで表現された値を確認できます。 値がゼロの場合でも、属性値がクラスターに存在しないことを意味するわけではありません。つまり、分散によって1つのクラスターが互いに優先されるというわけではありません。|  
|**ライター\<cluster 2>**|右側の棒グラフは、選択した属性と値のペアが、**[クラスター 2]** で選択したクラスターの代表である確率を表します。|  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データ マイニング モデル ビューアー](data-mining/data-mining-model-viewers.md)  
  
  
