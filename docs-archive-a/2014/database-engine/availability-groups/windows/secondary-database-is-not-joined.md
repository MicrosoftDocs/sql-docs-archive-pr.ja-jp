---
title: セカンダリ データベースが参加していない | Microsoft Docs
ms.custom: ''
ms.date: 01/09/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.drp2joined.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 10817e5e-75fa-42dd-baa2-359bea3ad051
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 81275e85fd865924778f6d6f985e170a5bda9f9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740471"
---
# <a name="secondary-database-is-not-joined"></a>セカンダリ データベースが参加していない
    
## <a name="introduction"></a>はじめに  
  
|||  
|-|-|  
|**ポリシー名**|可用性データベースの参加状態|  
|**問題点**|セカンダリ データベースが参加していません。|  
|**カテゴリ**|**警告**|  
|**ファセット**|可用性データベース|  
  
## <a name="description"></a>説明  
 このポリシーは、セカンダリ データベース ("セカンダリ データベース レプリカ" とも呼ばれます) の参加状態をチェックします。 データセット レプリカが参加していない場合、ポリシーは通常とは異なる状態です。 それ以外の場合、ポリシーは正常な状態です。  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]のこのリリース向けに、TechNet Wiki の「 [Secondary database is not joined](https://go.microsoft.com/fwlink/p/?LinkId=220862) 」 (セカンダリ データベースが参加していない) に、考えられるエラーの原因および解決方法に関する情報が紹介されています。  
  
## <a name="possible-causes"></a>考えられる原因  
 このセカンダリ データベースは可用性グループに参加していません。 このセカンダリ データベースの構成が不完全です。  
  
## <a name="possible-solution"></a>考えられる解決方法  
 Transact-SQL、PowerShell、または SQL Server Management Studio を使用して、セカンダリ レプリカを可用性グループに参加させます。 セカンダリ レプリカを可用性グループに参加させる方法の詳細については、「 [可用性グループへのセカンダリ レプリカの参加 (SQL Server)](https://msdn.microsoft.com/library/ff878473\(en-us,SQL.110\).aspx)」をご覧ください。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn ダッシュボードの使用 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
