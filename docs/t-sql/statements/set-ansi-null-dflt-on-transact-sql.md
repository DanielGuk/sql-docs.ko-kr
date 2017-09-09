---
title: SET ANSI_NULL_DFLT_ON (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ANSI_NULL_DFLT_ON
- ANSI_NULL_DFLT_ON_TSQL
- SET ANSI_NULL_DFLT_ON
- SET_ANSI_NULL_DFLT_ON_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SET ANSI_NULL_DFLT_ON statement
- ANSI_NULL_DFLT_ON option
- default nullability
- null values [SQL Server], overriding
- overriding default nullability
ms.assetid: 8c925924-a466-4c8b-aeb2-7e0d341f32db
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17bd1817d8f7f04401f49f9a02562bcf577c9088
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansinulldflton-transact-sql"></a>SET ANSI_NULL_DFLT_ON(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  새 열의 기본 null 허용 여부를 재정의 하는 세션의 동작을 수정 하는 경우는 **ANSI null 기본값** 는 데이터베이스에 대 한 옵션 **false**합니다. 값을 설정 하는 방법에 대 한 자세한 내용은 **ANSI null 기본값**, 참조 [ALTER database&#40; Transact SQL &#41; ](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_NULL_DFLT_ON {ON | OFF}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_NULL_DFLT_ON ON;  
```  
  
## <a name="remarks"></a>주의  
 이 설정은 CREATE TABLE과 ALTER TABLE 문에 열의 Null 허용이 지정되어 있지 않을 때 새 열의 Null 허용에만 영향을 줍니다. SET ANSI_NULL_DFLT_ON을 ON으로 설정하면 열의 Null 허용 여부 상태가 명시적으로 지정되지 않은 경우 ALTER TABLE과 CREATE TABLE 문을 사용해 만든 새 열에 Null 값을 사용할 수 있습니다. SET ANSI_NULL_DFLT_ON은 NULL 또는 NOT NULL을 명시적으로 지정하여 만든 열에 영향을 주지 않습니다.  
  
 SET ANSI_NULL_DFLT_OFF와 SET ANSI_NULL_DFLT_ON을 동시에 ON으로 설정할 수 없습니다. 둘 중 하나를 ON으로 설정하면 다른 옵션은 OFF로 설정됩니다. 따라서 ANSI_NULL_DFLT_OFF와 ANSI_NULL_DFLT_ON 중 하나만 ON으로 설정하거나 둘 다 OFF로 설정할 수 있습니다. 두 옵션 중 하나를 ON으로 설정하면 이 설정(SET ANSI_NULL_DFLT_OFF 또는 SET ANSI_NULL_DFLT_ON)이 적용됩니다. 두 옵션 모두 OFF로 설정 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 값이 사용 하는 **is_ansi_null_default_on** 열에는 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 카탈로그 뷰.  
  
 Null 허용 여부 설정이 서로 다른 데이터베이스에서 사용되는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트로 가장 안정적으로 작업하려면 CREATE TABLE과 ALTER TABLE 문에서 NULL 또는 NOT NULL을 지정하는 것이 좋습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 드라이버 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 공급자에 대 한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 연결 될 때 자동으로 ANSI_NULL_DFLT_ON을 ON으로 설정 합니다. DB-Library 응용 프로그램에서 연결하는 경우 SET ANSI_NULL_DFLT_ON의 기본값은 OFF입니다.  
  
 SET ANSI_DEFAULTS를 ON으로 설정하면 SET ANSI_NULL_DFLT_ON 옵션이 설정됩니다.  
  
 SET ANSI_NULL_DFLT_ON은 실행 시간이나 런타임에 설정되며 구문 분석 시간에는 설정되지 않습니다.  
  
 SET ANSI_NULL_DFLT_ON의 설정은 SELECT INTO 문을 사용하여 테이블을 만드는 경우에는 적용되지 않습니다.  
  
 이 설정에 대한 현재 설정을 보려면 다음 쿼리를 실행합니다.  
  
```  
DECLARE @ANSI_NULL_DFLT_ON VARCHAR(3) = 'OFF';  
IF ( (1024 & @@OPTIONS) = 1024 ) SET @ANSI_NULL_DFLT_ON = 'ON';  
SELECT @ANSI_NULL_DFLT_ON AS ANSI_NULL_DFLT_ON;  
  
```  
  
## <a name="permissions"></a>Permissions  
 **public** 역할의 멤버 자격이 필요합니다.  
  
## <a name="examples"></a>예  
 다음 예제에서는의 효과 보여 줍니다. `SET ANSI_NULL_DFLT_ON` 두 설정에 대 한으로 **ANSI null 기본값** 데이터베이스 옵션입니다.  
  
```  
USE AdventureWorks2012;  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON  
-- has an effect when the 'ANSI null default' for the database is false.  
-- Set the 'ANSI null default' database option to false by executing  
-- ALTER DATABASE.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t2.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL insert should succeed.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t3.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t3 (a TINYINT);  
GO  
-- NULL insert should fail.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- The code from this point on demonstrates that SET ANSI_NULL_DFLT_ON   
-- has no effect when the 'ANSI null default' for the database is true.  
-- Set the 'ANSI null default' database option to true.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON  
GO  
  
-- Create table t4.  
CREATE TABLE t4 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t4 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to ON and create table t5.  
SET ANSI_NULL_DFLT_ON ON;  
GO  
CREATE TABLE t5 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t5 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_ON to OFF and create table t6.  
SET ANSI_NULL_DFLT_ON OFF;  
GO  
CREATE TABLE t6 (a TINYINT);  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t6 (a) VALUES (NULL);  
GO  
  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1,t2,t3,t4,t5,t6;  
```  
  
## <a name="see-also"></a>관련 항목:  
 [ALTER TABLE&#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE&#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [SET 문&#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SET ANSI_NULL_DFLT_OFF &#40; Transact SQL &#41;](../../t-sql/statements/set-ansi-null-dflt-off-transact-sql.md)  
  
  