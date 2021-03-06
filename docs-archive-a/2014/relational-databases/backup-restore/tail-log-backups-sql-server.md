---
title: ログ末尾のバックアップ (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], tail of log
- transaction log backups [SQL Server], tail-log backups
- NO_TRUNCATE clause
- backups [SQL Server], log backups
- tail-log backups
- backups [SQL Server], tail-log backups
ms.assetid: 313ddaf6-ec54-4a81-a104-7ffa9533ca58
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: cd7c505701a4edb1f66ca516d06179b2eb1a222d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632527"
---
# <a name="tail-log-backups-sql-server"></a>ログ末尾のバックアップ (SQL Server)
  このトピックは、完全復旧モデルまたは一括ログ復旧モデルを使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのバックアップと復元のみに関連しています。  
  
 *ログ末尾のバックアップ* は、まだバックアップされていないすべてのログ レコード ( *ログの末尾*) をキャプチャし、作業内容の消失を防いで、ログ チェーンの完全性を維持します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースをその最新の時点まで復元するには、トランザクション ログの末尾をあらかじめバックアップしておく必要があります。 ログ末尾のバックアップは、データベースの復旧プランの対象になる最後のバックアップとなります。  
  
> [!NOTE]  
>  ログ末尾のバックアップは、すべての復元シナリオで必要となるわけではありません。 復旧ポイントが、それより前のログ バックアップに含まれているのであれば、ログ末尾のバックアップは不要です。 また、データベースを移動するか置き換えて (上書きして) いる場合、ログ末尾のバックアップは不要であり、最新のバックアップ以降の特定の時点に復元する必要もありません。  
  
 
  
##  <a name="scenarios-that-require-a-tail-log-backup"></a><a name="TailLogScenarios"></a> ログ末尾のバックアップが必要となるシナリオ  
 以下に示すシナリオでは、ログ末尾のバックアップをお勧めします。  
  
-   データベースがオンライン状態であり、データベースに対して復元操作を実行する予定がある場合に、ログ末尾のバックアップを最初に行う。 オンラインデータベースでエラーが発生しないようにするには、...[BACKUP](/sql/t-sql/statements/backup-transact-sql)ステートメントの with NORECOVERY オプション [!INCLUDE[tsql](../../includes/tsql-md.md)] 。  
  
-   データベースがオフラインで起動できず、データベースを復元する必要がある場合に、まずログの末尾をバックアップする。 このとき、トランザクションは発生しないので、WITH NORECOVERY の指定は省略できます。  
  
-   データベースが破損したとき、BACKUP ステートメントの WITH CONTINUE_AFTER_ERROR オプションを使用してログ末尾のバックアップを試す。  
  
     破損しているデータベースでログ末尾のバックアップが成功するのは、ログ ファイルが破損しておらず、データベースがログ末尾のバックアップをサポートしている状態であり、一括ログ記録された変更がデータベースに含まれていない場合に限られます。 ログ末尾のバックアップを作成できない場合、最新のログ バックアップの後にコミットされたトランザクションはすべて失われます。  
  
 次の表は、BACKUP NORECOVERY と CONTINUE_AFTER_ERROR オプションをまとめたものです。  
  
|BACKUP LOG オプション|説明|  
|-----------------------|--------------|  
|NORECOVERY|データベースの復元操作を続行する場合は、必ず NORECOVERY を使用します。 NORECOVERY を指定すると、データベースは復元中の状態になります。 これにより、ログ末尾のバックアップの後にデータベースが変化しないことが保障されます。  NO_TRUNCATE オプションまたは COPY_ONLY オプションも指定されていない限り、ログは切り捨てられます。<br /><br /> 重要データベースが破損している場合を除き、NO_TRUNCATE を使用しないことをお勧めします。 ** \* \* \* \* **|  
|CONTINUE_AFTER_ERROR|破損したデータベースの末尾をバックアップする場合に限り、CONTINUE_AFTER_ERROR を使用します。<br /><br /> 注: 破損したデータベースでログの末尾のバックアップを使用すると、通常はログバックアップでキャプチャされたメタデータの一部が使用できなくなる場合があります。 詳細については、後の「[不完全なバックアップ メタデータが含まれたログ末尾のバックアップ](#IncompleteMetadata)」を参照してください。|  
  
##  <a name="tail-log-backups-that-have-incomplete-backup-metadata"></a><a name="IncompleteMetadata"></a>不完全なバックアップメタデータが含まれるログ末尾のバックアップ  
 データベースがオフラインである場合、データベースが破損している場合、またはデータ ファイルが欠落している場合でも、ログ末尾のバックアップではログの末尾がキャプチャされます。 これが原因で、復元情報コマンドや **msdb**のメタデータが不完全になる場合があります。 ただし、メタデータが不完全なだけで、キャプチャされたログは完全であり、使用できます。  
  
 ログ末尾のバックアップに不完全なメタデータが含まれている場合は、 [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) テーブルの **has_incomplete_metadata** が **1**に設定されます。 また、 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)の出力で **HasIncompleteMetadata** が **1**に設定されます。  
  
 ログ末尾のバックアップのメタデータが不完全な場合、ログ末尾のバックアップ時に、ファイル グループに関する情報の大部分が [backupfilegroup](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) テーブルから欠落します。 **backupfilegroup** テーブルのほとんどの列は NULL になり、意味を持つ列は次の列のみです。  
  
-   **backup_set_id**  
  
-   **filegroup_id**  
  
-   **type**  
  
-   **type_desc**  
  
-   **is_readonly**  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
 ログ末尾のバックアップを作成するには、「[データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)」をご覧ください。  
  
 トランザクション ログ バックアップを復元するには、「[トランザクション ログ バックアップの復元 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [SQL Server データベースのバックアップと復元](back-up-and-restore-of-sql-server-databases.md)   
 [コピーのみのバックアップ &#40;SQL Server&#41;](copy-only-backups-sql-server.md)   
 [トランザクション ログのバックアップ &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)   
 [トランザクション ログ バックアップの適用 &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md)  
  
  
