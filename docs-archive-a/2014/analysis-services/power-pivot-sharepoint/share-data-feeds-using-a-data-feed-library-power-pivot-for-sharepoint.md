---
title: データフィードライブラリを使用したデータフィードの共有 (PowerPivot for SharePoint) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data feeds [Analysis Services with SharePoint]
ms.assetid: 4ec98dec-0cd2-4727-bb79-5bf6f8a865d6
author: minewiskan
ms.author: owend
ms.openlocfilehash: cb24a0ae66cdb0b0623aaa217be778280bdb14ae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641275"
---
# <a name="share-data-feeds-using-a-data-feed-library-powerpivot-for-sharepoint"></a>データフィードライブラリを使用したデータフィードの共有 (PowerPivot for SharePoint)
  データ フィードとは、データを Atom ワイヤ形式で公開するサービスまたはアプリケーションから生成される XML データ ストリームです。 データをアプリケーション間で転送したり、クライアント側のビューアーに転送したりするために使用されることが増えています。 PowerPivot for SharePoint の配置では、データフィードを使用し [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] て、Atom 対応のアプリケーションまたはサービスからのデータをデータソースに設定します。  
  
 Atom 対応アプリケーションの組み合わせを既に使用している場合は、データがアプリケーション間でシームレスに転送されるので、フィードの生成方法と使用方法を理解する必要はありません。 ただし、カスタム ソリューションを使用して Atom フィードをパブリッシュする組織は、インフォメーション ワーカーがフィードを使用できるようにしなければならないことがよくあります。 これを実現する方法の 1 つに、フィードを生成するオンライン ソースへの接続が指定されるデータ サービス ドキュメント (.atomsvc) ファイルを作成して共有する方法があります。 データ フィード ライブラリと呼ばれる特別な用途のライブラリによって、SharePoint Web アプリケーションでのデータ サービス ドキュメントの作成と共有がサポートされます。  
  
 このトピックは、次のセクションで構成されています。  
  
 [必須コンポーネント](#prereq)  
  
 [データ サービス ドキュメントの作成](#createdsdoc)  
  
 [データ サービス ドキュメントのセキュリティ保護](#securedsdoc)  
  
 [データサービスドキュメントの変更](#modifydsdoc)  
  
 [次の手順: データサービスドキュメントの使用](#usedsdoc)  
  
> [!NOTE]  
>  データ フィードは [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] で作成した [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]データ ソースに Web データを追加するために使用されますが、データ サービス ドキュメントの処理は、Atom フィードを読み取ることができる任意のクライアント アプリケーションで実行できます。  
  
##  <a name="prerequisites"></a><a name="prereq"></a> 前提条件  
 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] クエリ処理を SharePoint ファームに追加する PowerPivot for SharePoint の配置が必要です。 データ フィードは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ソリューション パッケージによってサポートされます。  
  
 データ サービス ドキュメントのコンテンツ タイプをサポートする SharePoint ライブラリが必要です。 この場合は既定のデータ フィード ライブラリをお勧めしますが、コンテンツ タイプを任意のライブラリに手動で追加することもできます。 詳細については、「[データフィードライブラリの作成またはカスタマイズ &#40;PowerPivot for SharePoint&#41;](create-or-customize-a-data-feed-library-power-pivot-for-sharepoint.md)」を参照してください。  
  
 Atom 1.0 形式の XML 表形式データを提供するデータ サービスまたはオンライン データ ソースが必要です。  
  
 SharePoint ライブラリでデータ サービス ドキュメントを作成または管理するために、SharePoint サイトに対する投稿権限が必要です。  
  
##  <a name="create-a-data-service-document"></a><a name="createdsdoc"></a>データサービスドキュメントの作成  
 データ サービス ドキュメントとは、フィード形式のデータを提供するオンライン データ ソースまたはアプリケーションからの要求時にデータをストリーミングするために常設されている要求です。 データ サービス ドキュメントの作成時に、Atom 配信形式の XML 表を提供する URL アドレスを指定可能な 1 つ以上のデータ サービスを指すポインターを指定します。  
  
 1 つのドキュメントで複数のデータ フィードを指定できます。 これは、単一のインポート操作で同じサービスまたは異なるサービスからデータ ペイロード セットを取得する場合に便利です。  
  
1.  SharePoint サイトで、データ フィード ライブラリ、またはデータ サービスのコンテンツ タイプを追加および構成した別のドキュメント ライブラリを開きます。 以前に作成したデータ フィード ライブラリを見つけるには、サイド リンク バーで **[すべて表示]** をクリックします。  
  
2.  ページ上部のリボンの [ドキュメント ツール] で **[ドキュメント]** をクリックします。  
  
3.  **[新しいドキュメント]** をクリックし、 **[データ サービス ドキュメント]** をクリックします。  
  
4.  [新しいデータ サービス ドキュメント] ページで、次の情報を入力します。  
  
    1.  データ サービス ドキュメントの名前と説明。 十分に詳しい情報を指定して、ユーザーがフィードを使用するかどうかを判断できるようにします。  
  
    2.  [データ フィード] に、データを Atom 1.0 形式で提供するデータ サービスまたは Web アプリケーションの URL を入力します。  
  
         URL は、行および列の構造化または半構造化されたデータを返すサービスに解決される必要があります。 このサービスは、匿名でデータを返すか、現在のユーザーのセキュリティ資格情報を使用してデータを返します。  
  
         URL は、Windows 認証、基本認証、または匿名アクセスをサポートするサービスに解決される必要があります。 フィードをインポートするユーザーが、使用するスキームを指定します。 既定では統合セキュリティが選択されます。  
  
         データ フィード URL にはパラメーターを含めることができます。 さまざまな種類のデータ サービス テクノロジで、使用するデータを正確に選択できる高度な URL アドレス指定スキームがサポートされています。 たとえば、ADO.NET データ サービスには、基になるデータのエンティティ、アソシエーション、およびナビゲーション パスを指定するための URL パラメーターが用意されています。 複雑な URL をデータ フィードのソースとして指定することで、使用するデータセットを正確に指定できます。  
  
    3.  同じデータ フィードにおいて、クライアント アプリケーションでデータセットを識別することになるテーブル名を入力します。 [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]では、インポートする各データ フィードは、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] データ ソース内の固有のテーブル コントロールに配置されます。 データ フィードの設定時に、インポートされたデータを受け取るテーブルの名前を指定する必要があります。  
  
5.  [別のデータ フィードの追加] をクリックし、前の手順を繰り返して同じサービスまたは異なるサービスからの追加のフィードを指定します。  
  
     各データ サービス ドキュメントは単一の操作として処理されます。 同じ操作で、ドキュメント内のすべてのデータ フィードが非同期に生成されてクライアント アプリケーションに返されます。 このため、同時に使用するデータ フィードの URL テーブルのペアのみを指定します。  
  
     認証方法はデータ サービス ドキュメント レベルで設定されるので、追加の各データ フィードは、同じ認証方法を最初のフィードとしてサポートするサービスまたはアプリケーションから生成される必要があります。 同じデータ サービス ドキュメント内のすべてのフィードが、実行時に同じ方法で認証されます。  
  
6.  ドキュメントを保存します。 データ サービス ドキュメントは、このコンテンツ タイプ用に構成されたコンテンツ ライブラリに物理ファイル (.atomsvc) として格納されます。  
  
 データ サービス ドキュメントを使用するには、 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] で [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)] ブックを開いて、データのインポート ウィザードで **[データ フィードから]** オプションを選択します。 指定画面が表示されたら、ユーザーがデータ サービス ドキュメントの SharePoint URL を指定して、データのインポート操作を開始します。 詳細については、「[データフィードの使用 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)」を参照してください。  
  
##  <a name="secure-a-data-service-document"></a><a name="securedsdoc"></a>データサービスドキュメントのセキュリティ保護  
 データ サービス ドキュメントは、そのドキュメントを格納するライブラリの権限を継承します。 アイテムに対して設定した権限によって、ユーザーがデータ サービス ドキュメントを表示、変更、または削除できるかどうかが決まります。  
  
 データ サービス ドキュメントを PowerPivot クライアント アプリケーションでデータ フィードのインポートとして使用するために必要なのは、ドキュメントに対する表示権限だけです。 インポート ウィザードで URL を解決するには表示権限で十分です。  
  
 データ サービス ドキュメントに対する表示権限は、データ フィードのインポート操作が開始されるときにのみ確認されます。 インポート後は、ドキュメントに対する権限は確認されません。PowerPivot データ ソースに追加されたフィードは、元の接続情報を提供したデータ サービス ドキュメントから切断された静的データとして存在します。  
  
 同様に、後でスケジュール設定するデータ更新操作でもデータ サービス ドキュメントは除外されます。 インポート時に、更新のために各フィードの接続情報が PowerPivot データ ソースにコピーされます。 したがって、ドキュメント自体は更新操作で参照されないので、データ サービス ドキュメントに対する権限はデータ更新では確認されません。  
  
|タスク|SharePoint 権限の要件|  
|----------|----------------------------------------|  
|データ フィードを PowerPivot 対応のブックにインポートする。|ライブラリのデータ サービス ドキュメントに対する表示権限。|  
|PowerPivot クライアント アプリケーションで、以前にフィードを介して取得されたデータを更新する。|該当なし。 PowerPivot クライアント アプリケーションは、埋め込まれた HTTP 接続情報を使用して、フィードを提供するデータ サービスおよびアプリケーションに直接接続します。 PowerPivot クライアント アプリケーションでは、データ サービス ドキュメントは使用されません。|  
|SharePoint ファームで、ユーザー入力を要求せずにデータを定期タスクとして更新する。|該当なし。 PowerPivot サービスは、埋め込まれた HTTP 接続情報を使用して、フィードを提供するデータ サービスおよびアプリケーションに直接接続します。 PowerPivot サービスでは、データ サービス ドキュメントは使用されません。|  
|ライブラリのデータ サービス ドキュメントを削除する。|ライブラリに対する投稿権限。|  
  
##  <a name="modify-a-data-service-document"></a><a name="modifydsdoc"></a> データ サービス ドキュメントの変更  
 データ サービス ドキュメントで個々の URL テーブル エントリを追加、編集、または削除できます。 変更を保存した後は、新しいインポート操作でサービス ドキュメントを選択するユーザーが、指定されたデータ フィードを取得します。  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックが、以前のバージョンのドキュメントを使用していた場合は、この変更の影響を受けません。 これは、データ サービス ドキュメントが最初のインポート操作で一度だけ読み取られるためです。 インポート時に、サービスの URL とテーブル名がブックに内部的にコピーおよび格納されます。 これらの内部値は、その後の更新操作で更新されたデータを取得するために使用されます。  
  
 SharePoint サイトのデータ サービス ドキュメントとインポートされたフィードが含まれる [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックの間に永続的なリンクがないので、データ サービス ドキュメントの一部を変更しても既存の [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブックには影響しません。  
  
> [!IMPORTANT]  
>  データ サービス ドキュメントは一度しか読み取られませんが、実際のデータを提供するデータ サービスには、新しいフィードを取得するために定期的にアクセスできます。 データを更新する方法の詳細については、「 [PowerPivot データ更新](power-pivot-data-refresh.md)」を参照してください。  
  
##  <a name="next-step-use-a-data-service-document"></a><a name="usedsdoc"></a> 次の手順: データ サービス ドキュメントの使用  
 SharePoint ライブラリで作成したデータサービスドキュメントを使用するには、PowerPivot データソースの [**データフィードから**] インポートオプションを使用します。 手順については、「[データフィードの使用 &#40;PowerPivot for SharePoint&#41;](use-data-feeds-power-pivot-for-sharepoint.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [PowerPivot データ フィード](power-pivot-data-feeds.md)  
  
  