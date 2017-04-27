---
title: "승인 필요(Master Data Services) | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b475a53d-269d-49f3-bb42-965c555f80be
caps.latest.revision: 7
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 7
---
# 승인 필요(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 관리자는 엔터티를 승인 필요 항목으로 설정할 수 있습니다. 이 엔터티를 변경할 때마다 엔터티 관리자 중 한 명이 변경 내용을 검토하고 승인해야 합니다.  
  
> [!NOTE]  
>  리프 멤버를 변경하는 경우 승인이 필요합니다. 사용되지 않는 명시적 계층 및 컬렉션을 변경하는 경우에는 승인이 무시됩니다.  
>   
>  준비 테이블 프로세스에서 수행하는 변경에서도 승인이 무시됩니다.  
>   
>  비즈니스 규칙을 통한 변경 역시 승인이 무시됩니다.  
  
## 필수 구성 요소  
 이 절차를 수행하려면  
  
-   시스템 관리 기능 영역에 액세스할 수 있는 권한이 있어야 합니다.  
  
-   모델 관리자여야 합니다. 자세한 내용은 [관리자&#40;Master Data Services&#41;](../master-data-services/administrators-master-data-services.md)를 참조하세요.  
  
-   엔터티가 있어야 합니다. 자세한 내용은 [엔터티 만들기&#40;Master Data Services&#41;](../master-data-services/create-an-entity-master-data-services.md)를 참조하세요.  
  
## 엔터티에 대해 승인 필요 기능을 사용하도록 설정하려면  
  
1.  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 **시스템 관리**를 클릭합니다.  
  
2.  **모델 관리** 페이지의 표에서 모델을 선택하고 **엔터티**를 클릭합니다.  
  
3.  **엔터티 관리** 페이지의 표에서  **승인 필요** 를 사용하도록 설정할 엔터티의 행을 선택합니다.  
  
4.  **편집**을 클릭하고 **승인 필요**를 선택한 후에 **저장**을 클릭합니다.  
  
## 참고 항목  
 [변경 집합&#40;Master Data Services&#41;](../master-data-services/changesets-master-data-services.md)  
  
  