---
title: HumanResources.myTeam サンプル テーブル (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7d4e0cbbf42c2bdd25e3dd7c9577e4d0ec44549a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643345"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>HumanResources.myTeam サンプル テーブル (SQL Server)
  「 [一括データのインポートおよびエクスポート](bulk-import-and-export-of-data-sql-server.md) 」のコード例の大部分では、 **myTeam**という名前の特殊なテスト用テーブルが必要になります。 これらのコード例を実行する前に、 **データベースの** HumanResources **スキーマに** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] テーブルを作成する必要があります。  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] は [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]のサンプル データベースの 1 つです。  
  
 **myTeam** には、次の列が含まれています。  
  
|列|データ型|NULL 値の許容|説明|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|`smallint`|不可|行の主キー。 チーム メンバーの従業員 ID。|  
|**名前**|`nvarchar(50)`|不可|チーム メンバーの名前。|  
|**Title**|`nvarchar(50)`|Nullable|チームにおける従業員の肩書き。|  
|**バックグラウンド**|`nvarchar(50)`|不可|行が最後に更新された日時 (既定値)。|  
  
 **HumanResources.myTeam テーブルを作成するには**  
  
-   次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを使用します。  
  
    ```  
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
 **HumanResources.myTeam テーブルに行を設定するには**  
  
-   次の `INSERT` ステートメントでは、テーブルに 2 つの行を設定します。  
  
    ```  
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  これらのステートメントでは、4 番目の列 `Background`がスキップされます。 この行には既定値が設定されています。 この列をスキップすると、この `INSERT` ステートメントを実行した際に、この列が空欄のままになります。  
  
## <a name="see-also"></a>参照  
 [データの一括インポートと一括エクスポート &#40;SQL Server&#41;](bulk-import-and-export-of-data-sql-server.md)  
  
  
