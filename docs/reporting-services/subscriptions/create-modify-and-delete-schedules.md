---
title: 일정 만들기, 수정 및 삭제 | Microsoft Docs
ms.date: 07/01/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: subscriptions
ms.topic: conceptual
helpviewer_keywords:
- report-specific schedules [Reporting Services]
- shared schedules [Reporting Services]
- modifying schedules
- removing schedules
- shared schedules [Reporting Services], creating
- shared schedules [Reporting Services], modifying
- schedules [Reporting Services], deleting
- deleting schedules
- schedules [Reporting Services], creating
- schedules [Reporting Services], modifying
- shared schedules [Reporting Services], deleting
ms.assetid: 05da5f3d-9222-43a9-893b-aa10f0f690f8
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 346b348f2df1ccb6cd6373dad130b10c71ea1bcb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679791"
---
# <a name="create-modify-and-delete-schedules"></a>일정 만들기, 수정 및 삭제
  이 항목에서는 [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] 공유 일정을 만들고 수정하고 삭제하는 방법을 알아봅니다.  기본 모드에 대한 공유 일정을 관리하려면 웹 포털의 일정 페이지나 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 공유 일정 폴더를 사용합니다. SharePoint 모드의 경우에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 서비스 애플리케이션을 위한 관리 페이지를 사용합니다.  
  
 다음 방법 중 하나를 사용하여 공유 일정이 현재 사용되고 있는지 확인합니다.  
  
-   **웹 포털:** 사이트 설정 페이지의 공유 일정 페이지에서 마지막 실행 날짜, 다음 실행 날짜 및 상태 필드의 값을 검토합니다. 일정이 만료되어 더 이상 실행되지 않으면 상태 필드에 만료 날짜가 나타납니다. 자세한 내용은 [Web portal (SSRS Native Mode)](../../reporting-services/web-portal-ssrs-native-mode.md)을 참조하세요.
  
-   **[!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)]:** 지정한 공유 일정의 보고서 페이지를 봅니다. 이 페이지에는 공유 일정을 사용하는 모든 보고서 및 공유 데이터 집합의 목록이 나열됩니다. 자세한 내용은 [SQL Server Management Studio의 Reporting Services ](../../reporting-services/tools/reporting-services-in-sql-server-management-studio-ssrs.md)를 참조하세요.
  
-  **:** 보고서 실행 로그 파일 또는 추적 로그에서 보고서가 일정에 지정된 시간에 실행되었는지 확인합니다. 자세한 내용은 [Reporting Services 로그 파일 및 소스](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)를 참조하세요.  
  
## <a name="when-you-delete-a-shared-schedule"></a>공유 일정을 삭제하는 경우  
공유 일정은 웹 포털의 일정 페이지나 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]의 공유 일정 폴더를 사용하여 수동으로 삭제해야 합니다. 사용 중인 공유 일정을 삭제하면 공유 일정에 대한 모든 참조가 보고서별 일정으로 바뀝니다.  
 
여러 보고서 및 구독에 사용되는 공유 일정을 삭제하면 보고서 서버는 공유 일정을 사용하던 각 보고서 및 구독에 대해 개별적인 일정을 만듭니다. 각 개별 일정에는 공유 일정에 지정되었던 날짜, 시간 및 되풀이 패턴이 포함됩니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 는 개별 일정을 중앙에서 관리하지 않습니다. 공유 일정을 삭제하면 개별 항목에 대해 일정 정보를 관리해야 합니다.  
  
**참고:**  공유 일정 사용 여부를 모를 경우에는 웹 포털 대신 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서 삭제하는 것이 좋습니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 에서는 보고서 관리자와 동일한 공유 일정 관리 기능을 제공하지만 일정을 사용하는 각 보고서의 이름을 표시한 추가 보고서 페이지를 제공합니다.  
   
 일정을 삭제하는 것과 만료시키는 것은 다릅니다. 만료 날짜를 사용하여 일정을 중지할 수 있지만 일정이 삭제되지는 않습니다. 일정은 여러 가지 기능을 자동화하는 데 사용되기 때문에 자동으로 삭제되지 않습니다. 만료된 일정은 보고서 서버 관리자에게 자동화된 처리가 갑자기 중지된 이유에 대한 근거를 제공합니다. 만료된 일정이 없으면 보고서 서버 관리자가 문제를 잘못 진단하거나 기능적인 과정 전체의 문제 해결을 위해 불필요한 시간을 보낼 수 있습니다.  
 
 ## <a name="when-you-delete-a-report-specific--schedule"></a>보고서별 일정을 삭제하는 경우  
보고서 일정과 구독별 일정은 보고서 또는 구독을 삭제하거나 다른 방법을 선택하여 보고서 또는 구독을 실행하는 경우 삭제됩니다. 예를 들어 **항상 최신 데이터로 이 보고서 실행** 을 선택하면 만든 보고서별 일정이 삭제되고 보고서가 보고서 실행 스냅숏으로 실행됩니다.  

