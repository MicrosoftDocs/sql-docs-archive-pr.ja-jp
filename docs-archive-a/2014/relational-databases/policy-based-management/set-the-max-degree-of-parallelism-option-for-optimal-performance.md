---
title: 最適なパフォーマンスを実現するための max degree of parallelism オプションの設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: ec908006-67ae-4674-9a61-25ea741d6197
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3043a656cbe1ac1ec40f0d0a67b6eac057005af4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740849"
---
# <a name="set-the-max-degree-of-parallelism-option-for-optimal-performance"></a>最適なパフォーマンスを実現するための max degree of parallelism オプションの設定
  このルールでは、値の max degree of parallelism (MAXDOP) オプションが 8 より大きいかどうかを確認します。 このオプションを大きな値に設定すると、多くの場合、不要なリソース消費やパフォーマンスの低下が発生します。  
  
## <a name="best-practices-recommendations"></a>ベスト プラクティスと推奨事項  
 sp_configure を使用して max degree of parallelism オプションを 8 以下に設定してください。  
  
## <a name="for-more-information"></a>詳細情報  
 [サポート技術情報の資料 329204](https://go.microsoft.com/fwlink/?linkid=117786)  
  
 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)  
  
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
