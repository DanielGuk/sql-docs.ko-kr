---
title: 그룹 이해(보고서 작성기 및 SSRS) | Microsoft Docs
ms.date: 03/07/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
f1_keywords:
- "10056"
- "10424"
ms.assetid: c32d4d89-45e4-4f77-a3e9-0429f53f9d6f
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: c9d7125e0575a5df51baa0594aee39e366b015ca
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47608311"
---
# <a name="understanding-groups-report-builder-and-ssrs"></a>그룹 이해(보고서 작성기 및 SSRS)
  [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 페이지를 매긴 보고서에서 그룹은 데이터 영역에 바인딩된 보고서 데이터 집합의 명명된 데이터 집합입니다. 기본적으로 그룹은 보고서 데이터 집합의 뷰를 구성합니다. 데이터 영역의 모든 그룹은 같은 보고서 데이터 집합의 서로 다른 뷰를 지정합니다.  
  
 그룹의 개념을 시각적으로 이해하려면 테이블릭스 데이터 영역의 미리 보기를 보여 주는 다음 그림을 참조하십시오. 이 그림에서 행 그룹은 제품 종류별로 데이터 집합을 범주화하고 열 그룹은 지리적 지역과 연도별로 데이터 집합을 범주화합니다.  
  
 ![Tablix data region areas](../../reporting-services/report-design/media/rs-tablixareas.gif "Tablix data region areas")  
  
 다음 섹션에서는 그룹의 다양한 측면에 대해 설명합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="what-makes-a-group"></a>그룹의 구성  
 그룹에는 이름 및 지정한 그룹 식 집합이 포함되어 있습니다. 그룹 식 집합은 단일 데이터 집합 필드에 대한 참조이거나 여러 식의 조합일 수 있습니다. 그룹에 여러 식이 있으면 런타임에 그룹 식이 결합되어 그룹의 데이터에 적용됩니다. 예를 들어 날짜 필드를 사용하여 데이터 영역에 있는 데이터를 구성하는 그룹이 있는 경우 런타임에 데이터가 날짜별로 구성된 다음 각 날짜에 대해 기타 데이터 집합 값이 합계와 함께 표시됩니다.  
  
## <a name="when-do-i-create-groups"></a>그룹을 만드는 경우  
 대부분의 경우 데이터 영역을 디자인할 때 보고서 작성기 및 보고서 디자이너에서 그룹이 자동으로 만들어집니다. 테이블, 행렬 또는 목록의 경우 필드를 그룹화 창으로 끌어 오면 그룹이 만들어집니다. 차트의 경우 필드를 차트 끌어 놓기 영역으로 끌어 오면 그룹이 만들어집니다. 계기의 경우 계기 속성 대화 상자를 사용해야 합니다. 테이블, 행렬 또는 목록의 경우 그룹을 수동으로 만들 수도 있습니다. 자세한 내용은 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)를 참조하세요. 보고서를 만들 때 그룹을 추가하는 방법의 예는 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md) 또는 [기본 테이블 보고서 만들기&#40;SSRS 자습서&#41;](../../reporting-services/create-a-basic-table-report-ssrs-tutorial.md)를 참조하세요.  
  
## <a name="how-can-i-modify-a-group"></a>그룹 수정 방법  
 그룹을 만든 후에는 필터/정렬 식, 페이지 나누기 및 범위 관련 데이터를 보관할 그룹 변수와 같은 데이터 영역 관련 속성을 설정할 수 있습니다. 자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)를 참조하세요.  
  
 기존 그룹을 수정하려면 해당하는 그룹 속성 대화 상자를 엽니다. 여기에서 그룹의 이름을 변경할 수 있습니다. 또한 단일 필드, 여러 필드 또는 런타임에 값이 정해지는 보고서 매개 변수를 기반으로 그룹 식을 지정할 수도 있습니다. 인구 통계 정보 데이터에 대한 나이 범위를 지정하는 식 집합과 같은 식 집합을 기반으로 그룹을 지정할 수도 있습니다. 자세한 내용은 [그룹 식 예&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/group-expression-examples-report-builder-and-ssrs.md)를 참조하세요.  
  
> [!NOTE]  
>  그룹 이름을 변경하는 경우 그룹의 이전 이름을 참조하는 모든 그룹 식을 수동으로 업데이트해야 합니다.  
  
