---
title: GetChildren 메서드 (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_GetChildren
- _Record::GetChildren
helpviewer_keywords:
- GetChildren method [ADO]
ms.assetid: b3f09bac-4f66-49f6-aa5a-6fbb4fb28338
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 910977912a23ee48f740afccdb58c6f82801f2a7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47784185"
---
# <a name="getchildren-method-ado"></a>GetChildren 메서드(ADO)
반환 된 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md) 컬렉션의 자식을 나타내는 행이 있는 [레코드](../../../ado/reference/ado-api/record-object-ado.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Set recordset = record.GetChildren  
```  
  
## <a name="return-value"></a>반환 값  
 A **Recordset** 개체는 각 행이 나타내는 현재 자식 **레코드** 개체입니다. 예를 들어 자식을 **레코드** 나타냅니다 디렉터리는 되도록 파일과 하위 디렉터리의 부모 디렉터리 내에 포함 합니다.  
  
## <a name="remarks"></a>Remarks  
 열에 반환 되는 공급자에 따라 결정 **레코드 집합**합니다. 예를 들어, 문서 소스 공급자 리소스를 항상 반환 **레코드 집합**합니다.  
  
## <a name="applies-to"></a>적용 대상  
  
|||  
|-|-|  
|[레코드 개체(ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[레코드 집합 개체(ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|
