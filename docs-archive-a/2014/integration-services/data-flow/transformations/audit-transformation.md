---
title: 監査変換 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittrans.f1
helpviewer_keywords:
- environment data in packages [Integration Services]
- Audit transformation
ms.assetid: 8c143682-9c81-4150-83d6-1d9678151d37
author: chugugrace
ms.author: chugu
ms.openlocfilehash: e8e302f6dd1dc5666ae65af2eb9705a4922915c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712193"
---
# <a name="audit-transformation"></a>監査変換
  監査変換により、パッケージが実行される環境に関するデータをパッケージ内のデータ フローに含めることができます。 たとえば、パッケージ、コンピューター、および演算子の名前をデータ フローに追加できます。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] には、この情報を提供するシステム変数が含まれています。  
  
## <a name="system-variables"></a>システム変数  
 次の表では、監査変換で使用できるシステム変数について説明します。  
  
|システム変数|インデックス|説明|  
|---------------------|-----------|-----------------|  
|`ExecutionInstanceGUID`|0|パッケージの実行インスタンスを識別する GUID です。|  
|`PackageID`|1|パッケージの一意識別子です。|  
|`PackageName`|2|パッケージの名前です。|  
|`VersionID`|3|パッケージのバージョンです。|  
|`ExecutionStartTime`|4|パッケージの実行を開始した時刻です。|  
|`MachineName`|5|コンピューター名|  
|`UserName`|6|パッケージを開始した人のログイン名です。|  
|`TaskName`|7|監査変換が関連付けられているデータ フロー タスクの名前です。|  
|**TaskId**|8|データ フロー タスクの一意識別子です。|  
  
## <a name="configuration-of-the-audit-transformation"></a>監査変換の構成  
 監査変換を構成するには、新しい出力列の名前を設定し、変換出力に追加します。次に、その出力列にシステム変数をマップします。 1 つのシステム変数は、複数の列にマップできます。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[監査変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、「 [Audit Transformation Editor](../../audit-transformation-editor.md)」を参照してください。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Common Properties](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
 プロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
  
