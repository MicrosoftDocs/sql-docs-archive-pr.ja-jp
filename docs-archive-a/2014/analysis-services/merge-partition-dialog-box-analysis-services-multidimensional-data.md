---
title: '[パーティションのマージ] ダイアログボックス (Analysis Services 多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.mergepartition.f1
ms.assetid: 1c94e250-ee18-4f98-b112-985f6346102a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1978c187bfb5097d286f78650b5bda6645c7a054
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644203"
---
# <a name="merge-partition-dialog-box-analysis-services---multidimensional-data"></a>[パーティションのマージ] ダイアログ ボックス (Analysis Services - 多次元データ)
  **SQL Server Management Studio** の **[パーティションのマージ]** ダイアログ ボックスを使用すると、キューブ内のメジャー グループのパーティションをマージできます。 **[パーティションのマージ]** ダイアログ ボックスを表示するには、 **オブジェクト エクスプローラー** で [パーティション] フォルダーまたはパーティションを右クリックし、ショートカット メニューの **[パーティションのマージ]** をクリックします。  
  
## <a name="options"></a>Options  
 **[サーバー]**  
 対象パーティションを含む Analysis Services インスタンスの名前を選択します。  
  
 **名前**  
 対象パーティションとして使用する既存のパーティションの名前を選択します。  
  
 **フォルダー**  
 [名前] で選択されたパーティションで Analysis Services インスタンスの既定のフォルダーが使用されていない場合は、ターゲット パーティションが含まれるフォルダーの名前を表示します。  
  
 **[基になるパーティション]**  
 対象パーティションにマージ可能な、基になるパーティションが含まれているグリッドを表示します。  
  
> [!NOTE]  
>  マージできるパーティションは、同じメジャー グループに属し同じ集計デザインを共有するパーティションだけです。  
  
 このグリッドには次の列が含まれています。  
  
|列|説明|  
|------------|-----------------|  
|**[マージ]**|選択すると、基になるパーティションを対象パーティションにマージできます。|  
|**[パーティション名]**|基になるパーティションの名前を表示します。|  
|**[最終処理]**|基になるパーティションが最後に処理された日時を表示します。|  
  
## <a name="see-also"></a>参照  
 [パーティション &#40;Analysis Services-多次元データ&#41;](multidimensional-models-olap-logical-cube-objects/partitions-analysis-services-multidimensional-data.md)   
 [Analysis Services でのパーティションのマージ (SSAS - 多次元)](multidimensional-models/merge-partitions-in-analysis-services-ssas-multidimensional.md)  
  
  
