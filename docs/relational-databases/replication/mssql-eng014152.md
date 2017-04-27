---
title: "MSSQL_ENG014152 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG014152 오류"
ms.assetid: 4215e2b1-cd30-441f-9671-9afc742adf6e
caps.latest.revision: 11
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 11
---
# MSSQL_ENG014152
    
## 메시지 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|14152|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|심볼 이름||  
|메시지 텍스트|복제-%s: 에이전트 %s이(가) 다시 시도하도록 예약되었습니다. %s|  
  
## 설명  
 지정한 복제 에이전트가 요청한 작업을 다시 시도하도록 예약되었습니다. 작업 단계에 대해 구성된 최대의 다시 시도 횟수에 도달할 때까지 프로세스는 계속해서 작업을 다시 시도합니다.  
  
 일반적으로 다시 시도는 다음 원인 중 하나로 인해 발생합니다.  
  
-   **QueryTimeout** 값이 초과되었습니다.  
  
-   **LoginTimeout** 값이 초과되었습니다.  
  
-   복제 프로세스가 교착 상태에서 처리되지 않았습니다.  
  
## 사용자 동작  
 사용자 동작은 다시 시도 메시지가 빈번하게 표시되는 경우에만 필요합니다.  
  
 사용 하 여 [sp_help_jobstep](../../relational-databases/system-stored-procedures/sp-help-jobstep-transact-sql.md) 최대 다시 시도 횟수에 대 한 현재 설정을 보려면는 **에이전트 실행** 단계 지정한 복제 에이전트가 다시 시도 합니다. 사용할 수는 **@retry_attempts** 의 매개 변수는 [sp_update_jobstep](../../relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql.md) 저장 프로시저는 작업 단계를 다시 시도 횟수를 조정할 수 있습니다.  
  
 다시 시도 메시지가 자주 표시되는 경우 다시 시도를 발생시키는 메시지를 기준으로 문제를 해결합니다. 다시 시도가 예약된 이유를 나타내는 메시지에 대한 에이전트 기록을 확인합니다. 경우에 따라 복제 에이전트에 대해 더 자세한 로깅을 설정해야 합니다. 복제에 대한 로깅을 구성하는 방법은 Microsoft 기술 자료 문서 [312292](http://support.microsoft.com/kb/312292)를 참조하십시오.  
  
## 참고 항목  
 [오류 및 이벤트 참조 & #40입니다. 복제 및 #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  