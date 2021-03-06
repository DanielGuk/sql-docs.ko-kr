---
title: SQL Server 에이전트 마스터 작업의 단계 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 8f1a0ee6-49ff-4080-94ca-d661daeff2a6
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f23c4817ff1a09c7d25b636049c22410003da002
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221163"
---
# <a name="change-steps-of-a-sql-server-agent-master-job"></a>Change Steps of a SQL Server Agent Master Job
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 또는 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 을 사용하여 [!INCLUDE[tsql](../../includes/tsql-md.md)]에서 SQL Server 에이전트 마스터 작업의 단계를 변경하는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  
  
     [제한 사항](#Restrictions)  
  
     [보안](#Security)  
  
-   **다음을 사용하여 SQL Server 에이전트 마스터 작업의 단계를 변경하려면:**  
  
     다른 도구는 [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전에  
  
###  <a name="Restrictions"></a> 제한 사항  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트 마스터 작업은 로컬 및 원격 서버 모두에서 대상이 될 수 없습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> Permissions  
 **sysadmin** 고정 서버 역할의 멤버가 아닌 경우 자신이 소유한 작업만 수정할 수 있습니다. 자세한 내용은 [Implement SQL Server Agent Security](implement-sql-server-agent-security.md)을 참조하세요.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server 에이전트 마스터 작업의 단계를 변경하려면  
  
1.  **개체 탐색기** 에서 더하기 기호를 클릭하여 단계를 수정하려는 작업이 들어 있는 서버를 확장합니다.  
  
2.  더하기 기호를 클릭하여 **SQL Server 에이전트**를 확장합니다.  
  
3.  더하기 기호를 클릭하여 **작업** 폴더를 확장합니다.  
  
4.  단계를 수정하려는 작업을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
5.  **작업 속성-***job_name* 대화 상자의 **페이지 선택**에서 **단계**를 선택합니다.  
  
6.  **편집**을 클릭하여 **작업 단계 속성 –***job_step_name* 대화 상자를 엽니다. 이 대화 상자에서 사용 가능한 옵션에 대 한 자세한 내용은 참조 하세요. [작업 단계 속성: 새 작업 단계 &#40;일반 페이지&#41; ](../../integration-services/general-page-of-integration-services-designers-options.md) 하 고 [작업 단계 속성: 새 작업 단계 &#40;고급 페이지&#41; ](job-step-properties-new-job-step-advanced-page.md).  
  
7.  완료되었으면 **확인**을 클릭합니다.  
  
8.  **작업 속성-***job_name* 대화 상자에서 **확인**을 클릭합니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
  
#### <a name="to-make-changes-to-the-steps-of-a-sql-server-agent-master-job"></a>SQL Server 에이전트 마스터 작업의 단계를 변경하려면  
  
1.  **개체 탐색기**에서 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결합니다.  
  
2.  표준 도구 모음에서 **새 쿼리**를 클릭합니다.  
  
3.  다음 예를 복사하여 쿼리 창에 붙여 넣고 **실행**을 클릭합니다.  
  
    ```  
    -- changes the number of retry attempts for the first step of the Weekly Sales Data Backup job.   
    -- After running this example, the number of retry attempts is 10   
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_update_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_id = 1,  
        @retry_attempts = 10 ;  
    GO  
    ```  
  
 자세한 내용은 [sp_update_jobstep &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-update-jobstep-transact-sql)합니다.  
  
  
