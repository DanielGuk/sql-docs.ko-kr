---
title: "Stored Procedures 이벤트 범주 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Stored Procedures event category [SQL Server]
- SQL Server event classes, Stored Procedures event category
- event classes [SQL Server], Stored Procedures event category
ms.assetid: 71bebaa3-a05a-4695-b349-078cecd0949a
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f1c72514c72b06b9fea644848df952879619d43c
ms.lasthandoff: 04/11/2017

---
# <a name="stored-procedures-event-category"></a>Stored Procedures 이벤트 범주
  **Stored Procedures** 이벤트 범주는 일반 저장 프로시저 이벤트를 포함합니다.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|설명|  
|-----------|-----------------|  
|[RPC:Completed 이벤트 클래스](../../relational-databases/event-classes/rpc-completed-event-class.md)|RPC(원격 프로시저 호출)가 완료되었음을 나타냅니다.|  
|[PreConnect:Completed 이벤트 클래스](../../relational-databases/event-classes/preconnect-completed-event-class.md)|리소스 관리자의 분류자 함수가 실행을 완료하는 때를 나타냅니다.|  
|[PreConnect:Starting 이벤트 클래스](../../relational-databases/event-classes/preconnect-starting-event-class.md)|리소스 관리자의 분류자 함수가 실행을 시작하는 때를 나타냅니다.|  
|[RPC Output Parameter 이벤트 클래스](../../relational-databases/event-classes/rpc-output-parameter-event-class.md)|실행 후 원격 프로시저 호출의 출력 매개 변수 값을 추적합니다.|  
|[RPC:Starting 이벤트 클래스](../../relational-databases/event-classes/rpc-starting-event-class.md)|원격 프로시저 호출을 시작했음을 나타냅니다.|  
|[SP:CacheHit 이벤트 클래스](../../relational-databases/event-classes/sp-cachehit-event-class.md)|저장 프로시저가 캐시에 있음을 나타냅니다.|  
|[SP:CacheInsert 이벤트 클래스](../../relational-databases/event-classes/sp-cacheinsert-event-class.md)|저장 프로시저를 캐시로 가져왔음을 나타냅니다.|  
|[SP:CacheMiss 이벤트 클래스](../../relational-databases/event-classes/sp-cachemiss-event-class.md)|저장 프로시저가 캐시에 없음을 나타냅니다.|  
|[SP:CacheRemove 이벤트 클래스](../../relational-databases/event-classes/sp-cacheremove-event-class.md)|저장 프로시저가 캐시에서 제거되었음을 나타냅니다.|  
|[SP:Completed 이벤트 클래스](../../relational-databases/event-classes/sp-completed-event-class.md)|저장 프로시저 실행이 완료되었음을 나타냅니다.|  
|[SP:Recompile 이벤트 클래스](../../relational-databases/event-classes/sp-recompile-event-class.md)|저장 프로시저가 다시 컴파일되었음을 나타냅니다.|  
|[SP:Starting 이벤트 클래스](../../relational-databases/event-classes/sp-starting-event-class.md)|저장 프로시저 실행을 시작했음을 나타냅니다.|  
|[SP:StmtCompleted 이벤트 클래스](../../relational-databases/event-classes/sp-stmtcompleted-event-class.md)|저장 프로시저 내의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 완료했음을 나타냅니다.|  
|[SP:StmtStarting 이벤트 클래스](../../relational-databases/event-classes/sp-stmtstarting-event-class.md)|저장 프로시저 내의 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 시작했음을 나타냅니다.|  
  
## <a name="see-also"></a>참고 항목  
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  