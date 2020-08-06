---
title: あいまい参照変換 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptrans.f1
helpviewer_keywords:
- cleaning data
- comparing data
- token delimiters [Integration Services]
- temporary indexes [Integration Services]
- temporary tables [Integration Services]
- Fuzzy Lookup transformation
- reference tables [Integration Services]
- match similar data [Integration Services]
- replacing missing values
- correcting data [Integration Services]
- cache [Integration Services]
- standardizing data [Integration Services]
- lookups [Integration Services]
- confidence scores [Integration Services]
- fuzzy matches
- missing values replaced [Integration Services]
- similarity thresholds [Integration Services]
ms.assetid: 019db426-3de2-4ca9-8667-79fd9a47a068
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 742a87e7425fd65b8af7bcda87c237151d382f77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642200"
---
# <a name="fuzzy-lookup-transformation"></a>あいまい参照変換
  あいまい参照変換では、データの標準化、データの修正、不足している値の提供など、データのクリーン タスクを実行します。  
  
> [!NOTE]  
>  パフォーマンスやメモリの制限など、あいまい参照変換に関する詳細については、ホワイト ペーパー「 [SQL Server Integration Services 2005 のあいまい参照とあいまいグループ化](https://go.microsoft.com/fwlink/?LinkId=96604)」を参照してください。  
  
 あいまい参照変換は、あいまい一致を使用するという点が参照変換とは異なります。 参照変換では、等結合を使用して、参照テーブル内の一致レコードを検索します。 返されるのは、一致レコードを少なくとも 1 つ含むレコードと、一致レコードがないレコードです。 これに対して、あいまい参照変換では、あいまい一致を使用して、参照テーブル内の 1 つ以上の類似一致を返します。  
  
 あいまい参照変換は、一般的に、パッケージ データ フローで参照変換に続けて実行されます。 まず、参照変換によって完全一致の検索が行われます。 完全一致が見つからない場合、あいまい参照変換によって、参照テーブル内の類似一致が提供されます。  
  
 変換では、入力データの整理と拡張に使用する値を含む参照データ ソースにアクセスできる必要があります。 参照データ ソースは [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのテーブルである必要があります。 入力列の値と参照テーブルの値の一致は、完全一致である場合とあいまい一致である場合があります。 ただし、あいまい一致の場合、少なくとも 1 つの列一致が設定されている必要があります。 完全一致のみを使用する場合は、参照変換を使用してください。  
  
 この変換は 1 つの入力と 1 つの出力をとります。  
  
 あいまい一致では、データ型が `DT_WSTR` または `DT_STR` の入力列だけが使用されます。 完全一致では、`DT_TEXT`、`DT_NTEXT`、`DT_IMAGE` を除くすべての DTS データ型を使用できます。 詳細については、「 [Integration Services Data Types](../integration-services-data-types.md)」を参照してください。 入力と参照テーブルの結合に使用される列のデータ型には、互換性が必要です。 たとえば、DTS データ型の列とデータ型の列の結合は有効ですが、データ型の列をデータ型の `DT_WSTR` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] `nvarchar` 列に結合することは無効です `DT_WSTR` `int` 。  
  
 この変換は、使用する最大メモリ量、行比較アルゴリズム、および変換で使用するインデックス テーブルと参照テーブルのキャッシュを指定することにより、カスタマイズできます。  
  
 あいまい参照変換で使用されるメモリの量は、MaxMemoryUsage カスタム プロパティを設定することによって構成できます。 メガバイト (MB) 単位の数値を指定するか、0 を指定できます。0 を指定すると、変換に必要なメモリの量と使用できる物理メモリの量に基づいて、変換に使用されるメモリの量が動的に決まります。 MaxMemoryUsage カスタム プロパティは、パッケージの読み込み時にプロパティ式で更新できます。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../../expressions/integration-services-ssis-expressions.md)」、「[パッケージでプロパティ式を使用する](../../expressions/use-property-expressions-in-packages.md)」、および「[変換のカスタム プロパティ](transformation-custom-properties.md)」を参照してください。  
  
