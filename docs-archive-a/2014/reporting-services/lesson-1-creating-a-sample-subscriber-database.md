---
title: 'レッスン 1: サンプル サブスクライバー データベースの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 47a882b7-efe5-4ee6-bef4-06118eb56903
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ee49f0858b28c0c4b00fd391b0db7b4d2c54b16
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742910"
---
# <a name="lesson-1-creating-a-sample-subscriber-database"></a>レッスン 1 : サンプル サブスクライバー データベースの作成
  データ ドリブン サブスクリプションを定義するには、その前に、サブスクリプション データを提供するデータ ソースを用意する必要があります。 ここでは、このチュートリアル用のサブスクリプション データを格納する簡単なデータベースを作成します。 後でサブスクリプションを処理する際、このデータがレポート サーバーにより取得され、レポート出力、配信オプション、およびレポート表示形式のカスタマイズに使用されます。  
  
 このレッスンでは、を使用してデータベースを作成することを前提としてい [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] ます。  
  
### <a name="to-create-a-sample-subscriber-database"></a>サンプル サブスクライバー データベースを作成するには  
  
1.  [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] を起動し、[!INCLUDE[ssDE](../includes/ssde-md.md)]への接続を開きます。  
  
2.  [データベース] を右クリックして **[新しいデータベース]** をクリックします。  
  
3.  [新しいデータベース] ダイアログボックスの [データベース名] に「*サブスクライバー*」と入力します。 [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
4.  ツール バーの **[新しいクエリ]** ボタンをクリックします。  
  
5.  次の [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントを空のクエリにコピーします。  
  
    ```  
    Use Subscribers  
    CREATE TABLE [dbo].[OrderInfo] (  
        [SubscriptionID] [int] NOT NULL PRIMARY KEY ,  
        [Order] [nvarchar] (20) NOT NULL,  
        [FileType] [bit],  
        [Format] [nvarchar] (20) NOT NULL ,  
    ) ON [PRIMARY]  
    GO  
  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('1', 'so43659', '1', 'IMAGE')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('2', 'so43664', '1', 'MHTML')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('3', 'so43668', '1', 'PDF')  
    INSERT INTO [dbo].[OrderInfo] (SubscriptionID, [Order], FileType, Format)   
    VALUES ('4', 'so71949', '1', 'Excel')  
    GO  
    ```  
  
6.  ツールバーの **[実行]** をクリックします。  
  
7.  SELECT ステートメントを使用して、3 行のデータがあることを確認します。 例: `select * from OrderInfo`  
  
## <a name="next-steps"></a>次の手順  
 以上の操作で、レポートを配信し、各サブスクライバーごとにレポート出力を変えるサブスクリプション データを作成できました。 次に、サブスクライバーに配信するレポートのデータ ソース プロパティを更新します。 データ ソース プロパティを更新する目的は、データ ドリブン サブスクリプション配信用のレポートを準備することです。 また、レポートのデザインを変更して、サブスクリプションがサブスクライバーのデータと共に使用するパラメーターを含めます。 [レッスン 2: レポートデータソースのプロパティの変更](lesson-2-modifying-the-report-data-source-properties.md)  
  
## <a name="see-also"></a>参照  
 [データ ドリブン サブスクリプションの作成 &#40;SSRS チュートリアル&#41;](create-a-data-driven-subscription-ssrs-tutorial.md)   
 [データベースを作成する](../relational-databases/databases/create-a-database.md)   
 [基本的なテーブル レポートの作成 (SSRS チュートリアル)](create-a-basic-table-report-ssrs-tutorial.md)  
  
  
