---
title: SharePoint と2008および 2008 R2 レポートサーバーの統合 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d9f51c37-b071-45d0-baec-f82fa6db366f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0b12429a520a674f4bc3ec7626bb3885fc33c814
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712698"
---
# <a name="sharepoint-integration-with-2008-and-2008-r2--report-servers"></a>2008 および 2008 R2 レポート サーバーとの SharePoint 統合
  [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] リリースの [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] では、新しいアーキテクチャが導入され、SharePoint モードが SharePoint 共有サービスに基づくようになりました。 新しい機能の管理は、SharePoint サーバーの全体管理の [**サービス**と**マネージャーサービスアプリケーション**の管理] ページで行います。 Sharepoint [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 統合の以前のアーキテクチャは、sharepoint 2010 製品用のアドインで引き続きサポートされている [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ため、sharepoint 2010 を以前のバージョンのレポートサーバーと統合できます。  
  
 古いアーキテクチャの管理に使用する SharePoint サーバーの全体管理ページへは、次の方法でアクセスできます。  
  
1.  SharePoint サーバーの全体管理で、[**アプリケーションの全般設定**] をクリックします。  
  
2.  グループ**SQL Server Reporting Services (2008 および 2008 R2)** には、以前のアーキテクチャのリンクと管理ページが含まれています。  
  
## <a name="server-integration-architecture"></a>サーバー統合のアーキテクチャ  
 レポート サーバーを SharePoint の製品のインスタンスと統合すると、アイテムとプロパティは SharePoint コンテンツ データベースに格納されます。 これによって、コンテンツの格納、セキュリティ保護、アクセスの方法を決めるサーバー テクノロジどうしをより深いレベルで統合できます。  
  
 SharePoint コンテンツ データベースにレポートのアイテムとプロパティを格納すると、SharePoint ライブラリでレポート サーバー コンテンツの種類を閲覧したり、SharePoint サイトでホストされている他のビジネス ドキュメントへのアクセスを制御する同じ権限レベルや認証プロバイダーを使ってアイテムを保護することができます。また、コラボレーション機能やドキュメント管理機能を使って変更レポートのチェックイン/チェックアウトを行ったり、警告を使ってアイテムの変更を通知することができます。さらに、アプリケーション内のページやサイトでレポート ビューアー Web パーツを組み込んだりカスタマイズすることもできます。 SharePoint サイト内で十分な権限を持っている場合は、共有データ ソースからレポート モデルを生成し、レポート ビルダーを使用してレポートを作成することもできます。  
  
 レポート サーバーでは引き続き、すべてのデータ処理、表示、配信が行われます。 また、スナップショットやレポート履歴に関連するレポート処理のスケジュール機能もすべてサポートされます。 SharePoint サイトからレポートを開くと、レポート サーバー エンドポイントからレポート サーバーへの接続が行われ、セッションが作成されます。次にレポート処理のための準備が行われ、データが取得された後、レポートがレポート レイアウトにマージされ、レポート ビューアー Web パーツで表示されます。 レポートが開かれたら、レポートをさまざまなアプリケーション形式にエクスポートしたり、ドリルダウンや関連レポートへのクリックスルー機能を使ってデータを対話的に操作することができます。 エクスポートとレポートの対話操作はレポート サーバーで処理されます。  
  
 レポート サーバーでは、SharePoint との間で操作とデータが同期され、処理対象ファイルの情報が追跡されます。 レポート サーバー アイテムのプロパティまたは設定を変更すると、その変更内容は SharePoint データベースに格納された後、レポート サーバーの内部記憶域であるレポート サーバー データベースにコピーされます。  
  
## <a name="related-content"></a>関連コンテンツ  
 [SharePoint でのレポート サーバーと Power View の統合機能のアクティブ化](activate-the-report-server-and-power-view-integration-features-in-sharepoint.md)  
 以前のリリースのレポート サーバーとの統合に必要なレポート サーバー機能をアクティブ化する方法について説明します。  
  
  
