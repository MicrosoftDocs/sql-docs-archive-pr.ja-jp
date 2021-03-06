---
title: アソシエーションモデルのマイニングモデルコンテンツ (Analysis Services データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- itemsets [Analysis Services]
- association algorithms [Analysis Services]
- mining model content, association models
- rules [Data Mining]
- associations [Analysis Services]
ms.assetid: d5849bcb-4b8f-4f71-9761-7dc5bb465224
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8904ce155526aee595db19094fd2bad48770e83e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639797"
---
# <a name="mining-model-content-for-association-models-analysis-services---data-mining"></a>アソシエーション モデルのマイニング モデル コンテンツ (Analysis Services - データ マイニング)
  このトピックでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] アソシエーション ルール アルゴリズムを使用するモデルに固有のマイニング モデル コンテンツについて説明します。 すべてのモデルの種類に適用されるマイニング モデル コンテンツに関連する一般用語と統計用語の説明については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="understanding-the-structure-of-an-association-model"></a>アソシエーション モデルの構造について  
 アソシエーション モデルの構造は単純です。 モデルとそのメタデータを表す 1 つの親ノードが各モデルにあり、各親ノードにはアイテムセットとルールのフラット リストがあります。 アイテムセットとルールはツリーを構成していません。次の図のように、最初がアイテムセット、次がルールという順に並んでいます。  
  
 ![アソシエーション モデルのモデル コンテンツの構造](../media/modelcontentstructure-assoc.gif "アソシエーション モデルのモデル コンテンツの構造")  
  
 各アイテムセットはそれぞれ固有のノードに含まれています (NODE_TYPE = 7)。 " *ノード* " には、アイテムセットの定義、そのアイテムセットを含むケースの数、およびその他の情報が含まれています。  
  
 ルールもそれぞれ固有のノードに含まれています (NODE_TYPE = 8)。 " *ルール* " は、アイテムがどのように関連付けられるかを示す一般的なパターンを記述します。 ルールは IF-THEN ステートメントに似ています。 ルールの左辺は、既存の条件または条件のセットを表します。 ルールの右辺は、左辺の条件に通常関連付けられるデータセット内のアイテムを表します。  
  
 **注** ルールやアイテムセットを抽出するには、クエリを使用して必要な種類のノードのみを取得します。 詳細については、「 [結合モデルのクエリ例](association-model-query-examples.md)」を参照してください。  
  
