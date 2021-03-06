---
title: Analysis Services インポートウィザードを使用してデータマイニングプロジェクトをインポートする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 62bc9fc5-c6ff-4517-b598-d92df76743a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5b39062cc5bc5401a1746f35e98ea643db2d16c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634728"
---
# <a name="import-a-data-mining-project-using-the-analysis-services-import-wizard"></a>Analysis Services インポート ウィザードを使用したデータ マイニング プロジェクトのインポート
  このトピックでは、別のサーバーにある既存のデータ マイニング プロジェクトからメタデータをインポートすることによって新しいデータ マイニング プロジェクトを作成する方法を説明します。インポートには、 **の "** サーバーからインポート (多次元およびデータ マイニング) プロジェクト [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]" というテンプレートを使用します。  
  
## <a name="import-data-sources-mining-structures-and-mining-models-from-an-existing-data-mining-project"></a>データ ソース、マイニング構造、およびマイニング モデルを既存のデータ マイニング プロジェクトからインポートする  
 テンプレート **(多次元およびデータマイニング) プロジェクト**を使用すると、に [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] よって新しいデータマイニングプロジェクトが作成され、指定されたデータマイニングプロジェクトからメタデータがコピーされます。 新しいプロジェクトには、インポート元の ssASnoversion データベースと同じデータ ソース、データ ソース ビュー、マイニング構造、およびマイニング モデルが含まれています。 したがって、インポート プロセスが完了し、オブジェクトが作成された後、マイニング構造と依存モデルのトレーニングによって、それらのオブジェクトに自分でデータを投入する必要があります。  
  
-   データ自体は、移行元サーバーから新しいデータマイニングプロジェクトにコピーされるのではなく、データソースとデータソースビューの定義だけがインポートされます。 したがって、インポート プロセスが完了し、オブジェクトが作成された後、マイニング構造と依存モデルをトレーニングすることによって、それらのオブジェクトに自分でデータを投入する必要があります。 モデルと構造のトレーニングは、データ マイニング デザイナーの **[すべて処理]** コマンドを使用して実行できます。  
  
-   インポートするプロジェクトが以前のバージョンの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]で作成されたものである場合、データ ソースに使用されているプロバイダーが、プロジェクトのインポート先となるサーバーにはインストールされていない可能性があります。 インポートしたマイニング構造を処理しているときにエラーが発生した場合、各データ ソースを右クリックし、 **[デザイナーを開く]** を選択して、接続文字列を編集し、プロバイダーのプロパティを確認します。  
  
     データ マイニング オブジェクトを処理したりデータ マイニング モデルを照会したりする際のアカウントに、データ ソースに対する必要な権限があるかどうかも、場合によってはこの時点で確認する必要があります。  
  
-   既定では、プロジェクトをインポートすると、ワークスペース データベースが localhost (または ** で **[既定のターゲット サーバー][!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] として構成されている既定のインスタンス) に設定されます。 このプロパティを設定するには、 **[オプション]** メニューから **[ビジネス インテリジェンス デザイナー]** を選択し、 **[Analysis Services]** を選択して **[全般]** を選択します。  
  
     それとは別に、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] テーブル モデル プロジェクト用の既定の配置サーバーを構成する際に設定できる専用のオプションが存在します。 この設定は **"既定の配置サーバー"** と呼ばれ、テーブル モデル プロジェクト用の既定のワークスペース データベースを指定することができます。 データ マイニング プロジェクトのテーブル モデルをサポートするインスタンスは使用できません。  
  
     多次元モードまたはデータ マイニング モードで動作している [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを使用するように既定の配置データベースを変更できない場合でも、 **[プロジェクトのプロパティ]** ダイアログ ボックスを使用していつでも配置データベースを指定できます。  
  
#### <a name="to-create-a-new-data-mining-project-by-importing-an-existing-data-mining-project"></a>既存のデータ マイニング プロジェクトをインポートして新しいデータ マイニング プロジェクトを作成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]の **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックします。  
  
2.  **[新しいプロジェクト]** ダイアログ ボックスの **[インストールされているテンプレート]** で **[ビジネス インテリジェンス]** をクリックし、 **[Analysis Services]** をクリックして、 **[サーバーからインポート (多次元/データ マイニング)]** をクリックします。  
  
3.  **[名前]** でプロジェクトの名前を入力し、場所とソリューション名を指定してから **[OK]** をクリックします。  
  
     **Analysis Services データベースのインポート ウィザード** が起動します。 [ようこそ] ページで [OK] をクリックして先に進みます。  
  
4.  **[ソース データベースの選択]** ページで、インポートするソリューションが存在する **インスタンスを**[サーバー] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に指定します。  
  
     **[データベース]** については、インポートするデータ マイニング オブジェクトが存在する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを選択します。  
  
    > [!WARNING]  
    >  インポートするオブジェクトを指定することはできません。既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを選択すると、多次元オブジェクトとデータ マイニング オブジェクトがすべてインポートされます。  
  
     **[次へ]** をクリックします。  
  
5.  **[ウィザードの完了]** ページに、インポート処理の進行状況が表示されます。 処理をキャンセルしたり、インポート対象のオブジェクトを変更したりすることはできません。 終了したら **[完了]** をクリックします。  
  
     [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を使用して、新しいプロジェクトが自動的に表示されます。  
  
## <a name="see-also"></a>参照  
 [プロジェクトのプロパティ (SSAS テーブル)](../tabular-models/properties-ssas-tabular.md)  
  
  
