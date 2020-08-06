---
title: Microsoft 汎用コンテンツツリービューアー (データマイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.contentviewer.f1
ms.assetid: 751b4393-f6fd-48c1-bcef-bdca589ce34c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0dab06d6af8f2c5af029d9ce831f518faa4067e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740572"
---
# <a name="microsoft-generic-content-tree-viewer-data-mining"></a>Microsoft 汎用コンテンツ ツリー ビューアー (データ マイニング)
  **Microsoft 汎用コンテンツ ツリー ビューアー** には、データ マイニング モデルのコンテンツに関する詳細情報が、標準化された HTML テーブル形式で表示されます。 このビューを使用すると、モデルの基になる構造に加え、係数や値の分布などの詳細を確認できます。  
  
 テーブルに実際に表示される内容は使用されたアルゴリズムによって異なり、列、ルール、プロパティ、属性、ノード、および数式が含まれる場合があります。 モデル コンテンツ、および各モデルの種類の情報を解釈する方法の詳細については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
 ビューアーに表示される情報は、マイニング モデルのコンテンツ スキーマ行セットに基づく共通の構造を使用します。 コンテンツ スキーマ行セットは、データ マイニング モデルのパターン、統計、およびその他のコンテンツを格納するための汎用フレームワークです。 マイニング モデルのデータ マイニング スキーマ行セット内の列の一覧については、「 [DMSCHEMA_MINING_MODEL_CONTENT 行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)」を参照してください。  
  
## <a name="options"></a>Options  
 **[ノードのキャプション (一意の ID)]**  
 このペインには、選択したマイニング モデルのすべてのノードが一覧表示されます。 ツリーでのノードの配置方法は、表示中のモデルの種類によって異なります。  
  
 ノードをクリックすることで、そのノードに関する詳細を **[ノードの詳細]** ペインに表示できます。  
  
 **ノードの詳細**  
 選択したノードのコンテンツに関する詳細情報が表示されます。 各ノードの情報は標準化された形式で格納されますが、テーブルの各行の内容と意味は、表示中のモデルの種類またはノードの型によって異なります。 たとえば、関連モデルのルールを表すノードに保存される情報は、デシジョン ツリー モデルのツリーを表すノードとは別の情報を格納します。  
  
 特定のモデルの種類のノード情報を解釈する方法については、「[マイニング モデル コンテンツ (Analysis Services - データ マイニング)](data-mining/mining-model-content-analysis-services-data-mining.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [データマイニングアルゴリズム &#40;Analysis Services-データマイニング&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [データマイニングモデルデザイナー &#40;のマイニングモデルビューアー&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [データマイニングクエリ](data-mining/data-mining-queries.md)  
  
  
