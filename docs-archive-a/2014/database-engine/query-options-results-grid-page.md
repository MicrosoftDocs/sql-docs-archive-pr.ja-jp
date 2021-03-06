---
title: '[クエリオプション] の [結果] ([グリッド] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- sql12.swb.query.grid.f1
ms.assetid: 764bf435-3aab-4c62-b4e0-64fe020a5a95
author: rothja
ms.author: jroth
ms.openlocfilehash: bf300dd5071128b0259230ae788a27595bd8d29e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644126"
---
# <a name="query-options-results-grid-page"></a>[クエリ オプション] の [結果] ([グリッド] ページ)
  このページを使用すると、クエリ結果セットをグリッド形式で表示するためのオプションを指定できます。  
  
## <a name="options"></a>Options  
 **[結果セットにクエリを含める]**  
 クエリのテキストを結果セットの一部として返します。  
  
 **[結果のコピーまたは保存時に列のヘッダーを含める]**  
 結果をクリップボードにコピーしたりファイルに保存したりするときに、列のヘッダー (タイトル) を含めます。 保存またはコピーされる結果データに列の見出しを含めずに、データだけ保存またはコピーするには、このチェック ボックスをオフにします。  
  
 **[実行後に結果を破棄する]**  
 画面表示がクエリ結果を受け取った後にクエリ結果を破棄することによって、メモリを解放します。  
  
 **[結果を別のタブに表示する]**  
 結果セットを、クエリ ドキュメント ウィンドウの下部ではなく、新しいドキュメント ウィンドウに表示します。  
  
 **[クエリ実行後に [結果] タブに切り替える]**  
 画面のフォーカスを自動的に結果セットに設定します。  
  
 **[取得される最大文字数]**  
 **XML 以外のデータ**:  
  
 1 ～ 65,535 の値を入力して、各セルに表示される最大文字数を指定します。  
  
> [!NOTE]  
>  大きな文字数を指定すると、結果セット内のデータが切り捨てられたように見える場合があります。 各セルに表示される最大文字数は、フォントのサイズに依存します。 大きな結果セットが返された場合、このボックスに大きな値を指定していると、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のメモリ上での実行速度が低下したり、システムのパフォーマンスに悪影響が及んだりすることがあります。  
  
 **XML データ**:  
  
 **[1 MB]**、 **[2 MB]**、または **[5 MB]** を選択します。 すべての文字を取得する場合は、 **[無制限]** を選択します。  
  
 **既定値にリセット**  
 このページ上のすべての値を元の既定値にリセットします。  
  
  
