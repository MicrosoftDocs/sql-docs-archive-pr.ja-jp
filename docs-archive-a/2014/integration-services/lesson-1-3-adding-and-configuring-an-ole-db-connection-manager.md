---
title: '手順 3: OLE DB 接続マネージャーの追加と構成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: e7b74cba-a0e5-4478-af12-3f81b9484e9e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3bc4c885ce6c39c72031dd3b528a769cd47ac8f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641105"
---
# <a name="step-3-adding-and-configuring-an-ole-db-connection-manager"></a>手順 3:OLE DB 接続マネージャーの追加と構成
  前の実習では、データ ソースに接続するためのフラット ファイル接続マネージャーを追加しました。次は、データの変換先に接続するための OLE DB 接続マネージャーを追加します。 パッケージに OLE DB 接続マネージャーを追加すれば、OLE DB 対応のデータ ソースからデータを抽出したり、OLE DB 対応のデータ ソースへデータを読み込んだりできるようになります。 OLE DB 接続マネージャーでは、接続に必要なサーバー、認証方法、既定のデータベースを指定できます。  
  
 このレッスンでは、Windows 認証を使用して **AdventureWorksDB2012**のローカル インスタンスに接続する OLE DB 接続マネージャーを作成します。 参照変換や OLE DB 変換先など、このチュートリアルで後ほど作成するその他のコンポーネントも、ここで作成する OLE DB 接続マネージャーを参照します。  
  
### <a name="to-add-and-configure-an-ole-db-connection-manager-to-the-ssis-package"></a>SSIS パッケージに OLE DB 接続マネージャーを追加して構成するには  
  
1.  **[接続マネージャー]** 領域内を右クリックし、 **[新しい OLE DB 接続]** をクリックします。  
  
2.  **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスで、 **[新規作成]** をクリックします。  
  
3.  **[サーバー名]** に「 **localhost**」と入力します。  
  
     サーバー名に localhost という名前を使用すると、接続マネージャーは、ローカル コンピューター上の [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] の既定のインスタンスに接続します。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のリモート インスタンスを使用するには、localhost ではなく、接続先のサーバー名を指定します。  
  
4.  **[サーバーにログオンする]** で、 **[Windows 認証を使用する]** が選択されていることを確認します。  
  
5.  [**データベースへの接続**] グループの **[データベース名の選択または入力**] ボックスに、「」と入力するか、またはを選択し `AdventureWorksDW2012` ます。  
  
6.  **[接続テスト]** をクリックし、指定した接続設定が有効であることを確認します。  
  
7.  **[OK]** をクリックします。  
  
8.  **[OK]** をクリックします。  
  
9. **[OLE DB 接続マネージャーの構成]** ダイアログ ボックスの **[データ接続]** ペインで、 **localhost.AdventureWorksDW2012** が選択されていることを確認します。  
  
10. **[OK]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 4:パッケージへのデータ フロー タスクの追加](lesson-1-4-adding-a-data-flow-task-to-the-package.md)  
  
## <a name="see-also"></a>参照  
 [OLE DB 接続マネージャー](connection-manager/ole-db-connection-manager.md)  
  
  
