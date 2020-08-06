---
title: 既存のテーブルを使用してディメンションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Analysis Services], dimensions
- main dimension tables
- dimensions [Analysis Services], standard
- standard dimensions [Analysis Services]
ms.assetid: edd96fbe-1b1c-445a-95d6-7a025e0ee868
author: minewiskan
ms.author: owend
ms.openlocfilehash: 42b236275a6e1543ec0b63cc09a9a1bc06b781f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737050"
---
# <a name="create-a-dimension-by-using-an-existing-table"></a><span data-ttu-id="565ec-102">既存のテーブルを使用したディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="565ec-102">Create a Dimension by Using an Existing Table</span></span>
  <span data-ttu-id="565ec-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、のディメンションウィザードを使用して、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 既存のテーブルからディメンションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a dimension from an existing table.</span></span> <span data-ttu-id="565ec-104">この操作を行うには、ウィザードの **[作成方法の選択]** ページで **[既存のテーブルの使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="565ec-104">You do this by selecting the **Use an existing table** option on the **Select Creation Method** page of the wizard.</span></span> <span data-ttu-id="565ec-105">このオプションを選択すると、ディメンション構造は、ディメンション テーブル、その列、および既存のデータ ソース ビュー内の列間のリレーションシップに基づいて作成されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-105">If you select this option, the wizard bases the dimension structure on the dimension tables, their columns, and any relationships between those columns in an existing data source view.</span></span> <span data-ttu-id="565ec-106">ウィザードでは、ソース テーブルと関連テーブル内のデータが抽出されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-106">The wizard samples the data in the source table and related tables.</span></span> <span data-ttu-id="565ec-107">その後、このデータを使用して、ディメンション テーブル内の列に基づいて属性列を定義したり、属性階層 ( *ユーザー定義* 階層) を定義したりします。</span><span class="sxs-lookup"><span data-stu-id="565ec-107">It uses this data to define attribute columns that are based on the columns in the dimension tables, and to define hierarchies of attributes (called *user-defined* hierarchies).</span></span> <span data-ttu-id="565ec-108">ディメンション ウィザードを使用してディメンションを作成した後、ディメンション デザイナーを使用して、ディメンションの属性と階層を追加、削除、および構成できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-108">After you use the Dimension Wizard to create your dimension, you can use Dimension Designer to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
 <span data-ttu-id="565ec-109">既存のテーブルを使用してディメンションを作成する場合、ディメンション ウィザードでは次の手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-109">When you are using an existing table to create a dimension, the Dimension Wizard guides you through the following:</span></span>  
  
-   <span data-ttu-id="565ec-110">基になる情報の指定</span><span class="sxs-lookup"><span data-stu-id="565ec-110">Specifying the source information</span></span>  
  
-   <span data-ttu-id="565ec-111">関連テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="565ec-111">Selecting related tables</span></span>  
  
-   <span data-ttu-id="565ec-112">ディメンション属性の選択</span><span class="sxs-lookup"><span data-stu-id="565ec-112">Selecting dimension attributes</span></span>  
  
