---
title: リテラル (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- string literals
- numeric literals [Integration Services]
- Boolean literals
- expressions [Integration Services], literals
- literals [Integration Services]
- mapping literals [Integration Services]
ms.assetid: a980cd52-54ef-4b9c-b00c-e6807cf8e01f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b553b4f5ebc51c8252136ecbb6317b7e7228f246
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718614"
---
# <a name="literals-ssis"></a>リテラル (SSIS)
  式には、数値、文字列、およびブール値のリテラルを含めることができます。 式エバリュエーターでは、整数、10 進数、浮動小数点定数など、さまざまな数値リテラルがサポートされます。 さらに、式エバリュエーターが値を処理する方法を指定する long 型および float 型サフィックスと、数値リテラルの科学的表記法がサポートされます。  
  
## <a name="numeric-literals"></a>数値リテラル  
 式エバリュエーターでは、整数および非整数の数値データ型がサポートされます。 また、パッケージ要素における一意の数値識別子である、系列 ID もサポートされています。 系列 ID は数値ですが、数学的演算には使用できません。  
  
 式エバリュエーターではサフィックスがサポートされます。サフィックスを使用すると、式エバリュエーターが数値リテラルを処理する方法を示すことができます。 たとえば、37L または 37l と記述することにより、整数 37 を long 型の整数データ型として処理することを示すことができます。  
  
 次の表に、数値リテラルのサフィックスの一覧を示します。  
  
|サフィックス|説明|  
|------------|-----------------|  
|L または l|long 型数値リテラル。|  
|U または u|符号なし数値リテラル。|  
|E または e|科学的表記法における指数。|  
  
 次の表に、数値式の要素とその正規表現の一覧を示します。  
  
|式の要素|正規表現|説明|  
|------------------------|------------------------|-----------------|  
|D で表現される数字。|[0-9]|任意の数字です。|  
|E で表現される科学的表記法。|[Ee][+-]?{D}+|大文字と小文字の e、+ または - (オプション)、および D で定義された 1 個以上の数字です。|  
|IS で表現される整数サフィックス。|(([lL]?[uU]?)&#124;([uU]?[lL]?))|必要に応じて、大文字または小文字の u および l、または u と l の組み合わせを使用します。 U または u は、符号なしの値を示します。 L または l は、long 型の値を示します。|  
|FS で表現される float 型サフィックス。|([f&#124;F]&#124;[l&#124;L])|大文字または小文字の f または l です。 F または f は、float 型の値 (DT_R4 データ型) を示します。 L または l は、long 型の値 (DT_R8 データ型) を示します。|  
|H で表現される 16 進数字。|[a-fA-F0-9]|任意の 16 進数字です。|  
  
 次の表では、正規表現言語を使用した有効な数値リテラルについて説明します。  
  
|正規表現|説明|  
|------------------------|-----------------|  
|{D}+{IS}|1 個以上の数字 (D) を持つ整数の数値リテラルと、long 型または符号なし、あるいはその両方のサフィックス (IS) (オプション) です。  たとえば、457、785u、986L、7945ul などです。|  
|{D}+{E}{FS}|1 個以上の数字 (D) を持つ非整数の数値リテラル、科学的表記法、および long 型または float 型サフィックスです。  たとえば、4E8l、13e-2f、5E+L などです。|  
|{D}*"."{D}+{E}?{FS}|小数点を持つ非整数の数値リテラル、1 個以上の数字 (D) を持つ小数部分、指数 (E) (オプション)、および 1 個の float 型または long 型識別子 (FS) です。 数値リテラルは、DT_R4 データ型または DT_R8 データ型です。  たとえば、6.45E3f、.89E-2l、1.05E+7F などです。|  
|{D}+"."{D}*{E}?{FS}|1 個以上の有効桁 (D) を持つ非整数の数値リテラル、小数点、指数 (E)、および 1 個の float 型または long 型識別子 (FS) です。 数値リテラルは、DT_R4 データ型または DT_R8 データ型です。  たとえば、1.E-4f、4.6E6L、8.365E+2f などです。|  
|{D}*.{D}+|有効桁数と小数点以下桁数を持つ非整数の数値リテラルです。 小数点および 1 個以上の数字 (D) を持つ小数部分が含まれます。 この数値リテラルは、DT_NUMERIC データ型です。  たとえば、.9、5.8、0.346 などです。|  
|{D}+.{D}*|有効桁数と小数点以下桁数を持つ非整数の数値リテラルです。 1 個以上の有効桁 (D) と小数点が含まれます。 この数値リテラルは、DT_NUMERIC データ型です。  たとえば、6.、0.2、8.0 などです。|  
|#{D}+|系列 ID です。 ポンド (#) 文字と 1 個以上の数字 (D) で構成されます。 たとえば、#123 などです。|  
|0[xX]{H}+{uU}|16 進数形式の数値リテラルです。 0、大文字または小文字の x、1 個以上の大文字の 16 進数字 (H)、および符号なしサフィックス (オプション) が含まれます。 たとえば、0xFF0A や 0X000010000U などです。|  
  
 式エバリュエーターが使用するデータ型に関する詳細については、「 [Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。  
  
 式には、異なるデータ型を持つ複数の数値リテラルを含めることができます。 式エバリュエーターがこれらの式を評価する場合、データは互換性のあるデータ型に変換されます。 詳しくは、「 [式における Integration Services データ型](integration-services-data-types-in-expressions.md)」をご覧ください。  
  
 ただし、一部のデータ型の変換には、明示的なキャストが必要な場合があります。 式エバリュエーターでは、データ型の明示的な変換を実行するキャスト演算子が用意されています。 詳細については、「[Cast &#40;SSIS 式&#41;](cast-ssis-expression.md)」をご覧ください。  
  
### <a name="mapping-numeric-literals-to-integration-services-data-types"></a>数値リテラルから Integration Services データ型へのマッピング  
 式エバリュエーターは、数値リテラルの評価を行うときに次の変換を実行します。  
  
-   整数の数値リテラルは、次の integer データ型にマップされます。  
  
    |サフィックス|結果の種類|  
    |------------|-----------------|  
    |なし|DT_I4|  
    |U|DT_UI4|  
    |L|DT_I8|  
    |UL|DT_UI8|  
  
    > [!IMPORTANT]  
    >  long 型 (L または l) サフィックスがない場合、式エバリュエーターは、符号付きの値を DT_I4 データ型にマップし、符号なしの値を DT_UI4 データ型にマップします。値がデータ型でオーバーフローしても、マップは行われます。  
  
-   指数が含まれる数値リテラルは、DT_R4 または DT_R8 データ型のどちらかに変換されます。 long 型サフィックスが含まれる式は DT_R8 データ型に、float 型サフィックスが含まれる式は DT_R4 データ型に変換されます。  
  
-   非整数の数値リテラルに F または f が含まれる場合は、DT_R4 データ型にマップされます。 L または l が含まれ、その数値が整数の場合は、DT_I8 データ型にマップされます。 実数の場合は、DT_R8 データ型にマップされます。 long 型サフィックスが含まれる場合は、DT_R8 データ型に変換されます。  
  
-   有効桁数と小数点以下桁数を持つ非整数の数値リテラルは、DT_NUMERIC データ型にマップされます。  
  
## <a name="string-literals"></a>文字列リテラル  
 文字列リテラルは引用符で囲まれている必要があります。 式言語には、出力されない文字や引用符など、一般的にエスケープされる文字用に、エスケープ シーケンスのセットが用意されています。  
  
 文字列リテラルは、引用符で囲まれた 0 個以上の文字で構成されます。 文字列に引用符が含まれる場合、式を解析するためにはエスケープする必要があります。 \x0000 以外の 2 バイト文字は、すべて文字列として使用できます。\x0000 文字は、文字列の NULL ターミネータです。  
  
 文字列には、エスケープ シーケンスに必要なその他の文字を含めることができます。 次の表に、文字列リテラルのエスケープ シーケンスの一覧を示します。  
  
|エスケープ シーケンス|説明|  
|---------------------|-----------------|  
|\a|警告|  
|\b|バックスペース|  
|\f|フォーム フィード|  
|\n|改行|  
|\r|キャリッジ リターン|  
|\t|水平タブ|  
|\v|垂直タブ|  
|\\"|引用符|  
|\\\|バックスラッシュ|  
|\xhhhh|16 進法で表記された Unicode 文字|  
  
## <a name="boolean-literals"></a>ブール型リテラル  
 式エバリュエーターでは、通常のブール型リテラルの `True` と `False` がサポートされます。 式エバリュエーターでは、大文字と小文字は区別されず、大文字と小文字を組み合わせた任意の文字が使用できます。 たとえば、TRUE は True と同様に機能します。  
  
> [!NOTE]  
>  式では、ブール型リテラルをスペースで区切る必要があります。  
  
## <a name="related-content"></a>関連コンテンツ  
 pragmaticworks.com の技術記事「 [SSIS 式チート シート](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet)」  
  
  