---
title: "Members (집합) (MDX) | Microsoft Docs"
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
- Members
dev_langs:
- kbMDX
helpviewer_keywords:
- Members function
ms.assetid: 0c4d5bb9-500b-47ce-b7fc-f5a10e2400e0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 4430d24665eb791b8567fa83e7793c64727fd88f
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="members-set-mdx"></a>Members(집합)(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  차원, 수준 또는 계층의 멤버 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>인수  
 *Hierarchy_Expression*  
 계층을 반환하는 유효한 MDX 식입니다.  
  
 *Level_Expression*  
 수준을 반환하는 유효한 MDX 식입니다.  
  
## <a name="remarks"></a>주의  
 계층 식이 지정 되는 **Members (집합)** 함수 계산된 멤버를 포함 하지 않고 지정된 된 계층 내의 모든 멤버 집합을 반환 합니다. 계산 하는 모든 멤버 집합을 구하거 나, 계층 구조를 사용 하 여 [AllMembers &#40; Mdx&#41; ](../mdx/allmembers-mdx.md) 함수  
  
 수준 식이 지정 되는 **Members (집합)** 함수는 지정 된 수준 내의 모든 멤버 집합을 반환 합니다.  
  
> [!IMPORTANT]  
>  차원에 표시 가능한 계층이 하나만 있는 경우 해당 차원 이름은 표시 가능한 유일한 계층으로 확인되므로 해당 계층을 차원 이름이나 계층 이름 중 하나로 참조할 수 있습니다. 예를 들어 Measures.Members는 Measures 차원의 유일한 계층으로 확인되므로 유효한 MDX 식입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 Adventure Works 큐브에 있는 Calendar Year 계층의 모든 멤버 집합을 반환합니다.  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 다음 예에서는 `[Product].[Products].[Product Line]` 수준의 각 멤버에 대해 2003년 주문 수량을 반환합니다. **멤버** 함수 모든 수준의 멤버를 나타내는 집합을 반환 합니다.  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>참고 항목  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
