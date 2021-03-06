---
title: 캐시 새로 고침 옵션 (보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: e1fb1f7f249d8252873eb7ecc879aac05fb496b4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48081553"
---
# <a name="cache-refresh-options-report-manager"></a>캐시 새로 고침 옵션(보고서 관리자)
  캐시 새로 고침 옵션 페이지를 사용하여 보고서 또는 공유 데이터 집합의 임시 데이터 복사본과 함께 캐시를 사전 로드하는 일정을 계획할 수 있습니다. 새로 고침 계획에는 일정 및 매개 변수 값을 지정하거나 재정의하는 옵션이 포함됩니다. 공유 데이터 집합의 경우 읽기 전용으로 표시된 매개 변수의 값은 재정의할 수 없습니다. 새로 고침 옵션 페이지에서는 새로 고침 계획을 여러 개 만들어 사용할 수 있습니다.  
  
 캐시 새로 고침 계획의 관련 보고서 및 공유 데이터 집합을 추가, 삭제, 변경 및 볼 수 있는 기본 역할 할당은 내용 관리자, 내 보고서 및 게시자입니다.  
  
> [!NOTE]  
>  이 기능은 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]버전에서는 사용할 수 없습니다. 버전에서 지원 되는 기능 목록은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 참조 하세요 [SQL Server 2014 버전에서 지 원하는 기능](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)합니다.  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a>보고서 또는 공유 데이터 집합에 대한 캐시 새로 고침 계획 속성 페이지를 열려면  
  
1.  보고서 관리자를 열고 캐시 새로 고침 속성을 구성할 보고서나 공유 데이터 집합을 찾습니다.  
  
2.  보고서 또는 공유 데이터 집합 위로 마우스를 이동한 후 드롭다운 화살표를 클릭합니다.  
  
3.  드롭다운 목록에서 **관리**를 클릭합니다. **일반** 속성 페이지가 열립니다.  
  
4.  **캐시 새로 고침 계획** 탭을 클릭합니다.  
  
5.  캐시 계획을 새로 만들려면 **새 캐시 새로 고침 계획**을 클릭합니다.  
  
    > [!NOTE]  
    >  SQL Server 에이전트 서비스를 사용하도록 설정하고 시작하여 캐시 새로 고침 계획을 만들어야 합니다.  
  
6.  캐시 계획 복사본을 만들어 사용자 지정하려면 **기존 계획에서 새로 만들기**를 클릭합니다.  
  
## <a name="cache-refresh-options"></a>캐시 새로 고침 옵션  
 **Delete**  
 선택한 새로 고침 계획을 모두 삭제합니다.  
  
 **기존 계획에서 새로 만들기**  
 이 옵션은 캐시 새로 고침 계획을 하나 선택한 경우에만 설정됩니다. 이 옵션은 원래 계획에서 복사하여 새로운 새로 고침 옵션을 만듭니다. 캐시 새로 고침 계획 페이지의 정보가 선택한 계획의 정보로 채워져서 열립니다. 그런 다음 새로 고침 계획 옵션을 수정하고 새로운 설명과 함께 계획을 저장할 수 있습니다.  
  
 **새 캐시 새로 고침 계획**  
 현재 캐시 새로 고침 옵션에서 사용할 새로 고침 계획을 새로 만들려면 클릭합니다.  
  
 **편집**  
 현재 새로 고침 계획을 편집하려면 이 옵션을 선택합니다.  
  
