---
title: SQL Server の ExecStatistics オブジェクト | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:ExecStatistics
- ExecStatistics object
ms.assetid: 4f8557a8-345f-4622-a8a5-763a0388ad94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d1a50c97add4708a58b9edc45fd49982b97a51ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633093"
---
# <a name="sql-server-execstatistics-object"></a>SQL Server の ExecStatistics オブジェクト
  Microsoft SQL Server の **SQLServer:ExecStatistics** オブジェクトには、さまざまな実行を監視するためのカウンターがあります。  
  
 次の表では、SQL Server の **Exec Statistics** カウンターについて説明します。  
  
|SQL Server Exec Statistics のカウンター|説明|  
|-----------------------------------------|-----------------|  
|**Distributed Query**|分散クエリの実行に関連する統計データ。|  
|**DTC calls**|DTC 呼び出しの実行に関連する統計データ。|  
|**Extended Procedures**|拡張プロシージャの実行に関連する統計データ。|  
|**OLEDB calls**|OLEDB 呼び出しの実行に関連する統計データ。|  
  
 オブジェクトの各カウンターには、次のインスタンスが含まれています。  
  
|Item|説明|  
|----------|-----------------|  
|**Average execution time (ms)**|選択した種類の実行の平均実行時間。|  
|**Cumulative execution time (ms) per second**|選択した種類の実行の 1 秒あたりの累積実行時間。|  
|**Execs in progress**|選択した種類の実行のうち現在進行中の数。|  
|**Exec started per second**|選択した種類の実行が 1 秒あたりに開始される数。|  
  
## <a name="see-also"></a>参照  
 [リソースの利用状況の監視 &#40;システム モニター&#41;](monitor-resource-usage-system-monitor.md)  
  
  
