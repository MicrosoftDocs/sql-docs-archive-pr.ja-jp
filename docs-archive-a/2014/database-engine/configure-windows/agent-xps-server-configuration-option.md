---
title: Agent XP サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Agent XPs option
- extended stored procedures [SQL Server], SQL Server Agent
ms.assetid: 2e1c6c64-5ce7-4357-98c7-ac7763a9f9de
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 541c81ea8d9f782a9c1ea391824b90a6fee772d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642311"
---
# <a name="agent-xps-server-configuration-option"></a>Agent XP サーバー構成オプション
  **Agent XPs** オプションは、このサーバーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にする場合に使用します。 このオプションを有効にしないと、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のオブジェクト エクスプローラーに [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] エージェントのノードが表示されません。  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ツールを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスを開始すると、これらの拡張ストアド プロシージャは自動的に有効になります。 詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] のオブジェクト エクスプローラーには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント サービスの状態にかかわらず、これらの拡張ストアド プロシージャを有効にしない限り、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのノードのコンテンツは表示されません。  
  
 指定できる値は、  
  
-   **0**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できないことを示します (既定)。  
  
-   **1**は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを使用できることを示します。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
## <a name="examples"></a>例  
 次の例では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの拡張ストアド プロシージャを有効にします。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Agent XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [管理タスクの自動化 &#40;SQL Server エージェント&#41;](../../ssms/agent/sql-server-agent.md)   
 [SQL Server エージェント サービスの開始、停止、または一時停止](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
  
