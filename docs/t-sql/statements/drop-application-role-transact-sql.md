---
title: DROP APPLICATION ROLE (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_APPLICATION_ROLE_TSQL
- DROP APPLICATION ROLE
dev_langs:
- TSQL
helpviewer_keywords:
- dropping application roles
- deleting application roles
- removing application roles
- application roles [SQL Server], removing
- DROP APPLICATION ROLE statement
ms.assetid: 44121ee7-ef40-405d-b03b-f8ddb4e3c559
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 326c0bb53e995aeacb807a91b83d69f59d034d2f
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="drop-application-role-transact-sql"></a>DROP APPLICATION ROLE(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  현재 데이터베이스에서 응용 프로그램 역할을 제거합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
DROP APPLICATION ROLE rolename  
```  
  
## <a name="arguments"></a>인수  
 *역할 이름*  
 삭제할 응용 프로그램 역할의 이름을 지정합니다.  
  
## <a name="remarks"></a>주의  
 보안 개체를 소유한 응용 프로그램 역할은 삭제할 수 없습니다. 보안 개체를 소유한 응용 프로그램 역할을 삭제하려면 먼저 보안 개체의 소유권을 이전하거나 보안 개체를 삭제해야 합니다.  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>Permissions  
 데이터베이스에 대한 ALTER ANY APPLICATION ROLE 권한이 필요합니다.  
  
## <a name="examples"></a>예  
 데이터베이스에서 응용 프로그램 역할 "weekly_ledger"를 삭제합니다.  
  
```  
DROP APPLICATION ROLE weekly_ledger;  
GO  
```  
  
## <a name="see-also"></a>관련 항목:  
 [응용 프로그램 역할](../../relational-databases/security/authentication-access/application-roles.md)   
 [APPLICATION role&#40; 만들기 Transact SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [ALTER APPLICATION role&#40; Transact SQL &#41;](../../t-sql/statements/alter-application-role-transact-sql.md)   
 [EVENTDATA&#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)  
  
  