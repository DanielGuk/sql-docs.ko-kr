---
title: "추적 시작 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server 프로파일러, 추적 중지"
  - "추적 일시 중지"
  - "프로파일러 [SQL Server 프로파일러], 추적 중지"
  - "프로파일러 [SQL Server 프로파일러], 추적 시작"
  - "추적 [SQL Server], 시작"
  - "SQL Server 프로파일러, 추적 일시 중지"
  - "추적 [SQL Server], 중지"
  - "프로파일러 [SQL Server 프로파일러], 추적 일시 중지"
  - "추적 [SQL Server], 일시 중지"
  - "SQL Server 프로파일러, 추적 시작"
  - "추적 중지"
  - "추적 시작"
ms.assetid: aeeb38eb-229a-4c8b-ad66-57e9ce45fb6a
caps.latest.revision: 24
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 24
---
# 추적 시작
  [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 새 추적을 정의하거나 템플릿을 만든 후 새 추적 정의 또는 템플릿을 사용하여 데이터 캡처를 시작, 일시 중지 또는 중지할 수 있습니다.  
  
## 추적 시작  
 추적을 시작하고 정의된 원본이 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 또는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]의 인스턴스인 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]는 캡처된 서버 이벤트의 임시 보유 장소를 제공하는 큐를 만듭니다.  
  
 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 SQL 추적에 액세스하는 경우 추적이 시작되면 새 추적 창이 열리면서(창이 열려 있지 않은 경우) 데이터가 즉시 캡처됩니다.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 시스템 저장 프로시저를 사용하여 SQL 추적에 액세스하는 경우에는 데이터 캡처를 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 시작될 때마다 추적을 시작해야 합니다. 추적이 시작되면 추적 이름만 수정할 수 있습니다.  
  
> [!NOTE]  
>  기존의 추적으로 작업하면 속성을 볼 수는 있지만 수정할 수는 없습니다. 속성을 수정하려면 추적을 시작하거나 일시 중지하십시오.  
  
## 참고 항목  
 [서버 연결 후 자동으로 추적 시작&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/start-a-trace-automatically-after-connecting-to-a-server-sql-server-profiler.md)   
 [추적 일시 중지&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/pause-a-trace-sql-server-profiler.md)   
 [추적 중지&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/stop-a-trace-sql-server-profiler.md)   
 [추적 창 지우기&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/clear-a-trace-window-sql-server-profiler.md)   
 [일시 중지 또는 중지 후 추적 실행&#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/run-a-trace-after-it-has-been-paused-or-stopped-sql-server-profiler.md)  
  
  