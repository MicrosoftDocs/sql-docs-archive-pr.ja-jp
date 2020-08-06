---
title: Azure Storage への接続 (復元) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restore.connectstorage.f1
ms.assetid: c0b7d7c8-b878-4b7f-8120-d0c6917b583f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: dff9730d6592381b1c8e8a1cf7ee45ad7532a440
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645676"
---
# <a name="connect-to-azure-storage-restore"></a>Azure Storage への接続 (復元)
  このダイアログ ボックスを使用すると、Azure ストレージ アカウントのファイル ストレージを取得するために、Azure ストレージ アカウント情報への接続を指定できます。 必要な情報を指定した後、 **[接続]** をクリックして Azure Storage への接続を確立します。  
  
## <a name="azure-storage-account"></a>Azure Storage アカウント  
 **ストレージ アカウント**  
 使用する Azure ストレージ アカウントの名前を選択、入力、または貼り付けます。 ドロップダウン リストに、以前に使用したアカウントが表示されます。  
  
 **アカウント キー**  
 Azure ストレージ アカウントのアクセス キーを指定します。  
  
 **[安全なエンドポイントを使用する (HTTPS)]** チェック ボックス  
 Azure Storage に対してセキュリティで保護された接続を確立するには、このオプションを選択します (推奨)。  
  
 **[アカウント キーを保存する]** チェック ボックス  
 このストレージ アカウントのアクセス キーを SQL Server に記憶させる場合は、このチェック ボックスをオンにします。  
  
### <a name="sql-credential"></a>[SQL 資格情報]  
 **[既存の資格情報の選択]**  
 ストレージ アカウントおよびアカウント キー情報と一致する既存の SQL 資格情報を選択します。  
  
 **[新しい資格情報の作成]**  
 ストレージ アカウントとアカウント キー情報を使用して新しい資格情報を作成するには、このオプションを選択します。 **[資格情報名]** フィールドに新しい資格情報の名前を指定します。  
  
  
