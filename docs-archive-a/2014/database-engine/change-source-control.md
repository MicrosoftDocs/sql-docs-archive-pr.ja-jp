---
title: ソース管理の変更 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- IDD_SCC_CONNECTION_DIALOG
helpviewer_keywords:
- Change Source Control dialog box
ms.assetid: e6a5d83c-5809-4c56-907a-73d0c7ccdd7a
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 55831529243608e8c71972a31009e5672fb0234f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642329"
---
# <a name="change-source-control"></a>ソース管理の変更
  ローカルに保存されたソリューションまたはプロジェクトを、ソース管理データベース フォルダーに関連付ける、接続とバインドの作成と管理を行います。  
  
## <a name="dialog-box-access"></a>ダイアログ ボックスの表示  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のソリューション エクスプローラーで、項目を選択します。 [**ファイル**] メニューの [**ソース管理**] をクリックし、[**ソース管理の変更**] をクリックします。  
  
> [!NOTE]  
>  ソリューション エクスプローラーで項目を右クリックしても、このダイアログ ボックスを表示できます。  
  
## <a name="options"></a>Options  
 **束縛**  
 指定したソース管理サーバーの場所に、選択した項目を関連付けます。 たとえば、このボタンを使用して、最後に認識したソース管理サーバーのフォルダーとデータベースにバインドすることができます。 最近使用したサーバーのフォルダーやデータベースが見つからない場合、別のものを指定するように求めるメッセージが表示されます。  
  
 **[参照]**  
 指定した項目に適用する、新しいソース管理サーバーの場所を指定します。  
  
 **[列]**  
 表示する列とその表示順序を指定します。  
  
 **のインスタンスに接続するときには、**  
 選択した項目とソース管理サーバーの間に接続を作成します。  
  
 **接続済み**  
 選択したソリューションまたはプロジェクトの接続状態が表示されます。  
  
 **Disconnect (切断)**  
 コンピューター上のソリューションまたはプロジェクトのローカル コピーと、データベース上のマスター コピーとの接続を解除します。 たとえばラップトップを使用してオフラインで作業しているときなど、コンピューターとソース管理サーバーの接続を解除する前にこのコマンドを使用します。  
  
 **[OK]**  
 このダイアログ ボックスで加えた変更が適用されます。  
  
 **プロバイダー**  
 ソース管理プラグインの名前が表示されます。  
  
 **[更新]**  
 このダイアログ ボックスに表示されている、すべてのプロジェクトの接続情報を更新します。  
  
 **[サーバー バインド]**  
 ソース管理サーバーへの項目のバインドを示します。  
  
 **[サーバー名]**  
 対応するソリューションまたはプロジェクトがバインドされているソース管理サーバーの名前が表示されます。  
  
 **[ソリューション/プロジェクト]**  
 現在の選択における各ソリューションおよびプロジェクトの名前が表示されます。  
  
 **Sort**  
 表示される列の順序を並べ替えます。  
  
 **状態**  
 項目のバインドと接続の状態を示します。 選択可能なオプションは次のとおりです。  
  
|**オプション**|**説明**|  
|----------------|---------------------|  
|有効|項目は、その項目が属するサーバー フォルダーに正しくバインドされ、接続されています。|  
|無効|項目は、その項目が属するフォルダーに正しくバインドされていないか、接続が切断されています。 この項目には、[**バインド**] ではなく [**ソース管理に追加**] コマンドを使用します。|  
|Unknown|ソース管理下にある項目の状態がまだ決定されていません。|  
|[制御しない]|項目がソース管理下にありません。|  
  
 **バインドの解除**  
 [**ソース管理**] ダイアログボックスを表示して、ソース管理から選択した項目を削除したり、その項目と現在のフォルダーとの関連付けを完全に解除したりすることができます。  
  
## <a name="see-also"></a>参照  
 [ソリューション エクスプローラーのソース管理](../../2014/database-engine/solution-explorer-source-control.md)  
  
  