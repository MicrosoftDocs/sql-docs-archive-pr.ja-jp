---
title: SQL Server エージェントの JobSteps オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- JobSteps object
- SQLAgent:JobSteps
ms.assetid: 44f9983c-1753-4fe0-8475-973aa2460b3a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3759303807714e2bb7f71f59e644bc485d36cfcb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633798"
---
# <a name="sql-server-agent-jobsteps-object"></a>SQL Server エージェントの JobSteps オブジェクト
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの **JobSteps** パフォーマンス オブジェクトには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブ ステップについての情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
 次の表は、 **SQLAgent:JobSteps** カウンターの一覧です。  
  
|名前|説明|  
|----------|-----------------|  
|**Active steps**|このカウンターは、現在実行中のジョブ ステップの数を報告します。|  
|**Queued steps**|このカウンターは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントで実行する準備が整っているジョブ ステップで、まだ実行が開始されていないジョブ ステップの数を報告します。|  
|**Total Step Retries**|このカウンターは、サーバーを前回再起動してから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がジョブ ステップを再試行した合計回数を報告します。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|インスタンス|説明|  
|--------------|-----------------|  
|**_Total**|すべてのジョブ ステップの情報です。|  
|**ActiveScripting**|**ActiveScripting** サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISCOMMAND**|ANALYSISCOMMAND サブシステムを使用するジョブ ステップの情報です。|  
|**ANALYSISQUERY**|ANALYSISQUERY サブシステムを使用するジョブ ステップの情報です。|  
|**CmdExec**|**CmdExec** サブシステムを使用するジョブ ステップの情報です。|  
|**Distribution**|**Distribution** サブシステムを使用するジョブ ステップの情報です。|  
|**Dts**|[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サブシステムを使用するジョブ ステップの情報です。|  
|**LogReader**|**LogReader** サブシステムを使用するジョブ ステップの情報です。|  
|**[マージ]**|**Merge** サブシステムを使用するジョブ ステップの情報です。|  
|**PowerShell**|**PowerShell** サブシステムを使用するジョブ ステップの情報です。|  
|**QueueReader**|**QueueReader** サブシステムを使用するジョブ ステップの情報です。|  
|**スナップショット**|**Snapshot** サブシステムを使用するジョブ ステップの情報です。|  
|**TSQL**|[!INCLUDE[tsql](../../includes/tsql-md.md)]を実行するジョブ ステップの情報です。|  
  
## <a name="see-also"></a>参照  
 [ジョブ ステップの管理](../../ssms/agent/manage-job-steps.md)   
 [パフォーマンス オブジェクトの使用](../../ssms/agent/use-performance-objects.md)   
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  
