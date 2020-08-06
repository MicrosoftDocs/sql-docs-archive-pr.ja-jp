---
title: '[データベースのプロパティ] ダイアログボックス (SSAS-テーブル) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.DatabaseProperties.f1
ms.assetid: 0f0ec02f-7b55-40ea-8a04-ed0deb1efd7a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41bf7838a714c35e2149e8163e21a7b8044a77c6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645913"
---
# <a name="database-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="86ef2-102">[データベースのプロパティ] ダイアログ ボックス (SSAS - テーブル)</span><span class="sxs-lookup"><span data-stu-id="86ef2-102">Database Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="86ef2-103">このダイアログ ボックスは、タイムスタンプとその他の情報に加え、データベースがキャッシュされたデータを使用するかどうかを決定するカスタマイズ可能なプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-103">This dialog box provides timestamps and other descriptive information, plus customizable properties that determine whether the database uses cached data.</span></span> <span data-ttu-id="86ef2-104">他のカスタマイズ可能なプロパティには、データベース名の変更と権限借用オプションの指定が含まれます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-104">Other customizable properties include changing the database name and specifying the impersonation options.</span></span>  
  
## <a name="options"></a><span data-ttu-id="86ef2-105">Options</span><span class="sxs-lookup"><span data-stu-id="86ef2-105">Options</span></span>  
  
