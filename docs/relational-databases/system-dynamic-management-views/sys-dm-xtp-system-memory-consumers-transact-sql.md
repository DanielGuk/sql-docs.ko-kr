---
title: sys.dm_xtp_system_memory_consumers (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_system_memory_consumers
- sys.dm_xtp_system_memory_consumers_TSQL
- sys.dm_xtp_system_memory_consumers
- dm_xtp_system_memory_consumers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_system_memory_consumers dynamic management view
ms.assetid: 9eb0dd82-7920-42e0-9e50-7ce6e7ecee8b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8341ac09af815f2e96eadd1616fd02cc75810644
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47815051"
---
# <a name="sysdmxtpsystemmemoryconsumers-transact-sql"></a>sys.dm_xtp_system_memory_consumers(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[hek_2](../../includes/hek-2-md.md)]에 대한 시스템 수준 메모리 소비자를 보고합니다. 이러한 소비자에 대한 메모리는 기본 풀(할당이 사용자 스레드의 컨텍스트에 있는 경우)에서 제공되거나 내부 풀(할당이 시스템 스레드의 컨텍스트에 있는 경우)에서 제공됩니다.  
  
```  
-- system memory consumers @ instance  
select * from sys.dm_xtp_system_memory_consumers  
```  
  
 자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
|열 이름|형식|Description|  
|-----------------|----------|-----------------|  
|memory_consumer_id|**bigint**|메모리 소비자의 내부 ID입니다.|  
|memory_consumer_type|**int**|다음 값 중 하나를 사용 하 여 메모리 소비자의 유형을 나타내는 정수:<br /><br /> 0 – 표시되어서는 안 됩니다. 둘 이상 소비자의 메모리 사용량을 집계합니다.<br /><br /> 1-할당 준비: 시스템 할당 준비에 대 한 메모리 소비량을 추적 합니다.<br /><br /> 2-VARHEAP: 가변 길이 힙에 대 한 메모리 소비량을 추적 합니다.<br /><br /> 4-IO 페이지 풀: IO 작업에 사용 되는 시스템 페이지 풀에 대 한 메모리 소비량을 추적 합니다.|  
|memory_consumer_type_desc|**nvarchar(16)**|메모리 소비자의 유형에 대한 설명입니다.<br /><br /> 0 – 표시되어서는 안 됩니다.<br /><br /> 1 – LOOKASIDE<br /><br /> 2 - VARHEAP<br /><br /> 4 - PGPOOL|  
|memory_consumer_desc|**nvarchar(64)**|메모리 소비자 인스턴스에 대한 설명입니다.<br /><br /> VARHEAP: <br />시스템 힙입니다. 일반 용도입니다. 현재, 가비지 수집 작업 항목을 할당하는 데만 사용됩니다.<br />-또는-<br />할당 준비 힙입니다. 할당 준비 목록에 포함된 항목 수가 미리 결정된 캡(일반적으로 약 5,000개 항목)에 도달할 경우 할당 준비에 사용됩니다.<br /><br /> PGPOOL: IO 시스템에 대 한 풀의 경우는 세 가지 다양 한 크기 시스템 4k 페이지 풀, 시스템 64k 페이지 풀 및 시스템 256k 페이지 풀이 있습니다.|  
|lookaside_id|**bigint**|스레드-로컬, 할당 준비 메모리 공급자의 ID입니다.|  
|pagepool_id|**bigint**|스레드-로컬, 페이지 풀 메모리 공급자의 ID입니다.|  
|allocated_bytes|**bigint**|이 소비자에 대해 예약된 바이트 수입니다.|  
|used_bytes|**bigint**|이 소비자가 사용하는 바이트입니다. varheap 메모리 소비자에만 적용됩니다.|  
|allocation_count|**int**|할당 수입니다.|  
|partition_count|**int**|내부적으로만 사용됩니다.|  
|sizeclass_count|**int**|내부적으로만 사용됩니다.|  
|min_sizeclass|**int**|내부적으로만 사용됩니다.|  
|max_sizeclass|**int**|내부적으로만 사용됩니다.|  
|memory_consumer_address|**varbinary**|소비자의 내부 주소입니다.|  
  
## <a name="permissions"></a>사용 권한  
 서버에 대한 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="user-scenario"></a>사용자 시나리오  
  
```  
-- system memory consumers @ instance  
selectmemory_consumer_type_desc,   
allocated_bytes/1024 as allocated_bytes_kb,   
used_bytes/1024 as used_bytes_kb, allocation_count  
from sys.dm_xtp_system_memory_consumers  
```  
  
 출력은 시스템 수준에서 모든 메모리 소비자를 보여 줍니다. 예를 들어 트랜잭션 할당 준비를 위한 소비자가 있습니다.  
  
```  
memory_consumer_type_name           memory_consumer_desc                           allocated_bytes_kb   used_bytes_kb        allocation_count  
-------------------------------          ---------------------                          -------------------  --------------        ----------------  
VARHEAP                                  Lookaside heap                                 0                    0                    0  
VARHEAP                                  System heap                                    768                  0                    2  
LOOKASIDE                                GC transaction map entry                       64                   64                   910  
LOOKASIDE                                Redo transaction map entry                     128                  128                  1260  
LOOKASIDE                                Recovery table cache entry                     448                  448                  8192  
LOOKASIDE                                Transaction recent rows                        3264                 3264                 4444  
LOOKASIDE                                Range cursor                                   0                    0                    0  
LOOKASIDE                                Hash cursor                                    3200                 3200                 11070  
LOOKASIDE                                Transaction save-point set entry               0                    0                    0  
LOOKASIDE                                Transaction partially-inserted rows set        704                  704                  1287  
LOOKASIDE                                Transaction constraint set                     576                  576                  1940  
LOOKASIDE                                Transaction save-point set                     0                    0                    0  
LOOKASIDE                                Transaction write set                          704                  704                  672  
LOOKASIDE                                Transaction scan set                           320                  320                  156  
LOOKASIDE                                Transaction read set                           704                  704                  343  
LOOKASIDE                                Transaction                                    4288                 4288                 1459  
PGPOOL                                   System 256K page pool                          5120                 5120                 20  
PGPOOL                                   System 64K page pool                           0                    0                    0  
PGPOOL                                   System 4K page pool                            24                   24                   6  
```  
  
 시스템 할당자가 사용하는 총 메모리를 보려면 다음을 수행합니다.  
  
```  
select sum(allocated_bytes)/(1024*1024) as total_allocated_MB, sum(used_bytes)/(1024*1024) as total_used_MB   
from sys.dm_xtp_system_memory_consumers  
  
total_allocated_MB   total_used_MB  
-------------------- --------------------  
2                    2  
```  
  
## <a name="see-also"></a>관련 항목  
 [메모리 최적화 테이블 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
