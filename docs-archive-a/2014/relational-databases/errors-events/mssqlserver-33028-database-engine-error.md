---
title: MSSQLSERVER_33028 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33028 (Database Engine error)
ms.assetid: c5cec0e4-0bcd-4907-826f-e7d835cfcb37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 555dcf0220793abc0e8af81b3f56867f9960c5f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640023"
---
# <a name="mssqlserver_33028"></a>MSSQLSERVER_33028
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|33028|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SEC_CRYPTOPROV_CANTOPENSESSION|  
|メッセージ テキスト|%S_MSG '%.*ls' のセッションを開くことができません。 プロバイダー エラー コード: %d。|  
  
## <a name="explanation"></a>説明  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、エラー メッセージに表示されている暗号化サービス プロバイダーを開くことができませんでした。 暗号化サービス プロバイダーは、表示されているエラー コードを返しました。 エラーの詳細については、暗号化サービス プロバイダーに問い合わせる必要があります。  
  
|エラー コード|説明|  
|----------------|-----------------|  
|0|正常終了しました。 エラーなし。|  
|1|失敗しました。 未定義のエラーまたは予期しないエラーが発生しました。 追加情報は入手できません。|  
|2|バッファーが不足しています。 暗号化サービス プロバイダー用の領域を割り当てることができませんでした。|  
|3|サポートされていません。 問題となる暗号化サービス プロバイダーが、このリリースではサポートされていません。 別の暗号化サービス プロバイダーを選択してください。|  
|4|Not Found. (見つかりませんでした。) 指定した暗号化サービス プロバイダーが存在しないか、ファイルにアクセスする承認を得ていません。|  
|5|承認エラーです。 資格情報の作成時に指定したパスワードまたはユーザー名が正しくないか、 資格情報が存在しない可能性があります。|  
|6|引数が無効です。 暗号化サービス プロバイダーに無効な引数が渡されました。|  
  
## <a name="user-action"></a>ユーザーの操作  
 エラーを解決するか、暗号化サービス プロバイダーに詳細を問い合わせてください。  
  
  
