---
title: レポートデザインの CSDLBI 属性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 61ba3a27-790e-43bc-b421-e01bf2fdbda6
author: minewiskan
ms.author: owend
ms.openlocfilehash: ee53cb3e4910e988403350bac5c993ef68b5170d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634698"
---
# <a name="csdlbi-attributes-for-report-design"></a>レポート デザインの CSDLBI 属性
  このセクションでは、テーブル モデリングについての CSDL に対する拡張機能の、[!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] クエリ デザインに影響のある属性について説明します。  
  
## <a name="model-attributes"></a>モデル属性  
 これらの属性は、CSDL [EntityContainer](https://msdn.microsoft.com/library/bb399169.aspx)要素のサブ要素で定義されます。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|カルチャ|Text|通貨形式に使用されるカルチャを示します。 省略した場合は、EN-US が使用されます。|  
|IsRightToLeft|Boolean|テキスト フィールドの値を既定で右から左に読む必要があるかどうかを示します。|  
  
## <a name="entity-attributes"></a>エンティティ属性  
 以下の属性は、CSDL の EntitySet または EntityType 要素のサブ要素で定義されています。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Text|DAX クエリでこのエンティティを参照するために使用される識別子。 省略した場合は、名前が使用されます。|  
|`Caption`|Text|エンティティの表示名。|  
|`Documentation`|Text|ビジネス ユーザーがデータの意味を理解できるように説明するテキスト。|  
|`Hidden`|Boolean|エンティティを表示するかどうかを示します。 既定では、 `false`です。|  
|`CollectionCaption`|Text|エンティティのインスタンスのセットを参照するための複数形の名前。 省略した場合は、Caption 属性が使用されます。|  
|`DisplayKey`|MemberRef[]|ビジネス ユーザーに対してエンティティのインスタンスを示すために使用されるフィールドの順序付きリスト。 参照には、インスタンス プロパティとナビゲーション プロパティを含めることができます。 ナビゲーションプロパティが参照されている場合は、ターゲット エンティティの `DisplayKey` が表示されます 。 `DisplayKey` の値を指定しないと、キー フィールドが使用されます。|  
|`DefaultImage`|MemberRef|ビジネス ユーザーに対してエンティティのインスタンスを視覚的に示すために使用される画像を含むフィールドの参照。 省略した場合は、エンティティの最初の画像フィールドが使用されます (存在する場合)。|  
|`DefaultDetails`|MemberRef[]|ビジネス ユーザーに対して表示されるエンティティ インスタンスについての詳細情報の既定セットを表すフィールドの順序付きリスト。省略すると、エンティティの最初の 5 つのフィールドが使用されます。ただし、`Key`、`DisplayKey`、または `DefaultImage` によって既に参照されているフィールドは除外されます。|  
|`SortProperties`|MemberRef[]|エンティティ インスタンスの標準的な並べ替えに使用されるフィールドの順序付きリスト。 これらのフィールドで並べ替えられるときは、各フィールドで指定されている `SortDirection` が使用されます。 省略した場合は、`DisplayKey` フィールドが使用されます。|  
|`DefaultMeasure`|MemberRef|メジャーまたはフィールドをエンティティの複数のインスタンスに対する既定の表現として使用する必要があることを示すための、モデルで定義されているメジャー、または既定の集計関数のある数値フィールドの参照。 省略した場合は、エンティティ インスタンスの数が使用されます。|  
|`DefaultLocation`|MemberRef|値がエンティティ インスタンスと関連付けられた既定の場所を表しているフィールドの参照。 省略した場合は、エンティティの最初の場所フィールドが使用されます (存在する場合)。|  
  
## <a name="field-attributes"></a>フィールド属性  
 これらの属性は、CSDL プロパティまたは[NavigationProperty](https://msdn.microsoft.com/library/bb387104.aspx)要素のサブ要素で定義されます。  
  
|属性名|データ型|説明|  
|--------------------|---------------|-----------------|  
|`ReferenceName`|Text|DAX クエリでこのエンティティを参照するために使用される識別子。 省略した場合は、フィールド名が使用されます。|  
|`Caption`|Text|エンティティの表示名。 省略した場合は、フィールドの `ReferenceName` が使用されます。|  
|`Documentation`|Text|ビジネス ユーザーがフィールドの意味を理解できるように説明するテキスト。|  
|`Hidden`|Boolean|フィールドを表示するかどうかを示します。 既定値は `false` で、フィールドが表示されることを意味します。|  
|`DisplayFolder`|Text|このフィールドが表示されるフォルダーの名前 (完全なパス)。 省略した場合、フィールドはモデルのルートに表示されます。|  
|`ContextualNameRule`|列挙型|プロパティ名をそれが使用されるコンテキストに基づいて変更する必要があるかどうか、および変更する方法を示す値。 使用できる値は `None` 、、 `Role` 、 `Merge` です。|  
|`Alignment`|列挙型|表形式の表示でフィールドの値を配置する方法を示す値。 指定できる値は、`Default`、`Center`、`Left`、`Right` です。 省略した場合、既定では、フィールドのデータ型に基づいて配置が決定されます。|  
|`FormatString`|Text|フィールドの値が既定でどのように書式設定されるかを示す .NET 形式の文字列。 省略した場合は、次の形式と見なされます。<br /><br /> -Datetime フィールド: 地域の短い日付または "d"<br />-既定の集計関数を使用した浮動小数点フィールドと整数フィールド: 地域番号または "n"<br />-既定の集計関数のない整数: 地域の10進数または "d"<br /><br /> 他のすべての型のフィールドについては、書式指定文字列は適用されません。|  
|`Units`|Text|単位を表現するためにフィールド値に適用される記号。 省略した場合、単位は不明と見なされます。|  
|`Width`|Integer|表形式の表示でフィールドの値を表示するために予約する必要がある文字の幅 (推奨)。 省略した場合、既定の幅はフィールドのデータ型に基づきます。|  
|`SortDirection`|列挙型|フィールド値の一般的な並べ替え方法を示す値。 指定できる値は、`Default`、`Ascending`、`Descending` です。 省略した場合、既定値では、フィールドのデータ型に基づいて並べ替えの方向が割り当てられます。|  
|`IsRightToLeft`|Boolean|右から左に読む必要のあるテキストがフィールドに含まれるかどうかを示します。 省略した場合は、モデルの設定と見なされます。|  
|`OrderBy`|MemberRef|このフィールドの値の並べ替え順序を定義する、モデル内の別のフィールドへの参照。 2 つのフィールドの値は 1:1 で対応している必要があります。そうでない場合、並べ替えの動作は定義されません。 省略した場合、フィールドはそれ自体の値に基づいて並べ替えられます。|  
|`Contents`|列挙型|フィールドのサブタイプまたは内容を記述する列挙。 省略した場合、フィールドのデータ型が Binary でない限り、特定のサブタイプは想定されません。この場合、イメージはと見なされます。 サポートされるコンテンツ タイプの詳細については、AMO のドキュメントを参照してください。|  
|`DefaultAggregateFunction`|列挙型|このフィールドの集計に通常使用される既定の関数を示す値 (ある場合)。 使用できる値は、`None`、`Sum`、`Average`、`Count`、`Min`、`Max` です。 省略した場合、数値フィールドについては `Sum` と想定され、他のすべてのフィールドについては `None` と想定されます。|  
|`IsSimpleMeasure`|Boolean|メジャーが単に数値フィールドの単純な集計かどうかを示します。 このような集計はクエリで必要に応じて簡単に定義できるので、パフォーマンス向上のためモデル定義では省略する必要があります。 省略した場合は、`false` と想定されます。|  
|`Kpi`<br /><br /> `KpiGoal`<br /><br /> `KpiStatus`|サブ要素|メジャー要素が KPI として使用されることを示します。 KPI サブ要素では、KpiGoal および KpiStauts 要素を使用して、関連する表示画像とターゲット範囲が定義されます。|  
  
  