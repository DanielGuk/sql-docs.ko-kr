---
title: 트랜잭션 복제를 위한 아티클 옵션 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- articles [SQL Server replication], transactional replication options
- transactional replication, article options
ms.assetid: 3469b185-0ea5-4690-a71c-717230d886b6
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7e003ab7a1928c98e2e4e004d53d71fc001227d7
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48190723"
---
# <a name="article-options-for-transactional-replication"></a>트랜잭션 복제를 위한 아티클 옵션
  트랜잭션 게시의 아티클에는 여러 가지 옵션이 있습니다. 트랜잭션 복제를 사용하여 다음 작업을 수행할 수 있습니다.  
  
-   게시자에서 구독자로 변경 내용이 전파되는 방법을 지정합니다. 자세한 내용은 [트랜잭션 아티클에 대한 변경 내용을 전파하는 방법 지정](transactional-articles-specify-how-changes-are-propagated.md)을 참조하세요.  
  
-   저장 프로시저의 실행 결과를 복제하도록 지정합니다. 이는 많은 데이터에 영향을 주는 유지 관리 관련 저장 프로시저의 결과를 복제할 때 유용합니다. 자세한 내용은 [Publishing Stored Procedure Execution in Transactional Replication](publishing-stored-procedure-execution-in-transactional-replication.md)을(를) 참조하세요.  
  
-   제약 조건 및 트리거를 구독자로 복사할지 여부와 같은 스키마 옵션을 지정합니다. 자세한 내용은 [스키마 옵션 지정](../publish/specify-schema-options.md)을 참조하세요.  
  
-   행 필터와 열 필터를 사용합니다. 테이블 아티클을 필터링하여 게시할 데이터 파티션을 만들 수 있습니다. 자세한 내용은 [게시된 데이터 필터링](../publish/filter-published-data.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터 및 데이터베이스 개체 게시](../publish/publish-data-and-database-objects.md)  
  
  
