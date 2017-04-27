---
title: "참조 데이터(외부) 기술 자료를 사용하여 데이터 정리 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "data-quality-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 158009e9-8069-4741-8085-c14a5518d3fc
caps.latest.revision: 15
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 15
---
# 참조 데이터(외부) 기술 자료를 사용하여 데이터 정리
  이 항목에서는 참조 데이터 공급자의 기술 자료를 사용하여 데이터를 정리하는 방법에 대해 설명합니다. 실행의 모든 단계 동안 정리 작업에 대해 동일에 설명 된 대로 참조 데이터 공급자의 정보를 사용 하 여 데이터 정리는 [데이터를 사용 하 여 DQS 정리 & #40; 내부 & #41; 기술](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md), 이 항목에서 참조 데이터 서비스를 사용 하 여 데이터 정리에 관련 된 정보를 제공 합니다. [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS).  
  
 DQS의 참조 데이터 서비스 기능을 사용하여 데이터를 정리하는 경우 DQS 정리 프로세스에서는 매핑된 도메인 값을 참조 데이터 서비스 공급자에게 일괄 처리 요청으로 보냅니다. 참조 데이터 서비스는 다음과 같은 정보로 응답합니다.  
  
-   제안된 수정  
  
-   신뢰도  
  
-   매핑된 도메인에 대한 추가 정보 참조 데이터는 추가 데이터로 원본을 표준화, 구문 분석 또는 보강할 수 있습니다. 이 정보는 응답의 추가 필드에 제공됩니다.  
  
 참조 데이터 서비스에서 응답을 받은 후 정리 작업 도중 DQS에서는 다음과 같은 작업이 수행됩니다.  
  
-   도메인을 참조 데이터 서비스와 매핑하는 동안 지정한 **자동 수정 임계값** 및 **최소 신뢰도** 값을 기반으로 신뢰도 수준에 따라 도메인 값이 자동으로 수정되거나 제안됩니다.  
  
    > [!NOTE]  
    >  참조 데이터 서비스에서 기술 자료를 사용하여 데이터를 정리하는 동안 도메인을 참조 데이터 서비스에 매핑하는 도중 지정한 임계값이 적용되며 **구성** 섹션의 **일반 설정** 탭에서 지정한 임계값은 적용되지 않습니다. 참조 데이터 정리에 대 한 임계값을 지정 하는 방법에 대 한 내용은 참조의 9 단계 [연결 도메인 또는 복합 도메인을 참조 데이터](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)합니다.  
  
-   도메인 값은 **제안**, **새로 만들기**, **잘못 됨**, **수정됨**및 **수정**으로 분류됩니다.  
  
-   추가 데이터가 원본에 연결되고 정보를 정리된 데이터와 함께 내보내기에 사용할 수 있습니다.  
  
## 시작하기 전에  
  
###  <a name="Prerequisites"></a> 필수 구성 요소  
 DQS 기술 자료의 필수 도메인이 알맞은 참조 데이터 서비스에 매핑되어 있어야 합니다. 또한 정리할 데이터 유형에 대한 정보가 기술 자료에 포함되어 있어야 합니다. 예를 들어 미국 주소가 포함된 원본 데이터를 정리하려면 미국 주소의 "고품질" 데이터를 제공하는 참조 데이터 서비스 공급자에게 도메인을 매핑해야 합니다. 자세한 내용은 참조 [연결 도메인 또는 복합 도메인을 참조 데이터](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md)합니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 데이터 정리를 수행하려면 DQS_MAIN 데이터베이스에 대한 dqs_kb_editor 또는 dqs_kb_operator 역할이 있어야 합니다.  
  
##  <a name="Cleanse"></a> 참조 데이터 기술 자료를 사용하여 데이터 정리  
 이전 항목에서 매핑한 것 도메인을 사용 하 여 동일한 예제는 꾸준히 [연결 도메인 또는 복합 도메인을 참조 데이터](../data-quality-services/attach-domain-or-composite-domain-to-reference-data.md), Windows Azure Marketplace의 Melissa Data 서비스와 함께 합니다. 이제 같은 도메인을 사용하여 샘플 US 주소 몇 개를 정리합니다. 에 설명 된 대로 동일한 데이터를 정리 하는 단계는 [데이터를 사용 하 여 DQS 정리 & #40; 내부 & #41; 기술](../data-quality-services/cleanse-data-using-dqs-internal-knowledge.md)합니다. 그러나 프로세스를 진행하는 동안 필요할 때마다 다시 설명하겠습니다.  
  
1.  데이터 품질 프로젝트를 만들고 **정리** 작업을 선택합니다. [Create a Data Quality Project](../data-quality-services/create-a-data-quality-project.md)을 참조하세요.  
  
2.  **맵** 페이지에서 **Address Line**, **City**, **State**및 **Zip**도메인을 원본 데이터의 알맞은 열에 매핑합니다. **다음**을 클릭합니다.  
  
    > [!NOTE]  
    >  내 4에 있는 모든 도메인을 매핑 했으므로 **Address Verification** 복합 도메인에 데이터 정리는 지금 수행 될 복합 도메인 수준에서 개별 도메인 수준이 아닌 합니다.  
  
3.  에 **정리** 페이지를 클릭 하 여 컴퓨터 기반 정리 프로세스를 실행 합니다. **시작**합니다. 정리 프로세스가 끝난 후 **다음**을 클릭합니다.  
  
    > [!NOTE]  
    >  에 **정리** 페이지, DQS에 참조 데이터 서비스는 다음 두 가지 방법으로 연결 되어 있는 도메인에 대 한 정보를 표시 합니다.  
    >   
    >  -   아래 메시지가 표시 되는 **시작** 단추: "도메인 \< Domain1>, \< 도메인 2>,... \< DomainN> 참조 데이터 서비스 공급자를 사용 하 여 정리 됩니다. " 이 예에서는 다음 메시지가 표시됩니다. “Address Verification 도메인이 참조 데이터 서비스 공급자를 사용하여 정리됩니다.”  
    > -   아이콘, ![도메인이 RDS에 연결됨](../data-quality-services/media/dqs-rdsindicator.png "도메인이 RDS에 연결됨"), 에 표시 되는 **프로파일러** 참조 데이터 서비스 공급자에 연결 된 도메인에 대해 영역입니다. 이 예에서는 **Address Verification** 복합 도메인에 대해 아이콘이 표시됩니다.  
  
4.  **결과 관리 및 보기** 페이지에서 도메인 값을 검토합니다. 참조 데이터 서비스는 도메인이 참조 데이터 서비스에 매핑되는 동안 **제안된 후보** 상자에 지정된 최대 제안 수에 따라 둘 이상의 제안을 값에 대해 표시할 수 있습니다(사용 가능한 경우). 예를 들어, 다음 미국 주소에는 두 가지 제안이 표시됩니다.  
  
     **원래 값:**  
  
    |Address Line|City|State|Zip|  
    |------------------|----------|-----------|---------|  
    |1 msft way|Redmond||98052|  
  
     **제안된 값:**  
  
    |Address Line|City|State|Zip|  
    |------------------|----------|-----------|---------|  
    |1 Microsoft Way|Redmond|WA|98052|  
    |PO Box 1|Redmond|WA|98073|  
  
     ![참조 데이터 서비스를 사용하여 정리](../data-quality-services/media/dqs-rdscleansing.JPG "참조 데이터 서비스를 사용하여 정리")  
  
    > [!NOTE]  
    >  복합 도메인의 경우 컴퓨터 기반 정리 프로세스 도중 수정한 개별 도메인이 다른 색으로 강조 표시됩니다. 예를 들어 이 경우에는 **Address Line** 및 **State** 도메인이 수정되었으므로 녹청으로 강조 표시됩니다.  
  
5.  모든 도메인 값을 검토한 후 **다음** 을 클릭하여 데이터를 내보냅니다.  
  
6.  에 **내보내기** 페이지 (원본, 이유, 신뢰도 및 상태)에 각 도메인에 대 한 정리 작업에 대 한 일반 정보, 외 추가 정보는 Melissa Data 참조에 의해 위 도와 경도 주소, 지방 이름, 주소를 같은 주소 데이터에 대 한 데이터 서비스 (건물, 거리 등)을 입력 하 고 등 제공을 확인할 수 있습니다.  
  
7.  데이터를 필요한 대상 (SQL Server, CSV 또는 Excel) 내보내고 클릭 **마침** 프로젝트를 닫습니다.  
  
    > [!IMPORTANT]  
    >  64비트 버전의 Excel을 사용 중인 경우 정리한 데이터를 Excel 파일로 내보낼 수 없습니다. SQL Server 데이터베이스 또는 .csv 파일로만 내보낼 수 있습니다.  
  
  