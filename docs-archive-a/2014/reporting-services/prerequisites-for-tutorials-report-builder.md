---
title: チュートリアルの前提条件 (レポート ビルダー) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 9b8346a6-f4f4-4ad3-bc98-8f2be342ef2d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b1f037d1a19fdce566a5a22c7e6a3274fb10ed7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631638"
---
# <a name="prerequisites-for-tutorials-report-builder"></a>チュートリアルの前提条件 (レポート ビルダー)
  レポート ビルダー チュートリアルでは、レポート サーバー上またはレポート サーバーと統合されている SharePoint サイト上でレポートを表示および保存できることを前提としています。 すべてのチュートリアルでは、データを取得するために、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]のインスタンスで処理される必要があるリテラル クエリを使用します。  
  
 レポート サーバーやサイト、またはデータ ソースにアクセスできない場合は、オフラインのレポートを作成することによってレポート ビルダーについて学習できます。 「[チュートリアル: オフラインでのクイック グラフ レポートの作成 &#40;レポート ビルダー&#41;](report-builder/tutorial-create-a-quick-chart-report-offline-report-builder.md)」を参照してください。  
  
## <a name="requirements"></a>必要条件  
 レポート ビルダーのチュートリアルを完了するには、次の条件を満たしている必要があります。  
  
-   レポートビルダーにアクセス [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] します。 レポート ビルダーを実行するには、スタンドアロン バージョンまたは ClickOnce バージョンのレポート ビルダーを使用します。ClickOnce バージョンは、レポート マネージャーまたは SharePoint サイトから利用できます。 ClickOnce バージョンでは、最初の手順であるレポートビルダーを開く方法のみが異なります。  
  
     レポートマネージャーを使用するには、レポートマネージャーを開き、[**レポートビルダー**] をクリックします。 既定ではレポートマネージャーの URL は http:// \<*servername*> /レポートです。  
  
     SharePoint サイトを使用する場合は、サイトに移動し、[ドキュメント] タブ、[新しいドキュメント] の順にクリックして、ドロップダウン リストの [レポート ビルダー レポート] をクリックします。 たとえば、http:// \<servername> /sites/mySite/reports. SharePoint 管理者は、各ドキュメント ライブラリのレポート ビルダー レポート機能を有効にする必要があります。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポート サーバー、または [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] レポート サーバーと統合されている SharePoint サイトの URL。 レポート、共有データ ソース、共有データセット、レポート パーツ、およびモデルを保存および表示する権限が必要です。 既定では、レポートサーバーの URL は http:// \<servername> /reportserverです。 既定では、SharePoint サイトの URL は http:// \<sitename> または http:// \<server> /siteです。  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスの名前と任意のデータベースへの読み取り専用アクセスに必要な資格情報。 チュートリアルのデータセット クエリでは、リテラル データを使用します。ただし、各クエリは、レポート データセットに必要なメタデータを返すように、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] インスタンスで処理される必要があります。 たとえば、 `data source=<servername>`という接続文字列では、サーバーしか指定されていません。 この場合は、そのサーバーにアクセスする権限を付与したシステム管理者によって割り当てられた既定のデータベースに対する読み取りアクセス権が必要です。 `data source=<servername>;initial catalog=<database>`という接続文字列のように、データベースを指定することもできます。  
  
-   マップを含むチュートリアルの場合は、Bing マップの背景をサポートするようにレポート サーバーが構成されている必要があります。 詳細については、msdn.microsoft.com のオンラインブックのドキュメントの「[マップレポートのサポートを計画する](plan-for-map-report-support.md)」を参照してください [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) 。  
  
-   チュートリアル「[チュートリアル: 詳細レポートとメインレポートの作成」 &#40;レポートビルダー&#41;](tutorial-creating-drillthrough-and-main-reports-report-builder.md)では、Contoso ビジネスインテリジェンスデモデータセットを使用します。 このデータセットは、ContosoDW データ ウェアハウスと Contoso_Retail オンライン分析処理 (OLAP) データベースで構成されています。 このチュートリアルで作成するレポートは、Contoso Sales キューブからレポート データを取得します。 Contoso_Retail OLAP データベースは、 [Microsoft ダウンロード センター](https://www.microsoft.com/download/details.aspx?id=18279)からダウンロードできます。 ダウンロードする必要があるファイルは、ContosoBIdemoABF.exe だけです。 このファイルに OLAP データベースが含まれています。  
  
     もう一方のファイル (ContosoBIdemoBAK.exe) は、ContosoDW データ ウェアハウスのファイルです。ContosoDW データ ウェアハウスは、このチュートリアルでは使用しません。  
  
     上述の Web サイトには、ContosoRetail.abf バックアップ ファイルを抽出して Contoso_Retail OLAP データベースを復元する手順の説明も含まれています。  
  
     OLAP データベースをインストールする [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへのアクセス権が必要です。  
  
 レポート サーバー管理者は、レポート サーバーに対する必要な権限の許可、 [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] のフォルダーの場所の構成、およびレポート ビルダーの既定のオプションの構成を行う必要があります。 詳細については、「 [Install、Uninstall、およびレポートビルダー Support](install-uninstall-and-report-builder-support.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [チュートリアル &#40;レポートビルダー&#41;](report-builder-tutorials.md)  
  
  
