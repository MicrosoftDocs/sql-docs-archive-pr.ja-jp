---
title: 警告デザイナーでのデータ警告の編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9906b33ae50d51733eaec1bf5c201c9f5b5d120e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719641"
---
# <a name="edit-a-data-alert-in-alert-designer"></a>警告デザイナーでのデータ警告の編集
  編集対象のデータ警告定義は、データ警告マネージャーから開きます。 警告の定義は、作成したユーザーのみが編集できます。 詳細については、「 [データ警告マネージャーでのデータ警告の管理](manage-my-data-alerts-in-data-alert-manager.md)」をご覧ください。

 次の図は、データ警告マネージャーでの、データ警告のショートカット メニューを示しています。

 ![[編集] をクリックしてデータ警告デザイナーを開く](media/rs-alertmanageriwopendesigner.gif "[編集] をクリックしてデータ警告デザイナーを開く")

 次の手順には、データ警告デザイナーで編集するためにデータ警告マネージャーから警告定義を開く手順が含まれます。

### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a>データ警告デザイナーでデータ警告定義を編集するには

1.  データ警告マネージャーで、編集するデータ警告定義を右クリックし、 **[編集]** をクリックします。

     データ警告デザイナーに警告定義が表示されます。

2.  ルール、スケジュール設定、および電子メールの設定を更新します。 詳細については、「 [データ警告デザイナー](../../2014/reporting-services/data-alert-designer.md) 」および「 [警告デザイナーでのデータ警告の作成](create-a-data-alert-in-data-alert-designer.md)」をご覧ください。

    > [!NOTE]
    >  別のデータ フィードを選択することはできません。 異なるデータ フィードを使用するには、新しいデータ警告定義を作成する必要があります。

3.  **[保存]** をクリックします。

    > [!NOTE]
    >  レポートが変更され、レポートから生成されたデータ フィードが変更されている場合、警告の定義が無効になっている可能性があります。 この状況が生じるのは、警告定義のルールで参照される列がレポートから削除された場合、列のデータ型が変更された場合、またはレポートが削除または移動された場合です。 無効な警告定義は開くことはできますが、基になるレポート データ フィードの現行バージョンに基づいて有効になるまでは再保存できません。 レポートからデータ フィードが生成される方法の詳細については、「[複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)」を参照してください。

## <a name="see-also"></a>参照
 [警告管理者がデータ警告を Reporting Services するためのデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)


