---
title: SQL Server 속성(서비스 탭) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
ms.assetid: e4ae0c6b-6fd8-4325-b54e-1758fc659958
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d69ded06359dfc7f5f7c71864d3be6b64de6f7af
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48227327"
---
# <a name="sql-server-properties-service-tab"></a>SQL Server 속성(서비스 탭)
  **MSSQLSERVER 속성**대화 상자의 **서비스** 탭을 사용하여 다음 옵션을 확인하거나 지정할 수 있습니다.  
  
## <a name="options"></a>변수  
 **이진 경로**  
 이 서비스에 사용되는 프로그램 파일의 위치를 표시합니다.  
  
 **오류 제어**  
 1은 `SERVICE_ERROR_NORMAL`을 나타냅니다. 컴퓨터 시작 중에 서비스를 시작하지 못하면 시작 프로그램은 오류를 기록하고 팝업 메시지 상자를 표시하지만 컴퓨터를 시작하는 작업은 계속됩니다. 이 값은 변경할 수 없습니다.  
  
 **종료 코드**  
 오류가 발생하면 이 상자에 오류 번호가 나타납니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] 기술 자료에서 이 번호를 검색하여 오류를 해결하거나 기술 지원부에 이 번호를 제공하십시오.  
  
 **Host Name**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 컴퓨터 또는 클러스터의 이름을 표시합니다.  
  
 **이름**  
 서비스의 표시 이름을 나타냅니다.  
  
 **프로세스 ID**  
 Windows 프로세스 ID를 표시합니다.  
  
 **서비스 유형**  
 호출 프로세스에 제공되는 서비스의 유형을 표시합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 몇 가지 서비스를 설치합니다.  
  
 **시작 모드**  
 이 서비스를 다음 옵션으로 설정합니다.  
  
-   수동: 컴퓨터가 시작될 때 이 서비스가 자동으로 시작되지 않습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자나 다른 도구를 사용하여 서비스를 시작해야 합니다.  
  
-   자동: 컴퓨터가 시작될 때 이 서비스가 시작됩니다.  
  
-   사용 안 함: 이 서비스를 시작할 수 없습니다.  
  
 **State**  
 이 서비스가 실행 중인지, 중지되었는지 또는 비활성화되었는지 나타냅니다. "**...**"는 상태 변경이 보류 중임을 나타냅니다.  
  
  
