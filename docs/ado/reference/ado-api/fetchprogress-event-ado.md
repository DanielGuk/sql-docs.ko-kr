---
title: "FetchProgress 이벤트 (ADO) | Microsoft Docs"
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
- FetchProgress
- Recordset::FetchProgress
helpviewer_keywords:
- FetchProgress event [ADO]
ms.assetid: 301716fd-81fc-40eb-8a04-221ef7ab410e
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 606e91ca69d981cf4c1396109f0114ce0244dc3b
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="fetchprogress-event-ado"></a>FetchProgress 이벤트 (ADO)
**FetchProgress**이벤트에 현재으로 가져온 더 많은 행의 수를 보고 하기 위해 시간이 오래 걸리는 비동기 작업을 하는 동안에 주기적으로 호출 됩니다는 [레코드 집합](../../../ado/reference/ado-api/recordset-object-ado.md)합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
FetchProgress Progress, MaxProgress, adStatus, pRecordset  
```  
  
#### <a name="parameters"></a>매개 변수  
 *진행률*  
 A **긴** 현재 반입 작업을 통해 검색 된 레코드의 수를 나타내는 값입니다.  
  
 *MaxProgress*  
 A **긴** 레코드의 최대 수를 나타내는 값을 검색할 필요 합니다.  
  
 *adStatus*  
 [EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md) 상태 값입니다.  
  
 *pRecordset*  
 A **레코드 집합** 레코드는 가져온 개체입니다.  
  
## <a name="remarks"></a>주의  
 사용 하는 경우 **FetchProgress** 자식이 있는 **레코드 집합**, 알아야 하는 *진행률* 및 *MaxProgress* 매개 변수 값에서 파생 된 기본 [커서 서비스](../../../ado/guide/appendixes/microsoft-cursor-service-for-ole-db-ado-service-component.md) 행 집합입니다. 반환 되는 값은 현재 장의 레코드 수가 뿐 아니라 원본 행 집합에 있는 레코드의 총 수를 나타냅니다.  
  
> [!NOTE]
>  사용 하도록 **FetchProgress** 와 Microsoft Visual Basic, Visual Basic 6.0 이상이 필요 합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [ADO 이벤트 모델 예제 (VC + +)](../../../ado/reference/ado-api/ado-events-model-example-vc.md)   
 [ADO 이벤트 처리기 요약](../../../ado/guide/data/ado-event-handler-summary.md)