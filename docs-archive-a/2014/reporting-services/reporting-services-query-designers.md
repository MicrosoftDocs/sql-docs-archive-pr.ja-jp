---
title: Reporting Services クエリデザイナー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- query designers [Reporting Services]
ms.assetid: 07efd3f1-804f-45f7-b62a-3e727a3d9835
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4febd0b0e0bf028d16aa3ef13ce4294feb930072
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719461"
---
# <a name="reporting-services-query-designers"></a>Reporting Services クエリ デザイナー
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] にはグラフィカルおよびテキスト ベースのクエリ デザイナーが用意されており、レポートのデータ ソースの種類ごとにクエリを作成することができます。  
  
 一部のデータ ソースでは、クエリを対話形式で作成できるグラフィカル デザイナーがサポートされています。 その他のデータ ソースでは、テキスト ベースのクエリ デザイナーを使用します。 グラフィカル クエリ デザイナーでは、データ ソースの基になるデータを表すメタデータ アイテムをクエリ デザイン画面にドラッグできます。 テキスト ベースのクエリ デザイナーでは、コマンド テキストをクエリ ペインに入力できます。 グラフィカル クエリ デザイナーからテキスト ベースのクエリ デザイナーに変更するには、ツール バーのテキスト ベースのクエリ デザイナー アイコンをクリックします。  
  
 レポートで使用できるデータ ソースの種類は、クライアントまたはレポート サーバーにインストールされている [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] データ拡張機能によって決まります。 詳細については、「 [Rsreportdesigner 構成ファイル](report-server/rsreportdesigner-configuration-file.md)」と「 [rsreportserver 構成ファイル](report-server/rsreportserver-config-configuration-file.md)」を参照してください。  
  
 データ処理拡張機能および関連するクエリ デザイナーは、次のようにデータ ソースのサポートにおいて異なる場合があります。  
  
-   **クエリ デザイナーの種類。** たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースでは、グラフィカルとテキスト ベースの両方のクエリ デザイナーがサポートされます。  
  
-   **クエリ言語のバリエーション。** たとえば、 [!INCLUDE[tsql](../includes/tsql-md.md)] などのクエリ言語は、データ ソースの種類によって構文が異なることがあります。 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[tsql](../includes/tsql-md.md)] 言語および Oracle SQL 言語には、クエリコマンドの構文のバリエーションがいくつかあります。  
  
-   **データベース オブジェクト名のスキーマの部分に対するサポート。** データ ソースでデータベース オブジェクト識別子の一部としてスキーマが使用されている場合、既定のスキーマを使用しない名前については、クエリにスキーマ名を指定する必要があります。 たとえば、`SELECT FirstName, LastName FROM [Person].[Person]` のように指定します。  
  
-   **クエリ パラメーターのサポート。** パラメーターのサポートは、データ プロバイダーによって異なります。 一部のデータ プロバイダーでは、 `SELECT Col1, Col2 FROM Table WHERE <parameter identifier><parameter name> = <value>`のような名前付きパラメーターがサポートされます。 また別のデータ プロバイダーでは、 `SELECT Col1, Col2 FROM Table WHERE <column name> = ?`のような無名パラメーターがサポートされます。 パラメーター識別子はデータ プロバイダーごとに異なります。たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では "アット" (@) 記号を使用し、Oracle ではコロン (:) を使用します。 パラメーターがサポートされないデータ プロバイダーもあります。  
  
-   **クエリをインポートする機能。** たとえば、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ ソースの場合は、レポート定義ファイル (.rdl) または .sql ファイルからクエリをインポートできます。  
  
## <a name="query-designers"></a>クエリ デザイナー  
 次のトピックでは、各クエリ デザイナーのユーザー インターフェイスについて説明しています。  
  
-   [Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス](report-data/analysis-services-mdx-query-designer-user-interface.md)  
  
-   [Analysis Services の DMX クエリ デザイナーのユーザー インターフェイス](report-data/analysis-services-dmx-query-designer-user-interface.md)  
  
-   [グラフィカル クエリ デザイナーのユーザー インターフェイス](report-data/graphical-query-designer-user-interface.md)  
  
-   [リレーショナル クエリ デザイナーのユーザー インターフェイス](../../2014/reporting-services/relational-query-designer-user-interface.md)  
  
-   [Hyperion Essbase クエリ デザイナーのユーザー インターフェイス](report-data/hyperion-essbase-query-designer-user-interface.md)  
  
-   [レポート モデル クエリ デザイナーのユーザー インターフェイス](report-data/report-model-query-designer-user-interface.md)  
  
-   [SAP NetWeaver BI Query Designer のユーザー インターフェイス](report-data/sap-netweaver-bi-query-designer-user-interface.md)  
  
-   [SharePoint リストのクエリ デザイナー](../../2014/reporting-services/sharepoint-list-query-designer.md)  
  
-   [テキストベースのクエリ デザイナーのユーザー インターフェイス](../../2014/reporting-services/text-based-query-designer-user-interface.md)  
  
## <a name="see-also"></a>参照  
 [Reporting Services &#40;SSRS&#41;でサポートされるデータソース](create-deploy-and-manage-mobile-and-paginated-reports.md)   
 [SSRS&#41;&#40;外部データソースからデータを追加する](report-data/add-data-from-external-data-sources-ssrs.md)   
 [データ処理拡張機能と .NET Framework データプロバイダー &#40;SSRS&#41;](report-data/data-processing-extensions-and-net-framework-data-providers-ssrs.md)   
 [拡張機能 (SSRS)](extensions-ssrs.md)  
  
  
