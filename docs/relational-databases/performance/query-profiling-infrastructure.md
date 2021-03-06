---
title: 쿼리 프로파일링 인프라 | Microsoft Docs
ms.custom: ''
ms.date: 11/26/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual - "query plans [SQL Server]" - "execution plans [SQL Server]" - "query profiling" - "lightweight query profiling" - "lightweight profiling" - "lwp"
ms.assetid: 07f8f594-75b4-4591-8c29-d63811d7753e
author: pmasl
ms.author: pelopes
manager: amitban
ms.openlocfilehash: e0ee0bc2c99d997d6a44d5ca0e9944e0ae4bfeb3
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617253"
---
# <a name="query-profiling-infrastructure"></a>쿼리 프로파일링 인프라
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]은 쿼리 실행 계획에 대한 런타임 정보에 액세스하는 기능을 제공합니다. 성능 문제가 발생할 때 가장 중요한 작업 중 하나는 실행 중인 워크로드와 리소스 사용량의 변화를 정확하게 이해하는 것입니다. 이를 위해 [실제 실행 계획](../../relational-databases/performance/display-an-actual-execution-plan.md)에 액세스하는 것이 중요합니다.

실제 쿼리 계획의 가용성을 확보하려면 반드시 쿼리를 완료해야 하지만, [활성 쿼리 통계](../../relational-databases/performance/live-query-statistics.md)는 한 [쿼리 계획 연산자](../../relational-databases/showplan-logical-and-physical-operators-reference.md)에서 다른 쿼리 계획 연산자로 데이터가 흐를 때 실시간 인사이트를 제공할 수 있습니다. 활성 쿼리 계획은 전체 쿼리 진행률 및 생성된 행 수, 경과 시간, 연산자 진행률 등과 같은 연산자 수준의 런타임 실행 통계를 표시합니다. 이 데이터는 쿼리가 완료될 때까지 기다릴 필요 없이 실시간으로 사용할 수 있으므로 이 실행 통계는 오래 실행되는 쿼리, 무한히 실행되어 결코 완료되지 않는 쿼리 등의 쿼리 성능 문제를 디버깅할 때 매우 유용합니다.

## <a name="the-standard-query-execution-statistics-profiling-infrastructure"></a>표준 쿼리 실행 통계 프로파일링 인프라

*쿼리 실행 통계 프로필 인프라* 또는 표준 프로파일링을 사용하도록 설정하여 실행 계획, 즉, 행 수, CPU 및 I/O 사용량에 대한 정보를 수집해야 합니다. **대상 세션**에 대한 실행 계획 정보를 수집하는 다음 방법은 표준 프로파일링 인프라를 활용합니다.

- [SET STATISTICS XML](../../t-sql/statements/set-statistics-xml-transact-sql.md) 
- [SET STATISTICS PROFILE](../../t-sql/statements/set-statistics-profile-transact-sql.md)
- [활성 쿼리 통계](../../relational-databases/performance/live-query-statistics.md)

> [!NOTE]
> [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]를 사용하는 활성 쿼리 통계는 표준 프로파일링 인프라를 활용합니다.    
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 상위 버전에서는 [간단한 프로파일링 인프라](#lwp)를 사용하도록 설정하면 표준 프로파일링 대신 활성 쿼리 통계에서 활용됩니다.

**모든 세션**에 대한 실행 계획 정보를 전역적으로 수집하는 다음 방법은 표준 프로파일링 인프라를 활용합니다.

-  ***query_post_execution_showplan*** 확장 이벤트. 확장 이벤트를 사용하도록 설정하려면 [Monitor System Activity Using Extended Events](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)을 참조하세요.  
- [SQL 추적](../../relational-databases/sql-trace/sql-trace.md) 및 [SQL Server 프로파일러](../../tools/sql-server-profiler/sql-server-profiler.md)의 **Showplan XML** 추적 이벤트. 이 추적 이벤트에 대한 자세한 내용은 [Showplan XML 이벤트 클래스](../../relational-databases/event-classes/showplan-xml-event-class.md)를 참조하세요.

*query_post_execution_showplan* 이벤트를 사용하는 확장 이벤트 세션을 실행하면 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) DMV도 채워지며, 따라서 [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md)를 사용하여 또는 DMV를 직접 쿼리하여 모든 세션에 활성 쿼리 통계를 사용할 수 있습니다. 자세한 내용은 [Live Query Statistics](../../relational-databases/performance/live-query-statistics.md)를 참조하세요.

