---
title: "다른 팩트 테이블을 사용하도록 파티션 원본 변경 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "팩트 테이블 [Analysis Services]"
  - "파티션 [Analysis Services], 팩트 테이블"
ms.assetid: 5508312f-8e46-4802-9362-6688ca03d098
caps.latest.revision: 29
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 29
---
# 다른 팩트 테이블을 사용하도록 파티션 원본 변경
  큐브에 대한 파티션을 만들 때 다양한 팩트 테이블을 사용하도록 선택할 수 있습니다. 이러한 테이블은 단일 데이터 원본 뷰, 여러 개의 데이터 원본 뷰 또는 여러 개의 데이터 원본에서 가져온 테이블일 수 있습니다. 데이터 원본 뷰에는 둘 이상의 데이터 원본에서 가져온 여러 테이블이 포함될 수도 있습니다.  
  
 큐브의 파티션에 대한 모든 팩트 테이블 및 차원은 해당 큐브의 팩트 테이블 및 차원과 구조가 동일해야 합니다. 예를 들어 서로 다른 팩트 테이블이 구조는 같지만 서로 다른 연도나 제품 라인에 대한 데이터를 포함할 수 있습니다.  
  
 파티션 마법사의 **원본 정보 지정** 페이지에서 팩트 테이블을 지정합니다. 이 페이지의 **찾는 위치**옆의 파티션 원본 그룹에서 찾을 위치로 데이터 원본 또는 데이터 원본 뷰를 지정합니다. 다음으로 **테이블 찾기**를 클릭한 다음 **사용 가능한 테이블**에서 사용할 테이블을 선택합니다.  
  
 여러 팩트 테이블을 사용하는 경우 파티션 간에 데이터가 중복되지 않도록 합니다. 예를 들어 특정 팩트 테이블에는 2012년의 트랜잭션만 포함되고 다른 팩트 테이블에는 2013년의 트랜잭션만 포함되는 경우 두 테이블의 데이터는 서로 독립적입니다. 마찬가지로 특정 제품 라인 또는 지리적인 특정 영역에 대한 팩트 테이블도 서로 독립적입니다.  
  
 중복 데이터가 포함된 여러 개의 서로 다른 팩트 테이블을 사용할 수는 있지만 권장하지는 않습니다. 이러한 경우에는 파티션에서 필터를 사용하여 한 파티션에서 사용되는 데이터가 다른 어떤 파티션에서도 사용되지 않게 해야 합니다. 자세한 내용은 [로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)를 참조하세요.  
  
## 관련 항목:  
 [로컬 파티션 만들기 및 관리&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/create-and-manage-a-local-partition-analysis-services.md)  
  
  