---
title: 스키마 행 집합 지원 (OLE DB) | Microsoft Docs
description: 스키마 행 집합 지원(OLE DB)
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- schema rowsets [OLE DB]
- OLE DB, schema rowsets
- OLE DB rowsets, schema
- OLE DB Driver for SQL Server, schema rowsets
- rowsets [OLE DB], schema
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 78acce6157928d579a06e06fbf95008c4a7e11c1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47664601"
---
# <a name="schema-rowset-support-ole-db"></a>스키마 행 집합 지원(OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server용 OLE DB 드라이버는 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 분산 쿼리를 처리할 때 연결된 서버에서 스키마 정보를 반환하는 것도 지원합니다.  
  
> [!NOTE]  
>  하지만 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 동의어 SQL Server 용 OLE DB 드라이버에서 반환 되지 않습니다에 대 한 동의어, 메타 데이터를 지원 합니다.  
  
 다음 표에는 SQL Server용 OLE DB 드라이버가 지원하는 스키마 행 집합 및 제한 열이 나와 있습니다.  
  
|스키마 행 집합|제한 열|  
|-------------------|-------------------------|  
|DBSCHEMA_CATALOGS|CATALOG_NAME|  
|DBSCHEMA_COLUMN_PRIVILEGES|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME GRANTOR GRANTEE|  
|DBSCHEMA_COLUMNS|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME COLUMN_NAME<br /><br /> 다음의 추가 열은 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]와 관련됩니다.<br /><br /> COLUMN_LCID. 데이터 정렬의 로캘 ID입니다. COLUMN_LCID는 Windows LCID 값과 같습니다.<br /><br /> COLUMN_COMPFLAGS. 데이터 정렬에 지원되는 비교를 정의합니다. 데이터 형식은 DBPROB_FINDCOMPAREOPS와 같습니다.<br /><br /> COLUMN_SORTID. 데이터 정렬에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 정렬 스타일입니다.<br /><br /> COLUMN_TDSCOLLATION. 열에 대한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터 정렬입니다.<br /><br /> IS_COMPUTED. 열이 계산 열이면 VARIANT_TRUE이고, 그렇지 않으면 VARIANT_FALSE입니다.|  
|DBSCHEMA_FOREIGN_KEYS|모든 제한 사항이 지원됩니다.<br /><br /> PK_TABLE_CATALOG PK_TABLE_SCHEMA PK_TABLE_NAME FK_TABLE_CATALOG FK_TABLE_SCHEMA FK_TABLE_NAME|  
|DBSCHEMA_INDEXES|제한 사항 1, 2, 3 및 5가 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA INDEX_NAME TABLE_NAME|  
|DBSCHEMA_PRIMARY_KEYS|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_PROCEDURE_PARAMETERS|모든 제한 사항이 지원됩니다.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME PARAMETER_NAME|  
|DBSCHEMA_PROCEDURES|제한 사항 1, 2 및 3이 지원됩니다.<br /><br /> PROCEDURE_CATALOG PROCEDURE_SCHEMA PROCEDURE_NAME<br /><br /> DBSCHEMA_PROCEDURES는 현재 사용자가 실행할 수 있는 프로시저나 현재 사용자가 VIEW DEFINITION 권한을 부여받은 프로시저만 반환합니다.|  
|DBSCHEMA_PROVIDER_TYPES|모든 제한 사항이 지원됩니다.<br /><br /> DATA_TYPE BEST_MATCH|  
|DBSCHEMA_SCHEMATA|모든 제한 사항이 지원됩니다.<br /><br /> CATALOG_NAME SCHEMA_NAME SCHEMA_OWNER|  
|DBSCHEMA_STATISTICS|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME|  
|DBSCHEMA_TABLE_CONSTRAINTS|모든 제한 사항이 지원됩니다.<br /><br /> CONSTRAINT_CATALOG CONSTRAINT_SCHEMA CONSTRAINT_NAME TABLE_CATALOG TABLE_SCHEMA TABLE_NAME CONSTRAINT_TYPE|  
|DBSCHEMA_TABLE_PRIVILEGES|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME GRANTOR GRANTEE|  
|DBSCHEMA_TABLES|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
|DBSCHEMA_TABLES_INFO|모든 제한 사항이 지원됩니다.<br /><br /> TABLE_CATALOG TABLE_SCHEMA TABLE_NAME TABLE_TYPE|  
  
## <a name="in-this-section"></a>섹션 내용  
 [스키마 행 집합에서 분산 쿼리 지원](../../oledb/ole-db/schema-rowsets-distributed-query-support.md)  
  
 [LINKEDSERVERS 행 집합 &#40;OLE DB&#41;](../../oledb/ole-db/schema-rowsets-linkedservers-rowset.md)  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server 프로그래밍용 OLE DB 드라이버](../../oledb/ole-db/oledb-driver-for-sql-server-programming.md)   
 [사용자 정의 형식 사용](../../oledb/features/using-user-defined-types.md)  
  
  
