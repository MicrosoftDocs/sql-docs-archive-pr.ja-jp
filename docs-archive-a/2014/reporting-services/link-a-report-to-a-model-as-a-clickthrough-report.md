---
title: レポートをクリックスルーレポートとしてモデルにリンクする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb84f8036dbe5a1694628144f0b948452261ca75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632959"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a>レポートをクリックスルー レポートとしてモデルにリンクする
  クリックスルー レポートの既定のテンプレートを使用する代わりに、レポート ビルダーのレポートを作成し、それをレポート モデルの特定のエンティティにリンクすることができます。 レポートを閲覧しているユーザーがメイン レポート内の対話型データをクリックすると、このレポートがクリックスルー レポートとして表示されます。 レポートをエンティティにリンクするには、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート マネージャーを使用します。  
  
> [!IMPORTANT]  
>  レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。  
  
### <a name="to-start-report-manager-from-a-browser"></a>ブラウザーからレポート マネージャーを起動するには  
  
1.  [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 以降を開きます。  
  
2.  Web ブラウザーのアドレス バーに、レポート マネージャーの URL を入力します。 既定では、URL は http:// \<*ComputerName*> /レポートです。  
  
### <a name="to-create-a-customized-clickthrough-report"></a>カスタマイズされたクリックスルー レポートを作成するには  
  
1.  カスタマイズされたクリックスルー レポートを追加するレポート モデルに移動します。  
  
2.  レポート モデルをダブルクリックします。  
  
3.  **[クリックスルー]** をクリックします。  
  
4.  カスタマイズされたクリックスルー レポートをアタッチするエンティティを選択します。  
  
    > [!NOTE]  
    >  このエンティティは、カスタマイズされたクリックスルー レポートの基本エンティティと同じものである必要があります。  
  
5.  選択したエンティティの単一のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、単一インスタンス レポートの **[参照]** ボタンをクリックします。  
  
     または  
  
     選択したエンティティの複数のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、複数インスタンス レポートの **[参照]** ボタンをクリックします。  
  
6.  レポートを選択し、 **[OK]** をクリックします。  
  
7.  **[Apply]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [クリックスルーレポート &#40;SSRS&#41;](reports/clickthrough-reports-ssrs.md)  
  
  
