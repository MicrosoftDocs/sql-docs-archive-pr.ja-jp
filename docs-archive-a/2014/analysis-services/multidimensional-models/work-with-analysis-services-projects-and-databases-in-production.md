---
title: 運用環境での Analysis Services のプロジェクトおよびデータベースの操作 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Analysis Services, projects
ms.assetid: c589097f-ad29-4b97-8c7e-b8a910909c1a
author: minewiskan
ms.author: owend
ms.openlocfilehash: e9a2555511c422e5553662e2fcd292a5a2ec7c67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641311"
---
# <a name="working-with-analysis-services-projects-and-databases-in-a-production-environment"></a>実稼働環境における Analysis Services プロジェクトおよびデータベースの操作
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトから [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースを開発して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置したら、配置したデータベース内のオブジェクトに対する変更方法を指定する必要があります。 セキュリティ ロール、パーティション分割、ストレージ設定などの変更は、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]のいずれかを使用して行うことができます。 その他の変更 (属性やユーザー定義階層の追加など) を行うには、プロジェクト モードまたはオンライン モードで [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]を実行する必要があります。  
  
 オンライン モードの [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で、配置した [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えると、その直後に、配置で使用された [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは期限切れになります。 開発担当者が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクト内で変更を加え、変更したプロジェクトを配置しようとすると、データベース全体を上書きするように求めるメッセージが表示されます。 データベース全体を上書きする場合は、データベースの処理も必要になります。 配置されたデータベースを実稼働環境のスタッフが直接変更した場合は、その変更を開発チームに通知しておかないと、この問題は複雑になります。それは、開発チーム側が、自分たちが変更した内容が [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに反映されていない理由を知らされないままとなるからです。  
  
 SQL Server の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールを使用すると、このような問題を未然に防ぐことができます。次の方法があります。  
  
-   方法 1 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの実稼働環境バージョンに変更を加えるたびに、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースの変更バージョンに基づいて新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成します。 この新しい [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトは、プロジェクトのマスター コピーとしてソース管理システムにチェックインできます。 この方法は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースに変更を加えたかどうかに関係なく利用できます。  
  
-   方法 2 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をプロジェクト モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 この方法では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の配置ウィザードで利用できるオプションを使用して、セキュリティ ロールやストレージ設定など、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で加えられた変更を維持できます。 たとえば、プロジェクト ファイル内のデザイン関連設定を維持 (ストレージ設定およびセキュリティ ロールを除外) し、オンライン サーバーのストレージ設定およびセキュリティ ロールが使用されるようにすることができます。  
  
-   方法 3 : [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] をオンライン モードで使用することにより、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] データベースの実稼働バージョンにのみ変更を加えます。 SQL Server Management Studio と Business Intelligence Development Studio のいずれのツールも、同じオンライン サーバーだけを操作するので、バージョンが異なってもデータベースの同期が外れる可能性はありません。  
  
  
