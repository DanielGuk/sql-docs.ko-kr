---
title: sp_delete_proxy (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_delete_proxy
- sp_delete_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_delete_proxy
- DROP PROXY statement
ms.assetid: 44a1db13-b7f2-4dab-a1b5-b8dafb41737c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1db08d96a36112d686ab34db0b7989e910a01960
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47844061"
---
# <a name="spdeleteproxy-transact-sql"></a>sp_delete_proxy(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  지정한 프록시를 제거합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_delete_proxy [ @proxy_id = ] id , [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>인수  
 [ **@proxy_id**= ] *id*  
 제거할 프록시의 프록시 ID입니다. 합니다 *proxy_id* 됩니다 **int**, 기본값은 NULL 사용 하 여 합니다.  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 제거할 프록시의 이름입니다. 합니다 *proxy_name* 됩니다 **sysname**, 기본값은 NULL 사용 하 여 합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="result-sets"></a>결과 집합  
 없음  
  
## <a name="remarks"></a>Remarks  
 어느 **@proxy_name** 하거나 **@proxy_id** 지정 해야 합니다. 두 인수가 모두 지정될 경우 두 인수는 같은 프록시를 참조해야 합니다. 그렇지 않으면 저장 프로시저가 실패합니다.  
  
 작업 단계가 지정된 프록시를 참조할 경우 해당 프록시는 삭제할 수 없으며 저장 프로시저가 실패합니다.  
  
## <a name="permissions"></a>사용 권한  
 기본적으로의 멤버만 합니다 **sysadmin** 고정된 서버 역할을 실행할 수 있습니다 **sp_delete_proxy**합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 `Catalog application proxy`라는 프록시를 삭제합니다.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_delete_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [sp_add_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)  
  
  
