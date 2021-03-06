---
title: レポートを印刷する (Reporting Services の SharePoint モード) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- printing reports, SharePoint Web application
- printing reports
ms.assetid: 026784f7-8cb4-4351-93ee-230b2ab0f8f5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5beb9301d21d59d166e1f3725e19b27e994c0b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634280"
---
# <a name="print-a-report-reporting-services-in-sharepoint-mode"></a>レポートを印刷する (Reporting Services の SharePoint モード)
  SharePoint モードで実行されているレポート サーバーで SharePoint Web アプリケーションからレポートを印刷するには次の 3 つの方法があります。  
  
-   **SharePoint サイトから印刷する方法:** レポートを開くとレポート ツール バーに表示される **[アクション]** メニューから、 **[印刷]** を選択します。 これにより、Reporting Services の印刷機能を使用できます。この印刷機能では、標準の **[印刷]** ダイアログ ボックスを使用して、プリンターの選択、ページと余白の指定、およびレポートのプレビューを行うことができます。 この印刷機能は、ブラウザーの [ファイル] メニューの [印刷] コマンドの代わりに使用するためのものです。 この方法でレポートを印刷すると、レポートがデザインどおりに印刷され、Web ページの印刷で表示されるような余分な要素は印刷されません。  
  
-   **ブラウザーから印刷する方法:** ブラウザーの印刷機能は、HTML レポートが 1 ページに収まる場合に適しています。 通常、ブラウザーから印刷したページには、Web ページ上にあるすべての可視要素と、ページまたは Web サイトを識別するヘッダーおよびフッター情報が含まれます。 ブラウザーから印刷すると、現在のウィンドウの内容のみが印刷されます。 長いレポートの場合はその一部しか印刷されません (通常は最初のページのみ)。  
  
-   **対象アプリケーションから印刷する方法:** レポートをエクスポートすると、Microsoft Office Excel や Adobe Acrobat Reader など、エクスポート先アプリケーションの印刷機能を使用することができます。 TIFF や PDF など、アプリケーションの形式が複数ページのレポートの印刷に適しているものもあります。 レポートをデスクトップ アプリケーションにエクスポートすると、そのアプリケーションに備わっている特殊な印刷機能を使用できます。 レポートをエクスポートするには、レポートを開いたときにレポート ツール バーに表示される **[アクション]** メニューの **[エクスポート]** を選択します。  
  
> [!NOTE]  
>  レポートを印刷するには、レポートを表示する権限が必要です。  
  
 Web ページからレポートを印刷したときに最適な結果を得るには、 **[アクション]** メニューの **[印刷]** を使用します。 **[印刷]** アクションは、レポート サーバーからダウンロードされるクライアントの印刷コントロールに関連付けられます。 ダウンロードが行われるのは、初めて **[印刷]** を選択したときの 1 回だけです。  
  
 レポート作成者は、レポートを印刷用または特定のアプリケーション形式向けに設計できます。 アプリケーションの形式によってページの割り当て方法が異なるため、すべてのエクスポート形式であらゆるレポートを最適な形で印刷できるとは限りません。 印刷用に設計するレポートとは対照的に、画面用のレポートのページは、データ量の変化に対応するように設計します。 たとえば、マトリックスを含むレポートでは、行や列をどのように展開するかによって、ページが上下左右に広がる可能性があります。 サイズが変化するレポートを印刷する場合、マトリックスを展開したユーザーと展開していないユーザーでは、印刷結果が異なります。 エクスポートしたレポートでは、ほとんどの場合、レポートに表示されるすべての要素 (ユーザーがコンピューターの画面上で見るすべての要素) がレポートの印刷結果に含まれます。  
  
### <a name="how-to-print-reports-from-the-actions-menu"></a>[アクション] メニューからレポートを印刷する方法  
  
1.  レポートを開きます。  
  
2.  **[アクション]** メニューの **[印刷]** をクリックします。 **[アクション]** メニューが表示されない場合は、レポート ツール バーが非表示になっているため、このツール バーの機能を使用できません。 **[アクション]** メニューが表示されていても、そのメニューに **[印刷]** がない場合は、印刷機能がレポート サーバー上で無効になっているため、使用できません。  
  
3.  **[印刷]** ダイアログ ボックスで、使用するプリンターと設定を選択し、 **[OK]** をクリックします。  
  
     既定の設定を変更するには、 **[プロパティ]** ボタンをクリックします。 ページ サイズは、レポート定義で定義されているレポート ページ サイズの既定の高さと幅によって決まります。 ページのサイズをどの程度変更できるかは、使用しているプリンターの機能によって異なります。  
  
     印刷する前にレポートを表示するには、 **[プレビュー]** ボタンをクリックします。 これにより、レポートの最初のページが別のプレビュー ウィンドウに表示されます。 残りのページは、レポート サーバーでレポートが表示されると利用可能になります。 レポートのプレビューは、EMF 形式で表示されます。 プレビューでは前後のページに移動することができ、最後のページに到達すると、 **[次へ]** ボタンが無効になります。 プレビュー ページの印刷余白を変更するには、 **[余白]** ボタンをクリックします。 **[余白]** ダイアログ ボックスが表示されます。 上下および左右の余白を設定し、 **[OK]** をクリックします。 ダイアログ ボックスが閉じ、プレビューの表示および印刷の設定が保存されます。  
  
## <a name="see-also"></a>参照  
 [Reporting Services のクライアント側印刷機能の有効化と無効化](../report-server/enable-and-disable-client-side-printing-for-reporting-services.md)  
  
  