## <a name="lwp"></a> 간단한 쿼리 실행 통계 프로파일링 인프라

[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 및 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]부터 새로운 *간단한 쿼리 실행 통계 프로파일링 인프라* 또는 **간단한 프로파일링**이 도입되었습니다. 

> [!NOTE]
> 고유하게 컴파일된 저장 프로시저는 간단한 프로파일링에서 지원되지 않습니다.  

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v1"></a>간단한 쿼리 실행 통계 프로파일링 인프라 v1

**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 ~ [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]). 
  
[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2 및 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]부터는 간단한 프로파일링을 도입하여 실행 계획에 대한 정보를 수집하는 성능 오버헤드를 줄였습니다. 표준 프로파일링과는 달리, 간단한 프로파일링에서 CPU 런타임 정보를 수집하지 않습니다. 그러나 간단한 프로파일링에서는 여전히 행 수 및 I/O 사용 정보를 수집합니다.

간단한 프로파일링을 활용하는 새 ***query_thread_profile*** 확장 이벤트도 도입되었습니다. 이 확장 이벤트는 연산자별 실행 통계를 표시하므로 각 노드 및 스레드의 성능을 자세히 파악할 수 있습니다. 이 확장 이벤트를 사용하는 샘플 세션을 아래 예제처럼 구성할 수 있습니다.

```sql
CREATE EVENT SESSION [NodePerfStats] ON SERVER
ADD EVENT sqlserver.query_thread_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

> [!NOTE]
> 쿼리 프로파일링의 성능 오버헤드에 자세한 내용은 [개발자 선택 사항: 쿼리 진행률 - 언제, 어디서나](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) 블로그 게시물을 참조하세요. 

*query_thread_profile* 이벤트를 사용하는 확장 이벤트 세션을 실행하면 간단한 프로파일링을 사용하여 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md) DMV도 채워지며, 따라서 [Activity Monitor](../../relational-databases/performance-monitor/activity-monitor.md)를 사용하여 또는 DMV를 직접 쿼리하여 모든 세션에 활성 쿼리 통계를 사용할 수 있습니다.

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v2"></a>간단한 쿼리 실행 통계 프로파일링 인프라 v2

**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 ~ [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]). 

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1에는 오버헤드를 최소화하도록 수정된 버전의 간단한 프로파일링이 포함되어 있습니다. 위의 *적용 대상*에 언급된 버전의 [추적 플래그 7412](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)를 사용하여 간단한 프로파일링을 전역적으로 사용할 수도 있습니다. 새 DMF [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)은 진행 중인 요청에 대한 쿼리 실행 계획을 반환하기 위해 도입되었습니다.

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP2 CU3 및 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU11부터는 간단한 프로파일링이 전역적으로 사용되지 않으면 새 [USE HINT 쿼리 힌트](../../t-sql/queries/hints-transact-sql-query.md#use_hint) 인수 **QUERY_PLAN_PROFILE**을 사용하여 쿼리 수준에서, 모든 세션에 간단한 프로파일링을 사용하도록 설정할 수 있습니다. 이 새 힌트를 포함하는 쿼리가 완료되면 *query_post_execution_showplan* 확장 이벤트와 마찬가지로 실제 실행 계획 XML을 제공하는 새 ***query_plan_profile*** 확장 이벤트도 출력됩니다. 이 확장 이벤트를 사용하는 샘플 세션을 아래 예제처럼 구성할 수 있습니다.

```sql
CREATE EVENT SESSION [PerfStats_LWP_Plan] ON SERVER
ADD EVENT sqlserver.query_plan_profile(
  ACTION(sqlos.scheduler_id,sqlserver.database_id,sqlserver.is_system,
    sqlserver.plan_handle,sqlserver.query_hash_signed,sqlserver.query_plan_hash_signed,
    sqlserver.server_instance_name,sqlserver.session_id,sqlserver.session_nt_username,
    sqlserver.sql_text))
