---
title: "SQL Server 에이전트, Alerts 개체 | Microsoft 문서"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Alerts object
- SQLAgent:Alerts
ms.assetid: e5e37f74-ee88-46d0-ad8f-71fd1b1fa64a
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4b477d24172655ff459136bab58af76b5a542f1b
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-agent-alerts-object"></a>SQL Server 에이전트, Alerts 개체
  SQL Server 에이전트 **Alerts** 성능 개체는 SQL Server 에이전트 경고에 대한 정보를 보고하는 성능 카운터를 포함합니다. 다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.  
  
 다음 표에서는 **SQLAgent:Alerts** 카운터를 나열합니다.  
  
|이름|설명|  
|----------|-----------------|  
|**Activated alerts**|이 카운터는 SQL Server 에이전트가 마지막으로 다시 시작된 이후 SQL Server 에이전트가 활성화한 총 경고 수를 보고합니다.|  
|**Alerts activated/minute**|이 카운터는 마지막 시간(분) 내에 SQL Server 에이전트가 활성화한 경고의 수를 보고합니다.|  
  
> [!NOTE]  
>  이 SQL Server 에이전트 개체를 사용하려면 **sysadmin** 고정 서버 역할의 멤버여야 합니다.  
  
## <a name="see-also"></a>참고 항목  
 [Alerts](http://msdn.microsoft.com/library/3f57d0f0-4781-46ec-82cd-b751dc5affef)   
 [성능 개체 사용](http://msdn.microsoft.com/library/830b843a-6b2a-4620-a51b-98358e9fc54b)   
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  