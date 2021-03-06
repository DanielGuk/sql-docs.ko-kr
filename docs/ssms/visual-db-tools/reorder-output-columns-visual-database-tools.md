---
title: 출력 열 다시 정렬(Visual Database Tools) | Microsoft 문서
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 68898742ad340c648414614cde8741157f814221
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47806019"
---
# <a name="reorder-output-columns-visual-database-tools"></a>출력 열 다시 정렬(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
출력 열이 결과에 표시되는 순서는 선택 쿼리에 데이터 열을 추가하는 순서에 따라 결정됩니다. 쿼리에 추가하는 첫 번째 열은 결과의 가장 왼쪽에 나타나고 두 번째 열은 그 다음에 나타나는 방식입니다.  
  
업데이트 쿼리나 삽입 쿼리를 만드는 경우 열을 추가하는 순서는 데이터가 처리되는 순서에 영향을 줍니다.  
  
열의 순서를 바꾸면 결과 집합에 데이터 열이 나타나는 위치나 데이터 열이 사용되는 순서를 제어할 수 있습니다.  
  
### <a name="to-reorder-columns-for-output"></a>출력 열의 순서를 바꾸려면  
  
1.  [조건 창](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)에서 행의 왼쪽에 있는 행 선택기 단추를 클릭하여 열이 포함된 행을 선택합니다.  
  
2.  행 선택기 단추를 가리키고 행을 새 위치에 끌어 옵니다.  
  
    -또는-  
  
    [SQL 창](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)에서 열 이름의 순서를 편집합니다.  
  
> [!TIP]  
> 조건 창에 빈 행을 삽입한 다음 삽입할 데이터 열을 지정하여 조건 창의 특정 위치에 데이터 행을 추가할 수 있습니다. 자세한 내용은 [쿼리에 열 추가&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[쿼리 결과 정렬 및 그룹화&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[쿼리 결과 요약&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[쿼리 관련 기본 작업 수행&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