## <a name="model-content-for-an-association-model"></a>アソシエーション モデルのモデル コンテンツ  
 ここでは、マイニング モデル コンテンツの列のうち、アソシエーション モデルに関連する列についてのみ詳細と例を紹介します。  
  
 スキーマ行セットの汎用の列 (MODEL_CATALOG や MODEL_NAME など) の詳細については、「 [マイニング モデル コンテンツ &#40;Analysis Services - データ マイニング&#41;](mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
 MODEL_CATALOG  
 モデルが格納されているデータベースの名前。  
  
 MODEL_NAME  
 モデルの名前。  
  
 ATTRIBUTE_NAME  
 このノードに対応する属性の名前です。  
  
 NODE_NAME  
 ノード名。 アソシエーション モデルの場合、この列には NODE_UNIQUE_NAME と同じ値が含まれます。  
  
 NODE_UNIQUE_NAME  
 ノードの一意の名前。  
  
 NODE_TYPE  
 アソシエーション モデルでは次のノード型のみが出力されます。  
  
|ノードの種類の ID|Type|  
|------------------|----------|  
|1 (モデル)|ルート ノード (親ノード)。|  
|7 (アイテムセット)|アイテムセット (属性と値のペアのコレクション)。 例 :<br /><br /> `Product 1 = Existing, Product 2 = Existing`<br /><br /> or<br /><br /> `Gender = Male`.|  
|8 (ルール)|アイテムが互いにどのように関連付けられるかを定義するルール。<br /><br /> 例:<br /><br /> `Product 1 = Existing, Product 2 = Existing -> Product 3 = Existing`.|  
  
 NODE_CAPTION  
 ノードに関連付けられたラベルまたはキャプション。  
  
 **アイテムセット ノード** アイテムのコンマ区切りのリスト。  
  
 **ルール ノード** ルールの左辺と右辺が含まれます。  
  
 CHILDREN_CARDINALITY  
 現在のノードの子の数を示します。  
  
 **親ノード** アイテムセットおよびルールの合計数を示します。  
  
> [!NOTE]  
>  アイテムセットとルールの数の内訳は、モデルのルート ノードの NODE_DESCRIPTION で確認できます。  
  
 **アイテムセット ノードまたはルール ノード** 常に 0 です。  
  
 PARENT_UNIQUE_NAME  
 ノードの親の一意な名前です。  
  
 **親ノード**常に NULL です。  
  
 **アイテムセット ノードまたはルール ノード** 常に 0 です。  
  
 NODE_DESCRIPTION  
 ノードのコンテンツについてのわかりやすい説明。  
  
 **親ノード** モデルに関する次の情報のコンマ区切りのリストが含まれます。  
  
|Item|説明|  
|----------|-----------------|  
|ITEMSET_COUNT|モデル内のすべてのアイテムセットの数。|  
|RULE_COUNT|モデル内のすべてのルールの数。|  
|MIN_SUPPORT|任意の 1 つのアイテムセットに対して検出された最小のサポート。<br /><br /> **注** この値は、 *MINIMUM _SUPPORT* パラメーターに設定した値とは異なる場合があります。|  
|MAX_SUPPORT|任意の 1 つのアイテムセットに対して検出された最大のサポート。<br /><br /> **注** この値は、 *MAXIMUM_SUPPORT* パラメーターに設定した値とは異なる場合があります。|  
|MIN_ITEMSET_SIZE|アイテムの数として表される最小のアイテムセットのサイズ。<br /><br /> 値 0 は、`Missing` 状態が独立したアイテムとして扱われたことを示します。<br /><br /> **注***MINIMUM_ITEMSET_SIZE* パラメーターの既定値は 1 です。|  
|MAX_ITEMSET_SIZE|検出された最大のアイテムセットのサイズを示します。<br /><br /> **注** この値は、モデルの作成時に *MAX_ITEMSET_SIZE* パラメーターに設定した値によって制限されます。 その値を超えることはありませんが、その値より小さくなることはあります。 既定値は、3 です。|  
|MIN_PROBABILITY|モデル内の任意の 1 つのアイテムセットまたはルールに対して検出された最小の確率。<br /><br /> 例: 0.400390625<br /><br /> **注** アイテムセットの場合、この値は常に、モデルの作成時に *MINIMUM_PROBABILITY* パラメーターに設定した値より大きくなります。|  
|MAX_PROBABILITY|モデル内の任意の 1 つのアイテムセットまたはルールに対して検出された最大の確率。<br /><br /> 例: 1<br /><br /> **注** アイテムセットの最大確率を制限するパラメーターはありません。 頻度が高すぎるアイテムを除外するには、代わりに *MAXIMUM_SUPPORT* パラメーターを使用します。|  
|MIN_LIFT|モデルによって任意のアイテムセットに対して提供されているリフトの最小量。<br /><br /> 例 : 0.14309369632511<br /><br /> 注: 最小リフトがわかると、特定のアイテムセットのリフトが大きいかどうかを判断できます。|  
|MAX_LIFT|モデルによって任意のアイテムセットに対して提供されているリフトの最大量。<br /><br /> 例 : 1.95758227647523 **注** 最大リフトがわかると、特定のアイテムセットのリフトが大きいかどうかを判断できます。|  
  
 **アイテムセット ノード** アイテムセット ノードには、コンマ区切りのテキスト文字列として表示されるアイテムのリストが含まれています。  
  
 例:  
  
 `Touring Tire = Existing, Water Bottle = Existing`  
  
 これは、Touring Tire と Water Bottle が一緒に購入されたことを表しています。  
  
 **ルール ノード** ルール ノードには、矢印で区切られたルールの左辺と右辺が含まれています。  
  
 例: `Touring Tire = Existing, Water Bottle = Existing -> Cycling cap = Existing`  
  
 これは、Touring Tire と Water Bottle を購入した顧客は Cycling Cap も購入する傾向があることを表しています。  
  
 NODE_RULE  
 ノードに埋め込まれたルールまたはアイテムセットを記述する XML フラグメント。  
  
 **親ノード** 空白。  
  
 **アイテムセット ノード** 空白。  
  
 **ルール ノード** ルールに関する有用な追加情報 (サポート、信頼度、アイテムの数など) と、ルールの左辺を表すノードの ID が含まれます。  
  
 MARGINAL_RULE  
 空白。  
  
 NODE_PROBABILITY  
 アイテムセットまたはルールに関連付けられている確率または信頼スコア。  
  
 **親ノード** 常に 0 です。  
  
 **アイテムセット ノード** アイテムセットの確率です。  
  
 **ルール ノード** ルールの信頼度の値です。  
  
 MARGINAL_PROBABILITY  
 NODE_PROBABILITY と同じです。  
  
 NODE_DISTRIBUTION  
 このテーブルに含まれる情報は、ノードがアイテムセットかルールかによって大きく異なります。  
  
 **親ノード** 空白。  
  
 **アイテムセット ノード** アイテムセット内の各アイテムと、その確率およびサポートの値の一覧が含まれます。 たとえば、アイテムセットに 2 つの製品が含まれている場合は、各製品の名前と、その製品を含むケースの数の一覧が含まれます。  
  
 **ルール ノード** 2 つの行が含まれます。 1 つ目の行には、ルールの右辺の属性 (予測されたアイテム) が信頼スコアと共に表示されます。  
  
 2 つ目の行はアソシエーション モデルに固有の行で、ルールの右辺のアイテムセットへのポインターが含まれています。 このポインターは、ATTRIBUTE_VALUE 列で、右辺のアイテムのみを含むアイテムセットの ID として表されます。  
  
 たとえば、 `If {A,B} Then {C}`というルールの場合は、アイテム `{C}`の名前と、アイテム C のアイテムセットを含むノードの ID がテーブルに含まれます。  
  
 アイテムセット ノードからは、右辺の製品を含むケースの合計数を特定できるため、このポインターは便利です。 ルール `If {A,B} Then {C}` が当てはまるケースは、 `{C}`のアイテムセットに含まれるケースのサブセットです。  
  
 NODE_SUPPORT  
 このノードをサポートするケースの数。  
  
 **親ノード** モデル内のケースの数。  
  
 **アイテムセット ノード** アイテムセット内のすべてのアイテムを含むケースの数。  
  
 **ルール ノード** ルールに含まれるすべてのアイテムを含むケースの数。  
  
 MSOLAP_MODEL_COLUMN  
 ノードがアイテムセットかルールかによって異なる情報が含まれます。  
  
 **親ノード** 空白。  
  
 **アイテムセット ノード** 空白。  
  
 **ルール ノード** ルールの左辺のアイテムを含むアイテムセットの ID。 たとえば、 `If {A,B} Then {C}`というルールの場合は、 `{A,B}`のみを含むアイテムセットの ID が含まれます。  
  
 MSOLAP_NODE_SCORE  
 **親ノード** 空白。  
  
 **アイテムセット ノード** アイテムセットの重要度スコア。  
  
 **ルール ノード** ルールの重要度スコア。  
  
> [!NOTE]  
>  重要度の計算方法はアイテムセットとルールで異なります。 詳細については、「 [Microsoft アソシエーション アルゴリズム テクニカル リファレンス](microsoft-association-algorithm-technical-reference.md)」を参照してください。  
  
 MSOLAP_NODE_SHORT_CAPTION  
 空白。  
  
## <a name="see-also"></a>参照  
 [マイニングモデルコンテンツ &#40;Analysis Services-データマイニング&#41;](mining-model-content-analysis-services-data-mining.md)   
 [Microsoft アソシエーションアルゴリズム](microsoft-association-algorithm.md)   
 [結合モデルのクエリ例](association-model-query-examples.md)  
  
  
