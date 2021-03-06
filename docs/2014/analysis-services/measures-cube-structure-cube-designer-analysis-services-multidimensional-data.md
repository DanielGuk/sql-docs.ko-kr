---
title: 측정값 (Cube Structure Tab, Cube Designer) (Analysis Services-다차원 데이터) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.cubebuilder.measurespane.f1
ms.assetid: be70f63b-58f2-4eff-81bc-c86d8229e617
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3b063029126a8141e1a1a8044991a1653b536b8
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090322"
---
# <a name="measures-cube-structure-tab-cube-designer-analysis-services---multidimensional-data"></a>측정값(큐브 구조 탭, 큐브 디자이너)(Analysis Services - 다차원 데이터)
  큐브 디자이너의 **큐브 구조** 탭에서 **측정값** 창을 사용하여 측정값 그룹 및 멤버를 조작할 수 있습니다.  
  
## <a name="options"></a>변수  
 큐브 구조  
 큐브에 포함된 측정값 그룹 및 측정값을 다음 두 가지 뷰 중 선택한 뷰에 따라 표시합니다.  
  
 trEE  
 측정값을 자식 노드로 하여 측정값 그룹의 트리 뷰를 표시합니다.  
  
 측정값을 보려면 측정값 그룹을 확장합니다. 측정값 그룹 또는 측정값의 이름을 바꾸려면 선택한 측정값 그룹 또는 측정값을 클릭합니다.  
  
 표 형태  
 측정값 및 해당 측정값에서 가장 많이 액세스하는 속성의 표를 표시합니다. **새 측정값** 대화 상자를 표시하고 표에 새 측정값을 추가하려면 **새 측정값 추가** 를 클릭합니다.  
  
 표에는 다음 열이 있습니다.  
  
 이름  
 측정값 이름을 입력합니다.  
  
 측정값 그룹  
 측정값이 들어 있는 측정값 그룹을 표시합니다.  
  
 데이터 형식  
 측정값의 데이터 형식을 선택합니다.  
  
 집계  
 측정값의 집계 함수를 선택합니다.  
  
## <a name="context-menu"></a>상황에 맞는 메뉴  
 다음 옵션은 **측정값** 창을 마우스 오른쪽 단추로 클릭하면 표시되는 상황에 맞는 메뉴를 통해 사용할 수 있습니다.  
  
 **새 측정값**  
 **새 측정값** 대화 상자를 표시하고 현재 **측정값** 창에서 선택한 측정값 그룹에 새 측정값을 추가하려면 선택합니다.  
  
 **새 측정값 그룹**  
 **새 측정값 그룹** 대화 상자를 표시하고 **측정값** 창에 새 측정값 그룹을 추가하려면 선택합니다.  
  
 **측정값 표시 위치**  
 다음 옵션 간에 전환하거나 하나를 선택하여 **측정값** 창의 뷰를 변경하려면 선택합니다.  
  
|옵션|정의|  
|------------|----------------|  
|**트리**|측정값 그룹과 측정값을 트리 뷰에 표시합니다.|  
|**표**|측정값 그룹과 측정값을 표에 표시합니다.|  
  
 **이름 바꾸기**  
 선택한 측정값 그룹 또는 측정값의 이름을 바꾸려면 선택합니다.  
  
 **Delete**  
 **개체 삭제** 대화 상자를 표시하고 **측정값** 창에서 선택한 개체를 삭제하려면 클릭합니다.  
  
 **위로 이동**  
 선택한 측정값 그룹 또는 측정값을 한 단계 위로 이동하려면 선택합니다.  
  
> [!NOTE]  
>  이 옵션은 선택한 항목을 위로 이동할 수 없는 경우에는 사용할 수 없습니다.  
  
 **아래로 이동**  
 선택한 측정값 그룹 또는 측정값을 한 단계 아래로 이동하려면 선택합니다.  
  
> [!NOTE]  
>  이 옵션은 선택한 항목을 아래로 이동할 수 없는 경우에는 사용할 수 없습니다.  
  
 **새 연결 된 개체**  
 **연결된 개체 마법사** 를 표시하여 다른 큐브의 측정값 그룹 및 차원을 연결하고 선택한 큐브로 동작, KPI 및 계산을 가져오려면 클릭합니다.  
  
 **Properties**  
 선택한 측정값 그룹 또는 측정값에 대해 **의** 속성 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 창을 표시하려면 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [측정값 속성 구성](multidimensional-models/configure-measure-properties.md)   
 [측정값 및 측정값 그룹](multidimensional-models/measures-and-measure-groups.md)  
  
  
