---
title: '[Raw ファイル変換先エディター] ([接続マネージャー] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.rawfiledestinationconnectionmanager.f1
ms.assetid: a0ec9643-3b44-4467-b855-f45ae4794f7f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a693591921a5669eb9bc8160f0be076ab4d6869b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713273"
---
# <a name="raw-file-destination-editor-connection-manager-page"></a>[RAW ファイル変換先エディター] ([接続マネージャー] ページ)
  ファイルに RAW データを書き込むための RAW ファイル変換先を構成するには、RAW ファイル変換先エディターを使用します。  
  
 **目的に合ったトピックをクリックしてください**  
  
-   [Raw ファイル変換先エディターを開く](#open)  
  
-   [[接続マネージャー] タブのオプションの設定](#connection)  
  
-   [[列] タブのオプションの設定](#mapping)  
  
##  <a name="open-the-raw-file-destination-editor"></a><a name="open"></a> RAW ファイル変換先エディターを開く  
  
1.  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] で、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]パッケージに RAW ファイル変換先を追加します。  
  
2.  コンポーネントを右クリックし、 **[編集]** をクリックします。  
  
##  <a name="set-options-on-the-connection-manager-tab"></a><a name="connection"></a> [接続マネージャー] タブのオプションの設定  
 **アクセス モード**  
 ファイル名の指定方法を選択します。 ファイル名とパスを直接入力するには **[ファイル名]** を選択します。ファイル名を含んでいる変数を指定するには、 **[変数からのファイル名]** を選択します。  
  
 **[ファイル名]** または **[変数名]**  
 RAW ファイルの名前とパスを入力するか、またはファイル名を含んでいる変数を選択します。  
  
 **[書き込みオプション]**  
 ファイルの作成およびファイルへの書き込みに使用するメソッドを選択します。  
  
 **[初期 RAW ファイルの生成]**  
 パッケージを実行せずに、列のみを含む空の RAW ファイル (メタデータのみのファイル) を生成するには、このボタンをクリックします。 ファイルには、 **[RAW ファイル変換先エディター]** の **[列]** ページで選択した列が含まれています。 RAW ファイル ソースの参照先を、このメタデータのみのファイルにすることができます。  
  
 **[初期 RAW ファイルの生成]** をクリックすると、メッセージ ボックスが表示されます。 ファイルの作成を続行するには、 **[OK]** をクリックします。 **[列]** ページで別の列の一覧を選択するには、 **[キャンセル]** をクリックします。  
  
##  <a name="set-options-on-the-columns-tab"></a><a name="mapping"></a>[列] タブのオプションの設定  
 **使用できる入力列**  
 RAW ファイルに書き込む 1 つ以上の入力列を選択します。  
  
 **入力列**  
 **[使用できる入力列]** から選択した場合、このテーブルに入力列が自動的に追加されます。入力列をこのテーブルで直接選択することもできます。  
  
 **[出力の別名]**  
 出力列に使用する代替名を指定します。  
  
## <a name="see-also"></a>参照  
 [RAW ファイル変換先](data-flow/raw-file-destination.md)  
  
  
