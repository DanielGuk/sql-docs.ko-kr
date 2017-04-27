---
title: "기업 내 작업 관리 | Microsoft 문서"
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
- multiserver job management [SQL Server]
- jobs [SQL Server Agent], modifying
- modifying jobs
- SQL Server Agent jobs, modifying
- target servers [SQL Server], job changes
ms.assetid: 4fe7f6c6-f89b-4430-979c-4994a5dcf7a6
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b5290d5109618f7c2d05722d5ee304a14b1ab528
ms.lasthandoff: 04/11/2017

---
# <a name="manage-jobs-across-an-enterprise"></a>기업 내 작업 관리
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 외부에서 다중 서버 작업 정의를 변경하면 변경 사항을 다운로드 목록에 게시해야 대상 서버에서 업데이트된 작업을 다시 다운로드할 수 있습니다. 대상 서버가 최근의 작업 정의를 갖도록 하려면 다중 서버 작업을 업데이트한 후 다음과 같이 INSERT 명령을 게시하십시오.  
  
```  
EXECUTE sp_post_msx_operation 'INSERT', 'JOB', '<job id>'  
```  
  
다중 서버 작업이 수정되었음을 대상 서버에 알리려면 다음 프로시저 중 하나를 사용한 후 앞의 명령을 호출해야 합니다.  
  
-   [sp_add_jobstep(Transact-SQL)](http://msdn.microsoft.com/en-us/97900032-523d-49d6-9865-2734fba1c755)  
  
-   [sp_update_jobstep(Transact-SQL)](http://msdn.microsoft.com/en-us/e158802c-c347-4a5d-bf75-c03e5ae56e6b)  
  
-   [sp_delete_jobstep(Transact-SQL)](http://msdn.microsoft.com/en-us/421ede8e-ad57-474a-9fb9-92f70a3e77e3)  
  
-   [이벤트 관리](http://msdn.microsoft.com/en-us/80c80eaf-cf23-4ed8-b8dd-65fe59830dd1)  
  
-   [sp_detach_schedule(Transact-SQL)](http://msdn.microsoft.com/en-us/9a1fc335-1bef-4638-a33a-771c54a5dd19)  
  
    > [!NOTE]  
    > 저장 프로시저에서는 요청된 변경 내용을 다운로드 목록에 자동 게시하기 때문에 **sp_update_job** 이나 **sp_delete_job** 을 호출한 다음에 **sp_post_msx_operation**을 호출하지 않아도 됩니다.  
  
다음은 기업 전체에 걸쳐 업무 관리에 사용하는 공통 태스크입니다.  
  
**대상 서버의 상태를 점검하려면**  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/f841d3bd-901a-4980-ad0b-1c6eeba3f717)  
  
-   [SMO(SQL Server 관리 개체)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**작업의 대상 서버를 변경하려면**  
  
-   [SQL Server Management Studio](../../ssms/agent/modify-the-target-servers-for-a-job.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/485252cc-0081-490a-9bd1-cbbd68eea286)  
  
-   [SMO(SQL Server 관리 개체)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**대상 서버의 위치를 변경하려면**  
  
-   [SQL Server Management Studio](../../ssms/agent/specify-a-target-server-s-location-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f)  
  
-   [SMO(SQL Server 관리 개체)](http://msdn.microsoft.com/en-us/4cde2b85-2a31-4cac-8d16-7a4196066193)  
  
**대상 서버 클럭을 동기화하려면**  
  
-   [SQL Server Management Studio](../../ssms/agent/synchronize-target-server-clocks-sql-server-management-studio.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/40e44df7-d3e3-44ee-b149-08aba629a21f)  
  
**대상 서버가 마스터 서버를 폴링하도록 설정하려면**  
  
-   [SQL Server Management Studio](../../ssms/agent/force-a-target-server-to-poll-the-master-server.md)  
  
-   [Transact-SQL](http://msdn.microsoft.com/en-us/085deef8-2709-4da9-bb97-9ab32effdacf)  
  
## <a name="see-also"></a>참고 항목  
[이벤트 관리](../../ssms/agent/manage-events.md)  
  
