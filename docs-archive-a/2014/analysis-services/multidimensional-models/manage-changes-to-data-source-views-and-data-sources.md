---
title: データソースビューおよびデータソースへの変更の管理 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- modifying data sources
- modifying data source views
- data source views [Analysis Services], schema updates
- data sources [Analysis Services], schema updates
ms.assetid: 928c9f63-365a-43fd-9bbd-78828cc7e54d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f558ce6aaf9e57576d5773322352d33b81a3392
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714649"
---
# <a name="manage-changes-to-data-source-views-and-data-sources"></a>データ ソース ビューおよびデータ ソースへの変更の管理
  スキーマ生成ウィザードが再実行されると、元の生成に使用されたものと同じデータ ソースとデータ ソース ビューが再び使用されます。 データ ソースまたはデータ ソース ビューを追加しても、ウィザードでは使用されません。 最初の生成後に元のデータ ソースまたはデータ ソース ビューを削除した場合は、最初からウィザードを実行する必要があります。 ウィザードで以前使用した設定もすべて削除されます。 削除されたデータ ソースまたはデータ ソース ビューにバインドされていた、基になるデータベースの既存のオブジェクトは、次にスキーマ生成ウィザードを実行したとき、ユーザーが作成したオブジェクトとして取り扱われます。  
  
 データ ソース ビューに、基になるデータベースの生成時の実際の状態が反映されていないと、スキーマ生成ウィザードではサブジェクト領域データベースのスキーマを生成するときにエラーが発生する場合があります。 たとえば、データ ソース ビューで列のデータ型が **int**に指定されているときに、この列のデータ型が実際には **string**である場合、スキーマ生成ウィザードではデータ ソース ビューに合わせて外部キーのデータ型を **INT** に設定します。リレーションシップを作成すると、実際のデータ型が **string**であるため、処理は失敗します。  
  
 一方、データ ソース接続文字列を以前の生成後に別のデータベースに変更した場合は、エラーは発生しません。 この場合は新しいデータベースが使用され、以前のデータベースには変更は行われません。  
  
## <a name="see-also"></a>参照  
 [増分生成の理解](understanding-incremental-generation.md)  
  
  
