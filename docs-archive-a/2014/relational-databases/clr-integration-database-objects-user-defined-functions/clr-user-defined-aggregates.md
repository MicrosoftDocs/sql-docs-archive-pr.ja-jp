---
title: CLR ユーザー定義集計 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
ms.openlocfilehash: d1ef5d07fe082d0eeb2c3484d6e99572d8fc80e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641695"
---
# <a name="clr-user-defined-aggregates"></a>CLR ユーザー定義集計
  集計関数は、値の集まりに対して計算を実行し、1 つの値を返します。 従来、で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `SUM` は、 `MAX` 入力スカラー値のセットに対して演算を実行し、そのセットから1つの集計値を生成するやなどの組み込み集計関数のみがサポートされていました。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR (共通言語ランタイム) と統合されたことにより、開発者はマネージド コードでカスタム集計関数を作成し、[!INCLUDE[tsql](../../includes/tsql-md.md)] や他のマネージド コードから作成した関数にアクセスできるようになりました。  
  
 次の表に、このセクションの各トピックの一覧を示します。  
  
 [CLR ユーザー定義集計の要件](clr-user-defined-aggregates-requirements.md)  
 CLR ユーザー定義集計関数の実装要件の概要について説明します。  
  
 [CLR ユーザー定義集計関数の呼び出し](clr-user-defined-aggregate-invoking-functions.md)  
 ユーザー定義集計を呼び出す方法について説明します。  
  
  
