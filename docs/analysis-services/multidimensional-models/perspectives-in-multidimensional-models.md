---
title: 다차원 모델의 큐브 뷰 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5427142f682d4fb76011c0514539267d05c3097b
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34023680"
---
# <a name="perspectives-in-multidimensional-models"></a>다차원 모델의 큐브 뷰
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  큐브 뷰는 특정 애플리케이션이나 사용자 그룹을 위해 생성된 큐브 하위 집합입니다. 큐브 자체가 기본 큐브 뷰입니다. 큐브 뷰는 큐브로 클라이언트에게 노출됩니다. 큐브 뷰는 사용자에게 다른 큐브와 같게 보입니다. 큐브 뷰에서 쓰기 저장을 통해 큐브 데이터를 변경하면 원본 큐브에 변경 내용이 반영됩니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 뷰에 대한 자세한 내용은 [큐브 뷰](../../analysis-services/multidimensional-models-olap-logical-cube-objects/perspectives.md)를 참조하세요.  
  
 큐브 디자이너의 **큐브 뷰** 탭을 사용하여 큐브에 큐브 뷰를 만들거나 수정할 수 있습니다. **큐브 뷰** 탭의 첫 번째 열은 큐브의 모든 개체가 나열된 **큐브 개체** 열입니다. 이 열은 큐브의 기본 큐브 뷰에 해당되며, 큐브 자체를 나타냅니다.  
  
## <a name="creating-or-deleting-perspectives"></a>큐브 뷰 만들기 또는 삭제  
 **큐브** 메뉴의 **새 큐브 뷰** 를 클릭하여 **큐브 뷰** 탭에 큐브 뷰를 추가할 수 있습니다. 도구 모음의 **새 큐브 뷰** 단추를 클릭하거나 창의 아무 곳이나 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **새 큐브 뷰** 를 클릭해도 됩니다. 큐브에 큐브 뷰를 얼마든지 추가할 수 있습니다.  
  
 큐브 뷰를 제거하려면 먼저 삭제할 큐브 뷰에 해당하는 열에서 아무 셀이나 클릭합니다. 그런 다음 **큐브** 메뉴에서 **큐브 뷰 삭제**를 클릭합니다. 도구 모음에서 **큐브 뷰 삭제** 단추를 클릭하거나 삭제할 큐브 뷰에서 아무 셀이나 마우스 오른쪽 단추로 클릭하고 바로 가기 메뉴에서 **큐브 뷰 삭제** 를 클릭해도 됩니다.  
  
## <a name="renaming-perspectives"></a>큐브 뷰 이름 바꾸기  
 각 큐브 뷰의 첫 번째 행에 큐브 뷰의 이름이 표시됩니다. 큐브 뷰를 만들면 처음에는 이름이 Perspective입니다. Perspective라는 큐브 뷰가 이미 있는 경우에는 1부터 시작하는 서수가 뒤에 붙습니다. 이름을 클릭하고 편집할 수 있습니다.  
  
## <a name="hiding-objects-from-a-perspective"></a>큐브 뷰에서 개체 숨기기  
 큐브 뷰에서 개체를 숨기려면 큐브 뷰 열에서 해당 개체에 대한 행에 있는 확인란의 선택을 취소합니다. 큐브 뷰에서 숨길 수 있는 큐브 개체는 다음과 같습니다.  
  
-   측정값 그룹  
  
-   측정값 그룹  
  
-   차원  
  
-   계층 구조  
  
-   명명된 집합  
  
-   KPI  
  
-   작업  
  
-   계산 멤버  
  
 개체를 표시하려면**큐브 개체**에서 해당 개체 유형에 대한 범주( **측정값 그룹**, **차원**, **KPI**, **계산**또는 **동작**)를 확장합니다. 차원의 계층이나 특성을 표시하려면 먼저 차원을 확장한 다음 **계층** 또는 **특성** 행을 확장합니다. 측정값 그룹의 측정값을 표시하려면 측정값 그룹을 확장합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [다차원 모델의 큐브](../../analysis-services/multidimensional-models/cubes-in-multidimensional-models.md)  
  
  
