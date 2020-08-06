---
title: 名前付きセットの作成 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
ms.openlocfilehash: e92984102ceb8ad0ac049c15870e9f1efd6090fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712574"
---
# <a name="create-named-sets"></a>名前付きセットの作成
  名前付きセットはディメンション メンバーのセットまたはセット式で、たとえば多次元式 (MDX) のクエリなどで再利用するために作成されます。 名前付きセットは、キューブ データ、算術演算子、数値、および関数を組み合わせることによって作成できます。 たとえば、Top Ten Factories という名前付きセットを作成して、その中に Factories ディメンションのメンバーのうち Production メジャーの最高値を持つものを上から 10 個含めることができます。 この結果、エンド ユーザーがクエリで Top Ten Factories を使用できるようになります。 たとえば、エンド ユーザーは Top Ten Factories を 1 つの軸に配置し、Production などの Measures ディメンションを別の軸に配置できます。 詳細については、「[多次元モデルの計算](calculations-in-multidimensional-models.md)」および「[MDX での名前付きセットの作成 (MDX)](mdx/mdx-named-sets-building-named-sets.md)」を参照してください。  
  
 名前付きセットを作成するには、キューブ デザイナーの **[計算]** タブで **[新しい名前付きセット]** コマンドを使用します。 このコマンドは、 **[計算]** タブのツール バー上にある **[キューブ]** メニューから起動できます。 このコマンドでは、名前付きセットの次のオプションを指定するためのフォームが表示されます。  
  
 **名前**  
 名前付きセットの名前を選択します。 この名前は、エンド ユーザーがキューブを参照したときに表示されます。  
  
 **[式]**  
 名前付きセットを作成する式を指定します。 この式は、MDX で記述することもできます。 式には、次の要素を含めることができます。  
  
-   ディメンション、レベル、メジャーなど、キューブのコンポーネントを表すデータ式  
  
-   算術演算子  
  
-   数値  
  
-   関数  
  
 キューブ コンポーネントは、 **[計算ツール]** ペインの **[メタデータ]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。 関数は、 **[計算ツール]** ペインの **[関数]** タブから **名前付きセット フォーム エディター** ペインの **[式]** ボックスにコピーまたはドラッグできます。  
  
> [!IMPORTANT]  
>  セット内のメンバーに明示的に名前を付けてセット式を作成する場合は、メンバーの一覧を中かっこ () で囲み {} ます。  
  
## <a name="see-also"></a>参照  
 [多次元モデルの計算](calculations-in-multidimensional-models.md)  
  
  
