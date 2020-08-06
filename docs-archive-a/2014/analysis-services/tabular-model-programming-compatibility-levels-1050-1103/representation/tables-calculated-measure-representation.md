---
title: 計算されるメジャー表現 (表形式) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
ms.assetid: 4cb9fea5-1616-467b-a539-d051e5833aea
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6b630fa075ae07b84e4886ad8bc115611da8e2d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643494"
---
# <a name="calculated-measure-representation-tabular"></a><span data-ttu-id="386e6-102">計算されるメジャー表現 (テーブル)</span><span class="sxs-lookup"><span data-stu-id="386e6-102">Calculated Measure Representation (Tabular)</span></span>
  <span data-ttu-id="386e6-103">計算されるメジャーとは、使用されるたびに評価される名前付き DAX 式です。</span><span class="sxs-lookup"><span data-stu-id="386e6-103">A calculated measure is a named DAX expression evaluated every time it is used.</span></span>  
  
## <a name="calculated-measure-representation"></a><span data-ttu-id="386e6-104">計算されるメジャー表現</span><span class="sxs-lookup"><span data-stu-id="386e6-104">Calculated Measure Representation</span></span>  
  
### <a name="calculated-measure-in-amo"></a><span data-ttu-id="386e6-105">AMO 内の計算されるメジャー</span><span class="sxs-lookup"><span data-stu-id="386e6-105">Calculated Measure in AMO</span></span>  
 <span data-ttu-id="386e6-106">AMO を使用してテーブル モデルの計算されるメジャーを管理する場合、<xref:Microsoft.AnalysisServices.Command> オブジェクトの <xref:Microsoft.AnalysisServices.MdxScript> オブジェクトに定義されているメジャーと、論理的な計算されるメジャー オブジェクトが一対一で対応します。</span><span class="sxs-lookup"><span data-stu-id="386e6-106">When using AMO to manage a tabular model calculated measure, there is a one-to-one match between the logical Calculated Measure object and a measure defined in a <xref:Microsoft.AnalysisServices.Command> object of the <xref:Microsoft.AnalysisServices.MdxScript> object.</span></span> <span data-ttu-id="386e6-107">各**計算されるメジャー**は、オブジェクト内の式として定義され、 `CREATE MEASURE` <xref:Microsoft.AnalysisServices.Command> セミコロンで区切られます。</span><span class="sxs-lookup"><span data-stu-id="386e6-107">Each **Calculated Measure** is defined as a `CREATE MEASURE` expression inside a <xref:Microsoft.AnalysisServices.Command> object and separated by a semicolon.</span></span> <span data-ttu-id="386e6-108">テーブル モデルにおける計算されるメジャーは、すべて <xref:Microsoft.AnalysisServices.MdxScript> オブジェクト内の 1 つのコマンド オブジェクトのコレクション `CREATE MEASURE` 文字列に対応しています。</span><span class="sxs-lookup"><span data-stu-id="386e6-108">All calculated measures in a tabular model correspond to the collection `CREATE MEASURE` string in one command object in a <xref:Microsoft.AnalysisServices.MdxScript> object.</span></span> <span data-ttu-id="386e6-109">また、計算される各メジャーは、<xref:Microsoft.AnalysisServices.CalculationProperty> と一対一でマップされます。</span><span class="sxs-lookup"><span data-stu-id="386e6-109">For each calculated measure, there is one-to-one mapping with a <xref:Microsoft.AnalysisServices.CalculationProperty>.</span></span>  
  
 <span data-ttu-id="386e6-110">次のコード スニペットは、計算されるメジャーの作成方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="386e6-110">The following code snippet shows how to create a calculated measure.</span></span>  
  
```  
  
private void addCalculatedMeasure(  
                   AMO.Cube modelCube  
                 , string cmTableName  
                 , string cmName  
                 , string newCalculatedMeasureExpression  
             )  
{  
    //Verify input requirements  
    if (string.IsNullOrEmpty(cmName) || string.IsNullOrWhiteSpace(cmName))  
    {  
        MessageBox.Show(String.Format("Calculated Measure name is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
    if (string.IsNullOrEmpty(newCalculatedMeasureExpression) || string.IsNullOrWhiteSpace(newCalculatedMeasureExpression))  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression is not defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
        return;  
    }  
  
    StringBuilder measuresCommand = new StringBuilder();  
  
    AMO.MdxScript mdxScript = modelCube.MdxScripts["MdxScript"];  
  
    //ToDo: Verify if measure already exits and ask user what wants to do next  
  
    if (mdxScript.Commands.Count == 1)  
    {  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine("-- Tabular Model measures command (do not modify manually) --");  
        measuresCommand.AppendLine("-------------------------------------------------------------");  
        measuresCommand.AppendLine();  
        measuresCommand.AppendLine();  
        mdxScript.Commands.Add(new AMO.Command(measuresCommand.ToString()));  
  
    }  
    else  
    {  
        measuresCommand.Append(mdxScript.Commands[1].Text);  
    }  
    measuresCommand.AppendLine(string.Format("CREATE MEASURE '{0}'[{1}]={2};", cmTableName, cmName, newCalculatedMeasureExpression));  
  
    mdxScript.Commands[1].Text = measuresCommand.ToString();  
  
    if (!mdxScript.CalculationProperties.Contains(cmName))  
    {  
        AMO.CalculationProperty cp = new AMO.CalculationProperty(cmName, AMO.CalculationType.Member);  
        cp.FormatString = ""; // ToDo: Get formatting attributes for the member  
        cp.Visible = true;  
        mdxScript.CalculationProperties.Add(cp);  
    }  
  
    try  
    {  
        modelCube.Update(AMO.UpdateOptions.ExpandFull, AMO.UpdateMode.UpdateOrCreate);  
        MessageBox.Show(String.Format("Calculated Measure successfully defined."), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Information);  
    }  
    catch (AMO.OperationException amoOpXp)  
    {  
        MessageBox.Show(String.Format("Calculated Measure expression contains syntax errors, or references undefined or missspelled elements.\nError message: {0}", amoOpXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (AMO.AmoException amoXp)  
    {  
        MessageBox.Show(String.Format("AMO exception accessing the server.\nError message: {0}", amoXp.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Warning);  
        return;  
    }  
    catch (Exception)  
    {  
        throw;  
    }  
}  
  
```  
  
  