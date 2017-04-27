---
title: "이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler) | Microsoft Docs"
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
  - "이벤트 시작 시간 [SQL Server]"
  - "필터 [SQL Server], 추적"
  - "추적 [SQL Server], 필터"
  - "추적 [SQL Server], 이벤트"
ms.assetid: e965579e-d006-41a3-89ec-cfd5398c67d2
caps.latest.revision: 25
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 25
---
# 이벤트 시작 시간을 기준으로 이벤트 필터링(SQL Server Profiler)
  이 항목에서는 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]를 사용하여 이벤트 시작 시간을 기준으로 추적 이벤트를 필터링하는 방법에 대해 설명합니다.  
  
### 이벤트 시작 시간을 기준으로 이벤트를 필터링하려면  
  
1.  **파일** 메뉴에서 **새 추적**을 클릭한 다음 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 연결합니다.  
  
     **추적 속성** 대화 상자가 표시됩니다.  
  
    > [!NOTE]  
    >  **연결한 후 즉시 추적 시작**을 선택한 경우에는 **추적 속성** 대화 상자가 나타나지 않고 추적이 시작됩니다. 이 설정을 해제하려면 **도구**메뉴에서 **옵션**을 클릭한 다음 **연결한 후 즉시 추적 시작** 확인란의 선택을 취소합니다.  
  
2.  **추적 이름** 입력란에 추적의 이름을 입력합니다.  
  
3.  **템플릿 사용** 이름 목록에서 추적 템플릿을 선택합니다.  
  
4.  필요에 따라 추적 결과의 저장 대상을 지정합니다.  
  
5.  **이벤트 선택** 탭에서 **StartTime** 열 머리글을 클릭합니다. 열 머리글을 마우스 오른쪽 단추로 클릭한 다음 **열 필터 편집**을 클릭하여 **필터 편집** 대화 상자를 시작할 수도 있습니다.  
  
6.  **보다 큼** 또는 **보다 작음**을 확장한 다음 비교 연산자 아래 나타나는 필드에 **datetime** 값을 입력합니다.  
  
## 참고 항목  
 [SQL Server 프로파일러](../../tools/sql-server-profiler/sql-server-profiler.md)  
  
  