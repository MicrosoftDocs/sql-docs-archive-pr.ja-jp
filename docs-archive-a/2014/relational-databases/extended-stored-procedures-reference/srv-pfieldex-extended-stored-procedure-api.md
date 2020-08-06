---
title: srv_pfieldex (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_pfieldex
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_pfieldex
ms.assetid: d4e9a34b-b3a3-434f-8556-768bd20d145a
author: rothja
ms.author: jroth
ms.openlocfilehash: a474eafcb6b6d42161a7e67ce7f93636269c46c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633849"
---
# <a name="srv_pfieldex-extended-stored-procedure-api"></a>srv_pfieldex (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 要求された SRV_PROC フィールドを格納したデータへのポインターを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
void *srv_pfieldex(SRV_PROC *   
srvproc  
, int   
field  
, int *   
len  
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドルである SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
 *分野*  
 返す *srvproc* フィールドを指定します。  
  
|フィールド|説明|戻り値の型|  
|-----------|-----------------|------------------|  
|SRV_MSGLCID|現在のセッションのメッセージ LCID。|ULONG*|  
|SRV_INSTANCENAME|インスタンス名 (指定されている場合)。それ以外の場合は NULL を返します。|WCHAR*|  
  
 *len*  
 返される *field* 値の長さ (バイト単位) を格納した **int** 型変数を指すポインターです。 *len* が NULL の場合、長さは返されていません。 NULL が返されると、**len* は 0 に設定されます。  
  
## <a name="returns"></a>戻り値  
 *field* によってデータ型が決定されるデータを指すポインターです。 *len* または *srvproc* が NULL の場合は NULL が返されます。 *field* が不明の場合は NULL が返されます。 NULL が返されると、**len* は 0 に設定されます。  
  
> [!IMPORTANT]  
>  サーバーから返されるバッファーは読み取り専用にする必要があります。 そうでない場合、サーバーの状態が壊れることがあります。  
  
## <a name="remarks"></a>解説  
 **セキュリティに関する注意** 拡張ストアド プロシージャのソース コードを十分に確認し、コンパイルした DLL をテストしたうえで実稼働サーバーにインストールしてください。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
  
