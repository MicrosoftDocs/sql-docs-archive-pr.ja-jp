---
title: SQL Server、Memory Node | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 55b28ba9-b6d5-4ea9-8103-db8a72f42982
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d5bbc3f581ea9ececeb7d55a614ef27c3c72de7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645004"
---
# <a name="sql-server-memory-node"></a>SQL Server、Memory Node
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の **Memory Node** オブジェクトには、NUMA ノードのサーバー メモリの使用状況を監視するためのカウンターが用意されています。  
  
## <a name="memory-node-counters"></a>Memory Node カウンター  
 次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Memory Node** カウンターについて説明します。  
  
|SQL Server Memory Manager カウンター|説明|  
|----------------------------------------|-----------------|  
|**Database Node Memory (KB)**|このノードでデータベース ページに現在使用しているメモリの量を指定します。|  
|**Free Node Memory (KB)**|このノードの未使用のメモリの量を指定します。|  
|**Foreign Node Memory (KB)**|このノードの NUMA ローカル メモリ以外のメモリの量を指定します。|  
|**Stolen Memory Node (KB)**|このノードでデータベース ページ以外に使用しているメモリの量を指定します。|  
|**Target Node Memory**|このノードの理想的なメモリの量を指定します。|  
|**Total Node Memory**|サーバーがこのノードでコミットしているメモリの総容量を示します。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;System Monitor&#41;](monitor-resource-usage-system-monitor.md)   
 [SQL Server: Buffer Manager オブジェクト](sql-server-buffer-manager-object.md)   
 [sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql)  
  
  
