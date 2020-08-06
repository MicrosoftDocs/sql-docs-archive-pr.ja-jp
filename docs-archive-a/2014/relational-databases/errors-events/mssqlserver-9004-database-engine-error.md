---
title: MSSQLSERVER_9004 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9004 (Database Engine error)
ms.assetid: b528bb49-340c-4a81-9c8d-cefce6562f16
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 910665b4349e5b13c5abb4fd687dcf0c6fc122cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640005"
---
# <a name="mssqlserver_9004"></a>MSSQLSERVER_9004
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9004|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|LOG_CORRUPT|  
|メッセージ テキスト|データベース '%.*ls' のログを処理中にエラーが発生しました。  可能な場合は、バックアップから復元してください。 バックアップを使用できない場合は、ログの再構築が必要になることがあります。|  
  
## <a name="explanation"></a>説明  
 ロールバック、復旧、またはレプリケーションの操作で、ログの処理中にエラーが発生しました。 オペレーティング システムで検出されたエラーか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で検出された内部的な一貫性エラーを示している可能性があります。  
  
## <a name="user-action"></a>ユーザーの操作  
 次のいずれかのアクションでこのエラーを修正します。  
  
-   バックアップからの復元を実行する。  
  
-   ログを再構築する。  
  
 また、システムのイベント ログまたはエラー ログで、システム内の問題がエラーの原因になっていないか調べます。  
  
  