|<span data-ttu-id="86ef2-106">期間</span><span class="sxs-lookup"><span data-stu-id="86ef2-106">Term</span></span>|<span data-ttu-id="86ef2-107">定義</span><span class="sxs-lookup"><span data-stu-id="86ef2-107">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="86ef2-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="86ef2-108">**Name**</span></span>|<span data-ttu-id="86ef2-109">**[名前]** は、サーバー上のデータベースを識別するデータベース名です。</span><span class="sxs-lookup"><span data-stu-id="86ef2-109">**Name** is the database name that uniquely identifies the database on the server.</span></span> <span data-ttu-id="86ef2-110">データベース名を変更するときは、既存の接続文字列で現在の名前を使用するレポートおよびクライアント アプリケーションへの影響を考慮します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-110">When changing the database name, consider the impact on reports and client applications that use the current name in existing connection strings.</span></span> <span data-ttu-id="86ef2-111">アクセス拒否エラーを避けるために、既存のレポートの接続文字列を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="86ef2-111">You will need to update connection strings in existing reports to avoid access denied errors.</span></span> <span data-ttu-id="86ef2-112">また、このデータベースのソースであるテーブル モデルでは、ほとんどの場合、元の名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-112">In addition, the tabular model that is the source of this database most likely uses the original name.</span></span> <span data-ttu-id="86ef2-113">モデルへの今後の更新が目的のデータベースに発行されるように、モデル内のデータベース配置プロパティを更新することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="86ef2-113">Consider updating the database deployment properties in the model to ensure that future updates to that model are published to the intended database.</span></span>|  
|<span data-ttu-id="86ef2-114">**ID**</span><span class="sxs-lookup"><span data-stu-id="86ef2-114">**ID**</span></span>|<span data-ttu-id="86ef2-115">データベースの ID が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-115">Displays the identifier of the database.</span></span>|  
|<span data-ttu-id="86ef2-116">**説明**</span><span class="sxs-lookup"><span data-stu-id="86ef2-116">**Description**</span></span>|<span data-ttu-id="86ef2-117">データベースの説明を変更するときに、説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-117">Type to change the description of the database.</span></span>|  
|<span data-ttu-id="86ef2-118">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-118">**Create Timestamp**</span></span>|<span data-ttu-id="86ef2-119">データベースが作成された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-119">Displays the date and time the database was created.</span></span>|  
|<span data-ttu-id="86ef2-120">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-120">**Last Schema Update**</span></span>|<span data-ttu-id="86ef2-121">データベースのメタデータが最後に更新されたときの日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-121">Displays the date and time the metadata for the database was last updated.</span></span>|  
|<span data-ttu-id="86ef2-122">**[最終更新]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-122">**Last Update**</span></span>|<span data-ttu-id="86ef2-123">データベースのデータが最後に更新されたときの日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-123">Displays the date and time the data for the database was last updated.</span></span>|  
|<span data-ttu-id="86ef2-124">**読み取り/書き込みモード**</span><span class="sxs-lookup"><span data-stu-id="86ef2-124">**Read-Write Mode**</span></span>|<span data-ttu-id="86ef2-125">これは読み取り専用プロパティですが、 **Detach** および **Attach** コマンドのシーケンスを使用して変更できます。このプロパティは、 **Attach** コマンドのパラメーターです。</span><span class="sxs-lookup"><span data-stu-id="86ef2-125">This is a read-only property, but you can change it using a sequence of **Detach** and **Attach** commands, where the property is a parameter of the **Attach** command.</span></span> <span data-ttu-id="86ef2-126">詳細については、「 [データベースの ReadWriteMode](multidimensional-models/database-readwritemodes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ef2-126">For more information, see [Database ReadWriteModes](multidimensional-models/database-readwritemodes.md).</span></span>|  
|<span data-ttu-id="86ef2-127">**DirectQueryMode**</span><span class="sxs-lookup"><span data-stu-id="86ef2-127">**DirectQueryMode**</span></span>|<span data-ttu-id="86ef2-128">データベースがインメモリ ストレージのみ (ディスク ストレージなし) を使用するか、ディスク ベース ストレージのみを使用するか、またはその 2 つの組み合わせを使用するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-128">Specifies whether the database uses only in-memory storage (no disk storage), only disk-based storage, or some combination of the two.</span></span> <span data-ttu-id="86ef2-129">有効な値は、InMemory、DirectQuery、InMemoryWithDirectQuery (ほとんどはメモリ ベースで、一部がディスクへのページング)、または DirectQueryWithInMemory (ほとんどがディスク ベースで、一部がインメモリ ストレージ) です。</span><span class="sxs-lookup"><span data-stu-id="86ef2-129">Valid values are InMemory, DirectQuery, InMemoryWithDirectQuery (mostly memory-based with some paging to disk), or DirectQueryWithInMemory (mostly disk-based with some in-memory storage).</span></span> <span data-ttu-id="86ef2-130">詳細については、「 [SSAS のデプロイシナリオ &#40;SSAS 表形式&#41;](directquery-deployment-scenarios-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86ef2-130">For more information, see [DirectQuery Deployment Scenarios &#40;SSAS Tabular&#41;](directquery-deployment-scenarios-ssas-tabular.md).</span></span>|  
|<span data-ttu-id="86ef2-131">**[データ ソースの権限借用情報]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-131">**Data Source Impersonation Info**</span></span>|<span data-ttu-id="86ef2-132">ローカルまたはリモート パーティション、リレーショナル データ ストア (DirectQuery による) に対して実行されるクエリ、不一致バインド、およびターゲットからソースへのデータベース同期で、データを処理または更新するときにデータベース接続で使用される権限借用アカウントを指定します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-132">Specifies the impersonation account used for database connections when processing or refreshing data on local or remote partitions, queries that run against a relational data store (via DirectQuery), out-of-line bindings, and database synchronization from target to source.</span></span><br /><br /> <span data-ttu-id="86ef2-133">有効な値には、Analysis Services サービス アカウントまたは Windows 資格情報の特定のセットが含まれます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-133">Valid values include the Analysis Services service account or a specific set of Windows credentials.</span></span> <span data-ttu-id="86ef2-134">**[現在のユーザーの資格情報を使用する]** を指定しないでください。</span><span class="sxs-lookup"><span data-stu-id="86ef2-134">Do not specify **Use the credentials of the current user**.</span></span> <span data-ttu-id="86ef2-135">この資格情報オプションは、テーブル モデル データベースではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="86ef2-135">That credential option is not supported for a tabular model database.</span></span>|  
|<span data-ttu-id="86ef2-136">**[最終処理]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-136">**Last Processed**</span></span>|<span data-ttu-id="86ef2-137">データベースが最後に処理された日時が表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-137">Displays the date and time the database was last processed.</span></span>|  
|<span data-ttu-id="86ef2-138">**[推定サイズ]**</span><span class="sxs-lookup"><span data-stu-id="86ef2-138">**Estimated Size**</span></span>|<span data-ttu-id="86ef2-139">データベースの推定サイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="86ef2-139">Displays the estimated size of the database.</span></span>|  
|<span data-ttu-id="86ef2-140">**ストレージの場所**</span><span class="sxs-lookup"><span data-stu-id="86ef2-140">**Storage Location**</span></span>|<span data-ttu-id="86ef2-141">データベースの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="86ef2-141">Specifies the location of the database.</span></span> <span data-ttu-id="86ef2-142">データベースが既定のデータ ディレクトリにある場合は、この値は空になります。</span><span class="sxs-lookup"><span data-stu-id="86ef2-142">If the database is located in the default Data directory, this value will be empty.</span></span>|  
  
  