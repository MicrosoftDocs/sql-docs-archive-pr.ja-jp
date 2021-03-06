---
title: '[ディメンション処理変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dimprocessingtransformation.connection.f1
helpviewer_keywords:
- Dimension Processing Destination Editor
ms.assetid: 44aab631-d62d-4895-8fc7-7f1f3b1b68ce
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 50ba42292c1f48c9b1cdf2ba00c709dacd2f9675
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645193"
---
# <a name="dimension-processing-destination-editor-connection-manager-page"></a>[ディメンション処理変換先エディター] ([接続マネージャー] ページ)
  **[ディメンション処理変換先エディター]** ダイアログ ボックスの **[接続マネージャー]** ページを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスへの接続を指定できます。  
  
 ディメンション処理変換先の詳細については、「 [Dimension Processing Destination](data-flow/dimension-processing-destination.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **Connection manager**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]** をクリックして新しい接続を作成します。  
  
 **[新規作成]**  
 **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して、新しい接続を作成します。  
  
 **利用可能なディメンションの一覧**  
 処理するディメンションを選択します。  
  
 **[処理方法]**  
 一覧で選択したディメンションに適用する処理方法を選択します。 このオプションの既定値は **[完全]** です。  
  
|値|説明|  
|-----------|-----------------|  
|**[追加 (増分)]**|ディメンションの増分処理を実行します。|  
|**完全**|ディメンションの完全処理を実行します。|  
|**アップデート**|ディメンションの更新処理を実行します。|  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [ディメンション処理変換先エディター &#40;マッピングページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-mappings-page.md)   
 [ディメンション処理変換先エディター &#40;[詳細設定] ページ&#41;](../../2014/integration-services/dimension-processing-destination-editor-advanced-page.md)  
  
  
