---
title: Database Mail XPs サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Database Mail XPs option
- Database Mail [SQL Server], enabling
ms.assetid: e22c4e63-1792-473b-af11-14a7931ca9ed
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 33ee15e862e0992f39373ec30275040c4fcacc0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642282"
---
# <a name="database-mail-xps-server-configuration-option"></a>Database Mail XPs サーバー構成オプション
  **Database Mail XPs** オプションを使用して、サーバーのデータベース メールを有効にします。 指定できる値は、  
  
-   **0** : データベース メールが使用できないことを示します (既定値)。  
  
-   **1** : データベース メールが使用できることを示します。  
  
 この設定は、サーバーを停止して再起動しなくてもすぐに有効になります。  
  
 データベース メールを使用するには、データベース メールを有効にしてから、データベース メールのホスト データベースを構成する必要があります。  
  
 **データベース メール構成ウィザード** を使用してデータベース メールを構成すると、 **msdb** データベースのデータベース メール拡張ストアド プロシージャが有効になります。 **データベース メール構成ウィザード**を使用する場合、以下の例の **sp_configure** を使用する必要はありません。  
  
 **Database Mail XPs** オプションを 0 に設定すると、データベース メールは開始されません。 データベース メールが実行されている場合にこのオプションを 0 に設定すると、 **DatabaseMailExeMinimumLifeTime** オプションで設定したアイドル状態の時間が続くまで、データベース メールは継続して実行され、メールが送信されます。  
  
## <a name="examples"></a>例  
 次の例では、データベース メール拡張ストアド プロシージャが有効になります。  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Database Mail XPs', 1;  
GO  
RECONFIGURE  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース メール](../../relational-databases/database-mail/database-mail.md)  
  
  
