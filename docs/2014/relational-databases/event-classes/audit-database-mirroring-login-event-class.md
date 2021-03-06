---
title: Audit Database Mirroring Login 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- Audit Database Mirroring Login event class
- database mirroring [SQL Server], event notifications
ms.assetid: d0bd436d-aade-4208-a7e5-75cf3b5d0ce9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8d2c920a2b7341b75f85c2c9cf46bc381d607e1d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48128863"
---
# <a name="audit-database-mirroring-login-event-class"></a>Audit Database Mirroring Login 이벤트 클래스
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 **Audit Database Mirroring Login** 이벤트를 만들어 데이터베이스 미러링 전송 보안과 관련된 감사 메시지를 보고합니다.  
  
## <a name="audit-database-mirroring-login-event-class-data-columns"></a>Audit Database Mirroring Login 이벤트 클래스 데이터 열  
  
|데이터 열|형식|Description|열 번호|필터 가능|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|이 이벤트 클래스에서는 사용되지 않습니다.|10|사용자 계정 컨트롤|  
|**ClientProcessID**|**int**|이 이벤트 클래스에서는 사용되지 않습니다.|9|사용자 계정 컨트롤|  
|**DatabaseID**|**int**|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] ServerName **데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면** 에 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|**EventClass**|**int**|캡처된 이벤트 클래스 유형입니다. **Audit Database Mirroring Login** 에 대해서는 항상 **154**입니다.|27|아니요|  
|**EventSequence**|**int**|이 이벤트의 시퀀스 번호입니다.|51|아니요|  
|**EventSubClass**|**int**|각 이벤트 클래스에 대한 자세한 정보를 제공하는 이벤트 하위 클래스 유형입니다. 다음 표에서는 이 이벤트에 대한 이벤트 하위 클래스 값을 나열합니다.|21|사용자 계정 컨트롤|  
|**FileName**|**nvarchar**|원격 데이터베이스 미러링 엔드포인트에서 구성된 지원되는 인증 방법입니다. 둘 이상의 메서드를 사용할 수 있는 경우 수락하는(대상) 엔드포인트에서 먼저 시도할 메서드를 결정합니다. 가능한 값은<br /><br /> **없음**. 인증 방법이 구성되어 있지 않습니다.<br /><br /> **NTLM**. NTLM 인증이 필요합니다.<br /><br /> **KERBEROS**- Kerberos 인증이 필요합니다.<br /><br /> **NEGOTIATE**- Windows에서 인증 방법을 협상합니다.<br /><br /> **CERTIFICATE**- 엔드포인트에 대해 구성된 인증서가 필요합니다. 이 인증서는 **master** 데이터베이스에 저장되어 있습니다.<br /><br /> **NTLM, CERTIFICATE**- NTLM 또는 엔드포인트 인증서 인증을 적용합니다.<br /><br /> **KERBEROS, CERTIFICATE**- Kerberos 또는 엔드포인트 인증서 인증을 적용합니다.<br /><br /> **NEGOTIATE, CERTIFICATE**- Windows에서 인증 방법을 협상하거나 엔드포인트 인증서 인증을 사용합니다.<br /><br /> **CERTIFICATE, NTLM**- 엔드포인트 인증서 또는 NTLM 인증을 적용합니다.<br /><br /> **CERTIFICATE, KERBEROS**- 엔드포인트 인증서 또는 Kerberos 인증을 적용합니다.<br /><br /> **CERTIFICATE, NEGOTIATE**- 엔드포인트 인증서 인증을 적용하거나 Windows에서 인증 방법을 협상합니다.|36|아니요|  
|**HostName**|**nvarchar**|이 이벤트 클래스에서는 사용되지 않습니다.|8|사용자 계정 컨트롤|  
|**IsSystem**|**int**|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다. 1 = 시스템, 0 = 사용자|60|아니요|  
|**LoginSid**|**image**|로그인한 사용자의 SID(보안 ID)입니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|사용자 계정 컨트롤|  
|**NTDomainName**|**nvarchar**|사용자가 속한 Windows 도메인입니다.|7|사용자 계정 컨트롤|  
|**NTUserName**|**nvarchar**|이 이벤트를 생성한 연결을 소유하고 있는 사용자의 이름입니다.|6|사용자 계정 컨트롤|  
|**ObjectName**|**nvarchar**|이 연결에 사용된 연결 문자열입니다.|34|아니요|  
|**OwnerName**|**nvarchar**|로컬 데이터베이스 미러링 엔드포인트에서 구성된 지원되는 인증 방법입니다. 둘 이상의 메서드를 사용할 수 있는 경우 수락하는(대상) 엔드포인트에서 먼저 시도할 메서드를 결정합니다. 가능한 값은<br /><br /> **없음**. 인증 방법이 구성되어 있지 않습니다.<br /><br /> **NTLM**. NTLM 인증이 필요합니다.<br /><br /> **KERBEROS**- Kerberos 인증이 필요합니다.<br /><br /> **NEGOTIATE**- Windows에서 인증 방법을 협상합니다.<br /><br /> **CERTIFICATE**- 엔드포인트에 대해 구성된 인증서가 필요합니다. 이 인증서는 **master** 데이터베이스에 저장되어 있습니다.<br /><br /> **NTLM, CERTIFICATE**- NTLM 또는 엔드포인트 인증서 인증을 적용합니다.<br /><br /> **KERBEROS, CERTIFICATE**- Kerberos 또는 엔드포인트 인증서 인증을 적용합니다.<br /><br /> **NEGOTIATE, CERTIFICATE**- Windows에서 인증 방법을 협상하거나 엔드포인트 인증서 인증을 사용합니다.<br /><br /> **CERTIFICATE, NTLM**- 엔드포인트 인증서 또는 NTLM 인증을 적용합니다.<br /><br /> **CERTIFICATE, KERBEROS**- 엔드포인트 인증서 또는 Kerberos 인증을 적용합니다.<br /><br /> **CERTIFICATE, NEGOTIATE**- 엔드포인트 인증서 인증을 적용하거나 Windows에서 인증 방법을 협상합니다.|37|아니요|  
|**ProviderName**|**nvarchar**|이 연결에 사용된 인증 방법입니다.|46|아니요|  
|**RoleName**|**nvarchar**|연결의 역할입니다. 이 역할은 **시작자** 또는 **대상**입니다.|38|아니요|  
|**데이터 열이 추적에서 캡처되고 서버를 사용할 수 있으면**|**nvarchar**|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니요|  
|**SPID**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 클라이언트와 관련된 프로세스에 할당한 서버 프로세스 ID입니다.|12|사용자 계정 컨트롤|  
|**StartTime**|**datetime**|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|사용자 계정 컨트롤|  
|**State**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 원본 코드 내에서 이벤트가 생성된 위치를 나타냅니다. 이 이벤트가 생성될 수 있는 각 위치의 상태 코드는 서로 다릅니다. Microsoft 지원 엔지니어는 이 상태 코드를 사용하여 이벤트가 생성된 위치를 찾을 수 있습니다.|30|아니요|  
|**TargetUserName**|**nvarchar**|로그인 상태입니다. 다음 중 하나입니다.<br /><br /> INITIAL<br /><br /> WAIT LOGIN NEGOTIATE<br /><br /> ONE ISC<br /><br /> ONE ASC<br /><br /> TWO ISC<br /><br /> TWO ASC<br /><br /> WAIT ISC Confirm<br /><br /> WAIT ASC Confirm<br /><br /> WAIT REJECT<br /><br /> WAIT PRE-MASTER SECRET<br /><br /> WAIT VALIDATION<br /><br /> WAIT ARBITRATION<br /><br /> ONLINE<br /><br /> error<br /><br /> <br /><br /> 참고: ISC = 보안 컨텍스트 시작. ASC = 보안 컨텍스트 허용.|39|아니요|  
|**TransactionID**|**bigint**|시스템이 할당한 트랜잭션 ID입니다.|4|아니요|  
  
 다음 표에서는 이 이벤트 클래스에 대한 하위 클래스 값을 나열합니다.  
  
