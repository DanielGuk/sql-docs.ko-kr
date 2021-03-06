---
title: 참조 데이터에 도메인 또는 복합 도메인 연결 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql13.dqs.dm.refdata.f1
- sql13.dqs.dm.refcatalog.f1
ms.assetid: 36af981c-d0d0-4dc6-afe5-bbb3c97845dc
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 358b1779ebc24f17035cb50eda77c7249456ff9a
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617085"
---
# <a name="attach-domain-or-composite-domain-to-reference-data"></a>참조 데이터에 도메인 또는 복합 도메인 연결

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  이 항목에서는 데이터 품질 기술 자료의 도메인/복합 도메인을 Windows Azure Marketplace의 참조 데이터 서비스에 연결하여 고품질 데이터 참조 데이터에 대한 정보를 구축하는 방법에 대해 설명합니다. 각 참조 데이터 서비스에는 스키마(데이터 열)가 포함되어 있습니다. 도메인 또는 복합 도메인을 참조 데이터 서비스에 연결한 후 연결된 도메인 또는 연결된 복합 도메인 내의 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑해야 합니다. 복합 도메인을 참조 데이터 서비스에 연결하면 한 도메인만 참조 데이터 서비스에 연결한 다음 복합 도메인 내 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑할 수 있습니다.  

> [!IMPORTANT]
> 이 문서에서는 Azure DataMarket에서 이전에 사용할 수 있었던 타사 참조 데이터 서비스에 대해 설명합니다. 예를 들어 Melissa 주소 데이터를 포함한 DataMarket 및 Data Services는 2016년 12월 31일 이후 중단되었습니다. 따라서 DataMarket의 지정된 서비스를 사용하여 이 문서의 예제를 더 이상 실행할 수 없습니다. 타사 참조 데이터 공급자로부터 직접 온라인으로 사용할 수 있는 참조 데이터 서비스는 계속 사용할 수 있습니다.

> [!WARNING]  
>  도메인을 참조 데이터 서비스 스키마의 열에 매핑하는 동안 참조 데이터 서비스에 연결된 복합 도메인을 도메인 드롭다운 목록에서 사용할 수 있습니다. 복합 도메인을 참조 데이터 서비스 스키마의 열에 매핑하지 마세요. 복합 도메인 내의 개별 도메인만 참조 데이터 서비스 스키마의 적절한 열에 매핑해야 합니다. 그렇지 않으면 오류가 발생합니다.  
  
 참조 데이터 서비스를 사용하도록 선택한 경우 참조 데이터 서비스 스키마에 적절한 도메인과 함께 매핑되어야 하는 필수 열이 있을 수 있습니다. 참조 데이터 스키마의 필수 열은 열 이름에서 "(M)"으로 식별됩니다. 예를 들어 **AddressLine**은 **Melissa Data – Address Data**의 필수 스키마 열이고 **CompanyName**은 **Digital Trowel Inc. – Us companies and professional data for SQL users**의 필수 스키마 열입니다.  
  
 이 토픽에서는 복합 도메인 **Address Verification** 아래에 **Address Line**, **City**, **State** 및 **Zip**의 4개 도메인을 만들고, 도메인을 **Melissa Data – Address Check** 참조 데이터 서비스에 연결한 다음, 복합 도메인 내의 개별 도메인을 참조 데이터 서비스 스키마의 적절한 열에 매핑할 것입니다.  
  
## <a name="before-you-begin"></a>시작하기 전 주의 사항  
  
###  <a name="Prerequisites"></a> 사전 요구 사항  
 참조 데이터 서비스를 사용하도록 DQS( [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] )를 구성한 상태여야 합니다. [참조 데이터를 사용하도록 DQS 구성](../data-quality-services/configure-dqs-to-use-reference-data.md)을 참조하세요.  
  
###  <a name="Security"></a> 보안  
  
#### <a name="permissions"></a>Permissions  
 참조 데이터에 도메인을 매핑하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 역할이 있어야 합니다.  
  
##  <a name="Map"></a> Melissa Data의 참조 데이터에 도메인 매핑  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)] [Data Quality Client 응용 프로그램을 실행합니다](../data-quality-services/run-the-data-quality-client-application.md).  
  
2.  [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] 홈 화면의 **기술 자료 관리**에서 **새 기술 자료**를 클릭합니다.  
  
3.  **새 기술 자료** 화면에서 새 기술 자료의 이름을 입력하고 **도메인 관리** 작업을 클릭한 후 **만들기**를 클릭합니다.  
  
