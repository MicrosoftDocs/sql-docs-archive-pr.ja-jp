---
title: SQL Server の最大容量仕様 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- objects [SQL Server]
- number capacity specifications [SQL Server]
- size [SQL Server], capacity specifications
- number of objects
- capacity specifications [SQL Server]
- maximum capacity specifications [SQL Server]
- size [SQL Server]
- replication capacity specifications [SQL Server]
- objects [SQL Server], capacity specifications
- Database Engine [SQL Server], capacity specifications
ms.assetid: 13e95046-0e76-4604-b561-d1a74dd824d7
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3e7780d94e49199010fcd45d20389ce380d145ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640339"
---
# <a name="maximum-capacity-specifications-for-sql-server"></a>SQL Server の最大容量仕様
  次の各表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] コンポーネントで定義される各種オブジェクトの最大サイズと最大数を示します。 各 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] テクノロジの表に移動するには、それぞれのリンクをクリックしてください。  
  
 [SQL Server データベース エンジン オブジェクト](#Engine)  
  
 [SQL Server ユーティリティ オブジェクト](#Utility)  
  
 [SQL Server データ層アプリケーション オブジェクト](#DAC)  
  
 [SQL Server レプリケーション オブジェクト](#Replication)  
  
##  <a name="ssde-objects"></a><a name="Engine"></a>[!INCLUDE[ssDE](../includes/ssde-md.md)]オブジェクト  
 次の表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データベースで定義される各種オブジェクト、または [!INCLUDE[tsql](../includes/tsql-md.md)] ステートメントで参照される各種オブジェクトの最大サイズと最大数を示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] オブジェクト|最大サイズ/最大数 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 ビット)|最大サイズ/最大数 ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 64 ビットの場合)|  
|---------------------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|バッチ サイズ<br /><br /> 注: ネットワークパケットサイズは、アプリケーションとリレーショナルの間の通信に使用される表形式のデータストリーム (TDS) パケットのサイズ [!INCLUDE[ssDE](../includes/ssde-md.md)] です。 既定のパケット サイズは 4 KB であり、network packet size 構成オプションによって制御されます。|65,536 * ネットワーク パケット サイズ|65,536 * ネットワーク パケット サイズ|  
|通常の string 列ごとのバイト数|8,000|8,000|  
|GROUP BY、ORDER BY ごとのバイト数|8,060|8,060|  
|インデックス キーごとのバイト数<br /><br /> 注: インデックスキーの最大バイト数は、の900を超えることはできません [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。 最大サイズの合計が 900 を超えるような組み合わせで複数の可変長列を使用してキーを定義することは可能ですが、これらの列のデータが 900 バイトを超えるような行が挿入されないことが条件です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、インデックス キーが最大サイズ制限の 900 バイトを超えないように、非クラスター化インデックスに非キー列を含めることができます。|900|900|  
|外部キーごとのバイト数|900|900|  
|主キーごとのバイト数|900|900|  
|行ごとのバイト数<br /><br /> 注:<br />        [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 行オーバーフロー ストレージがサポートされています。これにより、可変長列の行外への移動が可能になります。 行外に移動される可変長列のうち、ルートの 24 バイトだけが本体のレコードに格納されます。これにより、実際の行制限は、以前のリリースの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]よりも大きい値になります。 詳細については、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] オンライン ブックの「8 KB を超える場合の行オーバーフロー データ」を参照してください。|8,060|8,060|  
|メモリ最適化テーブル内の行ごとのバイト数<br /><br /> 注:<br />        [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インメモリ OLTP では、行オーバーフロー ストレージがサポートされていません。 可変長列は行外にプッシュされません。 この結果、メモリ最適化テーブルで指定できる可変長列の最大の幅が、最大行サイズに制限されます。 詳細については、「 [メモリ最適化テーブルのテーブルと行のサイズ](../relational-databases/in-memory-oltp/table-and-row-size-in-memory-optimized-tables.md)」を参照してください。|サポートされていません|8,060|  
|ストアド プロシージャのソース テキスト内のバイト数|バッチ サイズまたは 250 MB のいずれか小さい方|バッチ サイズまたは 250 MB のいずれか小さい方|  
|`varchar(max)`、`varbinary(max)`、`xml`、`text`、または `image` 列ごとのバイト数|2^31-1|2^31-1|  
|`ntext` または `nvarchar(max)` 列ごとの文字数|2^30-1|2^30-1|  
|テーブルごとのクラスター化インデックス数|1|1|  
|GROUP BY、ORDER BY の列数|バイト数のみによって制限されます。|バイト数のみによって制限されます。|  
|GROUP BY WITH CUBE または WITH ROLLUP ステートメント内の列または式の数|10|10|  
|インデックス キーごとの列数<br /><br /> 注: テーブルに1つ以上の XML インデックスが含まれている場合、XML 列がプライマリ XML インデックスのクラスター化キーに追加されるため、ユーザーテーブルのクラスター化キーは15列に制限されます。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、キー列数が最大キー列数制限の 16 を越えないように、非クラスター化インデックスに非キー列を含めることができます。 詳細については、「 [付加列インデックスの作成](../relational-databases/indexes/create-indexes-with-included-columns.md)」を参照してください。|16|16|  
|外部キーごとの列数|16|16|  
|主キーごとの列数|16|16|  
|幅の狭いテーブルごとの列数|1,024|1,024|  
|幅の広いテーブルごとの列数|30,000|30,000|  
|SELECT ステートメントごとの列数|4,096|4,096|  
|INSERT ステートメントごとの列数|4096|4096|  
|クライアントごとの接続数|構成した接続の最大値|構成した接続の最大値|  
|データベース サイズ|524,272 テラバイト|524,272 テラバイト|  
|インスタンスごとのデータベース数 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|32,767|32,767|  
|データベースごとのファイル グループ数|32,767|32,767|  
|メモリ最適化データに対応する、データベースごとのファイル グループ|サポートされていません|1|  
|データベースごとのファイル数|32,767|32,767|  
|ファイル サイズ (データ)|16 テラバイト|16 テラバイト|  
|ファイル サイズ (ログ)|2 テラバイト|2 テラバイト|  
|データベースごとのメモリ最適化データに対応するデータ ファイル|サポートされていません|4.096|  
|メモリ最適化データに対応するデータ ファイルごとのデルタ ファイル|サポートされていません|1|  
|テーブルごとの外部キー テーブル参照数<br /><br /> 注: テーブルに含めることができる FOREIGN KEY 制約の数に制限はありませんが、推奨される最大値は253です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] をホストするハードウェア構成によっては、追加の FOREIGN KEY 制約を指定するとクエリ オプティマイザーの処理が遅くなる可能性があります。|253|253|  
|識別子長 (文字数)|128|128|  
|コンピューターごとのインスタンス数|すべての [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] エディションでは、スタンドアロン サーバー上に 50 個のインスタンス。<br /><br /> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]では、共有クラスターディスクを使用する場合、フェールオーバークラスターで25個のインスタンスがサポートされます。クラスターインストールの格納オプションとして共有クラスターディスクを使用する場合は [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 、フェールオーバークラスター上の50インスタンスがサポートされます。詳細については、クラスターインストールのストレージオプションとして SMB ファイル共有を選択した場合は、 [2014 SQL Server](install/hardware-and-software-requirements-for-installing-sql-server.md)|スタンドアロン サーバー上に 50 個のインスタンス。<br /><br /> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] では、クラスター インストールのストレージ オプションとして共有クラスター ディスクを使用する場合、フェールオーバー クラスター上に 25 個のインスタンスがサポートされます。クラスター インストールのストレージ オプションとして SMB ファイル共有を選択する場合は、フェールオーバー クラスター上に 50 個のインスタンスがサポートされます。|  
|メモリ最適化テーブルごとのインデックス|サポートされていません|8|  
|SQL ステートメントが含まれた文字列の長さ (バッチ サイズ)<br /><br /> 注: ネットワークパケットサイズは、アプリケーションとリレーショナルの間の通信に使用される表形式のデータストリーム (TDS) パケットのサイズ [!INCLUDE[ssDE](../includes/ssde-md.md)] です。 既定のパケット サイズは 4 KB であり、network packet size 構成オプションによって制御されます。|65,536 * ネットワーク パケット サイズ|65,536 * ネットワーク パケット サイズ|  
|接続ごとのロック数|サーバーごとの最大ロック数|サーバーごとの最大ロック数|  
|のインスタンスごとのロック数 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]<br /><br /> 注: この値は、静的ロック割り当て用です。 動的ロックの場合は、メモリのみによって制限されます。|最大 2,147,483,647|メモリのみによって制限されます。|  
|ストアド プロシージャの入れ子レベル数<br /><br /> 注: ストアドプロシージャが1つ以上のデータベースにアクセスするか、インターリーブ中に2つ以上のデータベースに64アクセスすると、エラーが発生します。|32|32|  
|入れ子にしたサブクエリの数|32|32|  
|トリガーの入れ子レベル数|32|32|  
|テーブルごとの非クラスター化インデックス数|999|999|  
|GROUP BY 句に含まれる個別の式の数 (CUBE、ROLLUP、GROUPING SETS、WITH CUBE、または WITH ROLLUP のいずれかが存在する場合)|32|32|  
|GROUP BY 句内の演算子によって生成されるグループ化セットの数|4,096|4,096|  
|ストアド プロシージャごとのパラメーター数|2,100|2,100|  
|ユーザー定義関数ごとのパラメーター数|2,100|2,100|  
|テーブルごとの参照数|253|253|  
|テーブルごとの行数|使用可能な記憶領域によって制限されます。|使用可能な記憶領域によって制限されます。|  
|データベースごとのテーブル数<br /><br /> 注: データベースオブジェクトには、テーブル、ビュー、ストアドプロシージャ、ユーザー定義関数、トリガー、ルール、既定値、制約などのオブジェクトが含まれます。 1 つのデータベース内のオブジェクトの合計数は 2,147,483,647 以下にする必要があります。|データベース内のオブジェクト数によって制限されます。|データベース内のオブジェクト数によって制限されます。|  
|パーティション テーブルまたはインデックスごとのパーティション数|1,000<br /><br /> 重要1000パーティションを含むテーブルまたはインデックスの作成は32ビットシステムでは可能ですが、サポートされていません。 ** \* \* \* \* **|15,000|  
|インデックス付けされていない列の統計|30,000|30,000|  
|SELECT ステートメントごとのテーブル数|使用可能なリソースのみによって制限されます。|使用可能なリソースのみによって制限されます。|  
|テーブルごとのトリガー数<br /><br /> 注: データベースオブジェクトには、テーブル、ビュー、ストアドプロシージャ、ユーザー定義関数、トリガー、ルール、既定値、制約などのオブジェクトが含まれます。 1 つのデータベース内のオブジェクトの合計数は 2,147,483,647 以下にする必要があります。|データベース内のオブジェクト数によって制限されます。|データベース内のオブジェクト数によって制限されます。|  
|UPDATE ステートメント (幅の広いテーブル) ごとの列数|4096|4096|  
|ユーザー接続数|32,767|32,767|  
|XML インデックス数|249|249|  
  
