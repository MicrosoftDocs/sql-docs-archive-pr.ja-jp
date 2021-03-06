---
title: MSSQLSERVER_3431 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3431 (Database Engine error)
ms.assetid: 9541217f-e5c6-4a12-a19a-006058f1d3f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9b62047a25d71ca05dc3ab03651e5672353bc0a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643859"
---
# <a name="mssqlserver_3431"></a>MSSQLSERVER_3431
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|3431|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|UNRESOLVED_XACT|  
|メッセージ テキスト|トランザクションの結果を解決できないので、データベース '%.*ls' (データベース ID %d) を復旧できませんでした。 Microsoft 分散トランザクション コーディネーター (MS DTC) のトランザクションは準備されていましたが、MS DTC では解決策を決定できませんでした。 解決するには、MS DTC の修正、完全バックアップからの復元、またはデータベースの修復のいずれかを実行してください。|  
  
## <a name="explanation"></a>説明  
 データベースをシャットダウンしたときに、[!INCLUDE[msCoName](../../includes/msconame-md.md)] 分散トランザクション コーディネーター (MS DTC) を使用する分散トランザクションの 1 つ以上が完了しませんでした。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、MS DTC からの詳細な情報がないとトランザクションの完了やロールバックを行うことができないので、このデータベースの復旧は失敗します。  
  
## <a name="user-action"></a>ユーザーの操作  
 このデータベースを復旧するには、まず MS DTC の問題を解決する必要があります。 MS DTC の問題を調査するため、Windows イベント ログを確認します。 MS DTC の問題を解決してデータベースを復旧できない場合は、データベースのバックアップを復元します。  
  
  
