---
title: ネットワークプロトコルの選択 |Microsoft Docs
description: 共有メモリ、TCP/IP、名前付きパイプなどの SQL Server データベースエンジンへの接続に使用できるネットワークプロトコルを比較対照します。
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
- Named Pipes [SQL Server]
- TCP [SQL Server]
- network protocols [SQL Server], choosing
- protocols [SQL Server], choosing
- NWLink IPX/SPX [SQL Server]
- client configuration [SQL Server], protocols
- VIA
- Multiprotocol Net-Library [SQL Server]
- IPX/SPX [SQL Server]
- Banyan VINES
- protocols [SQL Server], client configuration
ms.assetid: 6565fb7d-b076-4447-be90-e10d0dec359a
author: rothja
ms.author: jroth
ms.openlocfilehash: 13cbfbcbef54759a16729692e4f5a649f387d059
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720678"
---
# <a name="choosing-a-network-protocol"></a><span data-ttu-id="caaf1-103">ネットワーク プロトコルの選択</span><span class="sxs-lookup"><span data-stu-id="caaf1-103">Choosing a Network Protocol</span></span>
  <span data-ttu-id="caaf1-104">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]に接続するには、ネットワーク プロトコルを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-104">To connect to [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] you must have a network protocol enabled.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="caaf1-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、複数のプロトコルに対して同時に要求を処理できます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can service requests on several protocols at the same time.</span></span> <span data-ttu-id="caaf1-106">クライアントは、1 つのプロトコルを使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続します。</span><span class="sxs-lookup"><span data-stu-id="caaf1-106">Clients connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] with a single protocol.</span></span> <span data-ttu-id="caaf1-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がどのプロトコルでリッスンしているかをクライアント プログラムによって判別できない場合は、複数のプロトコルを順に試みるようにクライアントを構成してください。</span><span class="sxs-lookup"><span data-stu-id="caaf1-107">If the client program does not know which protocol [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is listening on, configure the client to sequentially try multiple protocols.</span></span> <span data-ttu-id="caaf1-108">ネットワーク プロトコルを有効化、無効化、または構成するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="caaf1-108">Use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager to enable, disable, and configure network protocols.</span></span>  
  
## <a name="shared-memory"></a><span data-ttu-id="caaf1-109">共有メモリ</span><span class="sxs-lookup"><span data-stu-id="caaf1-109">Shared Memory</span></span>  
 <span data-ttu-id="caaf1-110">共有メモリは、使用できる最も単純なプロトコルであり、構成可能な設定はありません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-110">Shared memory is the simplest protocol to use and has no configurable settings.</span></span> <span data-ttu-id="caaf1-111">共有メモリ プロトコルを使用するクライアントは、同じコンピューター上で実行されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにしか接続できないため、ほとんどのデータベース操作にとって実用的ではありません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-111">Because clients using the shared memory protocol can only connect to a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance running on the same computer, it is not useful for most database activity.</span></span> <span data-ttu-id="caaf1-112">共有メモリ プロトコルは、他のプロトコルが正しく構成されていない可能性がある場合に、トラブルシューティングを行うために使用できます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-112">Use the shared memory protocol for troubleshooting when you suspect the other protocols are configured incorrectly.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="caaf1-113">MDAC 2.8 以前を使用しているクライアントでは、共有メモリ プロトコルを使用できません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-113">Clients that use MDAC 2.8 or earlier cannot use shared memory protocol.</span></span> <span data-ttu-id="caaf1-114">このようなクライアントで共有メモリ プロトコルの使用を試みた場合は、自動的に名前付きパイプ プロトコルに切り替わります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-114">If these clients try this, they are automatically switched to the named pipes protocol.</span></span>  
  