## <a name="controlling-fuzzy-matching-behavior"></a>あいまい一致の動作の制御  
 あいまい参照変換では、入力行に対して返される一致の最大数、トークン区切り記号、類似性のしきい値という 3 つの機能によって、実行する参照をカスタマイズします。  
  
 変換では、指定した数を上限とする 0 個以上の一致が返されます。 一致の最大数を指定しても、必ずその数の一致が返されるとは限りません。変換が返す一致の最大数が設定されるだけです。 一致の最大数を 1 より大きな値に設定すると、変換では参照ごとに複数行が出力され、行が重複する場合もあります。  
  
 変換には、データをトークン化する際に使用する区切り記号の既定のセットが用意されていますが、データのニーズに合わせてトークン区切り記号を追加できます。 Delimiters プロパティには、既定の区切り記号が含まれています。 トークンは相互比較するデータの単位を定義するので、トークンの設定は重要です。  
  
 類似性のしきい値は、コンポーネント レベルおよび結合レベルで設定できます。 結合レベルの類似性のしきい値は、入力と参照テーブルの列のあいまい一致を実行する場合にのみ使用できます。 類似性の範囲は 0 ～ 1 です。 しきい値が 1 に近いほど、行や列が一致していると判断される場合の類似性が高くなります。 類似性のしきい値は、コンポーネント レベルおよび結合レベルで MinSimilarity プロパティを設定して指定します。 コンポーネント レベルで指定された類似性を満たすには、すべての行がすべての一致に関して、指定された類似性のしきい値以上の類似性を持つ必要があります。 したがって、行レベルまたは結合レベルでの一致が均一に類似していない限り、コンポーネント レベルで非常に類似した一致を指定することはできません。  
  
 一致には、類似スコアおよび信頼スコアが含まれます。 類似スコアは、入力レコードとあいまい参照変換が参照テーブルから返したレコードとのテキストの類似性を数値で表したものです。 信頼スコアは、特定の値が、参照テーブル内で見つかった一致の中で最適の一致である確率を表す数値です。 特定のレコードに割り当てられる信頼スコアは、返された他の一致レコードに依存します。 たとえば、 *St.* と *Saint* の一致の類似スコアは他の一致に関係なく低くなりますが、 *Saint* が返された唯一の一致の場合には、信頼スコアは高くなります。 参照テーブル内に *Saint* と *St.* の両方が存在した場合、 *St.* の信頼スコアが高く、 *Saint* の信頼スコアが低くなります。 ただし、類似スコアが高くても、信頼スコアが高いとは限りません。 たとえば、 *Chapter 4* という値を検索した場合、 *Chapter 1* *Chapter 2* *Chapter 3* が結果として返されて、それぞれの類似スコアは高くなります。しかし、どの結果が最適の一致であるかがはっきりしないため、信頼スコアは低くなります。  
  
 類似スコアは 0 ～ 1 の 10 進値で示されます。類似スコア 1 は、入力列の値と参照テーブルの値が完全に一致していることを表します。 信頼スコアも 0 ～ 1 の 10 進値で、一致の信頼性を表します。 使用できる一致が見つからない行には類似スコアおよび信頼スコアに 0 が割り当てられ、参照テーブルからコピーされる出力列は NULL 値になります。  
  
 あいまい参照では、参照テーブルから適切な一致を見つけられない場合があります。 これは、参照に使用する入力値が単一の短い語の場合などに起こりやすくなります。 たとえば、参照テーブルに *hello* という値がある場合、その列または同じ行の他の列に他のトークンがないと、 *helo* とは一致しません。  
  
 変換の出力列には、パススルー列として指定された入力列、参照テーブルで指定された列が含まれ、次の列が追加されます。  
  
-   **_Similarity**列は、入力列と参照列の値の類似性を表します。  
  
-   **_Confidence**列は、一致の精度を表します。  
  
 変換では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続を使用して、あいまい一致アルゴリズムで使用する一時テーブルを作成します。  
  
