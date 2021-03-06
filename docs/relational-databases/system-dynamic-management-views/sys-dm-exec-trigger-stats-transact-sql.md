---
title: sys.dm_exec_trigger_stats (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_trigger_stats
- dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats_TSQL
- sys.dm_exec_trigger_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_trigger_stats dynamic management function
ms.assetid: 863498b4-849c-434d-b748-837411458738
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cf9299896fb03ea8eb947b5fb5ab9f1967e7d7c0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649208"
---
# <a name="sysdmexectriggerstats-transact-sql"></a>sys.dm_exec_trigger_stats(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  캐시된 트리거에 대한 집계 성능 통계를 반환합니다. 이 뷰에는 트리거당 하나의 행이 포함되며 행의 유효 기간은 트리거가 캐시에 남아 있는 기간과 같습니다. 캐시에서 트리거가 제거되면 이 뷰에서도 해당 행이 제거됩니다. 이때 Performance Statistics SQL 추적 이벤트를 발생 비슷합니다 **sys.dm_exec_query_stats**합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|이 트리거가 있는 데이터베이스 ID입니다.|  
|**object_id**|**int**|이 트리거의 개체 ID입니다.|  
|**type**|**char(2)**|개체의 유형입니다.<br /><br /> TA = 어셈블리(CLR) 트리거<br /><br /> TR = SQL 트리거|  
|**Type_desc**|**nvarchar(60)**|개체 유형에 대한 설명:<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**sql_handle**|**varbinary(64)**|이 쿼리는 상관 관계를 사용할 수 있습니다 **sys.dm_exec_query_stats** 이 트리거 내에서 실행 된 합니다.|  
|**plan_handle**|**varbinary(64)**|메모리 내 계획의 식별자입니다. 이 식별자는 일시적이며 계획이 캐시에 있는 동안에만 일정하게 유지됩니다. 이 값을 사용 하 여 사용할 수는 **sys.dm_exec_cached_plans** 동적 관리 뷰.|  
|**cached_time**|**datetime**|이 트리거가 캐시에 추가된 시간입니다.|  
|**last_execution_time**|**datetime**|이 트리거가 마지막으로 실행된 시간입니다.|  
|**execution_count**|**bigint**|트리거 이후 실행 된 횟수 만큼 마지막으로 컴파일 되었습니다.|  
|**total_worker_time**|**bigint**|총 CPU 시간을 마이크로초에서 컴파일된 이후 실행 될 때이 트리거 사용 된 양입니다.|  
|**last_worker_time**|**bigint**|이 트리거가 마지막으로 실행될 때 사용된 CPU 시간(마이크로초)입니다.|  
|**min_worker_time**|**bigint**|최대 CPU 시간을 마이크로초는이 트리거는 단일 실행 중입니다.|  
|**max_worker_time**|**bigint**|최대 CPU 시간을 마이크로초는이 트리거는 단일 실행 중입니다.|  
|**total_physical_reads**|**bigint**|컴파일된 이후이 트리거가 실행 될 때 수행 된 물리적 읽기의 총 수입니다.|  
|**last_physical_reads**|**bigint**|마지막으로 트리거 실행을 수행 하는 물리적 읽기 수 있습니다.|  
|**min_physical_reads**|**bigint**|단일 실행 중이 트리거가 수행한 물리적 읽기의 최소 수입니다.|  
|**max_physical_reads**|**bigint**|단일 실행 중이 트리거가 수행한 물리적 읽기의 최대 수입니다.|  
|**total_logical_writes**|**bigint**|컴파일된 이후이 트리거가 실행 될 때 수행 된 논리적 쓰기의 총 수입니다.|  
|**last_logical_writes**|**bigint**|마지막으로 트리거 실행을 수행 하는 논리적 쓰기 수 있습니다.|  
|**min_logical_writes**|**bigint**|단일 실행 중이 트리거가 수행한 논리적 쓰기의 최소 수입니다.|  
|**max_logical_writes**|**bigint**|단일 실행 중이 트리거가 수행한 논리적 쓰기의 최대 수입니다.|  
|**total_logical_reads**|**bigint**|컴파일된 이후이 트리거가 실행 될 때 수행 된 논리적 읽기의 총 수입니다.|  
|**last_logical_reads**|**bigint**|마지막으로 트리거 실행을 수행 하는 논리적 읽기 수 있습니다.|  
|**min_logical_reads**|**bigint**|단일 실행 중이 트리거가 수행한 논리적 읽기의 최소 수입니다.|  
|**max_logical_reads**|**bigint**|단일 실행 중이 트리거가 수행한 논리적 읽기의 최대 수입니다.|  
|**total_elapsed_time**|**bigint**|총 경과 시간,이 트리거가 완료 된 실행에 대 한 마이크로초입니다.|  
|**last_elapsed_time**|**bigint**|가장 최근에 이 트리거의 실행을 완료하는 데 소요된 경과 시간(마이크로초)입니다.|  
|**min_elapsed_time**|**bigint**|최소 경과 시간 (마이크로초)에 대 한이 트리거의 실행을 완료 합니다.|  
|**max_elapsed_time**|**bigint**|최대 경과 시간 (마이크로초)에 대 한이 트리거의 실행을 완료 합니다.| 
|**total_spills**|**bigint**|컴파일된 이후이 트리거의 실행에 의해 유출 되는 페이지의 총 수입니다.<br /><br /> **적용할**:부터 시작 하 여 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**last_spills**|**bigint**|트리거가 실행 된 마지막 시간 유출 되는 페이지 수입니다.<br /><br /> **적용할**:부터 시작 하 여 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**min_spills**|**bigint**|단일 실행 중이 트리거가 넘어가지 적이 있는 페이지의 최소 수입니다.<br /><br /> **적용할**:부터 시작 하 여 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
|**max_spills**|**bigint**|단일 실행 중이 트리거가 넘어가지 적이 있는 페이지의 최대 수입니다.<br /><br /> **적용할**:부터 시작 하 여 [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU3|  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에서 동적 관리 뷰는 데이터베이스 포함에 영향을 줄 수 있는 정보 또는 사용자가 액세스할 수 있는 다른 데이터베이스 정보를 노출할 수 없습니다. 이러한 정보 노출을 방지하기 위해 연결된 테넌트에 속하지 않는 데이터가 포함된 행은 모두 필터링됩니다.  

쿼리가 완료되면 뷰의 통계가 업데이트됩니다.  
  
## <a name="permissions"></a>사용 권한  

온 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)], 필요한 `VIEW SERVER STATE` 권한.   
온 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)], 필요를 `VIEW DATABASE STATE` 데이터베이스의 권한.   
  
## <a name="examples"></a>예  
 다음 예에서는 평균 경과 시간으로 식별된 상위 5개의 트리거에 대한 정보를 반환합니다.  
  
```sql  
SELECT TOP 5 d.object_id, d.database_id, DB_NAME(database_id) AS 'database_name',   
    OBJECT_NAME(object_id, database_id) AS 'trigger_name', d.cached_time,  
    d.last_execution_time, d.total_elapsed_time,   
    d.total_elapsed_time/d.execution_count AS [avg_elapsed_time],   
    d.last_elapsed_time, d.execution_count  
FROM sys.dm_exec_trigger_stats AS d  
ORDER BY [total_worker_time] DESC;  
```  
  
## <a name="see-also"></a>관련 항목  
[실행 관련 동적 관리 뷰 및 함수 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
[sys.dm_exec_sql_text &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
[sys.dm_exec_query_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
[sys.dm_exec_procedure_stats &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)   
[sys.dm_exec_cached_plans &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
  
