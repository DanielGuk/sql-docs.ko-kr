---
title: 스크립트 태스크에서 변수 사용 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Foreach Loop containers
- Script task [Integration Services], variables
- scripts [Integration Services], variables
- Variables property
- Variable object
- SSIS Script task, variables
- variables [Integration Services], Script task
ms.assetid: 593b5961-4bfa-4ce1-9531-a251c34e89d3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2b187a87643353f94a44173472b72478553b7110
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48085303"
---
# <a name="using-variables-in-the-script-task"></a>스크립트 태스크에서 변수 사용
  스크립트 태스크에서는 변수를 통해 패키지의 다른 개체와 데이터를 교환할 수 있습니다. 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](../../integration-services-ssis-variables.md)를 참조하세요.  
  
 스크립트 태스크에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용하여 패키지의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 개체를 읽고 씁니다.  
  
> [!NOTE]  
>  <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 클래스의 <xref:Microsoft.SqlServer.Dts.Runtime.Variable> 속성은 `Object` 형식을 사용합니다. 스크립트 태스크에는 `Option Strict`가 설정되어 있으므로 스크립트 태스크를 사용하려면 먼저 <xref:Microsoft.SqlServer.Dts.Runtime.Variable.Value%2A> 속성을 적절한 형식으로 캐스팅해야 합니다.  
  
 **스크립트 태스크 편집기**의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadOnlyVariables%2A> 및 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptTask.ReadWriteVariables%2A> 목록에 기존 변수를 추가하여 사용자 지정 스크립트에서 해당 변수를 사용할 수 있게 할 수 있습니다. 변수 이름은 대/소문자를 구분합니다. 스크립트 내에서는 `Dts` 개체의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 통해 두 유형의 변수에 액세스합니다. 개별 변수를 읽고 쓰는 데는 `Value` 속성을 사용합니다. 스크립트 태스크에서는 스크립트가 변수 값을 읽고 수정할 때 잠금을 투명하게 관리합니다.  
  
 <xref:Microsoft.SqlServer.Dts.Runtime.Variables.Contains%2A> 속성에서 반환된 <xref:Microsoft.SqlServer.Dts.Runtime.Variables> 컬렉션의 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 메서드를 사용하여 코드에서 변수를 사용하기 전에 해당 변수가 있는지 여부를 확인할 수 있습니다.  
  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 속성(Dts.VariableDispenser)을 사용하여 스크립트 태스크에서 변수를 사용할 수도 있습니다. <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A>를 사용하는 경우 개발자가 자신의 고유 코드에서 잠금 의미 체계와 변수 값에 대한 데이터 형식 캐스팅을 모두 처리해야 합니다. 디자인 타임에는 사용할 수 없지만 런타임에 프로그래밍 방식으로 만들어지는 변수를 사용하려면 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.VariableDispenser%2A> 속성 대신 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> 속성을 사용해야 합니다.  
  
## <a name="using-the-script-task-within-a-foreach-loop-container"></a>Foreach 루프 컨테이너 내에서 스크립트 태스크 사용  
 스크립트 태스크가 Foreach 루프 컨테이너 내에서 반복적으로 실행되는 경우 스크립트는 일반적으로 열거자에서 현재 항목의 내용을 사용해야 합니다. 예를 들어 Foreach File 열거자를 사용하는 경우에는 스크립트에서 현재 파일 이름을 알고 있어야 하며, Foreach ADO 열거자를 사용하는 경우에는 스크립트에서 현재 데이터 행의 열 내용을 알고 있어야 합니다.  
  
 변수는 Foreach 루프 컨테이너와 스크립트 태스크 간의 이 통신을 가능하게 해 줍니다. **Foreach 루프 편집기**의 **변수 매핑** 페이지에서는 열거된 단일 항목에서 반환된 각 데이터 항목에 변수를 할당합니다. 예를 들어 Foreach File 열거자는 인덱스 0 위치의 파일 이름만 반환하므로 변수 매핑이 하나만 필요한 반면, 각 행의 여러 데이터 열을 반환하는 열거자의 경우에는 스크립트 태스크에서 사용할 각 열에 서로 다른 변수를 매핑해야 합니다.  
  
 열거 된 항목을 변수에 매핑한 후 매핑된 변수를를 추가 해야 합니다는 `ReadOnlyVariables` 속성에는 **스크립트** 페이지를 **스크립트 태스크 편집기** 를 사용할 수 있게 하려면 프로그램 스크립트입니다. 폴더의 이미지 파일을 처리하는 Foreach 루프 컨테이너 내에서의 스크립트 태스크에 대한 예제는 [스크립트 태스크를 사용한 이미지 작업](../../extending-packages-scripting-task-examples/working-with-images-with-the-script-task.md)을 참조하세요.  
  
