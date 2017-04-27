---
title: "SQL Server 에이전트 자동 시작(SQL Server Management Studio) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent, starting
- autostart SQL Server Agent
ms.assetid: 2ea332da-0ede-4d2b-b122-c4c10eaca191
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d04f69be267c374559c65638d09d24ac6ef4822d
ms.lasthandoff: 04/11/2017

---
# <a name="autostart-sql-server-agent-sql-server-management-studio"></a>Autostart SQL Server Agent (SQL Server Management Studio)
이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트가 [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)]에서 예기치 않게 중지될 경우 자동으로 다시 시작되도록 구성하는 방법에 대해 설명합니다.  
  
**항목 내용**  
  
-   **시작하기 전에:**  
  
    [제한 사항](#Restrictions)  
  
    [보안](#Security)  
  
-   [SQL Server Management Studio를 사용하여 자동으로 시작되도록 SQL Server 에이전트를 구성하려면](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>시작하기 전에  
  
### <a name="Restrictions"></a>제한 사항  
사용 권한이 있는 경우에만 개체 탐색기에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트 노드가 표시됩니다.  
  
### <a name="Security"></a>보안  
  
#### <a name="Permissions"></a>Permissions  
해당 기능을 수행하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에서 **sysadmin** 고정 서버 역할 멤버인 계정의 자격 증명을 사용하도록 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]에이전트를 구성해야 합니다. 이 계정에는 다음과 같은 Windows 사용 권한이 필요합니다.  
  
-   서비스로 로그온(SeServiceLogonRight)  
  
-   프로세스 수준 토큰 바꾸기(SeAssignPrimaryTokenPrivilege)  
  
-   트래버스 검사 무시(SeChangeNotifyPrivilege)  
  
-   프로세스의 메모리 할당량 조정(SeIncreaseQuotaPrivilege)  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트 서비스 계정에 필요한 Windows 사용 권한에 대한 자세한 내용은 [SQL Server 에이전트 서비스의 계정 선택](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md) 및 [Windows 서비스 계정 설정](http://msdn.microsoft.com/en-us/309b9dac-0b3a-4617-85ef-c4519ce9d014)을 참조하세요.  
  
## <a name="SSMSProcedure"></a>SQL Server Management Studio 사용  
  
#### <a name="to-configure-sql-server-agent-to-automatically-restart"></a>자동으로 다시 시작되도록 SQL Server 에이전트를 구성하려면  
  
1.  **개체 탐색기**에서 더하기 기호를 클릭하여 자동으로 다시 시작되도록 SQL Server 에이전트를 구성할 서버를 확장합니다.  
  
2.  **SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
3.  **일반** 페이지에서 **SQL Server 에이전트가 갑자기 작동을 멈추면 자동으로 다시 시작**을 선택합니다.  
  
