---
title: "기본적으로 해제되어 있는 기능(Analysis Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a9529edf-337e-4fdd-9a13-99cfe96b4fa1
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# 기본적으로 해제되어 있는 기능(Analysis Services)
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 기본적으로 보안되도록 디자인되었습니다. 따라서 보안을 손상시킬 수 있는 기능은 기본적으로 비활성화됩니다. 다음 기능은 기본적으로 비활성화된 상태로 설치되며 이러한 기능을 사용하려면 별도로 활성화해야 합니다.  
  
## 기능 목록  
 다음 기능을 활성화하려면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 연결합니다. 인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 **패싯**을 선택합니다. 또는 다음 섹션에 설명된 것처럼 서버 속성을 통해 이러한 기능을 활성화할 수 있습니다.  
  
-   임시 데이터 마이닝(OpenRowset) 쿼리  
  
-   연결된 개체(대상)  
  
-   연결된 개체(원본)  
  
-   로컬 연결에서만 수신  
  
-   사용자 정의 함수  
  
## 서버 속성  
 기본적으로 해제되어 있는 추가 기능은 서버 속성을 통해 활성화할 수 있습니다. [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에 연결합니다. 인스턴스 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다. **일반**을 클릭한 다음 **고급 표시** 를 클릭하여 더 많은 속성 목록을 표시합니다.  
  
-   임시 데이터 마이닝(OpenRowset) 쿼리  
  
-   세션 마이닝 모델 허용(데이터 마이닝)  
  
-   연결된 개체(대상)  
  
-   연결된 개체(원본)  
  
-   COM 기반 사용자 정의 함수  
  
-   비행 레코더 추적 정의(템플릿)  
  
-   쿼리 로깅  
  
-   로컬 연결에서만 수신  
  
-   이진 XML  
  
-   압축  
  
-   그룹 선호도. 자세한 내용은 [Thread Pool Properties](../../analysis-services/server-properties/thread-pool-properties.md) 를 참조하세요.  
  
  