---
title: 사용자 데이터베이스에 대한 게스트 사용 권한 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 540f1c6d-df51-497e-958a-3a0f429d2920
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ee463adbdcd90d9454cd995e1c1bc52e45988fe2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071963"
---
# <a name="guest-permissions-on-user-databases"></a>사용자 데이터베이스에 대한 게스트 사용 권한
  이 규칙은 게스트 사용자에게 데이터베이스에 대한 액세스 권한이 있는지 확인합니다. 이 규칙은 사용자 데이터베이스에만 적용됩니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 필요한 경우가 아니라면 게스트 사용자의 데이터베이스 액세스 권한을 취소합니다.  
  
 guest 사용자는 삭제할 수 없지만 master, tempdb 또는 msdb 이외의 데이터베이스 내에서 REVOKE CONNECT FROM GUEST를 실행하면 guest 사용자의 CONNECT 권한이 취소되므로 사용할 수 없게 됩니다.  
  
## <a name="for-more-information"></a>참조 항목  
 [SQL Server 보안 설정](../security/securing-sql-server.md)  
  
## <a name="see-also"></a>관련 항목  
 [정책 기반 관리를 사용하여 최선의 방법 모니터링 및 적용](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