##  <a name="ssnoversion-utility-objects"></a><a name="Utility"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ユーティリティオブジェクト  
 次の表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティでテストされた各種オブジェクトの最大サイズと最大数を示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティ オブジェクト|最大サイズ/最大数 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 ビット)|最大サイズ/最大数 ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 64 ビットの場合)|  
|----------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティごとのコンピューター数 (物理コンピューターまたは仮想マシン)|100|100|  
|コンピューターごとの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス数|5|5|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティごとの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンス総数|200*|200*|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のインスタンス (データ層アプリケーションを含む) ごとのユーザー データベース数|50|50|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーティリティごとのユーザー データベース総数|1,000|1,000|  
|データベースごとのファイル グループ数|1|1|  
|ファイル グループごとのデータ ファイル数|1|1|  
|データベースごとのログ ファイル数|1|1|  
|コンピューターごとのボリューム数|3|3|  
  
 * ユーティリティでサポートされるのマネージインスタンスの最大数は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] サーバーのハードウェア構成によって異なる場合があります。 概要情報については、「 [SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md)」を参照してください。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]ユーティリティコントロールポイントは、のすべてのエディションで使用できるわけではありません [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。 の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。  
  
##  <a name="ssnoversion-data-tier-application-objects"></a><a name="DAC"></a>[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]データ層アプリケーションオブジェクト  
 次の表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] データ層アプリケーション (DAC) でテストされた各種オブジェクトの最大サイズと最大数を示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] DAC オブジェクト|最大サイズ/最大数 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (32 ビット)|最大サイズ/最大数 ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 64 ビットの場合)|  
