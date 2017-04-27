---
title: "멤버(Master Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "master-data-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "리프 멤버 [Master Data Services]"
  - "통합 멤버 [Master Data Services]"
  - "통합 멤버 [Master Data Services], 통합 멤버 정보"
  - "멤버 [Master Data Services], 멤버 정보"
  - "리프 멤버 [Master Data Services], 리프 멤버 정보"
  - "멤버 [Master Data Services]"
ms.assetid: 0fda32b9-677d-4ba2-bb28-f76f2383a30f
caps.latest.revision: 16
author: "sabotta"
ms.author: "carlasab"
manager: "jhubbard"
caps.handback.revision: 14
---
# 멤버(Master Data Services)
  [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]에서 멤버는 실제 마스터 데이터입니다. 예를 들어, 멤버는 Product 엔터티의 Road-150 bike이거나 Customer 엔터티의 특정 고객일 수 있습니다.  
  
## 다른 모델 개체와 멤버의 관계  
 멤버는 테이블의 행으로 생각할 수 있습니다. 관련 멤버는 엔터티에 포함되며 특성 값으로 각 멤버가 정의됩니다.  
  
 이 예에서 테이블은 엔터티를 나타내고, 테이블의 행은 멤버를 나타내며, 테이블의 열은 특성을 나타냅니다. 각 셀은 특정 멤버의 특성 값을 나타냅니다.  
  
 ![테이블로 표시된 MDS(Master Data Services) 엔터티](../master-data-services/media/mds-conc-entity-table.gif "테이블로 표시된 MDS(Master Data Services) 엔터티")  
  
## 멤버 유형  
 리프 멤버, 통합 멤버 및 컬렉션 멤버로 세 가지 멤버 유형이 있습니다.  
  
 리프 멤버는 엔터티의 기본 멤버입니다.  
  
-   파생 계층에서 멤버 유형은 리프 멤버뿐입니다. 한 엔터티의 리프 멤버가 다른 엔터티의 리프 멤버 부모로 사용됩니다.  
  
-   명시적 계층에서 리프 멤버는 최하위 수준이므로 자식을 가질 수 없습니다.  
  
 통합 멤버는 엔터티에 명시적 계층 및 컬렉션을 사용할 수 있는 경우에만 존재합니다.  
  
-   파생 계층에는 통합 멤버가 포함되지 않습니다.  
  
-   명시적 계층에서 통합 멤버는 계층 내 다른 멤버의 부모가 되거나 자식이 될 수 있습니다.  
  
## 계층 및 컬렉션을 사용하여 멤버 구성  
 계층과 컬렉션을 사용하여 보고 또는 분석을 위한 멤버를 그룹화할 수 있습니다. 자세한 내용은 [계층&#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md) 및 [컬렉션&#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)을 참조하세요.  
  
## 멤버 예  
 다음 예의 각 멤버는 Name, Code, Subcategory, StandardCost, ListPrice 및 FilePhoto 특성 값으로 구성되어 있습니다.  
  
 ![Bike 제품 엔터티 테이블](../master-data-services/media/mds-conc-entity-table-w-data.gif "Bike 제품 엔터티 테이블")  
  
## 관련 작업  
  
|태스크 설명|항목|  
|----------------------|-----------|  
|새 리프 멤버를 만듭니다.|[리프 멤버 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-leaf-member-master-data-services.md)|  
|새 통합 멤버를 만듭니다.|[통합 멤버 만들기&#40;Master Data Services&#41;](../master-data-services/create-a-consolidated-member-master-data-services.md)|  
|기존 멤버 또는 컬렉션을 삭제합니다.|[멤버 또는 컬렉션 삭제&#40;Master Data Services&#41;](../master-data-services/delete-a-member-or-collection-master-data-services.md)|  
|삭제된 멤버 또는 컬렉션을 다시 활성화합니다.|[멤버 또는 컬렉션 다시 활성화&#40;Master Data Services&#41;](../master-data-services/reactivate-a-member-or-collection-master-data-services.md)|  
|멤버의 속성 값을 업데이트합니다.|[특성 유형 변경&#40;Excel용 MDS 추가 기능&#41;](../master-data-services/microsoft-excel-add-in/change-the-attribute-type-mds-add-in-for-excel.md)|  
|계층 내에서 멤버를 이동합니다.|[계층 내에서 멤버 이동&#40;Master Data Services&#41;](../Topic/Move%20Members%20within%20a%20Hierarchy%20\(Master%20Data%20Services\).md)|  
|병합 충돌을 해결합니다.|[병합 충돌&#40;Master Data Services&#41;](../master-data-services/merge-conflicts-master-data-services.md)|  
  
## 관련 내용  
  
-   [Master Data Services 개요&#40;MDS&#41;](../master-data-services/master-data-services-overview-mds.md)  
  
-   [엔터티&#40;Master Data Services&#41;](../master-data-services/entities-master-data-services.md)  
  
-   [특성&#40;Master Data Services&#41;](../master-data-services/attributes-master-data-services.md)  
  
-   [계층&#40;Master Data Services&#41;](../master-data-services/hierarchies-master-data-services.md)  
  
-   [컬렉션&#40;Master Data Services&#41;](../master-data-services/collections-master-data-services.md)  
  
-   [리프 권한&#40;Master Data Services&#41;](../master-data-services/leaf-permissions-master-data-services.md)  
  
-   [통합 사용 권한&#40;Master Data Services&#41;](../Topic/Consolidated%20Permissions%20\(Master%20Data%20Services\).md)  
  
-   [필터 연산자&#40;Master Data Services&#41;](../master-data-services/filter-operators-master-data-services.md)  
  
  