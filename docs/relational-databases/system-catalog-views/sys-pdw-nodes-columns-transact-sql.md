---
title: sys.pdw_nodes_columns (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 268c77b7-1d71-4197-a2ed-5e2b2b8fc260
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 7b811bb94039974faa8c145ef93df92949fbd702
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47714911"
---
# <a name="syspdwnodescolumns-transact-sql"></a>sys.pdw_nodes_columns (Transact SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  사용자 정의 테이블 및 사용자 정의 뷰에 대 한 열을 보여 줍니다.  
  
|열 이름|데이터 형식|Description|범위|  
|-----------------|---------------|-----------------|-----------|  
|object_id|**int**|이 열이 속한 개체의 ID입니다.||  
|NAME|**sysname**|열의 이름입니다. 개체에 고유 합니다.||  
|column_id|**int**|열의 ID입니다. 개체에 고유 합니다.||  
|system_type_id|**tinyint**|열의 시스템 유형 ID입니다.||  
|user_type_id|**int**|열의 유형에 대한 사용자 정의 ID입니다.||  
|max_length|**smallint**|열의 최대 길이(바이트)입니다.|지원 되지 않는 열 형식에 대 한 (올바르지 않음)-1을 포함합니다.|  
|전체 자릿수|**tinyint**|숫자 기반일 경우에는 열의 전체 자릿수이고, 그렇지 않으면 0입니다.||  
|소수 자릿수|**tinyint**|숫자 기반일 경우에는 열의 소수 자릿수이고, 그렇지 않으면 0입니다.||  
|collation_name|**sysname**|문자 기반일 경우에는 열의 데이터 정렬 이름이고, 그렇지 않으면 NULL입니다.||  
|is_nullable|**bit**|1 = 열이 Null 값을 허용합니다.||  
|is_ansi_padded|**bit**|1 = 열이 문자, 이진 또는 variant인 경우 ANSI_PADDING ON 동작을 사용합니다.|항상 0입니다.|  
|is_rowguidcol|**bit**|1 = 선언된 ROWGUIDCOL 열입니다.|항상 0입니다.|  
|is_identity|**bit**|1 = 열에 ID 값이 있습니다.|항상 0입니다.|  
|is_computed|**bit**|1 = 열이 계산 열입니다.|항상 0입니다.|  
|is_filestream|**bit**|1 = 열이 FILESTREAM 열입니다.|항상 0입니다.|  
|is_replicated|**bit**|1 = 복제된 열입니다.|항상 0입니다.|  
|is_non_sql_subscribed|**bit**|1 = 열에 SQL이 아닌 구독자에 있습니다.|항상 0입니다.|  
|is_merge_published|**bit**|1 = 병합 게시 열입니다.|항상 0입니다.|  
|is_dts_replicated|**bit**|1 = 열이 SSIS를 사용 하 여 복제 합니다.|항상 0입니다.|  
|is_xml_document|**bit**|1 = 내용이 완전한 XML 문서입니다.|항상 0입니다.|  
|xml_collection_id|**int**|0 = XML 스키마 컬렉션이 없습니다.|항상 0입니다.|  
|default_object_id|**int**|기본 개체의 ID 0 = 기본값이 없습니다.|항상 0입니다.|  
|rule_object_id|**int**|열에 바인딩된 독립 실행형 규칙의 ID입니다. <br />0 = 독립 실행형 규칙이 없습니다.|항상 0입니다.|  
|is_sparse|**bit**|1 = 열이 스파스 열입니다.|항상 0입니다.|  
|is_column_set|**bit**|1 = 열이 열 집합입니다.|항상 0입니다.|  
|pdw_node_id|**int**|고유 식별자를 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 노드.|NOT NULL|  
  
## <a name="permissions"></a>사용 권한  
 CONTROL SERVER 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SQL Data Warehouse 및 병렬 데이터 웨어하우스 카탈로그 뷰](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [sys.all_columns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-all-columns-transact-sql.md)  
  
  
