---
title: MSSQLSERVER_8993 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8993 (Database Engine error)
ms.assetid: 06aac110-a41c-4853-bc8e-a83e8535b8be
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: eb4856b0c4fe0c364958230fdf85681a0624163b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792841"
---
# <a name="mssqlserver8993"></a>MSSQLSERVER_8993
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|8993|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|DBCC3_MISSING_FORWARDED_ROW|  
|메시지 텍스트|개체 ID O_ID, 전달 행 페이지 P_ID1, 슬롯 S_ID1이(가) 페이지 P_ID2, 슬롯 S_ID2을(를) 가리킵니다. 전달된 행이 없습니다. 할당 오류인 것 같습니다.|  
  
## <a name="explanation"></a>설명  
힙의 전달 행이 존재하지 않는 전달된 행을 가리킵니다.  
  
## <a name="user-action"></a>사용자 동작  
  
### <a name="look-for-hardware-failure"></a>하드웨어 오류 찾기  
하드웨어 진단을 실행하여 문제가 있으면 이를 해결하십시오. [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 시스템 및 응용 프로그램 로그와 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 오류 로그도 검토하여 해당 오류가 하드웨어 오류로 인해 발생했는지 확인하십시오. 로그에 하드웨어 관련 문제가 포함되어 있으면 이를 해결하십시오.  
  
데이터 손상 문제가 지속되면 다른 하드웨어 구성 요소로 교체하여 문제를 해결하십시오. 시스템의 디스크 컨트롤러에 쓰기 캐시가 설정되어 있지 않은지 확인하세요. 쓰기 캐시가 문제가 된다고 생각되면 하드웨어 공급업체에 문의하십시오.  
  
마지막으로 새 하드웨어 시스템으로 교체하는 것이 유용할 수도 있습니다. 여기에는 디스크 드라이브를 다시 포맷하고 운영 체제를 다시 설치하는 작업도 포함됩니다.  
  
### <a name="restore-from-backup"></a>백업에서 복원  
하드웨어 관련 문제가 아니면 정상적인 백업(있는 경우)을 사용하여 데이터베이스를 복원하세요.  
  
### <a name="run-dbcc-checkdb"></a>DBCC CHECKDB 실행  
정상적인 백업이 없으면 REPAIR 절 없이 DBCC CHECKDB를 실행하여 손상된 정도를 확인하십시오. DBCC CHECKDB 실행 시 REPAIR 절을 사용하라는 메시지가 나타나면 적합한 REPAIR 절을 사용하여 DBCC CHECKDB를 실행하고 손상을 복구하십시오.  
  
> [!CAUTION]  
> REPAIR 절을 사용할 경우 DBCC CHECKDB가 데이터에 미치는 영향을 확인하려면 이 문을 실행하기 전에 주 지원 공급자에게 문의하세요.  
  
REPAIR 절 중 하나를 사용하여 DBCC CHECKDB를 실행해도 문제가 해결되지 않으면 주 지원 공급자에게 문의하세요.  
  
#### <a name="results-of-running-repair-options"></a>REPAIR 옵션의 실행 결과  
전달 행이 삭제되고 비클러스터형 인덱스가 있을 경우 다시 작성됩니다.  
  
