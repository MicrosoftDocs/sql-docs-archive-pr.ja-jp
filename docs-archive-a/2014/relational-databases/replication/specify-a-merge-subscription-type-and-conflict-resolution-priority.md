---
title: マージサブスクリプションの種類と競合解決の優先度を指定します (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], merge subscription resolvers
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 2b828d83-2341-4924-b92a-4f81a22246c0
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a19ae6246fe59308283fbaf2f35e2c49f96b140c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743209"
---
# <a name="specify-a-merge-subscription-type-and-conflict-resolution-priority-sql-server-management-studio"></a>マージ サブスクリプションの種類と競合解決の優先度の指定 (SQL Server Management Studio)
  サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、マージ サブスクリプションの種類と競合解決の優先度を指定します。 このウィザードの使用方法の詳細については、「 [Create a Pull Subscription](create-a-pull-subscription.md) 」および「 [Create a Push Subscription](create-a-push-subscription.md)」を参照してください。  
  
 サブスクリプションの種類はサブスクリプションの作成後には変更できませんが、サーバー サブスクリプションの種類の優先度は、 **[サブスクリプションのプロパティ - \<Publisher>:\<PublicationDatabase>]** ダイアログ ボックスで変更できます。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Push Subscription Properties](view-and-modify-push-subscription-properties.md) 」および「 [View and Modify Pull Subscription Properties](view-and-modify-pull-subscription-properties.md)」を参照してください。  
  
### <a name="to-specify-a-merge-subscription-type-and-conflict-resolution-priority"></a>マージ サブスクリプションの種類と競合解決の優先度を指定するには  
  
1.  サブスクリプションの新規作成ウィザードの **[サブスクリプションの種類]** ページで、 **[サブスクリプションの種類]** オプションに対して **[クライアント]** または **[サーバー]** を選択します。  
  
2.  サブスクリプションの種類として **[サーバー]** を選択した場合は、 **[競合解決の優先度]** オプションの値 (0.00 ～ 99.99) も入力します。  
  
### <a name="to-modify-the-conflict-resolution-priority"></a>競合解決の優先度を変更するには  
  
1.  パブリッシャーの **[サブスクリプションのプロパティ - \<Publisher>:\<PublicationDatabase>]** で、 **[優先度]** オプションの値 (0.00 ～ 99.99) を入力します。  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [Advanced Merge Replication Conflict Detection and Resolution](merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [パブリケーションのサブスクライブ](subscribe-to-publications.md)  
  
  
