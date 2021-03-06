---
title: sys.dm_os_workers (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_os_workers_TSQL
- sys.dm_os_workers_TSQL
- dm_os_workers
- sys.dm_os_workers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_workers dynamic management view
ms.assetid: 4d5d1e52-a574-4bdd-87ae-b932527235e8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 9c1e81b333a4f486923478b7a4f3004b7960d3da
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728731"
---
# <a name="sysdmosworkers-transact-sql"></a>sys.dm_os_workers(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  시스템의 각 작업자에 대해 행을 반환합니다.  
  
> [!NOTE]  
>  이를 호출 하 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 나 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], 이름을 사용 하 여 **sys.dm_pdw_nodes_os_workers**합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|worker_address|**varbinary(8)**|작업자의 메모리 주소입니다.|  
|상태|**int**|내부적으로만 사용됩니다.|  
|is_preemptive|**bit**|1 = 작업자가 선점형 일정을 사용하여 실행되고 있습니다. 외부 코드를 실행 중인 작업자는 선점형 일정을 사용하여 실행됩니다.|  
|is_fiber|**bit**|1 = 작업자가 경량 풀링을 사용하여 실행되고 있습니다. 자세한 내용은 이 항목의 뒷부분에 나오는 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)백업 및 복원의 기본적인 백업 미디어 관련 용어를 소개합니다.|  
|is_sick|**bit**|1 = 작업자가 spinlock을 획득하려고 하는 중 멈췄습니다. 이 비트가 설정된 경우 자주 액세스되는 개체에 경합 문제가 있음을 나타내는 것일 수 있습니다.|  
|is_in_cc_exception|**bit**|1 = 작업자가 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 예외가 아닌 다른 예외를 처리하고 있습니다.|  
|is_fatal_exception|**bit**|이 작업자에 치명적인 예외가 발생했는지 지정합니다.|  
|is_inside_catch|**bit**|1 = 작업자가 현재 예외를 처리하고 있습니다.|  
|is_in_polling_io_completion_routine|**bit**|1 = 작업자가 현재 보류 중인 I/O에 대해 I/O 완료 루틴을 실행하고 있습니다. 자세한 내용은 [sys.dm_io_pending_io_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-pending-io-requests-transact-sql.md)합니다.|  
|context_switch_count|**int**|이 작업자가 수행한 스케줄러 컨텍스트 전환 횟수입니다.|  
|pending_io_count|**int**|이 작업자가 수행한 실제 I/O 수입니다.|  
|pending_io_byte_count|**bigint**|이 작업자에 대해 보류 중인 모든 실제 I/O의 총 바이트 수입니다.|  
|pending_io_byte_average|**int**|이 작업자에 대한 실제 I/O의 평균 바이트 수입니다.|  
|wait_started_ms_ticks|**bigint**|특정 시간 내에 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)이 작업 자가 SUSPENDED 상태로 설정 하는 경우. ms_ticks에서이 값을 빼면 [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) 작업자 대기 시간 (밀리초)의 수를 반환 합니다.|  
|wait_resumed_ms_ticks|**bigint**|특정 시간 내에 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)이 작업 자가 RUNNABLE 상태로 들어간 하는 경우. ms_ticks에서이 값을 빼면 [sys.dm_os_sys_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md) 작업자 실행 가능 큐에서 된 밀리초 수를 반환 합니다.|  
|task_bound_ms_ticks|**bigint**|특정 시간 내에 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)이 작업자에 태스크가 바인딩되는 경우.|  
|worker_created_ms_ticks|**bigint**|특정 시간 내에 [ms_ticks](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)자가 생성 되는 경우.|  
|exception_num|**int**|이 작업자에 마지막으로 발생한 예외의 오류 번호입니다.|  
|exception_severity|**int**|이 작업자에 마지막으로 발생한 예외의 심각도입니다.|  
|exception_address|**varbinary(8)**|예외가 발생한 코드 주소입니다.|  
|affinity|**bigint**|작업자의 스레드 선호도입니다. 스레드 선호도 일치 [sys.dm_os_threads &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)합니다.|  
|state|**nvarchar(60)**|작업자 상태입니다. 다음 값 중 하나를 사용할 수 있습니다.<br /><br /> INIT = 작업자가 현재 초기화되고 있습니다.<br /><br /> RUNNING = 작업자가 현재 선점형 모드나 비선점형 모드로 실행되고 있습니다.<br /><br /> RUNNABLE = 스케줄러에서 작업자를 실행할 준비가 되었습니다.<br /><br /> SUSPENDED = 작업자가 현재 일시 중지되어 이벤트에서 신호를 보낼 때까지 기다리고 있습니다.|  
|start_quantum|**bigint**|이 작업자의 현재 실행이 시작된 시간(밀리초)입니다.|  
|end_quantum|**bigint**|이 작업자의 현재 실행이 종료된 시간(밀리초)입니다.|  
|last_wait_type|**nvarchar(60)**|마지막 대기의 유형입니다. 대기 유형 목록은 참조 하세요 [sys.dm_os_wait_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql.md)합니다.|  
|return_code|**int**|마지막 대기에서 반환된 값입니다. 다음 값 중 하나를 사용할 수 있습니다.<br /><br /> 0 = 성공<br /><br /> 3 = 교착<br /><br /> 4 = 중간 시작<br /><br /> 258 = 시간 초과|  
|quantum_used|**bigint**|내부적으로만 사용됩니다.|  
|max_quantum|**bigint**|내부적으로만 사용됩니다.|  
|boost_count|**int**|내부적으로만 사용됩니다.|  
|tasks_processed_count|**int**|이 작업자가 처리한 태스크 수입니다.|  
|fiber_address|**varbinary(8)**|이 작업자와 연관된 파이버의 메모리 주소입니다.<br /><br /> NULL = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 경량 풀링을 사용하도록 구성되지 않았습니다.|  
|task_address|**varbinary(8)**|현재 태스크의 메모리 주소입니다. 자세한 내용은 [sys.dm_os_tasks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)합니다.|  
|memory_object_address|**varbinary(8)**|작업자 메모리 개체의 메모리 주소입니다. 자세한 내용은 [sys.dm_os_memory_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)합니다.|  
|thread_address|**varbinary(8)**|이 작업자와 연관된 스레드의 메모리 주소입니다. 자세한 내용은 [sys.dm_os_threads &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-threads-transact-sql.md)합니다.|  
|signal_worker_address|**varbinary(8)**|이 개체에 마지막으로 신호를 보낸 작업자의 메모리 주소입니다. 자세한 내용은 [sys.dm_os_workers](../../relational-databases/system-dynamic-management-views/sys-dm-os-workers-transact-sql.md)합니다.|  
|scheduler_address|**varbinary(8)**|스케줄러의 메모리 주소입니다. 자세한 내용은 [sys.dm_os_schedulers &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-schedulers-transact-sql.md)합니다.|  
|processor_group|**smallint**|이 스레드에 할당된 프로세서 그룹 ID를 저장합니다.|  
|pdw_node_id|**int**|**적용 대상**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)], [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 이 배포에 있는 노드에 대 한 식별자입니다.|  
  
## <a name="remarks"></a>Remarks  
 작업자 상태가 RUNNING이고 작업자가 비선점형 모드로 실행되고 있으면 작업자 주소가 sys.dm_os_schedulers의 active_worker_address와 일치합니다.  
  
 이벤트를 기다리고 있는 작업자가 신호를 받으면 해당 작업자가 실행 가능한 큐의 맨 처음에 배치됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 이 작업이 연속해서 1,000회 발생할 수 있습니다. 그런 다음 작업자가 큐 끝에 배치됩니다. 작업자를 큐 끝으로 이동하면 성능에 약간 영향을 줍니다.  
  
## <a name="permissions"></a>사용 권한

온 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요한 `VIEW SERVER STATE` 권한.   
온 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], 필요를 `VIEW DATABASE STATE` 데이터베이스의 권한.   

