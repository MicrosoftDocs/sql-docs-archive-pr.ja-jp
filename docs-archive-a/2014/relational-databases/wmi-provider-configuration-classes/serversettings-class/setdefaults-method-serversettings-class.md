---
title: SetDefaults メソッド (ServerSettings クラス) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ServerSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 76e4cfab-4b15-4da4-bb2f-8aac6f927f79
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 93dd2eee5a395d4d7463ebf9b85530fcf82d1888
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715113"
---
# <a name="setdefaults-method-serversettings-class"></a>SetDefaults メソッド (ServerSettings クラス)
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 既存のデータを上書きするオプションを使用して、のインスタンスのすべての既定値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 クライアントインスタンスを表す[Serversettings クラス](serversettings-class.md)オブジェクト [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---------------|-----------------|  
|*OverwriteAll*|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンス上の既存の値を上書きするかどうかを指定するブール値。既存のデータを上書きするには `true`、既存のデータを上書きしない場合は `false` を指定します。|  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 u`int32` 値。サービスが正常に変更された場合は 0、要求がサポートされない場合は 1 になります。それ以外の数値はエラーを示します。  
  
## <a name="remarks"></a>解説  
  
## <a name="see-also"></a>参照  
 [サーバーのネットワーク プロトコルと Net-Library の構成](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)  
  
  
