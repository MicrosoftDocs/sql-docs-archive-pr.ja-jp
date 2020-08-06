---
title: '[Web サービスタスクエディター] ([出力] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6ad034ae78a096ebe5998ac2c3d2573fe7c3bfd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644526"
---
# <a name="web-service-task-editor-output-page"></a>[Web サービス タスク エディター] ([出力] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。  
  
 このタスクの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」(Web サービス タスク) を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[OutputType]**  
 結果を格納するときに使用するストレージ型を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|説明|  
|-----------|-----------------|  
|**[ファイル接続]**|結果をファイルに格納します。 この値を選択すると、動的オプションの **[ファイル]** が表示されます。|  
|**変数**|結果を変数に格納します。 この値を選択すると、動的オプションの **[変数]** が表示されます。|  
  
## <a name="outputtype-dynamic-options"></a>[OutputType] の動的オプション  
  
### <a name="outputtype--file-connection"></a>[OutputType] = [ファイル接続]  
 **[最近使ったファイル]**  
 一覧でファイル接続マネージャーを選択するか、[\<**New Connection...**>] をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>[OutputType] = [変数]  
 **変数**  
 一覧で変数を選択するか、[\<**New Variable...**>] をクリックして新しい変数を作成します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web サービスタスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[Web サービスタスクエディター] &#40;入力ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
