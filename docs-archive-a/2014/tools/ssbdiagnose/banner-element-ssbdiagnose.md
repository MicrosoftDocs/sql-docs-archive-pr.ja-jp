---
title: バナー要素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742725"
---
# <a name="banner-element-ssbdiagnose"></a>Banner 要素 (ssbdiagnose)
  **ssbdiagnose** の出力 XML ファイルを生成したユーティリティを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a>要素の属性  
  
|Attribute|説明|  
|---------------|-----------------|  
|`title`|**ssbdiagnose** の XML 出力ファイルを生成したユーティリティを示します。|  
|`product`|**ssbdiagnose** の XML 出力ファイルを生成した製品を示します。|  
|`version`|XML 出力ファイルを生成したユーティリティのバージョンを示します。|  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|**ssbdiagnose** の出力 XML ファイルにつき 1 個。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DiagnosticInformation 要素 &#40;ssbdiagnose&#41;](diagnosticinformation-element-ssbdiagnose.md)|  
|**子要素**|[なし] :|  
  
## <a name="example"></a>例  
 バナー要素の例を次に示します。  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a>参照  
 [ssbdiagnose ユーティリティ &#40;Service Broker&#41;](ssbdiagnose-utility-service-broker.md)  
  
  
