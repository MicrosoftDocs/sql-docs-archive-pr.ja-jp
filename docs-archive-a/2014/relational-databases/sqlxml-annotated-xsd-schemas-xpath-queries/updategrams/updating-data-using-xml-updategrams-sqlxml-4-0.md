---
title: XML アップデートグラムを使用したデータの更新 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- IDREF type attribute [SQLXML]
- before attribute
- <sync> block
- <after> block
- id attribute
- <before> block
- updg:after attribute
- mapping-schema attribute
- IDREFS type attribute [SQLXML]
- updg:id attribute
- multiple record updates
- after attribute
- updategrams [SQLXML], updating data
- updg:before attribute
- record updates [SQLXML]
ms.assetid: 90ef8a33-5ae3-4984-8259-608d2f1d727f
author: rothja
ms.author: jroth
ms.openlocfilehash: 6b019478868b61f293eda824d9b302099728dec4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642700"
---
# <a name="updating-data-using-xml-updategrams-sqlxml-40"></a>XML アップデートグラムを使用した、データの更新 (SQLXML 4.0)
  既存のデータを更新する場合は、ブロックとブロックの両方を指定する必要があり **\<before>** **\<after>** ます。 およびブロックで指定された要素は、 **\<before>** **\<after>** 必要な変更を記述します。 アップデートグラムでは、ブロックに指定されている要素を使用して、 **\<before>** データベース内の既存のレコードを識別します。 ブロック内の対応する要素は、 **\<after>** 更新操作の実行後にレコードがどのように表示されるかを示します。 この情報から、アップデートグラムでは、ブロックと一致する SQL ステートメントが作成され **\<after>** ます。 そのステートメントによってデータベースが更新されます。  
  
 更新操作のアップデートグラムの形式は次のとおりです。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync [mapping-schema="SampleSchema.xml"]  >  
   <updg:before>  
      <ElementName [updg:id="value"] .../>  
      [<ElementName [updg:id="value"] .../> ... ]  
   </updg:before>  
   <updg:after>  
      <ElementName [updg:id="value"] ... />  
      [<ElementName [updg:id="value"] .../> ...]  
   </updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 `<updg:before>`  
 ブロック内の要素は、 **\<before>** データベーステーブル内の既存のレコードを識別します。  
  
 `<updg:after>`  
 ブロック内の要素は、 **\<after>** ブロックに指定されたレコードが **\<before>** 更新プログラムが適用された後にどのように表示されるかを示します。  
  
 `mapping-schema` 属性では、アップデートグラムで使用するマッピング スキーマを指定します。 アップデートグラムでマッピングスキーマを指定する場合は、およびブロックで指定された要素名と属性名 **\<before>** **\<after>** が、スキーマ内の名前と一致している必要があります。 マッピング スキーマでは、これらの要素または属性の名前がデータベース テーブルと列の名前にマップされます。  
  
 アップデートグラムにスキーマを指定しない場合は、アップデートグラムで既定のマッピングが使用されます。 既定のマッピングでは、 **\<ElementName>** アップデートグラムで指定したがデータベーステーブルにマップされ、子要素または属性がデータベース列にマップされます。  
  
 ブロック内の要素は **\<before>** 、データベース内の1つのテーブル行にのみ一致する必要があります。 要素が複数のテーブル行に一致するか、テーブル行と一致しない場合、アップデートグラムはエラーを返し、ブロック全体を取り消し **\<sync>** ます。  
  
 アップデートグラムには、複数のブロックを含めることができ **\<sync>** ます。 各 **\<sync>** ブロックはトランザクションとして扱われます。 各 **\<sync>** ブロックには、複数のおよびブロックを含めることができ **\<before>** **\<after>** ます。 たとえば、既存の2つのレコードを更新する場合は、 **\<before>** **\<after>** 更新するレコードごとに1つずつ、2つのペアを指定できます。  
  