## <a name="tcpip"></a><span data-ttu-id="caaf1-115">TCP/IP</span><span class="sxs-lookup"><span data-stu-id="caaf1-115">TCP/IP</span></span>  
 <span data-ttu-id="caaf1-116">TCP/IP は、インターネットで広く使われている一般的なプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="caaf1-116">TCP/IP is a common protocol widely used over the Internet.</span></span> <span data-ttu-id="caaf1-117">このプロトコルは、多様なハードウェア アーキテクチャやオペレーティング システムを備えたコンピューターが相互に接続されているネットワーク上の通信を実現します。</span><span class="sxs-lookup"><span data-stu-id="caaf1-117">It communicates across interconnected networks of computers that have diverse hardware architectures and various operating systems.</span></span> <span data-ttu-id="caaf1-118">TCP/IP には、ネットワーク トラフィックをルーティングするための標準や、高度なセキュリティ機能も含まれています。</span><span class="sxs-lookup"><span data-stu-id="caaf1-118">TCP/IP includes standards for routing network traffic and offers advanced security features.</span></span> <span data-ttu-id="caaf1-119">TCP/IP は、今日の業務で最も一般的に使用されているプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="caaf1-119">It is the most popular protocol that is used in business today.</span></span> <span data-ttu-id="caaf1-120">TCP/IP を使用するためにコンピューターを構成する作業は複雑になることもありますが、ほとんどのネットワーク コンピューターには適切な構成が既に適用されています。</span><span class="sxs-lookup"><span data-stu-id="caaf1-120">Configuring your computer to use TCP/IP can be complex, but most networked computers are already correctly configured.</span></span> <span data-ttu-id="caaf1-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーで表示されない TCP/IP 設定を構成するには、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="caaf1-121">To configure the TCP/IP settings that are not exposed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows documentation.</span></span>  
  
## <a name="named-pipes"></a><span data-ttu-id="caaf1-122">名前付きパイプ</span><span class="sxs-lookup"><span data-stu-id="caaf1-122">Named Pipes</span></span>  
 <span data-ttu-id="caaf1-123">名前付きパイプは、ローカル エリア ネットワークのために開発されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="caaf1-123">Named Pipes is a protocol developed for local area networks.</span></span> <span data-ttu-id="caaf1-124">このプロトコルでは、1 つのプロセスが、メモリの一部を使用して別のプロセスに情報を渡します。このとき、1 つ目のプロセスの出力が 2 つ目のプロセスの入力になります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-124">A part of memory is used by one process to pass information to another process, so that the output of one is the input of the other.</span></span> <span data-ttu-id="caaf1-125">2 つ目のプロセスは、ローカル (1 つ目のプロセスと同じコンピューター上にある) またはリモート (ネットワーク コンピューター上にある) のどちらでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-125">The second process can be local (on the same computer as the first) or remote (on a networked computer).</span></span>  
  
