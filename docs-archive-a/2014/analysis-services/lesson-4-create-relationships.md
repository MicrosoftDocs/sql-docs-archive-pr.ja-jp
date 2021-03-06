---
title: 'レッスン 5: リレーションシップの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: abac1a00-f827-4c3e-a473-6db5c8a3a66f
author: minewiskan
ms.author: owend
ms.openlocfilehash: f622f88d4d400fedf24e99059eda94882b1bcc3f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718861"
---
# <a name="lesson-5-create-relationships"></a>レッスン 5: [リレーションシップの作成]
  このレッスンでは、データをインポートした際に自動的に作成されたリレーションシップを確認し、異なるテーブル間に新しいリレーションシップを追加します。 リレーションシップとは、2 つのテーブル間を接続し、それらのテーブル内のデータをどのように関連付けるかを決定するものです。 たとえば、Product テーブルと Product Subcategory テーブルの間には、どの製品も特定のサブカテゴリに属しているという事実に基づいたリレーションシップが存在します。 詳細については、[「リレーションシップ (SSAS テーブル)」](tabular-models/relationships-ssas-tabular.md) を参照してください。  
  
 このレッスンの推定所要時間: **10 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 3: 列名の変更」](rename-columns.md)を完了している必要があります。  
  
## <a name="review-existing-relationships-and-add-new-relationships"></a>既存のリレーションシップの確認と新しいリレーションシップの追加  
 テーブルのインポート ウィザードを使用してデータをインポートした際に、AdventureWorksDW データベースから 7 つのテーブルがインポートされました。 通常、リレーショナル ソースからデータをインポートすると、データと共に既存のリレーションシップがインポートされます。 ただし、モデルのオーサリングを続行する前に、テーブル間のリレーションシップが正しく作成されたかどうかを確認する必要があります。 またこのチュートリアルでは、3 つの新しいリレーションシップの追加も行います。  
  
#### <a name="to-review-existing-relationships"></a>既存のリレーションシップを確認するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、[ **モデル** ] メニューをクリックし、[ **モデル ビュー**] をポイントして、[ **ダイアグラム ビュー**] をクリックします。  
  
     モデル デザイナーがダイアグラム ビューで表示されます。このグラフィカルな形式では、インポートしたすべてのテーブルが、それらを結ぶ線と共に表示されます。 テーブル間の線は、データのインポート時に自動的に作成されたリレーションシップを表します。  
  
     モデル デザイナーの右上隅にあるミニマップ コントロールを使用すると、できるだけ多くのテーブルが表示されるようにビューを調整できます。 テーブルをクリックして別の場所にドラッグすれば、テーブルどうし近づけたり、特定の順序に並べたりすることもできます。 テーブルを移動しても、テーブル間の既存のリレーションシップには影響しません。 特定のテーブル内のすべての列を表示するには、テーブルの端をクリックしてドラッグし、大きさを調整します。  
  
2.  **Customer** テーブルと **Geography** テーブルの間の実線をクリックします。 これら 2 つのテーブル間の実線は、そのリレーションシップがアクティブであることを示します。つまり、そのリレーションシップは DAX 数式の計算時に既定で使用されます。  
  
     **Customer** テーブル内の **Geography Id** 列と **Geography** テーブル内の **Geography Id** 列が、どちらもボックス内に表示されます。 これは、これらの列がリレーションシップに使用されていることを示しています。 リレーションシップのプロパティが [**プロパティ**] ウィンドウにも表示されるようになりました。  
  
    > [!TIP]  
    >  ダイアグラム ビューのモデル デザイナーを使用することに加え、[ **リレーションシップの管理** ] ダイアログ ボックスを使用して、すべてのテーブル間のリレーションシップをテーブル形式で表示することもできます。 [ **テーブル** ] メニューをクリックし、[ **リレーションシップの管理**] をクリックします。 [ **リレーションシップの管理** ] ダイアログ ボックスに、データのインポート時に自動的に作成されたリレーションシップが表示されます。  
  
3.  ダイアグラム ビューのモデル デザイナーか、または [ **リレーションシップの管理** ] ダイアログ ボックスを使用して、各テーブルが AdventureWorksDW データベースからインポートされた際に、次のリレーションシップが作成されたことを確認します。  
  
    |アクティブ|テーブル|関連する参照テーブル|  
    |------------|-----------|--------------------------|  
    |はい|**Customer [Geography Id]**|**Geography [Geography Id]**|  
    |はい|**Product [Product Subcategory Id]**|**Product Subcategory [Product Subcategory Id]**|  
    |はい|**Product Subcategory [Product Category Id]**|**Product Category [Product Category Id]**|  
    |はい|**Internet Sales [Customer Id]**|**Customer [Customer Id]**|  
    |はい|**Internet Sales [Product Id]**|**Product [Product Id]**|  
  
 上記のいずれかのテーブル間リレーションシップが存在しない場合は、モデルに次のテーブルが含まれていることを確認します: Customer、Date、Geography、Product、Product Category、Product Subcategory、および Internet Sales。 同じデータ ソース接続のテーブルが別々の時期にインポートされた場合、これらのテーブル間のリレーションシップは作成されないので手動で作成する必要があります。  
  
 場合によっては、特定のビジネス ロジックをサポートするために、モデル内のテーブル間に追加でリレーションシップを作成する必要があります。 このチュートリアルでは、Internet Sales テーブルと Date テーブルの間に 3 つの追加リレーションシップを作成する必要があります。  
  
#### <a name="to-add-new-relationships-between-tables"></a>テーブル間に新しいリレーションシップを追加するには  
  
1.  モデル デザイナーの **Internet Sales** テーブルで、 **Order Date** 列をクリックし、そのままカーソルを **Date** テーブル内の **Date** 列にドラッグして離します。  
  
     **Internet Sales** テーブルの **Order Date** 列と **Date** テーブルの **Date** 列の間にアクティブなリレーションシップが作成され、それを示す実線が表示されます。  
  
    > [!NOTE]  
    >  リレーションシップを作成する際には、主テーブルと、関連する参照テーブルの順序は自動的に正しい順序に設定されます。  
  
2.  **Internet Sales** テーブルで、 **Due Date** 列をクリックし、そのままカーソルを **Date** テーブル内の **Date** 列にドラッグして離します。  
  
     **Internet Sales** テーブルの **Due Date** 列と **Date** テーブルの **Date** 列の間に非アクティブなリレーションシップが作成され、それを示す点線が表示されます。 テーブル間には複数のリレーションシップを持つことができますが、一度にアクティブにできるリレーションシップは 1 つのみです。  
  
3.  最後に、もう 1 つリレーションシップを作成します。 **Internet Sales** テーブルで、 **Ship Date** 列をクリックし、そのままカーソルを **Date** テーブル内の **Date** 列にドラッグして離します。  
  
     **InternetSales** テーブルの **Ship Date** 列と **Date** テーブルの **Date** 列の間に非アクティブなリレーションシップが作成され、それを示す点線が表示されます。  
  
## <a name="next-step"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン [「レッスン 6: 計算列の作成」](lesson-5-create-calculated-columns.md)に進んでください。  
  
  