## <a name="using-the-updgid-attribute"></a>updg:id 属性の使用  
 およびブロックに複数の要素が指定されている場合は、 **\<before>** **\<after>** 属性を使用して、 `updg:id` ブロックおよびブロック内の行をマークし **\<before>** **\<after>** ます。 処理ロジックでは、この情報を使用して、ブロック内のどのレコードがブロック内のどのレコードであるかを判断し **\<before>** **\<after>** ます。  
  
 次のいずれかに該当する場合、`updg:id` 属性は必ずしも必要ではありません (ただし使用が推奨されます)。  
  
-   指定したマッピング スキーマの要素に `sql:key-fields` 属性がある。  
  
-   アップデートグラムのキー フィールドに特定の値が 1 つ以上提供されている。  
  
 いずれかに該当する場合、アップデートグラムでは、で指定されたキー列を使用 `sql:key-fields` **\<before>** して、ブロックとブロックの要素をペアにし **\<after>** ます。  
  
 マッピング スキーマで `sql:key-fields` によりキー列が指定されていない場合、またはアップデートグラムでキー列の値を更新する場合は、`updg:id` を指定する必要があります。  
  
 およびブロックで識別されるレコードは、 **\<before>** **\<after>** 同じ順序である必要はありません。 `updg:id`属性は、およびブロックで指定されている要素間の関連付けを強制し **\<before>** **\<after>** ます。  
  
 ブロック内に1つの要素を指定し、 **\<before>** ブロック内に対応する要素を1つだけ指定した場合 **\<after>** 、を使用する `updg:id` 必要はありません。 ただし、あいまいになるのを避けるため、この場合も `updg:id` を指定することをお勧めします。  
  
## <a name="examples"></a>例  
 アップデートグラムの例を使用する前に、次のことに注意してください。  
  
-   ほとんどの例では、アップデートグラムでマッピング スキーマを指定せず、既定のマッピングを使用します。 マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
-   ほとんどの例では、AdventureWorks サンプル データベースを使用します。 すべての更新内容は、このデータベースのテーブルに適用されます。 AdventureWorks データベースは復元できます。  
  
### <a name="a-updating-a-record"></a>A. レコードを更新する  
 次のアップデートグラムでは、AdventureWorks データベースの Person.Contact テーブルで、従業員の姓を Fuller に更新します。 アップデートグラムにマッピング スキーマは指定しないので、既定のマッピングが使用されます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
<updg:sync >  
<updg:before>  
   <Person.Contact ContactID="1" />  
</updg:before>  
<updg:after>  
   <Person.Contact LastName="Abel-Achong" />  
