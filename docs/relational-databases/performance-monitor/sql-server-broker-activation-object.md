---
title: "SQL Server, Broker Activation 개체 | Microsoft 문서"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Broker Activation
- Broker Activation object
ms.assetid: cd9b6880-c924-42c7-b333-09c303317c0b
caps.latest.revision: 20
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 98c72781fdd1532c683bc918221b22a77c419f12
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-broker-activation-object"></a>SQL Server, Broker 활성화 개체
  **SQLServer:BrokerActivation** 성능 개체에는 저장 프로시저 활성화에 대한 정보를 보고하는 성능 카운터가 포함되어 있습니다. 다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.  
  
|SQL Server, Broker 활성화 카운터|설명|  
|-------------------------------------------|-----------------|  
|**Stored Procedures Invoked/sec**|이 카운터는 인스턴스의 모든 큐 모니터에서 호출하는 초당 총 활성화 저장 프로시저 수를 보고합니다.|  
|**Task Limit Reached**|이 카운터는 큐 모니터가 새 태스크를 시작했지만 해당 큐에 대한 최대 수의 작업이 이미 실행 중이기 때문에 시작하지 못한 총 횟수를 보고합니다.|  
|**Task Limit Reached/sec**|이 카운터는 큐 모니터가 새 태스크를 시작했지만 해당 큐에 대한 최대 수의 작업이 이미 실행 중이기 때문에 시작하지 못한 초당 횟수를 보고합니다.|  
|**Tasks Aborted/sec**|이 카운터는 오류로 인해 종료되거나 메시지를 받는 데 실패하여 큐 모니터에서 중단시킨 활성화 저장 프로시저 태스크 수를 보고합니다.|  
|**Tasks Running**|이 카운터는 현재 실행 중인 활성화 저장 프로시저 수를 보고합니다.|  
|**Tasks Started/sec**|이 카운터는 인스턴스의 모든 큐 모니터에서 시작하는 초당 활성화 저장 프로시저 수를 보고합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [sys.dm_broker_activated_tasks&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-activated-tasks-transact-sql.md)   
 [sys.dm_broker_queue_monitors&#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-broker-queue-monitors-transact-sql.md)   
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  