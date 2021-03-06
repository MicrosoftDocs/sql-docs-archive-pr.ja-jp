---
title: サポートされるデータソース (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d6c2b1b3-91fc-4175-af25-509946dc7f24
author: minewiskan
ms.author: owend
ms.openlocfilehash: d451a929d392c32506aef8598abe68ad07d27e65
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643487"
---
# <a name="data-sources-supported-ssas-tabular"></a>サポートされているデータ ソース (SSAS テーブル)
  このトピックでは、テーブル モデルで使用できるデータ ソースの種類について説明します。  
  
 この記事は、次のセクションで構成されています。  
  
-   [サポートされるデータ ソース](#bkmk_supported_ds)  
  
-   [サポートされていないソース](#bkmk_unsupported_ds)  
  
-   [データソースの選択に関するヒント](#bkmk_tips)  
  
##  <a name="supported-data-sources"></a><a name="bkmk_supported_ds"></a>サポートされるデータソース  
 次の表のデータ ソースからデータをインポートできます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]をインストールする際のセットアップで、各データ ソースに対して挙げられているプロバイダーはインストールされません。 プロバイダーは、他のアプリケーションと共にコンピューターに既にインストールされている場合もあれば、プロバイダーをダウンロードしてインストールしなくてはならない場合もあります。  
  
|||||  
|-|-|-|-|  
|source|バージョン|ファイルの種類|プロバイダー <sup>1</sup>|  
|Access データベース|Microsoft Access 2003、2007、2010。|.accdb または .mdb|ACE 14 OLE DB プロバイダー|  
|SQL Server リレーショナル データベース|Microsoft SQL Server2005、2008、2008 R2、SQL Server 2012、Microsoft SQL Azure データベース<sup>2</sup>|(該当なし)|OLE DB Provider for SQL Server<br /><br /> SQL Server Native Client OLE DB プロバイダー<br /><br /> SQL Server Native 10.0 Client OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for SQL Client|  
|SQL Server 並列データウェアハウス (PDW) <sup>3</sup>|2008 R2|(該当なし)|OLE DB provider for SQL Server PDW|  
|Oracle リレーショナル データベース|Oracle 9i、10g、11g|(該当なし)|Oracle OLE DB プロバイダー<br /><br /> .NET Framework Data Provider for Oracle Client<br /><br /> SQL Server 用の .NET Framework データ プロバイダー<br /><br /> OraOLEDB<br /><br /> MSDASQL|  
|Teradata リレーショナル データベース|Teradata V2R6、V12|(該当なし)|TDOLEDB OLE DB プロバイダー<br /><br /> .Net Data Provider for Teradata|  
|Informix リレーショナル データベース||(該当なし)|Informix OLE DB プロバイダー|  
|IBM DB2 リレーショナル データベース|8.1|(該当なし)|DB2OLEDB|  
|Sybase Adaptive Server Enterprise (ASE) リレーショナル データベース|15.0.2|(該当なし)|Sybase OLE DB プロバイダー|  
|その他のリレーショナル データベース|(該当なし)|(該当なし)|OLE DB プロバイダーまたは ODBC ドライバー|  
|テキスト ファイル|(該当なし)|.txt、.tab、.csv|ACE 14 OLE DB Provider for Microsoft Access|  
|Microsoft Excel ファイル|Excel 97 ～ 2003、2007、2010|.xlsx、.xlsm、.xlsb、.xltx、.xltm|ACE 14 OLE DB プロバイダー|  
|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] ブック|Microsoft SQL Server 2008 R2 Analysis Services|.xlsx、.xlsm、.xlsb、.xltx、.xltm|ASOLEDB 10.5<br /><br /> ( [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] がインストールされている SharePoint ファームにパブリッシュされた [!INCLUDE[ssGeminiShort](../../includes/ssgeminishort-md.md)] ブックでのみ使用)|  
|Analysis Services キューブ|Microsoft SQL Server 2005、2008、2008 R2 Analysis Services|(該当なし)|ASOLEDB 10|  
|データ フィード<br /><br /> (Reporting Services のレポート、Atom サービス ドキュメント、Microsoft Azure Marketplace DataMarket、および単一のデータ フィードからのデータのインポートに使用)|Atom 1.0 形式<br /><br /> Windows Communication Foundation (WCF) データ サービス (以前の ADO.NET Data Services) として公開されている任意のデータベースまたはドキュメント。|.atomsvc (1 つ以上のフィードを定義するサービス ドキュメント用)<br /><br /> .atom (Atom Web フィード ドキュメント用)|Microsoft Data Feed Provider for [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]<br /><br /> 用の .NET Framework データ フィード データ プロバイダー [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]|  
|Office データ接続ファイル||.odc||  
  
 <sup>1</sup> OLE DB PROVIDER for ODBC を使用することもできます。  
  
 <sup>2</sup> SQL Azure の詳細については、web サイト[SQL Azure](https://go.microsoft.com/fwlink/?LinkID=157856)を参照してください。  
  
 <sup>3</sup> SQL Server PDW の詳細については、web サイト[SQL Server 2008 R2 Parallel Data Warehouse](https://go.microsoft.com/fwlink/?LinkId=150895)」を参照してください。  
  
 <sup>4</sup>場合によっては、MSDAORA OLE DB プロバイダーを使用すると、特に新しいバージョンの Oracle で接続エラーが発生する可能性があります。 エラーが生じる場合は、Oracle 用に記載されている他のプロバイダーを使用することをお勧めします。  
  
##  <a name="unsupported-sources"></a><a name="bkmk_unsupported_ds"></a>サポートされていないソース  
 次のデータ ソースは、現在サポートされていません。  
  
-   サーバー ドキュメント (たとえば、SharePoint にパブリッシュされている Access データベース) はインポートできません。  
  
##  <a name="tips-for-choosing-data-sources"></a><a name="bkmk_tips"></a>データソースの選択に関するヒント  
  
1.  リレーショナル データベースからテーブルをインポートする場合、インポート時には *外部キー* リレーションシップを使用して、モデル デザイナーのテーブル間にリレーションシップが作成されるので、手順を省略できます。  
  
2.  複数のテーブルをまとめてインポートしてから不必要なテーブルを削除することで、手順を省略することもできます。 テーブルを 1 つずつインポートしても、テーブル間のリレーションシップを手動で作成する必要が生じる場合があります。  
  
3.  複数のデータ ソースに、類似データが格納されている列があれば、モデル デザイナー内でリレーションシップを作成する理由になります。 異種のデータ ソースを使用する場合は、同一データまたは類似データが格納されている他のデータ ソースのテーブルにマップできる列のあるテーブルを選択します。  
  
4.  一般に、OLE DB プロバイダーは、大規模なデータに対して高いパフォーマンスを発揮します。 同じデータ ソースに対して数種類のプロバイダーの中から選択する場合は、最初に OLE DB プロバイダーを選択することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式のデータソース &#40;&#41;](../data-sources-ssas-tabular.md)   
 [データのインポート &#40;SSAS テーブル&#41;](../import-data-ssas-tabular.md)  
  
  
