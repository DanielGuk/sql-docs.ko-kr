---
title: 계산 측정값 표현 (테이블 형식) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 4cb9fea5-1616-467b-a539-d051e5833aea
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58382e66ca6e59ea89e942f97a20ba5d6a138559
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48160783"
---
# <a name="calculated-measure-representation-tabular"></a>계산 측정값 표현(테이블 형식)
  계산 측정값은 사용할 때마다 평가되는 명명된 DAX 식입니다.  
  
## <a name="calculated-measure-representation"></a>계산 측정값 표현  
  
### <a name="calculated-measure-in-amo"></a>AMO의 계산 측정값  
 AMO를 사용하여 테이블 형식 모델 계산 측정값을 관리하는 경우 논리적 계산 측정값 개체와 <xref:Microsoft.AnalysisServices.Command> 개체의 <xref:Microsoft.AnalysisServices.MdxScript>에 정의된 측정값 사이에 일 대 일 일치 관계가 있습니다. 각 **계산 측정값** 로 정의 됩니다는 `CREATE MEASURE` 내부의 식을 <xref:Microsoft.AnalysisServices.Command> 개체 및 세미콜론으로 구분 합니다. 테이블 형식 모델의 모든 계산 측정값은 <xref:Microsoft.AnalysisServices.MdxScript> 개체에 있는 하나의 명령 개체에서 컬렉션 `CREATE MEASURE` 문자열과 대응합니다. 또한 각 계산 측정값에는 <xref:Microsoft.AnalysisServices.CalculationProperty>에 대한 일 대 일 매핑이 있습니다.  
  
 다음 코드 조각에서는 계산 측정값을 만드는 방법을 보여 줍니다.  
  
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
  
  
