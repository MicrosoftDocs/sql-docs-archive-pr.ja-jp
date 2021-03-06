---
title: 'タスク 12: ナレッジの検出 (ナレッジ検出) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: dd80a8e6-1e41-4c49-9898-02b1d2505a10
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2dee66f94f1df609701f92d591f2c31863702465
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714886"
---
# <a name="task-12-discovering-knowledge-knowledge-discovery"></a>タスク 12: ナレッジを検出する (ナレッジ検出)
  このタスクでは、 **SUPPLIER ID**および**supplier Name**ドメインで**ナレッジ検出**アクティビティを実行します。 このシナリオでは、ナレッジ検出プロセスにより主にこれら 2 つのドメインの値をインポートします。  
  
 このチュートリアルでは、ナレッジ ベースを最初から作成しました。 さらに、ナレッジ検出アクティビティを実行してナレッジ ベースを作成することができます。 メインページで [**ナレッジベースの作成**] をクリックすると、DQS クライアントは、アクティビティに対して選択された**ドメイン管理**アクティビティを含むページに移動します。 **アクティビティ**を**ナレッジ検出**に変更し、次のページでナレッジ検出プロセスの一部としてドメインを作成できます。 詳細については、「[ナレッジ検出の実行](https://msdn.microsoft.com/library/hh510398.aspx)」を参照してください。  
  
1.  DQS クライアントのメインページの [**最近使用したナレッジベース**] セクションで、[**サプライヤー** ] ナレッジベースの横に**ある右矢印**をクリックし、[**ナレッジ検出**] をクリックします。 または、[**ナレッジベースを開く**] をクリックし、**ナレッジベースの一覧**から [**仕入先**] を選択して、[**ナレッジ検出**] を**アクティビティ**として選択し、[**次へ**] をクリックします。  
  
     ![メイン ページでの [ナレッジ検出] メニュー](../../2014/tutorials/media/et-discoveringknowledge-01.jpg "メイン ページでの [ナレッジ検出] メニュー")  
  
2.  **データソース**として**Excel ファイル**を選択します。  
  
3.  [**参照**] をクリックし、[ **Suppliers.xls**] をクリックして、[**開く**] をクリックします。  
  
4.  **ワークシート**の**検出のためのサプライヤー**を選択します。  
  
5.  [**マッピング**] セクションで、**ドロップダウンリスト**を使用して、仕入先の列を**Excel**ファイル**から supplier** **ID** **ドメインおよび supplier name 列****にマップし**ます。 Excel ファイルには、 **SUPPLIER ID**および**supplier Name**ドメインのサンプルデータが含まれています。 検出プロセスでは、値を検出するドメインを選択できます。 このページでドメインを作成し、これらのドメインにソース列をマップできます。 ドメイン管理アクティビティ中にドメインを作成する代わりに、ナレッジ検出アクティビティ中にドメインを作成することは一般的でありません。  
  
     ![検出プロセスの [マップ] ページ](../../2014/tutorials/media/et-discoveringknowledge-02.jpg "検出プロセスの [マップ] ページ")  
  
6.  [**次へ**] をクリックして、[**検出**] ページに移動します。  
  
7.  [**検出**] ページで、[**開始**] をクリックして検出プロセスを開始します。 検出は、 **Suppliers.xls**ファイルの列の**仕入****先名と仕入先名**に対して実行されます。 **SUPPLIER ID**および**supplier Name**ドメインには、検出から得られたナレッジが設定されている必要があります。  
  
     ![検出プロセスの [検出] ページ](../../2014/tutorials/media/et-discoveringknowledge-03.jpg "検出プロセスの [検出] ページ")  
  
8.  分析が完了したら、ページの下部にある [**プロファイラー] タブ**で**ソースの統計**を確認します。 合計20個の値 (**仕入****先名と仕入先名****の値) を**含む10個の新しいレコードが検出されたことに注意してください。 さらに、これらの値のうちいくつが、新しい値、一意の値、新しい一意の値、および有効な値であるかがわかります。 右側のリスト ボックスには、検出プロセスに使用された各ドメインの詳細が表示されます。 [完全] 列のステータス バーにマウス ポインターを合わせると、ソースの列に不足値があるかどうかを表示できます。  
  
     ![ナレッジ検出の結果](../../2014/tutorials/media/et-discoveringknowledge-04.jpg "ナレッジ検出の結果")  
  
9. [**次へ**] をクリックして、[**ドメイン値の管理**] ページに切り替えます。  
  
10. [**ドメイン値の管理**] ページで、ドメインの一覧から [ **Supplier Name** Domain] をクリックします。  
  
11. 右側のウィンドウで、[ **Lazy Country Storex** (最後に ' x ' に注意してください)] を右クリックし、[ **lazy country Store**] を選択します。 DQS により、ドメインに対するスペル チェッカーの実行後、この変更内容が提案されます。 既定では、作成するドメインに対するスペル チェックが有効になっています。  
  
     ![適切な仕入先名 - Lazy Country Store](../../2014/tutorials/media/et-discoveringknowledge-05.jpg "適切な仕入先名 - Lazy Country Store")  
  
12. [ドメイン値] ボックスの一覧で、lazy country **Storex**が修正として**レイジー country store**でエラー (赤い**X**マーク) として設定されていること、また、 **lazy country ストア**も有効な値として追加されていることを確認します。  
  
     ![ドメイン値と [次に修正] の値](../../2014/tutorials/media/et-discoveringknowledge-06.jpg "ドメイン値と [次に修正] の値")  
  
13. **[完了]** をクリックします。  
  
14. **SQL Server Data Quality Services** ] ダイアログボックスで、[**発行**] をクリックします。  
  
15. 成功メッセージボックスで [ **OK]** をクリックします。  
  
     これで、チュートリアルの最初のレッスンを完了しました。  
  
## <a name="next-step"></a>次の手順  
 [レッスン 2: Suppliers ナレッジ ベースを使用して仕入先データをクレンジングする](../../2014/tutorials/lesson-2-cleansing-supplier-data-using-the-suppliers-knowledge-base.md)  
  
  
