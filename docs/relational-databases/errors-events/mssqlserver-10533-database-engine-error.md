---
title: MSSQLSERVER_10533 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10533 (Database Engine error)
ms.assetid: cc2fbdab-7b90-415f-a1f9-066824344283
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 7748f025a36bbfd29b11e0f7c982fa36f317c6e0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703541"
---
# <a name="mssqlserver10533"></a>MSSQLSERVER_10533
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|10533|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|PG_NAME_TOO_BIG|  
|메시지 텍스트|계획 지침 이름이 허용된 최대 문자 수인 124자를 초과하므로 계획 지침 '%.*ls'을(를) 만들 수 없습니다. 125자 미만의 이름을 지정하십시오.|  
  
## <a name="explanation"></a>설명  
계획 지침 이름이 허용된 최대 문자 수인 124자를 초과합니다.  
  
## <a name="user-action"></a>사용자 동작  
125자 미만의 이름을 지정하십시오.  
  
## <a name="see-also"></a>참고 항목  
[계획 지침](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide&#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[sp_create_plan_guide_from_handle&#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
