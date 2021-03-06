---
title: bcp を使用したファイル ストレージ型の指定 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- bcp utility [SQL Server], file storage types
- importing data, file storage types
- native data format [SQL Server]
- file storage types [SQL Server]
- data formats [SQL Server], file storage types
ms.assetid: 85e12df8-1be7-4bdc-aea9-05aade085c06
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c1f3ad2a94ffe3e0f1db19a8e66f85497e7143dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632469"
---
# <a name="specify-file-storage-type-by-using-bcp-sql-server"></a>bcp を使用したファイル ストレージ型の指定 (SQL Server)
  *ファイル ストレージ型* は、データ ファイルへのデータの格納方法を記述します。 データ ファイルには、データベース テーブルの型 (ネイティブ形式)、文字表現 (文字形式)、または暗黙的な型変換がサポートされているデータ型のいずれかでデータをエクスポートできます。暗黙的な型変換では、たとえば、`smallint` は `int` としてコピーされます。 ユーザー定義のデータ型は、基本データ型としてエクスポートされます。  
  
## <a name="the-bcp-prompt-for-file-storage-type"></a>ファイル ストレージ型の bcp プロンプト  
 対話型の **bcp** コマンドで、フォーマット ファイル スイッチ ( **-f** ) またはデータ形式スイッチ ( **-n** 、 **-c**、 **-w**、または **-N**) のどちらも付けずに **in**または **out**オプションを指定すると、次のように各データ フィールドのファイル ストレージ型を要求するプロンプトが表示されます。  
  
 `Enter the file storage type of field <field_name> [<default>]:`  
  
 この要求への応答は、次のように、実行するタスクによって異なります。  
  
-   できるだけコンパクトなストレージ型 (ネイティブ データ形式) で [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするには、**bcp** によって提供される既定のファイル ストレージ型をそのまま使用します。 ネイティブのファイル ストレージ型の一覧については、このトピックの「ネイティブのファイル ストレージ型」を参照してください。  
  
-   文字形式で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするには、テーブルのすべての列にファイル ストレージ型として `char` を指定します。  
  
-   データ ファイルから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスにデータを一括インポートするには、文字形式で格納されたデータの場合はファイル ストレージ型として `char` を指定し、ネイティブ データ型形式で格納されたデータの場合は、必要に応じて次のファイル ストレージ型のいずれかを指定します。  
  
    |ファイル ストレージ型|コマンド プロンプトで入力する文字|  
    |-----------------------|-----------------------------|  
    |`char` <sup>1</sup>|`c`[`har`]|  
    |`varchar`|`c[har]`|  
    |`nchar`|`w`|  
    |`nvarchar`|`w`|  
    |`text` <sup>2</sup>|`T`[`ext`]|  
    |`ntext2`|`W`|  
    |`binary`|`x`|  
    |`varbinary`|`x`|  
    |`image` <sup>2</sup>|`I`[`mage`]|  
    |`datetime`|**d[ate]**|  
    |`smalldatetime`|`D`|  
    |`time`|`te`|  
    |`date`|`de`|  
    |`datetime2`|`d2`|  
    |`datetimeoffset`|`do`|  
    |`decimal`|`n`|  
    |`numeric`|`n`|  
    |`float`|**f[loat]**|  
    |`real`|`r`|  
    |`Int`|**i[nt]**|  
    |`bigint`|`B[igint]`|  
    |`smallint`|**s[mallint]**|  
    |`tinyint`|**t[inyint]**|  
    |`money`|**m[oney]**|  
    |`smallmoney`|`M`|  
    |`bit`|`b[it]`|  
    |`uniqueidentifier`|`u`|  
    |`sql_variant`|`V[ariant]`|  
    |`timestamp`|`x`|  
    |`UDT` (ユーザー定義データ型)|`U`|  
    |`XML`|`X`|  
  
     <sup>1</sup>フィールド長、プレフィックス長、およびターミネータの相互作用によって、ファイルストレージ型としてエクスポートされた非文字データのデータファイルに割り当てられる記憶域の容量が決まり `char` ます。  
  
     <sup>2</sup> `ntext` 、 `text` 、および `image` の各データ型は、の将来のバージョンで削除される予定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] です。 新しい開発作業ではこれらのデータ型の使用を避け、現在このデータ型を使用しているアプリケーションは変更を検討してください。 代わりに `nvarchar(max)`、`varchar(max)`、および `varbinary(max)` 型を使用してください。  
  
