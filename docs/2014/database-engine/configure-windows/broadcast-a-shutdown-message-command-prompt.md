---
title: 종료 메시지 브로드캐스트(명령 프롬프트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f4ac2fc507e86a9f0b24b03f661326a64f20f354
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48055876"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>종료 메시지 브로드캐스트(명령 프롬프트)
  이 항목에서는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에서 **net send** 명령을 사용하여 종료 메시지를 브로드캐스팅하는 방법에 대해 설명합니다. 사용자가 제시간에 태스크를 완료할 수 있도록 메시지에 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스 중지 시간을 포함시키세요.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>종료 메시지를 브로드캐스팅하려면  
  
1.  명령 프롬프트에서 다음을 입력합니다.  
  
     **net send /users "message"**  
  
     **/users** 옵션은 서버에 연결된 모든 사용자에게 메시지를 보내도록 지정합니다.  
  
> [!NOTE]  
>  **net send** 명령을 사용하려면 보내는 컴퓨터와 받는 컴퓨터 모두에서 메신저 서비스가 실행되고 있어야 합니다. 메신저 서비스는 Windows Server 2003에서 기본적으로 해제되어 있습니다. **net send**에 대한 자세한 내용은 Windows 설명서를 참조하세요.  
  
 네트워크에서는 전자 메일이나 전화로 사용자에게 연락하는 것이 더 적절합니다. 현재 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 연결된 사용자를 확인하려면 작업 모니터를 사용합니다. 작업 모니터에 대한 자세한 내용은 [작업 모니터](../../relational-databases/performance-monitor/activity-monitor.md) 및 [작업 모니터 열기&#40;SQL Server Management Studio&#41;](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](start-stop-pause-resume-restart-sql-server-services.md)  
  
  
