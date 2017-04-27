---
title: "MSSQL_ENG014121 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG014121 error
ms.assetid: c8595854-cce1-4566-ad64-d565555caded
caps.latest.revision: 13
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2a8972728183fff1e679063cf48e1e20cd7b5089
ms.lasthandoff: 04/11/2017

---
# <a name="mssqleng014121"></a>MSSQL_ENG014121
    
## <a name="message-details"></a>메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|14121|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|배포자 '%s'을(를) 삭제할 수 없습니다. 이 배포자가 배포 데이터베이스와 연관되어 있습니다.|  
  
## <a name="explanation"></a>설명  
 배포자로 구성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스와 연결된 배포 데이터베이스가 있으므로 해당 인스턴스를 배포자 역할에서 제거할 수 없습니다. 이 오류는 하나 이상의 게시자와 연결된 배포 데이터베이스를 삭제하려고 할 때 발생합니다.  
  
## <a name="user-action"></a>사용자 동작  
 이 배포자와 연결된 게시자 및 배포 데이터베이스의 이름을 찾으려면 배포자의 데이터베이스에서 [sp_helpdistpublisher&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistpublisher-transact-sql.md)를 실행합니다.  
  
 이 배포자와 연결된 배포 데이터베이스에 대해 [sp_dropdistributiondb&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)를 실행합니다. 모든 배포 데이터베이스 연결을 제거한 다음 배포를 해제할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [오류 및 이벤트 참조&#40;복제&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [배포 구성](../../relational-databases/replication/configure-distribution.md)  
  
  