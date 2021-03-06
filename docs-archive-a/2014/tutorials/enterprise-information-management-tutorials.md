---
title: Enterprise Information Management チュートリアル |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 8745dc80-193d-4de0-9f17-ba648ab1e81c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: b8cde162479645ab13a6ae000cc46e42e3c10e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643045"
---
# <a name="enterprise-information-management-tutorials"></a>Enterprise Information Management のチュートリアル
  このセクションには、[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] に付属の Enterprise Information Management (EIM) テクノロジを使用して、企業で情報を管理する方法のチュートリアルが含まれています。 Enterprise Integration Management (EIM) では、組織がデータの信頼性と一貫性を信頼してビジネス上の重要な意思決定を行うことを可能にするソリューションのポートフォリオが用意されています。 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] には、企業で EIM ソリューションを実装する際に役立つ以下のテクノロジがあります。  
  
-   SQL Server Integration Services (SSIS)。 SSIS では、ビジネス ワークフロー、データ ウェアハウス、またはマスター データ管理をサポートする包括的な抽出、変換、および読み込み (ETL) のさまざまなソースからデータを統合するための強力な拡張可能プラットフォームを用意しています。  
  
-   SQL Server Data Quality Services (DQS)。 DQS ではデータのクレンジング、照合、標準化、および拡充が可能なため、ビジネス インテリジェンス、データ ウェアハウス、およびトランザクション処理ワークロードに対して信頼できる情報を提供できます。  
  
-   SQL Server マスター データ サービス (MDS)。 MDS の中央データ ハブは、情報の整合性とデータの一貫性がアプリケーション間で変化していないかどうかを確認します。  
  
 [SSIS、MDS、DQS を組み合わせたエンタープライズ情報管理 &#91;チュートリアル&#93;](../../2014/tutorials/enterprise-information-management-using-ssis-mds-and-dqs-together-[tutorial].md)  
 このチュートリアルでは、SSIS、MDS、および DQS を組み合わせて、Enterprise Information Management (EIM) ソリューションのサンプルを実装する方法について学習します。 まず、DQS を使用して仕入先データ (メタデータ) についてのナレッジを含むナレッジ ベースを作成し、ナレッジ ベースに対して Excel ファイル内のデータをクレンジングして、データ内の重複項目を特定および削除するようにデータを照合します。 次に、Excel 用の MDS アドインを使用して、クレンジングおよび照合済みのデータを MDS にアップロードします。 次に、SSIS ソリューションを使用して全体のプロセスを自動化します。  
  
## <a name="see-also"></a>参照  
 [エンタープライズ情報管理-Microsoft SQL Server](https://go.microsoft.com/fwlink/?LinkId=270871)  
  
  
