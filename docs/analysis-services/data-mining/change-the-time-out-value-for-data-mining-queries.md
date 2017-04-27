---
title: "데이터 마이닝 쿼리에 대한 제한 시간 값 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "제한 시간"
ms.assetid: f1add4bc-e882-440a-a98b-333cfa274c3e
caps.latest.revision: 12
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 12
---
# 데이터 마이닝 쿼리에 대한 제한 시간 값 변경
  리프트 차트를 작성하거나 예측 쿼리를 실행할 때 예측에 필요한 모든 데이터를 생성하는 데 많은 시간이 소요될 수 있습니다. 쿼리가 제한 시간을 초과하지 않도록 하려면 쿼리를 완료할 때까지 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 서버가 기다리는 시간을 제어하는 값을 변경하면 됩니다.  
  
 기본값은 15이지만 모델이 복잡하거나 데이터 원본이 크면 이 시간이 충분하지 않을 수도 있습니다. 필요에 따라 처리 시간이 충분하도록 값을 많이 늘릴 수 있습니다. 예를 들어 **쿼리 제한 시간** 을 600으로 설정하면 최대 10분 동안 쿼리가 계속 실행될 수 있습니다.  
  
 예측 쿼리에 대한 자세한 내용은 [데이터 마이닝 쿼리 태스크 및 방법](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)을 참조하세요.  
  
### 데이터 마이닝 쿼리에 대한 제한 시간 값 구성  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]의 **도구** 메뉴에서 **옵션**을 선택합니다.  
  
2.  **옵션** 창에서 **비즈니스 인텔리전스 디자이너**를 확장합니다.  
  
3.  **쿼리 제한 시간** 입력란을 클릭하고 시간(초) 값을 입력합니다.  
  
## 관련 항목:  
 [데이터 마이닝 쿼리 태스크 및 방법](../../analysis-services/data-mining/data-mining-query-tasks-and-how-tos.md)   
 [데이터 마이닝 쿼리](../../analysis-services/data-mining/data-mining-queries.md)  
  
  