---
title: 쿼리 및 Slicer Axis (MDX)으로 쿼리 제한 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4de964dcfa7bad1f307de12e81593c93bcd8e859
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34020780"
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>MDX 쿼리 및 Slicer 축-쿼리 제한
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  MDX(Multidimensional Expressions) SELECT 쿼리를 구성할 때 애플리케이션에서는 일반적으로 큐브를 검토하고 계층 집합을 다음과 같이 두 개의 하위 집합으로 나눕니다.  
  
-   **Query 축**- 여러 멤버에 대해 데이터가 검색되는 계층 집합입니다. 쿼리 축에 대한 자세한 내용은 [쿼리 축의 내용 지정&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)을 참조하세요.  
  
-   **Slicer 축**- 단일 멤버에 대해 데이터가 검색되는 계층 집합입니다. Slicer 축에 대한 자세한 내용은 [Slicer 축의 내용 지정&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)을 참조하세요.  
  
 쿼리 및 slicer 축은 쿼리할 큐브의 여러 계층으로부터 구성될 수 있으므로, 이러한 용어는 MDX 쿼리로 반환된 큐브에서 생성되는 계층으로부터 쿼리할 큐브가 사용하는 계층을 구분하기 위해 사용됩니다.  
  
 쿼리 및 slicer 축을 사용하는 간단한 예제를 보려면 [간단한 예제에서 쿼리 및 Slicer 축 사용&#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목:  
 [멤버, 튜플 및 집합 & #40; 사용 Mdx& #41;](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [MDX 쿼리 기본 사항 & #40; Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