4.  **도메인 관리** 화면에서 **도메인 만들기** 아이콘을 클릭하여 도메인을 만듭니다. 4개의 도메인 **Address Line**, **City**, **State**및 **Zip**을 만듭니다.  
  
5.  **복합 도메인 만들기** 아이콘을 클릭하여 복합 도메인을 만듭니다. **복합 도메인 만들기** 대화 상자에서 **복합 도메인 이름** 입력란에 **Address Verification** 을 입력하고 3단계에서 만든 모든 도메인을 복합 도메인에 포함합니다. **확인**을 클릭합니다.  
  
6.  왼쪽에 있는 **도메인** 창에서 **Address Verification**을 클릭하여 복합 도메인을 선택한 다음 오른쪽에서 **참조 데이터** 탭을 클릭합니다.  
  
7.  **찾아보기** 아이콘을 클릭합니다.  
  
8.  **온라인 참조 데이터 공급자 카탈로그** 대화 상자에서 다음을 수행합니다.  
  
    1.  **DataMarket Data Quality Services**에서 **Melissa Data – Address Check** 확인란을 선택합니다.  
  
    2.  Melissa Data – Address Check 참조 데이터 서비스의 열을 적절한 도메인(Address Line, City, State 및 Zip)과 함께 매핑합니다. **RDS 스키마** 열에서 참조 데이터 서비스 열을 선택한 다음 **도메인** 열에서 적절한 도메인을 선택하여 열을 매핑합니다. 테이블에 더 많은 행을 추가하려면 **스키마 항목 추가** 아이콘을 클릭합니다.  
  
    3.  **확인** 을 클릭하여 변경 내용을 저장하고 **온라인 참조 데이터 공급자 카탈로그** 대화 상자를 닫습니다.  
  
         ![온라인 참조 데이터 공급자 카탈로그 대화 상자](../data-quality-services/media/dqs-onlinereferencedataproviderscatalog.gif "온라인 참조 데이터 공급자 카탈로그 대화 상자")  
  
        > [!NOTE]  
        >  -   **온라인 참조 데이터 공급자 카탈로그** 대화 상자의 **DataMarket Data Quality Services** 노드에 Windows Azure Marketplace에서 구독한 모든 참조 데이터 서비스 공급자가 표시됩니다. DQS에서 다이렉트 온라인 타사 참조 데이터 서비스 공급자를 구성한 경우 **타사 Direct Online 공급자** 라는 노드 아래에 해당 공급자가 표시됩니다(지금은 DQS에 다이렉트 온라인 타사 참조 데이터 서비스 공급자가 구성되어 있지 않으므로 사용할 수 없음).  
  
9. **참조 데이터** 탭으로 돌아갑니다. **공급자 설정** 영역에서 필요에 따라 다음 입력란의 값을 변경합니다.  
  
    -   **자동 수정 임계값**: 신뢰도 수준이 이 임계값보다 높은 참조 데이터 서비스의 수정 사항이 자동으로 적용됩니다. 해당 백분율 값의 10진수 표기법으로 값을 입력합니다. 예를 들어 90%의 경우 0.9를 입력합니다.  
  
    -   **제안된 후보**: 참조 데이터 서비스에서 표시할 제안된 후보의 개수입니다.  
  
    -   **최소 신뢰도**: 신뢰도 수준이 이 값보다 낮은 참조 데이터 서비스의 제안은 무시됩니다. 해당 백분율 값의 10진수 표기법으로 값을 입력합니다. 예를 들어 60%의 경우 0.6을 입력합니다.  
  
10. **마침** 을 클릭하여 기술 자료를 게시합니다. 기술 자료가 올바르게 게시되면 확인 메시지가 나타납니다.  
  
 이제 데이터 품질 프로젝트의 정리 작업에 이 기술 자료를 사용하여 Windows Azure Marketplace를 통해 Melissa Data에서 제공하는 정보를 기반으로 원본 데이터의 미국 주소를 표준화하고 정리할 수 있습니다.  
  
##  <a name="FollowUp"></a> 후속 작업: 참조 데이터에 도메인을 매핑한 후  
 데이터 품질 프로젝트를 만들고 미국 주소가 포함된 원본 데이터를 이 항목에서 만든 기술 자료와 비교하여 정리 작업을 실행합니다. [참조 데이터&#40;외부&#41; 기술 자료를 사용하여 데이터 정리](../data-quality-services/cleanse-data-using-reference-data-external-knowledge.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [DQS의 참조 데이터 서비스](../data-quality-services/reference-data-services-in-dqs.md)   
 [데이터 정리](../data-quality-services/data-cleansing.md)  
  
  