## <a name="examples"></a>예  
 다음 쿼리를 사용하여 SUSPENDED 또는 RUNNABLE 상태에서 작업자가 실행된 시간을 확인할 수 있습니다.  
  
```sql
SELECT   
    t1.session_id,  
    CONVERT(varchar(10), t1.status) AS status,  
    CONVERT(varchar(15), t1.command) AS command,  
    CONVERT(varchar(10), t2.state) AS worker_state,  
    w_suspended =   
      CASE t2.wait_started_ms_ticks  
        WHEN 0 THEN 0  
        ELSE   
          t3.ms_ticks - t2.wait_started_ms_ticks  
      END,  
    w_runnable =   
      CASE t2.wait_resumed_ms_ticks  
        WHEN 0 THEN 0  
        ELSE   
          t3.ms_ticks - t2.wait_resumed_ms_ticks  
      END  
  FROM sys.dm_exec_requests AS t1  
  INNER JOIN sys.dm_os_workers AS t2  
    ON t2.task_address = t1.task_address  
  CROSS JOIN sys.dm_os_sys_info AS t3  
  WHERE t1.scheduler_id IS NOT NULL;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  

```
 session_id status     command         worker_state w_suspended w_runnable  
 ---------- ---------- --------------- ------------ ----------- --------------------  
 4          background LAZY WRITER     SUSPENDED    688         688  
 6          background LOCK MONITOR    SUSPENDED    4657        4657
 19         background BRKR TASK       SUSPENDED    603820344   603820344  
 14         background BRKR EVENT HNDL SUSPENDED    63583641    63583641  
 51         running    SELECT          RUNNING      0           0  
 2          background RESOURCE MONITO RUNNING      0           603825954  
 3          background LAZY WRITER     SUSPENDED    422         422  
 7          background SIGNAL HANDLER  SUSPENDED    603820485   603820485  
 13         background TASK MANAGER    SUSPENDED    603824704   603824704  
 18         background BRKR TASK       SUSPENDED    603820407   603820407  
 9          background TRACE QUEUE TAS SUSPENDED    454         454  
 52         suspended  SELECT          SUSPENDED    35094       35094  
 1          background RESOURCE MONITO RUNNING      0           603825954  
```

 출력에서 `w_runnable`과 `w_suspended`가 같으면 작업자가 SUSPENDED 상태에 있는 시간을 나타냅니다. 그렇지 않으면 `w_runnable`은 작업자가 RUNNABLE 상태에서 소요한 시간을 나타냅니다. 출력에서 세션 `52`는 `SUSPENDED` 밀리초 동안 `35,094`됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server 운영 체제 관련 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


