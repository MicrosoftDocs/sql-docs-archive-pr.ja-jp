---
title: マップレポートのサポートを計画する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3d1e1774e44ae879b8c01e66289cefd4d42ee1c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739498"
---
# <a name="plan-for-map-report-support"></a>マップ レポートのサポートを計画する
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)]では、空間データソースを使用するマップレポートがサポートされています。 空間データは、SQL Server データベース、ESRI シェープファイル、または Reporting Services かレポート ビルダーを使用してインストールされたマップ ギャラリーから取得できます。 また、マップには Bing のマップ タイルの背景も表示できます。 レポートの作成者は、空間データまたは Bing のマップ タイルが動的であり実行時に取得されるか、静的でありレポート定義に埋め込まれるかを指定してレポートを作成できます。  
  
## <a name="support-for-bing-maps"></a>Bing Maps のサポート  
 マップには、Bing のマップ タイルを表示する背景レイヤーを含めることができます。 マップ タイル レイヤーを含むパブリッシュ済みレポートを表示するには、Bing Maps Web サービスからタイルを取得するようにレポート サーバーを構成する必要があります。 詳しくは、「 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)」をご覧ください。  
  
 各レポートについて、レポート作成者は、タイル サーバーからタイルを取得する際に SSL (Secure Sockets Layer) 接続を使用するかどうかを指定できます。 この操作を行うには、タイルレイヤーの [プロパティ] ペインで、ブール型プロパティの UseSecureConnection をに設定する必要があり `true` ます。  
  
> [!NOTE]  
>  レポート内での Bing のマップ タイルの使用については、「 [追加使用条件](https://go.microsoft.com/fwlink/?LinkId=151371) 」および「 [プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkId=151372)」を参照してください。  
  
## <a name="report-design-recommendations"></a>レポートのデザインに関する推奨事項  
 マップ レポートを適切にデザインするには、静的な空間データと動的な空間データのトレードオフを評価し、レポートのユーザーにとって最適なバランスを見極める必要があります。 マップ要素を埋め込んだ場合、レポート定義のサイズが著しく増加しますが、レポート内でマップを表示するために要する時間が短縮されます。 動的なマップ要素の場合、レポート定義のサイズが小さくなりますが、マップを処理して表示するために要する時間が増加します。 レポートの作成者は、この相反する要因の間で適切にバランスをとる必要があります。  
  
 レポート定義のサイズが問題となる場合、レポート サーバーの管理者は、レポートの設計者にレポート定義の空間データの量を削減するように促してもよいでしょう。  
  
 次のような場合には、マップ要素がレポート定義に埋め込まれます。  
  
-   レポートの作成時に、空間データ ソースがローカルのファイル システムに置かれている。 これには、ローカルにインストールされた ESRI シェープファイルまたはマップ ギャラリーからの空間データも含まれます。 既定で、マップ ウィザードおよびマップ レイヤー ウィザードでは、ローカル ファイル システム上のデータ ソースに由来する空間データが埋め込まれます。  
  
-   レポートの作成者が、レポートに空間データを手動で埋め込むオプションを選択した。  
  
 マップを含むレポート定義のサイズを削減するには、次の選択肢を 1 つ以上実行します。  
  
-   のレポートデザイナーから [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 、ESRI シェープファイルの空間データソースをレポートサーバープロジェクトに追加します。 プロジェクトの配置時に、レポートに加えて ESRI シェープファイルがレポート サーバーにパブリッシュされます。 マップ ウィザードを実行する際に、レポート サーバー プロジェクトの空間データ ソースを指定すると、既定でマップ要素はレポート定義に埋め込まれません。  
  
-   レポートビルダーから、レポートサーバーからシェープファイルを選択して、ESRI シェープファイルの空間データソースを追加します。 マップ ウィザードを実行する際に、レポート サーバーの空間データ ソースを参照して指定すると、既定でマップ要素はレポート定義に埋め込まれません。  
  
-   マップ データを埋め込みマップ データにする必要がある場合、ビューポートの中心位置とズーム レベルを調整して、レポートに必要なマップ データのみが含まれるようにする。  
  
 詳細については、 [&#40;レポートビルダーと SSRS&#41;をマップ](report-design/maps-report-builder-and-ssrs.md)します。  
  
## <a name="see-also"></a>参照  
 [レポートのトラブルシューティング: マップ レポート &#40;レポート ビルダーおよび SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
