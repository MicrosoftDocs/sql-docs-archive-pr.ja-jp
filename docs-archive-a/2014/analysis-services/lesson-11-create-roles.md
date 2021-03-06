---
title: 'レッスン 12: ロールの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 984face4-00fc-46d3-8ae1-9755bf737bdf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 962cd19726a5404de81e20a2209b25b9cc277e21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631295"
---
# <a name="lesson-12-create-roles"></a>レッスン 12:ロールの作成
  このレッスンでは、ロールを作成します。 ロールを使用すると、ロール メンバーである Windows ユーザーのみにアクセスを制限することで、モデル データベース オブジェクトとデータにセキュリティを提供できます。 各ロールには､1 つの許可 (なし､読み取り､読み取りと処理､処理､管理者のいずれか) のみ定義します｡ モデルのロールは、モデルの作成時に [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の [ロール マネージャー] ダイアログ ボックスを使用して定義できます。 モデルを配置した後は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]を使用してロールを管理できます。 詳細については、「[ロール (SSAS テーブル)](tabular-models/roles-ssas-tabular.md)」 を参照してください。  
  
> [!NOTE]  
>  このチュートリアルでは､ロールの作成は必須のレッスンではありません｡ 既定では､現在のログインに使用したアカウントがモデルの管理者権限を保有します｡ ただし、組織内の他のユーザーがレポート クライアント アプリケーションを使用してモデルを参照できるようにするには、読み取り権限を持ったロールを少なくとも 1 つ作成し、それらのユーザーをメンバーとして追加する必要があります。  
  
 3 つのルールを作成します｡  
  
-   Sales Manager-このロールには、すべてのモデルオブジェクトとデータに対する読み取り権限を付与する組織内のユーザーを含めることができます。  
  
-   販売アナリストの米国-このロールには、米国での売上に関連するデータのみを参照できるようにする組織内のユーザーを含めることができます (米国)。 このロールに対しては、DAX 式を使用して *行フィルター*を定義することにより、メンバーが米国のデータのみを参照できるように制限します。  
  
-   管理者-このロールには、管理者権限を付与するユーザーを含めることができます。これにより、モデルデータベースに対する管理タスクを実行するための無制限のアクセス権と権限が許可されます。  
  
 社内の Windows ユーザー アカウントとグループ アカウントは一意であるため､特定のアカウントをメンバーに追加できます｡ しかし、このチュートリアルでは、メンバーを空白のままにすることもできます。 各ロールの影響は、後の「レッスン 12: Excel での分析」でもテストできます。  
  
 このレッスンの推定所要時間: **15 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン「 [レッスン 11: パーティションの作成](lesson-10-create-partitions.md)」を完了している必要があります。  
  
## <a name="create-roles"></a>ロールの作成  
  
#### <a name="to-create-a-sales-manager-user-role"></a>Sales Manager ユーザー ロールを作成する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[ロール]** をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
     "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales Manager` ます。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。  
  
5.  任意: **[メンバー]** タブをクリックし、**[追加]** をクリックします。  
  
6.  **Select Users また Groups** ダイアログ ボックスでこのロールに含める社内 Windows ユーザーまたはグループを入力します｡  
  
7.  選択内容を確認し、[ **OK** ] をクリックします。  
  
#### <a name="to-create-a-sales-analyst-us-user-role"></a>Sales Analyst US ユーザー ロールを作成する  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で **[モデル]** メニューをクリックし、 **[ロール]** をクリックします。  
  
2.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
     "なし" 権限を設定された新しいロールがリストに追加されます。  
  
3.  新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales US` ます。  
  
4.  **[権限]** 列で、ドロップダウン リストをクリックし、**[読み取り]** 権限を選択します。  
  
5.  行フィルターをクリックし、 **Geography** テーブルに対してのみ、[DAX フィルター] 列に次の式を入力します。  
  
     `=Geography[Country Region Code] = "US"`  
  
     Row Filter 式の結果は ブール値 (真/偽) をとる必要があります｡ この数式では、国の地域コード値が "US" である行のみがユーザーに表示されるように指定しています。  
  
     数式の入力が終了したら、Enter キーを押します。  
  
6.  任意: **[メンバー]** タブをクリックし、**[追加]** をクリックします。  
  
7.  **Select Users また Groups** ダイアログ ボックスでこのロールに含める社内 Windows ユーザーまたはグループを入力します｡  
  
8.  選択内容を確認し、[ **OK** ] をクリックします。  
  
#### <a name="to-create-an-administrator-role"></a>Administrator ロールを作成するには  
  
1.  **[ロール マネージャー]** ダイアログ ボックスで **[新規]** をクリックします。  
  
2.  新しいロールをクリックし、[**名前**] 列でロールの名前をに変更し `Internet Sales Administrator` ます。  
  
3.  **[権限]** 列で、ドロップダウン リストをクリックし、 **[管理者]** 権限を選択します。  
  
4.  **[メンバー]** タブをクリックし、 **[追加]** をクリックします。  
  
5.  (省略可能) **[ユーザーまたはグループの選択]** ダイアログ ボックスで、ロールに含める組織の Windows ユーザーまたはグループを入力します。  
  
6.  選択内容を確認し、[ **OK** ] をクリックします。  
  
## <a name="next-steps"></a>次の手順  
 このチュートリアルを続行するには、次のレッスン「 [レッスン 13: Excel での分析](lesson-12-analyze-in-excel.md)」に進んでください。  
  
  