## <a name="cache-refresh-plan-options"></a>캐시 새로 고침 계획 옵션  
 **설명**  
 캐시 새로 고침 계획에 대한 설명을 지정합니다.  
  
 **항목별 일정**  
 이 항목 전용의 일정을 만들려면 이 옵션을 선택합니다.  
  
 **구성**  
 빈도 정보를 지정하는 데 사용되는 일정 페이지를 열려면 클릭합니다.  
  
 자세한 내용은 [새 일정: 일정 페이지 편집 &#40;보고서 관리자&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md)합니다.  
  
 **공유 일정**  
 기존 일정을 선택하려면 이 옵션을 선택합니다.  
  
 자세한 내용은 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)합니다.  
  
 **@\<** *매개 변수* **>**  
 매개 변수 값의 한 조합을 지정합니다. 이 섹션은 현재 데이터 집합이나 보고서에 매개 변수가 있을 경우에만 나타납니다.  
  
 다음 섹션의 [매개 변수 지정](#Parameters) 을 참조하십시오.  
  
 **기본값 사용**  
 이 매개 변수의 미리 정의된 기본값을 사용하려면 이 옵션을 선택합니다.  
  
##  <a name="Parameters"></a> 매개 변수 지정  
 캐시 새로 고침 계획을 만들려면 각 보고서나 공유 데이터 집합 매개 변수에 값이 있어야 합니다. 보고서나 공유 데이터 집합 항목의 정의에 기본값이 없으면 값을 지정해야 합니다. 기본값이 있으면 여기서 기본값을 제공할 필요가 없습니다. 값을 제공하면 제공한 값이 기본값을 재정의합니다.  
  
 여러 개의 매개 변수 값 조합을 지정하려면 각 조합에 대해 별도의 캐시 새로 고침 계획을 만듭니다.  
  
 보고서나 공유 데이터 집합의 매개 변수에 대해 수행한 추가, 변경, 삭제 내용을 캐시 새로 고침 계획에 적용할 수 있습니다. 보고서에 대해 기본값을 포함하는 매개 변수를 추가하거나, 매개 변수를 제거하거나, 공유 데이터 집합 매개 변수의 읽기 전용 옵션 또는 데이터 형식을 변경할 경우 이러한 변경 내용은 다음에 캐시 새로 고침 계획이 처리될 때 적용됩니다.  
  
### <a name="shared-dataset-parameters"></a>공유 데이터 집합 매개 변수  
 공유 데이터 집합의 경우 다음 정보가 공유 데이터 집합 정의에서 파생됩니다.  
  
-   **이름** 쿼리 매개 변수의 이름을 지정합니다.  
  
-   **유형** 쿼리 매개 변수의 데이터 형식을 지정합니다. 이 데이터 형식은 데이터 공급자가 데이터 집합 쿼리를 처리할 때까지 알 수 없기 때문에 데이터 형식 유효성 검사는 공유 데이터 집합이 처리될 때까지 수행되지 않습니다.  
  
-   **Null 허용** NULL을 유효한 값으로 간주할지 여부를 지정합니다.  
  
-   **ReadOnly** 공유 데이터 집합 정의에서 이 매개 변수를 읽기 전용으로 표시할지 여부를 지정합니다. 읽기 전용 매개 변수는 캐시 새로 고침 옵션의 매개 변수 목록에 나타나지 않으며 공유 데이터 집합 정의에 기본값이 지정되어 있어야 합니다.  
  
-   **DefaultValues** 공유 데이터 집합 정의에 지정된 기본값입니다. 쿼리 매개 변수는 다중값을 가질 수 있습니다. 기본값을 재정의하려면 입력란 프롬프트 영역에 새 값을 입력합니다.  
  
 공유 데이터 집합 정의에서 매개 변수에 대해 **쿼리에서 생략** 옵션을 지정할 경우 기본값을 제공할 필요가 없습니다. 이 플래그는 해당 데이터 집합 매개 변수가 쿼리에 사용되지 않음을 나타냅니다. 예를 들어 이 매개 변수는 데이터 집합 필터에만 사용되는 보고서 매개 변수이기 때문에 공유 데이터 집합 정의에 나타납니다.  
  
 데이터 집합 매개 변수 옵션을 보거나 변경하려면 공유 데이터 집합 정의를 편집해야 합니다. 자세한 내용은 [공유 데이터 집합 관리](report-data/manage-shared-datasets.md)합니다.  
  
### <a name="report-parameters"></a>보고서 매개 변수  
 보고서의 경우 캐시 새로 고침 계획을 만들려면 각 매개 변수 값이 유효해야 합니다. 각 보고서 매개 변수에 대해 기본값을 입력하거나 선택해야 합니다. 사용자가 설정한 값은 보고서 서버에서 보고서 매개 변수에 대해 정의된 기본값을 재정의합니다.  
  
 매개 변수는 보고서 서버의 매개 변수 속성에 지정된 요구 사항을 따라야 합니다. 예를 들어 속성 AllowBlank 보고서 매개 변수의 false 인 경우 빈 문자열 값이 아닙니다 유효 합니다.  
  
 보고서 매개 변수 옵션을 보거나 변경하려면 보고서의 보고서 매개 변수를 편집하거나 보고서 서버에서 개별적으로 편집해야 합니다. 자세한 내용은 [보고서 매개 변수 개념 &#40;보고서 작성기 및 SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md)합니다.  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a>캐시 새로 고침 계획이 비활성화되는 조건  
 다음 조건에서는 공유 데이터 집합 또는 보고서 캐시 새로 고침 계획이 비활성화될 수 있습니다.  
  
-   공유 데이터 집합 캐시 또는 보고서 캐시 옵션이 사용되지 않도록 설정될 경우.  
  
-   필요한 매개 변수 값이 정의되지 않거나 유효하지 않거나 없을 경우. 보고서를 처리하려면 보고서의 모든 쿼리가 유효해야 합니다. 포함된 포고서가 있는 보고서의 경우 하위 보고서의 데이터 집합을 포함하여 모든 데이터 집합 쿼리가 먼저 처리됩니다. 데이터 집합을 처리할 수 없을 경우 보고서를 실행할 수 없습니다.  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a>캐시 새로 고침 계획이 다시 활성화되는 조건  
 계획이 비활성화된 후 다음 중 하나를 수행하여 캐시 새로 고침 계획의 평가를 트리거합니다.  
  
-   계획의 옵션을 변경합니다.  
  
-   새로 고침 계획과 연결된 공유 데이터 집합이나 보고서에 대해 캐싱을 사용하도록 설정합니다.  
  
-   새로 고침 계획과 연결된 데이터 집합 쿼리 매개 변수의 읽기 전용 옵션을 선택하거나 선택을 취소한 다음 새 정의를 보고서 서버에 저장합니다.  
  
## <a name="see-also"></a>관련 항목  
 [항목 수준의 태스크](security/tasks-and-permissions-item-level-tasks.md)   
 [보고서 관리자 &#40;SSRS 기본 모드&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md)   
 [보고서 관리자 F1 도움말](../../2014/reporting-services/report-manager-f1-help.md)   
 [보고서 캐시&#40;SSRS&#41;](report-server/caching-reports-ssrs.md)   
 [공유 데이터 집합 관리](report-data/manage-shared-datasets.md)  
  
  
