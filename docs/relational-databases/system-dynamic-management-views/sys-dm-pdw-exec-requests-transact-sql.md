---
title: sys.dm_pdw_exec_requests (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 390225cc-23e8-4051-a5f6-221e33e4c0b4
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: c2a1978aeea7ec69ea45bc088bbdff432de3c9f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47621871"
---
# <a name="sysdmpdwexecrequests-transact-sql"></a>sys.dm_pdw_exec_requests (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  모든 요청에 대 한 정보를 현재 또는 최근에 활성 보유 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]합니다. 요청/쿼리 당 하나의 행을 나열합니다.  
  
|열 이름|데이터 형식|Description|범위|  
|-----------------|---------------|-----------------|-----------|  
|request_id|**nvarchar(32)**|이 보기에 대 한 키입니다. 요청과 연결 된 고유 숫자 id입니다.|시스템의 모든 요청에서 고유 합니다.|  
|session_id|**nvarchar(32)**|이 쿼리를 실행 하는 세션에 연결 된 고유 숫자 id입니다. 참조 [sys.dm_pdw_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-sessions-transact-sql.md)합니다.||  
|상태|**nvarchar(32)**|요청의 현재 상태입니다.|' 실행 중 ', '일시 중지', '완료', '취소', '실패'입니다.|  
|submit_time|**datetime**|요청을 제출한 실행 시간입니다.|유효한 **날짜/시간** 작거나 start_time와 현재 시간입니다.|  
|start_time|**datetime**|요청 실행을 시작한 시간입니다.|큐에 대기 중인된 요청에 대 한 NULL 그렇지 않으면, 유효한 **날짜/시간** 현재 작거나 합니다.|  
|end_compile_time|**datetime**|엔진은 요청 컴파일 완료 하는 시간입니다.|아직 컴파일되지가 요청에 대 한 NULL 그렇지 않은 경우 유효한 **날짜/시간** start_time 보다 작음 및 현재 시간 보다 작거나 합니다.|
|end_time|**datetime**|요청 실행 완료, 실패 또는 취소 된 시간입니다.|활성 또는 대기 중인 요청에 대 한 null 그렇지 않은 경우 유효한 **날짜/시간** 현재 작거나 합니다.|  
|total_elapsed_time|**int**|요청 시간 (밀리초)에서 시작 된 이후 실행에서 경과한 시간입니다.|0 사이의 start_time 및 end_time 간의 차이입니다.<br /><br /> Total_elapsed_time 정수에 대 한 최대값을 초과 하면 total_elapsed_time 최대 값으로 계속 됩니다. 이 조건이 "최대 값을 초과 했습니다." 경고 생성<br /><br /> 시간 (밀리초)의 최 댓 값 24.8 일 하는 것과 같습니다.|  
|레이블|**nvarchar(255)**|일부 선택 쿼리 문과 연결 된 선택적 레이블 문자열입니다.|문자열을 포함 하는 ' a ~ z', ' A-z ','0-9', '_'.|  
|error_id|**nvarchar(36)**|있는 경우, 요청과 연결 된 오류의 고유 id입니다.|참조 [sys.dm_pdw_errors &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-errors-transact-sql.md); 오류가 발생 하지 않은 경우 NULL로 설정 합니다.|  
|database_id|**int**|명시적 컨텍스트 (예: 사용 하 여 DB_X) 사용 하는 데이터베이스의 식별자입니다.|id를 참조 하세요 [sys.databases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)합니다.|  
|command|**nvarchar(4000)**|사용자가 제출한 요청의 전체 텍스트를 포함 합니다.|모든 유효한 쿼리 또는 요청 텍스트입니다. 4000 바이트를 초과할 수 있는 쿼리는 잘립니다.|  
|resource_class|**nvarchar(20)**|이 요청에 대 한 리소스 클래스입니다. 관련 참조 **concurrency_slots_used** 에 [sys.dm_pdw_resource_waits &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-resource-waits-transact-sql.md).|SmallRC<br /><br /> MediumRC<br /><br /> LargeRC<br /><br /> XLargeRC|  
  
 이 보기에 의해 보존 된 최대 행에 대 한 내용은의 "최소 및 최대 값"를 참조 합니다 [!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]합니다.  
  
## <a name="permissions"></a>사용 권한  
 VIEW SERVER STATE 권한이 필요합니다.  
  
## <a name="security"></a>보안  
 sys.dm_pdw_exec_requests는 데이터베이스별 권한에 따라 쿼리 결과 필터링 하지 않습니다. VIEW SERVER STATE 권한이 있는 로그인 결과 모든 데이터베이스에 대 한 쿼리 결과 가져올 수 있습니다.  
  
> [!WARNING]  
>  공격자는 sys.dm_pdw_exec_requests를 사용 하 여 VIEW SERVER STATE 권한이 단순히 함으로써 및 데이터베이스별 권한 없이 특정 데이터베이스 개체에 대 한 정보를 검색할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Data Warehouse 및 병렬 데이터 웨어하우스 동적 관리 뷰 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
