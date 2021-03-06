---
title: Plan Guide Unsuccessful 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Plan Guide Unsuccessful event class
ms.assetid: ef9759f8-5613-4884-9257-86b609313f69
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: d2b5f3e49cbc458737dc0029e5678483d5e969cf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47649461"
---
# <a name="plan-guide-unsuccessful-event-class"></a>Plan Guide Unsuccessful 이벤트 클래스
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Plan Guide Unsuccessful 이벤트 클래스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 계획 지침이 포함된 쿼리 또는 일괄 처리에 대한 실행 계획을 만들지 못했음을 나타냅니다. 이 경우 계획 지침을 사용하지 않은 채 계획이 컴파일됩니다. 다음과 같은 경우 이 이벤트가 발생합니다.  
  
-   계획 지침 정의에 있는 일괄 처리/모듈이 실행 중인 일괄 처리와 일치하는 경우  
  
-   계획 지침 정의에 있는 쿼리가 실행 중인 쿼리와 일치하는 경우  
  
-   USE PLAN 힌트를 비롯하여 계획 지침 정의에 있는 힌트가 쿼리나 일괄 처리에 성공적으로 적용되지 않은 경우 (즉, 컴파일된 쿼리 계획에 지정된 힌트를 적용할 수 없고 계획 지침을 사용하지 않은 채 계획이 컴파일된 경우)  
  
 잘못된 계획 지침은 이 이벤트를 발생시킬 수 있습니다. [sys.fn_validate_plan_guide](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md) 함수를 사용하여 쿼리나 일괄 처리에서 사용하는 계획 지침의 유효성을 검사하고 이 함수가 보고하는 오류를 수정합니다.  
  
 이 이벤트는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 튜닝 템플릿에 포함되어 있습니다.  
  
## <a name="plan-guide-unsuccessful-event-class-data-columns"></a>Plan Guide Unsuccessful 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|설명|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 애플리케이션에서 전달한 값으로 채워집니다.|10|사용자 계정 컨트롤|  
|ClientProcessID|**int**|클라이언트 애플리케이션이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|사용자 계정 컨트롤|  
|DatabaseID|**int**|USE *database* 문에서 지정한 데이터베이스 ID이거나, 지정한 인스턴스에 대해 USE *database* 문을 실행하지 않은 경우 기본 데이터베이스입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에 ServerName 데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|DatabaseName|**nvarchar**|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|사용자 계정 컨트롤|  
|EventClass|**int**|이벤트 유형 = 218|27|아니오|  
|EventSequence|**int**|요청 내의 특정 이벤트 시퀀스입니다.|51|아니오|  
|HostName|**nvarchar**|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공할 경우 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|사용자 계정 컨트롤|  
|IsSystem|**int**|이벤트가 시스템 프로세스에서 발생했는지, 아니면 사용자 프로세스에서 발생했는지를 나타냅니다(1 = 시스템, 0 = 사용자).|60|사용자 계정 컨트롤|  
|LoginName|**nvarchar**|사용자 로그인 이름이며 DOMAIN [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] username [!INCLUDE[msCoName](../../includes/msconame-md.md)] 형식의\\*Windows 로그인 자격 증명 또는*보안 로그인입니다.|11|사용자 계정 컨트롤|  
|LoginSid|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 [sys.server_principals](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md) 또는 [sys.sql_logins](../../relational-databases/system-catalog-views/sys-sql-logins-transact-sql.md) 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|사용자 계정 컨트롤|  
|NTDomainName|**nvarchar**|사용자가 속한 Windows 도메인입니다.|7|사용자 계정 컨트롤|  
|NTUserName|**nvarchar**|Windows 사용자 이름입니다.|6|사용자 계정 컨트롤|  
|ObjectID|**int**|계획 지침을 적용할 때 실행 중이던 모듈의 개체 ID입니다. 계획 지침이 모듈에 적용되지 않은 경우 이 열은 NULL로 설정됩니다.|22|사용자 계정 컨트롤|  
|RequestID|**int**|문을 포함하는 요청의 ID입니다.|49|사용자 계정 컨트롤|  
|데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니오|  
|SessionLoginName|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 SessionLoginName은 Login1을 표시하고 LoginName은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|사용자 계정 컨트롤|  
|SPID|**int**|이벤트가 발생한 세션의 ID입니다.|12|사용자 계정 컨트롤|  
|StartTime|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|사용자 계정 컨트롤|  
|TextData|**ntext**|계획 지침의 이름입니다.|1|사용자 계정 컨트롤|  
|TransactionID|**bigint**|시스템이 할당한 트랜잭션의 ID입니다.|4|사용자 계정 컨트롤|  
|XactSequence|**bigint**|현재 트랜잭션을 설명하는 토큰입니다.|50|사용자 계정 컨트롤|  
  
## <a name="see-also"></a>참고 항목  
 [Plan Guide Successful 이벤트 클래스](../../relational-databases/event-classes/plan-guide-successful-event-class.md)   
 [확장 이벤트](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sys.fn_validate_plan_guide&#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-validate-plan-guide-transact-sql.md)   
 [sp_create_plan_guide&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)   
 [sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
  