ADD TARGET package0.ring_buffer(SET max_memory=(25600))
WITH (MAX_MEMORY=4096 KB,
  EVENT_RETENTION_MODE=ALLOW_SINGLE_EVENT_LOSS,
  MAX_DISPATCH_LATENCY=30 SECONDS,
  MAX_EVENT_SIZE=0 KB,
  MEMORY_PARTITION_MODE=NONE,
  TRACK_CAUSALITY=OFF,
  STARTUP_STATE=OFF);
```

### <a name="lightweight-query-execution-statistics-profiling-infrastructure-v3"></a>간단한 쿼리 실행 통계 프로파일링 인프라 v3

**적용 대상**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]부터)

[!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]에는 모든 실행의 행 수 정보를 수집하는 수정된 버전의 간단한 프로파일링이 포함되어 있습니다. 기본적으로 [!INCLUDE[sql-server-2019](../../includes/sssqlv15-md.md)]에서 간단한 프로파일링이 사용되며 추적 플래그 7412는 영향을 주지 않습니다.

## <a name="remarks"></a>Remarks

> [!IMPORTANT]
> [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)을 참조하는 저장 프로시저를 모니터링하는 동안 임의 AV가 발생할 수 있으므로 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 및 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]에 [KB 4078596](http://support.microsoft.com/help/4078596)을 설치해야 합니다.

오버헤드가 적은 간단한 프로파일링 v2부터는 아직 CPU의 제약을 받지 않는 모든 서버는 간단한 프로파일링을 **지속적으로** 실행할 수 있으며, 데이터베이스 전문가는 언제든지 진행 중인 실행으로 이동할 수 있습니다. 예를 들어 Activity Monitor를 사용하여 또는 `sys.dm_exec_query_profiles`를 직접 쿼리하여 런타임 통계가 포함된 쿼리 계획을 가져올 수 있습니다.

쿼리 프로파일링의 성능 오버헤드에 자세한 내용은 [개발자 선택 사항: 쿼리 진행률 - 언제, 어디서나](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/) 블로그 게시물을 참조하세요. 

## <a name="see-also"></a>참고 항목  
 [성능 모니터링 및 튜닝](../../relational-databases/performance/monitor-and-tune-for-performance.md)     
 [성능 모니터링 및 튜닝 도구](../../relational-databases/performance/performance-monitoring-and-tuning-tools.md)     
 [작업 모니터 열기&#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)     
 [작업 모니터](../../relational-databases/performance-monitor/activity-monitor.md)     
 [관련된 뷰, 함수 및 프로시저](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)     
 [확장 이벤트를 사용하여 시스템 작업 모니터링](../../relational-databases/extended-events/monitor-system-activity-using-extended-events.md)      
 [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md)     
 [sys.dm_exec_query_profiles](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-profiles-transact-sql.md)     
 [추적 플래그](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)    
 [실행 계획 논리 및 물리 연산자 참조](../../relational-databases/showplan-logical-and-physical-operators-reference.md)    
 [실제 실행 모드](../../relational-databases/performance/display-an-actual-execution-plan.md)    
 [활성 쿼리 통계](../../relational-databases/performance/live-query-statistics.md)      
 [개발자 선택 사항: 쿼리 진행률 - 언제, 어디서나](https://blogs.msdn.microsoft.com/sql_server_team/query-progress-anytime-anywhere/)
