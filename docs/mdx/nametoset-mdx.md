---
title: NameToSet (MDX) | Microsoft Docs
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
- NAMETOSET
dev_langs:
- kbMDX
helpviewer_keywords:
- NameToSet function
ms.assetid: e02e17d5-4309-49cb-84c7-5b445ac2bd94
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b615ddfdf8698e1d495e6d6070e489aa448d4c96
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="nametoset-mdx"></a>NameToSet(MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  MDX(Multidimensional Expressions) 형식 문자열에 의해 지정된 멤버가 포함된 집합을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>인수  
 *Member_Name*  
 멤버 이름을 나타내는 유효한 문자열 식입니다.  
  
## <a name="remarks"></a>주의  
 지정 된 멤버 이름이 있는 경우는 **NameToSet** 함수는 해당 멤버를 포함 하는 집합을 반환 합니다. 그렇지 않으면 빈 집합을 반환합니다.  
  
> [!NOTE]  
>  멤버는 멤버 식이 아니라 멤버 이름으로만 지정해야 합니다. 멤버 식을 사용 하려면 참조 [StrToSet &#40; Mdx&#41; ](../mdx/strtoset-mdx.md).  
  
## <a name="example"></a>예제  
 다음 예에서는 지정된 멤버 이름의 기본 측정값을 반환합니다.  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>관련 항목:  
 [MDX 함수 참조 &#40; Mdx&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
