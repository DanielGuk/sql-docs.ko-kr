---
title: 만들기 및 CA에서 파워 피벗 서비스 응용 프로그램 구성 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: e79087f98d5947706720b1dc63c000ae9d9e0ad5
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38982605"
---
# <a name="create-and-configure-power-pivot-service-application-in-ca"></a>만들기 및 CA에서 파워 피벗 서비스 응용 프로그램 구성
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스의 공유 서비스 인스턴스입니다. 각 서비스 애플리케이션은 고유한 애플리케이션 ID, 구성 설정, 속성 및 내부 데이터 저장소를 포함합니다.  
  
 이 항목에는 다음과 같은 섹션이 포함되어 있습니다.  
  
 [새 PowerPivot 서비스 응용 프로그램을 만들 것인지 여부 결정](#determine)  
  
 [PowerPivot 서비스 응용 프로그램 만들기](#CreateApp)  
  
 [PowerPivot 서비스 응용 프로그램 구성](#ConfigApp)  
  
 [웹 응용 프로그램에 PowerPivot 서비스 응용 프로그램 할당](#AssignGSA)  
  
 [서비스 응용 프로그램 속성 편집](#EditGSA)  
  
##  <a name="determine"></a> 새 PowerPivot 서비스 응용 프로그램을 만들 것인지 여부 결정  
 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 를 설치하려면 팜에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션이 하나 이상 있어야 합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 구성 도구를 사용하여 서버를 구성한 경우 서비스 응용 프로그램이 자동으로 만들어집니다. 그렇지 않은 경우에는 중앙 관리에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 수동으로 만들어야 합니다.  
  
 서비스 애플리케이션을 만들면 서비스를 사용할 수 있게 되며 서비스 애플리케이션 데이터베이스가 생성됩니다. 서비스 애플리케이션을 만들 때 선택한 옵션에 따라 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 연결이 기본 서비스 연결 그룹에 추가됩니다. 기본 서비스 연결 그룹을 구독하는 모든 SharePoint 웹 애플리케이션은 자동으로 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션에 즉시 액세스할 수 있게 됩니다.  
  
 여러 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만들 수 있습니다. 대부분의 배포 시나리오에서는 하나의 서비스 애플리케이션으로 충분하지만 비즈니스 요구 사항에 다음과 같은 내용이 포함되는 경우 추가 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만들 수 있습니다.  
  
-   각 애플리케이션에 대해 서로 다른 무인 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 새로 고침 계정을 사용하는 경우  
  
-   쿼리 응답 보고에 다른 제한 시간, 사용 기록 및 임계값을 사용하는 경우  
  
-   다른 사람에게 서비스 관리 권한을 위임하는 경우. 관리자에게는 자신이 관리하는 애플리케이션의 데이터 새로 고침 기록, 사용 데이터 및 기타 속성만 표시됩니다. SharePoint를 격리해야 하는 경우(예: 회사가 다른 고객에게 속한 SharePoint 웹 애플리케이션에 대한 데이터 격리를 보장해야 하는 호스팅 서비스를 제공하는 경우) 별도의 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만들면 각 서비스 관리자에게 자신이 관리하는 애플리케이션의 구성 설정 및 속성만 표시되도록 함으로써 격리 요구 사항을 충족할 수 있습니다.  
  
 추가 서비스 애플리케이션을 작성하면 서비스 연결 관리에 대한 새로운 요구 사항이 적용됩니다. 즉, 추가로 작성하는 각 서비스 애플리케이션에 대해 사용자 지정 서비스 연결 목록을 만들어 사용해야 합니다.  
  
 추가 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만들 특별한 이유가 없는 경우 팜의 모든 웹 애플리케이션에 대해 단일 서비스 애플리케이션을 사용해야 합니다.  
  
##  <a name="CreateApp"></a> PowerPivot 서비스 응용 프로그램 만들기  
  
1.  중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.  
  
2.  **서비스 응용 프로그램** 리본에서 **새로 만들기**를 클릭합니다.  
  
3.  **SQL Server [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램**을 선택합니다. 이 응용 프로그램이 목록에 표시되지 않으면 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 이 올바르게 설치되거나 구성되지 않은 것입니다.  
  
4.  **새 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램 만들기** 페이지에 응용 프로그램의 이름을 입력합니다. 기본값은 PowerPivotServiceApplication\<번호 >. 여러 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만드는 경우 설명이 포함된 이름을 사용하면 다른 관리자가 애플리케이션 사용 방식을 이해하는 데 도움이 됩니다.  
  
5.  애플리케이션 풀에서 애플리케이션에 대해 새 애플리케이션 풀을 만듭니다(권장). 애플리케이션 풀에 대한 관리 계정을 선택하거나 만듭니다. 도메인 사용자 계정을 지정하세요. 도메인 사용자 계정을 사용하면 SharePoint의 관리되는 계정 기능을 사용할 수 있으므로 암호 및 계정 정보를 한 곳에서 업데이트할 수 있습니다. 같은 ID로 실행할 추가 서비스 인스턴스를 포함하도록 배포를 확장할 계획인 경우에도 도메인 계정이 필요합니다.  
  
6.  **데이터베이스 서버**에서 기본값은 팜 구성 데이터베이스를 호스팅하는 SQL Server 데이터베이스 엔진 인스턴스입니다. 이 서버를 사용하거나 다른 SQL Server를 선택할 수 있습니다.  
  
7.  **데이터베이스 이름**, 기본값은 PowerPivotServiceApplication1_\<guid >. 각 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션에 대해 고유한 데이터베이스를 만들어야 합니다. 기본 데이터베이스 이름은 서비스 애플리케이션의 기본 이름에 해당합니다. 고유한 서비스 애플리케이션 이름을 입력한 경우 함께 관리할 수 있도록 데이터베이스 이름에 대해 비슷한 명명 규칙을 따릅니다.  
  
8.  **데이터베이스 인증**에서 기본값은 Windows  인증입니다. **SQL  인증**을 선택하는 경우 SharePoint  배포에서 이 인증 유형을 사용하는 최선의 구현 방법을 SharePoint  관리자 설명서에서 참조하십시오.  
  
9. 원하는 경우 **팜의 기본 프록시 그룹에 이 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션의 프록시를 추가합니다.** 확인란을 선택합니다. 확인란을 선택합니다. 이렇게 하면 기본 서비스 연결 그룹에 서비스 애플리케이션 연결이 추가됩니다.  
  
     첫 번째 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만드는 경우에는 이 확인란을 선택해야 합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드가 제대로 작동하려면 기본 연결 그룹에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램이 하나 있어야 합니다.  
  
     기본 연결 그룹에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션이 있는 경우에는 더 추가하지 마십시오. 같은 서비스 애플리케이션 유형의 여러 항목을 추가하는 구성은 지원되지 않으며 오류가 발생할 수 있습니다. 추가 서비스 애플리케이션을 만드는 경우에는 기본 연결 그룹 외부의 사용자 지정 목록에 추가하십시오.  
  
     서비스 연결에 대한 자세한 내용은 [중앙 관리에서 SharePoint 웹 애플리케이션에 파워 피벗 서비스 애플리케이션 연결](../../analysis-services/power-pivot-sharepoint/connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)을 참조하세요.  
  
10.  **확인.** 을 클릭합니다. 서비스가 다른 관리 서비스와 함께 팜의 서비스 애플리케이션 목록에 표시됩니다.  
  
##  <a name="ConfigApp"></a> PowerPivot 서비스 응용 프로그램 구성  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램은 기본 구성을 사용하여 만들어집니다. 대부분의 시나리오에서는 기본 설정을 사용하는 것이 좋습니다. 응답 시간이 느리거나 연결이 끊어진 경우 또는 특정 SharePoint 웹 애플리케이션에 대한 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 구성을 변경하는 경우에만 기본 설정을 변경합니다.  
  
1.  중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.  
  
     서비스 애플리케이션 목록에 방금 만들어 이름을 지정한 서비스 애플리케이션이 표시됩니다. 기본값은 **PowerPivotServiceApplication1**입니다.  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 클릭합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드가 열립니다.  
  
3.  대시보드 오른쪽 위 모퉁이에 있는 **동작** 목록에서 **서비스 애플리케이션 설정 구성**을 클릭합니다.  
  
4.  **데이터베이스 로드 제한 시간**에서 값을 늘리거나 줄여서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스가 데이터 로드 요청을 전달한 SQL Server Analysis Services([!INCLUDE[ssGemini](../../includes/ssgemini-md.md)]) 인스턴스에서 응답을 기다리는 시간을 변경합니다. 데이터 집합이 크면 네트워크를 통해 이동하는 데 시간이 걸리므로 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 인스턴스가 Excel 통합 문서를 검색하고 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터를 쿼리 처리를 위해 Analysis Services 인스턴스로 이동할 충분한 시간을 허용해야 합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터가 매우 클 수 있으므로 기본값은 30분입니다.  
  
5.  **연결 풀 제한 시간**에서 값을 늘리거나 줄여서 유휴 데이터 연결이 열려 있는 상태로 유지되는 시간(분)을 변경합니다. 기본값은 30분입니다. 이 기간 동안 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스는 같은 SharePoint 사용자가 같은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터에 대해 보내는 읽기 전용 요청에 유휴 데이터 연결을 다시 사용합니다. 지정된 기간 동안 해당 데이터에 대해 추가 요청이 수신되지 않는 경우 풀에서 연결이 제거됩니다. 유효한 값은 1초에서 3600초까지입니다. 연결 풀에 대한 자세한 내용은 [구성 설정 참조&#40;SharePoint용 파워 피벗&#41;](../../analysis-services/power-pivot-sharepoint/configuration-setting-reference-power-pivot-for-sharepoint.md)를 참조하세요.  
  
6.  **최대 사용자 연결 풀 크기**에서 값을 늘리거나 줄여서 PowerPivot 서비스가 각 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 사용자, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 집합 및 버전 조합에 대해 개별 연결 풀에서 만들 최대 유휴 연결 수를 변경합니다.  
  
     기본 유휴 연결 수는 1000입니다. 유효한 값은 -1(제한 없음), 0(사용자 연결 풀링 비활성화) 또는 1부터 10000까지입니다.  
  
     이러한 연결 풀을 사용하면 서비스가 같은 사용자의 같은 읽기 전용 데이터에 대한 지속적인 연결을 보다 효율적으로 지원할 수 있습니다. 연결 풀링을 사용하지 않도록 설정하면 모든 연결이 새로 작성됩니다.  
  
     연결 풀 크기에서 이 한계를 변경(0으로 설정하는 경우 포함)해도 연결이 끊기지는 않습니다. 연결 풀은 데이터에 연결할 때 대기 시간을 줄이기 위한 것이며, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스는 연결 풀 설정을 기반으로 한 연결을 거부하지 않습니다.  
  
7.  **최대 관리 연결 풀 크기**에서 값을 늘리거나 줄여서 Analysis Services 엔진 서비스에 대한 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 연결에 대해 만들어진 연결 풀에서 열려 있는 연결 수를 변경합니다. 각 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 인스턴스는 같은 컴퓨터에 있는 Analysis Services 인스턴스에 대해 별도의 관리 연결을 엽니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스는 별도의 풀을 만들어 유휴 연결을 확인하고 서버 상태를 모니터링하기 위해 관리 연결을 다시 사용합니다. 기본값은 연결 200개입니다. 유효한 값은 -1(제한 없음), 0(관리 연결 풀링 사용 안 함) 또는 1부터 10000까지입니다. 0을 선택하면 모든 연결이 새로 만들어집니다.  
  
8.  **할당 방법**에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스가 초기 요청의 부하를 분산하기 위해 특정 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 선택하는 데 사용하는 부하 분산 체계를 지정할 수 있습니다. 기본값은 사용 가능한 메모리와 프로세서 사용률을 기준으로 측정되는 서버 상태를 기준으로 하여 요청을 할당하는 **상태 기반**입니다. 서버가 사용 중인지 또는 유휴 상태인지에 관계없이 같은 반복 순서로 서버에 요청을 할당하는 **라운드 로빈** 을 선택할 수도 있습니다.  
  
9. 데이터 새로 고침의 **업무 시간**에 업무 시간을 정의하는 시간 범위를 지정할 수 있습니다. 데이터 새로 고침 일정은 업무 시간이 종료된 이후에 실행되어 정규 업무 시간 중에 생성된 트랜잭션 데이터를 가져올 수 있습니다.  
  
10. **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 무인 데이터 새로 고침 계정**에서 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 새로 고침 작업을 실행하는 데 사용되는 미리 정의된 계정을 저장할 미리 정의된 Secure Store Services 대상 응용 프로그램을 지정할 수 있습니다. ID가 아니라 대상 애플리케이션 이름을 지정해야 합니다. 무인 데이터 새로 고침에 대한 대상 애플리케이션은 SQL Server 설치 프로그램에서 새 서버 옵션을 사용해 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 설치한 경우 자동으로 작성됩니다. 그렇지 않은 경우에는 대상 애플리케이션을 수동으로 만들어야 합니다. 계정 구성 방법은 [파워 피벗 무인 데이터 새로 고침 계정 구성(SharePoint용 파워 피벗)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)을 참조하세요.  
  
11. **사용자가 사용자 지정 Windows 자격 증명을 입력할 수 있습니다**에서 확인란을 선택하거나 선택을 취소하여 일정 소유자가 데이터 새로 고침 일정을 실행하기 위해 임의의 Windows 자격 증명을 입력할 수 있는지 여부를 지정할 수 있습니다. 이 확인란을 선택하면 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션은 저장된 각 자격 증명 집합에 대해 대상 애플리케이션을 만들고 관리합니다. 자세한 내용은 [파워 피벗 데이터 새로 고침을 위한 저장된 자격 증명 구성(SharePoint용 파워 피벗)](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)을 참조하세요.  
  
12. **최대 처리 기록 길이**에서 데이터 새로 고침 처리의 기록 레코드를 유지할 기간을 지정할 수 있습니다. 이 정보는 데이터 새로 고침을 사용하는 각 통합 문서에 대해 유지되는 데이터 새로 고침 기록 페이지에 표시되며 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에도 표시됩니다.  
  
13. 사용 데이터 컬렉션의 **쿼리 보고 간격**에 쿼리 통계 보고에 대한 간격을 지정합니다. 쿼리 통계는 서버 간 통신을 최소화하기 위해 단일 이벤트로 보고됩니다.  
  
14. 사용 데이터 기록에 사용 데이터의 기록 레코드를 유지할 기간을 지정합니다. 사용 정보는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에 표시됩니다. 사용 데이터 기록에 대해 너무 작은 값을 지정하면 보고서의 효율성이 떨어집니다.  
  
15. 사용 데이터 컬렉션의 각 쿼리 응답 임계값에 한 범주가 끝나고 다른 범주가 시작되는 위치를 결정하는 상한을 지정합니다. 이러한 범주는 쿼리 동작이 측정되는 기준선을 설정합니다. 이러한 범주를 사용하여 시스템의 쿼리 응답 시간 추세를 모니터링할 수 있습니다. 이 정보는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 관리 대시보드에 표시됩니다.  
  
16. **확인** 을 클릭하여 변경 내용을 저장합니다.  
  
     로드 제한 시간 또는 할당 방법 변경 사항은 새로 수신되는 요청에만 적용됩니다. 이미 진행 중인 요청에는 요청을 받았을 때 유효했던 값이 적용됩니다.  
  
##  <a name="AssignGSA"></a> 웹 응용 프로그램에 PowerPivot 서비스 응용 프로그램 할당  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 구성한 후에는 이를 웹 응용 프로그램의 서비스 응용 프로그램 연결 목록에 추가하여 웹 응용 프로그램에 할당할 수 있습니다. 이때 다음과 같은 두 가지 방법을 사용할 수 있습니다.  
  
-   **기본** 연결 그룹에 PowerPivot 서비스 응용 프로그램을 추가합니다. *기본 연결 그룹* 은 이를 참조하는 모든 웹 응용 프로그램에서 사용할 수 있는 서비스 응용 프로그램 연결 모음입니다. 이 목록에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 추가해야 합니다.  
  
-   특정 웹 애플리케이션에 대한 **사용자 지정** 연결 목록을 만듭니다. 여러 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 만든 경우 사용자 지정 목록에서 선택하여 사용할 애플리케이션을 지정할 수 있습니다.  
  
 기본 연결 그룹에 같은 유형의 서비스 애플리케이션을 둘 이상 추가할 수 있습니다. 하지만 목록에 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션을 여러 개 추가하는 구성은 지원되지 않습니다.  
  
1.  중앙 관리의 **애플리케이션 관리**에서 **웹 애플리케이션 관리**를 클릭합니다.  
  
2.  연결을 지정할 애플리케이션을 선택합니다(예: SharePoint -80).  
  
3.  **서비스 연결**을 클릭합니다.  
  
4.  **다음 연결 그룹 편집**에서 **기본값** 또는 **[사용자 지정]** 을 선택합니다.  
  
5.  **[사용자 지정]** 에 대해 사용할 각 서비스 응용 프로그램 연결 옆에 있는 확인란을 선택합니다. 여러 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 애플리케이션이 있는 경우( **파워 피벗 서비스 애플리케이션 프록시**유형 설정으로 표시) 하나만 선택해야 합니다.  
  
6.  **확인**을 클릭합니다.  
  
##  <a name="EditGSA"></a> 서비스 응용 프로그램 속성 편집  
 서비스 애플리케이션 이름, 애플리케이션 풀, 데이터베이스 설정 및 서비스 연결을 지정하는 속성 페이지를 다시 열려면 다음 지침을 따르십시오.  
  
1.  중앙 관리의 애플리케이션 관리에서 **서비스 애플리케이션 관리**를 클릭합니다.  
  
2.  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 선택하되 클릭하지는 않습니다. 유형 이름을 클릭하여 전체 행을 선택할 수 있습니다.  
  
3.  리본에서 **속성** 을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [중앙 관리에서 Power Pivot 서버 관리 및 구성](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)  
  
  
