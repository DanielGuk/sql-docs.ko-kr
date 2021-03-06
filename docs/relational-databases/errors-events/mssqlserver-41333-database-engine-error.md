---
title: MSSQLSERVER_41333 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41333 (Database Engine error)
ms.assetid: c3c3ae9a-1e4c-4de6-ba72-2f393375b053
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a4e5e6d6b8e7b8fb62c3e7e8948bad8ecf5b0af2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47703471"
---
# <a name="mssqlserver41333"></a>MSSQLSERVER_41333
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|이벤트 ID|41333|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|CROSS_CONTAINER_ISOLATION_FAILURE|  
|메시지 텍스트|RepeatableRead 트랜잭션, Serializable 트랜잭션 및 RepeatableRead 또는 Serializable 격리 상태에서 메모리에 최적화되지 않은 테이블에 액세스하는 트랜잭션은 스냅숏 격리 하에 메모리 액세스에 최적화된 테이블 및 고유하게 컴파일된 저장 프로시저에 액세스해야 합니다.|  
  
## <a name="explanation"></a>설명  
디스크 기반 트랜잭션과 XTP 트랜잭션 간에는 높은 격리 수준의 사용자에 대한 제한 사항이 있습니다.  
  
## <a name="user-action"></a>사용자 동작  
메모리 최적화 테이블(및 고유하게 컴파일된 프로시저) 및 디스크 기반 테이블에서는 높은 수준의 격리 작업을 시도하지 마세요.  
  
자세한 내용은 [메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
[메모리 내 OLTP&#40;메모리 내 최적화&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
