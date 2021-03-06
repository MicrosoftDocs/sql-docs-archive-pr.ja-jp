---
title: マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server replication]
- sp_mergemetadataretentioncleanup
ms.assetid: 9b88baea-b7c6-4e5d-88f9-93d6a0ff0368
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5a2306db72fd3f0098e18ff058796a5498eafcac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736259"
---
# <a name="clean-up-merge-metadata-replication-transact-sql-programming"></a>マージ メタデータのクリーンアップ (レプリケーション Transact-SQL プログラミング)
  マージ レプリケーションのメタデータは、パブリケーションの保有期間設定に基づき、マージ エージェントによって定期的にクリーンアップされます。 クリーンアップは、パブリッシャーおよびサブスクライバーの [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、 [MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)、 [MSmerge_past_partition_mappings](/sql/relational-databases/system-tables/msmerge-past-partition-mappings-transact-sql)、 [MSmerge_current_partition_mappings](/sql/relational-databases/system-tables/msmerge-current-partition-mappings) の各システム テーブルで実行されます。 これらのテーブルに格納されたデータは、レプリケーションのストアド プロシージャを使って、プログラムからクリーンアップすることもできます。  
  
### <a name="to-manually-clean-up-merge-metadata"></a>マージ メタデータを手動でクリーンアップするには  
  
1.  パブリッシャーのパブリケーション データベースで [sp_mergemetadataretentioncleanup](/sql/relational-databases/system-stored-procedures/sp-mergemetadataretentioncleanup-transact-sql)を実行します。  
  
2.  Optional手順 1. で削除した行の数は、 [MSmerge_genhistory](/sql/relational-databases/system-tables/msmerge-genhistory-transact-sql)、 [MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql)、および[MSmerge_tombstone](/sql/relational-databases/system-tables/msmerge-tombstone-transact-sql)の各システムテーブルから、それぞれ、、およびの各出力パラメーターで返され **@num_genhistory_rows** **@num_contents_rows** **@num_tombstone_rows** ます。  
  
3.  サブスクライバーで手順 1. と手順 2. を繰り返し、サブスクリプション データベースのメタデータをクリーンアップします。  
  
## <a name="see-also"></a>参照  
 [サブスクリプションの有効期限と非アクティブ化](../subscription-expiration-and-deactivation.md)  
  
  
