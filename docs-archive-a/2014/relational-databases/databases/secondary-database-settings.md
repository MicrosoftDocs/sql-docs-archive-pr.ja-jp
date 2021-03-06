---
title: '[セカンダリ データベースの設定] | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.dest.f1
ms.assetid: f992ffc9-ee42-43fe-acec-512032f0ded1
author: stevestein
ms.author: sstein
ms.openlocfilehash: 265d6beda830e2090392918ae14d10c8b7752d02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640046"
---
# <a name="secondary-database-settings"></a>[セカンダリ データベースの設定]
  このダイアログ ボックスを使用すると、ログ配布構成におけるセカンダリ データベースのプロパティを構成および変更できます。  
  
 ログ配布の概念については、「 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[セカンダリ サーバー インスタンス]**  
 ログ配布構成において、現在、セカンダリ サーバーとして構成されている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前が表示されます。  
  
 **[セカンダリ データベース]**  
 ログ配布構成のセカンダリ データベースの名前を表示します。 新しいセカンダリ データベースをログ配布構成に追加する場合は、一覧からデータベースを選択するか、ボックスに新しいデータベースの名前を入力します。 新しいデータベースの名前を入力する場合は、セカンダリ データベースにプライマリ データベースの完全なデータベース バックアップを復元するオプションを **[初期化]** タブで選択する必要があります。 新しいデータベースは復元操作の一部として作成されます。  
  
 **のインスタンスに接続するときには、**  
 ログ配布構成において、セカンダリ サーバーとして使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続します。 接続に使用するアカウントは、セカンダリ サーバーのインスタンスの sysadmin 固定サーバー ロールのメンバーである必要があります。  
  
 **[初期化] タブ**  
 次のようなオプションがあります。  
  
 **[はい、プライマリ データベースの完全バックアップを生成して、セカンダリ データベースに復元します]**  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、プライマリ データベースをバックアップし、それをセカンダリ サーバーに復元することで、セカンダリ データベースを構成します。 **[セカンダリ データベース]** ボックスに新しいデータベースの名前を入力した場合、データベースは復元操作の一部として作成されます。  
  
 **[復元オプション]**  
 セカンダリ データベースのデータ ファイルおよびログ ファイルをセカンダリ サーバー上の既定以外の場所に復元する場合は、これをクリックします。  
  
 このボタンをクリックすると、 **[復元オプション]** ダイアログ ボックスが開きます。 このダイアログ ボックスで、セカンダリ データベースおよびそのログを保存する既定以外のフォルダーのパスを指定します。 どちらかのフォルダーを指定した場合は、もう一方のフォルダーも指定する必要があります。  
  
 パスでは、セカンダリ サーバーに対してローカルなドライブを参照する必要があります。 また、パスは、ローカル ドライブ名とコロンで始まっている必要があります (たとえば、 `C:`)。 マップされたドライブ名およびネットワーク パスは無効です。  
  
 **[復元オプション]** ボタンをクリックした後で既定のフォルダーを使用することにした場合は、 **[復元オプション]** ダイアログ ボックスを取り消すことをお勧めします。 既定以外の場所を既に指定した後で既定の場所を使用することにした場合は、 **[復元オプション]** をもう一度クリックし、テキスト ボックスを消去し、[OK] をクリックします。  
  
 **[はい、プライマリ データベースの既存のバックアップをセカンダリ データベースに復元します]**  
 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] で、プライマリ データベースの既存のバックアップを使用して、セカンダリ データベースを初期化します。 対象のバックアップの場所を **[バックアップ ファイル]** ボックスに入力します。 [セカンダリ データベース] ボックスに新しいデータベースの名前を入力した場合、データベースは復元操作の一部として作成されます。  
  
 **[バックアップ ファイル]**  
 **[はい、プライマリ データベースの既存のバックアップをセカンダリ データベースに復元します]** を選択した場合は、セカンダリ データベースを初期化するために使用する、データベースの完全バックアップのパスとファイル名を入力します。  
  
 **[復元オプション]**  
 このトピックで既に説明したこのボタンに関する記述を参照してください。  
  
 **[いいえ、セカンダリ データベースは初期化されています]**  
 セカンダリ データベースが既に初期化されていて、プライマリ データベースからトランザクション ログ バックアップを受け入れる準備が整っていることを指定します。 **[セカンダリ データベース]** ボックスに新しいデータベース名を入力した場合は、このオプションは使用できません。  
  
 **[ファイルのコピー] タブ**  
 次のようなオプションがあります。  
  
 **[ファイルのコピー先フォルダー: (通常、このフォルダーはセカンダリ サーバーにあります)]**  
 セカンダリ データベースに復元するために、トランザクション ログ バックアップのコピー先のパスを入力します。 通常は、セカンダリ サーバー上のフォルダーへのローカル パスを指定します。 フォルダーが別のサーバー上にある場合は、フォルダーへの UNC パスを指定する必要があります。 セカンダリ サーバー インスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービス アカウントには、このフォルダーに対する読み取り権限を指定する必要があります。 さらに、コピー ジョブおよび復元ジョブをセカンダリ サーバー インスタンスで実行するプロキシ アカウントに対して、このネットワーク共有に対する読み取り/書き込み権限を許可する必要があります。 既定では、セカンダリ サーバー インスタンスの SQL Server エージェント サービス アカウントが使用されますが、sysadmin はジョブに他のプロキシ アカウントを選択できます。  
  
 **[次の期間経過したコピー済みファイルを削除する]**  
 コピーされたトランザクション ログ バックアップ ファイルを削除する前に、コピー先フォルダーに保持する期間を選択します。  
  
 **ジョブ名**  
 トランザクション ログ バックアップ ファイルをプライマリ サーバーからセカンダリ サーバーにコピーするときに使用する、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブの名前が表示されます。 このジョブを作成しているときは、ボックスに入力することで名前を変更できます。  
  
 **[スケジュール]**  
 トランザクション ログ バックアップを、プライマリ サーバーからセカンダリ サーバーにコピーする、SQL Server エージェントのコピー ジョブの現在のスケジュールを表示します。 **[スケジュール]** をクリックすると、このスケジュールを変更できます。  
  
 **[スケジュール]**  
 トランザクション ログ バックアップを、プライマリ サーバーからセカンダリ サーバーにコピーする、SQL Server エージェント ジョブのパラメーターを変更します。  
  
 **[このジョブを無効にする]**  
 SQL Server エージェントのコピー ジョブを中断します。  
  
 **[トランザクション ログの復元] タブ**  
 次のようなオプションがあります。  
  
 **[バックアップの復元時に、データベースのユーザーを切断する]**  
 トランザクション ログのバックアップの復元時にセカンダリ データベースから自動的にユーザーを切断します。  
  
 **[復旧モードなし]**  
 セカンダリ データベースを NORECOVERY モードで保持します。  
  
 **[スタンバイ モード]**  
 セカンダリ データベースを STANDBY モードで保持します。 このモードでは、データベースに対して読み取り専用の操作を実行できます。  
  
