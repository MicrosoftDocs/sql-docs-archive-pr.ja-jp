---
title: オブジェクトの名前付け規則 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], naming
ms.assetid: b338a60d-4802-4b68-862a-6dc6a3f75e48
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6adfd4b23b6fe9129641271fc3c2381e161119ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643553"
---
# <a name="object-naming-rules-analysis-services"></a>オブジェクトの名前付け規則 (Analysis Services)
  このトピックでは、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のコードまたはスクリプトにおけるオブジェクトの名前付け規則、および、オブジェクト名で使用できない予約語と文字について説明します。  
  
##  <a name="naming-conventions"></a><a name="bkmk_Names"></a>名前付け規則  
 あらゆるオブジェクトは `Name` プロパティと `ID` プロパティを持ち、これらは親コレクションのスコープ内で一意にする必要があります。 たとえば、所属するデータベースが異なっていれば、2 つのディメンションが同じ名前であってもかまいません。  
  
 手動で指定することもできますが、`ID` は一般にオブジェクトの作成時に自動生成されます。 モデルの構築を開始した後は、`ID` を変更しないでください。 モデル内のオブジェクト参照はすべて `ID` に基づいて実行されます。 したがって、`ID` を変更すると簡単にモデルが壊れます。  
  
 名前付け規則の例外として、`DataSource` オブジェクトと `DataSourceView` オブジェクトに注意してください。 `DataSource` の ID は、現在のデータベースの参照として 1 つのドット (.) に設定でき、これは一意ではありません。 次の例外は、`DataSourceView` で、これは .NET フレームワークの `DataSet` オブジェクト用に定義された名前付け規則に従います。この場合、`Name` が識別子として使用されます。  
  
 `Name` プロパティと `ID` プロパティには、次のルールが適用されます。  
  
-   名前では大文字と小文字は区別されません。 同じデータベース内に "sales" という名前のキューブと "Sales" という名前のキューブを含めることはできません。  
  
-   オブジェクト名の先頭または末尾にスペースを付けることは許されません。ただし名前の途中にスペースを入れることはできます。 先頭および末尾にあるスペースは暗黙的に切り捨てられます。 この規則はオブジェクトの `Name` と `ID` の両方に適用されます。  
  
-   最大文字数は 100 文字です。  
  
-   識別子の最初の文字に関する特別な要件はありません。 最初の文字には、任意の有効な文字を使用できます。  
  
##  <a name="reserved-words-and-characters"></a><a name="bkmk_reserved"></a>予約語と文字  
 予約語は英語で、オブジェクト名に適用されます。キャプションには適用されません。 不注意で予約語をオブジェクト名に使用すると、検証エラーが発生します。 多次元モデルとデータ マイニング モデルでは、どのような場合でも、以下で説明する予約語をオブジェクト名で使用することはできません。  
  
 テーブル モデルでは、データベース互換性が 1103 に設定されている場合、一部のオブジェクトで検証ルールが緩められており、一部のクライアント アプリケーションの拡張文字要件と名前付け規則のためにルールに準拠していません。 これらの条件を満たすデータベースは、厳格でない検証ルールに従います。 この場合、制限された文字がオブジェクト名に使用されていても、検証に合格することがあります。  
  
 **予約語**  
  
-   AUX  
  
-   CLOCK$  
  
-   COM1 ～ COM9 (COM1、COM2、COM3 など)  
  
-   CON  
  
-   LPT1 ～ LPT9 (LPT1、LPT2、LPT3 など)  
  
-   NUL  
  
-   PRN  
  
-   NULL は XML 内の文字列の文字として許容されません。   
  
 **予約文字**  
  
 次の表では、特定のオブジェクトで無効な文字を示します。  
  
|Object|無効な文字|  
|------------|------------------------|  
|`Server`|サーバー オブジェクトに名前を付けるときは、Windows サーバーの名前付け規則に従います。 詳細については、「[名前付け規則 (Windows)](/windows/desktop/DNS/naming-conventions) 」を参照してください。|  
|`DataSource`| `: / \ * \| ? " () [] {} <>` |  
|`Level` または `Attribute`|````. , ; ' ` : / \ * & \| ? " & % $ ! + = [] {} < >````|  
|`Dimension` または `Hierarchy`|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} <,>````|  
|他のすべてのオブジェクト|````. , ; ' ` : / \ * \| ? " & % $ ! + = () [] {} < >````|  
  
 **例外: 予約文字を使用できる場合**  
  
 先に述べたように、特定のモダリティと互換性レベルを持つデータベースでは、予約文字を含むオブジェクト名を使用できます。 拡張文字を使用できる表形式データベース (1103 以上) の場合、ディメンション属性、階層、レベル、メジャー、および KPI オブジェクト名で予約文字を使用できます。  
  
|サーバー モードとデータベース互換性レベル|予約文字を使用できるか|  
|--------------------------------------------------|----------------------------------|  
|MOLAP (すべてのバージョン)|いいえ|  
|表形式-1050|いいえ|  
|表形式 - 1100|いいえ|  
|表形式-1130 以降|はい|  
  
 データベースは既定の ModelType を持つことができます。 既定値は多次元モデルと同等です。そのため、列名での予約文字の使用はサポートされません。  
  
## <a name="see-also"></a>参照  
 [MDX の予約語](/sql/mdx/mdx-reserved-words)   
 [翻訳 &#40;Analysis Services&#41;](/analysis-services/translation-support-in-analysis-services)   
 [XMLA&#41;&#40;XML for Analysis コンプライアンス](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-compliance-xmla)  
  
  
