---
title: 병합 복제 충돌 감지 및 해결 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- merge replication conflict resolution [SQL Server replication], about conflict resolution
- default conflict resolver
- conflict resolution [SQL Server replication]
- viewing merge replication conflicts
- resolving merge replication conflicts
- articles [SQL Server replication], conflict resolution
- merge replication conflict resolution [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: 0d033c76-e8c9-4e35-ab95-4d335abb18c1
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ada98028bface5ff05c54b89db4c0aacb6173636
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47599045"
---
# <a name="advanced-merge-replication---resolve-merge-replication-conflicts"></a>고급 병합 복제 - 병합 복제 충돌 해결
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  게시자와 구독자가 연결되고 동기화가 이루어지면 병합 에이전트는 충돌이 있는지 감지합니다. 충돌이 감지되면 병합 에이전트는 충돌 해결 프로그램을 사용해서 다른 사이트로 수락 및 전파할 데이터를 확인합니다.  
  
> [!NOTE]  
>  구독자와 게시자가 동기화되는 경우에도 충돌은 대체로 구독자 및 게시자에서 수행되는 업데이트가 아닌 여러 구독자에서 수행되는 업데이트 사이에서 발생합니다.  
  
 병합 복제는 충돌을 감지하고 해결하는 다양한 방법을 제공합니다. 대부분의 애플리케이션에는 기본 방법이 적합합니다.  
  
-   게시자와 구독자 사이에 충돌이 발생하면 게시자 변경 내용이 유지되고 구독자 변경 내용은 삭제됩니다.  
  
-   클라이언트 구독(가져오기 구독의 기본 유형)을 사용하는 두 구독자 사이에 충돌이 발생하면 게시자와 동기화하는 첫 번째 구독자의 변경 내용이 유지되고 두 번째 구독자의 변경 내용은 삭제됩니다. 클라이언트 및 서버 구독을 지정하는 방법에 대한 자세한 내용은 [병합 구독 유형 및 충돌 해결 우선 순위 지정&#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/specify-a-merge-subscription-type-and-conflict-resolution-priority.md)을 참조하세요.  
  
-   서버 구독(밀어넣기 구독의 기본 유형)을 사용하는 두 구독자 사이에 충돌이 발생하면 우선 순위가 가장 높은 구독자의 변경 내용이 유지되고 두 번째 구독자의 변경 내용은 삭제됩니다. 우선 순위 값이 같으면 게시자와 동기화하는 첫 번째 구독자의 변경 내용이 유지됩니다.  
  
 병합 복제의 충돌 감지 및 해결에 대한 자세한 내용은 [Advanced Merge Replication Conflict Detection and Resolution](../../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [병합 복제를 위한 아티클 옵션](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [게시 구독](../../../relational-databases/replication/subscribe-to-publications.md)  
  
  
