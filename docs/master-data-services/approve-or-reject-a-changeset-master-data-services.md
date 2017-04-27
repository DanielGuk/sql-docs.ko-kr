---
title: "변경 집합 승인 또는 거부(Master Data Services) | Microsoft Docs"
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
ms.assetid: 45bd01f9-ae15-4fc5-a2ba-eee565a26ef8
caps.latest.revision: 8
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 8
---
# 변경 집합 승인 또는 거부(Master Data Services)
  변경 집합은 마스터 데이터에 대해 보류 중인 변경 내용의 컬렉션입니다. 엔터티를 변경할 때 관리자가 승인을 해야 하는 경우 승인을 위해 변경 집합이 제출되면 변경 집합을 검토한 후 승인하거나 거부할 수 있습니다.  
  
## 필수 구성 요소  
  
-   **탐색기** 기능 영역에 액세스할 수 있는 권한이 있어야 합니다. 자세한 내용은 [기능 영역 권한&#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)을 참조하세요.  
  
-   엔터티에 대한 관리자 권한이 있어야 합니다.  
  
-   엔터티 변경 시 관리자가 승인을 해야 합니다.  
  
-   변경 집합 상태가 보류 중이면 변경 집합을 검토한 후 승인하거나 거부할 수 있습니다.  
  
-   사용자가 변경 내용을 직접 승인할 수는 없습니다. 엔터티 관리자는 자신의 변경 집합을 승인하도록 할 보조 관리자를 할당해야 합니다.  
  
## 변경 집합을 승인하거나 거부하려면  
  
1.  [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 홈 페이지에서 모델 및 버전을 선택하고 **탐색기**를 클릭합니다.  
  
2.  **엔터티** 메뉴에서 엔터티를 클릭합니다.  
  
3.  오른쪽 창에서 **변경 집합** 을 선택하고 승인 또는 거부할 변경 집합을 두 번 클릭합니다.  
  
4.  변경 집합을 적용하고 보류 중인 변경 내용을 검토하려면 **적용** 을 클릭합니다.  
  
5.  변경 집합을 거부하고 소유자에게 다시 보내려면 **거부** 를 클릭합니다.  
  
6.  **승인** 을 클릭하여 변경 집합을 승인합니다. 변경 집합이 자동으로 커밋됩니다.  
  
## 참고 항목  
 [변경 집합 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-changeset-master-data-services.md)   
 [변경 집합 적용 및 업데이트&#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)   
 [변경 집합 커밋 또는 제출&#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)  
  
  