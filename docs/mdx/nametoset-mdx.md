---
title: NameToSet (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5bb38614d9c83b0624d76f9f09c377c9fcbf82fb
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742362"
---
# <a name="nametoset-mdx"></a>NameToSet(MDX)


  MDX(Multidimensional Expressions) 형식 문자열에 의해 지정된 멤버가 포함된 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>인수  
 *Member_Name*  
 멤버 이름을 나타내는 유효한 문자열 식입니다.  
  
## <a name="remarks"></a>Remarks  
 지정 된 멤버 이름이 있는 경우는 **NameToSet** 함수는 해당 멤버를 포함 하는 집합을 반환 합니다. 그렇지 않으면 빈 집합을 반환합니다.  
  
> [!NOTE]  
>  멤버는 멤버 식이 아니라 멤버 이름으로만 지정해야 합니다. 멤버 식을 사용 하려면 참조 [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)합니다.  
  
## <a name="example"></a>예제  
 다음 예에서는 지정된 멤버 이름의 기본 측정값을 반환합니다.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목  
 [MDX 함수 참조 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
