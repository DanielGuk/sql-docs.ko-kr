---
title: "GRANT 가용성 그룹 사용 권한 (Transact SQL) | Microsoft Docs"
ms.custom: 
ms.date: 06/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], permissions
- GRANT statement, availability groups
- granting permissions, [SQL Server], availability groups
- permissions [SQL Server], availability group
ms.assetid: 060eb839-666a-4046-9e1d-5edc9ea75a11
caps.latest.revision: 9
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 154c99ddfb9f3a69a4a9eeae35f20c5e9720100d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="grant-availability-group-permissions-transact-sql"></a>가용성 그룹 사용 권한 부여(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Always On 가용성 그룹에 대 한 권한을 부여합니다.  
  

 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
GRANT permission  [ ,...n ] ON AVAILABILITY GROUP :: availability_group_name  
        TO < server_principal >  [ ,...n ]  
    [ WITH GRANT OPTION ]  
    [ AS SQL_Server_login ]   
  
<server_principal> ::=   
        SQL_Server_login  
    | SQL_Server_login_from_Windows_login   
    | SQL_Server_login_from_certificate   
    | SQL_Server_login_from_AsymKey  
```  
  
## <a name="arguments"></a>인수  
 *사용 권한*  
 가용성 그룹에 부여할 수 있는 사용 권한을 지정합니다. 사용 권한 목록은 이 항목의 뒤에 나오는 주의 섹션을 참조하세요.  
  
 가용성 그룹에 **::***availability_group_name*  
 사용 권한을 부여할 가용성 그룹을 지정합니다. 범위 한정자 (**::**)가 필요 합니다.  
  
 \<server_principal >  
 사용 권한을 부여할 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정합니다.  
  
 *SQL_Server_login*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_Windows_login*  
 Windows 로그인에서 생성된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_certificate*  
 인증서로 매핑된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 *SQL_Server_login_from_AsymKey*  
 비대칭 키에 매핑된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인의 이름을 지정합니다.  
  
 WITH GRANT OPTION  
 지정된 사용 권한을 다른 보안 주체에게 부여할 수 있는 권한도 이 보안 주체에 제공됨을 나타냅니다.  
  
 AS *SQL_Server_login*  
 이 쿼리를 실행하는 보안 주체가 사용 권한을 부여하는 권한을 부여할 수 있는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 지정합니다.  
  
## <a name="remarks"></a>주의  
 현재 데이터베이스는 경우에 서버 범위의 사용 권한은 부여할 수 **마스터**합니다.  
  
 가용성 그룹에 대 한 정보는 [sys.availability_groups&#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md) 카탈로그 뷰에 있습니다. 서버 사용 권한 정보에 표시 됩니다는 [sys.server_permissions](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md) 카탈로그 뷰 및 서버 보안 주체에 대 한 정보에 표시 되는 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) 카탈로그 뷰.  
  
 가용성 그룹은 서버 수준의 보안 개체입니다. 다음 표에는 가용성 그룹에 부여할 수 있는 가장 구체적이고 제한된 사용 권한과 함께 의미상 이러한 사용 권한을 포함하는 보다 일반적인 사용 권한이 나열되어 있습니다.  
  
|가용성 그룹 사용 권한|가용성 그룹 사용 권한에 포함된 사용 권한|서버 사용 권한에 포함된 사용 권한|  
|-----------------------------------|----------------------------------------------|----------------------------------|  
|ALTER|CONTROL|ALTER ANY AVAILABILITY GROUP|  
|CONNECT|CONTROL|CONTROL SERVER|  
|CONTROL|CONTROL|CONTROL SERVER|  
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|  
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|  
  
 모든 차트에 대 한 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 사용 권한 참조 [데이터베이스 엔진 권한 포스터](http://go.microsoft.com/fwlink/?LinkId=229142)합니다.  
  
## <a name="permissions"></a>Permissions  
 가용성 그룹에 대한 CONTROL 권한 또는 서버에 대한 ALTER ANY AVAILABILTIY GROUP 권한이 필요합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-granting-view-definition-permission-on-an-availability-group"></a>1. 가용성 그룹에 대한 VIEW DEFINITION 권한 부여  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인 `VIEW DEFINITION`에 가용성 그룹 `MyAg`에 대한 `ZArifin` 권한을 부여합니다.  
  
```  
USE master;  
GRANT VIEW DEFINITION ON AVAILABILITY GROUP::MyAg TO ZArifin;  
GO  
```  
  
### <a name="b-granting-take-ownership-permission-with-the-grant-option"></a>2. GRANT OPTION을 지정하여 TAKE OWNERSHIP 권한 부여  
 다음 예에서는 `TAKE OWNERSHIP`으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 `MyAg`에 가용성 그룹 `PKomosinski`에 대한 `GRANT OPTION` 권한을 부여합니다.  
  
```  
USE master;  
GRANT TAKE OWNERSHIP ON AVAILABILITY GROUP::MyAg TO PKomosinski   
    WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-control-permission-on-an-availability-group"></a>3. 가용성 그룹에 대한 CONTROL 권한 부여  
 다음 예에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 사용자 `CONTROL`에 가용성 그룹 `MyAg`에 대한 `PKomosinski` 권한을 부여합니다. CONTROL 권한이 있으면 가용성 그룹의 소유자가 아니더라도 가용성 그룹에 대한 완벽한 로그인 제어를 할 수 있습니다. 소유권을 변경 하려면 참조 [ALTER authorization&#40; Transact SQL &#41; ](../../t-sql/statements/alter-authorization-transact-sql.md).  
  
```  
USE master;  
GRANT CONTROL ON AVAILABILITY GROUP::MyAg TO PKomosinski;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [REVOKE 가용성 그룹 사용 권한 &#40; Transact SQL &#41;](../../t-sql/statements/revoke-availability-group-permissions-transact-sql.md)   
 [가용성 그룹 사용 권한 &#40; 거부 Transact SQL &#41;](../../t-sql/statements/deny-availability-group-permissions-transact-sql.md)   
 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [sys.availability_groups&#40; Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [AlwaysOn 가용성 그룹 카탈로그 뷰 &#40; Transact SQL &#41; ](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md) [사용 권한 &#40; 데이터베이스 엔진 &#41;](../../relational-databases/security/permissions-database-engine.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
