---
title: "SQL Server, Backup Device 개체 | Microsoft 문서"
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
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
caps.latest.revision: 19
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4a89a457d90882db719c387a317a6944aed7d745
ms.lasthandoff: 04/11/2017

---
# <a name="sql-server-backup-device-object"></a>SQL Server, Backup Device 개체
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  **Backup Device** 개체는 백업 및 복원 작업에 사용되는 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 백업 장치를 모니터링하는 카운터를 제공합니다. 장치 단위로 백업 및 복원 작업의 처리량, 진행률, 성능 등을 결정하려면 백업 장치를 모니터링합니다. 전체 데이터베이스 백업이나 복원 작업의 처리량을 모니터링하려면 **** Databases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. 자세한 내용은 [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md)을 참조하세요.  
  
 이 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** 카운터에 대해 설명합니다.  
  
|SQL Server Backup Device 카운터|설명|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|데이터베이스를 백업하거나 복원하는 데 사용되는 백업 장치의 읽기/쓰기 작업 처리량(초당 바이트 수)입니다. 이 카운터는 백업이나 복원 작업이 실행 중일 때만 존재합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [백업 장치&#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [리소스 사용 모니터링&#40;시스템 모니터&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  