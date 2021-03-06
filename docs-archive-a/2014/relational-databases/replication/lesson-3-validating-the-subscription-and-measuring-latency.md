---
title: 'レッスン 3 : サブスクリプションの検証と待機時間の計測 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: 147f7b93-1804-4e0b-9e17-57a51d035b2a
author: rothja
ms.author: jroth
ms.openlocfilehash: e4893c054d25d131eb2f88f32291606b0b789af7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739696"
---
# <a name="lesson-3-validating-the-subscription-and-measuring-latency"></a>レッスン 3 : サブスクリプションの検証と待機時間の計測
  このレッスンでは、トレーサー トークンを使用して、変更がサブスクライバーにレプリケートされているかどうかを検証し、待機時間を計測します。待機時間とは、パブリッシャーで加えられた変更がサブスクライバーに反映されるまでの所用時間です。 このレッスンを始める前に、前のレッスンの [「レッスン 2: トランザクション パブリケーションへのサブスクリプションの作成」](lesson-2-creating-a-subscription-to-the-transactional-publication.md)を完了している必要があります。  
  
### <a name="to-insert-a-tracer-token-and-view-information-on-the-token"></a>トレーサー トークンを挿入してトークンの情報を表示するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]でパブリッシャーに接続します。次に、サーバー ノードを展開して **[レプリケーション]** フォルダーを右クリックし、 **[レプリケーション モニターの起動]** をクリックします。  
  
     レプリケーション モニターが起動します。  
  
2.  左ペインでパブリッシャー グループを展開し、パブリッシャー インスタンスを展開して、 **[AdvWorksProductTrans]** パブリケーションをクリックします。  
  
3.  **[トレーサー トークン]** タブをクリックします。  
  
4.  **[トレーサーの挿入]** をクリックします。  
  
5.  **[パブリッシャーからディストリビューターまで]** 列、 **[ディストリビューターからサブスクライバーまで]** 列、および **[合計待機時間]** 列で、トレーサー トークンの経過時間を表示します。 値が**Pending**の場合は、トークンが特定のポイントに到達していないことを示します。  
  
## <a name="next-steps"></a>次の手順  
 このレッスンでは、トレーサー トークンを使用して、データの変更がパブリッシャーからスクライバへレプリケートされているかどうかを検証しました。 パブリッシャー側の **Product** テーブルに対してデータの挿入、更新、または削除を行い、レプリケーション後、サブスクライバー側の **Product** テーブルをクエリすることもできます。  
  
 チュートリアル「常時接続サーバー間でのデータのレプリケーション」はこれで完了です。 マージ レプリケーションを使用する類似のチュートリアルについては、 [「チュートリアル: モバイル クライアントとの間のデータのレプリケーション」](tutorial-replicating-data-with-mobile-clients.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [待機時間を計測して Connections for Transactional Replication を検証します。](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
  