만료된 보고서별 일정은 보고서에 연결된 상태로 남아 있습니다. 종료 날짜를 확인하면 일정이 만료되었는지 알 수 있습니다. 만료된 공유 일정은 공유 일정 목록에 남아 있습니다. 상태 필드는 일정이 만료되었는지 여부를 나타냅니다. 종료 날짜를 연장하여 일정을 복원할 수 있으며 더 이상 필요 없는 경우 일정 참조를 제거할 수 있습니다.  
  
## <a name="bkmk_native"></a> 공유 일정 만들기, 삭제 또는 수정(웹 포털)  
 일정을 만들고 수정할 때는 일정 실행 시기를 결정하는 빈도 옵션을 설정해야 합니다.  
  
 일정은 언제든지 만들거나 수정할 수 있습니다. 그러나 수정을 마치기 전에 일정이 실행되기 시작하면 이전 버전의 일정이 사용됩니다. 수정된 일정을 저장해야 변경 내용이 적용됩니다.  
  
 공유 일정을 수정하는 경우 변경하기 전에 일시 중지할 수 있습니다. 변경 내용은 일정을 다시 시작할 때 적용됩니다.  

1.  웹 포털의 도구 모음에서 **설정** ![ssrs_portal_settings_gear](../../reporting-services/subscriptions/media/ssrs-portal-settings-gear.png) 를 클릭합니다. **참고:** **사이트 설정** 을 사용할 수 없으면 사이트 설정에 액세스할 권한이 없는 것입니다.
2.  **사이트 설정**을 클릭합니다.  
3.  **일정**을 클릭합니다.  
4.  **새 일정**을 클릭합니다. 기존 일정을 수정하려면 일정 이름을 클릭합니다.  
5.  일정에 대한 설명이 포함된 이름을 입력합니다.  
6.  **시간**, **일**, **주**또는 **월**을 선택합니다. 한 번만 실행되는 일정을 만들려면 **한 번** 을 클릭합니다. 일정의 기준을 지정하면 다른 옵션이 추가로 표시됩니다.  
7.  일정을 시작할 날짜를 선택합니다(옵션). 기본값은 현재 날짜입니다. 현재 이후의 날짜를 선택하여 일정 시작 시간을 연기할 수 있습니다.  
8.  일정을 종료할 날짜를 선택합니다(선택 사항). 이 날짜에 일정 실행이 중지되지만 일정이 삭제되지는 않습니다.  
9. [!INCLUDE[clickOK](../../includes/clickok-md.md)] 

### <a name="to-delete-a-shared-schedule-web-portal"></a>공유 일정을 삭제하려면(웹 포털)  
  
1.  웹 포털의 전역 도구 모음에서 **사이트 설정**을 클릭합니다.     
2.  페이지의 **기타** 섹션에서 **공유 일정 관리**를 클릭합니다.  
3.  삭제할 일정 옆의 확인란을 선택한 다음 **삭제**를 클릭합니다.  
  
### <a name="create-delete-or-modify-a-shared-schedule-management-studio"></a>공유 일정 만들기, 삭제 또는 수정(Management Studio)  
 공유 일정에는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 서버에서 실행되는 게시된 여러 보고서 및 구독에 사용할 수 있는 일정 및 되풀이 정보가 포함됩니다. 동시에 실행되는 보고서와 구독이 여러 개 있을 경우 이러한 작업에 대한 공유 일정을 만들 수 있습니다. 이후에 되풀이 패턴 또는 종료 날짜를 변경하려는 경우 단일 위치에서 변경할 수 있습니다.  
  
 공유 일정은 관리하기가 더 쉬우므로 예약된 작업을 보다 유연하게 관리할 수 있습니다. 예를 들어 공유 일정을 일시 중지하고 재개할 수 있습니다. 또한 예약된 작업이 동시에 너무 많이 실행되는 경우에는 서로 다른 시간에 실행되는 공유 일정을 여러 개 만든 다음 처리 부하가 보고서 서버에서 균등하게 분포될 때까지 일정 정보를 조정할 수 있습니다.  
  
### <a name="to-create-or-modify-a-shared-schedule-management-studio"></a>공유 일정을 만들거나 수정하려면(Management Studio)  
  
1.  [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] 를 시작하고 보고서 서버 인스턴스에 연결합니다.  
2.  개체 탐색기에서 보고서 서버 노드를 확장합니다.  
3.  **공유 일정** 폴더를 마우스 오른쪽 단추로 클릭하고 **새 일정**을 클릭합니다. **새 공유 일정** 대화 상자의 일반 페이지가 표시됩니다.  
  
     기존 공유 일정을 수정하려면 공유 일정 폴더를 확장하고 수정할 일정을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
