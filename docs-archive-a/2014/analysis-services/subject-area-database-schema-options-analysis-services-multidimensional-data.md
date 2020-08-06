---
title: サブジェクト領域データベーススキーマのオプション (スキーマ生成ウィザード) (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.schemagenwizard.subjectareaschemaopts.f1
ms.assetid: 4c109bb8-e19d-412b-908f-bfdd7f872439
author: minewiskan
ms.author: owend
ms.openlocfilehash: 98460332478d02de823addcd113fb9c1e87d6958
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639679"
---
# <a name="subject-area-database-schema-options-schema-generation-wizard-analysis-services---multidimensional-data"></a>[サブジェクト領域データベース スキーマのオプション] (スキーマ生成ウィザード) (Analysis Services - 多次元データ)
  **[サブジェクト領域データベース スキーマのオプション]** ページを使用すると、スキーマの生成方法を制御したり、データの保存方法を定義したりできます。  
  
## <a name="options"></a>Options  
 **[所有しているスキーマ]**  
 新しいサブジェクト領域データベース内のスキーマの名前を指定します。  
  
 **[ディメンション テーブルに主キーを作成する]**  
 生成されたスキーマのディメンション テーブルに主キーを作成します。 このオプションを選択しない場合、インデックスは作成されません。  
  
> [!NOTE]  
>  このオプションを選択しない場合は、参照整合性が適用されます。  
  
 **[インデックスを作成する]**  
 生成されたスキーマの外部キー列にインデックスを作成します。  
  
 **[参照整合性を適用する]**  
 生成されたスキーマで参照整合性を適用します。 このオプションを選択しない場合、リレーションシップは作成されますが適用されません。  
  
 **[再生成時にデータを保存する]**  
 ウィザードの完了時にサブジェクト領域データベースのデータを保持します。 このオプションを選択しない場合、サブジェクト領域データベースのすべてのデータは警告なしに消去されます。  
  
 **[Time テーブルの設定]**  
 ウィザードで Time テーブルにデータを設定する方法を指定します。 このオプションで使用できる値を次の表に示します。  
  
> [!NOTE]  
>  このオプションは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] をプロジェクト モードで使用して [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] からスキーマ生成ウィザードが呼び出された場合だけ有効になります。  
  
|値|説明|  
|-----------|-----------------|  
|[設定]|サブジェクト領域の Time テーブルにデータが設定されます。|  
|[設定しない]|サブジェクト領域の Time テーブルにデータは設定されません。|  
|[空の場合のみ設定]|サブジェクト領域の Time テーブルは、空の場合にだけデータが設定されます。|  
  
## <a name="see-also"></a>参照  
 [スキーマ生成ウィザードの F1 ヘルプ &#40;Analysis Services-多次元データ&#41;](schema-generation-wizard-f1-help-analysis-services-multidimensional-data.md)  
  
  
