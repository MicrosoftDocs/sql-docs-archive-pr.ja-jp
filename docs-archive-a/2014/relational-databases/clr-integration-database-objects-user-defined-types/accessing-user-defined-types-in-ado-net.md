---
title: ADO.NET | でのユーザー定義型へのアクセスMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- ADO.NET [CLR integration]
- UDTs [CLR integration], ADO.NET
- user-defined types [CLR integration], ADO.NET
ms.assetid: 4b0d876c-8066-490e-8e18-327c0e942b19
author: rothja
ms.author: jroth
ms.openlocfilehash: a94e333ad743ed07dff6b973ebfe227312a1cab2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643408"
---
# <a name="accessing-user-defined-types-in-adonet"></a>ADO.NET でのユーザー定義型へのアクセス
  ユーザー定義型 (Udt) は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 検証可能なコードを生成する .NET Framework 共通言語ランタイム (CLR) でサポートされている言語のいずれかを使用して記述されます。 サポートされる言語には、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# や [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic などがあります。 UDT では、オブジェクトやカスタム データ構造を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに格納できます。 データは、.NET Framework のクラスまたは構造体のパブリック メンバーとして公開され、動作は .NET Framework のクラスまたは構造体のメソッドによって定義されます。 UDT は、テーブルの列定義、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチの変数、または [!INCLUDE[tsql](../../includes/tsql-md.md)] 関数やストアド プロシージャの引数として使用することができます。  
  
 ADO.NET では、`System.Data.SqlClient` プロバイダーにより次の形態で UDT が公開されます。  
  
-   `System.Data.SqlClient.SqlDataReader` によりオブジェクトとして。  
  
-   `SqlDataReader` により生のバイト列として。  
  
-   `System.Data.SqlClient.SqlParameter` オブジェクトのパラメーターとして。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [UDT データの取得](accessing-user-defined-types-retrieving-udt-data.md)  
 UDT データを取得する方法とパラメーターを指定する方法について説明します。  
  
 [データ アダプターによる UDT 列の更新](accessing-user-defined-types-updating-udt-columns-with-dataadapters.md)  
 `DataSets` 内の UDT を操作する方法と `DataAdapters` を使用して UDT データを更新する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [CLR ユーザー定義型](clr-user-defined-types.md)  
  
  
