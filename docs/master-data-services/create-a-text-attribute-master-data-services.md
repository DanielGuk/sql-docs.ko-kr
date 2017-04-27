---
title: "텍스트 특성 만들기(Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "특성 [Master Data Services], 텍스트 특성 만들기"
  - "텍스트 특성 만들기 [Master Data Services]"
ms.assetid: cd8b57de-364d-42a3-9273-c1c6b992bb40
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# 텍스트 특성 만들기(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 사용자가 텍스트 문자열을 특성 값으로 입력할 수 있도록 하려면 텍스트 특성을 만듭니다.  
  
## 필수 구성 요소  
 이 절차를 수행하려면  
  
-   **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
-   해당 특성을 만들 엔터티가 있어야 합니다. 자세한 내용은 [엔터티 만들기&#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)를 참조하세요.  
  
## 특성 정보  
 생성되는 각 특성에 대해 열이 7개 포함된 행이 표에 추가됩니다. 다음 표에서는 열을 설명합니다.  
  
|열|Description|  
|------------|-----------------|  
|상태|특성 상태입니다.<br /><br /> 저장을 클릭하면 특성이 업데이트되고 있음을 나타내는 ![Icon for updating status](../master-data-services/media/mds-statusicon-updating.png "Icon for updating status") 이미지가 표시됩니다.<br /><br /> 특성을 만들거나 편집할 때 오류가 발생하면 ![Icon for error status](../master-data-services/media/mds-statusicon-error.png "Icon for error status") 이미지가 표시됩니다.<br /><br /> 오류가 발생하지 않으면 상태가 정상이며 ![Icon for OK status](../master-data-services/media/mds-statusicon-ok.png "Icon for OK status") 이미지가 표시됩니다.|  
|이름|특성 이름입니다.|  
|표시 이름|특성 표시 이름입니다.|  
|Description|특성 설명입니다.|  
|표시 픽셀 폭|특성 폭입니다.|  
|유형 및 속성|특성의 유형 및 데이터 형식 정보입니다.|  
|변경 내용 추적 설정|특성의 변경 내용 추적을 사용할지 여부를 지정하고 그룹 번호를 괄호 안에 표시합니다.|  
  
 특성을 클릭하면 다음 정보가 표시됩니다.  
  
-   **만든 사람**: 특성을 만든 사용자의 이름입니다.  
  
-   **날짜**: 특성을 만든 날짜와 시간입니다.  
  
-   **업데이트한 사람**: 특성을 마지막으로 업데이트한 사용자의 이름입니다.  
  
-   **날짜**: 특성을 마지막으로 업데이트한 날짜와 시간입니다.  
  
### 텍스트 특성을 만들려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  **모델 관리** 페이지의 표에서 모델을 선택하고 **엔터티**를 클릭합니다.  
  
3.  **엔터티 관리** 페이지에서 해당 특성을 만들려는 엔터티의 행을 선택합니다.  
  
4.  **특성**을 클릭합니다.  
  
5.  **특성 관리** 페이지에서 다음 작업 중 하나를 수행하고 **추가**를 클릭합니다.  
  
    -   리프 멤버용 특성의 경우 **멤버 형식** 목록 상자에서 **리프** 를 선택합니다.  
  
    -   통합 멤버용 특성의 경우 **멤버 형식** 목록 상자에서 **통합** 을 선택합니다.  
  
    -   컬렉션용 특성의 경우 **멤버 형식** 목록 상자에서 **컬렉션** 을 선택합니다.  
  
6.  **이름** 상자에 특성의 이름을 입력합니다. 특성 이름으로 사용하지 않아야 하는 단어의 목록을 보려면 [예약어&#40;Master Data Services&#41;](../master-data-services/reserved-words-master-data-services.md)를 참조하세요.  
  
7.  필요에 따라 표시 이름을 입력하고 **설명** 상자에 특성의 설명을 입력합니다.  
  
8.  **탐색기** 표에 표시할 특성 열의 너비를 **표시 픽셀 폭** 상자에 입력합니다.  
  
9. **특성 유형** 목록에서 **자유 형식**을 선택합니다.  
  
10. **데이터 형식** 목록에서 **텍스트**를 선택합니다.  
  
11. **길이** 상자에 허용되는 최대 문자 수를 입력합니다.  
  
12. 또는 특성 그룹의 변경 내용을 추적하려면 **변경 내용 추적 설정** 을 선택합니다. 자세한 내용은 [변경 내용 추적 그룹에 특성 추가&#40;Master Data Services&#41;](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)를 참조하세요.  
  
13. **저장**을 클릭합니다.  
  
## 참고 항목  
 [특성&#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)   
 [특성 이름 및 데이터 형식 변경&#40;Master Data Services&#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [도메인 기반 특성 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [파일 특성 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  