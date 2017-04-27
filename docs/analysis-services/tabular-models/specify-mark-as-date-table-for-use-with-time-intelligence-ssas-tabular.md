---
title: "시간 인텔리전스에 사용할 날짜 테이블로 표시 지정(SSAS 테이블 형식) | Microsoft Docs"
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
ms.assetid: 30841d1f-0c3b-4575-8f4a-27a1492e248c
caps.latest.revision: 5
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 5
---
# 시간 인텔리전스에 사용할 날짜 테이블로 표시 지정(SSAS 테이블 형식)
  DAX 수식에 시간 인텔리전스 함수를 사용하려면 날짜 테이블 및 날짜 데이터 형식의 고유 식별자(datetime) 열을 지정해야 합니다. 날짜 테이블의 열을 고유 식별자로 지정한 후에는 날짜 테이블과 임의의 팩트 테이블에 있는 열 간에 관계를 만들 수 있습니다.  
  
 시간 인텔리전스 함수를 사용할 때는 다음 규칙이 적용됩니다.  
  
-   DAX 시간 인텔리전스 함수를 사용할 때는 팩트 테이블에서 datetime 열을 지정하면 안 됩니다. 항상 날짜 데이터 형식의 datetime 열 하나 이상과 고유 값이 포함된 별도의 날짜 테이블을 모델에 만드십시오.  
  
-   날짜 테이블에 연속 날짜 범위가 있는지 확인하십시오.  
  
-   날짜 테이블의 datetime 열은 세분성이 하루여야 하며 더 세부적으로 나뉘지 않아야 합니다.  
  
-   **날짜 테이블로 표시** 대화 상자를 사용하여 날짜 테이블 및 고유 식별자 열을 지정해야 합니다.  
  
-   팩트 테이블 및 날짜 테이블에 있는 날짜 데이터 형식의 열 간에 관계를 만드십시오.  
  
#### 날짜 테이블 및 고유 식별자를 지정하려면  
  
1.  모델 디자이너에서 날짜 테이블을 클릭합니다.  
  
2.   **테이블** 메뉴를 클릭한 다음 **날짜**, **Mark as 날짜 테이블**를 차례로 클릭합니다.  
  
3.  **날짜 테이블로 표시** 대화 상자의 **날짜** 목록 상자에서 고유 식별자로 사용할 열을 선택합니다. 이 열은 고유 값을 포함해야 하며 날짜 데이터 형식이어야 합니다. 예를 들어  
  
    |날짜|  
    |----------|  
    |2010/7/1 오전 12:00:00|  
    |2010/7/2 오전 12:00:00|  
    |2010/7/3 오전 12:00:00|  
    |2010/7/4 오전 12:00:00|  
    |2010/7/5 오전 12:00:00|  
  
4.  필요한 경우 팩트 테이블과 날짜 테이블 간에 관계를 만듭니다.  
  
## 관련 항목:  
 [계산&#40;SSAS 테이블 형식&#41;](../../analysis-services/tabular-models/calculations-ssas-tabular.md)   
 [시간 인텔리전스 함수(DAX)](http://msdn.microsoft.com/ko-kr/91df278d-4b28-40c1-a572-cdb91f081517)  
  
  