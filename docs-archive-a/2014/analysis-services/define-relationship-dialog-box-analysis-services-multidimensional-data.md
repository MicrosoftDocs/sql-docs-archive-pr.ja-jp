---
title: '[リレーションシップの定義] ダイアログボックス (Analysis Services-多次元データ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.dimensionusage.definerelationship.f1
helpviewer_keywords:
- Define Relationship dialog box
ms.assetid: 0fcee7f1-f138-4c2e-ae8c-245395ee0fe8
author: minewiskan
ms.author: owend
ms.openlocfilehash: e07095e99593c5cd1e7a3a3a904a473a8dfc3cc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715881"
---
# <a name="define-relationship-dialog-box-analysis-services---multidimensional-data"></a>[リレーションシップの定義] ダイアログ ボックス (Analysis Services - 多次元データ)
  キューブ デザイナーの **[リレーションシップの定義]** ダイアログ ボックスを使用すると、キューブ ディメンションとメジャー グループのリレーションシップを定義できます。 **[リレーションシップの定義]** ダイアログ ボックスを表示するには、キューブ デザイナーの **[ディメンションの使用法]** タブの **[グリッド]** ペイン内のセルで、 **[...]** をクリックします。  
  
## <a name="options"></a>Options  
 **[リレーションシップの種類の選択]**  
 ディメンション リレーションシップの種類を選択して、キューブ ディメンションとメジャー グループの間にリレーションシップを作成します。 ディメンション リレーションシップの種類を選択すると、 **[詳細]** ペインの内容が変わります。  
  
 **[リレーションシップがありません]** を選択した場合、ディメンション リレーションシップは作成されません。  
  
 **詳細**  
 **[リレーションシップの種類の選択]** で選択したディメンション リレーションシップの種類で使用できるオプションが表示されます。  
  
## <a name="detail-pane-options"></a>[詳細] ペインのオプション  
 **[リレーションシップの種類の選択]** で選択したリレーションシップの種類に応じて、 **[詳細]** ペインには次のオプションが表示されます。  
  
|リレーションシップの種類|説明|オプション|  
|-----------------------|-----------------|------------|  
|**[リレーションシップがありません]**|リレーションシップが定義されていません。 **[詳細]** ペインにはオプションが表示されません。||  
|**Regular**|標準のディメンション リレーションシップを指定します。 **[詳細]** ペインには次のオプションが表示されます。|**[粒度属性]**: <br />                      そのディメンションを基準として、メジャー グループの粒度を定義する属性を選択します。 通常、この属性はディメンションの重要な属性です。|  
|||**[ディメンション テーブル]**: ディメンションのメイン テーブルが表示されます。|  
|||**[メジャー グループ テーブル]**: メジャー グループのファクト テーブルが表示されます。|  
|||**[リレーションシップ]**: リレーションシップの基となる、ディメンション列とメジャー グループ列のグリッドが表示されます。 このグリッドには次の列が含まれています。<br /><br /> **[ディメンション列]**: 選択した粒度属性に関連付けられている列が表示されます。 メモ: ディメンションがまだ生成されていない場合、このオプションは **[生成]** に設定されます。<br />**[メジャー グループ列]** :<br />                              ディメンション列に関連付けられているメジャー グループの列を選択します。|  
|||**詳細**:<br />                      クリックすると、**[メジャー グループのバインド]** ダイアログ ボックスが開きます。ここで、属性とメジャー グループ列のリレーションシップに関する詳細なプロパティ (null 処理など) を編集できます。 [**メジャーグループのバインド**] ダイアログボックスの詳細については、「[[メジャーグループのバインド] ダイアログボックス &#40;Analysis Services 多次元データ&#41;](measure-group-bindings-dialog-box-analysis-services-multidimensional-data.md)」を参照してください。|  
|**ファクト**|ファクト ディメンション リレーションシップを指定します。 **[詳細]** ペインには次のオプションが表示されます。|**[粒度属性]** : そのディメンションを基準として、メジャー グループの粒度を定義する属性を選択します。 通常、この属性はディメンションの重要な属性です。|  
|||**[ディメンション テーブル]**: プライマリ ディメンション テーブルが表示されます。|  
|||**メジャーグループテーブル**: <br />                      メジャー グループの基となるテーブルが表示されます。|  
|**[参照対象]**|参照対象のディメンション リレーションシップを指定します。 **[詳細]** ペインには次のオプションが表示されます。|**参照ディメンション**: <br />                      選択したディメンションが表示されます。|  
|||**[中間ディメンション]**: <br />                      中間ディメンションを選択します。|  
|||**[参照ディメンションの属性]**:  <br />                      **[中間ディメンションの属性]** で指定された中間ディメンションの属性に関連付けられる、参照ディメンションの属性を選択します。|  
|||**[中間ディメンションの属性]**: <br />                      **[参照ディメンション]** で指定された参照ディメンションの属性に関連付けられる、中間ディメンションの属性を選択します。|  
|||**具体化**: <br />                      参照ディメンションの属性を MOLAP 構造のファクト テーブルにリンクする中間ディメンションの属性メンバーを格納する場合に選択します。 このリレーションシップの具体化は、クエリのパフォーマンスを最大限に高める既定の動作ですが、処理時間が増え、格納領域が余分に使用されます。|  
|**多対多**|多対多のディメンション リレーションシップを指定します。 **[詳細]** ペインには次のオプションが表示されます。|**[ディメンション]** : 選択したディメンションが表示されます。|  
|||**[中間メジャー グループ]** : <br />                      関連付けられている中間メジャー グループを選択します。<br /><br /> メモ: 中間メジャー グループでは、選択したメジャー グループと 1 つ以上のディメンションが共通している必要があります。 さらに、中間メジャー グループと共通ディメンションの間のリレーションシップの粒度が、選択したメジャー グループと共通ディメンションの間のリレーションシップの粒度以上である必要があります。|  
|**データ マイニング**|データ マイニング ディメンション リレーションシップを指定します。 **[詳細]** ペインには次のオプションが表示されます。|**[対象になるディメンション]**: 選択したデータ マイニング ディメンションが表示されます。<br /><br /> メモ: データ マイニング ディメンション リレーションシップを作成するには、データ マイニング ディメンションを選択する必要があります。|  
|||**[基になるディメンション]**: データ マイニング ディメンションで予測分析を行う際に使用されるディメンションを選択します。|  
  
## <a name="see-also"></a>参照  
 [ディメンションのリレーションシップ](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)   
 [ディメンションの使用法 &#40;キューブデザイナー&#41; &#40;Analysis Services-多次元データ&#41;](dimension-usage-cube-designer-analysis-services-multidimensional-data.md)   
 [多次元データ &#40;Analysis Services のデザイナーとダイアログボックス&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)  
  
  