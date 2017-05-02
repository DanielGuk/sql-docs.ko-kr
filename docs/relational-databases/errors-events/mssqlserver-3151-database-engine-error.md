---
title: "MSSQLSERVER_3151 | Microsoft 문서"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 3151 (Database Engine error)
ms.assetid: a8657a91-ec75-4649-a09a-21920e0030ff
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 3ce19f35c02f1af6fb430eb6d6beb318e7c4b80a
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver3151"></a>MSSQLSERVER_3151
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|3151|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|LDDB_MASTER_LOAD_FAILED|  
|메시지 텍스트|master 데이터베이스를 복원하지 못했습니다. SQL Server를 종료합니다. Check the error logs, and rebuild the master database. master 데이터베이스를 다시 작성하는 방법은 SQL Server 온라인 설명서를 참조하십시오.|  
  
## <a name="explanation"></a>설명  
**master** 데이터베이스에서 발생하는 다양한 문제를 나타내는 일반적인 오류 메시지입니다.  
  
## <a name="user-action"></a>사용자 동작  
자세한 내용은 오류 로그를 확인하십시오. 사용 가능한 **master** 데이터베이스를 만들려면 REBUILDDATABASE 옵션을 사용하여 Setup.exe를 실행합니다. 자세한 내용은 SQL Server 온라인 설명서의 "방법: 명령 프롬프트에서 SQL Server 설치"를 참조하세요.  
  
