---
title: RangeMax (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 417f92a00e396952218c6ef04d105245f1e3708e
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2018
ms.locfileid: "37968265"
---
# <a name="rangemax-dmx"></a>RangeMax(DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  불연속화된 열에 대해 발견한 예측 버킷의 최대값을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>적용 대상  
 스칼라 열  
  
## <a name="return-type"></a>반환 형식  
 스칼라 값  
  
## <a name="remarks"></a>Remarks  
 합니다 **RangeMax** 함수에서 사용할 수 있습니다 [SELECT DISTINCT FROM &#60;모델 &#62; &#40;DMX&#41; ](../dmx/select-distinct-from-model-dmx.md) 쿼리 합니다. 이 쿼리 유형에 스칼라 열 참조를 사용하면 해당 참조에 예측 가능 또는 입력 형식에 해당하는 연속 열이나 불연속 열이 포함될 수 있습니다.  
  
 와 함께 사용할 경우 [선택에서 &#60;모델&#62; PREDICTION JOIN &#40;DMX&#41;](../dmx/select-from-model-prediction-join-dmx.md)의 **RangeMin**를 **RangeMid**, 및 **RangeMax**  함수는 지정 된 버킷의 실제 경계 값을 반환 합니다. 예를 들어 불연속화된 열에 대해 예측을 수행하면 해당 쿼리는 불연속화된 열의 예측 버킷 번호를 반환합니다. 합니다 **RangeMin**를 **RangeMid**, 및 **RangeMax** 함수는 예측이 지정 하는 버킷을 설명 합니다. 경우는 **RangeMax** PREDICTION JOIN 문을 사용 하 여 함수는, 스칼라 열 참조에는 예측 가능한 불연속 열만 포함할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Decision Tree 마이닝 모델의 Yearly Income 연속 열에 대한 최대값, 최소값 및 평균값을 반환합니다.  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>관련 항목  
 [Data Mining Extensions &#40;DMX&#41; 함수 참조](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [함수 &#40;DMX&#41;](../dmx/functions-dmx.md)   
 [일반 예측 함수 &#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40;DMX&#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40;DMX&#41;](../dmx/rangemin-dmx.md)  
  
  