## <a name="running-the-fuzzy-lookup-transformation"></a>あいまい参照変換の実行  
 パッケージで最初に変換が実行される場合、参照テーブルがコピーされ、新しいテーブルに整数データ型のキーが追加され、キー列のインデックスが作成されます。 次に、一致インデックスと呼ばれる、参照テーブルのコピーに関するインデックスが作成されます。 一致インデックスには変換の入力列の値をトークン化した結果が格納され、変換では参照操作でこのトークンを使用します。 一致インデックスは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースのテーブルです。  
  
 パッケージが再度、実行された場合、変換では既存の一致インデックスを使用するか、新しいインデックスが作成されます。 参照テーブルが静的であれば、パッケージでは手間のかかるインデックスの再作成プロセスを行わず、データ クリーン セッションを繰り返すことができます。 既存のインデックスを使用するように選択した場合、パッケージが初めて実行されたときにインデックスが作成されます。 複数のあいまい参照変換で同じ参照テーブルを使用する場合、すべて同じインデックスを使用できます。 インデックスを再使用するには、参照操作が同一で、参照に同じ列を使用する必要があります。 インデックスには名前を付けることができ、インデックスを保存する [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続を選択できます。  
  
 変換で一致インデックスが保存されると、この一致インデックスは自動的に維持されます。 つまり、参照テーブルのレコードが更新されるたびに、一致インデックスも更新されます。 一致インデックスを維持することで処理時間を節約できます。これは、パッケージを実行する際に、インデックスを再作成する必要がないからです。 変換が一致インデックスを管理する方法を指定できます。  
  
 次の表に、一致インデックスのオプションを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|**GenerateAndMaintainNewIndex**|新しいインデックスを作成して保存し、維持します。 変換は、参照テーブルとインデックス テーブルの同期を保つためのトリガーを参照テーブルに組み込みます。|  
|**GenerateAndPersistNewIndex**|新しいインデックスを作成し保存しますが、維持はしません。|  
|**GenerateNewIndex**|新しいインデックスを作成しますが、保存しません。|  
|**ReuseExistingIndex**|既存のインデックスを再使用します。|  
  
### <a name="maintenance-of-the-match-index-table"></a>一致インデックス テーブルのメンテナンス  
 **GenerateAndMaintainNewIndex** オプションを指定すると、一致インデックス テーブルと参照テーブルの同期を保つためのトリガーが参照テーブルに組み込まれます。 組み込んだトリガーを削除する必要がある場合は、入力パラメーター値として MatchIndexName プロパティに指定した名前を設定して、 **sp_FuzzyLookupTableMaintenanceUnInstall** ストアド プロシージャを実行する必要があります。  
  
 **sp_FuzzyLookupTableMaintenanceUnInstall** ストアド プロシージャを実行する前に、維持されている一致インデックス テーブルを削除しないでください。 一致インデックス テーブルが削除されると、参照テーブルのトリガーが正しく実行されなくなります。 参照テーブルのトリガーを手動で削除するまで、参照テーブルに対する、以降の更新はすべて失敗します。  
  
 SQL の TRUNCATE TABLE コマンドでは、DELETE トリガーは起動されません。 TRUNCATE TABLE コマンドが参照テーブルに対して使用されると、参照テーブルと一致インデックスが同期されなくなり、あいまい参照変換が失敗します。 一致インデックス テーブルを維持するトリガーが参照テーブルに組み込まれている場合は、TRUNCATE TABLE コマンドではなく、SQL の DELETE コマンドを使用してください。  
  
> [!NOTE]  
>  **[あいまい参照変換エディター]** ダイアログ ボックスの **[参照テーブル]** タブで **[保存されたインデックスを維持する]** を選択すると、変換ではマネージド ストアド プロシージャを使用してインデックスを維持します。 これらのマネージド ストアド プロシージャは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]の共通言語ランタイム (CLR) 統合機能を使用します。 既定では、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の CLR 統合は無効です。 **[保存されたインデックスを維持する]** 機能を使用するには、CLR 統合を有効にする必要があります。 詳細については、「 [CLR 統合の有効化](../../../relational-databases/clr-integration/clr-integration-enabling.md)」を参照してください。  
>   
>  **[保存されたインデックスを維持する]** オプションは CLR 統合を必要とするため、この機能を使用できるのは、CLR 統合が有効になっている [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの参照テーブルを選択した場合だけです。  
  
## <a name="row-comparison"></a>行の比較  
 あいまい参照変換を構成する際には、参照テーブル内の一致するレコードの検索に使用する比較アルゴリズムを指定できます。 [完全] プロパティをに設定すると、変換によって、 `True` 入力内のすべての行が参照テーブルのすべての行と比較されます。 この比較アルゴリズムを使用すると、より正確な結果が生成されますが、参照テーブルの行の数が少ない場合を除けば、処理により多くの時間がかかるようになります。 完全なプロパティがに設定されている場合 `True` 、参照テーブル全体がメモリに読み込まれます。 パフォーマンスの問題を回避するには、パッケージの開発中にのみ、完全なプロパティをに設定することをお勧めし `True` ます。  
  
 完全なプロパティがに設定されている場合 `False` 、あいまい参照変換は、少なくとも1つのインデックス付きトークンまたは部分文字列 (部分文字列が*q&a*と呼ばれます) を持つ一致のみを入力レコードと共に返します。 参照の効率を最大にするために、あいまい参照変換が一致の検索に使用する逆インデックス構造で、テーブルの各行に含まれたトークンのサブセットにのみインデックス付けが行われます。 入力データセットが小さい場合は、完全にをに設定して、 `True` インデックステーブルに共通のトークンが存在しない一致が見つからないようにすることができます。  
  
## <a name="caching-of-indexes-and-reference-tables"></a>インデックス テーブルと参照テーブルのキャッシュ  
 あいまい参照変換の設定時に、インデックス テーブルと参照テーブルの一部を、変換を開始する前にメモリにキャッシュするかどうかを指定できます。 "表示" プロパティをに設定すると `True` 、インデックスと参照テーブルがメモリに読み込まれます。 入力に多数の行が含まれている場合、"出力" プロパティをに設定すると、 `True` 変換のパフォーマンスが向上します。 入力行の数が少ない場合は、"make Mcache" プロパティをに設定すると、 `False` 大きなインデックスを再利用できるようになります。  
  
## <a name="temporary-tables-and-indexes"></a>一時テーブルおよびインデックス  
 あいまい参照変換の実行時には、変換の接続先の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベース内に、テーブルやインデックスなどの一時オブジェクトが作成されます。 これらの一時テーブルとインデックスのサイズは、参照テーブルの行数とトークン数や、あいまい参照変換が作成するトークン数に比例します。したがって、膨大なディスク容量を消費する可能性もあります。 また、変換はこれらの一時テーブルに対してクエリを実行します。 このため、特に稼働サーバーのディスク容量が少ない場合は、あいまい参照変換を [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースの非稼働インスタンスに接続することを検討してください。  
  
 この変換で使用するテーブルおよびインデックスがローカル コンピューター上にあると、変換のパフォーマンスが向上する可能性があります。 あいまい参照変換が使用する参照テーブルが稼働サーバー上にある場合は、テーブルを非稼働サーバーにコピーして、あいまい参照変換がこのコピーにアクセスするように設定することを検討してください。 こうすることで、参照クエリによって稼働サーバーのリソースが消費されるのを回避できます。 また、MatchIndexOptionsis が **GenerateAndMaintainNewIndex** に設定されていて、あいまい参照変換で一致インデックスが維持されている場合は、データ クリーン操作中に参照テーブルがロックされ、他のユーザーやアプリケーションはテーブルにアクセスできません。  
  
## <a name="configuring-the-fuzzy-lookup-transformation"></a>あいまい参照変換の設定  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[あいまい参照変換エディター]** ダイアログ ボックスで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [あいまい参照変換エディター ([参照テーブル] タブ)](../../fuzzy-lookup-transformation-editor-reference-table-tab.md)  
  
-   [あいまい参照変換エディター ([列] タブ)](../../fuzzy-lookup-transformation-editor-columns-tab.md)  
  
-   [[あいまい参照変換エディター] &#40;[詳細設定] タブ&#41;](../../fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [Common Properties](../../common-properties.md)  
  
-   [変換のカスタム プロパティ](transformation-custom-properties.md)  
  
## <a name="related-tasks"></a>Related Tasks  
 データ フロー コンポーネントのプロパティの設定方法の詳細については、「 [データ フロー コンポーネントのプロパティを設定する](../set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [参照変換](lookup-transformation.md)   
 [あいまいグループ化変換](fuzzy-grouping-transformation.md)   
 [Integration Services の変換](integration-services-transformations.md)  
  
  