|------------------------------------------|------------------------------------------------------------------|------------------------------------------------------------------|  
|DAC ごとのデータベース数|1|1|  
|DAC ごとのオブジェクト数*|データベース内のオブジェクト数または使用可能なメモリによって制限されます。|データベース内のオブジェクト数または使用可能なメモリによって制限されます。|  
  
 *制限の対象となるオブジェクトの種類は、ユーザー、テーブル、ビュー、ストアド プロシージャ、ユーザー定義関数、ユーザー定義データ型、データベース ロール、スキーマ、およびユーザー定義テーブル型です。  
  
##  <a name="replication-objects"></a><a name="Replication"></a>レプリケーションオブジェクト  
 次の表に、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レプリケーションで定義される各種オブジェクトの最大サイズと最大数を示します。  
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レプリケーション オブジェクト|最大サイズ/最大数 (SQL Server 32 ビットの場合)|最大サイズ/最大数 (SQL Server 64 ビットの場合)|  
|--------------------------------------------------|---------------------------------------------------|---------------------------------------------------|  
|アーティクル数 (マージ パブリケーション)|256|256|  
|アーティクル数 (スナップショットまたはトランザクション パブリケーション)|32,767|32,767|  
|テーブル内の列数* (マージ パブリケーション)|246|246|  
|テーブル内の列数** ([!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のスナップショットまたはトランザクション パブリケーション)|1,000|1,000|  
|テーブル内の列数** (Oracle のスナップショットまたはトランザクション パブリケーション)|995|995|  
|行フィルターで使用される列のバイト数 (マージ パブリケーション)|1,024|1,024|  
|行フィルターで使用される列のバイト数 (スナップショットまたはトランザクション パブリケーション)|8,000|8,000|  
  
 *行レベルの追跡を使用して競合を検出する場合 (既定値)、ベース テーブルには最大 1,024 列含めることができますが、最大 246 列がパブリッシュされるようにアーティクルから列をフィルター選択する必要があります。 列の追跡を使用する場合、ベース テーブルには最大 246 列を含めることができます。  
  
 **ベース テーブルには、パブリケーション データベースで許容される最大数 ( [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]の場合は 1,024) の列を含めることができますが、列数がパブリケーション タイプに対して指定された最大数を超える場合は、アーティクルから列をフィルター選択する必要があります。  
  
## <a name="see-also"></a>参照  
 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](install/hardware-and-software-requirements-for-installing-sql-server.md)   
 [システム構成チェッカーのパラメーターの確認](../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md)   
 [SQL Server ユーティリティの機能とタスク](../relational-databases/manage/sql-server-utility-features-and-tasks.md)  
  
  
