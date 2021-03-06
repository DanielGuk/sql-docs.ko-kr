---
title: 구독 유효성 검사 옵션(트랜잭션 구독) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ec241a087a3f82385fef96328b9178e7c15973ee
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183431"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>구독 유효성 검사 옵션(트랜잭션 구독)
  **구독 유효성 검사 옵션** 대화 상자를 사용하여 유효성 검사에서 행 개수만 사용할지, 아니면 행 개수와 이진 체크섬을 사용할지를 지정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **구독자와 게시자에 있는 복제된 데이터의 행 개수가 같은지 확인합니다.**  
 수행할 행 개수 유효성 검사의 유형을 선택합니다. Oracle 게시의 경우 **테이블을 직접 쿼리하여 실제 행 개수 계산**옵션만 사용할 수 있습니다.  
  
 **체크섬을 비교하여 행 데이터 확인**  
 게시자 및 구독자에서 행 개수를 확인하고 이진 체크섬 알고리즘을 사용하여 모든 데이터의 체크섬을 계산합니다. 행 개수 확인을 실패하면 체크섬 계산이 수행되지 않습니다.  
  
 **유효성 검사 완료 시 배포 에이전트 중지**  
 기본적으로 배포 에이전트는 계속 실행됩니다. 유효성 검사를 수행한 다음 에이전트를 중지하려면 이 옵션을 선택합니다. 이 옵션을 사용하면 데이터를 구독자로 복제하기 전에 유효성 검사의 성공 여부를 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [구독자에서 데이터 유효성 검사](validate-data-at-the-subscriber.md)   
 [복제된 데이터의 유효성 검사](validate-replicated-data.md)  
  
  
