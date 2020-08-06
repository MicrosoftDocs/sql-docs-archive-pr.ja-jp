---
title: トポロジの構成 (ピア ツー ピア レプリケーション) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.p2pwizard.peers.f1
ms.assetid: 5377c59f-2e25-4852-a306-c87ae3dca9fd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2dfc09f5ae7f488afd46f29c301d11b7687e0a4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631837"
---
# <a name="configure-topology-peer-to-peer-replication"></a>[トポロジの構成] (ピア ツー ピア レプリケーション)
  **[トポロジの構成]** ページを使用すると、新しいノードの追加、ノードの削除、既存のノード間の新しい接続の追加など、一般的な構成タスクを実行できます。 このウィザードの **[パブリケーション]** ページで選択したノードがデザイン画面に表示されます。 構成オプションを指定するには、ノード、接続、またはデザイン画面を右クリックします。

> [!NOTE]
>  ピア ツー ピア トポロジ構成ウィザードでは、ウィザードの終了時にトポロジ情報が要求されます。 すべてのノードが情報の要求に応答する前にウィザードを閉じて再度開くと、ウィザードに不完全なネットワークが表示される場合があります。

## <a name="options"></a>オプション
 **[トポロジの構成]** ページには、要素を右クリックすると表示されるインターフェイス要素およびオプションがあります。 次の表では、各インターフェイス要素を説明します。

|インターフェイス要素|説明|
|-----------------------|-----------------|
|デザイン画面|その他のインターフェイス要素を表示します。 要素を追加するには、デザイン画面を右クリックします。|
|![トポロジの最初のノード](media/p2pwizard-firstnode.gif "トポロジの最初のノード")|トポロジの元のノード。 元のノードのパブリケーション データベースのコピーを使用して、新しいノードが初期化されます。|
|完全な情報またはそれ以降のバージョンを![持つノード](media/p2pwizard-complete.gif "情報が完全なノード")。レプリケーションには完全な情報が含まれています。 構成オプションを指定するには、ノードを右クリックします。|
|![情報が不完全なノード](media/p2pwizard-incomplete.gif "情報が不完全なノード")|レプリケーションに含まれている情報が不完全なノード。 構成オプションを指定するには、ノードを右クリックします。 レプリケーションに含まれている情報は、次のいずれかの理由で不完全になっています。<br /><br /> ウィザードで必要なメタデータが一部格納されない [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] のインスタンスがノードで実行されています。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の最新バージョンがノードで実行されていますが、レプリケーションがノードからサブスクリプション情報を取得できません。 このような場合は、次の方法で対処してください。<br />-ノードのデータベースがオンラインであること、およびノードに接続するディストリビューションエージェントと同じ資格情報を使用して接続できることを確認します。<br />-ノードに接続するログリーダーエージェントおよびすべてのディストリビューションエージェントが実行されていることを確認します。<br />-すべてのトポロジ情報を収集するために、更新のタイムアウトが十分に高い値に設定されていることを確認します。 タイムアウトを設定するには、デザイン画面を右クリックして **[更新のタイムアウトの設定]** をクリックします。|
|矢印の付いた灰色の線|2 つのノード間の接続。 接続を追加するには、接続するノードのいずれかを右クリックします。 接続を削除するには、接続を右クリックします。<br /><br /> 線に付いている矢印が単一の場合、レプリケーションに含まれているいずれかのノードの情報が不完全です。|

### <a name="options-for-the-design-surface"></a>デザイン画面のオプション
 **グラフの再描画**トポロジを更新せずに、デザイン画面でオブジェクトを再描画します。 再表示すると、トポロジが見やすくなる場合があります。

 **トポロジの更新**トポロジ内の各ノードに対してクエリを実行し、各ノードに関する更新された情報を表示します。 多数のノードが存在する場合、このプロセスには数分かかる場合があります。

 ウィザードによってトポロジ情報が要求された場合、すべてのノードが要求に応答する前にウィザードを閉じて再度開くと、このページにトポロジのノードが一部表示されない場合があります。

 **新しいピアノードの追加**のインスタンスを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ピアツーピアトポロジに追加します。 インスタンスをノードとして追加すると、ウィザードの完了後にそのインスタンスでパブリケーションが作成されます。 ノードの追加後に、そのノードを右クリックして新しいノードと既存のノード間の接続を追加します。

 ピア ツー ピア トポロジに参加するためには、インスタンスが次の要件を満たしている必要があります。

