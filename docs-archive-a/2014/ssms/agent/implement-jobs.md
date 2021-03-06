---
title: ジョブの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent]
- SQL Server Agent jobs
- SQL Server Agent jobs, about jobs
- jobs [SQL Server Agent], about jobs
ms.assetid: 69e06724-25c7-4fb3-8a5b-3d4596f21756
author: stevestein
ms.author: sstein
ms.openlocfilehash: 1925b3113db8d7c57ac4344958c0247763cfd1b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631463"
---
# <a name="implement-jobs"></a>ジョブの実装
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを使用すると、定型的な管理作業を自動化して定期的に実行し、管理を効率化できます。  
  
 ジョブとは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによって順番に実行される一連の操作です。 ジョブで実行できる操作は多岐にわたり、 [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト、コマンド ライン アプリケーション、Microsoft ActiveX スクリプト、Integration Services パッケージ、Analysis Services のコマンドおよびクエリ、レプリケーション タスクなどを実行できます。 ジョブでは、繰り返し行う作業や、スケジュールに設定できる作業を実行できます。また、警告を生成してジョブの状態をユーザーに自動的に通知できるので、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の管理を大幅に簡素化できます。  
  
 ジョブは手動で実行することも、スケジュールや警告に応じて実行されるように構成することもできます。  
  
## <a name="related-tasks"></a>Related Tasks  
  
|||  
|-|-|  
|**説明**|**トピック**|  
|ジョブの作成と所有権の割り当てについて説明します。|[ジョブの作成](create-jobs.md)|  
|ジョブをカテゴリごとに編成するための情報を記載しています。|[ジョブの整理](organize-jobs.md)|  
|ユーザーが作成できるさまざまな種類のジョブ ステップおよびそれらの管理方法について説明します。|[ジョブ ステップの管理](manage-job-steps.md)|  
|ジョブの実行開始時刻および実行頻度を定義する方法について説明します。|[スケジュールの作成とジョブへのアタッチ](create-and-attach-schedules-to-jobs.md)|  
|(スケジュールを設定せずに) ジョブを手動で実行するための情報を記載しています。|[ジョブの実行](run-jobs.md)|  
|ジョブに応答できるように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成する方法について説明します。 たとえば、ジョブが完了したら管理者に通知するように [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを構成できます。|[ジョブ応答の指定](specify-job-responses.md)|  
|既存のジョブおよびその実行履歴を参照する方法と、既存のジョブを変更する方法について説明します。|[ジョブの表示または変更](view-or-modify-jobs.md)|  
|ジョブを削除する方法について説明します。|[ジョブの削除](delete-jobs.md)|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのセキュリティの実装](implement-sql-server-agent-security.md)  
  
  
