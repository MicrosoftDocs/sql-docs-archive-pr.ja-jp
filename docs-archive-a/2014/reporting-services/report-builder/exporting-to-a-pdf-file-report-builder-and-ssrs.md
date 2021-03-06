---
title: PDF ファイルへのエクスポート (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f22497b7-f6c1-4c7b-b831-8c731e26ae37
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b4a324ad40d01d302196fe40ffb4232deb62a17
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631617"
---
# <a name="exporting-to-a-pdf-file-report-builder-and-ssrs"></a>PDF ファイルへのエクスポート (レポート ビルダーおよび SSRS)
  PDF 表示拡張機能を使用すると、Adobe Acrobat および PDF 1.3 をサポートするその他のサードパーティ製 PDF ビューアーで開くことのできるファイルとしてレポートが表示されます。 PDF 1.3 は Adobe Acrobat 4 以降のバージョンと互換性がありますが、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] では Adobe Acrobat 6 以降がサポートされています。 この表示拡張機能では、レポートの表示処理に Adobe 製のソフトウェアは必要ありません。 ただし、レポートを PDF 形式で表示または印刷するには、Adobe Acrobat などの PDF ビューアーが必要です。  
  
 PDF 表示拡張機能では ANSI 文字がサポートされ、日本語、韓国語、繁体中国語、簡体中国語、キリル文字、ヘブライ語、アラビア語の Unicode 文字を変換できます (一部制限事項があります)。 制限の詳細については、「[レポートのエクスポート &#40;レポートビルダーと SSRS&#41;](export-reports-report-builder-and-ssrs.md)」を参照してください。  
  
 PDF レンダラーは物理的なページ レンダラーなので、HTML や Excel などの他のレンダラーとは異なり、改ページ機能があります。 ここでは、PDF レンダラー固有の情報を提供し、規則の例外について説明します。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="font-embedding"></a><a name="FontRequirements"></a>フォントの埋め込み  
 PDF 表示拡張機能は、可能な場合、レポートを PDF ファイルで表示するために必要な各フォントのサブセットを埋め込みます。 レポートに使用されているフォントが、レポート サーバーにインストールされている必要があります。 レポート サーバーは、レポートを PDF 形式で生成する際に、レポートで参照されるフォントに保存されている情報を使用して、PDF ファイル内の文字マッピングを作成します。 参照されているフォントがレポート サーバーにインストールされていないと、結果の PDF ファイルに適切なマッピングが作成されず、正しく表示されなくなる可能性があります。  
  
 フォントは、次の条件が該当する場合、PDF ファイルに埋め込まれます。  
  
-   フォントの埋め込みがフォントの作成者によって許可されている。 インストールされているフォントには、そのフォントの作成者がドキュメントへのフォントの埋め込みを許可しているかどうかを示すプロパティが含まれています。 このプロパティの値が EMBED_NOEMBEDDING である場合、フォントは PDF ファイルに埋め込まれません。 詳細については、msdn.microsoft.com の「TTGetEmbeddingType」を参照してください。  
  
-   TrueType フォントである。  
  
-   フォントがレポート内の可視アイテムによって参照されている。 フォントを参照しているアイテムの "非表示" プロパティが True の場合、レンダリング データを表示する必要がないため、そのフォントはファイルに追加されません。 レンダリングされたレポート データを表示する必要がある場合にのみ、フォントの埋め込みが行われます。  
  
 以上の条件をすべて満たしている場合、フォントは PDF ファイルに埋め込まれます。 以上の条件が 1 つでも満たされなかった場合、そのフォントは PDF ファイルに埋め込まれません。  
  
> [!NOTE]  
>  ただし、条件が満たされていても、フォントが PDF ファイルに埋め込まれないという状況が発生する場合があります。 使用されているフォントが、一般に標準の Type 1 フォントまたは Base 14 フォントとして知られている PDF 仕様のフォントの場合、フォントは ANSI コンテンツには埋め込まれません。  
  
  
  
### <a name="fonts-on-the-client-computer"></a>クライアント コンピューター上のフォント  
 フォントが PDF ファイルに埋め込まれている場合、レポートを閲覧するコンピューター (クライアント コンピューター) にフォントがインストールされている必要はありません。フォントがインストールされていなくても、レポートは正しく表示されます。  
  
 フォントが PDF ファイルに埋め込まれていない場合、レポートを正しく表示するためには、クライアント コンピューターに適切なフォントがインストールされている必要があります。 クライアント コンピューターにフォントがインストールされていなかった場合、PDF ファイルには、サポートされていない文字の代わりに疑問符 (?) が表示されます。  
  
### <a name="verifying-fonts-in-a-pdf-file"></a>PDF ファイル内のフォントの検証  
 PDF 出力に差異が発生することが最も多い状況は、ラテン文字以外の文字をサポートしないフォントがレポートで使用されているときに、ラテン文字以外の文字がレポートに追加された場合です。 PDF 表示出力をレポート サーバーとクライアント コンピューターの両方でテストし、レポートが正しく表示されることを確認してください。  
  
 レポートのプレビュー表示やエクスポートした HTML 表示を過信しないでください。プレビューの場合はグラフィカル デザイン インターフェイスによって、HTML の場合は Microsoft Internet Explorer によって、それぞれフォントが自動的に置き換えられるため、レポートが正しく表示されているように見えます。 Unicode グリフがサーバーに存在しない場合、文字は疑問符 (?) で置き換えられることがあります。 フォントがクライアントに存在しない場合、文字は四角形 ( ) で置き換えられることがあります。  
  
 PDF ファイルに埋め込まれているフォントは、ファイルと共に保存される Fonts プロパティにメタデータとして追加されます。  
  
##  <a name="metadata"></a><a name="Metadata"></a> メタデータ  
 PDF 表示拡張機能では、レポート レイアウトに加えて PDF ドキュメント情報ディクショナリに次のメタデータを書き込みます。  
  
|PDF プロパティ|作成元|  
|------------------|------------------|  
|`Title`|`Name` RDL 要素の `Report` 属性です。|  
|`Author`|`Author` RDL 要素です。|  
|`Subject`|`Description` RDL 要素です。|  
|`Creator`|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 製品の名前およびバージョンです。|  
|`Producer`|表示拡張機能の名前とバージョンです。|  
|`CreationDate`|PDF `datetime` 形式でのレポートの実行時間です。|  
  
  
  
##  <a name="interactivity"></a><a name="Interactivity"></a>双  
 PDF では、いくつかの対話型要素がサポートされています。 具体的な動作について説明します。  
  
### <a name="show-and-hide"></a>表示/非表示  
 PDF では、動的な表示/非表示要素がサポートされていません。 PDF ドキュメントは、レポート内にあるすべてのアイテムの現在の状態に合わせて表示されます。 たとえば、レポートを最初に実行したときにアイテムが表示されている場合、そのアイテムが表示されます。 切り替え可能な画像は、レポートのエクスポート時に非表示になっている場合、表示されません。  
  
### <a name="document-map"></a>ドキュメント マップ  
 ドキュメント マップ ラベルがレポートに存在する場合、PDF ファイルにドキュメント アウトラインが追加されます。 各ドキュメント マップ ラベルは、ドキュメント アウトラインのエントリとして、レポートに表示される順番で表示されます。 Acrobat で、対象のブックマークがドキュメント アウトラインに追加されるのは、そのブックマークが存在するページが表示されている場合のみです。  
  
 1 ページしか表示されていない場合、ドキュメント アウトラインは追加されません。 ドキュメント マップは、レポート内の入れ子レベルを反映するために階層状に配置されます。 ドキュメントアウトラインは、Acrobat の [ブックマーク] タブに表示されます。ドキュメントアウトライン内のエントリをクリックすると、ドキュメントはブックマークが付けられた場所に移動します。  
  
### <a name="bookmarks"></a>ブックマーク  
 PDF 表示では、ブックマークはサポートされていません。  
  
### <a name="drillthrough-links"></a>ドリルスルー リンク  
 PDF 表示では、ドリルスルー リンクはサポートされていません。 ドリルスルー リンクはクリック可能なリンクとして表示されず、詳細レポートはドリルスルーの対象に接続できません。  
  
### <a name="hyperlinks"></a>ハイパーリンク  
 レポート内のハイパーリンクは、PDF ファイル内でクリック可能なリンクとして表示されます。 クリックすると、Acrobat により、既定のクライアント ブラウザーが起動し、ハイパーリンクの URL に移動できます。  
  
  
  
##  <a name="compression"></a><a name="Compression"></a>機能  
 画像の圧縮は、画像の元のファイルの種類に基づいて行われます。 PDF 表示拡張機能は、既定で PDF ファイルを圧縮します。  
  
 PDF ファイルに含まれる画像の圧縮を可能な限り保持するために、JPEG 画像は JPEG として保存され、その他の種類の画像はすべて BMP として保存されます。  
  
> [!NOTE]  
>  PDF ファイルは PNG 画像の埋め込みをサポートしていません。  
  
  
  
##  <a name="device-information-settings"></a><a name="DeviceInfo"></a>デバイス情報の設定  
 デバイス情報設定を変更することによって、このレンダラーの既定の設定の一部を変更することができます。 詳細については、「 [PDF Device Information Settings](../pdf-device-information-settings.md)」を参照してください。  
  
  
  
## <a name="see-also"></a>参照  
 [Reporting Services &#40;レポートビルダーおよび SSRS&#41;での改ページ](../report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [レポートビルダーおよび SSRS&#41;&#40;レンダリング動作](../report-design/rendering-behaviors-report-builder-and-ssrs.md)   
 [さまざまなレポート表示拡張機能の対話機能 &#40;レポートビルダーと SSRS&#41;](interactive-functionality-different-report-rendering-extensions.md)   
 [レポートビルダーおよび SSRS&#41;&#40;レポートアイテムのレンダリング](../report-design/rendering-report-items-report-builder-and-ssrs.md)   
 [テーブル、マトリックス、および一覧 &#40;レポート ビルダーおよび SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)  
  
  
