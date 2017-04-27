---
title: "디스크 사용량 모니터링 | Microsoft 문서"
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
- database monitoring [SQL Server], disk usage
- disks [SQL Server]
- monitoring performance [SQL Server], disk usage
- server performance [SQL Server], disk usage
- monitoring [SQL Server], disk activity
- excess paging [SQL Server]
- tuning databases [SQL Server], disk usage
- I/O [SQL Server], monitoring
- disks [SQL Server], monitoring activity
- isolating disk activity [SQL Server]
- database performance [SQL Server], disk usage
- monitoring server performance [SQL Server], disk usage
ms.assetid: 1525449c-ea7d-4222-b294-1ba1fe99c9ac
caps.latest.revision: 23
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 5ff4acc6d6465b09c721d376b14ba6574938ef38
ms.lasthandoff: 04/11/2017

---
# <a name="monitor-disk-usage"></a>디스크 사용량 모니터링
  Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 Microsoft Windows 운영 체제 I/O(입/출력) 호출을 사용하여 디스크에서 읽기 및 쓰기 작업을 수행합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 디스크 I/O가 수행되는 시간과 방법을 관리하지만 기본 I/O 작업은 Windows 운영 체제에서 수행합니다. I/O 하위 시스템에는 시스템 버스, 디스크 컨트롤러 카드, 디스크, 테이프 드라이브, CD-ROM 드라이브 및 기타 여러 I/O 장치가 있습니다. 디스크 I/O는 시스템에서 자주 병목 현상을 일으킵니다.  
  
 디스크 작업 모니터링은 다음 두 가지 핵심 영역으로 구성됩니다.  
  
-   디스크 I/O 모니터링 및 초과 페이징 검색  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 만드는 디스크 작업 격리  
  
 자세한 내용은 [디스크 사용 모니터링](http://social.technet.microsoft.com/wiki/contents/articles/monitoring-disk-usage.aspx)을 참조하십시오.  
  
  