---
title: REVOKE 개체 사용 권한(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- table permissions [SQL Server], revoking
- REVOKE statement, objects
- revoking permissions to access tables
- object permissions [SQL Server], revoking
ms.assetid: 99c7146e-d2e7-4f1a-80ff-21a05bc5e8bb
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 55c06191de80cf76f6ced789f2fe10ff8c1c79ed
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47623461"
---
# <a name="revoke-object-permissions-transact-sql"></a>REVOKE 개체 사용 권한(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  테이블, 뷰, 테이블 반환 함수, 저장 프로시저, 확장 저장 프로시저, 스칼라 함수, 집계 함수, 서비스 큐 또는 동의어에 대한 사용 권한을 취소합니다. 
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
REVOKE [ GRANT OPTION FOR ] <permission> [ ,...n ] ON   
    [ OBJECT :: ][ schema_name ]. object_name [ ( column [ ,...n ] ) ]  
        { FROM | TO } <database_principal> [ ,...n ]   
    [ CASCADE ]  
    [ AS <database_principal> ]  
  
<permission> ::=  
    ALL [ PRIVILEGES ] | permission [ ( column [ ,...n ] ) ]  
  
<database_principal> ::=   
        Database_user   
    | Database_role   
    | Application_role   
    | Database_user_mapped_to_Windows_User   
    | Database_user_mapped_to_Windows_Group   
    | Database_user_mapped_to_certificate   
    | Database_user_mapped_to_asymmetric_key   
    | Database_user_with_no_login      
```  
  
## <a name="arguments"></a>인수  
 *permission*  
 스키마 포함 개체에 대해 취소할 수 있는 사용 권한을 지정합니다. 사용 권한 목록은 이 항목의 뒤에 나오는 주의 섹션을 참조하세요.  
  
 ALL  
 ALL을 취소해도 일부 가능한 사용 권한은 취소되지 않습니다. ALL을 취소하는 것은 지정된 개체에 적용할 수 있는 모든 [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 사용 권한을 취소하는 것과 동일합니다. ALL의 의미는 다음과 같이 달라집니다.  
  
 스칼라 함수 사용 권한: EXECUTE, REFERENCES.  
  
 테이블 반환 함수 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 저장 프로시저 사용 권한: EXECUTE.  
  
 테이블 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 뷰 사용 권한: DELETE, INSERT, REFERENCES, SELECT, UPDATE.  
  
 PRIVILEGES  
 [!INCLUDE[vcpransi](../../includes/vcpransi-md.md)]-92 호환성을 위해 포함되었습니다. ALL의 동작을 변경하지 않습니다.  
  
 *column*  
 사용 권한을 취소할 테이블, 뷰 또는 테이블 반환 함수의 열 이름을 지정합니다. 괄호 ( )가 필요합니다. SELECT, REFERENCES 및 UPDATE 권한만 열에 정의할 수 있습니다. *column*은 권한 절에 지정하거나 보안 이름 뒤에 지정할 수 있습니다.  
  
 ON [ OBJECT :: ] [ *schema_name* ] . *object_name*  
 사용 권한을 취소할 개체를 지정합니다. *schema_name*을 지정한 경우 OBJECT 구는 선택 사항입니다. OBJECT 구가 사용된 경우 범위 한정자(::)가 필요합니다. *schema_name*을 지정하지 않은 경우 기본 스키마가 사용됩니다. *schema_name*을 지정하지 않은 경우 기본 스키마 범위 한정자(.)가 사용됩니다.  
  
 { FROM | TO } \<database_principal> 사용 권한을 취소할 보안 주체를 지정합니다.  
  
 GRANT OPTION  
 지정한 사용 권한을 다른 보안 주체에게 부여할 수 있는 권한이 취소됨을 나타냅니다. 사용 권한 자체는 취소되지 않습니다.  
  
> [!IMPORTANT]  
>  보안 주체에 GRANT 옵션 없이 지정된 사용 권한이 있는 경우 사용 권한 자체가 취소됩니다.  
  
 CASCADE  
 사용 권한이 취소된 보안 주체에게 사용 권한을 부여 받거나 거부당한 다른 보안 주체의 사용 권한도 취소됨을 나타냅니다.  
  
> [!CAUTION]  
>  WITH GRANT OPTION을 부여 받은 사용 권한이 연계되어 취소되면 해당 사용 권한의 GRANT 및 DENY가 모두 취소됩니다.  
  
 \<database_principal>로서 이 쿼리를 실행하는 보안 주체가 사용 권한을 부여하는 권한을 취소할 수 있는 다른 보안 주체를 지정합니다.  
  
 *Database_user*  
 데이터베이스 사용자를 지정합니다.  
  
 *Database_role*  
 데이터베이스 역할을 지정합니다.  
  
 *Application_role*  
 응용 프로그램 역할을 지정합니다.  
  
 *Database_user_mapped_to_Windows_User*  
 Windows 사용자로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_Windows_Group*  
 Windows 그룹으로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_certificate*  
 인증서로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_mapped_to_asymmetric_key*  
 비대칭 키로 매핑된 데이터베이스 사용자를 지정합니다.  
  
 *Database_user_with_no_login*  
 해당 서버 수준의 보안 주체가 없는 데이터베이스 사용자를 지정합니다.  
  
## <a name="remarks"></a>Remarks  
 개체에 대한 정보는 다양한 카탈로그 뷰에 표시됩니다. 자세한 내용은 [Object Catalog Views &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)을 참조하세요.  
  
 개체는 사용 권한 계층에서 해당 개체의 부모인 스키마에 포함된 스키마 수준 보안 개체입니다. 다음 표에는 개체에 대해 취소할 수 있는 가장 제한적인 특정 사용 권한이 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한과 함께 나열되어 있습니다.  
  
|개체 사용 권한|개체 사용 권한에 포함된 사용 권한|스키마 사용 권한에 포함된 사용 권한|  
|-----------------------|----------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER|  
|CONTROL|CONTROL|CONTROL|  
|Delete|CONTROL|Delete|  
|CREATE 문을 실행하기 전에|CONTROL|CREATE 문을 실행하기 전에|  
|INSERT|CONTROL|INSERT|  
|RECEIVE|CONTROL|CONTROL|  
|REFERENCES|CONTROL|REFERENCES|  
|SELECT|RECEIVE|SELECT|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|UPDATE|CONTROL|UPDATE|  
|VIEW CHANGE TRACKING|CONTROL|VIEW CHANGE TRACKING|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 개체에 대한 CONTROL 권한이 필요합니다.  
  
 AS 절을 사용하는 경우 지정된 보안 주체가 사용 권한을 취소할 개체를 소유해야 합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-revoking-select-permission-on-a-table"></a>1. 테이블에 대한 SELECT 사용 권한 취소  
 다음 예에서는 `SELECT` 데이터베이스의 `RosaQdM` 테이블에 대해 사용자 `Person.Address`에서 `AdventureWorks2012` 사용 권한을 취소합니다.  
  
```  
USE AdventureWorks2012;  
REVOKE SELECT ON OBJECT::Person.Address FROM RosaQdM;  
GO  
```  
  
### <a name="b-revoking-execute-permission-on-a-stored-procedure"></a>2. 저장 프로시저에 대한 EXECUTE 권한 취소  
 다음 예에서는 `EXECUTE`이라는 응용 프로그램 역할에서 저장 프로시저 `HumanResources.uspUpdateEmployeeHireInfo`에 대한 `Recruiting11` 사용 권한을 취소합니다.  
  
```  
USE AdventureWorks2012;  
REVOKE EXECUTE ON OBJECT::HumanResources.uspUpdateEmployeeHireInfo  
    FROM Recruiting11;  
GO   
```  
  
### <a name="c-revoking-references-permission-on-a-view-with-cascade"></a>3. CASCADE를 지정하여 뷰에 대한 REFERENCES 권한 취소  
 다음 예에서는 `REFERENCES`를 지정하여 사용자 `BusinessEntityID`로부터 `HumanResources.vEmployee` 뷰의 `Wanida` 열에 대한 `CASCADE` 권한을 거부합니다.  
  
```  
USE AdventureWorks2012;  
REVOKE REFERENCES (BusinessEntityID) ON OBJECT::HumanResources.vEmployee   
    FROM Wanida CASCADE;  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [GRANT 개체 사용 권한&#40;Transact-SQL&#41;](../../t-sql/statements/grant-object-permissions-transact-sql.md)   
 [DENY 개체 사용 권한&#40;Transact-SQL&#41;](../../t-sql/statements/deny-object-permissions-transact-sql.md)   
 [개체 카탈로그 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [사용 권한&#40;데이터베이스 엔진&#41;](../../relational-databases/security/permissions-database-engine.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [Securables](../../relational-databases/security/securables.md)   
 [sys.fn_builtin_permissions&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)   
 [HAS_PERMS_BY_NAME&#40;Transact-SQL&#41;](../../t-sql/functions/has-perms-by-name-transact-sql.md)   
 [sys.fn_my_permissions &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)  
  
  

