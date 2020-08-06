---
title: '[プロセス実行タスクエディター] ([処理] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ce8629be2c07ae4caac4586b266936a908e71499
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710982"
---
# <a name="execute-process-task-editor-process-page"></a>Execute Process Task Editor (Process Page)
  **[プロセス実行タスク エディター]** ダイアログ ボックスの **[処理]** ページを使用すると、プロセスを実行する際のオプションを構成できます。 オプションには、実行する実行可能ファイル、そのファイルの場所、コマンド プロンプト引数、入力するための変数、出力をキャプチャする変数などが含まれます。  
  
 このタスクの詳細については、「 [Execute Process Task](control-flow/execute-process-task.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **[RequireFullFileName]**  
 指定した場所に実行可能ファイルが見つからなかった場合に、タスクを中止するかどうかを指定します。  
  
 **[実行可能ファイル]**  
 実行する実行可能ファイルの名前を入力します。  
  
 **引数**  
 コマンド プロンプト引数を指定します。  
  
 **[WorkingDirectory]**  
 実行可能ファイルが置かれているフォルダーのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてフォルダーを指定します。  
  
 **[StandardInputVariable]**  
 プロセスが入力する変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。  
  
 **関連項目:**  [変数の追加](../../2014/integration-services/add-variable.md)  
  
 **[StandardOutputVariable]**  
 プロセスの出力をキャプチャする変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。  
  
 **[StandardErrorVariable]**  
 プロセッサのエラー出力をキャプチャする変数を選択するか、[\<**New variable...**>] をクリックして新しい変数を作成します。  
  
 **[FailTaskIfReturnCodeIsNotSuccessValue]**  
 プロセス終了コードが **[SuccessValue]** で指定されている値と異なった場合、タスクを終了するかどうかを指定します。  
  
 **[SuccessValue]**  
 実行可能ファイルが正常に終了した場合に返される値を指定します。 既定では、この値は **0**に設定されます。  
  
 **[TimeOut]**  
 プロセスを実行できる秒数を指定します。 値を **0** に指定すると、タイムアウト値が使用されず、プロセスは完了するかエラーが発生するまで実行されます。  
  
 **[TerminateProcessAfterTimeOut]**  
 **[TimeOut]** オプションで指定されたタイムアウト時間の後に、プロセスを強制終了するかどうかを指定します。 このオプションは、 **[TimeOut]** が **0**以外の場合にのみ使用できます。  
  
 **[WindowStyle]**  
 プロセスを実行する際のウィンドウのスタイルを指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