## <a name="named-pipes-vs-tcpip-sockets"></a><span data-ttu-id="caaf1-126">名前付きパイプと TCP/IP ソケット</span><span class="sxs-lookup"><span data-stu-id="caaf1-126">Named Pipes vs. TCP/IP Sockets</span></span>  
 <span data-ttu-id="caaf1-127">高速ローカル エリア ネットワーク (LAN) 環境の場合、TCP/IP ソケットを使用するクライアントと、名前付きパイプを使用するクライアントには、パフォーマンスの点でほとんど差はありません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-127">In a fast local area network (LAN) environment, Transmission Control Protocol/Internet Protocol (TCP/IP) Sockets and Named Pipes clients are comparable with regard to performance.</span></span> <span data-ttu-id="caaf1-128">ただし、両者のパフォーマンスの違いは、ワイド エリア ネットワーク (WAN) やダイヤルアップ ネットワークなどの低速のネットワークの場合に明らかになります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-128">However, the performance difference between the TCP/IP Sockets and Named Pipes clients becomes apparent with slower networks, such as across wide area networks (WANs) or dial-up networks.</span></span> <span data-ttu-id="caaf1-129">これは、プロセス間通信 (IPC) メカニズムによるピア間の通信方法が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="caaf1-129">This is because of the different ways the interprocess communication (IPC) mechanisms communicate between peers.</span></span>  
  
 <span data-ttu-id="caaf1-130">名前付きパイプの場合、ネットワーク通信は通常、より対話的なものになります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-130">For named pipes, network communications are typically more interactive.</span></span> <span data-ttu-id="caaf1-131">ピアは、別のピアから read コマンドによる要求があるまでデータを送信しません。</span><span class="sxs-lookup"><span data-stu-id="caaf1-131">A peer does not send data until another peer asks for it using a read command.</span></span> <span data-ttu-id="caaf1-132">ネットワークでの読み取りでは通常、データの読み取りを開始する前に、一連の名前付きパイプ メッセージを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-132">A network read typically involves a series of peek named pipes messages before it starts to read the data.</span></span> <span data-ttu-id="caaf1-133">これらは低速のネットワークにとって大きなコストとなり、過剰なネットワーク トラフィックを引き起こすので、他のネットワーク クライアントに影響を及ぼします。</span><span class="sxs-lookup"><span data-stu-id="caaf1-133">These can be very costly in a slow network and cause excessive network traffic, which in turn affects other network clients.</span></span>  
  
 <span data-ttu-id="caaf1-134">また、ローカル パイプとネットワーク パイプのどちらを指しているのかを区別することも重要です。</span><span class="sxs-lookup"><span data-stu-id="caaf1-134">It is also important to clarify if you are talking about local pipes or network pipes.</span></span> <span data-ttu-id="caaf1-135">サーバー アプリケーションが、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを実行しているコンピューター上でローカルに実行されている場合、ローカルの名前付きパイプ プロトコルを選択できます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-135">If the server application is running locally on the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the local Named Pipes protocol is an option.</span></span> <span data-ttu-id="caaf1-136">ローカルの名前付きパイプはカーネル モードで実行され、非常に高速です。</span><span class="sxs-lookup"><span data-stu-id="caaf1-136">Local named pipes runs in kernel mode and is very fast.</span></span>  
  
 <span data-ttu-id="caaf1-137">TCP/IP ソケットの場合、データ伝送はより効率的でオーバーヘッドも少なくて済みます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-137">For TCP/IP Sockets, data transmissions are more streamlined and have less overhead.</span></span> <span data-ttu-id="caaf1-138">また、データ伝送にウィンドウ化や遅延確認応答など、TCP/IP ソケットのパフォーマンス向上メカニズムを利用できます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-138">Data transmissions can also take advantage of TCP/IP Sockets performance enhancement mechanisms such as windowing, delayed acknowledgements, and so on.</span></span> <span data-ttu-id="caaf1-139">これは、低速ネットワークの場合に非常に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-139">This can be very helpful in a slow network.</span></span> <span data-ttu-id="caaf1-140">アプリケーションの種類によっては、このようなパフォーマンスの違いが大きく影響します。</span><span class="sxs-lookup"><span data-stu-id="caaf1-140">Depending on the type of applications, such performance differences can be significant.</span></span>  
  
 <span data-ttu-id="caaf1-141">TCP/IP ソケットは、バックログ キューもサポートしています。</span><span class="sxs-lookup"><span data-stu-id="caaf1-141">TCP/IP Sockets also support a backlog queue.</span></span> <span data-ttu-id="caaf1-142">名前付きパイプでは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への接続試行時にパイプがビジー状態になるエラーが生じる可能性があるので、それに比べると、接続をある程度スムーズにできる効果があります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-142">This can provide a limited smoothing effect compared to named pipes that could lead to pipe-busy errors when you are trying to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="caaf1-143">一般に、TCP/IP は低速の LAN、WAN、またはダイヤルアップ ネットワークに適しています。一方、ネットワークの速度に関する問題がない場合は、名前付きパイプの方が多くの機能を備えており、使いやすく、構成できるオプションも多いので適している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-143">Generally, TCP/IP is preferred in a slow LAN, WAN, or dial-up network, whereas named pipes can be a better choice when network speed is not the issue, as it offers more functionality, ease of use, and configuration options.</span></span>  
  
## <a name="enabling-the-protocol"></a><span data-ttu-id="caaf1-144">プロトコルの有効化</span><span class="sxs-lookup"><span data-stu-id="caaf1-144">Enabling the Protocol</span></span>  
 <span data-ttu-id="caaf1-145">プロトコルを使用するには、クライアントとサーバーの両方で有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="caaf1-145">The protocol must be enabled on both the client and server to work.</span></span> <span data-ttu-id="caaf1-146">サーバーは、有効なすべてのプロトコルで同時に要求をリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-146">The server can listen for requests on all enabled protocols at the same time.</span></span> <span data-ttu-id="caaf1-147">クライアントは、プロトコルを選択することも、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーの一覧の順でプロトコルを試すこともできます。</span><span class="sxs-lookup"><span data-stu-id="caaf1-147">Client computers can pick one, or try the protocols in the order listed in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager.</span></span>  
  
 <span data-ttu-id="caaf1-148">プロトコルを構成して [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続する方法に関する簡単なチュートリアルについては、「 [チュートリアル:データベース エンジンの概要](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="caaf1-148">For a short tutorial about how to configure protocols and connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)], see [Tutorial: Getting Started with the Database Engine](../../relational-databases/tutorial-getting-started-with-the-database-engine.md).</span></span>  
  
  