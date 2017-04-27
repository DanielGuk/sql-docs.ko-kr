---
title: "Lock Pages in Memory 옵션 설정(Windows) | Microsoft Docs"
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
  - "Lock Pages in Memory 옵션"
ms.assetid: cd581fbc-4747-439e-87f9-2f18e39c5bb9
caps.latest.revision: 35
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 35
---
# Lock Pages in Memory 옵션 설정(Windows)
  이 Windows 정책은 데이터를 실제 메모리에 유지하는 프로세스를 사용하여 시스템이 디스크의 가상 메모리로 데이터를 페이징하지 않도록 방지할 수 있는 계정을 결정합니다.  
  
> [!NOTE]  
>  메모리의 페이지를 잠그면 메모리를 디스크로 페이징할 때 성능이 향상됩니다.  
  
 Windows 그룹 정책 도구(gpedit.msc)를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 사용되는 계정에 대해 이 정책을 설정할 수 있습니다. 이 정책을 변경하려면 시스템 관리자여야 합니다.  
  
### 메모리의 페이지 잠금 옵션을 설정하려면  
  
1.  **시작** 메뉴에서 **실행**을 클릭합니다. **열기** 상자에 **gpedit.msc**를 입력합니다.  
  
2.  **로컬 그룹 정책 편집기** 콘솔에서 **컴퓨터 구성**을 확장한 다음 **Windows 설정**을 확장합니다.  
  
3.  **보안 설정**을 확장한 다음 **로컬 정책**을 확장합니다.  
  
4.  **사용자 권한 할당** 폴더를 선택합니다.  
  
     세부 정보 창에 정책이 표시됩니다.  
  
5.  세부 정보 창에서 **메모리의 페이지 잠그기**를 두 번 클릭합니다.  
  
6.  **로컬 보안 설정 – 메모리의 페이지 잠그기** 대화 상자에서 **사용자 또는 그룹 추가**를 클릭합니다.  
  
7.  **사용자, 서비스 계정 또는 그룹 선택** 대화 상자에서 sqlservr.exe를 실행할 권한이 있는 계정을 추가합니다.  
  
8.  이 변경 사항을 적용하려면 로그아웃한 다음 다시 로그인합니다.  
  
## 참고 항목  
 [서버 메모리 서버 구성 옵션](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  