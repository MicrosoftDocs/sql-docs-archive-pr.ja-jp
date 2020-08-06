---
title: '[列表示] ダイアログボックス (レポートビルダー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10127"
ms.assetid: 0c030cab-6087-45a5-99f0-c7bd693f20a1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4c775734a4dbba2120a2af86e35a3872f5fff718
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713902"
---
# <a name="column-visibility-dialog-box-report-builder"></a>[列表示] ダイアログ ボックス (レポート ビルダー)
  **[列表示]** ダイアログ ボックスでは、選択した列をレポートの初期実行時に表示または非表示にする操作や、別のレポート アイテムを使用して列の表示を切り替える操作を行うことができます。  
  
## <a name="options"></a>Options  
 **[レポートの初期実行時]**  
 レポートにレポート アイテムを表示する際の初期設定を示すオプションを選択します。  
  
 **表示**  
 列を表示します。  
  
 **Hide**  
 列を非表示にします。  
  
 **[式を基に表示/非表示を切り替える]**  
 式を使用して初期表示を変化させます。  
  
 アイテムを非表示にする場合は `Boolean`、アイテムを表示する場合は `True` と評価される `False` 値の式を入力します。 式を編集するには、式 ([*fx*]) ボタンをクリックします。  
  
 **[次のレポート アイテムでの表示の切り替えを可能にする]**  
 HTML レポート ビューアーでこの列の表示/非表示をユーザーが切り替えられるようにするための切り替えイメージを表示します。  
  
 切り替えイメージを表示するレポートのテキスト ボックスの名前 (「Textbox1」など) を入力または選択します。 選択するテキスト ボックスは、このレポート アイテムの現在のスコープまたはコンテナー スコープに存在する必要があります。 たとえば、子グループに関連付けられている行の表示を切り替えるには、親グループに関連付けられている行のテキスト ボックスを選択する必要があります。 グラフの表示を切り替えるには、レポート本文や四角形など、グラフと同じコンテナー スコープにあるテキスト ボックスを選択します。  
  
## <a name="see-also"></a>参照  
 [式の例 (レポート ビルダーおよび SSRS)](report-design/expression-examples-report-builder-and-ssrs.md)   
 [アイテムへの展開または折りたたみアクションの追加 &#40;レポートビルダーと SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)   
 [&#40;レポートビルダーと SSRS&#41;の画像](report-design/images-report-builder-and-ssrs.md)   
 [ダイアログボックス、ペイン、およびウィザードのヘルプのレポートビルダー](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [[全般] ([画像のプロパティ] ダイアログ ボックス) (レポート ビルダーおよび SSRS)](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
