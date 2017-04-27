---
title: "서버 찾아보기(네트워크 서버) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.browseservers.network.f1
ms.assetid: a59ffcd6-4b69-4c5c-9740-699ccb2183fb
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 0dfaef0364cf72e994b0fe5de778adc8a18bd715
ms.lasthandoff: 04/11/2017

---
# <a name="browse-for-servers-network-servers"></a>서버 찾아보기(네트워크 서버)
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 구성 요소에 연결 시 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인스턴스의 정확한 이름을 모르는 경우 **서버 이름** 상자에서 **더 찾아보기**를 클릭하여 **서버 찾아보기** 대화 상자를 엽니다.  
  
이 대화 상자는 서버 컴퓨터에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser 서비스로 채워집니다. 인스턴스의 이름이 목록에 나타나지 않는 경우 다음과 같은 여러 가지 이유 때문일 수 있습니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Browser 서비스가 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]를 실행하는 컴퓨터에서 실행 중이지 않을 수 있습니다.  
  
-   UDP 포트 1434가 방화벽에 의해 차단되었을 수 있습니다.  
  
-   **인스턴스 숨기기** 플래그가 설정되어 있을 수 있습니다.  
  
목록에 나타나지 않는 인스턴스에 연결하려면 TCP/IP 포트 번호 또는 명명된 파이프 이름을 포함하여 인스턴스의 전체 연결 문자열을 입력합니다.  
  
## <a name="options"></a>옵션  
**네트워크에서 연결할 SQL Server 인스턴스를 선택하십시오.**  
트리에 표시된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인스턴스를 클릭하여 연결할 서버를 지정합니다. **+** 또는 **–** 기호로 표시된 노드를 클릭하여 트리 뷰의 일부분을 표시하거나 숨길 수 있습니다.  
  