> [!IMPORTANT]  
>  既存のセカンダリ データベースの復旧モードを、たとえば、 **[復旧モードなし]** から **[スタンバイ モード]** に変更した場合、この変更は、次のログのバックアップがデータベースに復元されるまで有効になりません。  
  
 **[バックアップの復元を最低限次の期間遅延する]**  
 トランザクション ログ バックアップがセカンダリ データベースに復元されるまでの遅延を選択します。  
  
 **[復元が次の期間内に行われない場合は警告する]**  
 トランザクション ログの復元処理が発生しなかった場合に、ログ配布の警告を発生させる前に待機する期間を選択します。  
  
 **ジョブ名**  
 トランザクション ログ バックアップを、セカンダリ データベースに復元するために使用する SQL Server エージェント ジョブの名前を表示します。 このジョブを作成しているときは、ボックスに入力することで名前を変更できます。  
  
 **[スケジュール]**  
 トランザクション ログ バックアップを、セカンダリ データベースに復元するために使用する SQL Server エージェント ジョブの現在のスケジュールを表示します。 **[スケジュール]** をクリックすると、このオプションを変更できます。  
  
 **[スケジュール]**  
 SQL Server エージェントの復元ジョブに関連するパラメーターを変更します。  
  
 **[このジョブを無効にする]**  
 セカンダリ データベースへの復元操作を中断します。  
  
## <a name="see-also"></a>参照  
 [SQL Server データベースのバックアップと復元](../backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [ログ配布について &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
