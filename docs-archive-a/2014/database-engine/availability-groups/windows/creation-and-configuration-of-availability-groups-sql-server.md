---
title: 可用性グループの作成と構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc33da393527c19985f5e7b214ba4bc02dc2f3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743445"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a>可用性グループの作成と構成 (SQL Server)
  このセクションの各トピックでは、単一の WSFC (Windows Server フェールオーバー クラスタリング) フェールオーバー クラスターを構成する各 WSFC ノード上の [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] のインスタンスに対し、 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] の実装を配置する方法について説明します。  
  
 可用性グループを初めて作成する前に、次のトピックの情報をよく理解しておくことを強くお勧めします。  
  
 [AlwaysOn 可用性グループ &#40;SQL Server の前提条件、制限事項、推奨事項&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
 このトピックでは、コンピューター、WSFC ノード、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]インスタンス、可用性グループ、可用性レプリカ、および可用性データベースに関して、それぞれの前提条件、制限、および推奨事項を取り上げます。 このトピックでは、セキュリティに関する考慮事項も取り上げています。  
  
 [はじめに AlwaysOn 可用性グループ &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
 サーバー インスタンスの構成、可用性グループの構成、クライアント接続に必要な可用性グループの構成、可用性グループの管理、可用性グループの監視について、それぞれ手順を紹介します。  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> 関連タスク  
 **のサーバーインスタンスを構成するには[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**  
  
-   [AlwaysOn 可用性グループの有効化と無効化 &#40;SQL Server&#41;](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [AlwaysOn 可用性グループ &#40;SQL Server PowerShell のデータベースミラーリングエンドポイントを作成&#41;](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [Windows 認証でのデータベース ミラーリング エンドポイントの作成 &#40;Transact-SQL&#41;](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [データベース ミラーリング エンドポイントで発信接続に証明書を使用できるようにする &#40;Transact-SQL&#41;](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 **AlwaysOn 可用性グループの構成を開始するには**  
  
-   [はじめに AlwaysOn 可用性グループ &#40;SQL Server&#41;](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 **新しい可用性グループを作成して構成するには**  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)  
  
-   [可用性グループの作成 &#40;SQL Server PowerShell&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [自動フェールオーバーの条件を制御する柔軟なフェールオーバー ポリシーの構成 (AlwaysOn 可用性グループ)](configure-flexible-automatic-failover-policy.md)  
  
-   [可用性レプリカでのバックアップの構成 &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [可用性レプリカでの読み取り専用アクセスの構成 &#40;SQL Server&#41;](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [可用性グループの読み取り専用ルーティングの構成 &#40;SQL Server&#41;](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [AlwaysOn セカンダリデータベース &#40;SQL Server でのデータ移動の開始&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [可用性グループのデータベースのためのログインとジョブの管理 &#40;SQL Server&#41;](../../logins-and-jobs-for-availability-group-databases.md)  
  
 **トラブルシューティングを行うには**  
  
-   [AlwaysOn 可用性グループ構成 (SQL Server) の削除に関するトラブルシューティング](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [失敗したファイルの追加操作のトラブルシューティング &#40;AlwaysOn 可用性グループ&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> 関連コンテンツ  
  
-   **ブログ:**  
  
     [AlwaysON - HADRON 学習シリーズ:HADRON 対応データベースでのワーカー プールの使用](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [SQL Server AlwaysOn チームのブログ:SQL Server AlwaysOn チームのオフィシャル ブログ](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [CSS SQL Server エンジニアのブログ](https://blogs.msdn.com/b/psssql/)  
  
-   **ビデオ:**  
  
     [Microsoft SQL Server コード ネーム "Denali" AlwaysOn シリーズ パート 1: 次世代の高可用性ソリューションの概要](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [Microsoft SQL Server コードネーム "Denali" AlwaysOn シリーズ パート 2: AlwaysOn を使用したミッション クリティカルな高可用性ソリューションの構築](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **ホワイト ペーパー:**  
  
     [高可用性と災害復旧のための Microsoft SQL Server AlwaysOn ソリューション ガイド](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [SQL Server 2012 に関する Microsoft ホワイト ペーパー](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [SQL Server ユーザー諮問チームのホワイト ペーパー](http://sqlcat.com/)  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループ &#40;SQL Server の管理&#41;](administration-of-an-availability-group-sql-server.md)   
 [AlwaysOn 可用性グループ (SQL Server) での運用上の問題のための AlwaysOn ポリシー](always-on-policies-for-operational-issues-always-on-availability.md)   
 [可用性グループの監視 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)   
 [AlwaysOn 可用性グループの相互運用性 (SQL Server)](always-on-availability-groups-interoperability-sql-server.md)  
  
