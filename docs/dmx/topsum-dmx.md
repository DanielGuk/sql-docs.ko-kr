---
title: TopSum (DMX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- TOPSUM
dev_langs:
- DMX
helpviewer_keywords:
- TopSum function
ms.assetid: a0bebdfa-3db2-4818-ab8c-440598de71f1
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 7151f28a59f7020cd71388a4236ce2198ff4cbc4
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="topsum-dmx"></a>TopSum(DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  누적 합계가 지정한 값 이상이 되는 테이블의 맨 위 행을 내림차순으로 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
TopSum(<table expression>, <rank expression>, <sum>)  
```  
  
## <a name="applies-to"></a>적용 대상  
 와 같은 테이블을 반환 하는 식은 \<테이블 열 참조 >, 또는 테이블을 반환 하는 함수입니다.  
  
## <a name="return-type"></a>반환 형식  
 \<테이블 식 >  
  
## <a name="remarks"></a>주의  
 **TopSum** 의 계산된 값에 따라 차수의 내림차순으로 정렬의 최상위 행을 반환 하는 함수는 \<식의 순위 > 각 행에 대 한 인수 되도록의 합계는 \<식의 순위 > 값으로 지정 된 지정 된 합계 이상이 되는 \<합계 > 인수입니다. **TopSum** 지정된 된 합계 값에 맞추어 가능한 가장 작은 요소 수를 반환 합니다.  
  
## <a name="examples"></a>예  
 다음 예제에서는 연결 모델을 사용 하 여 작성에 대 한 예측 쿼리는 [기본 데이터 마이닝 자습서](http://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c)합니다.  
  
 TopPercent의 작동 방식을 이해 하려면 우선 중첩된 테이블만 반환 하는 예측 쿼리를 실행 하는 것이 도움이 수도 있습니다.  
  
```  
SELECT Predict ([Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 10)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
> [!NOTE]  
>  이 예에서 입력으로 제공된 값에는 작은따옴표가 들어 있으므로 작은따옴표를 앞에 추가하여 이스케이프해야 합니다. 이스케이프 문자를 삽입하는 구문을 모르는 경우 예측 쿼리 작성기를 사용하여 쿼리를 만들 수 있습니다. 드롭다운 목록에서 값을 선택하면 필요한 이스케이프 문자가 자동으로 삽입됩니다. 자세한 내용은 참조 [데이터 마이닝 디자이너에서 단일 쿼리를 만들](../analysis-services/data-mining/create-a-singleton-query-in-the-data-mining-designer.md)합니다.  
  
 예제 결과:  
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.291283016|0.252695851|  
|Water Bottle|2866|0.192620472|0.175205052|  
|Patch kit|2113|0.142012232|0.132389356|  
|Mountain Tire Tube|1992|0.133879965|0.125304948|  
|Mountain-200|1755|0.117951475|0.111260823|  
|Road Tire Tube|1588|0.106727603|0.101229538|  
|Cycling Cap|1473|0.098998589|0.094256014|  
|Fender Set - Mountain|1415|0.095100477|0.090718432|  
|Mountain Bottle Cage|1367|0.091874454|0.087780332|  
|Road Bottle Cage|1195|0.080314537|0.077173962|  
  
 **TopSum** 함수가 쿼리의 결과 받고 가장 큰 값을 가진 행 합계가 지정된 된 횟수를 반환 합니다.  
  
```  
SELECT   
TopSum  
    (  
    Predict([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,10),  
    $PROBABILITY,  
    .5)  
FROM   
     [Association]  
NATURAL PREDICTION JOIN  
(SELECT (SELECT 'Women''s Mountain Shorts' as [Model]) AS [v Assoc Seq Line Items]) AS t  
```  
  
 첫 번째 인수는 **TopSum** 함수는 테이블 열의 이름입니다. 이 예제에서는 중첩된 테이블은 예측 함수를 호출 하 고 INCLUDE_STATISTICS 인수를 사용 하 여 반환 됩니다.  
  
 두 번째 인수는 **TopSum** 함수 결과 정렬 하는 데 사용 하는 중첩된 테이블의 열입니다. 이 예에서 INCLUDE_STATISTICS 옵션은 $SUPPORT, $PROBABILTY 및 $ADJUSTED PROBABILITY 열을 반환합니다. 이 예에서는 $PROBABILITY를 사용하여 확률 합계가 최소 50%인 행을 반환합니다.  
  
 세 번째 인수는 **TopSum** 을 double로 대상 합계를 지정 하는 함수입니다. 확률 합계가 50%인 최상위 제품의 행을 가져오려면 .5를 입력합니다.  
  
 예제 결과:  
  
|Model|$SUPPORT|$PROBABILITY|$ADJUSTEDPROBABILITY|  
|-----------|--------------|------------------|--------------------------|  
|Sport-100|4334|0.29…|0.25…|  
|Water Bottle|2866|0.19…|0.17…|  
|Patch kit|2113|0.14…|0.13…|  
  
 **참고** 이 예제는 사용법을 설명 하기 위해 제공 됩니다 **TopSum**합니다. 데이터 집합의 크기에 따라 이 쿼리를 실행하는 데 시간이 오래 걸릴 수 있습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [함수 &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [일반 예측 함수 &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [TopPercent &#40; DMX &#41;](../dmx/toppercent-dmx.md)  
  
  
