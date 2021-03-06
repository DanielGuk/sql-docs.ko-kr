---
title: sys.column_store_segments (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/15/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- column_store_segments
- sys.column_store_segments_TSQL
- sys.column_store_segments
- column_store_segments_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.column_store_segments catalog view
ms.assetid: 1253448c-2ec9-4900-ae9f-461d6b51b2ea
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: df7698d222c2c2f0f68138eaa5f6289106b97659
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47799481"
---
# <a name="syscolumnstoresegments-transact-sql"></a>sys.column_store_segments(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

Columnstore 인덱스의 각 열 세그먼트에 대 한 하나의 행을 반환 합니다. 그룹당 열당 하나의 열 세그먼트가 있습니다. 예를 들어 10 개의 rowgroup 34 열과 테이블 340 행을 반환합니다. 
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|파티션 ID를 나타냅니다. 데이터베이스 내에서 고유합니다.|  
|**hobt_id**|**bigint**|이 Columnstore 인덱스를 가진 테이블의 B-트리 인덱스(hobt) 또는 힙의 ID입니다.|  
|**column_id**|**int**|Columnstore 열의 ID입니다.|  
|**segment_id**|**int**|행 그룹의 ID입니다. 이전 버전과 호환성을 위해 열 이름을 계속 해 서 행 그룹 ID입니다.이 경우에 segment_id 호출 사용 하 여 세그먼트를 고유 하 게 식별할 수 있습니다 \<hobt_id, partition_id, column_id >, < segment_id >.|  
|**version**|**int**|열 세그먼트 형식의 버전입니다.|  
|**encoding_type**|**int**|세그먼트에 사용 되는 인코딩 유형:<br /><br /> 1 = VALUE_BASED-문자열/이진이 아닌 없습니다 사전 (매우 유사 일부 내부 변형 4)를 사용 하 여<br /><br /> 2 = VALUE_HASH_BASED-사전에 공통 값과 문자열/이진이 아닌 열<br /><br /> 3 = STRING_HASH_BASED-사전에 공통 값과 문자열/이진 열<br /><br /> 4 = STORE_BY_VALUE_BASED-문자열/이진이 아닌 없습니다 사전 사용 하 여<br /><br /> 5 = STRING_STORE_BY_VALUE_BASED-없습니다 사전 사용 하 여 문자열 이진 파일<br /><br /> 모든 인코딩을 비트 압축 및 실행 길이 인코딩 가능 하면 활용 합니다.|  
|**row_count**|**int**|행 그룹의 행 수입니다.|  
|**has_nulls**|**int**|열 세그먼트에 Null 값이 있으면 1입니다.|  
|**base_id**|**bigint**|기준 값 id 인코딩 유형 1이 사용 됩니다.  인코딩 유형 1은 사용 되지 base_id-1로 설정 됩니다.|  
|**magnitude**|**float**|인코딩 유형 1을 사용 하는 경우 크기입니다.  인코딩 유형 1은 사용 되지 경우 크기는-1로 설정 됩니다.|  
|**primary_dictionary_id**|**int**|값이 0 전역 사전을 나타냅니다. -1 값이이 열에 대해 만든 전역 사전이 없습니다 임을 나타냅니다.|  
|**secondary_dictionary_id**|**int**|현재 세그먼트 (즉, rowgroup)에서이 열에 대 한 로컬 사전에 0이 아닌 값을 가리킵니다. -1 값이이 세그먼트에 대 한 사전이 없습니다 로컬 인지를 나타냅니다.|  
|**min_data_id**|**bigint**|열 세그먼트의 최소 데이터 ID입니다.|  
|**max_data_id**|**bigint**|열 세그먼트의 최대 데이터 ID입니다.|  
|**null_value**|**bigint**|Null을 나타내는 데 사용되는 값입니다.|  
|**on_disk_size**|**bigint**|세그먼트의 크기(바이트)입니다.|  
  
## <a name="remarks"></a>Remarks  
 다음 쿼리는 columnstore 인덱스의 세그먼트에 대한 정보를 반환합니다.  
  
```sql  
SELECT i.name, p.object_id, p.index_id, i.type_desc,   
    COUNT(*) AS number_of_segments  
FROM sys.column_store_segments AS s   
INNER JOIN sys.partitions AS p   
    ON s.hobt_id = p.hobt_id   
INNER JOIN sys.indexes AS i   
    ON p.object_id = i.object_id  
WHERE i.type = 5 OR i.type = 6  
GROUP BY i.name, p.object_id, p.index_id, i.type_desc ;  
GO  
```  
  
## <a name="permissions"></a>사용 권한  
 모든 열 이상이 필요 **VIEW DEFINITION** 테이블에 대 한 합니다. 다음 열을 null을 반환 하지 않으면 사용자도 **선택** 권한: has_nulls, base_id, 크기, min_data_id을 반환 합니다.  
  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [개체 카탈로그 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [카탈로그 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [SQL Server 시스템 카탈로그 FAQ](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [sys.columns&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)   
 [sys.computed_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-computed-columns-transact-sql.md)   
 [Columnstore 인덱스 가이드](~/relational-databases/indexes/columnstore-indexes-overview.md)    
 [sys.column_store_dictionaries&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql.md)  
  
  

