---
title: SQL Server ユーティリティへの接続 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: b9b90b8d-241f-4b74-ac14-de7b10ea1821
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e8e59a28e083fc302faebbcba932c18a04e73a7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633144"
---
# <a name="connect-to-a-sql-server-utility"></a>SQL Server ユーティリティへの接続
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続する前に、ユーティリティ コントロール ポイント (UCP) を作成する必要があります。 詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のリソース正常性を表示および管理するには、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] (SSMS) を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続します。

 SSMS を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続するには、次の手順を実行します。

1.  SSMS を起動します。

2.  SSMS で、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続します。

3.  **[表示]** をクリックし、 **[ユーティリティ エクスプローラー]** をクリックします。

4.  ユーティリティ エクスプローラーのナビゲーション ウィンドウで、![](../../database-engine/media/connect-to-utility.gif "Connect_to_Utility") **[ユーティリティへの接続]** をクリックします。

5.  **[サーバーへの接続]** ダイアログ ボックスで、UCP インスタンス名を指定し、 **[接続]** をクリックします。

6.  ユーティリティ エクスプローラーのナビゲーション ウィンドウを表示し、UCP の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] リソースのツリー ビューを表示します。

 新しい UCP を作成した場合も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティに接続されます。 詳細については、「[SQL Server ユーティリティ コントロール ポイントの作成 &#40;SQL Server ユーティリティ&#41;](create-a-sql-server-utility-control-point-sql-server-utility.md)」を参照してください。

## <a name="see-also"></a>参照
 [SQL Server ユーティリティの機能とタスクの](sql-server-utility-features-and-tasks.md)[表示 Resource Health ポリシーの結果を表示 &#40;SQL Server ユーティリティ&#41;](view-resource-health-policy-results-sql-server-utility.md)


