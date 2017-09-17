---
title: CREATE LOGIN (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 06/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: f64c2f34c7e0c2d8c768b5a846465a65ed51082d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="create-login-transact-sql"></a>CREATE LOGIN(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 대한 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 로그인을 만듭니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
-- Syntax for SQL Server  
  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE LOGIN login_name  
 { WITH <option_list3> }  
  
<option_list3> ::=   
    PASSWORD = { 'password' }  
    [ SID = sid ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  
  
## <a name="arguments"></a>인수  
 *login_name*  
 만들 로그인 이름을 지정합니다. 로그인에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인, Windows 로그인, 인증서 매핑 로그인 및 비대칭 키 매핑 로그인의 네 가지 유형이 있습니다. Windows 2000 이전 버전 사용자 로그온 이름 형식으로 사용 해야 Windows 도메인 계정에서 매핑된 로그인을 만들 때 [\<도메인 이름 >\\< login_name >]. 형식에 UPN을 사용할 수 없습니다 login_name@DomainName합니다. 이 항목의 뒷부분에 나오는 예 4를 참조하세요. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인증 로그인은 형식 **sysname** 규칙을 따라야 합니다 [식별자](http://msdn.microsoft.com/library/ms175874.aspx) 포함할 수 없습니다는 '**\\**'. Windows 로그인은 '**\\**'를 포함할 수 없습니다. Active Directory 사용자를 기반으로 로그인 21 보다 작은 문자 이름으로 제한 됩니다.  
  
 암호 **='***암호***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에만 적용됩니다. 만들 로그인의 암호를 지정합니다. 강력한 암호를 사용해야 합니다. 자세한 내용은 참조 [Strong Passwords](../../relational-databases/security/strong-passwords.md) 및 [암호 정책](../../relational-databases/security/password-policy.md)합니다. 부터는 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]저장 된 암호 정보가 솔트된 암호의 s h A-512를 사용 하 여 계산 됩니다.  
  
 암호는 대소문자를 구분합니다. 암호의 길이는 항상 8자 이상이어야 하며 128자를 초과할 수 없습니다.  암호에는 a-z, A-Z, 0-9 및 영숫자가 아닌 대부분의 문자를 포함할 수 있습니다. 암호에 작은따옴표를 포함할 수 없습니다 또는 *login_name*합니다.  
  
 암호  **=**  *hashed_password*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 HASHED 키워드에만 적용됩니다. 만들 로그인에 대한 암호의 해시된 값을 지정합니다.  
  
 HASHED  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에만 적용됩니다. PASSWORD 인수 다음에 입력한 암호가 이미 해시되었음을 지정합니다. 이 옵션을 선택하지 않으면 암호로 입력한 문자열이 데이터베이스에 저장되기 전에 해시됩니다. 이 옵션은 두 서버 간에 데이터베이스를 마이그레이션하는 데에만 사용해야 합니다. HASHED 옵션을 사용하여 새 로그인을 만들면 안 됩니다. HASHED  옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7  또는 그 이전 버전에서 만든 해시와 함께 사용할 수 없습니다.  
  
 MUST_CHANGE  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에만 적용됩니다. 이 옵션을 선택한 경우 새 로그인을 처음 사용할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 새 암호를 묻는 메시지를 표시합니다.  
  
 자격 증명  **=**  *credential_name*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 새 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에 매핑할 자격 증명의 이름입니다. 자격 증명이 서버에 이미 있어야 합니다. 현재 이 옵션은 자격 증명을 로그인에 연결하는 역할만 합니다. 자격 증명을 시스템 관리자 (sa) 로그인에 매핑할 수 없습니다.  
  
 SID = *sid*  
 로그인을 다시 만드는데 사용됩니다. 적용 대상 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인에만 Windows 인증 로그인 하지 않습니다. 새 SID를 지정 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인 합니다. 이 옵션을 사용 하지 않는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 자동으로 SID를 할당 합니다. SID 구조에 따라 달라 집니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 버전입니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]로그인 SID: 16 바이트 (**binary (16)**)는 GUID를 기반으로 한 리터럴 값입니다. 예를 들면 `SID = 0x14585E90117152449347750164BA00A7`입니다.  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)]로그인 SID:에 유효한 SID 구조 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]합니다. 일반적으로 이것은 32 바이트 (**binary(32)**)로 구성 된 리터럴 `0x01060000000000640000000000000000` 16 바이트 GUID를 나타내는 더하기 합니다. 예를 들면 `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`입니다.  
  
DEFAULT_DATABASE  **=**  *데이터베이스*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 로그인에 할당할 기본 데이터베이스를 지정합니다. 이 옵션을 선택하지 않으면 기본 데이터베이스가 master로 설정됩니다.  
  
DEFAULT_LANGUAGE  **=**  *언어*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 로그인에 할당할 기본 언어를 지정합니다. 이 옵션을 선택하지 않으면 기본 언어가 서버의 현재 기본 언어로 설정됩니다. 나중에 서버의 기본 언어가 변경되더라도 로그인의 기본 언어는 그대로 유지됩니다.  
  
