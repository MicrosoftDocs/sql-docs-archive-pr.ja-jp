---
title: 行セットとパラメーターでのデータ型マッピング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- mapping data types [OLE DB]
- DBTYPE_SQLVARIANT data type
- SQL Server Native Client OLE DB provider, data types
- rowsets [OLE DB], data type mapping
- data types [OLE DB]
- GetColumnInfo function
- parameters [OLE DB]
- SSPROP_ALLOWNATIVEVARIANT property
- GetParameterInfo function
- OLE DB, data types
ms.assetid: 3d831ff8-3b79-4698-b2c1-2b5dd2f8235c
author: rothja
ms.author: jroth
ms.openlocfilehash: 83923eb611ddc7baedc38c70b23c2ff5e17556d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643817"
---
# <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="ab701-102">行セットとパラメーターでのデータ型マッピング</span><span class="sxs-lookup"><span data-stu-id="ab701-102">Data Type Mapping in Rowsets and Parameters</span></span>
  <span data-ttu-id="ab701-103">行セットとパラメーター値として、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 関数**IColumnsInfo:: GetColumnInfo**および**ICommandWithParameters:: getparameterinfo**で報告される OLE DB 次の定義データ型を使用してデータを表します。</span><span class="sxs-lookup"><span data-stu-id="ab701-103">In rowsets and as parameter values, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider represents [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data by using the following OLE DB defined data types, reported in the functions **IColumnsInfo::GetColumnInfo** and **ICommandWithParameters::GetParameterInfo**.</span></span>  
  
|<span data-ttu-id="ab701-104">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="ab701-104">SQL Server data type</span></span>|<span data-ttu-id="ab701-105">OLE DB データ型</span><span class="sxs-lookup"><span data-stu-id="ab701-105">OLE DB data type</span></span>|  
|--------------------------|----------------------|  
|<span data-ttu-id="ab701-106">**bigint**</span><span class="sxs-lookup"><span data-stu-id="ab701-106">**bigint**</span></span>|<span data-ttu-id="ab701-107">DBTYPE_I8</span><span class="sxs-lookup"><span data-stu-id="ab701-107">DBTYPE_I8</span></span>|  
|<span data-ttu-id="ab701-108">**[バイナリ]**</span><span class="sxs-lookup"><span data-stu-id="ab701-108">**binary**</span></span>|<span data-ttu-id="ab701-109">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="ab701-109">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="ab701-110">**bit**</span><span class="sxs-lookup"><span data-stu-id="ab701-110">**bit**</span></span>|<span data-ttu-id="ab701-111">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="ab701-111">DBTYPE_BOOL</span></span>|  
|<span data-ttu-id="ab701-112">**char**</span><span class="sxs-lookup"><span data-stu-id="ab701-112">**char**</span></span>|<span data-ttu-id="ab701-113">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="ab701-113">DBTYPE_STR</span></span>|  
|<span data-ttu-id="ab701-114">**datetime**</span><span class="sxs-lookup"><span data-stu-id="ab701-114">**datetime**</span></span>|<span data-ttu-id="ab701-115">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="ab701-115">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="ab701-116">**datetime2**</span><span class="sxs-lookup"><span data-stu-id="ab701-116">**datetime2**</span></span>|<span data-ttu-id="ab701-117">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="ab701-117">DBTYPE_DBTIME2</span></span>|  
|<span data-ttu-id="ab701-118">**decimal**</span><span class="sxs-lookup"><span data-stu-id="ab701-118">**decimal**</span></span>|<span data-ttu-id="ab701-119">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="ab701-119">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="ab701-120">**float**</span><span class="sxs-lookup"><span data-stu-id="ab701-120">**float**</span></span>|<span data-ttu-id="ab701-121">DBTYPE_R8</span><span class="sxs-lookup"><span data-stu-id="ab701-121">DBTYPE_R8</span></span>|  
|<span data-ttu-id="ab701-122">**image**</span><span class="sxs-lookup"><span data-stu-id="ab701-122">**image**</span></span>|<span data-ttu-id="ab701-123">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="ab701-123">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="ab701-124">**int**</span><span class="sxs-lookup"><span data-stu-id="ab701-124">**int**</span></span>|<span data-ttu-id="ab701-125">DBTYPE_I4</span><span class="sxs-lookup"><span data-stu-id="ab701-125">DBTYPE_I4</span></span>|  
|<span data-ttu-id="ab701-126">**money**</span><span class="sxs-lookup"><span data-stu-id="ab701-126">**money**</span></span>|<span data-ttu-id="ab701-127">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="ab701-127">DBTYPE_CY</span></span>|  
|<span data-ttu-id="ab701-128">**nchar**</span><span class="sxs-lookup"><span data-stu-id="ab701-128">**nchar**</span></span>|<span data-ttu-id="ab701-129">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="ab701-129">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="ab701-130">**ntext**</span><span class="sxs-lookup"><span data-stu-id="ab701-130">**ntext**</span></span>|<span data-ttu-id="ab701-131">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="ab701-131">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="ab701-132">**numeric**</span><span class="sxs-lookup"><span data-stu-id="ab701-132">**numeric**</span></span>|<span data-ttu-id="ab701-133">DBTYPE_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="ab701-133">DBTYPE_NUMERIC</span></span>|  
|<span data-ttu-id="ab701-134">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="ab701-134">**nvarchar**</span></span>|<span data-ttu-id="ab701-135">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="ab701-135">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="ab701-136">**real**</span><span class="sxs-lookup"><span data-stu-id="ab701-136">**real**</span></span>|<span data-ttu-id="ab701-137">DBTYPE_R4</span><span class="sxs-lookup"><span data-stu-id="ab701-137">DBTYPE_R4</span></span>|  
|<span data-ttu-id="ab701-138">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="ab701-138">**smalldatetime**</span></span>|<span data-ttu-id="ab701-139">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="ab701-139">DBTYPE_DBTIMESTAMP</span></span>|  
|<span data-ttu-id="ab701-140">**smallint**</span><span class="sxs-lookup"><span data-stu-id="ab701-140">**smallint**</span></span>|<span data-ttu-id="ab701-141">DBTYPE_I2</span><span class="sxs-lookup"><span data-stu-id="ab701-141">DBTYPE_I2</span></span>|  
|<span data-ttu-id="ab701-142">**smallmoney**</span><span class="sxs-lookup"><span data-stu-id="ab701-142">**smallmoney**</span></span>|<span data-ttu-id="ab701-143">DBTYPE_CY</span><span class="sxs-lookup"><span data-stu-id="ab701-143">DBTYPE_CY</span></span>|  
|<span data-ttu-id="ab701-144">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="ab701-144">**sql_variant**</span></span>|<span data-ttu-id="ab701-145">DBTYPE_VARIANT、DBTYPE_SQLVARIANT</span><span class="sxs-lookup"><span data-stu-id="ab701-145">DBTYPE_VARIANT, DBTYPE_SQLVARIANT</span></span>|  
|<span data-ttu-id="ab701-146">**sysname**</span><span class="sxs-lookup"><span data-stu-id="ab701-146">**sysname**</span></span>|<span data-ttu-id="ab701-147">DBTYPE_WSTR</span><span class="sxs-lookup"><span data-stu-id="ab701-147">DBTYPE_WSTR</span></span>|  
|<span data-ttu-id="ab701-148">**text**</span><span class="sxs-lookup"><span data-stu-id="ab701-148">**text**</span></span>|<span data-ttu-id="ab701-149">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="ab701-149">DBTYPE_STR</span></span>|  
|<span data-ttu-id="ab701-150">**timestamp**</span><span class="sxs-lookup"><span data-stu-id="ab701-150">**timestamp**</span></span>|<span data-ttu-id="ab701-151">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="ab701-151">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="ab701-152">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="ab701-152">**tinyint**</span></span>|<span data-ttu-id="ab701-153">DBTYPE_UI1</span><span class="sxs-lookup"><span data-stu-id="ab701-153">DBTYPE_UI1</span></span>|  
|<span data-ttu-id="ab701-154">**UDT**</span><span class="sxs-lookup"><span data-stu-id="ab701-154">**UDT**</span></span>|<span data-ttu-id="ab701-155">DBTYPE_UDT</span><span class="sxs-lookup"><span data-stu-id="ab701-155">DBTYPE_UDT</span></span>|  
|<span data-ttu-id="ab701-156">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="ab701-156">**uniqueidentifier**</span></span>|<span data-ttu-id="ab701-157">DBTYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="ab701-157">DBTYPE_GUID</span></span>|  
|<span data-ttu-id="ab701-158">**varbinary**</span><span class="sxs-lookup"><span data-stu-id="ab701-158">**varbinary**</span></span>|<span data-ttu-id="ab701-159">DBTYPE_BYTES</span><span class="sxs-lookup"><span data-stu-id="ab701-159">DBTYPE_BYTES</span></span>|  
|<span data-ttu-id="ab701-160">**varchar**</span><span class="sxs-lookup"><span data-stu-id="ab701-160">**varchar**</span></span>|<span data-ttu-id="ab701-161">DBTYPE_STR</span><span class="sxs-lookup"><span data-stu-id="ab701-161">DBTYPE_STR</span></span>|  
|<span data-ttu-id="ab701-162">**XML**</span><span class="sxs-lookup"><span data-stu-id="ab701-162">**XML**</span></span>|<span data-ttu-id="ab701-163">DBTYPE_XML</span><span class="sxs-lookup"><span data-stu-id="ab701-163">DBTYPE_XML</span></span>|  
  
 <span data-ttu-id="ab701-164">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、図に示すように、コンシューマーによって要求されたデータ変換をサポートします。</span><span class="sxs-lookup"><span data-stu-id="ab701-164">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer-requested data conversions as shown in the illustration.</span></span>  
  
 <span data-ttu-id="ab701-165">**sql_variant** オブジェクトは、text、ntext、image、varchar(max)、nvarchar(max)、varbinary(max)、xml、timestamp、および Microsoft .NET Framework 共通言語ランタイム (CLR) のユーザー定義型を除く、任意の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型のデータを保持できます。</span><span class="sxs-lookup"><span data-stu-id="ab701-165">The **sql_variant** objects can hold data of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type except text, ntext, image, varchar(max), nvarchar(max), varbinary(max), xml, timestamp, and Microsoft .NET Framework common language runtime (CLR) user-defined types.</span></span> <span data-ttu-id="ab701-166">また、sql_variant データのインスタンスは、その基になる基本データ型として sql_variant を保持できません。</span><span class="sxs-lookup"><span data-stu-id="ab701-166">An instance of sql_variant data also cannot have sql_variant as its underlying base data type.</span></span> <span data-ttu-id="ab701-167">たとえば、一部の行の列に **smallint** 型の値を格納し、他の行の列に **float** 型の値を格納して、残りの行の列に **char**/**nchar** 型の値を格納できます。</span><span class="sxs-lookup"><span data-stu-id="ab701-167">For example, the column can contain **smallint** values for some rows, **float** values for other rows, and **char**/**nchar** values in the remainder.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ab701-168">**Sql_variant**のデータ型は、Microsoft Visual Basic での variant データ型に似ていますか。</span><span class="sxs-lookup"><span data-stu-id="ab701-168">The **sql_variant** data type is similar to the Variant data type in Microsoft Visual Basic??</span></span> <span data-ttu-id="ab701-169">および DBTYPE_VARIANT、OLEDB で DBTYPE_SQLVARIANT ます。</span><span class="sxs-lookup"><span data-stu-id="ab701-169">and the DBTYPE_VARIANT, DBTYPE_SQLVARIANT in OLEDB.</span></span>  
  
 <span data-ttu-id="ab701-170">**sql_variant** 型のデータを DBTYPE_VARIANT としてフェッチすると、このデータはバッファーの VARIANT 構造体内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-170">When **sql_variant** data is fetched as DBTYPE_VARIANT, it is put in a VARIANT structure in the buffer.</span></span> <span data-ttu-id="ab701-171">ただし、VARIANT 構造体内のサブタイプは、**sql_variant** データ型で定義されているサブタイプにマップされない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ab701-171">But the subtypes in the VARIANT structure may not map to subtypes defined in the **sql_variant** data type.</span></span> <span data-ttu-id="ab701-172">このため、すべてのサブタイプを一致させるには、**sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab701-172">The **sql_variant** data must then be fetched as DBTYPE_SQLVARIANT in order for all the subtypes to match.</span></span>  
  
## <a name="dbtype_sqlvariant-data-type"></a><span data-ttu-id="ab701-173">DBTYPE_SQLVARIANT データ型</span><span class="sxs-lookup"><span data-stu-id="ab701-173">DBTYPE_SQLVARIANT Data Type</span></span>  
 <span data-ttu-id="ab701-174">**Sql_variant**データ型をサポートするために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは DBTYPE_SQLVARIANT と呼ばれるプロバイダー固有のデータ型を公開します。</span><span class="sxs-lookup"><span data-stu-id="ab701-174">To support the **sql_variant** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes a provider-specific data type called DBTYPE_SQLVARIANT.</span></span> <span data-ttu-id="ab701-175">**sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチすると、データはプロバイダー固有の SSVARIANT 構造体内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-175">When **sql_variant** data is fetched in as DBTYPE_SQLVARIANT, it is stored in a provider-specific SSVARIANT structure.</span></span> <span data-ttu-id="ab701-176">SSVARIANT 構造体には、**sql_variant** データ型のサブタイプに一致するすべてのサブタイプが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ab701-176">The SSVARIANT structure contains all of the subtypes that match the subtypes of the **sql_variant** data type.</span></span>  
  
 <span data-ttu-id="ab701-177">また、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT を TRUE に設定する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ab701-177">The session property SSPROP_ALLOWNATIVEVARIANT must also be set to TRUE.</span></span>  
  
## <a name="provider-specific-property-ssprop_allownativevariant"></a><span data-ttu-id="ab701-178">プロバイダー固有のプロパティ SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="ab701-178">Provider-Specific Property SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="ab701-179">データをフェッチするときに、列またはパラメーターに返すデータ型を明示的に指定できます。</span><span class="sxs-lookup"><span data-stu-id="ab701-179">In fetching data, you can specify explicitly what kind of data type should be returned for a column or for a parameter.</span></span> <span data-ttu-id="ab701-180">また、**IColumnsInfo** を使用して列情報を取得し、その情報をバインドに使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="ab701-180">**IColumnsInfo** can also be used to get the column information and use that to do the binding.</span></span> <span data-ttu-id="ab701-181">**IColumnsInfo** を使用してバインド用の列情報を取得するときに、SSPROP_ALLOWNATIVEVARIANT セッション プロパティが FALSE (既定値) の場合、**sql_variant** 型の列には DBTYPE_VARIANT が返されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-181">When **IColumnsInfo** is used to obtain column information for binding purposes, if the SSPROP_ALLOWNATIVEVARIANT session property is FALSE (default value), DBTYPE_VARIANT is returned for **sql_variant** columns.</span></span> <span data-ttu-id="ab701-182">SSPROP_ALLOWNATIVEVARIANT プロパティが FALSE の場合、DBTYPE_SQLVARIANT はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="ab701-182">If SSPROP_ALLOWNATIVEVARIANT property is FALSE DBTYPE_SQLVARIANT is not supported.</span></span> <span data-ttu-id="ab701-183">SSPROP_ALLOWNATIVEVARIANT プロパティを TRUE に設定すると、列の型は DBTYPE_SQLVARIANT として返されます。この場合、バッファーには SSVARIANT 構造体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-183">If SSPROP_ALLOWNATIVEVARIANT property is set to TRUE, the column type is returned as DBTYPE_SQLVARIANT, in which case the buffer will hold the SSVARIANT structure.</span></span> <span data-ttu-id="ab701-184">**sql_variant** 型のデータを DBTYPE_SQLVARIANT としてフェッチするときは、セッション プロパティ SSPROP_ALLOWNATIVEVARIANT が TRUE に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ab701-184">In fetching **sql_variant** data as DBTYPE_SQLVARIANT, the session property SSPROP_ALLOWNATIVEVARIANT must be set to TRUE.</span></span>  
  
 <span data-ttu-id="ab701-185">SSPROP_ALLOWNATIVEVARIANT プロパティはプロバイダー固有の DBPROPSET_SQLSERVERSESSION プロパティ セットの一部であり、セッション プロパティです。</span><span class="sxs-lookup"><span data-stu-id="ab701-185">SSPROP_ALLOWNATIVEVARIANT property is part of the provider-specific DBPROPSET_SQLSERVERSESSION property set, and is a session property.</span></span>  
  
 <span data-ttu-id="ab701-186">DBTYPE_VARIANT は、他のすべての OLE DB プロバイダーに適用されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-186">DBTYPE_VARIANT applies to all other OLE DB providers.</span></span>  
  
## <a name="ssprop_allownativevariant"></a><span data-ttu-id="ab701-187">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="ab701-187">SSPROP_ALLOWNATIVEVARIANT</span></span>  
 <span data-ttu-id="ab701-188">SSPROP_ALLOWNATIVEVARIANT はセッション プロパティで、DBPROPSET_SQLSERVERSESSION プロパティ セットの一部です。</span><span class="sxs-lookup"><span data-stu-id="ab701-188">SSPROP_ALLOWNATIVEVARIANT is a session property and is part of DBPROPSET_SQLSERVERSESSION  property set.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ab701-189">SSPROP_ALLOWNATIVEVARIANT</span><span class="sxs-lookup"><span data-stu-id="ab701-189">SSPROP_ALLOWNATIVEVARIANT</span></span>|<span data-ttu-id="ab701-190">型 : VT_BOOL</span><span class="sxs-lookup"><span data-stu-id="ab701-190">Type: VT_BOOL</span></span><br /><br /> <span data-ttu-id="ab701-191">R/W: 読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="ab701-191">R/W: Read/Write</span></span><br /><br /> <span data-ttu-id="ab701-192">既定値 : VARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="ab701-192">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="ab701-193">説明 : データを DBTYPE_VARIANT と DBTYPE_SQLVARIANT のどちらとしてフェッチするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="ab701-193">Description: Determines if the data fetched in is as DBTYPE_VARIANT or DBTYPE_SQLVARIANT.</span></span><br /><br /> <span data-ttu-id="ab701-194">VARIANT_TRUE: 列の型は DBTYPE_SQLVARIANT として返され、バッファーには SSVARIANT 構造体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-194">VARIANT_TRUE: Column type is returned as DBTYPE_SQLVARIANT in which case the buffer will hold SSVARIANT structure.</span></span><br /><br /> <span data-ttu-id="ab701-195">VARIANT_FALSE: 列の型は DBTYPE_VARIANT として返され、バッファーには VARIANT 構造体が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ab701-195">VARIANT_FALSE: Column type is returned as DBTYPE_VARIANT and the buffer will have VARIANT structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab701-196">参照</span><span class="sxs-lookup"><span data-stu-id="ab701-196">See Also</span></span>  
 [<span data-ttu-id="ab701-197">データ型 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="ab701-197">Data Types &#40;OLE DB&#41;</span></span>](data-types-ole-db.md)  
  
  