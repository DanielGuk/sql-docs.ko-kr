---
title: 패키지 개체 복사 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 43378e9129b40324144a2f20f2039f6f376fa39d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200523"
---
# <a name="copy-package-objects"></a>패키지 개체 복사
  이 항목에서는 한 패키지 내에서 또는 패키지 간에 제어 흐름 항목, 데이터 흐름 항목 및 연결 관리자를 복사하는 방법에 대해 설명합니다.  
  
### <a name="to-copy-control-and-data-flow-items"></a>제어 흐름 항목 및 데이터 흐름 항목을 복사하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 복사할 두 패키지를 두 번 클릭합니다.  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 복사할 항목이 포함된 패키지의 탭을 클릭한 다음 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.  
  
4.  복사할 제어 흐름 항목 또는 데이터 흐름 항목을 선택합니다. Shift 키를 누른 채 항목을 클릭하여 한 번에 한 항목을 선택하거나 선택할 항목을 포인터로 끌어서 그룹으로 선택할 수 있습니다.  
  
    > [!IMPORTANT]  
    >  항목을 연결하는 선행 제약 조건 및 경로는 연결하는 두 항목을 선택할 때 자동으로 선택되지 않습니다. 순서가 지정된 워크플로, 즉 제어 흐름 또는 데이터 흐름 세그먼트를 복사하려면 선행 제약 조건 및 경로도 복사해야 합니다.  
  
5.  선택한 항목을 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다.  
  
6.  항목을 다른 패키지에 복사하는 경우 복사할 패키지를 클릭한 다음 항목 유형에 해당하는 탭을 클릭합니다.  
  
    > [!IMPORTANT]  
    >  패키지에 한 개 이상의 데이터 흐름 태스크가 포함되지 않은 경우 데이터 흐름을 패키지에 복사할 수 없습니다.  
  
7.  마우스 오른쪽 단추를 클릭한 다음 **붙여넣기**를 클릭합니다.  
  
### <a name="to-copy-connection-managers"></a>연결 관리자를 복사하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 작업할 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭합니다.  
  
3.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.  
  
4.  **연결 관리자** 영역에서 연결 관리자를 마우스 오른쪽 단추로 클릭한 다음 **복사**를 클릭합니다. 한 번에 하나의 연결 관리자만 복사할 수 있습니다.  
  
5.  항목을 다른 패키지에 복사하는 경우 복사할 패키지를 클릭한 다음 **제어 흐름**, **데이터 흐름**또는 **이벤트 처리기** 탭을 클릭합니다.  
  
6.  **연결 관리자** 영역을 마우스 오른쪽 단추로 클릭한 다음 **붙여넣기**를 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [제어 흐름](control-flow/control-flow.md)   
 [데이터 흐름](data-flow/data-flow.md)   
 [Integration Services&#40;SSIS&#41; 연결](connection-manager/integration-services-ssis-connections.md)   
 [프로젝트 항목 복사](../../2014/integration-services/copy-project-items.md)  
  
  
