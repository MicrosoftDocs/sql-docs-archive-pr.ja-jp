---
title: キューブセル (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- storing data [Analysis Services], cells
- hierarchies [Analysis Services], cells
- OLAP objects [Analysis Services], cells
- data members [Analysis Services]
- cubes [Analysis Services], cells
- empty cells [Analysis Services]
- nonleaf members
- cubes [Analysis Services], examples
- storage [Analysis Services], cells
- nonleaf cells
- calculated cells [Analysis Services]
- dimensions [Analysis Services], cells
- cells [Analysis Services]
- leaf members
- leaf cells
ms.assetid: 9945773c-a43b-40d4-91cf-3d2ebc90bca5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0b55e940f75319a965fb1441520a7e16ce7ab2f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632777"
---
# <a name="cube-cells-analysis-services---multidimensional-data"></a>キューブ セル (Analysis Services - 多次元データ)
  キューブはメジャー グループとディメンションで編成されたセルで構成されています。 セルは、キューブ内の各ディメンションの 1 メンバーのキューブ内の論理的な一意の交差部分を表します。 たとえば、次のダイアグラムで示すキューブには、Source、Route、Time という 3 つのディメンションで編成された 2 つのメジャーを持つメジャー グループが 1 つ含まれています。  
  
 ![1 つのセルを示すキューブ図](../../analysis-services/dev-guide/media/as-cubeintro5.gif "1 つのセルを示すキューブ図")  
  
 このダイアグラムの 1 つの影付きセルは、次のメンバーの交差部分です。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 4th quarter メンバー  
  
-   Packages メジャー  
  
## <a name="leaf-and-nonleaf-cells"></a>リーフ セルと非リーフ セル  
 キューブ内のセルの値は複数の方法で取得できます。 前の例では、セルを識別するために使用されるすべてのメンバーが*リーフメンバー*であるため、セルの値をキューブのファクトテーブルから直接取得できます。 階層的にはリーフ メンバーに子メンバーはなく、通常はディメンション テーブルの 1 つのレコードを参照しています。 この種類のセルは、*リーフセル*と呼ばれます。  
  
 ただし、*非リーフメンバー*を使用してセルを識別することもできます。 非リーフ メンバーとは、1 つ以上の子メンバーを持っているメンバーです。 この場合、セルの値は通常、非リーフ メンバーに関連付けられている子メンバーの集計から取得されます。 たとえば、次のメンバーとディメンションの交差部分では、集計によって値が指定されるセルを参照します。  
  
-   Route ディメンションの air メンバー  
  
-   Source ディメンションの Africa メンバー  
  
-   Time ディメンションの 2nd half メンバー  
  
-   Packages メンバー  
  
 Time ディメンションの 2nd half メンバーは非リーフ メンバーです。 そのため、次のダイアグラムに示すように、2nd half メンバーに関連付けられているすべての値を集計する必要があります。  
  
 ![下半期メンバーの第 3 四半期セルおよび第 4 四半期セル](../../analysis-services/dev-guide/media/as-cubeintro6.gif "下半期メンバーの第 3 四半期セルおよび第 4 四半期セル")  
  
 3rd quarter と 4th quarter の各メンバーの集計が合計であると仮定すると、指定したセルの値は、前のダイアグラムの影付きリーフ セルすべてを合計した 400 です。 セルの値は、他のセルの集計から取得されるので、指定されたセルは*非リーフセル*と見なされます。  
  
 カスタム メンバーだけでなくカスタム ロールアップやメンバー グループも使用しているメンバーのセルの値も、同様に取得されます。 ただし、計算されるメンバーのセルの値は、計算されるメンバーの定義に使用した多次元式 (MDX) 式に完全に基づいて取得されるため、場合によっては、実際のセル データは関係しないこともあります。 詳細については、「[親子ディメンションのカスタムロールアップ演算子](../multidimensional-models/parent-child-dimension-attributes-custom-rollup-operators.md)」、「[カスタムメンバー式の定義](../multidimensional-models/attribute-properties-define-custom-member-formulas.md)」、および「[計算](../multidimensional-models-olap-logical-cube-objects/calculations.md)」を参照してください。  
  
## <a name="empty-cells"></a>空のセル  
 キューブ内のすべてのセルに値が必要なわけではありません。キューブには、データのない交差部分もあります。 このような交差部分は空のセルと呼ばれ、キューブ内にしばしば発生します。これは、キューブ内にメジャーを持つディメンション属性のすべての交差部分に、ファクト テーブル内の対応するレコードが含まれているとは限らないからです。 キューブ内のセルの合計数に対するキューブ内の空のセルの比率は、一般にキューブの*密度*と呼ばれます。  
  
 たとえば、次のダイアグラムに示すキューブは、このトピックの他の例に似ていますが、 この例では、第 3 四半期の Africa または第 4 四半期の Australia への air による出荷が含まれていません。 これらのディメンションとメジャーの交差部分に対応するデータはファクト テーブルにありません。そのため、この交差部分にあるセルは空になります。  
  
 ![空のセルを示すキューブ図](../../analysis-services/dev-guide/media/as-cubeintro7.gif "空のセルを示すキューブ図")  
  
 では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、空のセルは特殊な品質を持つセルです。 空のセルは、相互結合、カウントなどの結果を非対称にできるため、多くの MDX 関数は、計算のために空のセルを無視する機能を提供しています。 詳細については、「 [mdx&#41; 参照 &#40;の多次元式](/sql/mdx/multidimensional-expressions-mdx-reference)」および「 [mdx &#40;Analysis Services&#41;の主要概念](../multidimensional-models/key-concepts-in-mdx-analysis-services.md)」を参照してください。  
  
## <a name="security"></a>セキュリティ  
 セル データへのアクセスは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のロール レベルで管理され、MDX 式を使用して細かく制御できます。 詳細については、「[ディメンションデータへのカスタムアクセス権の付与 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-dimension-data-analysis-services.md)」および「[セルデータへのカスタムアクセス権の付与 &#40;Analysis Services&#41;](../multidimensional-models/grant-custom-access-to-cell-data-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Cube Storage &#40;Analysis Services-多次元データ&#41;](../multidimensional-models-olap-logical-cube-objects/cube-storage-analysis-services-multidimensional-data.md)   
 [集計と集計デザイン](../multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)  
  
  
