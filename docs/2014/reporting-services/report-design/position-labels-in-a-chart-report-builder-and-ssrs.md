---
title: 차트의 레이블 위치 지정(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 5db74e0b-8be8-4b47-b386-faab56dffa9b
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 77a4a9b2749eefbe43cac04351fd1d2bd2c9300e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138762"
---
# <a name="position-labels-in-a-chart-report-builder-and-ssrs"></a>차트의 레이블 위치 지정(보고서 작성기 및 SSRS)
  차트 종류마다 셰이프가 다르므로 데이터 요소 레이블은 차트에서 방해가 되지 않을 최적의 위치에 배치됩니다. 레이블의 기본 위치는 차트 종류에 따라 달라집니다.  
  
-   누적 차트에서 레이블은 계열의 안쪽에만 배치할 수 있습니다.  
  
-   깔때기형 또는 피라미드형 차트에서 레이블은 열의 바깥쪽에 배치됩니다.  
  
-   원형 차트에서 레이블은 원형 차트의 개별 조각 안쪽에 배치됩니다.  
  
-   가로 막대형 차트에서 레이블은 데이터 요소를 나타내는 막대의 바깥쪽에 배치됩니다.  
  
-   극좌표형 차트에서 레이블은 데이터 요소를 나타내는 원형 영역의 바깥쪽에 배치됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-position-of-point-labels-in-a-pie-chart"></a>원형 차트에서 요소 레이블의 위치를 변경하려면  
  
1.  원형 차트를 만듭니다.  
  
2.  디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.  
  
3.  속성 창을 엽니다. **보기** 탭에서 **속성**을 클릭합니다.  
  
4.  디자인 화면에서 차트를 클릭합니다. 차트의 속성이 속성 창에 표시됩니다.  
  
5.  **일반** 섹션에서 **CustomAttributes** 노드를 확장합니다. 원형 차트에 대한 특성 목록이 표시됩니다.  
  
6.  PieLabelStyle 속성의 값을 선택합니다.  
  
### <a name="to-change-the-position-of-point-labels-in-a-funnel-or-pyramid-chart"></a>깔때기형 또는 피라미드형 차트에서 요소 레이블의 위치를 변경하려면  
  
1.  깔때기형 또는 피라미드형 차트를 만듭니다.  
  
2.  디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.  
  
3.  속성 창을 엽니다. **보기** 탭에서 **속성**을 클릭합니다.  
  
4.  디자인 화면에서 차트를 클릭합니다. 차트의 속성이 속성 창에 표시됩니다.  
  
5.  **일반** 섹션에서 **CustomAttributes** 노드를 확장합니다. 깔때기형 차트에 대한 특성 목록이 표시됩니다.  
  
6.  깔때기형 차트의 경우 FunnelLabelStyle 속성의 값을 선택하고, 피라미드형 차트의 경우 PyramidLabelStyle 속성의 값을 선택합니다.  
  
    > [!NOTE]  
    >  이 속성 값으로 설정 되는 경우 `OutsideInColumn`, 레이블이 세로 열에 그려집니다. 열의 위치는 변경할 수 없습니다.  
  
### <a name="to-change-the-position-of-point-labels-in-a-bar-chart"></a>가로 막대형 차트에서 요소 레이블의 위치를 변경하려면  
  
1.  가로 막대형 차트를 만듭니다.  
  
2.  디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.  
  
3.  속성 창을 엽니다. **보기** 탭에서 **속성**을 클릭합니다.  
  
4.  디자인 화면에서 차트를 클릭합니다. 차트의 속성이 속성 창에 표시됩니다.  
  
5.  **일반** 섹션에서 **CustomAttributes** 노드를 확장합니다. 막대형 차트에 대한 특성 목록이 표시됩니다.  
  
6.  BarLabelStyle 속성의 값을 선택합니다.  
  
 막대 레이블 스타일으로 설정 된 `Outside`,으로 차트 영역 내에서 막대의 바깥쪽 레이블을 배치 됩니다. 레이블을 막대의 바깥쪽에 배치할 수 없지만 차트 영역의 안쪽에는 배치할 수 있는 경우 레이블은 막대 안쪽에서 막대 끝에 가장 가까운 위치에 배치됩니다.  
  
### <a name="to-change-the-position-of-point-labels-in-an-area-column-line-or-scatter-chart"></a>영역형, 세로 막대형, 꺾은선형 또는 분산형 차트에서 요소 레이블의 위치를 변경하려면  
  
1.  영역형, 세로 막대형, 꺾은선형 또는 분산형 차트를 만듭니다.  
  
2.  디자인 화면에서 차트를 마우스 오른쪽 단추로 클릭하고 **데이터 레이블 표시**를 선택합니다.  
  
3.  속성 창을 엽니다. **보기** 탭에서 **속성**을 클릭합니다.  
  
4.  디자인 화면에서 계열을 클릭합니다. 계열의 속성이 속성 창에 표시됩니다.  
  
5.  **데이터** 섹션에서 **DataPoint** 노드를 확장한 다음 **Label**노드를 확장합니다.  
  
6.  Position 속성의 값을 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [원형 차트 &#40;보고서 작성기 및 SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [가로 막대형 차트 &#40;보고서 작성기 및 SSRS&#41;](bar-charts-report-builder-and-ssrs.md)   
 [차트의 축 레이블 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
 [축 레이블의 서식을 날짜 또는 통화로 지정&#40;보고서 작성기 및 SSRS&#41;](format-axis-labels-as-dates-or-currencies-report-builder-and-ssrs.md)   
 [원형 차트 외부에 표시 데이터 요소 레이블 &#40;보고서 작성기 및 SSRS&#41;](display-data-point-labels-outside-a-pie-chart-report-builder-and-ssrs.md)   
 [차트의 데이터 요소에 서식 지정&#40;보고서 작성기 및 SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md)  
  
  