CHECK_EXPIRATION  **=**  {ON | **OFF** }  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에만 적용됩니다. 이 로그인에 암호 만료 정책을 적용할지 여부를 지정합니다. 기본값은 OFF입니다.  
  
CHECK_POLICY  **=**  { **ON** | OFF}  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인에만 적용됩니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 실행 중인 컴퓨터의 Windows  암호 정책을 이 로그인에 적용하도록 지정합니다. 기본값은 ON입니다.  
  
 Windows 정책에 따라 강력한 암호가 필요한 경우에는 암호에 다음 네 가지 문자 중 세 가지 이상을 포함해야 합니다.  
  
-   대문자(A-Z)  
-   소문자(a-z)  
-   숫자(0-9)  
-   영숫자가 아닌 문자 중 하나(예: 공백, _, @, *, ^, %, !, $, # 또는 &)  
  
WINDOWS  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 로그인이 Windows 로그인에 매핑되도록 지정합니다.  
  
인증서 *certname*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 이 로그인과 연결될 인증서의 이름을 지정합니다. 이 인증서는 master 데이터베이스에 이미 있어야 합니다.  
  
비대칭 키 *asym_key_name*  
 **적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
 이 로그인과 연결될 비대칭 키의 이름을 지정합니다. 이 키는 master 데이터베이스에 이미 있어야 합니다.  
  
## <a name="remarks"></a>주의  
 암호는 대소문자를 구분합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 로그인을 만들 때만 암호를 미리 해시할 수 있습니다.  
  
 MUST_CHANGE를 지정한 경우에는 CHECK_EXPIRATION  및 CHECK_POLICY를 ON으로 설정해야 합니다. 그렇지 않으면 문이 실패합니다.  
  
 CHECK_POLICY = OFF와 CHECK_EXPIRATION = ON의 조합은 지원되지 않습니다.  
  
 CHECK_POLICY를 OFF로 설정한 경우 *lockout_time* 다시 설정 되 고 CHECK_EXPIRATION이 OFF로 설정 합니다.  
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION  및 CHECK_POLICY는 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 이상 버전에서만 적용됩니다. 자세한 내용은 [Password Policy](../../relational-databases/security/password-policy.md)을 참조하세요.  
  
 인증서나 비대칭 키에서 만든 로그인은 코드 서명 용도로만 사용되며 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결할 때는 사용할 수 없습니다. 인증서나 비대칭 키가 master 데이터베이스에 이미 있는 경우에만 인증서나 비대칭 키에서 로그인을 만들 수 있습니다.  
  
 로그인을 전송하는 스크립트는 [SQL Server 2005와 SQL Server 2008 인스턴스 간에 로그인 및 암호를 전송하는 방법](http://support.microsoft.com/kb/918992)을 참조하세요.  
  
 로그인을 만들면 새 로그인이 자동으로 사용하도록 설정되고 해당 로그인에 서버 수준 **CONNECT SQL** 권한이 부여됩니다.  
  
 권한 시스템 디자인에 대한 정보는 [Getting Started with Database Engine Permissions](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)을(를) 참조하세요.  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-and-includesssdwincludessssdw-mdmd-logins"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]및 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 로그인  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)], **CREATE LOGIN** 문은 일괄 처리에서 유일한 문 이어야 합니다.  
  
 에 연결 하는 몇 가지 방법에서 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]와 같은 **sqlcmd**를 추가 해야는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 서버 이름을 사용 하 여 연결 문자열의 로그인 이름에는  *\<로그인 >* @  *\<서버 >* 표기법입니다. 예를 들어 로그인이 `login1` 및의 정규화 된 이름을 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 서버는 `servername.database.windows.net`, *username* 연결 문자열의 매개 변수 여야 `login1@servername`합니다. 때문에의 총 길이 *username* 매개 변수는 128 자 *login_name* 서버 이름의 길이 만큼 뺀 길이로 127 자로 제한 됩니다. 이 예에서는 `login_name`이 10자이므로 `servername`에는 117자까지만 사용할 수 있습니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 및 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 로그인을 만들려면 master 데이터베이스에 연결 해야 합니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]규칙을 만들 수는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식에서 인증 로그인 \<loginname > @\<서버 이름 >. 경우에 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 서버는 **myazureserver** 고 로그인이  **myemail@live.com** , 로그인을 제공 해야 합니다  **myemail@live.com @myazureserver**  .  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)], 한 연결을 인증 하는 데 필요한 로그인 데이터 및 서버 수준 방화벽 규칙은 각 데이터베이스에 일시적으로 캐시 됩니다. 이 캐시는 주기적으로 새로 고쳐집니다. 인증 캐시 새로 고침을 데이터베이스에 최신 버전의 로그인 테이블에 있는지 확인 하려면 실행할 [DBCC FLUSHAUTHCACHE &#40; Transact SQL &#41; ](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
 에 대 한 자세한 내용은 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 로그인, 참조 [데이터베이스 및 Windows Azure SQL 데이터베이스에서 로그인 관리](http://msdn.microsoft.com/library/ee336235.aspx)합니다.  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 필요 **ALTER ANY LOGIN** 서버 또는 구성원에 대 한 권한이 **securityadmin** 고정된 서버 역할입니다.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]에서는 프로비전 프로세스를 통해 만들어진 서버 수준의 보안 주체 로그인이나 master  데이터베이스에서 `loginmanager` 데이터베이스 역할이 할당된 멤버만 새 로그인을 만들 수 있습니다.  
  
 **CREDENTIAL** 옵션을 사용하는 경우에는 서버에 대한 **ALTER ANY CREDENTIAL** 권한도 필요합니다.  
  
## <a name="next-steps"></a>다음 단계  
 로그인을 만든 후 로그인에 연결할 수는 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 또는 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] 에 부여 된 권한을 되었지만 **공용** 역할입니다. 다음 작업 중 일부를 수행하는 것이 좋습니다.  
  
-   데이터베이스에 연결하려면 로그인에 대한 데이터베이스 사용자를 만듭니다. 자세한 내용은 [CREATE USER&#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)를 참조하세요.  
  
-   사용자 정의 서버 역할을 사용 하 여 만들 [CREATE SERVER role&#40; Transact SQL &#41; ](../../t-sql/statements/create-server-role-transact-sql.md). **ALTER SERVER ROLE** 사용… **멤버 추가** 사용자 정의 서버 역할에 새 로그인을 추가 합니다. 자세한 내용은 참조 [CREATE SERVER role&#40; Transact SQL &#41; ](../../t-sql/statements/create-server-role-transact-sql.md) 및 [ALTER SERVER role&#40; Transact SQL &#41; ](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
-   사용 하 여 **sp_addsrvrolemember** 고정된 서버 역할에는 로그인을 추가 합니다. 자세한 내용은 참조 [서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md) 및 [sp_addsrvrolemember &#40; Transact SQL &#41; ](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
-   사용 하 여는 **GRANT** 새 로그인 또는 로그인이 포함 된 역할에 서버 수준 사용 권한을 부여 하 여 문을 합니다. 자세한 내용은 [GRANT&#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)를 참조하세요.  
  
## <a name="examples"></a>예  
  
### <a name="a-creating-a-login-with-a-password"></a>1. 암호로 로그인 만들기  
 다음 예에서는 특정 사용자에 대한 로그인을 만들고 암호를 할당합니다.  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password"></a>2. 암호로 로그인 만들기  
 다음 예에서는 특정 사용자에 대한 로그인을 만들고 암호를 할당합니다. `MUST_CHANGE` 옵션을 사용하는 경우 사용자는 서버에 처음 연결할 때 이 암호를 변경해야 합니다.  
  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' MUST_CHANGE;  
GO  
```  
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>3. 자격 증명에 매핑된 로그인 만들기  
 다음 예에서는 사용자를 사용하여 특정 사용자에 대한 로그인을 만듭니다. 이 로그인은 자격 증명에 매핑됩니다.  
  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>4. 인증서에서 로그인 만들기  
 다음 예에서는 master의 인증서에서 특정 사용자에 대 한 로그인을 만듭니다.  
  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
```  
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>5. Windows 도메인 계정에서 로그인 만들기  
 다음 예에서는 Windows 도메인 계정을 사용하여 로그인을 만듭니다.  
  
**적용 대상**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 부터 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]까지  
  
```  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>6. SID에서 로그인 만들기  
 다음 예에서는 먼저 만듭니다는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증 로그인의 경우 로그인의 SID를 결정 합니다.  
  
```  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 내 쿼리는 SID로 0x241C11948AEEB749B0D22646DB1A19F2를 반환합니다. 쿼리는 다른 값을 반환합니다. 다음 문은 로그인을 삭제한 후 로그인을 다시 만듭니다. 이전 쿼리의 SID를 사용합니다.  
  
```  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>예제:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>7. SQL Server 인증 로그인 암호를 사용 하 여 만들기  
 다음 예에서는 로그인 `Mary7` 암호로 `A2c3456`합니다.  
  
```tsql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>8. 옵션을 사용 하 여  
 다음 예에서는 로그인 `Mary8` 암호로 일부 선택적 인수입니다.  
  
```  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>9. Windows 도메인 계정에서 로그인 만들기  
 다음 예제에서는 명명 된 Windows 도메인 계정에서 로그인을 만든 `Mary` 에 `Contoso` 도메인입니다.  
  
```  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [데이터베이스 엔진 권한 시작](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [보안 주체&#40;데이터베이스 엔진&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [암호 정책](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP login&#40; Transact SQL &#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA&#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [로그인 만들기](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