-   ディストリビューターとして構成されているか、リモート ディストリビューターに関連付けられている。

-   レプリケーションに関係するデータベースのコピーが含まれている。 このコピーは通常、元のパブリケーション データベースの復元されたバックアップです。

 **表示するノードの選択**デザイン画面に表示するノードを選択します。 このオプションは、トポロジに多数のノードが存在する場合に役立ちます。 デザイン画面に表示されているノード間にしか接続を追加できないことに注意してください。

 **更新のタイムアウトの設定**操作がタイムアウトするまでに更新プロセスを実行できる期間を指定します。

### <a name="options-for-each-node"></a>各ノードのオプション
 **新しいピア接続の追加**2つのノード間の接続を追加します。 たとえば、ノード A とノード B 間の接続を追加すると、レプリケーションによって 2 つのサブスクリプションが追加されます。最初のサブスクリプションによってノード A がノード B のパブリケーションから変更を受信できるようになり、2 番目のサブスクリプションによってノード B がノード A のパブリケーションから変更を受信できるようになります。

 **ピアノードの削除**トポロジからノードを削除します。 たとえば、ノード C を削除すると、そのノードのパブリケーションが削除されます。 ノード A とノード C、およびノード B とノード C 間のサブスクリプションも削除されます。 ノード C のデータベースは削除されず、パブリッシングおよびディストリビューションは無効になりません。

> [!NOTE]
>  ピア ツー ピア レプリケーションを構成する場合は、各ノードに ID を指定します。 この ID は、トポロジ内のすべてのノードに対して一意である必要があり、[MSpeer_originatorid_history](/sql/relational-databases/system-tables/mspeer-originatorid-history-transact-sql) システム テーブルの originator_id 列に格納されます。 ノードがトポロジから削除されても、ID は履歴テーブルに保持されたままです。 ID が保持されるのは、削除されたノードからの変更がトポロジ全体でレプリケートされたままである場合に誤った競合が発生しないようにするためです。 新しいノードに対してこの ID を再利用する場合は、先にすべてのノードで MSpeer_originatorid_history テーブルからこの ID を手動で削除する必要があります。 ノードの ID を削除する前に、 [sp_requestpeerresponse](/sql/relational-databases/system-stored-procedures/sp-requestpeerresponse-transact-sql) を実行して、そのノードから発行されたすべての変更がレプリケートされていることを確認します。

 **表示されているすべてのノードに接続する**選択したノードと他のすべてのノード間の接続を追加します。 たとえば、3 ノード トポロジのノード C に対してこのオプションを選択すると、レプリケーションによって 4 つのサブスクリプションが追加されます。このうちの 2 つのサブスクリプションによってノード A とノード B がノード C のパブリケーションから変更を受信できるようになり、他の 2 つのサブスクリプションによってノード C がノード A とノード B のパブリケーションから変更を受信できるようになります。

 **表示するノードの選択**デザイン画面に表示するノードを選択します。 このオプションは、トポロジに多数のノードが存在する場合に役立ちます。 デザイン画面に表示されているノード間にしか接続を追加できないことに注意してください。

### <a name="options-for-the-connection-arrows"></a>接続矢印のオプション
 **ピア接続の削除**2つのノード間の接続を削除します。 たとえば、ノード A とノード B 間の接続を削除すると、レプリケーションによって 2 つのサブスクリプション (ノード A がノード B のパブリケーションから変更を受信できるようにしているサブスクリプションと、ノード B がノード A のパブリケーションから変更を受信できるようにしているサブスクリプション) が削除されます。

## <a name="see-also"></a>参照
 [パブリッシングおよびディストリビューション](configure-publishing-and-distribution.md)[の構成ピアツーピアトポロジの管理レプリケーション Transact-sql プログラミング&#41;](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md) [ピアツーピアトランザクションレプリケーション](transactional/peer-to-peer-transactional-replication.md)の &#40;

