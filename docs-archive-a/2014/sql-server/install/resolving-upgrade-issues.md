---
title: アップグレードに関する問題の解決 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- Upgrade Advisor [SQL Server], reference
- component issue resolution [Upgrade Advisor]
- resolving upgrade issues
- upgrade blocks [Upgrade Advisor]
- detecting upgrade issues
- finding upgrade issues
- Upgrade Advisor [SQL Server], blocking issues
- configurations preventing upgrading [Upgrade Advisor]
- locating upgrade issues
- blocking issues [Upgrade Advisor]
- issues preventing upgrading [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, reference
- analyzing system [Upgrade Advisor], resolving issues
- settings preventing upgrading [Upgrade Advisor]
- upgrade issue reference [Upgrade Advisor]
- identifying upgrade issues
- fixing upgrade issues [Upgrade Advisor]
ms.assetid: 113eb435-8d36-4ed6-9790-b5e4c14809c8
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: c00b08d40bc8c17013e6af19b5d11b0b7ad78c4b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645352"
---
# <a name="resolving-upgrade-issues"></a>アップグレードに関する問題とその対処方法
  このセクションのトピックでは、アップグレードに関連する検出可能な問題と、検出できずアップグレードまたはアップグレード後の動作に影響することが考えられる問題について説明します。 これらの問題は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] コンポーネントごとにまとめられています。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [アップグレードに関する最新の問題](../../../2014/sql-server/install/late-breaking-upgrade-issues.md)  
  
-   [データベース エンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md)  
  
-   [フルテキスト検索のアップグレードに関する問題](../../../2014/sql-server/install/full-text-search-upgrade-issues.md)  
  
-   [レプリケーションのアップグレードに関する問題](../../../2014/sql-server/install/replication-upgrade-issues.md)  
  
-   [アップグレードに関する問題を Reporting Services &#40;アップグレードアドバイザー&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
-   [SQL Server エージェントのアップグレードに関する問題](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
## <a name="issues-that-prevent-upgrading"></a>アップグレードを妨げる問題  
 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の構成または設定が原因で、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードできなくなる場合があります。 のインストール時にセットアップでこれらの問題が検出された場合 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、セットアップによってアップグレードプロセスが停止され、アップグレードアドバイザーを実行して、ブロックの問題を修正するように要求されます。  
  
### [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
 以下のタスクが[!INCLUDE[ssDE](../../includes/ssde-md.md)]のアップグレード レポートに表示された場合は、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] にアップグレードする前に必要な操作を実行する必要があります。  
  
-   [データベース ID 32767 をデタッチする](../../../2014/sql-server/install/detach-database-id-32767.md)  
  
-   [固定サーバー ロール名と一致するログイン名を変更する](../../../2014/sql-server/install/rename-logins-matching-fixed-server-role-names.md)  
  
-   [ユーザー sys の名前変更が必要](../../../2014/sql-server/install/rename-user-sys.md)  
  
-   [sp_rename を使用して重複するインデックス名を変更する](../../../2014/sql-server/install/use-sp-rename-to-rename-duplicate-index-name.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
