---
title: 구독 유형 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscriptiontype.f1
ms.assetid: 9a50f588-ee45-4a87-826f-372ff0798587
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 473c3ebc9347f5898e043a04a975e4fe497b0fc9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48091439"
---
# <a name="subscription-type"></a>구독 유형
  병합 복제는 서버와 클라이언트라는 구독 유형을 제공합니다. 이전 버전의 [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 각각 전역 및 로컬이라고 불렀습니다. 서버 구독이 있는 구독자는 다음을 수행할 수 있습니다.  
  
-   데이터를 다른 구독자에 다시 게시합니다.  
  
-   대체 동기화 파트너 역할을 수행합니다.  
  
-   설정한 우선 순위에 따라 충돌을 해결합니다.  
  
 대부분의 구독자는 이 기능이 필요하지 않으며 클라이언트 구독을 사용할 수 있습니다. 클라이언트 구독을 사용하면 충돌 감지 및 해결이 가능하지만 구독자에게 우선 순위가 할당되지 않습니다. 변경 내용을 게시자에 전송할 첫 번째 구독자는 해당 변경 내용으로 인해 발생하는 모든 충돌에서 우선 적용됩니다.  
  
> [!NOTE]  
>  구독 유형은 구독을 만든 후에는 변경할 수 없습니다.  
  
## <a name="options"></a>변수  
 **구독 속성**  
 각 구독자에 대해 **구독 유형** 열의 드롭다운 목록 상자에서 **클라이언트** 또는 **서버** 를 선택합니다. 서버 구독이 있는 구독자의 경우 **충돌 해결의 우선 순위** 열에 0에서 99.99 사이의 숫자를 입력합니다. 숫자가 클수록 구독자에 대한 우선 순위가 높습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [ssSDSFull](create-a-push-subscription.md)   
 [게시 구독](subscribe-to-publications.md)  
  
  
