---
title: RDL サンドボックスを有効または無効にする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7af1477751093862c99d00978278315e600511e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719617"
---
# <a name="enable-and-disable-rdl-sandboxing"></a>RDL サンドボックスの有効化と無効化
  RDL (レポート定義言語) サンドボックス機能を使用すると、複数のテナントが 1 つのレポート サーバー Web ファームを使用している環境で、個々のテナントによる特定の種類のリソースの使用を検出および制限できるようになります。 このような例として、複数のテナントまたは複数の企業によって使用される単一のレポート サーバー Web ファームを管理するホスティング サービスのシナリオがあります。 レポート サーバー管理者は、次の目的を達成するためにこの機能を有効にできます。  
  
-   外部リソースのサイズを制限する。 外部リソースには、画像、.xslt ファイル、およびマップ データが含まれます。  
  
-   レポートのパブリッシュ時に、式のテキストで使用される型およびメンバーを制限する。  
  
-   レポートの処理時に、テキストの長さおよび式の戻り値のサイズを制限する。  
  
 RDL サンドボックスが有効になると、次の機能は無効になります。  
  
-   **\<Code>** レポート定義の要素内のカスタムコード。  
  
-   [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] カスタム レポート アイテムに対する RDL の下位互換性モード。  
  
-   式での名前付きパラメーター。  
  
 このトピックでは、RSReportServer.Config ファイルの <> 要素内の各要素について説明し `RDLSandboxing` ます。 このファイルの編集の詳細については、「[Reporting Services の構成ファイル &#40;RSreportserver.config&#41; の変更](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)」を参照してください。 RDL サンドボックス機能に関連した操作は、サーバー トレース ログに記録されます。 トレース ログの詳細については、「 [レポート サーバー サービスのトレース ログ](report-server/report-server-service-trace-log.md)」を参照してください。  
  
## <a name="example-configuration"></a>構成の例  
 次の例は、RSReportServer.Config ファイルの <> 要素の設定と例の値を示して `RDLSandboxing` います。  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace="System.Drawing" AllowNew="True">Bitmap</Allow>  
      <Allow Namespace="TypeConverters.Custom" AllowNew="True">*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a>構成設定  
 次の表では、構成設定に関する情報を示します。 構成ファイルに出現する順に、設定を示します。  
  
|設定|Description|  
|-------------|-----------------|  
|**MaxExpressionLength**|RDL 式で許可される文字数の最大値です。<br /><br /> 既定: 1000|  
|**MaxResourceSize**|外部リソースに許可されるサイズの最大値 (単位: KB) です。<br /><br /> 既定値: 100|  
|**MaxStringResultLength**|RDL 式の戻り値で許可される文字数の最大値です。<br /><br /> 既定: 1000|  
|**MaxArrayResultLength**|RDL 式の配列戻り値で許可されるアイテム数の最大値です。<br /><br /> 既定値: 100|  
|**型**|RDL 式内で許可されるメンバーの一覧です。|  
|**許可**|RDL 式で許可される型または型のセットです。|  
|**Namespace**|**Allow** の属性の 1 つであり、Value に適用される 1 つ以上の型を含む名前空間です。 このプロパティでは、大文字と小文字が区別されません。|  
|`AllowNew`|**Allow**のブール属性で、型の新しいインスタンスを rdl 式と rdl 要素のどちらで作成できるかを制御し **\<Class>** ます。<br /><br /> 注: `RDLSandboxing` が有効になっている場合、の設定に関係なく、RDL 式に新しい配列を作成することはできません `AllowNew` 。|  
|**Value**|**Allow** に対する値であり、RDL 式で許可される型の名前を示します。 値は、 **\*** 名前空間のすべての型が許可されることを示します。 このプロパティでは、大文字と小文字が区別されません。|  
|**メンバー**|要素に含まれる型の一覧については、 **\<Types>** RDL 式で許可されないメンバー名の一覧があります。|  
|**Deny**|RDL 式で許可されないメンバーの名前です。 このプロパティでは、大文字と小文字が区別されません。<br /><br /> 注: メンバーに対して **Deny** が指定されている場合、この名前を持つすべての型のメンバーがすべて許可されません。|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a>RDL サンドボックスが有効なときの式の操作  
 式で使用されるリソースの管理を容易にするために、RDL サンドボックス機能を次のような方法で変更できます。  
  
-   式に使用する文字数を制限する。  
  
-   式から返される結果のサイズを制限する。  
  
-   式での使用を許可する特定の型の一覧を指定する。  
  
-   式での使用を許可された型の一覧に対して、制限するメンバーの一覧を名前で指定する。  
  
-   RDL サンドボックス機能では、承認する型の一覧と拒否するメンバーの一覧を作成できます。 承認する型の一覧を許可一覧と呼びます。 拒否するメンバーの一覧をブロック一覧と呼びます。  
  
> [!NOTE]  
>  レポート定義では、式のリファレンスの各インスタンスの型をコンピューターが知ることはできません。 ブロック一覧にメンバーを追加すると、許可一覧に含まれるすべての型について、その名前を持つすべてのメンバーが拒否されます。  
  
 RDL 式の結果は、実行時に検証されます。 RDL 式は、レポートのパブリッシュ時にレポート定義で検証されます。 レポート サーバーのトレース ログで、違反がないかどうかを確認できます。 詳細については、「 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)」を参照してください。  
  
