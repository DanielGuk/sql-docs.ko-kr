---
title: QN:Template 이벤트 클래스 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Template
ms.assetid: 9f752040-5901-42e1-8fdc-105528d9960a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: eaee265571f647c4908a42634a45fc91b355d7bf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48209283"
---
# <a name="qntemplate-event-class"></a>QN:Template 이벤트 클래스
  QN:Template 이벤트는 쿼리 템플릿의 내부 사용에 대한 정보를 보고합니다. 여기서 쿼리 템플릿이란 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 알리기 위해 쿼리 정의를 공유하는 데 사용하는 메커니즘을 말합니다. 이러한 템플릿은 매개 변수 테이블과 함께 만들어집니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서는 쿼리 템플릿이 만들어지거나 사용되거나 소멸될 때 이러한 유형의 이벤트를 만듭니다.  
  
## <a name="qntemplate-event-class-data-columns"></a>QN:Template 이벤트 클래스 데이터 열  
  
|데이터 열|형식|Description|열 번호|필터 가능|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결한 클라이언트 응용 프로그램의 이름입니다. 이 열은 프로그램의 표시 이름이 아니라 애플리케이션에서 전달한 값으로 채워집니다.|10|사용자 계정 컨트롤|  
|ClientProcessID|`int`|클라이언트 애플리케이션이 실행 중인 프로세스에 대해 호스트 컴퓨터가 할당한 ID입니다. 클라이언트가 클라이언트 프로세스 ID를 제공하면 이 데이터 열이 채워집니다.|9|사용자 계정 컨트롤|  
|DatabaseID|`int`|USE *database* 문으로 지정한 데이터베이스 ID이거나 지정한 인스턴스에 대해 실행된 USE *database*문이 없는 경우 기본 데이터베이스 ID입니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 에 데이터베이스 이름이 표시됩니다. DB_ID 함수를 사용하여 데이터베이스의 값을 확인할 수 있습니다.|3|사용자 계정 컨트롤|  
|DatabaseName|`nvarchar`|사용자 문이 실행되는 데이터베이스의 이름입니다.|35|사용자 계정 컨트롤|  
|EventClass|`int`|이벤트 유형 = 201|27|아니요|  
|EventSequence|`int`|이 이벤트의 시퀀스 번호입니다.|51|아니요|  
|EventSubClass|`nvarchar`|각 이벤트 클래스에 대한 자세한 정보를 제공하는 이벤트 하위 클래스 유형입니다. 이 열에는 다음 값이 포함될 수 있습니다.<br /><br /> 만든 템플릿: 쿼리 알림 템플릿이 데이터베이스에 생성되었음을 나타냅니다.<br /><br /> 만든 템플릿: 쿼리 알림 템플릿이 다시 사용되는 경우를 나타냅니다.<br /><br /> 삭제된 템플릿: 쿼리 알림 템플릿이 데이터베이스에서 제거되는 경우를 나타냅니다.|21|사용자 계정 컨트롤|  
|GroupID|`int`|SQL 추적 이벤트가 발생한 작업 그룹의 ID입니다.|66|사용자 계정 컨트롤|  
|HostName|`nvarchar`|클라이언트를 실행 중인 컴퓨터의 이름입니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다. 호스트 이름을 확인하려면 HOST_NAME 함수를 사용합니다.|8|사용자 계정 컨트롤|  
|IsSystem|`int`|이벤트가 시스템 프로세스에서 발생했는지 아니면 사용자 프로세스에서 발생했는지를 나타냅니다.<br /><br /> 0 = 사용자<br /><br /> 1 = 시스템|60|아니요|  
|LoginName|`nvarchar`|사용자 로그인 이름( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 보안 로그인 또는 *DOMAIN\Username*형식의 Windows 로그인 자격 증명)입니다.|11|아니요|  
|LoginSID|`image`|로그인한 사용자의 SID(보안 ID)입니다. 이 정보는 sys.server_principals 카탈로그 뷰에 있습니다. 각 SID는 서버의 각 로그인마다 고유합니다.|41|사용자 계정 컨트롤|  
|NTDomainName|`nvarchar`|사용자가 속한 Windows 도메인입니다.|7|사용자 계정 컨트롤|  
|NTUserName|`nvarchar`|이 이벤트를 생성한 연결을 소유하고 있는 사용자의 이름입니다.|6|사용자 계정 컨트롤|  
|RequestID|`int`|문을 포함하는 요청의 식별자입니다.|49|사용자 계정 컨트롤|  
|ssSqlProfiler|`nvarchar`|추적 중인 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 이름입니다.|26|아니요|  
|SessionLoginName|`nvarchar`|세션을 시작한 사용자의 로그인 이름입니다. 예를 들어 애플리케이션이 Login1을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에 연결하고 Login2로 문을 실행하는 경우 SessionLoginName은 "Login1"을 표시하고 LoginName은 "Login2"를 표시합니다. 이 열은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 및 Windows 로그인을 모두 표시합니다.|64|사용자 계정 컨트롤|  
|SPID|`int`|이벤트가 발생한 세션의 ID입니다.|12|사용자 계정 컨트롤|  
|StartTime|`datetime`|이벤트가 시작된 시간입니다(사용 가능한 경우).|14|사용자 계정 컨트롤|  
|TextData|`ntext`|이 이벤트에 해당하는 정보가 포함된 XML 문서를 반환합니다. 이 문서는 [SQL Server 쿼리 알림 프로파일러 이벤트 스키마](http://go.microsoft.com/fwlink/?LinkId=63331) 페이지에서 사용할 수 있는 XML 스키마를 따릅니다.|1|사용자 계정 컨트롤|  
  
  
