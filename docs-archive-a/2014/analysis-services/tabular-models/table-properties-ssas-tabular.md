---
title: テーブルのプロパティ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9613609c42de8fd3a4aab7aec3208dfe3d31be4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738815"
---
# <a name="table-properties-ssas-tabular"></a>Table Properties (SSAS Tabular)
  このトピックでは、テーブル モデルのテーブルのプロパティについて説明します。 ここで説明するプロパティは、ソースのどの列をインポートするかを定義する [テーブルのプロパティの編集] ダイアログ ボックスのプロパティとは異なります。  
  
 このトピックのセクション:  
  
-   [テーブルのプロパティ](#bkmk_properties)  
  
-   [テーブル プロパティの設定を構成するには](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a>テーブルのプロパティ  
 **Basic**  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**Connection Name**|\<connection name>|テーブルのデータソースへの接続の名前。<br /><br /> 接続を編集するには、ボタンをクリックします。|  
|**[非表示]**|誤り|レポート クライアント フィールドの一覧で、テーブルを非表示にするかどうかを指定します。|  
|**パーティション**||テーブルのパーティションは、 **[プロパティ]** ウィンドウに表示できません。 パーティションを表示、作成、または編集するには、ボタンをクリックしてパーティション マネージャーを開きます。|  
|**ソースデータ**||テーブルのソース データは、 **[プロパティ]** ウィンドウに表示できません。 ソース データを表示または編集するには、ボタンをクリックして [テーブルのプロパティの編集] ダイアログ ボックスを開きます。|  
|**テーブルの説明**||テーブルの説明文です。<br /><br /> [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]では、フィールド一覧のこのテーブルにエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。|  
|**テーブル名**|\<friendly name>|テーブルのフレンドリ名を指定します。 テーブルのインポート ウィザードを使用してテーブルをインポートするとき、またはインポート後の任意の時点で、テーブル名を指定できます。 モデル内のテーブル名は、ソースに関連付けられているテーブルとは異なる場合があります。 テーブル表示名は、レポート クライアント アプリケーション フィールドのリストおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のモデル データベース内に表示されます。|  
  
 **レポートのプロパティ**  
  
 レポートのプロパティの詳細な説明と構成に関する情報については、「[Power View レポート プロパティ (SSAS テーブル)](properties-ssas-tabular.md)」を参照してください。  
  
|プロパティ|既定の設定|説明|  
|--------------|---------------------|-----------------|  
|**既定のフィールド セット**|||  
|テーブルの動作|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a>テーブルプロパティの設定を構成するには  
  
1.  モデル デザイナーのデータ ビューでテーブル (タブ) をクリックするか、ダイアグラム ビューでテーブルのヘッダーをクリックします。  
  
2.  **[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、ボタンをクリックして追加の構成オプションを選択します。  
  
  
