---
title: Blocked Process Report 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Blocked Process Report event class
ms.assetid: e8acb408-938d-4b36-81dd-04f087410cc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2aecd264eac2a6beada1009ae070f1858dd6822c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48141033"
---
# <a name="blocked-process-report-event-class"></a>Blocked Process Report 이벤트 클래스
  **Blocked Process Report** 이벤트 클래스는 태스크가 지정된 시간보다 오래 차단되어 있음을 나타냅니다. 이 이벤트 클래스는 교착 상태를 감지할 수 없는 리소스에서 대기하는 작업 또는 시스템 태스크는 포함하지 않습니다.  
  
 보고서 생성의 임계값 및 빈도를 구성하려면 **sp_configure** 명령을 사용하여 **blocked process threshold** 옵션을 초 단위로 구성하세요. 기본적으로 차단된 프로세스 보고서는 생성되지 않습니다. **차단된 프로세스 임계값** 설정 옵션에 대한 자세한 내용은 [차단된 프로세스 임계값 서버 구성 옵션](../../database-engine/configure-windows/blocked-process-threshold-server-configuration-option.md)을 참조하세요.  
  
 **Blocked Process Report** 이벤트 클래스에서 반환된 데이터 필터링에 대한 자세한 내용은 [추적에서의 이벤트 필터링&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md), [추적 필터 설정&#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md) 또는 [sp_trace_setfilter&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql)를 참조하세요.  
  
## <a name="blocked-process-report-event-class-data-columns"></a>Blocked Process Report 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|잠금을 획득한 데이터베이스의 ID입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ServerName **데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면** 에 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|**기간**|**bigint**|프로세스가 차단된 시간(밀리초)입니다.|13|사용자 계정 컨트롤|  
|**EndTime**|**datetime**|이벤트가 종료된 시간입니다. 이 열은 **SQL:BatchStarting** 또는 **SP:Starting**과 같은 시작하는 이벤트 클래스의 경우 채워지지 않습니다.|15|사용자 계정 컨트롤|  
|**EventClass**|**int**|이벤트 유형 = 137|27|아니요|  
|**EventSequence**|**int**|요청 내의 지정된 이벤트 시퀀스입니다.|51|아니요|  
|**IndexID**|**int**|이벤트에 의해 영향 받는 개체의 인덱스 ID입니다. 개체의 인덱스 ID를 확인하려면 **sysindexes** 시스템 테이블의 **indid** 열을 사용하십시오.|24|사용자 계정 컨트롤|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|사용자 계정 컨트롤|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 이벤트는 항상 시스템 스레드에서 보고됩니다. IsSystem = 1; SID = sa|41|사용자 계정 컨트롤|  
|**모드**|**int**|이벤트가 수신했거나 요청 중인 상태입니다.<br /><br /> 0=NULL<br /><br /> 1=Sch-S<br /><br /> 2=Sch-M<br /><br /> 3=S<br /><br /> 4=U<br /><br /> 5=X<br /><br /> 6=IS<br /><br /> 7=IU<br /><br /> 8=IX<br /><br /> 9=SIU<br /><br /> 10=SIX<br /><br /> 11=UIX<br /><br /> 12=BU<br /><br /> 13=RangeS-S<br /><br /> 14=RangeS-U<br /><br /> 15=RangeI-N<br /><br /> 16=RangeI-S<br /><br /> 17=RangeI-U<br /><br /> 18=RangeI-X<br /><br /> 19=RangeX-S<br /><br /> 20=RangeX-U<br /><br /> 21=RangeX-X|32|사용자 계정 컨트롤|  
|**Exchange Spill**|**int**|잠금을 획득한 개체에 시스템이 할당한 ID입니다(사용 가능하고 필요한 경우).|22|사용자 계정 컨트롤|  
|**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26||  
|**SessionLoginName**|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 SQL Server에 연결하고 Login2로 문을 실행할 경우 **SessionLoginName** 은 Login1을 표시하고 **LoginName** 은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|사용자 계정 컨트롤|  
|**TextData**|**ntext**|추적에서 캡처된 이벤트 클래스에 따라 달라지는 텍스트 값입니다.|1|사용자 계정 컨트롤|  
|**TransactionID**|**bigint**|시스템이 할당한 트랜잭션의 ID입니다.|4|사용자 계정 컨트롤|  
  
## <a name="see-also"></a>관련 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