## <a name="variables-example"></a>변수 예  
 다음 예에서는 스크립트 태스크에서 변수에 액세스하고 이를 사용하여 패키지 워크플로의 경로를 확인하는 방법을 보여 줍니다. 샘플 라는 정수 변수 만들었다고 가정 `CustomerCount` 및 `MaxRecordCount` 추가 하는 `ReadOnlyVariables` 컬렉션에는 **스크립트 태스크 편집기**. `CustomerCount` 변수에는 가져올 고객 레코드 수가 들어 있습니다. 이 값이 `MaxRecordCount` 값보다 크면 스크립트 태스크에서 실패가 보고됩니다. `MaxRecordCount` 임계값 초과로 인해 실패할 경우 워크플로의 오류 경로에서 필요한 정리 작업을 구현할 수 있습니다.  
  
 이 예제를 컴파일하려면 Microsoft.SqlServer.ScriptTask 어셈블리에 대한 참조를 추가해야 합니다.  
  
```vb  
Public Sub Main()  
  
    Dim customerCount As Integer  
    Dim maxRecordCount As Integer  
  
    If Dts.Variables.Contains("CustomerCount") = True AndAlso _  
        Dts.Variables.Contains("MaxRecordCount") = True Then  
  
        customerCount = _  
            CType(Dts.Variables("CustomerCount").Value, Integer)  
        maxRecordCount = _  
            CType(Dts.Variables("MaxRecordCount").Value, Integer)  
  
    End If  
  
    If customerCount > maxRecordCount Then  
            Dts.TaskResult = ScriptResults.Failure  
    Else  
            Dts.TaskResult = ScriptResults.Success  
    End If  
  
End Sub  
```  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Dts.Runtime;  
  
public class ScriptMain  
{  
  
    public void Main()  
    {  
        int customerCount;  
        int maxRecordCount;  
  
        if (Dts.Variables.Contains("CustomerCount")==true&&Dts.Variables.Contains("MaxRecordCount")==true)  
  
        {  
            customerCount = (int) Dts.Variables["CustomerCount"].Value;  
            maxRecordCount = (int) Dts.Variables["MaxRecordCount"].Value;  
  
        }  
  
        if (customerCount>maxRecordCount)  
        {  
            Dts.TaskResult = (int)ScriptResults.Failure;  
        }  
        else  
        {  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
  
    }  
  
}  
  
```  
  
![Integration Services 아이콘 (작은)](../../media/dts-16.gif "Integration Services 아이콘 (작은)")**Integration Services를 사용 하 여 날짜를 알림 설정** <br /> Microsoft의 최신 다운로드, 문서, 예제 및 비디오와 커뮤니티에서 선택된 솔루션을 보려면 MSDN의 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 페이지를 방문하세요.<br /><br /> [MSDN의 Integration Services 페이지 방문](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> 이러한 업데이트에 대한 자동 알림을 받으려면 해당 페이지에서 제공하는 RSS 피드를 구독하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services &#40;SSIS&#41; 변수](../../integration-services-ssis-variables.md)   
 [패키지에서 변수 사용](../../use-variables-in-packages.md)  
  
  
