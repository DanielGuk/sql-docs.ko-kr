---
title: "외부 메타 데이터 구현 | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- disconnected validation [Integration Services]
- connected validation [Integration Services]
- custom data flow components [Integration Services], validating
- validation [Integration Services], components
- metadata [Integration Services]
- data flow components [Integration Services], validating
- data flow components [Integration Services], external metadata
- custom data flow components [Integration Services], external metadata
- external metadata [Integration Services]
ms.assetid: 8f5bd3ed-3e79-43a4-b6c1-435e4c2cc8cc
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96d413bca20ec171d515ac6d0ad81b5b994bd854
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="implementing-external-metadata"></a>외부 메타데이터 구현
  구성 요소와 해당 데이터 원본의 연결이 끊어진 경우 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100> 인터페이스를 사용하여 외부 데이터 원본의 열을 기준으로 입력 및 출력 열 컬렉션의 열에 대한 유효성을 검사할 수 있습니다. 이 인터페이스를 사용하면 외부 데이터 원본에 있는 열의 스냅숏을 유지 관리하고 이러한 열을 구성 요소의 입력 및 출력 열 컬렉션에 있는 열에 매핑할 수 있습니다.  
  
 외부 메타데이터 열을 구현하면 추가 열 컬렉션에 대한 유지 관리 및 유효성 검사를 수행해야 하므로 구성 요소 개발의 오버헤드와 복잡성이 늘어나지만 유효성 검사를 위한 고비용의 서버 왕복을 피할 수 있으면 이 개발 작업을 성공적으로 수행할 수 있습니다.  
  
## <a name="populating-external-metadata-columns"></a>외부 메타데이터 열 채우기  
 외부 메타데이터 열은 일반적으로 해당하는 입력 또는 출력 열이 만들어질 때 컬렉션에 추가됩니다. 새 열은 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.New%2A> 메서드 호출을 통해 만들어집니다. 그런 다음 열의 속성이 외부 데이터 원본과 일치하도록 설정됩니다.  
  
 외부 메타데이터 열을 해당하는 입력 또는 출력 열에 매핑하려면 해당 입력 또는 출력 열의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 속성에 외부 메타데이터 열의 ID를 할당합니다. 이렇게 하면 컬렉션의 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.GetObjectByID%2A> 메서드를 사용하여 특정 입력 또는 출력 열에 대한 외부 메타데이터 열을 쉽게 찾을 수 있습니다.  
  
 다음 예에서는 외부 메타데이터 열을 만든 다음 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSOutputColumn100.ExternalMetadataColumnID%2A> 속성을 설정하여 이 열을 외부 열에 매핑하는 방법을 보여 줍니다.  
  
```csharp  
public void CreateExternalMetaDataColumn(IDTSOutput100 output, int outputColumnID )  
{  
    IDTSOutputColumn100 oColumn = output.OutputColumnCollection.GetObjectByID(outputColumnID);  
    IDTSExternalMetadataColumn100 eColumn = output.ExternalMetadataColumnCollection.New();  
  
    eColumn.DataType = oColumn.DataType;  
    eColumn.Precision = oColumn.Precision;  
    eColumn.Scale = oColumn.Scale;  
    eColumn.Length = oColumn.Length;  
    eColumn.CodePage = oColumn.CodePage;  
  
    oColumn.ExternalMetadataColumnID = eColumn.ID;  
}  
```  
  
```vb  
Public Sub CreateExternalMetaDataColumn(ByVal output As IDTSOutput100, ByVal outputColumnID As Integer)   
 Dim oColumn As IDTSOutputColumn100 = output.OutputColumnCollection.GetObjectByID(outputColumnID)   
 Dim eColumn As IDTSExternalMetadataColumn100 = output.ExternalMetadataColumnCollection.New   
 eColumn.DataType = oColumn.DataType   
 eColumn.Precision = oColumn.Precision   
 eColumn.Scale = oColumn.Scale   
 eColumn.Length = oColumn.Length   
 eColumn.CodePage = oColumn.CodePage   
 oColumn.ExternalMetadataColumnID = eColumn.ID   
End Sub  
```  
  