## <a name="native-file-storage-types"></a>ネイティブのファイル ストレージ型  
 各ネイティブのファイル ストレージ型は、対応するホスト ファイル データ型として、フォーマット ファイルに記録されます。  
  
|ファイル ストレージ型|ホスト ファイル データ型|  
|-----------------------|-------------------------|  
|`char` <sup>1</sup>|SQLCHAR|  
|`varchar`|SQLCHAR|  
|`nchar`|SQLNCHAR|  
|`nvarchar`|SQLNCHAR|  
|`text` <sup>2</sup>|SQLCHAR|  
|`ntext` <sup>2</sup>|SQLNCHAR|  
|`binary`|SQLBINARY|  
|`varbinary`|SQLBINARY|  
|`image` <sup>2</sup>|SQLBINARY|  
|`datetime`|SQLDATETIME|  
|`smalldatetime`|SQLDATETIM4|  
|`decimal`|SQLDECIMAL|  
|`numeric`|SQLNUMERIC|  
|`float`|SQLFLT8|  
|`real`|SQLFLT4|  
|`int`|SQLINT|  
|`bigint`|SQLBIGINT|  
|`smallint`|SQLSMALLINT|  
|`tinyint`|SQLTINYINT|  
|`money`|SQLMONEY|  
|`smallmoney`|SQLMONEY4|  
|`bit`|SQLBIT|  
|`uniqueidentifier`|SQLUNIQUEID|  
|`sql_variant`|SQLVARIANT|  
|`timestamp`|SQLBINARY|  
|UDT (ユーザー定義データ型)|SQLUDT|  
  
 1文字形式で格納された<sup>1 つ</sup>のデータファイルは `char` 、ファイルストレージ型として使用されます。 したがって、文字データ ファイルの場合、フォーマット ファイルに表示されるデータ型は SQLCHAR のみです。  
  
 <sup>2</sup> `text` `ntext` `image` 既定値が設定されている、、およびの各列にデータを一括インポートすることはできません。  
  
## <a name="additional-considerations-for-file-storage-types"></a>ファイル ストレージ型のその他の考慮事項  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからデータ ファイルにデータを一括エクスポートするときは、次のことを考慮してください。  
  
-   `char` 型は、常にファイル ストレージ型として指定できます。  
  
-   無効な暗黙的な変換を表すファイルストレージ型を入力すると、 **bcp**は失敗します。たとえば、データにを指定することはできますが、 `int` `smallint` データにを指定すると `smallint` `int` 、オーバーフローエラーが発生します。  
  
-   `float`、`money`、`datetime`、または `int` などの非文字データ型をそれぞれのデータベース型として格納すると、データが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブ形式でデータ ファイルに書き込まれます。  
  
    > [!NOTE]  
    >  **bcp** コマンドですべてのフィールドを対話形式で指定すると、各フィールドへの応答を XML 形式以外のファイルに保存するように要求するプロンプトが表示されます。 XML 以外のフォーマット ファイルの詳細については、「[XML 以外のフォーマット ファイル &#40;SQL Server&#41;](xml-format-files-sql-server.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)   
 [bcp を使用したフィールド長の指定 &#40;SQL Server&#41;](specify-field-length-by-using-bcp-sql-server.md)   
 [フィールド ターミネータと行ターミネータの指定 &#40;SQL Server&#41;](specify-field-and-row-terminators-sql-server.md)   
 [bcp を使用したデータ ファイルのプレフィックス長の指定 &#40;SQL Server&#41;](specify-prefix-length-in-data-files-by-using-bcp-sql-server.md)  
  
  
