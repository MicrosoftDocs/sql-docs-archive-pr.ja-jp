---
title: レポートパラメーターの概念 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4b740362daea83b50a62f0b4453ce818ab21ace7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713850"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a>レポート パラメーターの概念 (レポート ビルダーおよび SSRS)
  関連するレポートをリンクさせたり、レポートの外観を制御したり、レポート データをフィルター選択したり、レポートの範囲を特定のユーザーまたは場所に絞り込んだりする目的で、レポートにはパラメーターを追加することができます。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 レポート パラメーターは次の方法で作成されます。  
  
-   自動: クエリ変数を含んだデータセット クエリを定義すると自動的に作成されます。 クエリ変数ごとに、同じ名前の対応するデータセット クエリ パラメーターおよびレポート パラメーターが作成されます。 クエリ パラメーターには、クエリ変数の参照のほか、ストアド プロシージャの入力パラメーターの参照を使用することができます。  
  
-   自動: クエリ パラメーターを含んだ共有データセットへの参照を追加すると自動的に作成されます。  
  
-   手動: レポート データ ペインでは、レポート パラメーターを手動で作成できます。 パラメーターは、レポート内の式に含めることのできる組み込みコレクションの 1 つです。 式はレポート定義の中で値を定義するために頻繁に使用されます。パラメーターを使用して、レポートの外観を制御したり、関連するサブレポート (またはパラメーターを使用する他のレポート) に値を渡したりすることができます。  
  
 詳細については、「 [レポート パラメーター (レポート ビルダーおよびレポート デザイナー)](report-parameters-report-builder-and-report-designer.md)にあります。  
  
 データがレポートに返される前や後にレポート データをフィルター処理する目的でパラメーターは頻繁に使用されます。 詳細については、「 [データのフィルター、グループ化、および並べ替え (レポート ビルダーおよび SSRS)](filter-group-and-sort-data-report-builder-and-ssrs.md)」を参照してください。  
  
 レポートをデザインするときは、レポート パラメーターはレポート定義に保存されます。 レポートをパブリッシュするときは、レポート パラメーターはレポート定義とは別に保存され管理されます。 レポート サーバーにレポートを保存した後、次のことを実行できます。  
  
-   レポート パラメーターの値を (レポート定義とは関係なく) レポート サーバー上で直接変更する。  
  
-   同じレポート定義へのリンクとして複数のリンク レポートを作成し、それぞれのリンク レポートに、レポート サーバー上で別々に管理できる一連のパラメーター値を割り当てる。  
  
 レポートのスナップショットや履歴、または、パブリッシュされたレポートに対するサブスクリプションを作成する予定がある場合は、レポート パラメーターが、レポートのデザイン要件にどのような影響を及ぼすかを理解する必要があります。  
  
## <a name="see-also"></a>参照  
 [レポート作成の概念 &#40;レポートビルダーと SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [レポート埋め込みデータセットと共有データセット &#40;レポートビルダーと SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [チュートリアル: レポートへのパラメーターの追加 &#40;レポート ビルダー&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  