|ID|하위 클래스|Description|  
|--------|--------------|-----------------|  
|1|Login Success|Login Success 이벤트는 인접한 데이터베이스 미러링 로그인 프로세스가 성공적으로 끝났음을 보고합니다.|  
|2|Login Protocol Error|Login Protocol Error 이벤트는 데이터베이스 미러링 로그인이 올바른 형식이지만 로그인 프로세스의 현재 상태에 맞지 않는 메시지를 수신했음을 보고합니다. 메시지가 잘못 전송되었거나 순서에 맞지 않게 전송되었을 수 있습니다.|  
|3|Message Format Error|Message Format Error 이벤트는 데이터베이스 미러링 로그인이 예상 형식에 맞지 않는 메시지를 수신했음을 보고합니다. 메시지가 손상되었거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 아닌 프로그램에서 데이터베이스 미러링이 사용하는 포트로 메시지를 보내는 것일 수 있습니다.|  
|4|Negotiate Failure|Negotiate Failure 이벤트는 로컬 데이터베이스 미러링 엔드포인트와 원격 데이터베이스 미러링 엔드포인트가 상호 배타적인 인증 수준을 지원하고 있음을 보고합니다.|  
|5|Authentication Failure|Authentication Failure 이벤트는 데이터베이스 미러링 엔드포인트가 오류로 인해 연결을 인증할 수 없음을 보고합니다. Windows 인증일 경우 이 이벤트는 데이터베이스 미러링 엔드포인트가 Windows 인증을 사용할 수 없음을 보고합니다. 인증서 기반 인증일 경우 이 이벤트는 데이터베이스 미러링 엔드포인트가 인증서에 액세스할 수 없음을 보고합니다.|  
|6|Authorization Failure|Authorization Failure 이벤트는 데이터베이스 미러링 엔드포인트에서 연결 인증을 거부했음을 보고합니다. Windows 인증일 경우 이 이벤트는 연결의 보안 식별자가 데이터베이스 사용자와 일치하지 않음을 보고합니다. 인증서 기반 인증일 경우 이 이벤트는 메시지에 전달된 공개 키가 **master** 데이터베이스의 인증서와 맞지 않음을 보고합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [CREATE ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/create-endpoint-transact-sql)   
 [ALTER ENDPOINT&#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-endpoint-transact-sql)   
 [데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  
