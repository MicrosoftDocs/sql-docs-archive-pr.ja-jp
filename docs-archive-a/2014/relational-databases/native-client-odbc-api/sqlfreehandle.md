---
title: SQLFreeHandle |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLFreeHandle function
ms.assetid: d374e5c8-ed35-43bf-8dd6-c37e38d9b5f1
author: rothja
ms.author: jroth
ms.openlocfilehash: f51f031bec05715e0345507278113f4f16179a77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639478"
---
# <a name="sqlfreehandle"></a>SQLFreeHandle
  手動コミットモードでは、トランザクションが開いているステートメントハンドルで**Sqlfreehandle**を呼び出すと、データベースに対する保留中の変更がロールバックされます。 ステートメントハンドルで**Sqlfreehandle**を呼び出すと、開いているカーソルが常に閉じられ、保留中の結果は破棄され、ステートメントハンドルに関連付けられているすべてのリソースが解放されます。  
  
## <a name="see-also"></a>参照  
 [SQLFreeHandle 関数](https://go.microsoft.com/fwlink/?LinkId=59345)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
