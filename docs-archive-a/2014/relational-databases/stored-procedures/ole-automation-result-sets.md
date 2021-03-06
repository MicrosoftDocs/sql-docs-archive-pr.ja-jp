---
title: OLE オートメーションの結果セット | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: conceptual
helpviewer_keywords:
- data types [SQL Server], OLE Automation
- two-dimensional arrays
- one-dimensional arrays
- result sets [SQL Server], OLE Automation
- OLE Automation [SQL Server], result sets
- arrays [SQL Server]
ms.assetid: b2f99e33-2303-427c-94b9-9d55f8e2a6ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: f7c9bdc4d51d989db2d4d676b29e0824c0e5b59a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646127"
---
# <a name="ole-automation-result-sets"></a>OLE オートメーションの結果セット
  OLE オートメーションのプロパティまたはメソッドがデータを 1 次元か 2 次元の配列で返す場合、その配列は、次のように結果セットとしてクライアントに返されます。  
  
-   1 次元の配列の場合は、配列内の要素数と同数の列を持つ 1 行の結果セットとしてクライアントに返されます。 たとえば、array(10) は 10 個の列から成る 1 つの行として返されます。  
  
-   2 次元の配列の場合は、最初の次元の配列の要素数を列数とし、2 番目の次元の配列の要素数を行数とした結果セットとしてクライアントに返します。 たとえば、array(2,3) は 2 列、3 行の結果セットとして返されます。  
  
 プロパティやメソッドの戻り値が配列の場合、sp_OAGetProperty または sp_OAMethod が結果セットをクライアントに返します。 メソッドの出力パラメーターを配列にすることはできません。これらのプロシージャは、配列内のすべてのデータ値をスキャンし、結果セットのそれぞれの列に使用する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の適切なデータ型とデータ長を決定します。 これらのプロシージャは必要なデータ型とデータ長を使用して、特定の列内のすべてのデータ値を表現します。  
  
 列内のすべてのデータ値が同じデータ型を共有する場合は、そのデータ型を列全体で使用します。 ある列のデータ値のデータ型が異なる場合、列全体に適用されるデータ型は次の表に基づいて選択されます。 次の表を使用するには、左側の行の軸と一番上の列の軸からデータ型を 1 つずつ選択します。 行と列の交差部分が結果セット列のデータ型を示しています。  
  
||||||||  
|-|-|-|-|-|-|-|  
||`int`|`float`|`money`|`datetime`|`varchar`|`nvarchar`|  
|`int`|`int`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`float`|`float`|`float`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`money`|`money`|`money`|`money`|`varchar`|`varchar`|`nvarchar`|  
|`datetime`|`varchar`|`varchar`|`varchar`|`datetime`|`varchar`|`nvarchar`|  
|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`varchar`|`nvarchar`|  
|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|`nvarchar`|  
  
## <a name="related-content"></a>関連コンテンツ  
 [OLE オートメーション ストアド プロシージャ &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/ole-automation-stored-procedures-transact-sql)  
  
 [Ole Automation Procedures サーバー構成オプション](../../database-engine/configure-windows/ole-automation-procedures-server-configuration-option.md)  
  
  
