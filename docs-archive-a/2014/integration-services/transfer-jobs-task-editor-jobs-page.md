---
title: '[ジョブ転送タスクエディター] ([ジョブ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferjobstask.jobs.f1
helpviewer_keywords:
- Transfer Jobs Task Editor
ms.assetid: e72b1dc7-8cda-4ee6-abb5-d438370f04df
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d2d506da6997965e40d66521f7dccb8218e165fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646215"
---
# <a name="transfer-jobs-task-editor-jobs-page"></a>[ジョブ転送タスク エディター] ([ジョブ] ページ)
  **[ジョブ転送タスク エディター]** ダイアログ ボックスの **[ジョブ]** ページを使用すると、1 つ以上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブを [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の 1 つのインスタンスから別のインスタンスにコピーするためのプロパティを指定できます。 ジョブ転送タスクの詳細については、「 [Transfer Jobs Task](control-flow/transfer-jobs-task.md)」を参照してください。  
  
> [!NOTE]  
>  コピー元サーバーのジョブにアクセスするには、少なくともサーバーの **SQLAgentUserRole** 固定データベース ロールのメンバーであることが必要です。 コピー先サーバーでジョブを正常に作成するには、 **sysadmin** 固定サーバー ロールのメンバーであるか、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールの 1 つであることが必要です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント固定データベース ロールおよびその権限の詳細については、「 [SQL Server エージェントの固定データベース ロール](../ssms/agent/sql-server-agent-fixed-database-roles.md)」をご覧ください。  
  
## <a name="options"></a>オプション  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送元サーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、 **[\<New connection...>]** をクリックして転送先サーバーへの新しい接続を作成します。  
  
 **[TransferAllJobs]**  
 コピー元サーバーからコピー先サーバーにすべてコピーするか、指定の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エージェント ジョブのみをコピーするかを選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**True** にします|すべてのジョブをコピーします。|  
|**False**|指定のジョブのみをコピーします。|  
  
 **[JobsList]**  
 **[...]** ボタンをクリックして、コピーするジョブを選択します。 少なくとも 1 つのジョブを選択する必要があります。  
  
> [!NOTE]  
>  コピーするジョブを選択する前に **[SourceConnection]** を指定します。  
  
 **[JobsList]** オプションは、 **[TransferAllJobs]** が **[True]** に設定されている場合は使用できません。  
  
 **[IfObjectExists]**  
 コピー先サーバーに既に存在する名前と同じ名前のジョブをどのように処理するかを選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**[FailTask]**|ジョブの名前がコピー先サーバーに既に存在する名前と同じである場合、タスクは失敗します。|  
|**Overwrite**|コピー先サーバーの同じ名前のジョブを上書きします。|  
|**Skip**|コピー先サーバーの同じ名前のジョブをスキップします。|  
  
 **[EnableJobsAtDestination]**  
 コピー先サーバーにコピーされたジョブを有効にするかどうかを選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**True** にします|コピー先サーバーのジョブを有効にします。|  
|**False**|コピー先サーバーのジョブを無効にします。|  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [[ジョブ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)  
  
  
