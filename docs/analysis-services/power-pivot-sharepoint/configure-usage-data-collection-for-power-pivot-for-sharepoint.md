---
title: 사용 현황 데이터 수집 구성 (SharePoint 용 Power Pivot | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bafa3d8b45dc2ad59314218f34959120b50e6bfe
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34026880"
---
# <a name="configure-usage-data-collection-for-power-pivot-for-sharepoint"></a>사용 현황 데이터 수집 구성(SharePoint용 파워 피벗)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  사용 데이터 컬렉션은 팜 수준의 SharePoint 기능입니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 은 이 시스템을 사용하고 확장하여 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 및 서비스 사용 상태를 보여 주는 보고서를 제공합니다. SharePoint를 구성한 방법에 따라 팜에 대해 사용 데이터 컬렉션이 해제될 수 있습니다. 팜 관리자는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에 표시되는 사용 데이터를 만들기 위해 사용 현황 로깅을 설정해야 합니다.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드의 사용 현황 데이터에 대한 자세한 내용은 [파워 피벗 관리 대시보드 및 사용 현황 데이터](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)를 참조하세요.  
  
 **항목 내용**  
  
 [사용 현황 데이터 수집 활성화 및 데이터 컬렉션을 트리거하는 이벤트 선택](#events)  
  
 [로그 파일 위치 설정](#configdb)  
  
 [사용 현황 데이터 수집에 사용되는 타이머 작업 구성](#jobs)  
  
 [사용 데이터 기록 저장 기간 제한](#confighist)  
  
 [보고에 대한 빠른, 보통 및 느린 쿼리 응답 범주 정의](#qrh)  
  
 [쿼리 통계가 사용 데이터 컬렉션 시스템에 보고되는 빈도 지정](#ttr)  
  
 [Power Pivot 서비스 응용 프로그램 페이지를 열어 구성 설정 액세스](#openconfig)  
  
 [Power Pivot 사용 데이터 컬렉션에 대한 기본 구성](#defaultconfig)  
  
> [!IMPORTANT]  
>  사용 데이터를 통해 사용자가 데이터와 리소스에 액세스하는 방법을 파악할 수 있으나 사용 데이터가 서버 작업 및 사용자 액세스에 대한 안정적이고 일관된 데이터를 보장하지는 않습니다. 예를 들어 서버를 다시 시작하는 경우 이벤트 사용 데이터가 손실되며 복구할 수 없게 됩니다. 마찬가지로 임시 로그 파일이 최대 크기에 도달하면 파일이 지워질 때까지 새 데이터가 추가되지 않습니다. 감사 기능이 필요한 경우 팜에 대한 감사 하위 시스템을 빌드하기 위해 SharePoint가 제공하는 워크플로 및 콘텐츠 형식 기능의 사용을 고려하세요. 자세한 내용은 웹에서 제품 및 커뮤니티 설명서를 찾아보세요.  
  
##  <a name="events"></a> 사용 현황 데이터 수집 활성화 및 데이터 컬렉션을 트리거하는 이벤트 선택  
 SharePoint 중앙 관리에서 사용 데이터 컬렉션을 구성합니다.  
  
1.  중앙 관리에서 **모니터링**을 클릭합니다.  
  
2.   **보고**섹션에서 **Usage and Health Data Collection 구성**을 클릭합니다.  
  
3.  **사용 현황 데이터 수집 사용**을 선택합니다.  
  
4.  **기록할 이벤트** 섹션에서 확인란을 선택하거나 취소하여 다음 Analysis Services 이벤트를 설정하거나 해제합니다.  
  
    |이벤트|Description|  
    |-----------|-----------------|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Connections**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 연결 이벤트는 사용자를 위해 설정된 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서버 연결을 모니터링하는 데 사용됩니다.|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Load Data Usage**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 로드 사용은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터를 서버 메모리로 로드하는 요청을 모니터링하는 데 사용됩니다. 콘텐츠 데이터베이스나 캐시에서 로드되는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 파일에 대해 로드 이벤트가 생성됩니다.|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Unload Data Usage**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 언로드 사용은 장기간 사용하지 않는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 원본을 언로드하기 위한 요청을 모니터링하는 데 사용됩니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 원본을 디스크에 캐시하면 언로드 이벤트로 보고됩니다.|  
    |**[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] Query Usage**|[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 쿼리 사용은 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 인스턴스에 로드되어 있는 데이터에 대한 쿼리 처리 시간을 모니터링하는 데 사용됩니다.|  
  
    > [!NOTE]  
    >  서버 상태 및 데이터 새로 고침 작업에서도 사용 데이터를 생성하지만 이러한 프로세스와 연관된 이벤트가 없습니다.  
  
5.  로그 파일 위치를 업데이트할 수도 있습니다. 자세한 내용은 다음 섹션을 참조하세요.  
  
6.  **확인** 을 클릭하여 변경 내용을 저장합니다.  
  
7.  선택적으로 모든 메시지를 기록할 것인지 또는 오류만 기록할 것인지를 지정할 수 있습니다. 이벤트 메시지를 제한하는 방법은 [SharePoint 로그 파일과 진단 로깅 구성 및 보기&#40;SharePoint용 파워 피벗&#41;](../../analysis-services/power-pivot-sharepoint/configure-and-view-sharepoint-and-diagnostic-logging.md)를 참조하세요.  
  
##  <a name="configdb"></a> 로그 파일 위치 설정  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 사용 현황 데이터는 처음에 로컬 서버의 사용 현황 로그 파일에 저장된 다음 정기적으로 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램 데이터베이스로 이동됩니다. 로그 파일 위치는 중앙 관리에 설정됩니다. 기본 위치는  
  
 `C:\Program Files\Common Files\Microsoft Shared\Web Server Extensions\15\logs`  
  
 이러한 속성을 보거나 변경하려면 **Usage and health data collection** 페이지를 사용합니다.  
  
1.  중앙 관리의 홈 페이지에서 **모니터링**을 클릭합니다.  
  
2.  모니터링 섹션에서 **사용 현황 및 상태 데이터 수집 구성**을 클릭합니다.  
  
3.  사용 현황 데이터 수집 설정에서 파일 위치, 이름 또는 최대 파일 크기를 보거나 수정합니다. 파일 크기를 너무 작게 지정하는 경우 파일 크기가 최대 한계에 도달하면 해당 내용이 중앙의 사용 데이터 컬렉션 데이터베이스로 이동될 때까지는 새 항목이 추가되지 않습니다.  
  
##  <a name="jobs"></a> 사용 현황 데이터 수집에 사용되는 타이머 작업 구성  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서버 상태 및 사용 현황 데이터는 사용 현황 데이터 컬렉션 시스템에서 두 개의 타이머 작업을 통해 다른 위치로 이동됩니다.  
  
-   "Microsoft SharePoint Foundation 사용 현황 데이터 가져오기" 타이머 작업이 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션 데이터베이스로 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 사용 데이터를 이동합니다.  
  
-   "[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드 처리 타이머 작업"이 기본 제공 관리 보고서의 데이터 원본인 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서로 데이터를 이동합니다.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에 나타나는 관리 보고서를 더 자주 새로 고쳐야 하는 경우에는 다음 단계를 따릅니다.  
  
1.  중앙 관리에서 **모니터링**을 클릭합니다.  
  
2.   **작업 정의 검토**를 클릭합니다. 를 클릭합니다. **타이머 작업** 섹션에서  
  
3.  **Microsoft SharePoint Foundation 사용 현황 데이터 가져오기**를 클릭합니다.  
  
4.  **지금 실행**을 클릭합니다. **지금 실행** 단추를 사용할 수 없는 경우 **사용** 을 클릭하고 **지금 실행**을 클릭합니다.  
  
5.  작업 정의 목록에서 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 관리 대시보드 처리 타이머 작업**을 클릭합니다.  
  
6.  **지금 실행**을 클릭합니다.  
  
7.  보고서에서 새로 고침 데이터를 봅니다. 자세한 내용은 [Power Pivot Management Dashboard and Usage Data](../../analysis-services/power-pivot-sharepoint/power-pivot-management-dashboard-and-usage-data.md)을(를) 참조하세요.  
  
##  <a name="confighist"></a> 사용 데이터 기록 저장 기간 제한  
 사용 데이터 기록은 이벤트(연결, 로드, 언로드 및 요청 시 쿼리 처리) 및 데이터 새로 고침(예약된 데이터 처리)에 대해 저장됩니다. SharePoint 사용 데이터 컬렉션 시스템을 통해 사용 데이터가 수집되지만 보고 데이터는 장기적 저장을 위해 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 애플리케이션 데이터베이스 및 보고 데이터베이스로 이동됩니다. 사용 데이터 기록 설정은 사용 데이터가 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 애플리케이션 데이터베이스에 보존되는 기간을 제어합니다. 같은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션 데이터베이스에 저장된 모든 형식의 사용 데이터에 같은 한계가 동일하게 적용됩니다.  
  
1.  [Power Pivot 서비스 응용 프로그램 페이지를 엽니다](#openconfig).  
  
2.  **사용 데이터 컬렉션** 섹션의 **사용 데이터 기록**에 각 통합 문서에 대한 데이터 새로 고침 작업 레코드를 보관할 일 수를 입력합니다.  
  
    -   기본값은 365일입니다.  
  
    -   0은 사용 데이터가 무한대로 보관되는 제한되지 않은 저장소를 지정합니다.  
  
    -   또는 1과 5000 사이의 범위를 지정할 수도 있습니다.  
  
     보존 기간을 작은 일 수로 줄이면 새 제한을 초과하는 데이터가 모두 삭제됩니다. 예를 들어 값을 365에서 30으로 변경하면 30일 전에 발생한 모든 기록 정보에 대해 사용 데이터가 삭제됩니다. 최근 30일 동안의 데이터만 보존됩니다.  
  
     다음 이벤트가 발생하면 데이터가 실제로 삭제됩니다. 시스템에서 이벤트를 처리할 때만 사용 데이터 기록에 대한 제한이 확인됩니다.  
  
3.  **확인**을 클릭합니다.  
  
 사용 현황 데이터를 수집하고 저장하는 방법은 [파워 피벗 사용 현황 데이터 수집](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)을 참조하세요.  
  
##  <a name="qrh"></a> 보고에 대한 빠른, 보통 및 느린 쿼리 응답 범주 정의  
 쿼리 처리 성능은 완료하는 데 걸리는 시간을 기준으로 요청-응답 주기를 정의하는 미리 정의된 범주에 대해 측정됩니다. 미리 정의된 범주에는 간단한, 빠른, 예상, 장기 실행 및 초과가 포함됩니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서버에 대한 모든 요청은 완료 시간을 기준으로 한 범주 중 하나에 해당됩니다.  
  
 쿼리 응답 정보는 작업 보고서에서 사용됩니다. 보고서 내에서 각 범주는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템의 성능 추세를 더 잘 나타내기 위해 다르게 사용됩니다. 예를 들면 간단한 요청을 제외하면 데이터에서 의미 없는 항목이 제거되고 나머지 범주를 사용하여 더욱 의미 있는 추세를 표시할 수 있으므로 간단한 요청이 완전히 제외됩니다. 반면 장기 실행 또는 초과 요청 통계가 보고서에서 눈에 잘 띄므로 관리자나 통합 문서 소유자가 즉시 수정 동작을 수행할 수 있습니다.  
  
 범주를 추가하거나 삭제할 수 없지만 한 범주를 중지하고 다음 범주를 시작하는 위치를 결정하는 상한과 하한을 정의할 수 있습니다. 조직에서 SLA(서비스 수준 계약)를 사용하여 허용되는 서버 가용성 및 성능 수준을 정의하는 경우 만든 SLA를 반영하도록 이러한 범주를 조정할 수 있습니다.  
  
1.  [Power Pivot 서비스 응용 프로그램 페이지를 엽니다](#openconfig).  
  
2.  **사용 현황 데이터 수집** 섹션의 **간단한 응답 상한값** 에 간단한 응답을 완료할 상한을 설정하는 값(밀리초)을 입력합니다. 이 범주에 속하는 요청에는 일반적으로 서버 ping, 세션 초기화 및 메타데이터 쿼리가 포함됩니다. 기본값은 500밀리초(또는 0.5초)입니다.  
  
3.  빠른 요청 상한에 빠른 응답을 완료할 상한을 설정하는 값(밀리초)을 입력합니다. 이 범주에 속하는 요청에는 매우 작은 데이터 집합이나 큰 데이터 집합의 메타데이터 서버에 대한 쿼리가 포함됩니다. 기본값은 1000밀리초(또는 1초)입니다.  
  
4.  **예상 응답 상한값**에 예상 또는 평균 시간대에서 응답을 완료할 상한을 설정하는 값(밀리초)을 입력합니다. 이 범주에 속하는 요청에는 뷰어로 데이터 로드가 포함됩니다. 기본값은 3000밀리초(또는 3초)입니다.  
  
5.  **긴 응답 상한값**에 장기 실행 응답을 완료할 상한을 설정하는 값(밀리초)을 입력합니다. 이 범주에 속하는 요청은 예상보다 길게 실행되지만 여전히 허용 가능한 범위 내에 속하는 요청입니다. 기본값은 10000밀리초(또는 10초)입니다.  
  
     이 한계를 초과하는 요청은 모두 *초과*로 분류됩니다. *초과*에 대해 구성할 수 있는 임계값은 없으며, 장기 요청 상한에 대해 지정한 상한에서 유추됩니다. 초과 범주에 속하는 요청은 정의한 SLA에서 허용한 시간보다 오래 실행됩니다.  
  
6.  **확인**을 클릭합니다.  
  
##  <a name="ttr"></a> 쿼리 통계가 사용 데이터 컬렉션 시스템에 보고되는 빈도 지정  
 보고 시간 간격은 쿼리 통계가 사용 데이터 컬렉션 시스템에 보고되는 빈도를 지정합니다. 쿼리 통계는 프로세스에 누적되고 정기적으로 단일 이벤트로 보고됩니다. 로그 파일에 자주 또는 덜 쓰도록 간격을 조정할 수 있습니다.  
  
1.  [Power Pivot 서비스 응용 프로그램 페이지를 엽니다](#openconfig).  
  
2.  **사용 현황 데이터 수집** 섹션의 **쿼리 보고 간격**에 서버에서 모든 범주(간단한, 빠른, 예상, 장기 실행 및 초과)에 대한 쿼리 통계를 단일 이벤트로 사용 데이터 수집 시스템에 보고하는 시간(초)을 입력합니다.  
  
    -   범위는 1부터 임의의 양의 정수입니다.  
  
    -   기본값은 300초(또는 5분)입니다. 다양한 애플리케이션과 서비스를 실행하는 동적 팜 환경에서는 이 값을 사용하는 것이 좋습니다.  
  
     이 값을 아주 큰 수로 늘리면 보고하기 전에 통계 데이터가 손실될 수 있습니다. 예를 들면 서비스 다시 시작으로 인해 통계 데이터가 손실될 수 있습니다. 반대로 기본 제공 작업 보고서에 충분한 데이터가 표시되지 않는 경우 보고 시간 이벤트가 자주 발생하도록 이 간격을 줄여봅니다.  
  
3.  **확인**을 클릭합니다.  
  
##  <a name="openconfig"></a> Power Pivot 서비스 응용 프로그램 페이지를 열어 구성 설정 액세스  
 서비스 애플리케이션 설정을 수정하려면 팜 또는 서비스 관리자여야 합니다. 팜에서 여러 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 정의한 경우 각 애플리케이션을 개별적으로 수정해야 합니다.  
  
1.  SharePoint 중앙 관리의 **애플리케이션 관리**에서 **서비스 애플리케이션 관리**를 클릭합니다.  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 찾습니다. 유형을 기준으로 서비스 애플리케이션을 식별할 수 있습니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램 유형은 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램**입니다.  
  
3.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램 이름을 클릭합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드가 열립니다.  
  
4.  **동작**에서 **서비스 응용 프로그램 설정 구성**을 클릭합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램 설정 페이지가 열립니다.  
  
##  <a name="defaultconfig"></a> Power Pivot 사용 데이터 컬렉션에 대한 기본 구성  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스에 대한 사용 데이터 컬렉션 작업을 기본 설정으로 활성화하여 Analysis Services 통합 기능을 지원하는 응용 프로그램에서 바로 사용할 수 있습니다. 기본 설정에는 사용 데이터 컬렉션을 트리거하는 이벤트, 사용 데이터 저장 기간 제한 및 쿼리 응답 시간 범주화를 위한 임계값이 포함됩니다.  
  
 다음 표에서는 사용 데이터 컬렉션 구성의 기본값을 보여 줍니다.  
  
|설정|기본값|형식|유효 범위|  
|-------------|-------------------|----------|-----------------|  
|**Analysis Services 사용 이벤트** (연결, 로드, 언로드, 요청)|\<enabled>|Boolean|이러한 값이 사용되거나 사용되지 않습니다.|  
|**Query Reporting interval**|300(초)|정수|1부터 임의의 양의 정수입니다. 기본값은 5분입니다.|  
|**Usage data history**|365(일)|정수|0은 제한이 없음을 지정하지만 기록 데이터를 만료할 상한을 설정하고 이 데이터가 자동으로 삭제되도록 할 수도 있습니다. 제한된 보존 기간에 유효한 값은 1 ~ 5000(일)입니다.|  
|간단한 응답 상한값|500(밀리초)|정수|간단한 요청-응답 교환을 정의하는 상한을 설정합니다. 0밀리초에서 500밀리초 사이에 완료되는 모든 요청은 간단한 요청으로, 보고에서 무시됩니다.|  
|빠른 응답 상한값|1000(밀리초)|정수|빠른 요청-응답 교환을 정의하는 상한을 설정합니다.|  
|예상 응답 상한값|3000(밀리초)|정수|예상 요청-응답 교환을 정의하는 상한을 설정합니다.|  
|긴 실행 응답 상한값|10000(밀리초)|정수|장기 실행 요청-응답 교환을 정의하는 상한을 설정합니다. 이 상한을 초과하는 모든 요청은 상한 임계값이 없는 초과 범주에 속합니다.|  
  
## <a name="see-also"></a>관련 항목:  
 [구성 설정 참조&#40;SharePoint용 파워 피벗&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)   
 [Power Pivot 사용 데이터 수집](../../analysis-services/power-pivot-sharepoint/power-pivot-usage-data-collection.md)  
  
  