</updg:after>  
</updg:sync>  
</ROOT>  
```  
  
 ブロックに記述されているレコードは、 **\<before>** データベース内の現在のレコードを表します。 アップデートグラムでは、ブロックで指定されたすべての列の値を使用して **\<before>** 、レコードを検索します。 このアップデートグラムでは、 **\<before>** ブロックは ContactID 列のみを提供します。そのため、アップデートグラムでは、値のみを使用してレコードが検索されます。 仮に、このブロックに LastName 値を追加した場合は、検索に ContactID と LastName の両方の値が使用されます。  
  
 このアップデートグラムでは、 **\<after>** 変更されている唯一の値であるため、block は LastName 列の値のみを提供します。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 UpdateLastName.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
### <a name="b-updating-multiple-records-by-using-the-updgid-attribute"></a>B. updg:id 属性を使用して複数のレコードを更新する  
 この例では、アップデートグラムで、AdventureWorks データベースの HumanResources.Shift テーブルに次の 2 つの更新操作を行います。  
  
-   7:00AM から始まる勤務時間の名前を "Day" から "Early Morning" に変更する。  
  
-   10:00AM から始まる、"Late Morning" という名前の新しい勤務時間を挿入する。  
  
 アップデートグラムでは、属性によって、 `updg:id` ブロックとブロックの要素間の関連付けが作成され **\<before>** **\<after>** ます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift updg:id="x" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift updg:id="y" Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
      <HumanResources.Shift updg:id="x" Name="Early Morning" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
 属性が、ブロック `updg:id` 内の要素の最初のインスタンスとブロック \<HumanResources.Shift> 内の **\<before>** 要素の2番目のインスタンスとのペアになっていることに注目 \<HumanResources.Shift> して **\<after>** ください。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 UpdateMultipleRecords.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
### <a name="c-specifying-multiple-before-and-after-blocks"></a>C. 複数 \<before> のブロックとブロックの指定 \<after>  
 あいまいさを避けるために、複数のおよびブロックのペアを使用して、例 B でアップデートグラムを記述でき **\<before>** **\<after>** ます。 **\<before>** とのペアを指定する **\<after>** ことは、少なくとも混乱を最小限に抑えて複数の更新プログラムを指定する方法の1つです。 また、との各ブロックが1つの要素のみを指定している場合は、 **\<before>** 属性を **\<after>** 使用する必要はありません `updg:id` 。  
  
> [!NOTE]  
>  ペアを形成するには、 **\<after>** タグが対応するタグの直後にある必要があり **\<before>** ます。  
  
 次のアップデートグラムでは、最初のとのペアによって、 **\<before>** **\<after>** 日シフトのシフト名が更新されます。 2 番目の組によって新しい勤務時間のレコードが挿入されます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
       <HumanResources.Shift ShiftID="1" Name="Day" />  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Early Morning" />  
    </updg:after>  
    <updg:before>  
    </updg:before>  
    <updg:after>  
      <HumanResources.Shift Name="Late Morning"   
                            StartTime="1900-01-01 10:00:00.000"  
                            EndTime="1900-01-01 18:00:00.000"  
                            ModifiedDate="2004-06-01 00:00:00.000"/>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 UpdateMultipleBeforeAfter.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
### <a name="d-specifying-multiple-sync-blocks"></a>D. 複数の \<sync> ブロックの指定  
 アップデートグラムでは、複数のブロックを指定でき **\<sync>** ます。 指定された各 **\<sync>** ブロックは、独立したトランザクションです。  
  
 次のアップデートグラムでは、最初の **\<sync>** ブロックが Sales. Customer テーブルのレコードを更新します。 簡素化するため、アップデートグラムでは ID 値 (CustomerID) と更新する値 (SalesPersonID) の 2 つの必要な値だけを指定します。  
  
 2番目のブロックは、 **\<sync>** SalesOrderHeader テーブルに2つのレコードを追加します。 このテーブルで、SalesOrderID は IDENTITY 型の列です。 そのため、アップデートグラムでは、各要素の SalesOrderID の値が指定されていません \<Sales.SalesOrderHeader> 。  
  
 複数のブロックを指定する **\<sync>** と便利です。これは、2つ目の **\<sync>** ブロック (トランザクション) が SalesOrderHeader テーブルにレコードを追加できなかった場合でも、最初の **\<sync>** ブロックが sales. customer テーブルの customer レコードを更新する可能性があるためです。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync >  
    <updg:before>  
      <Sales.Customer CustomerID="1" SalesPersonID="280" />  
    </updg:before>  
    <updg:after>  
      <Sales.Customer CustomerID="1" SalesPersonID="283" />  
    </updg:after>  
  </updg:sync>  
  <updg:sync >  
    <updg:before>  
    </updg:before>  
    <updg:after>  
   <Sales.SalesOrderHeader   
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="24643.9362"  
             TaxAmt="1971.5149"  
             Freight="616.0984"  
             rowguid="01010101-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-08 00:00:00.000" />  
   <Sales.SalesOrderHeader  
             CustomerID="1"  
             RevisionNumber="1"  
             OrderDate="2004-07-01 00:00:00.000"  
             DueDate="2004-07-13 00:00:00.000"  
             OnlineOrderFlag="0"  
             ContactID="378"  
             BillToAddressID="985"  
             ShipToAddressID="985"  
             ShipMethodID="5"  
             SubTotal="1000.0000"  
             TaxAmt="0.0000"  
             Freight="0.0000"  
             rowguid="10101010-2222-3333-4444-556677889900"  
             ModifiedDate="2004-07-09 00:00:00.000" />  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 UpdateMultipleSyncs.xml として保存します。  
  
2.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
### <a name="e-using-a-mapping-schema"></a>E. マッピング スキーマを使用する  
 この例では、アップデートグラムで `mapping-schema` を使用してマッピング スキーマを指定します。 ここでは既定のマッピングはなく、アップデートグラム内の要素および属性と、データベースのテーブルおよび列の間の必要なマッピングはマッピング スキーマによって指定します。  
  
 アップデートグラムで指定する要素と属性は、マッピング スキーマ内の要素と属性を参照します。  
  
 次の XSD マッピングスキーマには **\<Customer>** 、 **\<Order>** データベースの **\<OD>** sales. Customer、SalesOrderHeader、および SalesOrderDetail テーブルにマップされる、、およびの各要素があります。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="CustomerOrder"  
          parent="Sales.Customer"  
          parent-key="CustomerID"  
          child="Sales.SalesOrderHeader"  
          child-key="CustomerID" />  
  
    <sql:relationship name="OrderOD"  
          parent="Sales.SalesOrderHeader"  
          parent-key="SalesOrderID"  
          child="Sales.SalesOrderDetail"  
          child-key="SalesOrderID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Customer" sql:relation="Sales.Customer" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="Order"   
                     sql:relation="Sales.SalesOrderHeader"  
                     sql:relationship="CustomerOrder" >  
           <xsd:complexType>  
              <xsd:sequence>  
                <xsd:element name="OD"   
                             sql:relation="Sales.SalesOrderDetail"  
                             sql:relationship="OrderOD" >  
                 <xsd:complexType>  
                  <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
                  <xsd:attribute name="ProductID" type="xsd:integer" />  
                  <xsd:attribute name="UnitPrice" type="xsd:decimal" />  
                  <xsd:attribute name="OrderQty" type="xsd:integer" />  
                  <xsd:attribute name="UnitPriceDiscount" type="xsd:decimal" />   
                 </xsd:complexType>  
                </xsd:element>  
              </xsd:sequence>  
              <xsd:attribute name="CustomerID" type="xsd:string" />  
              <xsd:attribute name="SalesOrderID" type="xsd:integer" />  
              <xsd:attribute name="OrderDate" type="xsd:date" />  
           </xsd:complexType>  
        </xsd:element>  
      </xsd:sequence>  
      <xsd:attribute name="CustomerID"   type="xsd:string" />   
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 このマッピング スキーマ (UpdategramMappingSchema.xml) を次のアップデートグラムで指定します。 このアップデートグラムでは、Sales.SalesOrderDetail テーブルの特定の注文アイテムに、注文明細アイテムを追加します。 このアップデートグラムには、入れ子になった要素 (要素の内側に入れ子になった要素) が含まれ **\<OD>** **\<Order>** ます。 これら 2 つの要素の主キーと外部キーのリレーションシップは、マッピング スキーマで指定されます。  
  
```  
<ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
  <updg:sync mapping-schema="UpdategramMappingSchema.xml" >  
    <updg:before>  
       <Order SalesOrderID="43659" />  
    </updg:before>  
    <updg:after>  
      <Order SalesOrderID="43659" >  
          <OD ProductID="776" UnitPrice="2329.0000"  
              OrderQty="2" UnitPriceDiscount="0.0" />  
      </Order>  
    </updg:after>  
  </updg:sync>  
