---
title: 어셈블리 삭제 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- removing assemblies
- DROP ASSEMBLY statement
- assemblies [CLR integration], removing
- dropping assemblies
ms.assetid: 03481034-dc91-4488-ab24-ba44243e2690
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d7dceef4651804dabf4080d6f8b85d0597b1957b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135281"
---
# <a name="dropping-an-assembly"></a>어셈블리 삭제
  CREATE ASSEMBLY 문을 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에 등록한 어셈블리에서 제공하는 기능이 더 이상 필요 없는 경우 이 어셈블리를 삭제할 수 있습니다. 어셈블리를 삭제하면 데이터베이스에서 어셈블리뿐 아니라 디버그 파일 등의 모든 관련 파일이 제거됩니다. 어셈블리를 삭제하려면 DROP ASSEMBLY 문을 다음 구문으로 사용합니다.  
  
```  
DROP ASSEMBLY MyDotNETAssembly  
```  
  
 DROP ASSEMBLY는 현재 실행되고 있는 어셈블리를 참조하는 코드를 방해하지 않지만 DROP ASSEMBLY를 실행한 후 해당 어셈블리 코드를 호출하려고 하면 실패합니다.  
  
 어셈블리가 데이터베이스에 있는 다른 어셈블리에서 참조되거나 현재 데이터베이스의 CLR(공용 언어 런타임) 함수, 프로시저, 트리거, UDT(사용자 정의 형식) 또는 UDA(사용자 정의 집계)에서 사용되면 DROP ASSEMBLY가 오류를 반환합니다. 먼저 DROP AGGREGATE, DROP FUNCTION, DROP PROCEDURE, DROP TRIGGER 및 DROP TYPE 문을 사용하여 어셈블리에 포함된 관리되는 데이터베이스 개체를 삭제합니다.  
  
## <a name="removing-a-udt-from-the-database"></a>데이터베이스에서 UDT 제거  
 DROP TYPE 문은 현재 데이터베이스에서 UDT를 제거합니다. UDT를 삭제한 경우 DROP ASSEMBLY 문을 사용하여 데이터베이스에서 어셈블리를 삭제할 수 있습니다.  
  
 다음과 같이 개체가 UDT에 종속되어 있으면 DROP TYPE 문이 실패합니다.  
  
-   UDT를 사용하여 정의한 열이 포함된 데이터베이스의 테이블  
  
-   데이터베이스에 WITH SCHEMABINDING 절로 만든 함수, 저장 프로시저 또는 트리거가 있고 이러한 루틴이 UDT의 변수 또는 매개 변수를 사용하는 경우  
  
### <a name="finding-udt-dependencies"></a>UDT 종속성 찾기  
 따라서 먼저 모든 종속 개체를 삭제한 다음 DROP TYPE 문을 실행해야 합니다. 다음 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 쿼리 매개 변수에서 UDT를 사용 하는 열을 모두 찾습니다 합니다 **AdventureWorks** 데이터베이스입니다.  
  
```  
USE Adventureworks;  
SELECT o.name AS major_name, o.type_desc AS major_type_desc  
     , c.name AS minor_name, c.type_desc AS minor_type_desc  
     , at.assembly_class  
  FROM (  
        SELECT object_id, name, user_type_id, 'SQL_COLUMN' AS type_desc  
          FROM sys.columns  
     UNION ALL  
        SELECT object_id, name, user_type_id, 'SQL_PROCEDURE_PARAMETER'  
          FROM sys.parameters  
     ) AS c  
  JOIN sys.objects AS o  
    ON o.object_id = c.object_id  
  JOIN sys.assembly_types AS at  
    ON at.user_type_id = c.user_type_id;   
```  
  
## <a name="see-also"></a>관련 항목  
 [CLR 통합 어셈블리 관리](managing-clr-integration-assemblies.md)   
 [어셈블리 변경](altering-an-assembly.md)   
 [어셈블리 만들기](creating-an-assembly.md)   
 [DROP AGGREGATE &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/drop-aggregate-transact-sql)   
 [DROP FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-function-transact-sql)   
 [DROP PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-procedure-transact-sql)   
 [DROP TRIGGER&#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-trigger-transact-sql)   
 [삭제 유형을 &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/drop-type-transact-sql)  
  
  
