---
title: SQL Server, Broker TO Statistics 개체 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker Transmission Object object
- 'SQL Server: Broker Transmission Object'
ms.assetid: b5bc5dde-e540-4848-8aa3-5735c51df2fb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5dbf71d0b68654776783929cd59b475627747684
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158301"
---
# <a name="sql-server-broker-to-statistics-object"></a>SQL Server, Broker TO Statistics 개체
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  SQLServer:Broker TO Statistics 성능 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화 상자에서 전송 개체를 요청하는 횟수와 전송 개체가 **tempdb**에 기록되는 빈도에 대한 정보를 보고합니다.  
  
 전송 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 대화의 메시지 전송 상태를 기록하고, 메모리에 저장됩니다. 메모리를 늘리기 위해 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 는 정기적으로 비활성 전송 개체의 일괄 처리를 **tempdb**의 작업 테이블에 기록합니다.  
  
 다음 표에서는 이 개체가 포함하는 카운터를 나열합니다.  
  
|SQL Server Broker TO Statistics 카운터|설명|  
|----------------------------------------------|-----------------|  
|**Avg. Length of Batched Writes**|일괄 처리에 저장되는 평균 전송 개체 수입니다.|  
|**Avg. Time To Write Batch (ms)**|전송 개체 일괄 처리를 저장하는 데 필요한 평균 시간(밀리초)입니다.|  
|**Avg. Time to Write Batch Base**|내부용으로만 사용할 수 있습니다.|
|**Avg. Time Between Batches (ms)**|전송 개체의 일괄 처리 기록 간 평균 시간(밀리초)입니다.|  
|**Avg. Time Between Batches Base**|내부용으로만 사용할 수 있습니다.| 
|**Tran Object Gets/sec**|대화에서 전송 개체를 요청한 초당 횟수입니다.|  
|**Tran Objects Marked Dirty/sec**|전송 개체가 커밋되지 않은 것으로 표시된 초당 횟수입니다. 전송 개체는 처음 수정하면 커밋된 것으로 표시되어 메모리 내장 복사본이 **tempdb**에 저장된 복사본과 달라지게 됩니다. 전송 개체는 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 가 대화의 메시지 전송 상태에 변경 사항을 기록할 때 수정됩니다.|  
|**Tran Object Writes/sec**|전송 개체의 일괄 처리가 **tempdb** 작업 테이블에 기록된 초당 횟수입니다. 기록된 횟수가 많으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리가 스트레스 상태임을 나타낼 수 있습니다.|  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server, Access Methods 개체](../../relational-databases/performance-monitor/sql-server-access-methods-object.md)   
 [SQL Server, Memory Manager 개체](../../relational-databases/performance-monitor/sql-server-memory-manager-object.md)   
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
