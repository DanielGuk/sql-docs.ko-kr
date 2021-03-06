---
title: 게시자 속성 - 배포자 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.configdistwizard.distpubproperties.f1
helpviewer_keywords:
- Publisher Properties dialog box
ms.assetid: ab6ada76-0f99-43fe-b524-baac7b1bc483
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b010746d438ae320452839ec5b959dec16da732c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731741"
---
# <a name="publisher-properties---distributor"></a>게시자 속성 - 배포자
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **게시자 속성** 대화 상자를 사용하여 게시자와 이 게시자의 배포자 간 관계와 연결된 속성을 보고 수정할 수 있습니다.  
  
## <a name="options"></a>Options  
 **에이전트에서 게시자 연결**  
 다음 에이전트가 배포자에서 게시자로 연결하는 컨텍스트를 지정합니다.  
  
-   지연 업데이트 구독을 허용하는 트랜잭션 게시에 대한 큐 판독기 에이전트  
  
-   Oracle 게시에 대한 스냅숏 에이전트 및 로그 판독기 에이전트  
  
 이러한 에이전트가 실행되는 **Windows 계정의 컨텍스트를 사용하여 게시자에 연결하거나** SQL Server 인증 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 을 지정한 다음 **로그인**및 **암호** 에 값을 입력하려면 **에이전트 프로세스 계정 가장**을 선택합니다. **에이전트 프로세스 계정 가장**을 선택하는 것이 좋습니다. 에이전트 보안에 대한 자세한 내용은 [복제 에이전트 보안 모델](../../relational-databases/replication/security/replication-agent-security-model.md)을 참조하세요.  
  
 이러한 에이전트가 실행되는 Windows 계정은 새 게시 마법사에서 지정합니다. 이 계정은 다음 대화 상자에서 변경할 수 있습니다.  
  
-   큐 판독기 에이전트의 **배포자 속성** 대화 상자  
  
-   스냅숏 에이전트 및 로그 판독기 에이전트의 **게시 속성** 대화 상자  
  
 **기타**  
 **게시자 유형** 및 **배포 데이터베이스 이름** 속성은 읽기 전용입니다. **기본 스냅숏 폴더** 속성은 변경할 수 있습니다. 스냅숏 폴더에 대한 자세한 내용은 [스냅숏 폴더 보안 설정](../../relational-databases/replication/security/secure-the-snapshot-folder.md)을 참조하세요.  
  
## <a name="see-also"></a>참고 항목  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [배포자 및 게시자 속성 보기 및 수정](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [속성 참조&#40;복제&#41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
