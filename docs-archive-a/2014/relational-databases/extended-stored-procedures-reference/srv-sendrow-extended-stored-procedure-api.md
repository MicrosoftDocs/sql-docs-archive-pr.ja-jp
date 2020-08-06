---
title: srv_sendrow (拡張ストアド プロシージャ API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
api_name:
- srv_sendrow
api_location:
- opends60.dll
topic_type:
- apiref
dev_langs:
- C++
helpviewer_keywords:
- srv_sendrow
ms.assetid: a08f608a-10e6-4bff-9b48-0d02e8026cdb
author: rothja
ms.author: jroth
ms.openlocfilehash: df40348b8792a70f84719abfb42152fda9487e6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743233"
---
# <a name="srv_sendrow-extended-stored-procedure-api"></a>srv_sendrow (拡張ストアド プロシージャ API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]代わりに CLR Integration をご使用ください。  
  
 クライアントに 1 行のデータを送信します。  
  
## <a name="syntax"></a>構文  
  
```  
  
int srv_sendrow ( SRV_PROC *  
srvproc   
);  
  
```  
  
## <a name="arguments"></a>引数  
 *srvproc*  
 特定のクライアント接続のためのハンドル (この場合は、言語要求を受け取るハンドル) である SRV_PROC 構造体を指すポインターです。 この構造体には、アプリケーションとクライアントの間の通信やデータを管理するために、拡張ストアド プロシージャ API ライブラリで使用する情報が格納されます。  
  
## <a name="returns"></a>戻り値  
 SUCCEED または FAIL。  
  
## <a name="remarks"></a>解説  
 **srv_sendrow** 関数は、クライアントに送信される各行につき 1 回呼び出されます。 **srv_sendmsg**、**srv_status**、または **srv_senddone** を使用してメッセージ、状態値、または完了状態を送信する前に、すべての行をクライアントに送信しておく必要があります。  
  
 **srv_describe** によってすべての列を定義していない行を送信すると、拡張ストアド プロシージャ API アプリケーションで情報エラー メッセージが生成され、クライアントに FAIL が返されます。 この場合、その行は送信されません。  
  
> [!NOTE]  
>  拡張ストアド プロシージャ API ではクライアントへの計算行の送信はサポートされません。 また、`ntext` 型、`text` 型、または `image` 型のデータを格納している行をクライアントに送信した場合、テキスト ポインターおよびテキスト タイムスタンプは含まれません。  
  
> [!IMPORTANT]  
>  拡張ストアド プロシージャのソース コードを十分に確認し、コンパイル済み DLL を、運用サーバーにインストールする前にテストする必要があります。 セキュリティの確認およびテストについて詳しくは、[Microsoft の Web サイト](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)をご覧ください。  
  
## <a name="see-also"></a>参照  
 [srv_describe &#40;拡張ストアド プロシージャ API&#41;](srv-describe-extended-stored-procedure-api.md)  
  
  
