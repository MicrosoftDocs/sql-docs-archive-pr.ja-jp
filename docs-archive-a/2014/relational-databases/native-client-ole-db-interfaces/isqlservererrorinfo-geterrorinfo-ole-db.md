---
title: ISQLServerErrorInfo::GetErrorInfo (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- ISQLServerErrorInfo::GetErrorInfo (OLE DB)
topic_type:
- apiref
helpviewer_keywords:
- GetErrorInfo method
ms.assetid: 83265c9c-eaf9-41f0-9f73-b0ae0972f0d5
author: rothja
ms.author: jroth
ms.openlocfilehash: c3e325cd99276e04a178b89c19b233289edc09fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718129"
---
# <a name="isqlservererrorinfogeterrorinfo-ole-db"></a>ISQLServerErrorInfo::GetErrorInfo (OLE DB)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラーの詳細を格納している Native Client OLE DB プロバイダー SSERRORINFO 構造体へのポインターを返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
## <a name="syntax"></a>構文  
  
```  
  
   HRESULT GetErrorInfo(  
SSERRORINFO**ppSSErrorInfo,  
OLECHAR**ppErrorStrings);  
```  
  
## <a name="arguments"></a>引数  
 *ppSSErrorInfo*[out]  
 SSERRORINFO 構造体へのポインター。 メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppSSErrorInfo* 引数に NULL ポインターを設定します。  
  
 *ppErrorStrings*[out]  
 Unicode 文字列ポインターへのポインター。 メソッドが失敗するか、エラーに関連する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 情報がない場合、プロバイダーはメモリの割り当てを行わず、出力時に *ppErrorStrings* 引数に NULL ポインターを設定します。 **IMalloc::Free** メソッドを使用して *ppErrorStrings* 引数を解放すると、メモリがブロック単位で割り当てられているので、結果の SSERRORINFO 構造体の 3 つの各文字列メンバーが解放されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 S_OK  
 メソッドが成功しました。  
  
 E_INVALIDARG  
 *ppSSErrorInfo* または *ppErrorStrings* 引数のいずれかが NULL でした。  
  
 E_OUTOFMEMORY  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、要求を完了するために必要なメモリを割り当てることができませんでした。  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、コンシューマーによって渡されたポインターによって返される SSERRORINFO および OLECHAR 文字列にメモリを割り当てます。 コンシューマーはエラー データにアクセスする必要がなくなった時点で、**IMalloc::Free** メソッドを使用してこのメモリの割り当てを解除する必要があります。  
  
 SSERRORINFO 構造体は、次のように定義されています。  
  
```  
typedef struct tagSSErrorInfo  
   {  
   LPOLESTR pwszMessage;  
   LPOLESTR pwszServer;  
   LPOLESTR pwszProcedure;  
   LONG lNative;  
   BYTE bState;  
   BYTE bClass;  
   WORD wLineNumber;  
   }  
SSERRORINFO;  
```  
  
|メンバー|説明|  
|------------|-----------------|  
|*pwszMessage*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー メッセージ。 このメッセージは、**IErrorInfo::GetDescription** メソッドにより返されます。|  
|*pwszServer*|エラーが発生した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前。|  
|*pwszProcedure*|エラーがストアド プロシージャ内で発生している場合は、エラーが発生したストアド プロシージャの名前です。それ以外の場合は、空文字列になります。|  
|*lNative*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー番号。 このエラー番号は、**ISQLErrorInfo::GetSQLInfo** メソッドの *plNativeError* パラメーターに返されるものと同じになります。|  
|*bState*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの状態。|  
|*bClass*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エラーの重大度。|  
|*wLineNumber*|該当する場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャのエラー メッセージを生成した行です。 プロシージャが関係していない場合は、既定値 1 が使用されます。|  
  
 構造体内のポインターは、*ppErrorStrings* 引数に返される文字列内のアドレスを指します。  
  
## <a name="see-also"></a>参照  
 [ISQLServerErrorInfo &#40;OLE DB&#41;](../../database-engine/dev-guide/isqlservererrorinfo-ole-db.md)   
 [RAISERROR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/raiserror-transact-sql)  
  
  
