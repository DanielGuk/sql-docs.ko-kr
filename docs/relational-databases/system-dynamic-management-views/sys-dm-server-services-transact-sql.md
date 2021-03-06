---
title: sys.dm_server_services (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/07/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_server_services
- sys.dm_server_services
- sys.dm_server_services_TSQL
- dm_server_services_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_server_services dynamic management view
ms.assetid: 3f0defd0-478d-4e7f-96be-8795c9de4e3f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8acb2fae0aa0edadf1995a0a103ff60b66a912a9
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072138"
---
# <a name="sysdmserverservices-transact-sql"></a>sys.dm_server_services(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  SQL Server, 전체 텍스트 및 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스의 SQL Server 에이전트 서비스에 대한 정보를 반환합니다. 이 동적 관리 뷰를 사용하여 이러한 서비스에 대한 상태 정보를 보고할 수 있습니다.  
  
 
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|servicename|**nvarchar(256)**|이름을 합니다 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], 전체 텍스트 또는 SQL Server 에이전트 서비스입니다. null일 수 없습니다.|  
|startup_type|**int**|서비스의 시작 모드를 나타냅니다. 가능한 값 및 해당 설명을 다음과 같습니다.<br /><br /> 0: 기타<br />1: 다른<br />2: 자동<br />3: 수동<br />4: 사용 안 함<br /><br /> Null을 허용합니다.|  
|startup_desc|**nvarchar(256)**|서비스의 시작 모드를 설명합니다. 가능한 값 및 해당 설명을 다음과 같습니다.<br /><br /> 기타: 기타 (부팅 시작)<br />기타: 기타 (시스템 시작)<br />자동: 자동 시작<br />수동: 요청 시 시작<br />사용 안 함: 사용 안 함<br /><br /> null일 수 없습니다.|  
|상태|**int**|서비스의 현재 상태를 나타냅니다. 가능한 값 및 해당 설명을 다음과 같습니다.<br /><br /> 1: 중지<br />2: 기타 (시작 보류 중)<br />3: 기타 (중지 보류 중)<br />4: 실행<br />5: 기타 (계속 보류 중)<br />6: 다른 (일시 중지 보류 중)<br />7: 일시 중지<br /><br /> Null을 허용합니다.|  
|status_desc|**nvarchar(256)**|서비스의 현재 상태를 설명합니다. 가능한 값 및 해당 설명을 다음과 같습니다.<br /><br /> 중지 되었습니다: 서비스가 중지 되었습니다.<br />기타 (시작 작업이 보류 중): 서비스를 시작 하 고 있습니다.<br />기타 (중지 작업 보류 중): 서비스를 중지 하 고 있습니다.<br />실행 중: 서비스 실행 중입니다.<br />기타 (계속 보류 중인 작업이): 서비스가 보류 중 상태에서입니다.<br />다른 (일시 중지 보류 중): 서비스를 일시 중지 하 고 있습니다.<br />일시 중지: 서비스 일시 중지 됩니다.<br /><br /> null일 수 없습니다.|  
|process_id|**int**|서비스의 프로세스 ID입니다. null일 수 없습니다.|  
|last_startup_time|**datetimeoffset(7)**|서비스가 마지막으로 시작된 날짜와 시간입니다. Null을 허용합니다.|  
|service_account|**nvarchar(256)**|서비스를 제어할 권한이 부여된 계정입니다. 이 계정으로 서비스를 시작 또는 중지하거나 서비스 속성을 수정할 수 있습니다. null일 수 없습니다.|  
|filename|**nvarchar(256)**|서비스 실행 파일의 경로 및 파일 이름입니다. null일 수 없습니다.|  
|is_clustered|**nvarchar(1)**|서비스가 클러스터형 서버의 리소스로 설치되었는지 여부를 나타냅니다. null일 수 없습니다.|  
|cluster_nodename|**nvarchar(256)**|서비스가 설치된 클러스터 노드의 이름입니다. Null을 허용합니다.|
|instant_file_initialization_enabled|**nvarchar(1)**|즉시 파일 초기화에 대 한 사용 되는지 여부를 지정 된 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 서비스입니다.<br /><br />Y = 서비스에 대 한 인스턴트 파일 초기화가 사용 합니다.<br /><br />N = 서비스용 인스턴트 파일 초기화는 사용 하지 않도록 설정 합니다.<br /><br /> Null을 허용합니다.<br /><br /> **참고:** SQL Server 에이전트와 같은 다른 서비스에 적용 되지 않습니다.<br /><br /> **적용 대상:** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (부터 [!INCLUDE[sssql11](../../includes/sssql11-md.md)] SP4, 및 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]).|  

## <a name="security"></a>보안  
  
### <a name="permissions"></a>사용 권한  
 서버에 대한 `VIEW SERVER STATE` 권한이 필요합니다.  
  
## <a name="see-also"></a>관련 항목  
 [sys.dm_server_registry &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-server-registry-transact-sql.md)  
  
