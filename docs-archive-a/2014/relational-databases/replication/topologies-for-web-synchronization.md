---
title: Web 同期トポロジ | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web synchronization, topologies
- IIS server configuration [SQL Server replication]
ms.assetid: 59444faf-bcb6-4421-a3df-8715753e453b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5e28ca5a222e2286d154c16ef41d3147dc56e25a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641605"
---
# <a name="topologies-for-web-synchronization"></a>Web 同期トポロジ
  さまざまな [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Web 同期レプリケーション トポロジを選択できます。 Web 同期の一般的な構成には以下のものがあります。  
  
-   単一サーバー  
  
-   2 台のサーバー  
  
-   複数台の [!INCLUDE[msCoName](../../includes/msconame-md.md)] インターネット インフォメーション サービス (IIS) システムと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の再パブリッシュ  
  
 Web 同期の構成の詳細については、「[Configure Web Synchronization (Web 同期の構成)](configure-web-synchronization.md)」をご覧ください。  
  
## <a name="single-server"></a>シングル サーバー  
 最も単純なトポロジでは、IIS、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャー、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ディストリビューターをすべて 1 つのサーバー上に配置します。 サブスクライバーは、パブリッシャー上の IIS に接続することによって同期します。 パブリッシャーは、ファイアウォール内に置くこともできます。  
  
> [!NOTE]  
>  この構成は、イントラネットを使用する場合にのみお勧めします。 他のケースでは、IIS サーバーと [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] パブリッシャー/ディストリビューターを別々のコンピューター上に配置することをお勧めします。  
  
 ![シングル サーバーでの Web 同期](media/web-sync02.gif "シングル サーバーでの Web 同期")  
  
## <a name="two-servers"></a>2 台のサーバー  
 IIS を展開しているサーバーとは別のサーバーに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のパブリッシャーとディストリビューターを構成することもできます。 IIS を実行しているサーバーは、ファイアウォールを使用してインターネットから切り離すことができます。 サブスクライバーは IIS に接続することによって同期します。  
  
 ![2 台のサーバーでの Web 同期](media/web-sync03.gif "2 台のサーバーでの Web 同期")  
  
## <a name="multiple-iis-systems-and-sql-server-republishing"></a>複数台の IIS システムと SQL Server の再パブリッシュ  
 多数のサブスクライバーをサポートし、それらを同時に同期する必要がある場合は、IIS を実行している複数のコンピューターに処理の負荷を分散させることができます。  
  
 ![複数の IIS サーバーでの Web 同期](media/web-sync04.gif "複数の IIS サーバーでの Web 同期")  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を実行しているコンピューターにも負荷の分散が必要となった場合は、複数のコンピューターに再パブリッシュの階層を作成することもできます。 最上位レベルのパブリッシャーはデータをサブスクライバーにパブリッシュし、これを受けてサブスクライバーはデータを再パブリッシュします。結果としてサブスクライバーからの要求の負荷が分散されます。  
  
> [!NOTE]  
>  サブスクライバーは、特定のパブリッシャーとのみ同期できます。 たとえば、リパブリッシャー A が使用できない場合に、リパブリッシャー A に対するサブスクライバーをリパブリッシャー B と同期することはできません。  
  
 ![再パブリッシュでの Web 同期](media/web-sync05.gif "再パブリッシュでの Web 同期")  
  
## <a name="see-also"></a>参照  
 [Configure Web Synchronization](configure-web-synchronization.md)   
 [マージ レプリケーションの Web 同期](web-synchronization-for-merge-replication.md)  
  
  
