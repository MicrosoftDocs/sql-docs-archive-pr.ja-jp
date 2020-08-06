---
title: カスタム認証 Cookie を渡すようにレポートマネージャーを構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- authentication [Reporting Services]
- extensions [Reporting Services], custom security
ms.assetid: 91aeb053-149e-4562-ae4c-a688d0e1b2ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 90e8798fb91152ec64e7f290dc1522fc8eaa451c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633720"
---
# <a name="configure-report-manager-to-pass-custom-authentication-cookies"></a>カスタム認証クッキーを送信するようにレポート マネージャーを構成する
  カスタム認証拡張機能を使用している場合、カスタム認証クッキーを送信するようにレポート マネージャーを構成してください。 構成しない場合、レポート マネージャーはレポート サーバー固有の HTTP 要求を使用してクッキーを送信するだけです。 追加のクッキーを送信するには、RSReportServer.Config ファイルを変更する必要があります。  
  
## <a name="modifying-the-rsreportserverconfig-file"></a>RSReportServer.Config ファイルの変更  
 レポートマネージャーを有効にすると、 `PassThroughCookies` RSReportServer.config ファイルのレポートマネージャー構成設定に <> 要素を追加することにより、レポートサーバーに追加のクッキーを送信することができます。 追加のクッキーの送信は、レポート サーバーの認証クッキーだけでなく、サード パーティの認証システムのクッキーも必要なシングル サインオン認証ソリューションで便利です。  
  
 レポート マネージャーの使用時に HTTP 要求を使用した追加のクッキーの送信を有効にするには、RSReportServer.config ファイルに次の要素を設定してください。  
  
```  
<UI>  
   <CustomAuthenticationUI>  
      ...  
      <PassThroughCookies>  
         <PassThroughCookie>cookiename1</PassThroughCookie>  
         <PassThroughCookie>cookiename2</PassThroughCookie>  
      </PassThroughCookies>  
   </CustomAuthenticationUI>  
      ...  
</UI>  
```  
  
## <a name="see-also"></a>参照  
 [レポート サーバーでの認証](authentication-with-the-report-server.md)   
 [RSReportServer 構成ファイル](../report-server/rsreportserver-config-configuration-file.md)   
 [セキュリティ拡張機能の概要](../extensions/security-extension/security-extensions-overview.md)   
 [レポート サーバーを構成および管理する &#40;SSRSネイティブ モード&#41;](../report-server/configure-and-administer-a-report-server-ssrs-native-mode.md)  
  
  
