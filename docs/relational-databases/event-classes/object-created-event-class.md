---
title: "Object:Created 이벤트 클래스 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Object:Created event class
ms.assetid: 57536924-5e66-4b09-a76d-8fcea2131771
caps.latest.revision: 32
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 25cdce0deb228a8a02688a8b01fa3995c5230f6b
ms.lasthandoff: 04/11/2017

---
# <a name="objectcreated-event-class"></a>Object:Created 이벤트 클래스
  Object:Created 이벤트 클래스는 CREATE INDEX, CREATE TABLE, CREATE DATABASE 문 등을 사용하여 개체가 생성되었음을 나타냅니다.  
  
 이 이벤트 클래스를 사용하여 때때로 임시 저장 프로시저를 만드는 ODBC 응용 프로그램 등을 사용하여 개체가 생성되는지 여부를 확인할 수 있습니다. LoginName 및 NTUserName 데이터 열을 모니터링하면 개체를 생성, 삭제 또는 액세스하는 사용자의 이름을 확인할 수 있습니다.  
  
## <a name="objectcreated-event-class-data-columns"></a>Object:Created 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|설명|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|**nvarchar**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|10|예|  
|ClientProcessID|**int**|클라이언트 응용 프로그램이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|예|  
|DatabaseID|**int**|USE *database* 문에서 지정한 데이터베이스 ID이거나, 지정한 인스턴스에 대해 USE *database* 문을 실행하지 않은 경우 기본 데이터베이스입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에 ServerName 데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|예|  
|DatabaseName|**nvarchar**|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|예|  
|EventClass|**int**|이벤트 유형 = 46|27|아니요|  
|EventSequence|**int**|요청 내의 지정된 이벤트 시퀀스입니다.|51|아니요|  
|EventSubClass|**int**|이벤트 하위 클래스의 유형입니다.<br /><br /> 0=시작<br /><br /> 1=커밋<br /><br /> 2=롤백|21|예|  
|GroupID|**int**|SQL 추적 이벤트가 발생한 작업 그룹의 ID입니다.|66|예|  
|HostName|**nvarchar**|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|예|  
|IndexID|**int**|이벤트에 의해 영향 받는 개체의 인덱스 ID입니다. 개체의 인덱스 ID를 확인하려면 sys.indexes 카탈로그 뷰의 index_id 열을 사용합니다.|24|예|  
|IntegerData|**int**|추적에서 캡처된 이벤트 클래스에 의존하는 정수 값입니다.|25|예|  
|IsSystem|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|예|  
|LoginName|**nvarchar**|사용자 로그인 이름이며 DOMAIN\username 형식의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 보안 로그인입니다.|11|예|  
|LoginSid|**image**|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 sys.server_principals 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|예|  
|NTDomainName|**nvarchar**|사용자가 속한 Windows 도메인입니다.|7|예|  
|NTUserName|**nvarchar**|Windows 사용자 이름입니다.|6|예|  
|ObjectID|**int**|시스템이 할당한 개체의 ID입니다.|22|예|  
|ObjectID2|**bigint**|관련 개체 또는 엔터티의 ID입니다.|56|예|  
|ObjectName|**nvarchar**|참조되는 개체의 이름입니다.|34|예|  
|ObjectType|**int**|이벤트와 관련된 개체 유형을 나타내는 값입니다. 이 값은 sys.objects의 유형 열과 일치합니다. 값은 [ObjectType 추적 이벤트 열](../../relational-databases/event-classes/objecttype-trace-event-column.md)을 참조하세요.|28|예|  
|RequestID|**int**|문을 포함하는 요청의 ID입니다.|49|예|  
|ServerName|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니요|  
|SessionLoginName|**nvarchar**|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행할 경우 SessionLoginName은 Login1을 표시하고 LoginName은 Login2를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|예|  
|SPID|**int**|이벤트가 발생한 세션의 ID입니다.|12|예|  
|StartTime|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|예|  
|TransactionID|**bigint**|시스템이 할당한 트랜잭션의 ID입니다.|4|예|  
|XactSequence|**bigint**|현재 트랜잭션을 설명하는 토큰입니다.|50|예|  
  
## <a name="see-also"></a>참고 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  