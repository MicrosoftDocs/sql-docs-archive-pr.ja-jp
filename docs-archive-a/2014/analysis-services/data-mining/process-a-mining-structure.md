---
title: マイニング構造を処理する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining structures [Analysis Services], processing
ms.assetid: 4162f33e-c23f-4293-8905-271781e45fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d25a927ae61ee5ffadf4ca21073a1c04cdb542
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718957"
---
# <a name="process-a-mining-structure"></a>マイニング構造の処理
  マイニング構造に関連付けられているマイニング モデルを参照したり使用したりする前に、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置してマイニング構造とマイニング モデルを処理する必要があります。 また、マイニング構造またはマイニング モデルに変更を加えると、それらを再配置し、処理するように求められます。 **のデータ マイニング デザイナーの** [マイニング構造] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] タブで構造を処理すると、関連するモデルもすべて処理されます。  
  
 マイニング構造は、次のツールを使用して処理できます。  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   XMLA: Process コマンド  
  
 個々のモデルを処理する方法の詳細については、「 [マイニング モデルの処理](process-a-mining-model.md)」を参照してください。  
  
### <a name="to-process-a-mining-structure-and-all-associated-mining-models-using-sql-server-data-tools"></a>SQL Server データ ツールを使用してマイニング構造および関連するすべてのマイニング モデルを処理するには  
  
1.  **の** [マイニング モデル] **メニュー項目から** [マイニング構造および全モデルの処理] [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]を選択します。  
  
     マイニング構造に変更を加えた場合は、マイニング モデルを処理する前にマイニング構造を再配置するよう求められます。 **[はい]** をクリックします。  
  
2.  [**マイニング構造の処理- \<structure> ** ] ダイアログボックスで [**実行**] をクリックします。  
  
     **[処理の進行状況]** ダイアログ ボックスが開き、モデル処理の詳細が表示されます。  
  
3.  モデルの処理が完了したら、 **[処理の進行状況]** ダイアログ ボックスの **[閉じる]** をクリックします。  
  
4.  [**マイニング構造の処理- \<structure> ** ] ダイアログボックスで [**閉じる**] をクリックします。  
  
## <a name="see-also"></a>参照  
 [マイニング構造のタスクと操作方法](mining-structure-tasks-and-how-tos.md)  
  
  
