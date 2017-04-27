---
title: "작업 기록 로그 설정 | Microsoft 문서"
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
- jobs [SQL Server Agent], history
- logs [SQL Server], jobs
- SQL Server Agent jobs, history
- historical information [SQL Server], jobs
ms.assetid: 018e5c49-d3a0-4504-851a-f70996a34bb7
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 82d09693143af337c03a54e653f029fb50710a17
ms.lasthandoff: 04/11/2017

---
# <a name="set-up-the-job-history-log"></a>Set Up the Job History Log
이 항목에서는 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에이전트 작업 기록 로그를 설정하는 방법에 대해 설명합니다.  
  
-   **시작하기 전 주의 사항:**  [보안](#Security)  
  
-   **다음을 사용하여 작업 기록 로그 설정** [SQL Server Management Studio](#SSMS)  
  
## <a name="BeforeYouBegin"></a>시작하기 전에  
  
### <a name="Security"></a>보안  
자세한 내용은 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)을 참조하세요.  
  
## <a name="SSMS"></a>SQL Server Management Studio 사용  
**작업 기록 로그를 설정하려면**  
  
1.  **개체 탐색기** 에서 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.  
  
2.  **SQL Server 에이전트**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
3.  **SQL Server 에이전트 속성** 대화 상자에서 **기록** 페이지를 선택합니다.  
  
4.  다음 옵션 중에서 선택합니다.  
  
    1.  **작업 기록 로그 크기 제한**을 선택한 다음 작업 기록 로그의 최대 행 수와 작업당 최대 행 수를 입력합니다.  
  
    2.  **자동으로 에이전트 기록 제거**를 선택한 다음 해당 기간보다 오래된 기록은 로그에서 삭제되도록 기간을 지정합니다.  
  
## <a name="see-also"></a>참고 항목  
[작업 구현](../../ssms/agent/implement-jobs.md)  
[작업 활동 모니터링](../../ssms/agent/monitor-job-activity.md)  
[작업 만들기](../../ssms/agent/create-jobs.md)  
  
