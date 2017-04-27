---
title: "중복 행 제외(Visual Database Tools) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: bad0e2729b2a0bfa0728d9257194c4adb10a885e
ms.lasthandoff: 04/11/2017

---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>중복 행 제외(Visual Database Tools)
결과 집합에서 중복 행을 제외하도록 지정하면 결과 집합에 고유 값만 표시할 수 있습니다.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>결과 집합에서 중복 행을 제외하려면  
  
1.  다이어그램 창의 배경을 마우스 오른쪽 단추로 클릭한 다음 바로 가기 메뉴에서 **속성** 을 선택합니다.  
  
2.  속성 창에서 **고유 값** 을 클릭하고 값을 **예**로 설정합니다.  
  
    쿼리 및 뷰 디자이너에서 SQL 문의 열 표시 목록 앞에 DISTINCT라는 키워드가 삽입됩니다.  
  
    > [!NOTE]  
    > DISTINCT 키워드를 사용하면 결과 창에서 결과 집합을 수정할 수 없습니다.  
  
## <a name="see-also"></a>관련 항목:  
[검색 조건 지정&amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[쿼리 결과 정렬 및 그룹화&amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  
