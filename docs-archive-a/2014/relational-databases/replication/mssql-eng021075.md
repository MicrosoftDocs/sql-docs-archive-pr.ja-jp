---
title: MSSQL_ENG021075 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG021075 error
ms.assetid: c8c29543-d1f6-49d5-b6c8-e8c3aa373090
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f2428038326681f5f8eb877e5c3017ced30f00
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643251"
---
# <a name="mssql_eng021075"></a>MSSQL_ENG021075
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21075|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|パブリケーション '%s' の初期スナップショットはまだ使用できません。|  
  
## <a name="explanation"></a>説明  
 エラー MSSQL_ENG021075 は、スナップショット エージェントがスナップショットの生成を終える前にディストリビューション エージェントまたはマージ エージェントが開始されると発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 サブスクリプションが作成されてから、または最後にサブスクリプションの再初期化を選択してから、一度もパブリケーションのスナップショット エージェントが開始されていない場合は、スナップショット エージェントを開始し、完了した後でディストリビューション エージェントまたはマージ エージェントを開始します。 詳細については、「[スナップショットの作成および適用](create-and-apply-the-snapshot.md)」を参照してください。  
  
 スナップショット エージェントが完了しない場合は、スナップショット エージェントの履歴でエラーを確認して対応します。 レプリケーション モニターでのエージェントの状態やエラーの詳細の表示について詳しくは、「[レプリケーション モニターを使用して情報を表示し、タスクを実行する](monitor/view-information-and-perform-tasks-replication-monitor.md)」を参照してください。  
  
 エラーの発生が継続する場合は、エージェントのログ記録を増やし、ログの出力ファイルを指定します。 エラーのコンテキストによっては、エラーや他のエラー メッセージにつながる手順が示される可能性もあります。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)  
  
  
