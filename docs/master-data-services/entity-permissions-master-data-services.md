---
title: "엔터티 권한(Master Data Services) | Microsoft Docs"
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
  - "엔터티 [Master Data Services], 권한"
  - "권한 [Master Data Services], 엔터티"
ms.assetid: 22785062-4faf-46ee-bffa-01cbd6d5a5b3
caps.latest.revision: 6
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 6
---
# 엔터티 권한(Master Data Services)
  엔터티 권한은 다음에 적용됩니다.  
  
-   리프 멤버 및 통합 멤버 둘 다의 **이름** 및 **코드**를 포함하여 엔터티의 모든 특성  
  
-   엔터티의 모든 컬렉션  
  
-   명시적 계층 멤버 자격 및 관계  
  
 엔터티에 대한 사용 권한이 있는 경우 해당 엔터티, 명시적 계층 및 컬렉션에서 멤버를 추가하거나 제거할 수 있습니다.  
  
> [!NOTE]  
>  이러한 사용 권한은 사용자 인터페이스의 **탐색기** 기능 영역에만 적용됩니다.  
  
|사용 권한|Description|  
|----------------|-----------------|  
|**읽기**|사용자는 멤버, 특성, 계층 멤버 자격 또는 컬렉션 멤버를 읽을 수 있습니다.|  
|**만들기**|사용자는 멤버를 만들고 만드는 동안 특성 값을 할당할 수 있습니다.|  
|**Update**|사용자는 멤버, 특성, 계층 멤버 자격 또는 컬렉션 멤버를 업데이트할 수 있습니다.|  
|**Delete**|사용자는 멤버를 삭제할 수 있습니다.|  
|**거부**|엔터티에 대한 모든 액세스를 거부 합니다.|  
  
 읽기, 만들기, 업데이트 및 삭제 권한을 결합할 수도 있습니다. 만들기, 업데이트 및 삭제 권한이 할당될 때 읽기 권한은 자동으로 할당됩니다.  
  
## 참고 항목  
 [모델 개체 사용 권한 할당&#40;Master Data Services&#41;](../master-data-services/assign-model-object-permissions-master-data-services.md)   
 [모델 개체 권한&#40;Master Data Services&#41;](../master-data-services/model-object-permissions-master-data-services.md)   
 [엔터티&#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
  