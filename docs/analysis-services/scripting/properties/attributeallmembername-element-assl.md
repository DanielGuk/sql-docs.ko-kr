---
title: "AttributeAllMemberName 요소 (ASSL) | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- AttributeAllMemberName Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AttributeAllMemberName
helpviewer_keywords:
- AttributeAllMemberName element
ms.assetid: 5ede46a7-d8b0-40be-98d7-b01047b27d2e
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1024fe64852c6f6eca731e6ef8f03ec1e56b012d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="attributeallmembername-element-assl"></a>AttributeAllMemberName 요소(ASSL)
  차원의 All 멤버에 대한 캡션을 기본 언어로 포함합니다.  
  
## <a name="syntax"></a>구문  
  
```xml  
  
<Dimension>  
      ...  
   <AttributeAllMemberName>...</AttributeAllMemberName>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|데이터 형식 및 길이|문자열|  
|기본값|없음|  
|카디널리티|0-1: 한 번만 나타날 수 있는 선택적 요소입니다.|  
  
## <a name="element-relationships"></a>요소 관계  
  
|관계|요소|  
|------------------|-------------|  
|부모 요소|[Dimension](../../../analysis-services/scripting/objects/dimension-element-assl.md)|  
|자식 요소|없음|  
  
## <a name="remarks"></a>주의  
 부모에 해당 하는 요소 **AttributeAllMemberName** Analysis Management Objects (AMO) 개체 모델은 <xref:Microsoft.AnalysisServices.Dimension>합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [구성에서 &#40; 모든 &#41; 특성 계층의 수준](../../../analysis-services/multidimensional-models/database-dimensions-configure-the-all-level-for-attribute-hierarchies.md)   
 [속성 &#40; ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  