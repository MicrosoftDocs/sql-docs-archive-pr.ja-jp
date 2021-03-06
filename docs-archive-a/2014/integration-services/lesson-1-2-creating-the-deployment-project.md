---
title: '手順 2: 配置プロジェクトの作成 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 59990fe2-7036-4e9c-8efc-6ece9e66eda7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ebfce8796f98628c2832c5ab7f4be665c7915d10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641103"
---
# <a name="step-2-creating-the-deployment-project"></a>手順 2:配置プロジェクトの作成
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]では、配置可能な単位は [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトになります。 パッケージを配置するには、まず新しい [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを作成し、すべてのパッケージと、これらのパッケージと共に配置する補助ファイルをそのプロジェクトに追加する必要があります。  
  
### <a name="to-create-the-integration-services-project"></a>Integration Services プロジェクトを作成するには  
  
1.  **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントしてから、[SQL Server] の **[SQL Server Data Tools]** をクリックします。  
  
2.  新しい **プロジェクトを作成するため、** [ファイル] **メニューの**[新規作成] **をポイントし、** [プロジェクト] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] をクリックします。  
  
3.  **[新しいプロジェクト]** ダイアログ ボックスの **[テンプレート]** ペインで、 **[Integration Services プロジェクト]** をクリックします。  
  
4.  **[名前]** ボックスに表示されている既定の名前を「 **Deployment Tutorial**」に変更します。 必要に応じて、 **[ソリューションのディレクトリを作成]** チェック ボックスをオフにします。  
  
5.  既定の場所をそのまま使用するか、 **[参照]** をクリックして使用するフォルダーを指定します。  
  
6.  **[プロジェクトの場所]** ダイアログ ボックスで、目的のフォルダーをクリックして **[開く]** をクリックします。  
  
7.  **[OK]** をクリックします。  
  
8.  既定では、Package.dtsx という名前の空のパッケージが作成され、プロジェクトに追加されます。 ただし、このパッケージはここでは使用しません。代わりに既存のパッケージをプロジェクトに追加します。 プロジェクト内のすべてのパッケージを配置に含めるので、Package.dtsx は削除してください。 削除するには、Package.dtsx を右クリックし、 **[削除]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 3: パッケージとその他のファイルの追加](../integration-services/lesson-1-3-adding-packages-and-other-files.md)  
  
![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>参照  
 [Integration Services (SSIS) プロジェクト](integration-services-ssis-projects-and-solutions.md)  
  
  
