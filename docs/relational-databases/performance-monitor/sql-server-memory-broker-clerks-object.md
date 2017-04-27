---
title: "SQL Server, Memory Broker Clerk 개체 | Microsoft 문서"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLServer:Memory Broker Clerks
ms.assetid: 47b9c236-66a3-4c42-97ee-da5555bdc046
caps.latest.revision: 4
author: dagiro
ms.author: v-dagir
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7cf0f0a0d8ef7f7e8dec4a7a743dbc25bc98bb8d
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-memory-broker-clerks-object"></a>SQL Server, Memory Broker Clerk 개체
**SQLServer:Memory Broker Clerks** 성능 개체는 메모리 브로커 클럭에 관련된 통계에 대한 카운터를 제공합니다.

다음 표에서는 SQL Server **Memory Broker Clerks** 성능 개체에 대해 설명합니다.

|**SQL Server Memory Broker Clerk 카운터**|Description|  
|-------------|-----------------|  
|**Internal benefit**|엔트리 개수 압력에 대한 메모리의 내부 값(ms/페이지/ms)입니다(100억으로 곱하고 정수로 잘림).|
|**Memory broker clerk size**|클럭의 크기(페이지)입니다.|
|**Periodic evictions (pages)**|마지막 정기 제거에 의해 브로커 클럭에서 제거된 페이지 수입니다.|
|**Pressure evictions (pages/sec)**|메모리 가중에 의해 브로커 클럭에서 제거된 초당 페이지 수입니다.|
|**Simulation benefit**|클럭에 대한 메모리 값(밀리초/페이지/밀리초)입니다(100억으로 곱하고 정수로 잘림).|
|**Simulation size**|클럭 시뮬레이션의 현재 크기(페이지)입니다.|

버퍼 풀 및 열 저장소 개체 풀에 대한 카운터의 인스턴스입니다.

## <a name="see-also"></a>관련 항목:  
[리소스 사용 모니터링(시스템 모니터)](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)