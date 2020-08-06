---
title: '[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replconflictviewer.cvmerge.f1
ms.assetid: bfef5e21-ac04-4bc5-a55e-595421e34923
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1354a35e06f58b56f9678267338917a272ff8b19
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631826"
---
# <a name="microsoft-replication-conflict-viewer-merge-replication"></a>[Microsoft レプリケーション競合表示モジュール] (マージ レプリケーション)
  レプリケーション競合表示モジュールを使用すると、レプリケーション同期中に発生した競合を表示できます。 競合が発生するのは、同一のデータの変更が、2 つの異なるサーバー、たとえば、パブリッシャーとサブスクライバー、または 2 つの異なるサブスクライバーで行われたときです。 競合は、レプリケーションがアーティクルの作成時に選択された競合回避モジュールを使用することで自動的に解決されます。 ただし、レプリケーション競合表示モジュールを使用すると、必要な場合に、競合を回避するための別の解決方法を選択することができます。 発生する可能性がある競合は、次のとおりです。  
  
-   更新競合。 更新競合は、同一のデータが 2 つの異なる場所で変更された場合に発生します。 一方の変更が競合の優先データとなり、他方は非優先データとなります。 既存のデータ (競合の優先データ) を保持する、競合したデータ (競合の非優先データ) で既存のデータを上書きする、または優先データと非優先データをマージして既存のデータを更新するオプションがあります。  
  
-   挿入競合。 挿入競合は、他の場所での変更とマージされた場合に、データの一貫性のルールに違反する場所に行が挿入されたときに発生します。 既存のデータ (競合の優先データ) を保持する、競合したデータ (競合の非優先データ) で既存のデータを上書きする、または優先データと非優先データをマージして既存のデータを更新するオプションがあります。  
  
-   削除競合。 この競合は、同一行が、ある箇所で削除され、別の箇所で変更された場合に発生します。  
  
 競合は同期中に解決され、競合の非優先行のデータは競合テーブルに書き込まれます。 この競合に対して、最初の解決策を受け入れるか別の解決策を選択すると、記録された競合行は競合テーブルから削除されます。 定期的に競合を見直して、競合テーブルのサイズを小さくするようにしてください。  
  
> [!NOTE]  
>  論理レコードに関連する競合は、競合表示モジュールに表示されません。 これらの競合に関する情報を表示するには、レプリケーション ストアド プロシージャを使用します。 詳細については、「[マージ パブリケーションの競合情報の表示 (レプリケーション Transact-SQL プログラミング)](view-conflict-information-for-merge-publications.md)」を参照してください。  
  
## <a name="options"></a>Options  
 レプリケーション競合表示モジュールは 2 つのセクションに分かれています。 ダイアログ ボックスの上側のセクションには、選択されたテーブルの競合の一覧が表示されます。 競合の一覧の項目をクリックすると、競合の詳細がダイアログ ボックスの下側のセクションに表示されます。  
  
 競合の発生理由を示す情報 (パブリッシャーとサブスクライバーの両方で同じ行が更新された場合など) はダイアログ ボックスの下部に表示されます。 下側のセクションの競合データは、2 つの対応する列 (**[競合で優先されたデータ]** と **[競合で優先されなかったデータ]**) に表示されます。 更新されたデータと削除されたデータの間で競合が発生した場合、競合で削除された側にデータが表示されない場合があります。 この場合、レプリケーション競合表示モジュールでは、その行がある箇所では削除され別の箇所では更新されたことを示すメッセージが列の 1 つに表示されます。 また、提案された解決策についても示されます。  
  
 レプリケーション競合表示モジュールで編集できないデータ (たとえば、 **rowguid** データ) は、読み取り専用としてボックス内に淡色表示されます。  
  
 **[データベース]**  
 競合があるパブリケーションを含むデータベースを選択します。  
  
 **Publication**  
 競合があるテーブルを含むパブリケーションを選択します。  
  
 **テーブル**  
 競合を含むテーブルを選択します。  
  
 **[フィルターの定義]**  
 **[フィルターの定義]** ダイアログ ボックスが表示されます。  
  
 **[フィルターの適用または削除]**  
 **[フィルターの定義]** ダイアログ ボックスで定義されたフィルターを適用または削除します。  
  
 **[すべて選択]**  
 グリッドに一覧表示されたすべての競合を選択します。  
  
 **[なし] を選択**  
 グリッドに一覧表示されたすべての競合の選択を解除します。  
  
 **削除**  
 選択された競合をビューアーから削除し、関連するメタデータをレプリケーション システム テーブルから削除します。 それぞれの選択された競合に対して [優先するデータの送信] ボタンをクリックする (データへの変更を行わない) 場合と同じです。  
  
 **[すべての列を表示]**  
 テーブルのすべての列を表示します。  
  
 **[最初の 5 列および競合データが含まれている列を表示]**  
 最初の 5 列および競合データが含まれている列を表示します。 これは、テーブルに多数の列があり、競合を解決するのに最も関連する列のみを表示する場合に便利です。 主キーや名前フィールドなど、行を識別するフィールドはテーブルの最初の列にある場合が多いため、このビューでは最初の 5 列が必ず表示されます。  
  
 **列情報の表示**(**...**)  
 列の情報である **[テーブル名]**、 **[列名]**、 **[データ型]**、および **[列の値]** を表示します。 **[列の値]** は、値が読み取り専用と表示されている場合を除いて編集可能です。  
  
 **[優先されたデータの送信]**  
 競合回避モジュールによって優先データと見なされた行をそのまま使用します。 読み取り専用と表示されていない列の値は、このボタンをクリックする前に変更することができます。  
  
 **[優先されなかったデータの送信]**  
 競合回避モジュールによって非優先データと見なされた行を受け入れます。 読み取り専用と表示されていない列の値は、このボタンをクリックする前に変更することができます。  
  
 **[競合の詳細をログに記録]**  
 このボックスをオンにすると、競合の詳細がファイルに記録されます。 ファイルの場所を指定するには、 **[表示]** メニューをポイントし、 **[オプション]** をクリックします。 値を入力するか、参照ボタン (**[...]**) をクリックして適切なファイルに移動します。 **[OK]** をクリックして、 **[オプション]** ダイアログ ボックスを終了します。  
  
## <a name="see-also"></a>参照  
 [マージパブリケーションのデータの競合を表示および解決する &#40;SQL Server Management Studio&#41;](view-and-resolve-data-conflicts-for-merge-publications.md)   
 [マージ レプリケーションの競合検出および解決の詳細](merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  