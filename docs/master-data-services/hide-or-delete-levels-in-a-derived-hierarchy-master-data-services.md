---
title: "파생 계층의 수준 숨기기 또는 삭제(Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "파생된 계층, 수준 숨기기"
  - "파생된 계층, 수준 삭제"
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# 파생 계층의 수준 숨기기 또는 삭제(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서는 그룹화용으로 수준이 필요하지만 해당 수준을 표시할 필요는 없는 경우 파생 계층의 수준을 숨길 수 있습니다. 그룹화에 수준을 사용하지 않으려면 수준을 삭제합니다.  
  
## 필수 구성 요소  
 이 절차를 수행하려면  
  
-   **시스템 관리** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
### 파생 계층의 수준을 숨기거나 삭제하려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  메뉴 모음에서 **관리** 를 가리키고 **파생 계층**을 클릭합니다.  
  
3.  **파생 계층 유지 관리** 페이지의 **모델** 목록에서 모델을 선택합니다.  
  
4.  편집하려는 파생 계층의 행을 선택합니다.  
  
5.  **편집**을 클릭합니다.  
  
6.  **현재 수준** 창에서 다음을 수행합니다.  
  
    -   수준을 숨기려면 맨 위 또는 맨 아래 수준 외의 수준을 클릭합니다. **표시** 목록에서 **아니요**를 선택하고 **선택한 계층 항목 저장**을 클릭합니다.  
  
    -   최상위 수준을 삭제하려면 **선택한 계층 항목 삭제**를 클릭합니다. 확인 대화 상자에서 **확인**을 클릭합니다. 최상위 수준만 삭제할 수 있습니다.  
  
## 참고 항목  
 [계층 내에서 멤버 이동&#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)   
 [파생 계층&#40;Master Data Services&#41;](../master-data-services/derived-hierarchies-master-data-services.md)  
  
  