-   <span data-ttu-id="565ec-113">勘定科目インテリジェンスの定義</span><span class="sxs-lookup"><span data-stu-id="565ec-113">Defining account intelligence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="565ec-114">このトピックで説明する情報に対応する手順については、「 [ディメンション ウィザードを使用したディメンションの作成](create-a-dimension-using-the-dimension-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565ec-114">For the step-by-step instructions that correspond to the information presented in this topic, see [Create a Dimension Using the Dimension Wizard](create-a-dimension-using-the-dimension-wizard.md).</span></span>  
  
## <a name="specifying-the-source-information"></a><span data-ttu-id="565ec-115">基になる情報の指定</span><span class="sxs-lookup"><span data-stu-id="565ec-115">Specifying the Source Information</span></span>  
 <span data-ttu-id="565ec-116">基になる情報は、 **[基になる情報の指定]** ページで指定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-116">You specify the source information on the **Specify Source Information** page.</span></span> <span data-ttu-id="565ec-117">このプロセスでは、まず、作成するディメンションの基になるテーブルを含むデータ ソース ビューを選択します。</span><span class="sxs-lookup"><span data-stu-id="565ec-117">You begin this process by selecting the data source view that contains the table on which you want the dimension to be based.</span></span> <span data-ttu-id="565ec-118">次に、定義するディメンションのメイン ディメンション テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-118">You then specify the main dimension table for the dimension that you are defining.</span></span> <span data-ttu-id="565ec-119">メイン ディメンション テーブルとは、ファクト テーブルに直接リンクされるテーブルです。</span><span class="sxs-lookup"><span data-stu-id="565ec-119">The main dimension table is the table that is directly linked to the fact table.</span></span> <span data-ttu-id="565ec-120">たとえば、Products ディメンションには Product テーブルをメイン テーブルとして指定し、Employees ディメンションには Employee テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-120">For example, specify a Product table as the main table for a Products dimension, or an Employee table for an Employees dimension.</span></span> <span data-ttu-id="565ec-121">ウィザードでは、データ ソース ビューの主キーに基づいたキー列が自動的に選択されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-121">The wizard automatically selects a key column that is based on the primary key in the data source view.</span></span> <span data-ttu-id="565ec-122">ただし、キー列は、必要に応じて変更できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-122">However, you can change the key column as appropriate.</span></span> <span data-ttu-id="565ec-123">キー列によってディメンションのメンバーが決まります。</span><span class="sxs-lookup"><span data-stu-id="565ec-123">The key column determines the members of the dimension.</span></span> <span data-ttu-id="565ec-124">たとえば、Product ディメンションのキー列として ProductKey を定義します。</span><span class="sxs-lookup"><span data-stu-id="565ec-124">For example, you would define ProductKey as the key column for a Product dimension.</span></span>  
  
 <span data-ttu-id="565ec-125">必要に応じて、メンバー名を含む列を定義できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-125">Optionally, you can define a column that contains the member name.</span></span> <span data-ttu-id="565ec-126">既定では、ユーザーに表示されるメンバー名がキー列の値です。</span><span class="sxs-lookup"><span data-stu-id="565ec-126">By default, the member name that will be displayed to users is the value from the key column.</span></span> <span data-ttu-id="565ec-127">多くの場合、ProductID や EmployeeID などのキー列の値は、ユーザーにとって意味のない、システムで生成される一意のキーです。</span><span class="sxs-lookup"><span data-stu-id="565ec-127">The values in a key column, such as ProductID or EmployeeID, are often unique, system-generated keys that are meaningless to the user.</span></span> <span data-ttu-id="565ec-128">多くの場合、ユーザーに表示される名前を、ディメンションの他の列の対応する値に変更すると、ユーザーに意味のある情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-128">You can often provide more meaningful information to the user if you change the name that users see to a corresponding value in some other column in the dimension.</span></span> <span data-ttu-id="565ec-129">たとえば、製品名や従業員名を含むメンバー名列を定義できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-129">For example, you can define a member name column that contains product or employee names.</span></span> <span data-ttu-id="565ec-130">メンバー名を変更すると、わかりやすい名前が表示されますが、クエリでは、同じ名前を共有するメンバーを正しく区別するために、引き続きキー列の値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-130">If you change the member name, users see a more descriptive name, but queries still use the key column values to correctly distinguish members that share the same name.</span></span> <span data-ttu-id="565ec-131">キー列に複合キーを指定する場合は、キー属性のメンバーの値を提供する列も指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-131">If you specify a composite key for the key column, you must also specify the column that provides the member values for the key attribute.</span></span> <span data-ttu-id="565ec-132">属性のプロパティを構成する方法の詳細については、「 [ディメンションの属性のプロパティの参照](dimension-attribute-properties-reference.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565ec-132">For more information about how to configure attribute properties, see [Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md).</span></span>  
  
## <a name="selecting-related-tables"></a><span data-ttu-id="565ec-133">関連テーブルの選択</span><span class="sxs-lookup"><span data-stu-id="565ec-133">Selecting Related Tables</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="565ec-134">メイン ディメンション テーブルに他のディメンション テーブルとのリレーションシップがデータ ソース ビューで定義されていない場合は、ウィザードでこの手順が省略されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-134">The wizard skips this step if the main dimension table has no relationships defined in the data source view to other dimension tables.</span></span>  
  
 <span data-ttu-id="565ec-135">スノーフレーク ディメンションを構築している場合は、 **[関連テーブルの選択]** ページで追加属性の定義に使用する関連テーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-135">If you are building a snowflake dimension, you specify the related tables from which additional attributes will be defined on the **Select Related Tables** page.</span></span> <span data-ttu-id="565ec-136">たとえば、顧客の地理テーブルを作成する Customer ディメンションを構築しているとします。</span><span class="sxs-lookup"><span data-stu-id="565ec-136">For example, you are building a customer dimension in which you want to define a customer geography table.</span></span> <span data-ttu-id="565ec-137">この場合、地理テーブルを関連テーブルとして定義します。</span><span class="sxs-lookup"><span data-stu-id="565ec-137">In this case, you might define a geography table as a related table.</span></span>  
  
## <a name="selecting-dimension-attributes"></a><span data-ttu-id="565ec-138">ディメンション属性の選択</span><span class="sxs-lookup"><span data-stu-id="565ec-138">Selecting Dimension Attributes</span></span>  
 <span data-ttu-id="565ec-139">ディメンション テーブルを選択したら、 **[ディメンション属性の選択]** ページを使用して、ディメンションに含める属性をこれらのテーブルから選択します。</span><span class="sxs-lookup"><span data-stu-id="565ec-139">After selecting the dimension tables, you use the **Select Dimension Attributes** page to select the attributes that you want to include in the dimension from these tables.</span></span> <span data-ttu-id="565ec-140">これらすべてのテーブルの基になるすべての列は、ディメンションの属性として使用できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-140">All of the underlying columns from all these tables are available as potential dimension attributes.</span></span> <span data-ttu-id="565ec-141">ディメンション キー属性を選択して、参照を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-141">The dimension key attribute must be selected and enabled for browsing.</span></span>  
  
 <span data-ttu-id="565ec-142">既定では、ウィザードによって属性の型が `Regular` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-142">By default, the wizard sets the type of an attribute to `Regular`.</span></span> <span data-ttu-id="565ec-143">ただし、特定の属性を、データをより適切に表す別の属性型にマップする場合があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-143">However, you might want to map specific attributes to a different attribute type that better represents the data.</span></span> <span data-ttu-id="565ec-144">たとえば、 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW サンプル データベースの dbo.DimAccount テーブルには、勘定科目番号を示す AccountCodeAlternateKey 列があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-144">For example, the dbo.DimAccount table in the [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] DW sample database contains an AccountCodeAlternateKey column that provides the account number.</span></span> <span data-ttu-id="565ec-145">この属性の型をに設定する代わり `Regular` に、この属性を型にマップすることもでき `Account Number` ます。</span><span class="sxs-lookup"><span data-stu-id="565ec-145">Instead of setting the type to `Regular` for this attribute, you might want to map this attribute to the `Account Number` type.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="565ec-146">ディメンションの作成時にディメンションの種類と標準的な属性の型が設定されていない場合は、ディメンションの作成後に、ビジネス インテリジェンス ウィザードを使用して、これらの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-146">If the dimension type and standard attribute types are not set when you create the dimension, use the Business Intelligence Wizard to set these values after you create the dimension.</span></span> <span data-ttu-id="565ec-147">詳しくは、「 [ディメンションへのディメンション インテリジェンスの追加](bi-wizard-add-dimension-intelligence-to-a-dimension.md) 」または (種類が勘定科目ディメンションの場合は)「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="565ec-147">For more information, see [Add Dimension Intelligence to a Dimension](bi-wizard-add-dimension-intelligence-to-a-dimension.md) or (for an Accounts type dimension) [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
 <span data-ttu-id="565ec-148">ウィザードでは、指定されている属性の型に基づいて、ディメンションの種類が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-148">The wizard automatically sets the dimension type based on the attribute types that are specified.</span></span> <span data-ttu-id="565ec-149">ウィザードで指定された属性の型によって、属性の `Type` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-149">The attribute types specified in the wizard set the `Type` property for the attributes.</span></span> <span data-ttu-id="565ec-150">ディメンションとその属性の `Type` プロパティの設定により、ディメンションのコンテンツに関する情報が、サーバーおよびクライアント アプリケーションに提供されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-150">The `Type` property settings for the dimension and its attributes provide information about the contents of a dimension to server and client applications.</span></span> <span data-ttu-id="565ec-151">場合によっては、このような `Type` プロパティの設定は、クライアント アプリケーションに情報を提供するだけなので、省略できます。</span><span class="sxs-lookup"><span data-stu-id="565ec-151">In some cases, these `Type` property settings only provide guidance for client applications and are optional.</span></span> <span data-ttu-id="565ec-152">また、Accounts ディメンション、Time ディメンション、または Currency ディメンションでは、これらの `Type` プロパティの設定によって、サーバーベースの具体的な動作が決まるため、特定のキューブの動作を実装する際に、この設定が必要になる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="565ec-152">In other cases, as for Accounts, Time, or Currency dimensions, these `Type` property settings determine specific server-based behavior and might be required to implement certain cube behavior.</span></span>  
  
 <span data-ttu-id="565ec-153">ディメンションの種類と属性の型の詳細については、「 [ディメンションの種類](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md)」および「 [属性の種類の構成](attribute-properties-configure-attribute-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565ec-153">For more information about dimension and attribute types, see [Dimension Types](../multidimensional-models-olap-logical-dimension-objects/database-dimension-properties-types.md), [Configure Attribute Types](attribute-properties-configure-attribute-types.md).</span></span>  
  
## <a name="defining-account-intelligence"></a><span data-ttu-id="565ec-154">勘定科目インテリジェンスの定義</span><span class="sxs-lookup"><span data-stu-id="565ec-154">Defining Account Intelligence</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="565ec-155">ディメンション ウィザードでは、ウィザードの **[ディメンション属性の選択]** ページで **[勘定科目の種類]** ディメンション属性を定義した場合のみ、この手順が表示されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-155">The Dimension Wizard displays this step only if you defined an **Account Type** dimension attribute on the **Select Dimension Attributes** page of the wizard.</span></span>  
  
 <span data-ttu-id="565ec-156">**[勘定科目インテリジェンスの定義]** ページを使用して、勘定科目の種類のディメンションを作成します。</span><span class="sxs-lookup"><span data-stu-id="565ec-156">You use the **Define Account Intelligence** page to create an Account type dimension.</span></span> <span data-ttu-id="565ec-157">勘定科目の種類のディメンションを作成する場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でサポートしている標準的な勘定科目の種類を、ディメンションの勘定科目の種類の属性のメンバーにマップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="565ec-157">If you are creating an Account type dimension, you have to map standard account types supported by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to members of the account type attribute in the dimension.</span></span> <span data-ttu-id="565ec-158">サーバーではこれらのマッピングを使用して、勘定科目データの種類ごとに個別の集計関数と別名を指定します。</span><span class="sxs-lookup"><span data-stu-id="565ec-158">The server uses these mappings to provide separate aggregation functions and aliases for each type of account data.</span></span>  
  
 <span data-ttu-id="565ec-159">ウィザードでは、このような勘定科目の種類をマップするために、次の列を含むテーブルが用意されています。</span><span class="sxs-lookup"><span data-stu-id="565ec-159">To map these account types, the wizard provides a table with the following columns:</span></span>  
  
-   <span data-ttu-id="565ec-160">**[基になるテーブルの勘定科目の種類]** 列。データ ソース テーブルの勘定科目の種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-160">The **Source Table Account Types** column lists account types from the data source table.</span></span>  
  
-   <span data-ttu-id="565ec-161">**[ビルトイン勘定科目の種類]** 列。サーバーがサポートしている対応する標準的な勘定科目の種類が表示されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-161">The **Built-In Account Types** column lists the corresponding standard account types supported by the server.</span></span> <span data-ttu-id="565ec-162">ソース データで標準的な名前を使用すると、ウィザードによって、自動的に、ソースの種類がサーバーの種類にマップされ、この情報が **[ビルトイン勘定科目の種類]** 列に表示されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-162">If the source data uses standard names, the wizard automatically maps the source type to the server type, and populates the **Built-In Account Types** column with this information.</span></span> <span data-ttu-id="565ec-163">サーバーで勘定科目の種類をマップしない場合またはマッピングを変更する場合は、 **[ビルトイン勘定科目の種類]** 列の一覧から異なる種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="565ec-163">If the server does not map the account types or you want to change the mapping, select a different type from the list in the **Built-In Account Types** column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="565ec-164">ウィザードで Accounts ディメンションを作成する際に、勘定科目の種類がマップされていない場合は、ディメンションの作成後、ビジネス インテリジェンス ウィザードを使用して、これらのマッピングを構成します。</span><span class="sxs-lookup"><span data-stu-id="565ec-164">If the account types are not mapped when the wizard creates an Accounts dimension, use the Business Intelligence Wizard to configure these mappings after you create the dimension.</span></span> <span data-ttu-id="565ec-165">詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565ec-165">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="completing-the-wizard"></a><span data-ttu-id="565ec-166">ウィザードの完了</span><span class="sxs-lookup"><span data-stu-id="565ec-166">Completing the Wizard</span></span>  
 <span data-ttu-id="565ec-167">ウィザードで、ディメンション テーブルがスキャンされ、リレーションシップが検出されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-167">The wizard scans dimension tables to detect relationships.</span></span> <span data-ttu-id="565ec-168">ウィザードによって、スノーフレーク ディメンションのキー属性間の属性リレーションシップが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-168">The wizard will create attribute relationships between key attributes in snowflake dimensions automatically.</span></span>  
  
 <span data-ttu-id="565ec-169">また、親子リレーションシップがディメンションに存在するかどうかも自動的に検出されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-169">The wizard also automatically detects if a parent-child relationship exists in the dimension.</span></span> <span data-ttu-id="565ec-170">親属性がディメンションのキー属性のメンバーを参照するときには、親子リレーションシップが存在します。</span><span class="sxs-lookup"><span data-stu-id="565ec-170">A parent-child relationship exists when a parent attribute references members of the key attribute of the dimension.</span></span> <span data-ttu-id="565ec-171">このリレーションシップでは、ディメンションのリーフ メンバー間の階層リレーションシップおよび集計パスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="565ec-171">This relationship defines hierarchical relationships and aggregation paths between leaf members of the dimension.</span></span> <span data-ttu-id="565ec-172">親子階層の詳細については、「 [親子階層の属性](parent-child-dimension-attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="565ec-172">For more information about parent-child hierarchies, see [Attributes in Parent-Child Hierarchies](parent-child-dimension-attributes.md).</span></span>  
  
 <span data-ttu-id="565ec-173">**[ウィザードの完了]** ページで、新しいディメンションの名前を入力し、ディメンション構造を確認して、ウィザードを完了します。</span><span class="sxs-lookup"><span data-stu-id="565ec-173">On the **Completing the Wizard** page, you complete the wizard by typing a name for the new dimension and reviewing the dimension structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="565ec-174">参照</span><span class="sxs-lookup"><span data-stu-id="565ec-174">See Also</span></span>  
 <span data-ttu-id="565ec-175">[データソースに時間テーブル以外のテーブルを生成してディメンションを作成する](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) </span><span class="sxs-lookup"><span data-stu-id="565ec-175">[Create a Dimension by Generating a Non-Time Table in the Data Source](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md) </span></span>  
 <span data-ttu-id="565ec-176">[時間テーブルを生成して時間ディメンションを作成する](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="565ec-176">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 <span data-ttu-id="565ec-177">[ディメンションの属性のプロパティのリファレンス](dimension-attribute-properties-reference.md) </span><span class="sxs-lookup"><span data-stu-id="565ec-177">[Dimension Attribute Properties Reference](dimension-attribute-properties-reference.md) </span></span>  
 <span data-ttu-id="565ec-178">[時間テーブルを生成して時間ディメンションを作成する](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="565ec-178">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 [<span data-ttu-id="565ec-179">データ ソースに時間テーブル以外のテーブルを生成することによるディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="565ec-179">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>](create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)  
  
  