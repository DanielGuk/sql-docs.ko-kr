---
title: "SQL Server 오류 로그 보기(SQL Server Management Studio) | Microsoft 문서"
ms.custom: 
ms.date: 07/29/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- viewing logs
- displaying logs
- errors [SQL Server], logs
- logs [SQL Server], SQL Server error logs
- logs [SQL Server], viewing
ms.assetid: 55f468ba-146c-4ab3-95cd-d35d051afd12
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 4acdc87a3317c38b5b19235dae681bce426244e3
ms.lasthandoff: 04/11/2017

---
# <a name="view-the-sql-server-error-log-sql-server-management-studio"></a>SQL Server 오류 로그 보기(SQL Server Management Studio)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그에는 문제 해결을 위한 사용자 정의 이벤트와 특정 시스템 이벤트가 포함됩니다. 
  

  ## <a name="how-to-view-the-logs"></a>로그를 확인하는 방법
1.  SSMS에서 **개체 탐색기**를 선택합니다.

>개체 탐색기를 **열려면** 키보드 바로 가기 **F8**키를 누릅니다. 또는 상단 메뉴에서 보기/개체 탐색기를 클릭합니다. ![Object_explorer](../../relational-databases/performance/media/object-explorer.png) 


2.  **개체 탐색기**에서 SQL Server의 인스턴스에 연결한 다음 해당 인스턴스를 확장합니다.
  
3.  **관리** 섹션(볼 수 있는 권한이 있다고 가정)을 찾아 확장합니다.

4.  **SQL Server 로그**를 마우스 오른쪽 단추로 클릭하고 **SQL Server 로그 보기**를 선택합니다.
 ![View_SQLServer_Log_SSMS](../../relational-databases/performance/media/view-sqlserver-log-ssms.png) 
 
5.  확인할 로그 목록이 포함된 로그 파일 뷰어가 나타납니다(1분 정도 걸릴 수 있음).
  
6. 여러 사람이 [MSSQLTips.com](https://www.mssqltips.com/) 의 유용한 게시물인 [Identify location of the SQL Server Error Log file](https://www.mssqltips.com/sqlservertip/2506/identify-location-of-the-sql-server-error-log-file/)(SQL Server 오류 로그 파일의 위치 식별)을 추천했습니다. 도움이 되는 많은 정보를 확인해 보세요.
  
  
