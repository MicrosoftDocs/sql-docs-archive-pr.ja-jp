---
title: ディストリビューター | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.selectdistributor.f1
ms.assetid: 787f0e9c-09dd-438a-bc04-5b8f99c127b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c601a540088b5cd9d7a2033510a5cf9b83c3170e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632368"
---
# <a name="distributor"></a>ディストリビューター
  **[ディストリビューター]** ページは、ディストリビューションの構成ウィザードとパブリケーションの新規作成ウィザードで表示されます。 ディストリビューターは、ディストリビューション データベースを備え、あらゆる種類のレプリケーションのメタデータおよび履歴データを格納するサーバーです。 ディストリビューターは、トランザクション レプリケーションのトランザクションも格納します。 ディストリビューターは、パブリッシャーと同じサーバーであっても、別のサーバーであってもかまいません。前者の場合はローカル ディストリビューターで、後者の場合はリモート ディストリビューターになります。 ディストリビューターの役割は、実装するレプリケーションの種類によって異なります。 一般に、マージ レプリケーションやスナップショット レプリケーションに比べて、トランザクション レプリケーションに対するディストリビューターの役割は大きくなります。 マージ レプリケーションおよびスナップショット レプリケーションではローカル ディストリビューターを使用するのが一般的です。ただし、非常に稼働率が高いシステムでのトランザクション レプリケーションの場合は、リモート ディストリビューターを利用すると効果的です。  
  
 サーバーがディストリビューターとして指定されると、次のようなリソースが新たに消費されることになります。  
  
-   一般的な方法でパブリケーションのスナップショット ファイルがサーバーに格納される場合は、そのためのディスク領域  
  
-   ディストリビューション データベースを格納するためのディスク領域  
  
-   ディストリビューター上で実行されるプッシュ サブスクリプションのために、レプリケーション エージェントによって使用されるプロセッサ時間  
  
 ディストリビューターとして指定するサーバーには、サーバー上でさまざまな機能を果たしながら、レプリケーションの処理を実行できるだけの十分なディスク容量とプロセッサ パワーが必要です。  
  
## <a name="options"></a>Options  
 **'\<ServerName>' を独自のディストリビューターとする (SQL Server はディストリビューション データベースとログを作成します)**  
 このオプションを選択すると、ディストリビューターとして接続するサーバーを構成できます。  
  
 **[以下のサーバーをディストリビューターとして使用する (選択するサーバーはディストリビューターとして構成されている必要があります)]**  
 別のサーバーをディストリビューターとして構成するには、このオプションを選択し、以下のサーバーの名前をクリックします。  
  
 **追加**  
 ディストリビューターとして構成するサーバーが表示されていない場合は、 **[追加]** をクリックし、目的のサーバーを識別して一覧に追加します。  
  
> [!NOTE]  
>  リモート サーバーをディストリビューターとして使用するには、リモート サーバーがディストリビューターとして構成されている必要があります。 このウィザードの実行の対象となるサーバーは、そのディストリビューター上でパブリッシャーとして有効に設定されている必要があります。  
  
## <a name="see-also"></a>参照  
 [[ディストリビューションの構成]](configure-distribution.md)   
 [パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)  
  
  