---
title: Deprecation Final Support 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Deprecation Final Support event class
- deprecation [SQL Server], events final support
ms.assetid: 2b4d88d0-62be-45c0-bea8-c5900d553d31
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3187c30d3c39bfc488baf260f4b6061de5acb942
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48145870"
---
# <a name="deprecation-final-support-event-class"></a>Deprecation Final Support 이벤트 클래스
  **Deprecation Final Support** 이벤트 클래스는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 다음 번 주요 릴리스에서 제거할 기능을 사용할 때 발생합니다. 애플리케이션을 오랫동안 유지하려면 **Deprecation Final Support** 이벤트 클래스 또는 **Deprecation Announcement** 이벤트 클래스가 발생되는 기능을 사용하지 마십시오. 곧 사용이 중단될 예정인 기능을 사용하는 애플리케이션은 최대한 빨리 수정하십시오.  
  
## <a name="deprecation-final-support-event-class-data-columns"></a>Deprecation Final Support 이벤트 클래스 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|ApplicationName|`nvarchar`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 애플리케이션에서 전달한 값으로 채워집니다.|10|사용자 계정 컨트롤|  
|ClientProcessID|`int`|클라이언트 애플리케이션이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|사용자 계정 컨트롤|  
|DatabaseID|`int`|USE *database* 문에서 지정한 데이터베이스 ID이거나, 지정한 인스턴스에 대해 USE *database* 문을 실행하지 않은 경우 기본 데이터베이스입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 데이터베이스의 이름이 표시는 `ServerName` 데이터 열이 추적에서 캡처되고 서버를 사용할 수 있습니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|DatabaseName|`nvarchar`|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|사용자 계정 컨트롤|  
|EventClass|`int`|이벤트 유형 = 126|27|아니요|  
|EventSequence|`int`|요청 내에 지정된 이벤트 시퀀스입니다.|51|아니요|  
|HostName|`nvarchar`|클라이언트를 실행 중인 컴퓨터 이름입니다. 클라이언트가 호스트 이름을 제공할 경우 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|사용자 계정 컨트롤|  
|IntegerData2|`int`|실행 중인 문의 종료 오프셋(바이트)입니다.|55|사용자 계정 컨트롤|  
|IsSystem|`int`|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|사용자 계정 컨트롤|  
|LoginName|`nvarchar`|사용자 로그인 이름이며 DOMAIN\username 형식의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows 로그인 자격 증명 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 보안 로그인입니다.|11|사용자 계정 컨트롤|  
|LoginSid|`image`|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 **sys.server_principals** 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|사용자 계정 컨트롤|  
|NTDomainName|`nvarchar`|사용자가 속한 Windows 도메인입니다.|7|사용자 계정 컨트롤|  
|NTUserName|`nvarchar`|Windows 사용자 이름입니다.|6|사용자 계정 컨트롤|  
|Offset|`int`|저장 프로시저나 일괄 처리 내에 있는 문의 시작 오프셋입니다.|61|사용자 계정 컨트롤|  
|ObjectID|`int`|사용되지 않는 기능의 ID 번호입니다.|22|사용자 계정 컨트롤|  
|ObjectName|`nvarchar`|사용되지 않는 기능의 이름입니다.|34|사용자 계정 컨트롤|  
|RequestID|`int`|문을 포함하는 요청의 ID입니다.|49|사용자 계정 컨트롤|  
|데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면|`nvarchar`|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니요|  
|SessionLoginName|`nvarchar`|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어, 연결 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Login1을 사용 하 여 고 고 Login2로 문을 `SessionLoginName` 은 Login1을 표시 하 고 `LoginName` 은 Login2를 표시 합니다. 이 열에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 Windows 로그인이 모두 표시됩니다.|64|사용자 계정 컨트롤|  
|SPID|`int`|이벤트가 발생한 세션의 ID입니다.|12|사용자 계정 컨트롤|  
|SqlHandle|`image`|SQL 일괄 처리나 저장 프로시저를 식별하는 데 사용할 수 있는 이진 핸들입니다.|63|사용자 계정 컨트롤|  
|StartTime|`datetime`|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|사용자 계정 컨트롤|  
|TextData|`ntext`|추적에서 캡처된 이벤트 클래스에 따라 달라지는 텍스트 값입니다.|1|사용자 계정 컨트롤|  
|TransactionID|`bigint`|시스템이 할당한 트랜잭션의 ID입니다.|4|사용자 계정 컨트롤|  
|XactSequence|`bigint`|현재 트랜잭션을 설명하는 토큰입니다.|50|사용자 계정 컨트롤|  
  
## <a name="see-also"></a>관련 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)   
 [Deprecation Announcement 이벤트 클래스](deprecation-announcement-event-class.md)   
 [SQL Server 2014에서 사용되지 않는 데이터베이스 엔진 기능](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)  
  
  
