---
title: RSReportDesigner 構成ファイル | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Designer [Reporting Services], configuration file
- RSReportDesigner configuration file
ms.assetid: fdcc9c58-3bad-45b3-ba8e-c7816d64f14c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 563c5ea602eef3af2400057f3da41a5850a31cec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641448"
---
# <a name="rsreportdesigner-configuration-file"></a>RSReportDesigner 構成ファイル
  RSReportDesigner.config ファイルには、レポート デザイナーに利用できる表示拡張機能およびデータ処理拡張機能に関する設定が保存されています。 データ処理拡張機能の情報は、`Data` 要素に保存されます。 表示拡張機能の情報は、`Render` 要素に保存されます。 `Designer` 要素には、レポート デザイナーで使用されるクエリ ビルダーが列挙されます。  
  
 レポート デザイナーでは、レポートをプレビューするために埋め込みのレポート サーバー機能を使用します。 サーバー関連の設定を指定すると、サーバー側のプレビュー処理をローカルでサポートできます。 レポートサーバーの構成設定の詳細については、「 [Rsreportserver Configuration File](rsreportserver-config-configuration-file.md)」を参照してください。  
  
## <a name="file-location"></a>ファイルの場所  
 このファイルは、\Program Files\Microsoft Visual Studio 8\Common7\IDE\PrivateAssemblies にあります。  
  
## <a name="editing-guidelines"></a>編集のガイドライン  
 カスタム拡張機能を配置または削除する場合、プレビュー時のキャッシュを無効にする場合、およびサービス パック アップグレードの後に新しいデータ処理拡張機能を登録する場合を除いて、このファイルの設定を変更しないでください。  
  
 表示拡張機能の設定をカスタマイズしている場合は、構成ファイルの編集方法を説明したトピックが用意されています。 詳細については、「 [RSReportServer.Config で表示拡張機能パラメーターをカスタマイズする](../customize-rendering-extension-parameters-in-rsreportserver-config.md)」を参照してください。  
  
 一般的な構成ファイルを編集する方法については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。  
  
## <a name="example-configuration-file"></a>構成ファイルの例  
 以下の例は、RSReportDesigner.config ファイルの形式を示しています。  
  
```  
<Configuration>  
  <Add Key="SecureConnectionLevel" Value="0" />  
  <Add Key="InstanceName" Value="Microsoft.ReportingServices.PreviewServer" />  
  <Add Key="SessionCookies" Value="true" />  
  <Add Key="SessionTimeoutMinutes" Value="3" />  
  <Add Key="PolicyLevel" Value="rspreviewpolicy.config" />  
  <Add Key="CacheDataForPreview" Value="true" />  
  <Extensions>  
    <Render> . . . </Render>  
    <Data> . . . </Data>  
    <Designer> . . . </Designer>  
```  
  
## <a name="configuration-settings"></a>構成設定  
  
|設定|説明|  
|-------------|-----------------|  
|`SecureConnectionLevel`|Web サービス接続のセキュリティ レベルを指定します。 有効な値は、0 ～ 3 で、0 はセキュリティ レベルが最も低くなります。 詳細については、「 [セキュリティで保護された Web サービス メソッドの使用](../report-server-web-service/net-framework/using-secure-web-service-methods.md)」を参照してください。|  
|`InstanceName`|プレビュー サーバーの識別子です。 この値は変更しないでください。|  
|`SessionCookies`|レポート サーバーがブラウザーのクッキーを使用してセッション情報を保持するかどうかを指定します。 有効な値として、`true` および `false` があります。 既定では、 `true`です。 この値を false に設定すると、セッション データが **reportservertempdb** データベースに格納されます。|  
|`SessionTimeoutMinutes`|セッションのクッキーの有効期間を指定します。 既定値は 3 分です。|  
|`PolicyLevel`|セキュリティ ポリシーの構成ファイルを指定します。 有効な値は Rspreviewpolicy.config です。詳細については、「 [Reporting Services セキュリティポリシーファイルの使用](../extensions/secure-development/using-reporting-services-security-policy-files.md)」を参照してください。|  
|`CacheDataForPreview`|`True` に設定すると、レポート デザイナーがローカル コンピューター上のキャッシュ ファイルにデータを格納します。 有効な値は、`True` (既定値) および `False` です。 詳細については、「 [レポートのプレビュー](../reports/previewing-reports.md)」を参照してください。|  
|`Render`|プレビューのためにレポート デザイナーで利用できる表示拡張機能を列挙します。 プレビューに使用する表示拡張機能のセットは、レポート サーバーと一緒にインストールされた表示拡張機能と同一である必要があります。<br /><br /> `Name` は、表示拡張機能を指定します。 コードで表示拡張機能を起動している場合は、この値を使用して、特定の拡張機能を呼び出します。<br /><br /> `Type` は、拡張クラスの完全修飾クラス名、およびライブラリ名をコンマで区切って指定します。<br /><br /> `Visible` は、任意のユーザー インターフェイスに名前を表示するかどうかを指定します。 この値には、`True` (既定値) または `False` があります。 `True` を指定すると、名前がユーザー インターフェイスに表示されます。|  
|`Data`|レポートにデータを提供するデータ ソースに接続するためにレポート デザイナーで利用できるデータ処理拡張機能を列挙します。 レポート デザイナーで使用するデータ処理拡張機能のセットは、レポート サーバーと一緒にインストールされたデータ処理拡張機能と同一のものである場合があります。 カスタム拡張機能を追加または削除する場合は、「 [データ処理拡張機能の配置](../extensions/data-processing/deploying-a-data-processing-extension.md)」を参照してください。<br /><br /> `Name` は、データ処理拡張機能を指定します。<br /><br /> `Type` は、拡張クラスの完全修飾クラス名、およびライブラリ名をコンマで区切って指定します。|  
|`Designer`|レポート デザイナーで使用できるクエリ ビルダーが列挙されます。 クエリ ビルダーは、レポートで使用されるデータを取得するクエリを構築するためのユーザー インターフェイスを提供します。 クエリ ビルダーは、データ処理拡張機能によって異なる場合があります。 既定では、Reporting Services は、製品に含まれるすべてのデータ処理拡張機能に 1 つのビジュアル データ ツール ユーザー インターフェイスを提供します。 ただし、サード パーティのデータ処理拡張機能を構築または使用している場合は、他のクエリ ビルダー インターフェイスが適用されることがあります。|  
|`PreviewProcessingServiceStartupTimeoutSeconds`|エラー メッセージを表示する前にプレビュー処理サービスの起動を待機する時間を指定します。 既定値は 15 秒です。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](reporting-services-configuration-files.md)   
 [レポートデザイナー SQL Server Data Tools のクエリデザインツール &#40;SSRS&#41;](../report-data/query-design-tools-ssrs.md)  
  
  
