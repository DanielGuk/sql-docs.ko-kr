---
title: MSSQLSERVER_3413 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3413 (Database Engine error)
ms.assetid: 3fa07637-ba93-4633-aaf2-ade7d18bc487
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2af9a604c511c50b542fbacd547afb3e09d7ea54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201873"
---
# <a name="mssqlserver3413"></a>MSSQLSERVER_3413
    
## <a name="details"></a>설명  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|3413|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|MARKDB|  
|메시지 텍스트|데이터베이스 ID %d. 데이터베이스를 주의 대상으로 표시할 수 없습니다. sys.databases.database_id의 Getnext NC 검색이 실패했습니다. 오류 로그에서 이전 오류를 참조하여 원인을 확인하고 관련 문제를 모두 해결하십시오.|  
  
## <a name="explanation"></a>설명  
 카탈로그에서 사용자 데이터베이스를 SUSPECT로 표시하려는 동안 예기치 않은 오류가 발생했습니다. SUSPECT 상태는 지속되지 않습니다.  
  
## <a name="user-action"></a>사용자 동작  
 이전 오류를 참조하여 문제를 해결하십시오.  
  
  
