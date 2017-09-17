---
title: ParameterDirectionEnum | Microsoft Docs
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- ParameterDirectionEnum
helpviewer_keywords:
- ParameterDirectionEnum enumeration [ADO]
ms.assetid: c66aa6e6-d4f0-4f0f-9640-e08ae6cfdef3
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c32176b7c9c5dc235c77e5f2363f1fc51ae9bb40
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="parameterdirectionenum"></a>ParameterDirectionEnum
지정 여부는 [매개 변수](../../../ado/reference/ado-api/parameter-object.md) 는 입력된 매개 변수, 출력 매개 변수, 둘 다는 출력 매개 변수 또는 저장된 프로시저에서 반환 값 및 합니다.  
  
|상수|값|Description|  
|--------------|-----------|-----------------|  
|**adParamInput**|1.|기본. 매개 변수는 입력된 매개 변수를 나타냅니다.|  
|**adParamInputOutput**|3|매개 변수는 입력 및 출력 매개 변수를 나타냅니다.|  
|**adParamOutput**|2|매개 변수는 출력 매개 변수를 나타냅니다.|  
|**adParamReturnValue**|4|매개 변수를 반환 값을 나타냅니다.|  
|**adParamUnknown**|0|매개 변수 방향은 알려진 임을 나타냅니다.|  
  
## <a name="adowfc-equivalent"></a>해당 하는 ADO/WFC  
 패키지에 대 한 **com.ms.wfc.data**  
  
|상수|  
|--------------|  
|AdoEnums.ParameterDirection.INPUT|  
|AdoEnums.ParameterDirection.INPUTOUTPUT|  
|AdoEnums.ParameterDirection.OUTPUT|  
|AdoEnums.ParameterDirection.RETURNVALUE|  
|AdoEnums.ParameterDirection.UNKNOWN|  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[CreateParameter 메서드(ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|[Direction 속성](../../../ado/reference/ado-api/direction-property.md)|