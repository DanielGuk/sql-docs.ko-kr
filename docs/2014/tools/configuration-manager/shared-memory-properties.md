---
title: 공유 메모리 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- configmgr-client
ms.topic: conceptual
helpviewer_keywords:
- shared memory [SQL Server]
ms.assetid: dc1704da-eacd-4d26-b529-c996f958ca4b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2f2cbf499c8c5a7ab0a9cb10e0c0c301b3984f2e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185301"
---
# <a name="shared-memory-properties"></a>공유 메모리 속성
  **공유 메모리 속성** 대화 상자의 **프로토콜** 페이지를 사용하여 공유 메모리 프로토콜을 활성화 또는 비활성화할 수 있습니다. 공유 메모리는 가장 간단한 프로토콜이며 구성 가능한 설정이 없습니다. 공유 메모리 프로토콜을 사용하는 클라이언트는 동일한 컴퓨터에서 실행되는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에만 연결할 수 있으므로 대부분의 데이터베이스 작업에 유용하지 않습니다. 다른 프로토콜이 제대로 구성되지 않는 것으로 의심되는 경우 문제 해결에 공유 메모리 프로토콜을 사용하십시오.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 다시 시작해야 합니다.  
  
## <a name="options"></a>변수  
 **Enabled**  
 가능한 값은 **예** 및 **아니요**입니다. 공유 메모리 프로토콜은 기본적으로 활성화 상태입니다.  
  
## <a name="see-also"></a>관련 항목  
 [네트워크 프로토콜 선택](../../../2014/tools/configuration-manager/choosing-a-network-protocol.md)   
 [공유 메모리 프로토콜을 사용하여 유효한 연결 문자열 만들기](../../../2014/tools/configuration-manager/creating-a-valid-connection-string-using-shared-memory-protocol.md)  
  
  
