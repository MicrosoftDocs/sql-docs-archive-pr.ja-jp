---
title: IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- IsSharePointIntegrated property
ms.assetid: e21d00ad-5d9a-4290-8d74-7eeeda39e1ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d0c92ebe586d37053b47f90ca98c31b3068a7b91
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639857"
---
# <a name="issharepointintegrated-property-wmi-msreportserver_instance"></a>IsSharePointIntegrated プロパティ (WMI MSReportServer_Instance)
  レポート サーバーが SharePoint 統合モードであるかどうかを示します。 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降、このプロパティは常に `False` を返します。これは、SharePoint モードでは、[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] インスタンスは SharePoint 共有サービスであり、WMI プロバイダーによって制御されないためです。  
  
## <a name="syntax"></a>構文  
  
```vb  
Public Dim IsSharePointIntegrated As Boolean  
```  
  
```csharp  
public Boolean IsSharePointIntegrated;  
```  
  
## <a name="property-values"></a>プロパティ値  
 レポート サーバーが SharePoint 統合モードであるかどうかを示す `Boolean` 値。  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [!INCLUDE[ssRSWMInmspc](../../includes/ssrswminmspc-md.md)]  
  
## <a name="see-also"></a>参照  
 [MSReportServer_Instance メンバー](msreportserver-instance-members.md)   
 [MSReportServer_ConfigurationSetting クラス](msreportserver-configurationsetting-class.md)  
  
  
