---
title: "sqlagent90 응용 프로그램 | Microsoft Docs"
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
  - "SQL Server 에이전트 시작"
  - "sqlagent90 응용 프로그램"
  - "SQL Server 에이전트, 시작"
  - "명령 프롬프트 유틸리티 [SQL Server], sqlagent90"
ms.assetid: e8b80e8d-d0c9-4500-a868-0ce08233da08
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# sqlagent90 응용 프로그램
  **sqlagent90** 응용 프로그램을 사용하면 명령 프롬프트에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 시작할 수 있습니다. 일반적으로 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 통해 또는 응용 프로그램에서 SQL-DMO 메서드를 사용하여 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 에이전트를 실행해야 합니다. **에이전트를 진단하거나 주 지원 공급자가 지정하는 경우에만 명령 프롬프트에서** sqlagent90 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 을 실행할 수 있습니다.  
  
## 구문  
  
```  
  
sqlagent90  
-c [-v] [-i instance_name]  
```  
  
## 인수  
 **-c**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 명령 프롬프트에서 실행되고 Microsoft Windows 서비스 제어 관리자와 관계 없음을 나타냅니다. **-c**를 사용하면 관리 도구의 서비스 응용 프로그램 또는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 구성 관리자에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 제어할 수 없습니다. 이 인수는 필수입니다.  
  
 **-v**  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트를 자세한 정보 표시 모드로 실행하며 명령 프롬프트 창에 진단 정보를 기록합니다. 진단 정보는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트 오류 로그에 기록되는 정보와 같습니다.  
  
 **-i** *instance_name*  
 *instance_name*으로 지정한 명명된 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 인스턴스에 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 에이전트가 연결됨을 나타냅니다.  
  
## 주의  
 저작권 정보가 표시된 다음 **sqlagent90**은 **-v** 스위치가 지정된 경우에만 명령 프롬프트 창에 출력을 표시합니다. **sqlagent90**을 중지하려면 명령 프롬프트에서 Ctrl+C를 누릅니다. 또한 **sqlagent90**을 중지하기 전에 먼저 명령 프롬프트 창을 닫지 마십시오.  
  
## 참고 항목  
 [관리 태스크 자동화&#40;SQL Server Agent&#41;](../ssms/agent/automated-administration-tasks-sql-server-agent.md)  
  
  