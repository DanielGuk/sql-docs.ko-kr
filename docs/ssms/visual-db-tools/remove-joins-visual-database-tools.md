---
title: "조인 제거(Visual Database Tools) | Microsoft 문서"
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
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 6c7c9503f8b2edd9dce534e2c7a4caed659add86
ms.lasthandoff: 04/11/2017

---
# <a name="remove-joins-visual-database-tools"></a>조인 제거(Visual Database Tools)
내부 조인 또는 외부 조인을 통해 테이블을 더 이상 조인하지 않으려면 테이블 간의 조인을 제거하면 됩니다. 예를 들어 [쿼리 및 뷰 디자이너](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) 가 두 테이블 간에 자동으로 만든 조인을 제거할 수 있습니다.  
  
> [!NOTE]  
> 쿼리에서 조인을 제거해도 데이터베이스에서의 기본 관계는 변경되지 않습니다.  
  
조인된 두 테이블이 쿼리의 일부인 경우 이 테이블 간의 조인 조건을 모두 제거하면 그 결과 쿼리는 두 테이블 모두의 산물이 됩니다. 즉, CROSS JOIN이 됩니다.  
  
### <a name="to-remove-a-join"></a>조인을 제거하려면  
  
-   [다이어그램 창](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)에서 제거할 조인의 조인 선을 선택한 다음 Delete 키를 누릅니다. 한 번에 조인 선을 여러 개 선택하여 삭제할 수 있습니다.  
  
쿼리 및 뷰 디자이너는 조인 선을 제거하고 [SQL 창](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)에서 문을 변경합니다.  
  
## <a name="see-also"></a>참고 항목  
[테이블 자동 조인&amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[테이블 수동 조인&amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[조인을 사용한 쿼리&amp;#40;Visual Database Tools&amp;#41;](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  
