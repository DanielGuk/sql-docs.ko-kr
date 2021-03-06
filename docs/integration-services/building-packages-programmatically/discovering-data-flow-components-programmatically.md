---
title: 프로그래밍 방식으로 데이터 흐름 구성 요소 검색 | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PipelineComponentInfos collection
- data flow task [Integration Services], components
- discovering data flow components
- components [Integration Services], data flow
- data flow [Integration Services], components
ms.assetid: ff92a96a-8af6-4532-82cc-c0bbff92401b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a1d4b145407464853728e2ac62d0ae9dcbcde05f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850478"
---
# <a name="discovering-data-flow-components-programmatically"></a>프로그래밍 방식으로 데이터 흐름 구성 요소 검색
  패키지에 데이터 흐름 태스크를 추가한 후 사용할 수 있는 데이터 흐름 구성 요소를 확인할 수 있습니다. 로컬 컴퓨터에 설치되어 있고 사용 가능한 데이터 흐름 원본, 변환 및 대상을 프로그래밍 방식으로 검색할 수 있습니다. 패키지에 데이터 흐름 태스크 추가에 대한 자세한 내용은 [프로그래밍 방식으로 데이터 흐름 태스크 추가](../../integration-services/building-packages-programmatically/adding-the-data-flow-task-programmatically.md)를 참조하세요.  
  
## <a name="discovering-components"></a>구성 요소 검색  
 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 클래스에서는 로컬 컴퓨터에 올바르게 설치된 각 구성 요소에 대한 <xref:Microsoft.SqlServer.Dts.Runtime.Application.PipelineComponentInfos%2A> 개체가 들어 있는 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo> 컬렉션을 제공합니다. 각 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo>에는 구성 요소 이름, 설명 및 생성 이름과 같이 구성 요소에 대한 정보가 들어 있습니다. 패키지에 구성 요소를 추가할 때 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfo.CreationName%2A> 속성에서 반환된 값을 사용하여 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ComponentClassID%2A>의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100> 속성을 설정할 수 있습니다.  
  
## <a name="next-step"></a>다음 단계  
 사용 가능한 구성 요소를 검색한 후에는 다음의 [프로그래밍 방식으로 데이터 흐름 구성 요소 추가](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md) 항목에 설명된 대로 구성 요소를 추가하고 구성합니다.  
  
## <a name="sample"></a>예제  
 다음 코드 예제에서는 <xref:Microsoft.SqlServer.Dts.Runtime.PipelineComponentInfos> 개체의 <xref:Microsoft.SqlServer.Dts.Runtime.Application> 컬렉션을 열거하여 로컬 컴퓨터에서 사용할 수 있는 데이터 흐름 구성 요소를 프로그래밍 방식으로 검색하는 방법을 보여 줍니다. 이 샘플에는 Microsoft.SqlServer.ManagedDTS 어셈블리에 대한 참조가 필요합니다.  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace Microsoft.SqlServer.Dts.Samples  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      Application application = new Application();  
      PipelineComponentInfos componentInfos = application.PipelineComponentInfos;  
  
      foreach (PipelineComponentInfo componentInfo in componentInfos)  
      {  
        Console.WriteLine("Name: " + componentInfo.Name + "\n" +  
          " CreationName: " + componentInfo.CreationName + "\n");  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim application As Application = New Application()  
  
    Dim componentInfos As PipelineComponentInfos = application.PipelineComponentInfos  
  
    For Each componentInfo As PipelineComponentInfo In componentInfos  
      Console.WriteLine("Name: " & componentInfo.Name & vbCrLf & _  
        " CreationName: " & componentInfo.CreationName & vbCrLf)  
    Next  
  
    Console.Read()  
  
  End Sub  
  
End Module  
```
  
## <a name="see-also"></a>참고 항목  
 [프로그래밍 방식으로 데이터 흐름 구성 요소 추가](../../integration-services/building-packages-programmatically/adding-data-flow-components-programmatically.md)  
  
  
