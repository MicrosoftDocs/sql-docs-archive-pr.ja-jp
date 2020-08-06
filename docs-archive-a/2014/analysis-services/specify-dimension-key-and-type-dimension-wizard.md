---
title: '[ディメンションのキーと種類の指定] (ディメンションウィザード) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensionwizard.dimensionkeyandtype.f1
ms.assetid: d7d5db55-36c3-45f6-ade3-29aa516589c1
author: minewiskan
ms.author: owend
ms.openlocfilehash: cc08584ed12de8597b8289fd223cc47945d7d087
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643526"
---
# <a name="specify-dimension-key-and-type-dimension-wizard"></a>[ディメンションのキーおよび種類を指定] (ディメンション ウィザード)
  **[ディメンションのキーおよび種類を指定]** ページを使用すると、ディメンションのキー属性を定義でき、ディメンションが SCD (緩やかに変化するディメンション) であるかどうかを示すことができます。  
  
> [!NOTE]  
>  このページは、 **[構築方法の選択]** ページの **[データ ソースを使用せずにディメンションを構築する]** が選択され、 **[ディメンションの種類の選択]** ページの **[標準ディメンション]** が選択されている場合のみ表示されます。  
  
## <a name="options"></a>Options  
 **キー属性**  
 ディメンションのキー属性となる属性を選択します。  
  
> [!NOTE]  
>  ディメンションの属性が定義されていない場合、このオプションに使用できる値は **[キー属性を自動的に作成します]** のみとなります。 この値は、ディメンションの属性が定義されている場合は使用できません。  
  
 **[変化するディメンション]**  
 ディメンションが緩やかに変化するディメンションであることを示します。 このオプションを選択すると、時間経過と共にディメンションの階層内でメンバーが移動するのを追跡するために使用できる追加の列および属性が作成されます。  
  
## <a name="see-also"></a>参照  
 [ディメンションウィザードの F1 ヘルプ](dimension-wizard-f1-help.md)   
 [ディメンション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)   
 [多次元モデル内のディメンション](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
