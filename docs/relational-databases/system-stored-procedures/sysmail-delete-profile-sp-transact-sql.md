---
title: sysmail_delete_profile_sp (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysmail_delete_profile_sp
- sysmail_delete_profile_sp_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmail_delete_profile_sp
ms.assetid: 71998653-4a02-446d-b6f7-50646a29e8a2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c1f358385205c15954fe033a2f6631964a86fabc
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47793281"
---
# <a name="sysmaildeleteprofilesp-transact-sql"></a>sysmail_delete_profile_sp(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 메일에서 사용하는 메일 프로필을 삭제합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sysmail_delete_profile_sp  { [ @profile_id = ] profile_id | [ @profile_name = ] 'profile_name' }  
```  
  
## <a name="arguments"></a>인수  
 [ **@profile_id** = ] *profile_id*  
 삭제할 프로필의 ID입니다. *profile_id* 됩니다 **int**, 기본값은 NULL입니다. 어느 *profile_id* 하거나 *profile_name* 지정 해야 합니다.  
  
 [ **@profile_name** = ] **'***profile_name***'**  
 삭제할 프로필의 이름입니다. *profile_name* 됩니다 **sysname**, 기본값은 NULL입니다. 어느 *profile_id* 하거나 *profile_name* 지정 해야 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="remarks"></a>Remarks  
 프로필을 삭제해도 프로필에서 사용하는 계정은 삭제되지 않습니다.  
  
 이 저장 프로시저는 사용자가 프로필에 액세스할 수 있는지 여부에 관계없이 프로필을 삭제합니다. 사용자에 대 한 기본 개인 프로필이 나 기본 공개 프로필을 제거 하는 동안 주의 해야 합니다 **msdb** 데이터베이스입니다. 사용할 수 있으면 기본 프로필이 없을 **sp_send_dbmail** 인수로 프로필 이름이 필요 합니다. 따라서 기본 프로필을 제거 발생할 수 있습니다에 대 한 호출 **sp_send_dbmail** 실패 합니다. 자세한 내용은 [sp_send_dbmail &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-send-dbmail-transact-sql.md)합니다.  
  
 저장된 프로시저 **sysmail_delete_profile_sp** 에 **msdb** 데이터베이스 및 소유 하는 **dbo** 스키마입니다. 현재 데이터베이스에는 없는 경우 세 부분으로 된 이름을 사용 하 여 프로시저를 실행 해야 합니다 **msdb**합니다.  
  
## <a name="permissions"></a>사용 권한  
 이 프로시저 기본의 멤버에 대 한 권한을 실행 합니다 **sysadmin** 고정된 서버 역할입니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `AdventureWorks Administrator`라는 프로필을 삭제합니다.  
  
```  
EXECUTE msdb.dbo.sysmail_delete_profile_sp  
    @profile_name = 'AdventureWorks Administrator' ;  
```  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 메일](../../relational-databases/database-mail/database-mail.md)   
 [데이터베이스 메일 구성 개체](../../relational-databases/database-mail/database-mail-configuration-objects.md)   
 [데이터베이스 메일 저장 프로시저 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-mail-stored-procedures-transact-sql.md)  
  
  
