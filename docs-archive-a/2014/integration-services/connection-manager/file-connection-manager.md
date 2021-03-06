---
title: ファイル接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- folders [Integration Services], connections
- files [Integration Services], connections
- files [Integration Services]
- connection managers [Integration Services], File
- connections [Integration Services], files
- File connection manager
ms.assetid: 019078bc-44ee-4975-9169-0f9a89e3f3be
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cebb5438003c6b14c547d14012ff1bc1175a706d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738568"
---
# <a name="file-connection-manager"></a>ファイル接続マネージャー
  ファイル接続マネージャーを使用すると、パッケージで既存のファイルやフォルダーを参照したり、実行時にファイルやフォルダーを作成できます。 たとえば、Excel ファイルを参照できます。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の特定のコンポーネントでは、ファイルの情報を使用して作業が実行されます。 たとえば、SQL 実行タスクでは、そのタスクで実行する SQL ステートメントが含まれるファイルを参照できます。 他のコンポーネントは、ファイルに対する操作を実行します。 たとえば、ファイル システム タスクは新しい場所にコピーするファイルを参照できます。  
  
## <a name="usage-types-of-the-file-connection-manager"></a>ファイル接続マネージャーの使用法の種類  
 ファイル接続マネージャーの `FileUsageType` プロパティでは、ファイル接続の使用方法を指定します。 ファイル接続マネージャーでは、ファイルの作成、フォルダーの作成、既存のファイルの使用、または既存のフォルダーの使用を実行できます。  
  
 次の表に、`FileUsageType` の値の一覧を示します。  
  
|値|説明|  
|-----------|-----------------|  
|`0`|ファイル接続マネージャーは、既存のファイルを使用します。|  
|`1`|ファイル接続マネージャーは、ファイルを作成します。|  
|`2`|ファイル接続マネージャーは、既存のフォルダーを使用します。|  
|`3`|ファイル接続マネージャーは、フォルダーを作成します。|  
  
## <a name="multiple-file-or-folder-connections"></a>複数のファイルまたはフォルダーの接続  
 ファイル接続マネージャーが参照できるファイルまたはフォルダーは、1 つのみです。 複数のファイルまたはフォルダーを参照するには、ファイル接続マネージャーではなく、複数ファイル接続マネージャーを使用します。 詳細については、「 [複数ファイル接続マネージャー](multiple-files-connection-manager.md)」を参照してください。  
  
## <a name="configuration-of-the-file-connection-manager"></a>ファイル接続マネージャーの構成  
 ファイル接続マネージャーをパッケージに追加するときは、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] によって、実行時にファイル接続を解決する接続マネージャーを作成し、ファイル接続プロパティを設定して、ファイル接続をパッケージの `Connections` コレクションに追加します。  
  
 接続マネージャーの `ConnectionManagerType` プロパティは、`FILE` に設定されます。  
  
 ファイル接続マネージャーは、次の方法で構成できます。  
  
-   使用法の種類を指定します。  
  
-   ファイルまたはフォルダーを指定します。  
  
 ファイル接続マネージャーの ConnectionString プロパティは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]の [プロパティ] ウィンドウで式を指定することで設定できます。 ただし、式を使用してファイルまたはフォルダーを指定するときに検証エラーが発生しないようにするには、[ファイル**接続マネージャーエディター**] の [ファイル **/フォルダー**] で、ファイルまたはフォルダーのパスを追加します。  
  
 プロパティを設定するには [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「 [[ファイル接続マネージャー エディター] ダイアログ ボックス](../file-connection-manager-editor.md)」を参照してください。  
  
 プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。  
  
  
