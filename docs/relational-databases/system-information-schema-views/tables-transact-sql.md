---
title: 테이블 (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- TABLES_TSQL
- TABLES
dev_langs:
- TSQL
helpviewer_keywords:
- TABLES view
- INFORMATION_SCHEMA.TABLES view
ms.assetid: 723a9e63-8f6e-4d6e-b570-468cfaf03201
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cbbc17453dc1e86a50a1809b67ffa967c72f319a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51669812"
---
# <a name="tables-transact-sql"></a>TABLES(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  현재 사용자가 사용 권한을 가진 현재 데이터베이스의 각 테이블당 한 개의 행을 반환합니다.  
  
 이러한 뷰에서 정보를 검색할의 정규화 된 이름을 지정 **INFORMATION_SCHEMA. * * * view_name*합니다.  
  
|열 이름|데이터 형식|설명|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar(** 128 **)**|테이블 한정자입니다.|  
|**TABLE_SCHEMA**|**nvarchar(** 128 **)**|테이블이 포함된 스키마의 이름입니다.<br /><br /> **\*\* 중요 \* \***  개체의 스키마를 확인 하려면 INFORMATION_SCHEMA 뷰를 사용 하지 마십시오. 신뢰할 수 있는 유일한 개체 스키마 검색 방법은 sys.objects 카탈로그 뷰를 쿼리하는 것입니다. INFORMATION_SCHEMA 뷰는 모든 새 기능을 반영하도록 업데이트되지 않으므로 완전하지 않을 수 있습니다.|  
|**TABLE_NAME**|**sysname**|테이블 이름입니다.|  
|**TABLE_TYPE**|**varchar (** 10 **)**|테이블 유형입니다. VIEW 또는 BASE TABLE이 될 수 있습니다.|  
  
## <a name="see-also"></a>관련 항목  
 [시스템 뷰 &#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [정보 스키마 뷰 &#40;TRANSACT-SQL&#41;](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys.objects&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.tables&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)  
  
  
