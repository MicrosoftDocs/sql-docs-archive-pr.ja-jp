---
title: SharePoint サーバーに Analysis Services OLE DB Provider をインストールする |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 2c62daf9-1f2d-4508-a497-af62360ee859
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 371d344a451e7702a525e0cb6afa3421b6598cac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643126"
---
# <a name="install-the-analysis-services-ole-db-provider-on-sharepoint-servers"></a>SharePoint サーバーへの Analysis Services OLE DB プロバイダーのインストール
  Microsoft OLE DB Provider for Analysis Services (MSOLAP) は、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データを操作するためにクライアント アプリケーションで使用されるインターフェイスです。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] を含んだ SharePoint 環境では、このプロバイダーによって [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データに対する接続要求が処理されます。  
  
 データ プロバイダーは [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストール パッケージ (spPowerPivot.msi) に含まれていますが、手動でインストールすることが必要な場合があります。 SharePoint サーバーにクライアント ライブラリまたはデータ プロバイダーを手動でインストールしなければならない理由が 2 つあります。  
  
-   **下位互換性を有効に**します。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] のブックは、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの Analysis Services OLE DB プロバイダーを接続文字列に指定します。 したがって、要求を正常に終了させるには、このプロバイダー バージョンがコンピューターに存在する必要があります。  
  
-   **専用の Excel Services インスタンスでデータアクセスを有効に**します。 SharePoint ファーム内の [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] がインストールされていないサーバー上に Excel Services が存在する場合は、[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] インストール パッケージを使用して、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] バージョンのプロバイダーおよびその他のクライアント接続コンポーネントをインストールしてください。  
  
    > [!NOTE]  
    >  これらのシナリオは、共存することができます。 [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インスタンスを使用せずに Excel Services を実行するアプリケーション サーバーを含むファーム上で複数のブック バージョンをホストするには、各 Excel Services コンピューターに古いバージョンと新しいバージョンのデータ プロバイダーをインストールする必要があります。  
  
  
##  <a name="versions-of-the-ole-db-provider-supporting-powerpivot-data-access"></a><a name="bkmk_vers"></a>PowerPivot データアクセスをサポートする OLE DB プロバイダーのバージョン  
 SharePoint ファームには、PowerPivot データ アクセスをサポートしていない旧バージョンを含め、複数のバージョンの Analysis Services OLE DB プロバイダーが含まれていることがあります。  
  
 既定では、SharePoint 2010 により [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] バージョンのプロバイダーがインストールされます。 このバージョンは、MSOLAP.4 ([!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 用に使用されるのと同じバージョン番号) として認識されますが、PowerPivot データ アクセス用には機能しません。 正常に接続するには、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンのプロバイダーが必要です。  
  
 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] バージョン以降の OLE DB プロバイダーは、[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ構造に対するトランスポートおよび接続をサポートしています。 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックでは、このプロバイダーの新しいバージョンを使用して、ファーム内の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] サーバーからクエリ処理を要求します。 更新後のバージョンを入手するには、SQL Server 機能パックのページからダウンロードしてインストールします。  
  
 次の表に、有効なバージョンを示します。  
  
|製品バージョン|ファイル バージョン|有効な対象データ|  
|---------------------|------------------|----------------|  
|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]|ファイル システム内の MSOLAP100.dll<br /><br /> Excel 接続文字列内の MSOLAP.4<br /><br /> ファイル バージョン詳細の 10.50.1600 以降|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの PowerPivot for Excel を使用して作成されたデータ モデルに使用します。|  
|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]|ファイル システム内の MSOLAP110.dll<br /><br /> Excel 接続文字列内の MSOLAP.5<br /><br /> ファイル バージョン詳細の 11.0.0000 以降|[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] バージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel を使用して作成されたデータ モデルに使用します。|  
|[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]|ファイル システム内の MSOLAP120.dll<br /><br /> ファイル バージョン詳細の 12.0.20000 以降|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] モデル以外のデータ モデルに使用します。|  
  
  
##  <a name="why-you-need-to-install-the-ole-db-provider"></a><a name="bkmk_why"></a>OLE DB プロバイダーをインストールする必要がある理由  
 ファーム内のサーバーに OLE DB プロバイダーを手動でインストールしなければならないケースとしては、2 つのシナリオが挙げられます。  
  
 **最も一般的なシナリオは、** [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ファーム内のドキュメントライブラリに保存されている古いバージョンと新しいバージョンのブックがある場合です。 組織内のアナリストがバージョンの for Excel を使用していて、 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] それらのブックをインストールに保存している場合 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 、古いブックは機能しません。 この接続文字列は、プロバイダーの古いバージョンを参照します。これは、インストールしない限り、サーバー上には存在しません。 両方のバージョンをインストールすると、古いバージョンと新しいバージョンの [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] for Excel で作成された PowerPivot ブックに対してデータ アクセスが可能になります。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] のセットアップでは [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンのプロバイダーはインストールされないため、以前のバージョンのブックを使用している場合には、これを手動でインストールする必要があります。  
  
 **2 つ目のシナリオ**は、Excel Services を実行するサーバーが SharePoint ファーム内にあり、ではない場合です [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] 。 このような場合には、Excel Services を実行しているアプリケーション サーバーを、新しいバージョンのプロバイダーに手動で更新する必要があります。 これは、PowerPivot for SharePoint インスタンスに接続するために必要です。 Excel Services で以前のバージョンのプロバイダーを使用している場合は、接続要求が失敗します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をサポートするために必要なすべてのコンポーネントが確実にインストールされるように、[!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] セットアップまたは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] インストール パッケージ (spPowerPivot.msi) を使用してプロバイダーをインストールする必要があることに注意してください。  
  
  