</ROOT>  
```  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  上のマッピング スキーマをコピーして、テキスト ファイルに貼り付け、 UpdategramMappingSchema.xml として保存します。  
  
2.  上のアップデートグラムのテンプレートをコピーして、テキスト ファイルに貼り付け、 マッピング スキーマ (UpdategramMappingSchema.xml) と同じフォルダーに UpdateWithMappingSchema.xml として保存します。  
  
3.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
 マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
### <a name="f-using-a-mapping-schema-with-idrefs-attributes"></a>F. マッピング スキーマを IDREFS 属性と共に使用する  
 この例では、アップデートグラムでマッピング スキーマ内の IDREFS 属性を使用して、複数のテーブルのレコードを更新する方法を示します。 この例では、データベースは次のテーブルから構成されるものとします。  
  
-   Student (StudentID、LastName)  
  
-   Course (CourseID、CourseName)  
  
-   Enrollment (StudentID、CourseID)  
  
 学生 (Student) は複数の講座 (Course) に登録できるので、Course には複数の Student を含めることができます。3 番目のテーブル Enrollment は、この M:N リレーションシップを表すために必要です。  
  
 次の XSD マッピングスキーマでは、、、およびの各要素を使用して、テーブルの XML ビューを提供し **\<Student>** **\<Course>** **\<Enrollment>** ます。 マッピングスキーマ内の**IDREFS**属性は、これらの要素間のリレーションシップを指定します。 要素の**StudentIDList**属性 **\<Course>** は、登録テーブルの StudentID 列を参照する**IDREFS**型の属性です。 同様に、要素の**EnrolledIn**属性 **\<Student>** は**IDREFS**型の属性であり、登録テーブルの CourseID 列を参照します。  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
<xsd:annotation>  
  <xsd:appinfo>  
    <sql:relationship name="StudentEnrollment"  
          parent="Student"  
          parent-key="StudentID"  
          child="Enrollment"  
          child-key="StudentID" />  
  
    <sql:relationship name="CourseEnrollment"  
          parent="Course"  
          parent-key="CourseID"  
          child="Enrollment"  
          child-key="CourseID" />  
  </xsd:appinfo>  
</xsd:annotation>  
  
  <xsd:element name="Course" sql:relation="Course"   
                             sql:key-fields="CourseID" >  
    <xsd:complexType>  
    <xsd:attribute name="CourseID"  type="xsd:string" />   
    <xsd:attribute name="CourseName"   type="xsd:string" />   
    <xsd:attribute name="StudentIDList" sql:relation="Enrollment"  
                 sql:field="StudentID"  
                 sql:relationship="CourseEnrollment"   
                                     type="xsd:IDREFS" />  
  
    </xsd:complexType>  
  </xsd:element>  
  <xsd:element name="Student" sql:relation="Student" >  
    <xsd:complexType>  
    <xsd:attribute name="StudentID"  type="xsd:string" />   
    <xsd:attribute name="LastName"   type="xsd:string" />   
    <xsd:attribute name="EnrolledIn" sql:relation="Enrollment"  
                 sql:field="CourseID"  
                 sql:relationship="StudentEnrollment"   
                                     type="xsd:IDREFS" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 アップデートグラムでこのスキーマを指定して Course テーブルにレコードを挿入すると、Course テーブルには常に新しい講座レコードが挿入されます。 StudentIDList 属性に 1 つ以上の新しい学生 ID を指定すると、アップデートグラムでは Enrollment テーブルにも新しい学生ごとのレコードが挿入され、 重複した値が追加されていないことが Enrollment テーブルで確認されます。  
  
##### <a name="to-test-the-updategram"></a>アップデートグラムをテストするには  
  
1.  仮想ルートに指定したデータベースに、これらのテーブルを作成します。  
  
    ```  
    CREATE TABLE Student(StudentID varchar(10) primary key,   
                         LastName varchar(25))  
    CREATE TABLE Course(CourseID varchar(10) primary key,   
                        CourseName varchar(25))  
    CREATE TABLE Enrollment(StudentID varchar(10)   
                                      references Student(StudentID),  
                           CourseID varchar(10)   
                                      references Course(CourseID))  
    ```  
  
2.  次のサンプル データを追加します。  
  
    ```  
    INSERT INTO Student VALUES ('S1','Davoli')  
    INSERT INTO Student VALUES ('S2','Fuller')  
  
    INSERT INTO Course VALUES  ('CS101', 'C Programming')  
    INSERT INTO Course VALUES  ('CS102', 'Understanding XML')  
  
    INSERT INTO Enrollment VALUES ('S1', 'CS101')  
    INSERT INTO Enrollment VALUES ('S1', 'CS102')  
    ```  
  
3.  上のマッピング スキーマをコピーして、テキスト ファイルに貼り付け、 SampleSchema.xml として保存します。  
  
4.  上の手順のマッピング スキーマと同じフォルダーに、アップデートグラム (SampleUpdategram) を保存します。 このアップデートグラムでは、講座 CS102 から StudentID="1" の学生を削除します。  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
5.  SQLXML 4.0 テスト スクリプト (Sqlxml4test.vbs) を作成し、それを使用してアップデートグラムを実行します。  
  
     詳細については、「ADO を使用した[SQLXML 4.0 クエリの実行](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)」を参照してください。  
  
6.  上の手順の説明どおり、次のアップデートグラムを保存して実行します。 このアップデートグラムでは、Enrollment テーブルにレコードを追加し、講義 CS102 に StudentID="1" の学生をもう一度追加します。  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101" />  
        </updg:before>  
        <updg:after >  
            <Student updg:id="x" StudentID="S1" LastName="Davolio"  
                                 EnrolledIn="CS101 CS102" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
7.  前の手順の説明どおり、次のアップデートグラムを保存して実行します。 このアップデートグラムでは、新しい学生を 3 人追加し、講座 CS101 に登録します。 ここでもまた、IDREFS リレーションシップによって、Enrollment テーブルにレコードが挿入されます。  
  
    ```  
    <ROOT xmlns:updg="urn:schemas-microsoft-com:xml-updategram">  
      <updg:sync mapping-schema="SampleSchema.xml" >  
        <updg:before>  
           <Course updg:id="y" CourseID="CS101"   
                               CourseName="C Programming" />  
        </updg:before>  
        <updg:after >  
           <Student updg:id="x1" StudentID="S3" LastName="Leverling" />  
           <Student updg:id="x2" StudentID="S4" LastName="Pecock" />  
           <Student updg:id="x3" StudentID="S5" LastName="Buchanan" />  
           <Course updg:id="y" CourseID="CS101"  
                               CourseName="C Programming"  
                               StudentIDList="S3 S4 S5" />  
        </updg:after>  
      </updg:sync>  
    </ROOT>  
    ```  
  
 これは、これと同等の XDR スキーマです。  
  
```  
<?xml version="1.0" ?>  
<Schema xmlns="urn:schemas-microsoft-com:xml-data"  
        xmlns:dt="urn:schemas-microsoft-com:datatypes"  
        xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <ElementType name="Enrollment" sql:relation="Enrollment" sql:key-fields="StudentID CourseID">  
    <AttributeType name="StudentID" dt:type="id" />  
    <AttributeType name="CourseID" dt:type="id" />  
  
    <attribute type="StudentID" />  
    <attribute type="CourseID" />  
  </ElementType>  
  <ElementType name="Course" sql:relation="Course" sql:key-fields="CourseID">  
    <AttributeType name="CourseID" dt:type="id" />  
    <AttributeType name="CourseName" />  
  
    <attribute type="CourseID" />  
    <attribute type="CourseName" />  
  
    <AttributeType name="StudentIDList" dt:type="idrefs" />  
    <attribute type="StudentIDList" sql:relation="Enrollment" sql:field="StudentID" >  
        <sql:relationship  
                key-relation="Course"  
                key="CourseID"  
                foreign-relation="Enrollment"  
                foreign-key="CourseID" />  
    </attribute>  
  
  </ElementType>  
  <ElementType name="Student" sql:relation="Student">  
    <AttributeType name="StudentID" dt:type="id" />  
     <AttributeType name="LastName" />  
  
    <attribute type="StudentID" />  
    <attribute type="LastName" />  
  
    <AttributeType name="EnrolledIn" dt:type="idrefs" />  
    <attribute type="EnrolledIn" sql:relation="Enrollment" sql:field="CourseID" >  
        <sql:relationship  
                key-relation="Student"  
                key="StudentID"  
                foreign-relation="Enrollment"  
                foreign-key="StudentID" />  
    </attribute>  
  
    <element type="Enrollment" sql:relation="Enrollment" >  
        <sql:relationship key-relation="Student"  
                          key="StudentID"  
                          foreign-relation="Enrollment"  
                          foreign-key="StudentID" />  
    </element>  
  </ElementType>  
  
</Schema>  
```  
  
 マッピングスキーマを使用するアップデートグラムの例については、「[アップデートグラムでの注釈付きマッピングスキーマの指定 &#40;SQLXML 4.0&#41;](specifying-an-annotated-mapping-schema-in-an-updategram-sqlxml-4-0.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQLXML 4.0&#41;&#40;アップデートグラムのセキュリティに関する考慮事項](../security/updategram-security-considerations-sqlxml-4-0.md)  
  
  
