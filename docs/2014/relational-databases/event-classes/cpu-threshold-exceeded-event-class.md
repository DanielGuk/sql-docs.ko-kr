---
title: CPU Threshold Exceeded 이벤트 클래스 | Microsoft 문서
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
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bd85605f6f99563cd042e438e4ffd517a636d133
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48176473"
---
# <a name="cpu-threshold-exceeded-event-class"></a>CPU Threshold Exceeded 이벤트 클래스
  CPU Threshold Exceeded 이벤트 클래스는 리소스 관리자가 REQUEST_MAX_CPU_TIME_SEC에 지정된 CPU 임계값을 초과하는 쿼리를 감지했음을 나타냅니다.  
  
> [!NOTE]  
>  이 이벤트의 검색 간격은 5초입니다. 이는 최소 5초 단위로 쿼리가 지정된 제한을 초과할 경우 이벤트가 생성되도록 합니다. 그러나 쿼리가 5초 이내로 지정된 임계값을 초과하는 경우에는 쿼리 타이밍과 마지막 검색 스윕 시간에 따라 이러한 쿼리가 검색되지 않을 수 있습니다.  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>CPU Threshold Exceeded 데이터 열  
  
|데이터 열 이름|데이터 형식|Description|열 ID|필터 가능|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|`int`|CPU 사용량(밀리초)입니다.|18|사용자 계정 컨트롤|  
|EventClass|`int`|214|27|아니요|  
|EventSubClass|`int`|CPU 제한 위반입니다.|21|사용자 계정 컨트롤|  
|GroupID|`int`|위반이 발생한 그룹 ID입니다.|66|사용자 계정 컨트롤|  
|OwnerID|`int`|위반을 발생시킨 프로세스의 SPID입니다.|58|사용자 계정 컨트롤|  
|SPID|`int`|이 이벤트를 발생시키는 서버 프로세스의 ID입니다.<br /><br /> 참고: 이 ID는 시스템 스레드가 CPU 사용량의 유효성을 백그라운드 태스크로 검사할 경우 실제 사용자 SPID와 다를 수 있습니다.|12|사용자 계정 컨트롤|  
|StartTime|`datetime`|이 이벤트가 발생한 시간입니다.|14|사용자 계정 컨트롤|  
  
## <a name="see-also"></a>관련 항목  
 [sp_trace_setevent&#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
