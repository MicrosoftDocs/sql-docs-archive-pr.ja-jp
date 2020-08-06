---
title: 監査変換エディター |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.audittransformation.f1
helpviewer_keywords:
- Audit Transformation Editor
ms.assetid: 32786a34-5870-4fde-83c7-ec74d62404b8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: af6490643a0bef60cca961dc9a0564c5f6b46484
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740242"
---
# <a name="audit-transformation-editor"></a>監査変換エディター
  監査変換により、パッケージが実行される環境に関するデータをパッケージ内のデータ フローに含めることができます。 たとえば、パッケージ、コンピューター、および演算子の名前をデータ フローに追加できます。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、この情報を提供するシステム変数が含まれています。  
  
 監査変換の詳細については、「 [Audit Transformation](data-flow/transformations/audit-transformation.md)」を参照してください。  
  
## <a name="options"></a>Options  
 **出力列の名前**  
 監査情報を格納する、新しい出力列の名前を入力します。  
  
 **[監査の種類]**  
 監査情報を得るために使用できるシステム変数を選択します。  
  
|値|[説明]|  
|-----------|-----------------|  
|**[実行インスタンスの GUID]**|パッケージの実行インスタンスを個別に識別する GUID を挿入します。|  
|**[パッケージ ID]**|パッケージを個別に識別する GUID を挿入します。|  
|**パッケージ名**|パッケージ名を挿入します。|  
|**バージョン ID**|パッケージのバージョンを個別に識別する GUID を挿入します。|  
|**[実行開始時刻]**|パッケージの実行が開始される時刻を挿入します。|  
|**コンピューター名**|パッケージを起動したコンピューターの名前を挿入します。|  
|**ユーザー名**|パッケージを起動したユーザーのログイン名を挿入します。|  
|**タスク名**|監査変換が関連付けられているデータ フロー タスクの名前を挿入します。|  
|**タスク ID**|監査変換が関連付けられているデータ フロー タスクを個別に識別する GUID を挿入します。|  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
