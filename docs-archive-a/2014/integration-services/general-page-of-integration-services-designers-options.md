---
title: '[全般] ページ |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Business_Intelligence_Designers.Data_Transformation_Designers.General
ms.assetid: d695690a-923b-4036-945e-7621e8651deb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59073ac29f95f1e64bd0a9382366e9539ce1408a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632592"
---
# <a name="general-page"></a>[全般] ページ
  **[オプション]** ダイアログ ボックスの **[Integration Services デザイナー]** ページにある **[全般]** ページを使用すると、パッケージの読み込み、表示、およびアップグレードに関するオプションを指定できます。  
  
 **[全般]** ページを開くには、 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で **[ツール]** メニューの **[オプション]** をクリックし、 **[ビジネス インテリジェンス デザイナー]** を展開して **[Integration Services デザイナー]** を選択します。  
  
## <a name="options"></a>オプション  
 **[パッケージの読み込み時にデジタル署名を確認する]**  
 パッケージの読み込み時に [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] でデジタル署名を確認する場合に選択します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、デジタル署名が存在するか、有効であるか、信頼されるソースから来たものであるかということだけが確認されます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、パッケージの署名後にパッケージが変更されたかどうかは確認されません。  
  
 **BlockedSignatureStates** レジストリ値を設定すると、このレジストリ値が、 **[パッケージの読み込み時にデジタル署名を確認する]** オプションをオーバーライドします。 詳細については、「 [レジストリ値を設定して署名ポリシーを実装する](implement-a-signing-policy-by-setting-a-registry-value.md)」をご覧ください。  
  
 詳細については、「 [デジタル署名を使用してパッケージのソースを特定する](security/identify-the-source-of-packages-with-digital-signatures.md)」をご覧ください。  
  
 **[パッケージが署名されていない場合、警告を表示する]**  
 署名されていないパッケージが読み込まれたときに、警告を表示します。  
  
 **[優先順位制約ラベルを表示する]**  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] でパッケージを表示する場合に、優先順位制約でどのラベル ([成功]、[失敗]、または [完了]) を表示するかを選択します。  
  
 **[スクリプト言語]**  
 新しいスクリプト タスクおよびスクリプト コンポーネントの既定のスクリプト言語を選択します。  
  
 **[接続文字列を更新して新しいプロバイダー名を使用する]**  
 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] パッケージを開くかアップグレードするときに、現在のリリースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]について、次のプロバイダーの名前を使用するように接続文字列を更新します。  
  
-   [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] OLE DB プロバイダー  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] パッケージ アップグレード ウィザードは、接続マネージャーに格納されている接続文字列だけを更新します。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の式言語またはスクリプト タスクのコードによって動的に構築される接続文字列は更新しません。  
  
 **[新しいパッケージ ID の作成]**  
 [!INCLUDE[ssISversion2005](../includes/ssisversion2005-md.md)] パッケージをアップグレードするとき、アップグレードされたバージョンのパッケージ用に新しいパッケージ ID を作成します。  
  
## <a name="see-also"></a>参照  
 [セキュリティの概要 &#40;Integration Services&#41;](security/security-overview-integration-services.md)   
 [スクリプトによるパッケージの拡張](extending-packages-scripting/extending-packages-with-scripting.md)  
  
  
