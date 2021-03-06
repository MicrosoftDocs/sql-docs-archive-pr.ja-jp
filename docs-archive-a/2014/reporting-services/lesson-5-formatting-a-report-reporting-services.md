---
title: 'レッスン 5 : レポートの書式設定 (Reporting Services) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ae46efa9-6e04-48ec-afb4-5a2314dcb05a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 00f0d780e957fd9ff995fefb1d033275a7da428d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644842"
---
# <a name="lesson-5-formatting-a-report-reporting-services"></a>レッスン 5 : レポートの書式設定 (Reporting Services)
  Sales Orders レポートに 1 つのデータ領域といくつかのフィールドを追加した後、日付および通貨のフィールド、および列ヘッダーを書式設定できます。  
  
 このトピックの内容:  
  
-   [日付の書式設定](#bkmk_format_date)  
  
-   [通貨の書式設定](#bkmk_format_currency)  
  
-   [テキスト スタイルおよび列幅の変更](#bkmk_change_textstyle)  
  
##  <a name="format-the-date"></a><a name="bkmk_format_date"></a>日付の書式設定  
 日付フィールドには、既定では日付と時刻の情報が表示されます。 このフィールドを書式設定して、日付のみを表示できます。  
  
#### <a name="to-format-a-date-field"></a>日付フィールドを書式設定するには  
  
1.  **[デザイン]** タブをクリックします。  
  
2.  `[Date]` フィールド式が入力されているセルを右クリックし、[ **テキスト ボックスのプロパティ**] をクリックします。  
  
3.  [**数値**] をクリックし、[**カテゴリ**] フィールドでを選択し `Date` ます。  
  
4.  **[型]** ボックスで **[2000 年 1 月 31 日]** を選択します。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  レポートをプレビューして `[Date]` フィールドに対する変更を確認し、デザイン ビューに戻ります。  
  
##  <a name="format-the-currency"></a><a name="bkmk_format_currency"></a>通貨の書式を設定する  
 [LineTotal] フィールドには通常の数値が表示されます。 このフィールドを書式設定して、数値を通貨として表示します。  
  
#### <a name="to-format-a-currency-field"></a>通貨フィールドを書式設定するには  
  
1.  `[LineTotal]` フィールド式が入力されているセルを右クリックし、[ **テキスト ボックスのプロパティ**] をクリックします。  
  
2.  **[数値]** をクリックし、 **[Category]** フィールドで **[通貨]** を選択します。  
  
3.  地域設定が英語 (米国) の場合、既定値は次のようになります。  
  
    -   **小数点以下の桁数 : 2**  
  
    -   **負の数値 : ($12345.00)**  
  
    -   **記号 : $ 英語 (米国)**  
  
4.  [ **位取り区切り記号 (,) を使用する]** を選択します。  
  
     "**$12,345.00**" というサンプル テキストが表示されている場合、正しい設定が行われています。  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  レポートをプレビューして `[LineTotal]` フィールドに対する変更を確認し、デザイン ビューに戻ります。  
  
##  <a name="change-text-style-and-column-widths"></a><a name="bkmk_change_textstyle"></a>テキストのスタイルと列の幅を変更する  
 ヘッダー行の書式を変更して、レポートのデータの行と区別することもできます。 最後に、列の幅を調整します。  
  
#### <a name="to-format-header-rows-and-table-columns"></a>ヘッダー行およびテーブル列を書式設定するには  
  
1.  テーブルをクリックし、列ハンドルおよび行ハンドルをテーブルの上部および横に表示します。  
  
     ![デザイン、ヘッダー行と詳細行のあるテーブル](../../2014/tutorials/media/rs-basictabledetailsdesign.gif "デザイン、ヘッダー行と詳細行のあるテーブル")  
  
     テーブルの上と横のグレーのバーは、列および行ハンドルです。  
  
2.  列ハンドルの間の罫線をポイントします。カーソルが 2 方向の矢印の形状に変化します。 列をドラッグして、目的のサイズに変更します。  
  
3.  列ヘッダー ラベルを含む行を選択し、 **[書式]** メニューの **[フォント]** をポイントして **[太字]** をクリックします。  
  
4.  レポートをプレビューするには、[**プレビュー** ] タブをクリックします。次のようになります。  
  
     ![列ヘッダーが太字になっているテーブルのプレビュー](../../2014/tutorials/media/rs-basictabledetailsformattedpreview.gif "列ヘッダーが太字になっているテーブルのプレビュー")  
  
5.  **[ファイル]** メニューの **[すべてを保存]** をクリックして、レポートを保存します。  
  
## <a name="next-steps"></a>次の手順  
 ここでは、列ヘッダー、日付値、および通貨値を書式設定しました。 次に、レポートにグループ化および合計を追加します。 「[レッスン 6: グループと合計の追加 &#40;Reporting Services&#41;」](../reporting-services/lesson-6-adding-grouping-and-totals-reporting-services.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [&#40;レポートビルダーと SSRS&#41;の数値と日付の書式設定](report-design/formatting-numbers-and-dates-report-builder-and-ssrs.md)   
 [レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;](report-design/rendering-behaviors-report-builder-and-ssrs.md)  
  
  