## <a name="validating-with-external-metadata-columns"></a>외부 메타데이터 열을 사용하여 유효성 검사  
 유효성 검사를 수행할 때는 추가 열 컬렉션을 기준으로 해야 하므로 외부 메타데이터 열 컬렉션을 유지 관리하는 구성 요소에 대한 추가 단계가 필요합니다. 유효성 검사는 연결 시 유효성 검사와 연결 해제 시 유효성 검사로 나눌 수 있습니다.  
  
### <a name="connected-validation"></a>연결 시 유효성 검사  
 구성 요소가 외부 데이터 원본에 연결되어 있는 경우 입력 또는 출력 컬렉션의 열은 외부 데이터 원본을 기준으로 직접 유효성이 검사됩니다. 외부 메타데이터 컬렉션의 열에 대한 유효성 검사도 수행해야 합니다. 외부 메타 데이터 컬렉션을 사용 하 여 수정할 수 때문에 이것이 필요는 **고급 편집기** 에 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], 되며 컬렉션을 변경 하는 변경 내용을 감지할 수 없습니다. 따라서 연결된 상태일 때 구성 요소에서는 외부 메타데이터 열 컬렉션의 열이 계속해서 외부 데이터 원본의 열을 반영하는지 확인해야 합니다.  
  
 외부 메타 데이터 컬렉션을 숨길 수 있습니다는 **고급 편집기** 설정 하 여는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSExternalMetadataColumnCollection100.IsUsed%2A> 속성 컬렉션의 **false**합니다. 그러나이 숨겨집니다는 **열 매핑** 사용자가 입력 또는 출력 컬렉션에서 열을 외부 메타 데이터 열 컬렉션에서 열에 매핑할 수 있는 편집기의 탭 합니다. 이 속성을 설정 **false** 때도 개발자가 프로그래밍 방식으로 컬렉션을 수정할 수 없도록 하지만 에서만 사용 되는 구성 요소의 외부 메타 데이터 열 컬렉션에 대 한 보호 수준을 제공지 않습니다 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]합니다.  
  
### <a name="disconnected-validation"></a>연결 해제 시 유효성 검사  
 구성 요소가 외부 데이터 원본에 연결되어 있지 않은 경우 입력 또는 출력 컬렉션의 열은 외부 원본이 아니라 외부 메타데이터 컬렉션의 열을 기준으로 유효성이 검사되므로 유효성 검사 과정이 간단해집니다. 구성 요소 연결 되지 않은 유효성 검사를 수행 하거나 해당 외부 데이터 원본에 대 한 연결 설정 되지 않았습니다 때는 <xref:Microsoft.SqlServer.Dts.Pipeline.Wrapper.IDTSComponentMetaData100.ValidateExternalMetadata%2A> 속성은 **false**합니다.  
  
 다음 코드 예에서는 외부 메타데이터 열 컬렉션을 기준으로 유효성 검사를 수행하는 구성 요소의 구현을 보여 줍니다.  
  
```csharp  
public override DTSValidationStatus Validate()  
{  
    if( this.isConnected && ComponentMetaData.ValidateExternalMetaData )  
    {  
        // TODO: Perform connected validation.  
    }  
    else  
    {  
        // TODO: Perform disconnected validation.  
    }  
}  
```  
  
```vb  
Public  Overrides Function Validate() As DTSValidationStatus   
 If Me.isConnected AndAlso ComponentMetaData.ValidateExternalMetaData Then   
  ' TODO: Perform connected validation.  
 Else   
  ' TODO: Perform disconnected validation.  
 End If   
End Function  
```  

## <a name="see-also"></a>관련 항목:  
 [데이터 흐름](../../../integration-services/data-flow/data-flow.md)  
  
  