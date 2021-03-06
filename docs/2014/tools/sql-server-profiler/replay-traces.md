---
title: 추적 재생 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Profiler, replaying traces
- Run to Cursor option
- Toggle Breakpoint option
- traces [SQL Server], replaying
- replaying traces
- playback engine [SQL Server Profiler]
- events [SQL Server], replaying traces
- Profiler [SQL Server Profiler], replaying traces
ms.assetid: da958d3c-7f3e-44c9-aecc-8a9493bea7c0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9f20ef7be89e70de2ba50444691f17aff4128fa
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48135325"
---
# <a name="replay-traces"></a>추적 재생
  재생은 추적에 캡처된 작업을 재현하는 기능입니다. 추적을 만들거나 편집할 때 추적을 파일에 저장하면 나중에 재생할 수 있습니다. [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하면 단일 컴퓨터의 추적 작업만 재생할 수 있습니다. 대규모 작업의 경우 Distributed Replay Utility를 사용하면 여러 컴퓨터의 추적 데이터를 재생할 수 있습니다.  
  
 이 섹션에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]의 재생 기능을 사용하는 방법에 대해 설명합니다. Distributed Replay Utility에 대한 자세한 내용은 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)을 참조하십시오.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 는 사용자 연결 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인증을 시뮬레이션할 수 있는 다중 스레드 재생 엔진을 갖추고 있습니다. 재생 기능은 애플리케이션이나 프로세스 문제 해결에 유용합니다. 문제를 파악하여 수정한 다음에는 수정된 애플리케이션이나 프로세스에 대해 잠재적인 문제가 발견된 추적을 실행하고 원래 추적을 재생한 다음 결과를 비교합니다.  
  
 추적 재생을 사용 하 여 디버깅 지원는 **중단 점 토글** 및 **커서까지 실행** 옵션에 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] **재생** 메뉴. 이 옵션을 사용하면 추적 재생을 짧은 조각으로 분리하고 점차 큰 부분으로 분석 범위를 늘릴 수 있어 긴 스크립트를 분석할 때 유용합니다.  
  
 추적 재생에 필요한 권한에 대한 자세한 내용은 [SQL Server 프로파일러 실행에 필요한 권한](permissions-required-to-run-sql-server-profiler.md)을 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|Description|  
|-----------|-----------------|  
|[재생 요구 사항](replay-requirements.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 재생될 수 있도록 추적 정의에 꼭 포함되어야 하는 이벤트에 대해 설명합니다.|  
|[재생 옵션 &#40;SQL Server Profiler&#41;](replay-options-sql-server-profiler.md)|**의** 재생 구성 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]대화 상자에서 설정할 수 있는 옵션에 대해 설명합니다.|  
|[추적 재생 시 고려 사항 &#40;SQL Server Profiler&#41;](considerations-for-replaying-traces-sql-server-profiler.md)|[!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 를 사용하여 재생할 수 없는 추적 이벤트 및 추적 재생이 서버 성능에 미치는 영향에 대해 설명합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [SQL Server Distributed Replay](../distributed-replay/sql-server-distributed-replay.md)  
  
  
