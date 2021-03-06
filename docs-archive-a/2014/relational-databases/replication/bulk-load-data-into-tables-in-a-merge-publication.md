---
title: マージパブリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- bulk load [SQL Server replication]
- merge replication bulk loading [SQL Server replication]
- sp_addtabletocontents
ms.assetid: 16e6498a-b449-4051-aec4-ea814a2ad993
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f669a1f7132aa0f588fd89fb9747a7dc9017fcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741857"
---
# <a name="bulk-load-data-into-tables-in-a-merge-publication-replication-transact-sql-programming"></a>マージ レプリケーション内のテーブルにデータを一括読み込みする (レプリケーション Transact-SQL プログラミング)
  [bcp ユーティリティ](../../tools/bcp-utility.md)または [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) コマンドを使用してテーブルにデータを読み込むと、既定では、[MSmerge_contents](/sql/relational-databases/system-tables/msmerge-contents-transact-sql) システム テーブル内の追跡データを維持するマージ レプリケーション トリガーが起動されなくなります。 データが読み込まれたときにマージ レプリケーション トリガーを強制的に起動するか、一括コピー操作の後にレプリケーション ストアド プロシージャを使用して、生成されたレプリケーション メタデータをプログラムによって挿入できます。  
  
### <a name="to-bulk-load-data-into-tables-published-by-merge-replication-using-the-bcp-utility"></a>マージ レプリケーションによってパブリッシュされたテーブルに bcp ユーティリティを使用してデータを一括読み込みするには  
  
1.  マージ レプリケーションを使用してパブリッシュされたテーブルにデータを挿入するには、パブリッシャーまたはサブスクライバーで [bcp Utility](../../tools/bcp-utility.md) または [BULK INSERT](/sql/t-sql/statements/bulk-insert-transact-sql) を実行します。  
  
2.  挿入されたデータ用のレプリケーション メタデータが生成されようにするには、次のいずれかの方法を使用します。  
  
    -   FIRE_TRIGGERS オプションを使用して一括コピーを実行する。  
  
    -   データの挿入先のデータベースで、[sp_addtabletocontents &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addtabletocontents-transact-sql) を実行する。 データの挿入先のテーブル名を指定し **@table_name** ます。  
  
  
