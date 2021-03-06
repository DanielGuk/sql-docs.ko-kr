---
title: 큐 판독기 에이전트 보안 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.security.QRA.f1
helpviewer_keywords:
- Queue Reader Agent Security dialog box
ms.assetid: 77938da0-2afd-4455-8826-f4a6a9440cb3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2129289ae91688527156772c43d093851f52190
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47754383"
---
# <a name="queue-reader-agent-security"></a>큐 판독기 에이전트 보안
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **큐 판독기 에이전트 보안** 대화 상자를 사용하여 큐 판독기 에이전트가 실행 중이며 배포자에 로컬 연결을 설정하는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 계정을 지정할 수 있습니다. 에이전트는 **게시자 속성** 대화 상자( **배포자 속성** 대화 상자에서 사용 가능)에서 지정한 계정을 사용하여 게시자에 연결하고, 구독에 대한 배포 에이전트와 동일한 컨텍스트를 사용하여 구독자에 연결합니다. 자세한 내용은 [View and Modify Replication Security Settings](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md)을(를) 참조하세요.  
  
 계정은 올바른 암호가 지정된 유효한 것이어야 합니다. 계정 및 암호의 유효성은 에이전트를 실행할 때 검사합니다.  
  
## <a name="options"></a>Options  
 **프로세스 계정**  
 배포자에서 큐 판독기 에이전트가 실행되는 Windows 계정을 입력합니다. 지정한 Windows 계정은 적어도 배포 데이터베이스에 포함된 **db_owner** 고정 데이터베이스 역할의 멤버여야 합니다.  
  
 **암호** 및 **암호 확인**  
 Windows 계정의 암호를 입력합니다.  
  
## <a name="see-also"></a>참고 항목  
 [복제의 로그인 및 암호 관리](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [복제 에이전트 보안 모델](../../relational-databases/replication/security/replication-agent-security-model.md)   
 [복제 에이전트 개요](../../relational-databases/replication/agents/replication-agents-overview.md)   
 [복제 보안을 위한 최선의 구현 방법](../../relational-databases/replication/security/replication-security-best-practices.md)  
  
  
