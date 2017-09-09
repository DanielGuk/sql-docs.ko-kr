---
title: SET SHOWPLAN_TEXT (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SHOWPLAN_TEXT
- SET_SHOWPLAN_TEXT_TSQL
- SET SHOWPLAN_TEXT
- SHOWPLAN_TEXT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- statements [SQL Server], estimates
- execution information and estimates [SQL Server]
- statements [SQL Server], information without processing
- SET SHOWPLAN_TEXT statement
- canceling statement execution
- SHOWPLAN_TEXT option
- stopping statement execution
- estimated execution information [SQL Server]
ms.assetid: 2c4f3fc8-ff2c-4790-8b74-e7e8ef58f9a6
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7abd42acdcbfa4274686d3d8162e727cf36e5ee7
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="set-showplantext-transact-sql"></a>SET SHOWPLAN_TEXT(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하지 않도록 합니다. 대신 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 문 실행 방법에 대한 자세한 정보를 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
SET SHOWPLAN_TEXT { ON | OFF }  
```  
  
## <a name="remarks"></a>주의  
 SET SHOWPLAN_TEXT 옵션은 실행 시간 또는 런타임에 설정되며, 구문 분석 시에는 설정되지 않습니다.  
  
 SET SHOWPLAN_TEXT 옵션을 ON으로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 각 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행하지 않고 실행 정보만 반환합니다. 이 옵션을 ON으로 설정할 경우 다시 OFF로 설정할 때까지 이후 모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 문에 대한 실행 계획 정보가 반환됩니다. 예를 들어 SET SHOWPLAN_TEXT 옵션을 ON으로 설정한 상태에서 CREATE TABLE 문을 실행하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 같은 테이블을 포함하는 다음 SELECT 문에서 지정한 테이블이 없음을 알리는 오류 메시지를 반환합니다. 따라서 이후 이 테이블을 참조하는 작업은 실패합니다. SET SHOWPLAN_TEXT 옵션을 OFF로 설정하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 실행 계획 정보가 있는 보고서를 생성하지 않고 문을 실행합니다.  
  
 SET SHOWPLAN_TEXT와 같은 Microsoft Win32 명령 프롬프트 응용 프로그램에 대 한 읽기 쉬운 출력을 반환 하기 위한 용도가 **osql** 유틸리티입니다. SET SHOWPLAN_ALL 옵션은 해당 출력을 처리하도록 디자인된 프로그램에서 사용할 수 있도록 더 자세한 출력을 반환합니다.  
  
 SET SHOWPLAN_TEXT 및 SET SHOWPLAN_ALL 옵션은 저장 프로시저에서 지정할 수 없습니다. 두 옵션은 일괄 처리에서 유일한 문이어야 합니다.  
  
 SET SHOWPLAN_TEXT는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 쿼리 프로세서가 각 문을 실행할 때 수행한 단계를 나타내는 계층적 트리를 구성하는 행 집합으로 정보를 반환합니다. 출력에 반영된 각 문에는 문의 텍스트가 있는 단일 행이 포함되고, 이 단일 행 뒤에는 실행 단계에 대한 자세한 정보가 있는 몇 개의 행이 있습니다. 다음 표에서는 출력에 포함된 열을 보여 줍니다.  
  
|열 이름|Description|  
|-----------------|-----------------|  
|**명령문 텍스트**|PLAN_ROW 유형이 아닌 행에 대해 이 열에는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문의 텍스트가 포함됩니다. PLAN_ROW 유형의 행에 대해서는 이 열에 작업의 설명이 포함됩니다. 이 열에는 물리적 연산자가 포함되며 논리 연산자가 포함될 경우도 있습니다. 이 열 다음에 물리적 연산자가 결정한 설명이 나올 경우도 있습니다. 물리 연산자에 대 한 자세한 내용은 참조는 **인수** 열에 [SET showplan_all 옵션 &#40; Transact SQL &#41; ](../../t-sql/statements/set-showplan-all-transact-sql.md).|  
  
 실행 계획 출력에서 볼 수 있는 물리적 및 논리적 연산자에 대 한 자세한 내용은 참조 [실행 계획 논리 및 물리 연산자 참조](../../relational-databases/showplan-logical-and-physical-operators-reference.md)  
  
## <a name="permissions"></a>Permissions  
 SET SHOWPLAN_TEXT를 사용하려면 SET SHOWPLAN_TEXT가 실행되는 문을 실행할 수 있는 충분한 권한이 있어야 하며 참조된 개체를 포함하는 모든 데이터베이스에 대한 SHOWPLAN 권한이 있어야 합니다.  
  
 SELECT, INSERT, UPDATE, DELETE, EXEC에 대 한 *stored_procedure*, 및 EXEC *user_defined_function* 문의 해야 하는 사용자는 실행 계획을 생성 하려면:  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] 문을 실행할 수 있는 적절한 권한  
  
-   테이블이나 뷰와 같은 Transact-SQL 문이 참조하는 개체가 포함된 모든 데이터베이스에 대한 SHOWPLAN 권한  
  
 DDL, USE와 같은 다른 모든 문의 *database_name*, SET, DECLARE, 동적 SQL, 및에서 실행할 수 있는 적절 한 권한이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문이 필요 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 문을 처리할 때 인덱스를 사용하는 방법을 보여 줍니다.  
  
 다음은 인덱스를 사용 하 여 쿼리입니다.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 결과 집합은 다음과 같습니다.  
  
```  
StmtText                                             
---------------------------------------------------  
SELECT *  
FROM Production.Product   
WHERE ProductID = 905;   
  
StmtText                                                                                                                                                                                        
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Seek(OBJECT:([AdventureWorks2012].[Production].[Product].[PK_Product_ProductID]), SEEK:([AdventureWorks2012].[Production].[Product].[ProductID]=CONVERT_IMPLICIT(int,[@1],0)) ORDERED FORWARD)   
```  
  
 다음은 인덱스를 사용하지 않은 쿼리입니다.  
  
```  
USE AdventureWorks2012;  
GO  
SET SHOWPLAN_TEXT ON;  
GO  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;  
GO  
SET SHOWPLAN_TEXT OFF;  
GO  
```  
  
 결과 집합은 다음과 같습니다.  
  
```  
StmtText                                                                  
------------------------------------------------------------------------  
SELECT *  
FROM Production.ProductCostHistory  
WHERE StandardCost < 500.00;   
  
StmtText                                                                                                                                                                                                  
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------  
|--Clustered Index Scan(OBJECT:([AdventureWorks2012].[Production].[ProductCostHistory].[PK_ProductCostHistory_ProductCostID]), WHERE:([AdventureWorks2012].[Production].[ProductCostHistory].[StandardCost]<[@1]))  
```  
  
## <a name="see-also"></a>관련 항목:  
 [연산자 &#40; Transact SQL &#41;](../../t-sql/language-elements/operators-transact-sql.md)   
 [SET 문&#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET showplan_all 옵션 &#40; Transact SQL &#41;](../../t-sql/statements/set-showplan-all-transact-sql.md)  
  
  