4.  일정에 대한 설명이 포함된 이름을 입력합니다.  
5.  일정을 시작할 날짜를 선택합니다(옵션). 기본값은 현재 날짜입니다.  
6.  일정을 종료할 날짜를 선택합니다(옵션). 이 날짜에 일정 실행이 중지되지만 일정이 삭제되지는 않습니다.  
7.  되풀이 일정을 구성하려면 **시간**, **일**, **주**또는 **월**을 선택합니다. 추가 옵션이 표시됩니다. 이러한 추가 일정을 사용하여 원하는 시간, 일, 주 또는 월을 기준으로 일정 빈도를 구성할 수 있습니다.  
  
     또는 일회 일정 즉, 되풀이되지 않는 일정을 지정하려면 **한 번**을 선택하고 **시작 시간**을 지정합니다.  
  
8.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##### <a name="to-delete-a-shared-schedule-management-studio"></a>공유 일정을 삭제하려면(Management Studio)  
  
1.  개체 탐색기에서 보고서 서버 노드를 확장합니다.  
2.  공유 일정이 보고서에서 현재 사용되지 않는 것을 확인하려면 공유 일정 폴더를 확장하고 일정을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.
3. **보고서** 탭을 클릭하여 현재 일정을 사용 중인 보고서 목록을 확인합니다.
 **취소**를 클릭합니다.
4.  공유 일정 폴더를 확장하고 삭제할 일정을 마우스 오른쪽 단추로 클릭한 다음 **삭제**를 클릭합니다. **카탈로그 항목 삭제** 대화 상자가 나타납니다.  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
 여러 보고서 및 구독에 사용되는 공유 일정을 삭제하면 보고서 서버는 공유 일정을 사용하던 각 보고서 및 구독에 대해 개별적인 일정을 만듭니다. 각 개별 일정에는 공유 일정에 지정되었던 날짜, 시간 및 되풀이 패턴이 포함됩니다.
 
##  <a name="bkmk_sharepoint"></a> 공유 일정 만들기 및 관리(SharePoint 모드)  
 SharePoint 사이트에서 공유 일정을 만들거나, 수정하거나, 삭제하려면 사이트 관리자여야 합니다.  
  
 설명이 포함된 이름으로 특정 일정을 식별할 수 있습니다. 이름이 지정되어 있지 않으면 되풀이 패턴이나 실행 날짜 및 시간과 같은 일정 정보를 기반으로 기본 이름이 생성됩니다.  
  
> [!NOTE]  
>  공유 일정을 만들려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 서비스가 필요합니다.  
  
### <a name="create-shared-schedules-sharepoint-mode"></a>공유 일정 만들기(SharePoint 모드)  
1.  **사이트 작업**을 클릭합니다.  
2.  **사이트 설정**을 클릭합니다.  
3.  Reporting Services 섹션에서 **공유 일정 관리**를 클릭합니다.  
4.  **일정 추가** 를 클릭하여 일정 속성 페이지를 엽니다.  
5.  일정에 대한 설명이 포함된 이름을 입력합니다. [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 보고서 작업에 사용되는 응용 프로그램 페이지에서 이 이름은 사이트 전반에서 일정 정의 페이지의 드롭다운 목록에 나타납니다. 읽기 어려운 긴 이름은 사용하지 말고 이름 시작 부분에 가장 중요한 정보를 포함하는 명명 규칙을 따르세요.  
6.  빈도를 선택합니다. 선택하는 빈도에 따라 해당 빈도를 지원하기 위해 페이지에 나타나는 일정 옵션이 변경될 수 있습니다. 예를 들어 **월**을 선택하면 각 월의 이름이 페이지에 나타납니다.  
7.  일정을 정의합니다. 일부 일정 조합은 단일 일정으로 지원되지 않습니다.  
8.  시작 날짜와 종료 날짜를 설정합니다.  
9. **확인**을 클릭합니다.  
  
### <a name="delete-shared-schedules-sharepoint-mode"></a>공유 일정 삭제(SharePoint 모드)  
 공유 일정이나 보고서별 일정 모두 수동으로 삭제해야 합니다. 사용 중인 공유 일정을 삭제하면 해당 일정에 대한 모든 참조가 지정되지 않은 사용자 지정 일정, 즉 날짜 또는 시간 정보가 없는 사용자 지정 일정으로 바뀝니다.  
  
1.  **사이트 작업**을 클릭합니다.  
2.  **사이트 설정**을 클릭합니다.  
3.  Reporting Services 섹션에서 **공유 일정 관리**를 클릭합니다.  
4.  일정을 선택하고 **삭제**를 클릭합니다.  
 
  
## <a name="see-also"></a>참고 항목  
 [Schedules](../../reporting-services/subscriptions/schedules.md)   
 [공유 일정 일시 중지 및 다시 시작](../../reporting-services/subscriptions/pause-and-resume-shared-schedules.md)   
 [보고서 캐시&#40;보고서 관리자&#41;](../../reporting-services/report-server/cache-a-report-report-manager.md)   
 [보고서 기록에 스냅숏 추가&#40;보고서 관리자&#41;](../../reporting-services/report-server/add-a-snapshot-to-report-history-report-manager.md)  
  
  
