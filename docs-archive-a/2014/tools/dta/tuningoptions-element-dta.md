---
title: TuningOptions 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- TuningOptions element
ms.assetid: 58a22ba1-8e03-411f-bd46-85e4540f217a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2fab1c55c9d036424142b2692e8335ea65c22340
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720624"
---
# <a name="tuningoptions-element-dta"></a>TuningOptions 要素 (DTA)
  特定のチューニング セッションのチューニング オプションが含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
    <TuningOptions>...</TuningOptions>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|省略可能。 使用する場合は、`DTAInput` 要素につき 1 回使用できます。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素 &#40;DTA&#41;](dtainput-element-dta.md)|  
|**子要素**|`ReportSet` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> `TuningLogTable` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> `NumberOfEvents` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> [TuningTimeInMin 要素 &#40;DTA&#41;](tuningtimeinmin-element-dta.md)<br /><br /> [StorageBoundInMB 要素 &#40;DTA&#41;](storageboundinmb-element-dta.md)<br /><br /> `MaxKeyColumnsInIndex` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> `MaxColumnsInIndex` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> `MinPercentageImprovement` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> [TestServer 要素 &#40;DTA&#41;](server-element-dta.md)<br /><br /> [FeatureSet 要素 &#40;DTA&#41;](featureset-element-dta.md)<br /><br /> [Partitioning 要素 &#40;DTA&#41;](partitioning-element-dta.md)<br /><br /> [DropOnlyMode 要素 &#40;DTA&#41;](droponlymode-element-dta.md)<br /><br /> [KeepExisting 要素 &#40;DTA&#41;](keepexisting-element-dta.md)<br /><br /> [OnlineIndexOperation 要素 &#40;DTA&#41;](onlineindexoperation-element-dta.md)<br /><br /> [DatabaseToConnect 要素 &#40;DTA&#41;](databasetoconnect-element-dta.md)<br /><br /> `IgnoreConstantsInWorkload` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。<br /><br /> `RetainShellDB` 要素。 詳細については、 [データベース エンジン チューニング アドバイザーの XML スキーマ](https://go.microsoft.com/fwlink/?linkid=43100)を参照してください。|  
  
## <a name="example"></a>例  
 要素の例につい `TuningOptions` ては、「 [XML 入力ファイルのサンプル &#40;DTA&#41;](xml-input-file-samples-dta.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
