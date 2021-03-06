---
title: sp_lookupcustomresolver (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_lookupcustomresolver_TSQL
- sp_lookupcustomresolver
helpviewer_keywords:
- sp_lookupcustomresolver
ms.assetid: 356a7b8a-ae53-4fb5-86ee-fcfddbf23ddd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 02f0d4df65f9c93465b7bd79d3a21d192d302804
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688323"
---
# <a name="splookupcustomresolver-transact-sql"></a>sp_lookupcustomresolver(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  비즈니스 논리 처리기 또는 배포자에 등록된 COM 기반 사용자 지정 해결 프로그램 구성 요소의 CLSID(클래스 식별자) 값에 대한 정보를 반환합니다. 이 저장 프로시저는 게시 데이터베이스의 게시자에서 실행됩니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
sp_lookupcustomresolver [ @article_resolver = ] 'article_resolver'   
    [, [ @resolver_clsid = ] 'resolver_clsid' OUTPUT ]  
    [ , [ @is_dotnet_assembly = ] is_dotnet_assembly OUTPUT ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' OUTPUT ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' OUTPUT ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>인수  
 [  **@article_resolver =** ] **'***article_resolver***'**  
 등록을 취소할 사용자 지정 비즈니스 논리의 이름을 지정합니다. *article_resolver* 됩니다 **nvarchar(255)**, 기본값은 없습니다. 제거할 비즈니스 논리가 COM 구성 요소이면 이 매개 변수는 해당 구성 요소의 이름이며 비즈니스 논리가 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework 어셈블리이면 이 매개 변수는 어셈블리의 이름입니다.  
  
 [ **@resolver_clsid**=] **'***resolver_clsid***'** 출력  
 지정 된 사용자 지정 비즈니스 논리의 이름과 연결 된 COM 개체의 CLSID 값을 *article_resolver* 매개 변수입니다. *resolver_clsid* 됩니다 **nvarchar (50)**, 기본값은 NULL입니다.  
  
 [  **@is_dotnet_assembly=** ] **'***is_dotnet_assembly***'** 출력  
 등록할 사용자 지정 비즈니스 논리의 유형을 지정합니다. *is_dotnet_assembly* 됩니다 **비트**, 기본값은 0입니다. **1** 등록할 사용자 지정 비즈니스 논리가 비즈니스 논리 처리기 어셈블리 임을 나타냅니다 **0** 은 COM 구성 요소임을 나타냅니다.  
  
 [  **@dotnet_assembly_name=** ] **'***dotnet_assembly_name***'** 출력  
 비즈니스 논리 처리기를 구현하는 어셈블리의 이름입니다. *dotnet_assembly_name* 됩니다 **nvarchar(255)**, 기본값은 NULL입니다.  
  
 [  **@dotnet_class_name=** ] **'***dotnet_class_name***'** 출력  
 비즈니스 논리 처리기를 구현하도록 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule>을 재정의하는 클래스의 이름입니다. *dotnet_class_name* 됩니다 **nvarchar(255)**, 기본값은 NULL입니다.  
  
 [  **@publisher=** ] **'***게시자***'**  
 게시자의 이름입니다. *게시자* 됩니다 **sysname**, 기본값은 NULL입니다. 저장 프로시저가 게시자에서 호출되지 않을 경우 이 매개 변수를 사용하십시오. 지정하지 않으면 로컬 서버가 게시자인 것으로 가정합니다.  
  
## <a name="return-code-values"></a>반환 코드 값  
 **0** (성공) 또는 **1** (실패)  
  
## <a name="remarks"></a>Remarks  
 **sp_lookupcustomresolver** 병합 복제에 사용 됩니다.  
  
 **sp_lookupcustomresolver** 에 대 한 NULL 값을 반환 *resolver_clsid* 경우 구성 요소에 등록 되지 않았습니다 "00000000-0000-0000-0000-000000000000"의 값과 분포 등록에 속하는 경우는 .NET 어셈블리 비즈니스 논리 처리기로 등록 합니다.  
  
 **sp_lookupcustomresolver** 호출한 [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) 하 고 [sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) 지정 된 유효성 검사를 *article_resolver*합니다.  
  
## <a name="permissions"></a>사용 권한  
 멤버는 **db_owner** 게시 데이터베이스의 고정된 데이터베이스 역할을 실행할 수 있습니다 **sp_lookupcustomresolver**합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)   
 [병합 동기화 중 비즈니스 논리 실행](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)   
 [병합 아티클에 대한 비즈니스 논리 처리기 구현](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [병합 아티클 해결 프로그램 지정](../../relational-databases/replication/publish/specify-a-merge-article-resolver.md)   
 [sp_registercustomresolver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-registercustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [시스템 저장 프로시저&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
