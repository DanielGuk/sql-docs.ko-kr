---
title: "구성할 서버 선택(데이터베이스 미러링 보안 구성 마법사) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.configdbmsecurwiz.choosesrvrs.f1"
ms.assetid: 59e23ff3-d7ee-4e32-9629-0b54d3a258f7
caps.latest.revision: 25
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 25
---
# 구성할 서버 선택(데이터베이스 미러링 보안 구성 마법사)
  이 페이지를 사용하여 지금 구성할 서버 인스턴스를 지정할 수 있습니다. 마법사를 계속하려면 서버 인스턴스를 적어도 하나 이상 선택해야 합니다.  
  
 서버 인스턴스에 대한 확인란을 선택 취소하면 해당 인스턴스가 변경되지 않지만 해당 인스턴스에 대한 정보를 입력하라는 메시지가 나타나고 이 정보가 다른 서버 인스턴스 구성의 일부로 저장됩니다. 예를 들어 미러링 모니터 서버 인스턴스에 대한 확인란을 선택 취소하면 주 서버 인스턴스와 미러 서버 인스턴스에 저장된 보안 구성의 일부로 해당 계정에 대한 로그인을 만들어야 하기 때문에 미러링 모니터 서버의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 계정을 입력하라는 메시지가 나타납니다.  
  
 **SQL Server Management Studio를 사용하여 데이터베이스 미러링을 구성하려면**  
  
-   [Windows 인증을 사용하여 데이터베이스 미러링 세션 구성&#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/establish database mirroring session - windows authentication.md)  
  
-   [데이터베이스 미러링 보안 구성 마법사 시작&#40;SQL Server Management Studio&#41;](../../database-engine/database-mirroring/start the configuring database mirroring security wizard.md)  
  
## 옵션  
 **주 서버 인스턴스**  
 주 서버에 대한 보안을 구성하려면 선택합니다.  
  
 **미러 서버 인스턴스**  
 미러 서버에 대한 보안을 구성하려면 선택합니다.  
  
 **미러링 모니터 서버 인스턴스**  
 미러링 모니터 서버(있는 경우)에 대한 보안을 구성하려면 선택합니다.  
  
## 참고 항목  
 [데이터베이스 속성&#40;미러링 페이지&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [데이터베이스 미러링&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md)  
  
  