##  <a name="install-the-sql-server-2012-ole-db-provider-on-an-excel-services-server-by-using-sql-server-setup"></a><a name="bkmk_sql11"></a>SQL Server セットアップを使用して Excel Services サーバーに SQL Server 2012 OLE DB プロバイダーをインストールする  
 OLE DB プロバイダーおよび他のクライアント接続コンポーネントがまだインストールされていない SharePoint サーバー (同じハードウェア上に PowerPivot for SharePoint がない状態で Excel Services を実行しているアプリケーション サーバーなど) に OLE DB プロバイダーおよび他のクライアント接続コンポーネントを追加するには、次の説明に従います。  
  
 次の手順を使用して、現在の Analysis Services OLE DB プロバイダーをインストールし、グローバルアセンブリに**Microsoft.AnalysisServices.Xmla.dll**を追加します。  
  
#### <a name="run-sql-server-setup-and-install-the-client-connectivity-tools"></a>SQL Server セットアップの実行とクライアント接続ツールのインストール  
  
1.  Excel Services をホストするアプリケーション サーバー上で、SQL Server セットアップを実行します。  
  
2.  [インストール] ページで、[**新規 SQL Server スタンドアロンインストールを選択するか、既存のインストールに機能を追加**します。  
  
3.  [インストールの種類] ページで、[ **SQL Server 2012 の新規インストールを実行する**] を選択します。  
  
4.  [セットアップロール] ページで、[ **SQL Server 機能のインストール**] を選択します。  
  
5.  [**機能の選択**] ページで、[**クライアントツール接続**] をクリックします。 このオプションを選択すると、がインストールされ**Microsoft.AnalysisServices.Xmla.dll**  
  
     それ以外の機能は選択しないでください。  
  
6.  [**次**へ] をクリックしてウィザードを終了し、[**インストール**] をクリックしてセットアップを実行します。  
  
7.  Excel Services を実行しているが PowerPivot for SharePoint はインストールされていないサーバーが他にある場合は、前の手順を繰り返します。  
  
#### <a name="verify-msolap5-is-a-trusted-provider"></a>MSOLAP.5 が信頼できるプロバイダーであるかどうかの確認  
  
1.  サーバーの全体管理で、 **[アプリケーション構成の管理]** をクリックし、Excel Services サービス アプリケーションをクリックします。  
  
2.  **[信頼できるデータ プロバイダー]** をクリックします。  
  
3.  MSOLAP.5 が一覧に表示されていることを確認します。 PowerPivot for SharePoint の構成方法によっては、MSOLAP.5 が既に信頼されている場合があります。 PowerPivot 構成ツールを使用したにもかかわらず、このアクションがタスクの一覧から除外された場合、MSOLAP.5 は Excel Services によって信頼されないため、手動で追加する必要があります。  
  
4.  MSOLAP が一覧に表示されない場合は、[**信頼された Data Provider の追加**] をクリックします。  
  
5.  [プロバイダー ID] に、「`MSOLAP.5`」と入力します。  
  
6.  [プロバイダーの種類] では、OLE DB が選択されていることを確認します。  
  
7.  [プロバイダーの説明] に、「 **Microsoft OLE DB プロバイダー (OLAP Services 11.0 用)**」と入力します。  
  
#### <a name="verify-installation"></a>インストールの確認  
  
1.  Program files\Microsoft Analysis Services\AS OLEDB\110 に移動します。  
  
2.  msolap110.dll を右クリックし、 **[プロパティ]** をクリックします。  
  
3.  **[詳細]** をクリックします。  
  
4.  ファイルのバージョン情報が表示されます。 バージョンには 11.00. が含まれている必要が \<buildnumber> あります。  
  
5.  Windows\assembly フォルダーで、Microsoft.AnalysisServices.Xmla.dll、バージョン 11.0.0.0 が表示されることを確認します。  
  
  
##  <a name="use-the-powerpivot-for-sharepoint-installation-package-sppowerpivotmsi-to-install-the-sql-server-2012-ole-db-provider"></a><a name="bkmk_install2012_from_sppowerpivot_msi"></a>PowerPivot for SharePoint インストールパッケージ (spPowerPivot.msi) を使用して SQL Server 2012 OLE DB プロバイダーをインストールする  
 [!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] インストールパッケージ **(spPowerPivot.msi)** を使用して、および Excel Services サーバーに OLE DB プロバイダーをインストールします。  
  
#### <a name="download-the-msolap5-provider-from-the-sssql11sp1-feature-pack"></a>[!INCLUDE[ssSQL11SP1](../../includes/sssql11sp1-md.md)] Feature Pack から MSOLAP.5 プロバイダーをダウンロードします。  
  
1.  [Microsoft® SQL Server® 2012 SP1 Feature Pack](https://www.microsoft.com/download/details.aspx?id=35580)を参照してください。  
  
2.  [**インストール手順**] をクリックします。  
  
3.  「Microsoft Analysis Services OLE DB Provider for Microsoft SQL Server 2012 SP1」を参照してください。 ファイルをダウンロードし、インストールを開始します。  
  
4.  [**機能の選択**] ページで、[ **SQL Server の Analysis Services OLE DB Provider**を選択します。 他のコンポーネントの選択を解除して、インストールを完了します。 spPowerPivot.msi の詳細については、「 [SharePoint 2013&#41;&#40;PowerPivot for SharePoint アドインをインストールまたはアンインストールする](https://docs.microsoft.com/analysis-services/instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013)」を参照してください。  
  
5.  MSOLAP.5 を信頼できるプロバイダーとして SharePoint Excel Services に登録します。 詳細については、「 [Excel Services で信頼できるデータ プロバイダーとして MSOLAP.5 を追加](https://technet.microsoft.com/library/hh758436.aspx)」を参照してください。  
  
  
##  <a name="install-the-sql-server-2008-r2-ole-db-provider-to-host-earlier-version-workbooks"></a><a name="bkmk_kj"></a>以前のバージョンのブックをホストするために SQL Server 2008 R2 OLE DB プロバイダーをインストールする  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンの MSOLAP.4 プロバイダーをインストールして、Microsoft.AnalysisServices.ChannelTransport.dll ファイルを登録するには、次の手順に従います。 ChannelTransport は Analysis Services OLE DB プロバイダーのサブコンポーネントです。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] バージョンのプロバイダーは、ChannelTransport を使用して接続を行うときにレジストリを読み取ります。 このファイルの登録は、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] サーバー上の [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] プロバイダーによって処理される接続にのみ必要なインストール後の手順です。  
  
#### <a name="step-1-download-and-install-the-client-library"></a>手順 1: クライアント ライブラリのダウンロードとインストール  
  
1.  [ [SQL Server 2008 R2 Feature Pack] ページ](https://www.microsoft.com/download/details.aspx?id=44272)で Microsoft Analysis Services OLE DB Provider for Microsoft SQL Server 2008 r2 を見つけます。  
  
2.  `SQLServer2008_ASOLEDB10.msi` インストール プログラムの x64 パッケージをダウンロードします。 ファイル名には SQLServer2008 が含まれていますが、これは SQL Server 2008 R2 バージョンのプロバイダーに対応する適切なファイルです。  
  
3.  [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] がインストールされているコンピューターで、.msi を実行してライブラリをインストールします。  
  
4.  Excel Services を実行しているが [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] はインストールされていないサーバーが他にファーム内にある場合は、前の手順を繰り返して 2008 R2 バージョンのプロバイダーを Excel Services コンピューターにインストールします。  
  
#### <a name="step-2-register-the-microsoftanalysisserviceschanneltransportdll-file"></a>手順 2: Microsoft.AnalysisServices.ChannelTransport.dll ファイルの登録  
  
1.  regasm.exe ユーティリティを使用してファイルを登録します。 以前に regasm.exe を実行していない場合は、その親フォルダーの C:\Windows\Microsoft.NET\Framework64\v4.0.30319 \\ をシステムの path 変数に追加します。  
  
2.  管理者権限を使用してコマンド プロンプトを開きます。  
  
3.  C:\Windows\assembly\GAC_MSIL\Microsoft.AnalysisServices.ChannelTransport\10.0.0.0__89845dcd8080cc91 フォルダーに移動します。  
  
4.  次のコマンドを入力します。`regasm microsoft.analysisservices.channeltransport.dll`  
  
5.  2008 R2 バージョンのプロバイダーを手動でインストールしたすべてのコンピューターについて前の手順を繰り返します。  
  
#### <a name="verify-installation"></a>インストールの確認  
  
1.  これで、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] のブックのスライスまたはフィルター処理を行うことができるようになります。 エラーが発生した場合は、64 ビット版の regasm.exe を使用してファイルを登録したことを確認します。  
  
2.  さらに、ファイルのバージョンを確認することができます。  
  
     `C:\Program files\Microsoft Analysis Services\AS OLEDB\10` にアクセスします。 **msolap100.dll**を右クリックし、[**プロパティ**] を選択します。 **[詳細]** をクリックします。  
  
     ファイルのバージョン情報が表示されます。 バージョンには 10.50. が含まれている必要が \<buildnumber> あります。  
  
  
## <a name="see-also"></a>参照  
 [PowerPivot for SharePoint 2010 のインストール](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
  
  