### <a name="working-with-types"></a>型の操作  
 許可一覧に型を追加することで、RDL 式にアクセスする次のエントリ ポイントを制御できます。  
  
-   型の静的メンバー  
  
-   [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` メソッド。  
  
-   **\<Classes>** レポート定義内の要素。  
  
-   許可一覧に含まれる型に対してブロック一覧に追加したメンバー  
  
 許可一覧では、次のエントリ ポイントは制御されません。  
  
-   レポート データセット。 クエリから返されるレポート データセット内のフィールドは、任意の有効な RDL 型を含むことができます。  
  
-   レポート パラメーター。 ユーザーから提供されるパラメーターの値は、任意の有効な RDL 型を含むことができます。  
  
-   ブロック一覧に含まれていない、有効な型のメンバー。 既定では、許可一覧に含まれるすべての型のすべてのメンバーが有効になっています。 ブロック一覧にメンバー名を追加すると、許可一覧に含まれるすべての型について、その名前を持つすべてのメンバーが拒否されます。  
  
 1 つの型のメンバーを有効にして、別の型では同じ名前のメンバーを拒否するには、次の手順を実行する必要があります。  
  
-   **\<Deny>** メンバー名の要素を追加します。  
  
-   有効にするメンバーに対して、カスタム アセンブリのクラスに異なる名前のプロキシ メンバーを作成します。  
  
-   その新しいクラスを許可一覧に追加します。  
  
 許可一覧に [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の関数を追加するには、Microsoft.VisualBasic 名前空間の対応する型を許可一覧に追加します。  
  
 許可一覧に [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の型キーワードを追加するには、対応する CLR 型を許可一覧に追加します。 たとえば、.NET Framework キーワードを使用するには、 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `Integer` 要素に次の XML フラグメントを追加し **\<RDLSandboxing>** ます。  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 許可一覧にジェネリック型または [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の NULL 値を許容する型を追加するには、次の手順を実行します。  
  
-   ジェネリック型または [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の NULL 値を許容する型に対してプロキシ型を作成します。  
  
-   そのプロキシ型を許可一覧に追加します。  
  
 カスタム アセンブリから許可一覧に型を追加しても、アセンブリに対して暗黙に実行権限が付与されることはありません。 コード アクセス セキュリティ ファイルを具体的に変更して、アセンブリに実行権限を提供する必要があります。 詳細については、「 [Reporting Services のコード アクセス セキュリティ](extensions/secure-development/code-access-security-in-reporting-services.md)」を参照してください。  
  
#### <a name="maintaining-the-deny-list-of-members"></a>\<Deny>メンバーの一覧の管理  
 許可一覧に新しい型を追加するときには、次に示す場合に、メンバーのブロック一覧の更新が必要となります。  
  
-   新しい型を導入するバージョンでカスタム アセンブリを更新する場合。  
  
-   許可一覧に含まれる型にメンバーを追加する場合。  
  
-   レポート サーバー上で [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] を更新する場合。  
  
-   レポート サーバーを [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]の新しいバージョンにアップグレードする場合。  
  
-   RDL 型に新しいメンバーが追加された可能性があるため、新しい RDL スキーマを処理できるようにレポート サーバーを更新する場合  
  
### <a name="working-with-operators-and-new"></a>演算子と New の操作  
 既定では、[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework の言語演算子は、`New` を除いて常に許可されます。 `New`演算子は、要素の属性によって制御され `AllowNew` **\<Allow>** ます。 既定のコレクションアクセサー演算子やなどの .NET Framework キャストマクロなど、その他の言語演算子 `!` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `CInt` は常に許可されます。  
  
 カスタム演算子を含め、ブロック一覧への演算子の追加はサポートされていません。 特定の型に対して演算子を除外するには、次の手順を実行する必要があります。  
  
-   除外する演算子を実装しないプロキシ型を作成します。  
  
-   そのプロキシ型を許可一覧に追加します。  
  
 RDL 式に新しい配列を作成するには、定義するクラスのメソッドで配列を作成し、そのクラスを許可一覧に追加します。  
  
 RDL 式に新しい配列を作成するには、次の手順を実行する必要があります。  
  
-   新しいクラスを定義し、そのクラスのメソッドで配列を作成します。  
  
-   このクラスを許可一覧に追加します。  
  
## <a name="see-also"></a>参照  
 [RSReportServer 構成ファイル](report-server/rsreportserver-config-configuration-file.md)   
 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)  
  
  
