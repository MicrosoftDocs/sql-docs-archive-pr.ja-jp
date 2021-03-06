---
title: 階層 (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e3e50e89-f85d-485b-a271-1e0550520212
author: minewiskan
ms.author: owend
ms.openlocfilehash: a50b014dd6096b0bfa66ff34389789fcd34efdae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712510"
---
# <a name="hierarchies-ssas-tabular"></a>階層 (SSAS テーブル)
  表形式モデルにおける階層は、1 つのテーブルの 2 つ以上の列間の関係を定義するメタデータです。 階層は、あるレポート クライアント フィールドの一覧の他の列とは分けて表示できるため、クライアントのユーザーは簡単に移動し、レポートに含めることができます。  
  
 このトピックのセクション:  
  
-   [メリット](#bkmk_benefits)  
  
-   [階層の定義](#bkmk_define)  
  
-   [関連タスク](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> 利点  
 テーブルには明確な規則性のない特殊な列名を持つ数十または数百の列が含まれる場合があります。 そのため、レポート クライアント フィールドの一覧での表示が無秩序になり、ユーザーがレポート内のデータを見つけたりレポートにデータを含めたりするのが難しくなることがあります。 階層では、複雑なデータ構造を単純で直感的な形式で表示できます。  
  
 たとえば、日付テーブルにカレンダー階層を作成できます。 カレンダーの年が最上位の親レベルとして使用され、子レベルとして月、週、日が含まれます (カレンダーの年 -> 月 -> 週 -> 日)。 この階層により、カレンダーの年から日までの論理関係が示されます。 クライアント ユーザーはフィールドの一覧からカレンダー年度を選択して、ピボットテーブルにレベルをすべて含めたり、階層を展開してピボットテーブルに含める特定のレベルだけを選択したりできます。  
  
 ある階層の各レベルは、あるテーブルの 1 列の表現なので、そのレベルの名前を変更できます。 階層に限定されてはいません (テーブル モデルではどの列でも名前を変更できます) が、階層レベル名を変更すると、ユーザーがレポート内のレベルを見つけたり含めたりするのが容易になります。 レベル名を変更しても、参照先の列名は変更されません。レベルが識別しやすくなるだけです。 カレンダー年度階層の例に示す、データ ビューの日付テーブルでは、CalendarYear、CalendarMonth、CalendarWeek、および CalendarDay の各列の名前が Calendar Year、Month、Week、および Day に変更され、識別が容易になりました。 レベル名を変更することには、複数レポート間での一貫性という利点もあります。これは、ピボットテーブルやチャートなどでの読み取りやすさを高めるためにユーザーが列名を変更する必要がほとんどなくなるからです。  
  
 パースペクティブに階層を含めることができます。 パースペクティブを使用すると、ビジネス固有またはアプリケーション固有のビューポイントをモデルに対して的を絞って作成するための、表示可能なサブセットを定義できます。 たとえば、パースペクティブによって、ユーザー固有のレポート要件に必要なデータ アイテムのみが含まれる表示可能な一覧 (階層) を作成できます。 詳しくは、「 [パースペクティブ &#40;SSAS テーブル&#41;](perspectives-ssas-tabular.md)」をご覧ください。  
  
 階層は、セキュリティ メカニズムとして使用するためのものではなく、ユーザーの使用体験をより良いものにするためのツールとして使用するものです。 特定の階層のセキュリティはすべて、基になるモデルから継承されます。 階層では、ユーザーがアクセス権をまだ持っていないモデル オブジェクトにアクセスできません。 モデルのオブジェクトへのアクセスが階層を通じて提供されるようにするには、そのモデル データベースのセキュリティを解決しておく必要があります。 セキュリティ ロールを使用して、モデルのメタデータとデータをセキュリティ保護することができます。 詳しくは、「 [ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。  
  
##  <a name="defining-hierarchies"></a><a name="bkmk_define"></a>階層の定義  
 階層の作成と管理は、ダイアグラム ビューのモデル デザイナーを使用して行います。 階層の作成と管理は、データ ビューのモデル デザイナーではサポートされていません。 ダイアグラム ビューにモデル デザイナーを表示するには、 **[モデル]** メニューをクリックし、 **[モデル ビュー]** をポイントし、 **[ダイアグラム ビュー]** をクリックします。  
  
 階層を作成するには、親レベルとして指定する列を右クリックし、 **[階層の作成]** をクリックします。 (1 つのテーブル内で) 含める列の数に制限はなく、列をクリックして親レベルにドラッグすることで、子レベルとして後から追加することもできます。 複数の列を選択すると、カーディナリティに基づく順序で自動的に配置されます。 順序を変更するには、列 (レベル) をクリックして別の順序までドラッグするか、コンテキスト メニューにある上下の移動コントロールを使用します。 ある列を子レベルとして追加するとき、その列を親レベルにドラッグ アンド ドロップすることで、自動検出機能を使用できます。  
  
 1 つの列を複数の階層に表示することができます。 階層にメジャーや KPI などの非列オブジェクトを含めることはできません。 階層は単一のテーブルの列のみを基にして作成することができます。 1 つ以上の列と共に 1 つのメジャーを複数選択するか、または複数のテーブルから複数の列を選択した場合、コンテキスト メニューの **[階層の作成]** は無効になります。 異なるテーブルの列を追加するには、RELATED DAX 関数を使用して、関連するテーブル内の列を参照する計算列を追加します。 この関数では、 `=RELATED(TableName[ColumnName])`という構文を使用します。 関数の詳細については、「RELATED 関数」を参照してください。  
  
 既定では、新しい階層は hierarchy1、hierarchy 2、... のように名前が付けられます。親子関係の特性を反映するような階層名に変更して、ユーザーにとって識別しやすい名前にする必要があります。  
  
 階層の作成が完了したら、Excel で分析機能を使用して、階層の有効性をテストできます。 詳しくは、後の「 [Excel で分析 &#40;SSAS テーブル&#41;](analyze-in-excel-ssas-tabular.md)で [ロール マネージャー] ダイアログ ボックスを使用してロールを定義するテーブル モデル作成者向けです。  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> 関連タスク  
  
|タスク|説明|  
|----------|-----------------|  
|[階層の作成および管理 &#40;SSAS テーブル&#41;](hierarchies-ssas-tabular.md)|ダイアグラム ビューのモデル デザイナーを使用して階層の作成と管理を行う方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [SSAS 表形式&#41;&#40;テーブルモデルデザイナー](../tabular-model-designer-ssas-tabular.md)   
 [SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md)   
 [ロール (SSAS テーブル)](roles-ssas-tabular.md)  
  
  
