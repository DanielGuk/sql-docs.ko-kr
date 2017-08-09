---
title: Axis (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AXIS
dev_langs:
- kbMDX
helpviewer_keywords:
- Axis function
ms.assetid: a3a60a1e-e266-4fa1-ae13-bae73544de33
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 95a1d7f16c7f30f2a118820414994a615090d96c
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="axis-mdx"></a>Axis(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  튜플 집합을 지정된 축에 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Axis(Axis_Number)  
```  
  
## <a name="arguments"></a>인수  
 *Axis_Number*  
 축 번호를 지정하는 유효한 숫자 식입니다.  
  
## <a name="remarks"></a>주의  
 **축** 함수 축의 0부터 시작 위치를 사용 하 여 축의 튜플 집합을 반환 합니다. 예를 들어 `Axis(0)`은 COLUMNS 축을 반환하고, `Axis(1)`은 ROWS 축을 반환하는 식으로 진행됩니다. **축** 필터 축에 함수를 사용할 수 없습니다. 이 함수를 사용하면 계산 멤버에서 실행될 쿼리의 컨텍스트를 인식하도록 지정할 수 있습니다. 예를 들어 Rows 축에서 선택한 계산 멤버의 합계만 제공하는 계산 멤버가 필요할 수 있습니다. 또한 이 함수를 사용하여 한 축의 정의가 다른 축의 정의에 종속되도록 지정할 수 있습니다. 예를 들어 Columns 축의 첫 번째 항목 값에 따라 Rows 축의 내용을 정렬할 수 있습니다.  
  
> [!NOTE]  
>  축은 이전 축만 참조할 수 있습니다. 예를 들어 `Axis(0)`은 ROW 또는 PAGE 축과 같이 COLUMNS 축이 계산된 다음에만 발생해야 합니다.  
  
## <a name="examples"></a>예  
 다음 예제 쿼리에서는 Axis 함수를 사용하는 방법을 보여 줍니다.  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SETTOSTR(AXIS(1))`  
  
 `SELECT MEASURES.AXISDEMO ON 0,`  
  
 `[Date].[Calendar Year].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
 다음 예에서는 계산 멤버 내에 Axis 함수를 사용하는 방법을 보여 줍니다.  
  
 `WITH MEMBER MEASURES.AXISDEMO AS`  
  
 `SUM(AXIS(1), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.AXISDEMO} ON 0,`  
  
 `{[Date].[Calendar Year].&[2003], [Date].[Calendar Year].&[2004]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