## <a name="how-are-groups-organized"></a>그룹 구성 방법  
 그룹의 구성을 이해하면 동일한 그룹 식을 지정하여 같은 데이터에 대한 다양한 뷰를 표시하는 데이터 영역을 디자인하는 데 도움이 됩니다.  
  
 그룹은 각 데이터 영역에 대한 하나 이상 계층의 멤버로 내부적으로 구성됩니다. 그룹 계층에는 중첩된 부모/자식 그룹이 포함되어 있으며 인접 그룹을 포함할 수 있습니다.  
  
 부모/자식 그룹을 트리 구조로 생각하는 경우 각 그룹 계층은 트리 구조의 포리스트입니다. 테이블릭스 데이터 영역에는 행 그룹 계층과 열 그룹 계층이 포함됩니다. 행 그룹 멤버와 연결된 데이터는 페이지에서 가로 방향으로 확장되며 열 그룹 멤버와 연결된 데이터는 페이지에서 세로 방향으로 확장됩니다. 그룹화 창에는 디자인 화면에서 현재 선택한 테이블릭스 데이터 영역에 대한 행 그룹과 열 그룹 멤버가 표시됩니다. 자세한 내용은 [그룹화 창&#40;보고서 작성기#41;](../../reporting-services/report-design/grouping-pane-report-builder.md)을 참조하세요.  
  
 차트 데이터 영역에는 범주 그룹 계층과 계열 그룹 계층이 포함됩니다. 범주 그룹 멤버는 범주 축에 표시되고 계열 그룹 멤버는 계열 축에 표시됩니다.  
  
 일반적으로 계기 데이터 영역에는 필요하지 않으나 그룹을 통해 데이터를 그룹화하여 계기에서 집계하는 방법을 지정할 수 있습니다.  
  
## <a name="what-types-of-groups-are-available-per-data-region"></a>데이터 영역별로 사용 가능한 그룹 유형  
 표로 확장되는 데이터 영역은 요약 데이터를 시각적으로 표시하는 데이터 영역과는 다른 그룹을 지원합니다. 따라서 테이블릭스 데이터 영역 및 테이블릭스 데이터 영역 기반의 테이블, 목록 및 행렬은 차트 또는 계기보다 다양한 그룹을 지원합니다. 다음 섹션에서는 각 데이터 영역 유형에서 그룹화의 유형 및 용도에 대해 설명합니다.  
  
> [!NOTE]  
>  그룹은 다양한 데이터 영역에서 다양한 이름을 가지지만 그룹을 만들고 사용하는 방법의 원리는 같습니다. 데이터 영역에 대한 그룹을 만드는 경우 해당 데이터 영역에 연결된 데이터 집합의 정보 데이터를 구성하는 방법을 지정합니다. 각 데이터 영역은 그룹화된 데이터를 표시하기 위한 그룹 구조를 지원합니다.  
  
### <a name="groups-in-a-tablix-data-region-details-row-and-column-groups"></a>테이블릭스 데이터 영역의 그룹: 세부 정보, 행 및 열 그룹  
 이 항목에서 설명한 것처럼 테이블릭스 데이터 영역을 사용하면 데이터를 행 또는 열 단위 그룹으로 구성할 수 있습니다. 그러나 테이블릭스 데이터 영역에는 행 및 열 그룹 이외에도 다양한 그룹이 제공됩니다. 테이블릭스 데이터 영역에는 다음과 같은 유형의 그룹이 있을 수 있습니다.  
  
-   **세부 정보 그룹** 세부 정보 그룹은 보고서 작성기 또는 보고서 디자이너가 데이터 집합 및 데이터 영역 필터를 적용한 후 보고서 데이터 집합의 모든 데이터로 구성됩니다. 따라서 세부 정보 그룹은 그룹 식이 없는 유일한 그룹입니다.  
  
     기본적으로 세부 정보 그룹은 쿼리 디자이너에서 데이터 집합 쿼리를 실행할 때 표시할 데이터를 지정합니다. 예를 들어 판매 주문 테이블의 모든 열을 검색하는 쿼리를 사용하는 경우 이 세부 정보 그룹의 데이터는 테이블의 모든 열에 대한 각 행의 모든 값을 포함합니다. 이 세부 정보 그룹의 데이터는 이전에 만들었던 모든 계산된 데이터 집합 필드에 대한 값도 포함합니다.  
  
    > [!NOTE]  
    >  세부 정보 그룹의 데이터는 데이터 원본에서 계산되고 쿼리에서 검색되는 집계인 서버 집계도 포함할 수 있습니다. 기본적으로 보고서에서 Aggregate 함수를 사용하는 식을 포함하지 않는 경우 보고서 작성기 및 보고서 디자이너는 서버 집계를 정보 데이터로 처리합니다. 자세한 내용은 [집계](../../reporting-services/report-design/report-builder-functions-aggregate-function.md)를 참조하십시오.  
  
     기본적으로 보고서에 테이블이나 목록을 추가할 때 보고서 작성기 및 보고서 디자이너는 세부 정보 그룹을 자동으로 만들고 세부 데이터에 표시할 행을 추가합니다. 이 행의 셀에 데이터 집합 필드를 추가할 때 [Sales]와 같은 필드에 대한 단순 식이 기본적으로 표시됩니다. 데이터 영역을 확인할 때는 결과 집합의 각 값에 대해 정보 행이 한 번씩 반복됩니다.  
  
-   **행 그룹 및 열 그룹** 데이터는 행 또는 열 단위 그룹으로 구성할 수 있습니다. 행 그룹은 페이지에서 세로로 확장됩니다. 열 그룹은 페이지에서 가로로 확장됩니다. 그룹은 중첩될 수 있습니다. 예를 들면 [Year]로 그룹화한 다음 다시 [Quarter]로, 그리고 [Month]로 그룹화할 수 있습니다. 또한 그룹은 인접할 수도 있습니다. 예를 들어 [Territory]를 기준으로 그룹화하고 이와 별개로 [ProductCategory]를 기준으로 그룹화할 수도 있습니다.  
  
     데이터 영역에 대한 그룹을 만들 때 보고서 작성기 및 보고서 디자이너는 데이터 영역에 행 또는 열을 자동으로 추가하고 이러한 행 또는 열을 사용하여 그룹 데이터를 표시합니다.  
  
-   **재귀 계층 구조 그룹** 재귀 계층 구조 그룹은 여러 계층 수준을 포함하는 단일 보고서 데이터 집합으로부터 데이터를 구성합니다. 예를 들어 재귀 계층 구조 그룹은 [Employee]에 보고하는 [Employee]와 같은 조직 계층을 표시할 수 있습니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 이러한 종류의 보고서 데이터에 대한 그룹을 만들 수 있는 그룹 속성과 기본 제공 함수를 제공합니다. 자세한 내용은 [재귀 계층 구조 그룹 생성&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)을 참조하세요.  
  
 다음 목록에는 각 데이터 영역에 대한 그룹의 작업 방법이 요약되어 있습니다.  
  
-   **테이블** 중첩 행 그룹, 인접 행 그룹 및 재귀 계층 구조 행 그룹(예: 조직도)을 정의합니다. 기본적으로 테이블에는 세부 정보 그룹이 포함되어 있습니다. 데이터 집합 필드를 선택한 테이블의 그룹화 창으로 끌어 그룹을 추가합니다.  
  
-   **행렬** 중첩 행/열 그룹 및 인접 행/열 그룹을 정의합니다. 데이터 집합 필드를 선택한 행렬의 그룹화 창으로 끌어 그룹을 추가합니다.  
  
-   **목록** 기본적으로 세부 정보 그룹을 지원합니다. 일반적으로는 한 가지 수준의 그룹화를 지원하는 데 사용됩니다. 데이터 집합 필드를 선택한 목록의 그룹화 창으로 끌어 그룹을 추가합니다.  
  
 그룹을 추가한 후에는 데이터 영역의 행 및 열 핸들이 그룹 멤버 자격에 따라 변경됩니다. 그룹을 삭제한 후에는 그룹 정의만 삭제하거나 그룹과 그룹에 연결된 모든 행 및 열을 삭제할 수 있습니다. 자세한 내용은 [테이블릭스 데이터 영역 셀, 행 및 열&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)을 참조하세요.  
  
 정보 또는 그룹 데이터의 계산에 표시하거나 사용할 데이터를 제한하려면 그룹에서 필터를 설정합니다. 자세한 내용은 [데이터 집합 필터, 데이터 영역 필터 및 그룹 필터 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-dataset-filters-data-region-filters-and-group-filters.md)를 참조하세요.  
  
 기본적으로 그룹을 만들 때 그룹의 정렬 식은 그룹 식과 같은 식입니다. 정렬 순서를 변경하려면 정렬 식을 변경합니다. 자세한 내용은 [데이터 필터링, 그룹화 및 정렬&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)를 참조하세요.  
  
#### <a name="understanding-group-membership-for-tablix-cells"></a>테이블릭스 셀에 대한 그룹 멤버 자격 이해  
 테이블릭스 데이터 영역의 행 또는 열의 셀은 여러 행 및 열 그룹에 속할 수 있습니다. 집계 함수(예: `=Sum(Fields!FieldName.Value`)를 사용하는 셀의 입력란에서 식을 정의할 때 셀에 대한 기본 그룹 범위는 셀이 속한 가장 안쪽에 있는 자식 그룹입니다. 셀이 행 및 열 그룹 모두에 속할 때 기본 그룹 범위는 가장 안쪽에 있는 행 및 열 그룹입니다. 다른 데이터 집합에 대한 그룹으로 범위가 한정된 집계 부분합을 계산하는 식을 작성할 수도 있습니다. 예를 들어 데이터 영역의 열 그룹 또는 모든 데이터에 대한 그룹의 백분율을 계산할 수 있습니다(예: `=Sum(Fields!FieldName.Value)/Sum(Fields!FieldName.Value,"ColumnGroup")`). 자세한 내용은 [테이블릭스 데이터 영역&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tablix-data-region-report-builder-and-ssrs.md) 및 [합계, 집계 및 기본 제공 컬렉션의 식 범위&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/expression-scope-for-totals-aggregates-and-built-in-collections.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 영역에서 그룹 추가 또는 삭제&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)   
 [그룹 또는 테이블릭스 데이터 영역에 합계 추가&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md)   
 [데이터 영역의 데이터 정렬&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md)   
 [드릴다운 동작&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/drilldown-action-report-builder-and-ssrs.md)   
 [테이블, 행렬 및 목록&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
