---
title: "스크립트 태스크와 스크립트 구성 요소에서 중단점을 설정 하 여 스크립트 디버깅 | Microsoft Docs"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- breakpoints [Integration Services]
- scripts [Integration Services], breakpoints
ms.assetid: 6c03464f-3f7d-4882-b7f8-8e396f8e2944
caps.latest.revision: 33
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 96815b337311c4ba8d16e10c25891c728e7a0c74
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component"></a>스크립트 태스크 및 스크립트 구성 요소에서 중단점을 설정하여 스크립트 디버깅
  이 절차에서는 스크립트 태스크 및 스크립트 구성 요소에 사용되는 스크립트에서 중단점을 설정하는 방법에 대해 설명합니다.  
  
 스크립트에 중단점을 설정한 후의 **중단점 설정- \<개체 이름 >** 대화 상자에 기본 제공 중단점 함께 나열 합니다.  
  
> [!IMPORTANT]  
>  스크립트 태스크 및 스크립트 구성 요소의 중단점이 무시되는 경우도 있습니다. 자세한 내용은 참조는 **스크립트 태스크 디버깅** 섹션 [코딩 및 스크립트 태스크 디버깅](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md) 및 **Debugging the Script Component** 섹션 [코딩 및 스크립트 구성 요소 디버깅](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)합니다.  
  
### <a name="to-set-a-breakpoint-in-script"></a>스크립트에 중단점을 설정하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  중단점을 설정하려는 스크립트를 포함하는 패키지를 두 번 클릭합니다.  
  
3.  스크립트 태스크를 열려면는 **제어 흐름** 탭을 클릭 한 다음 스크립트 태스크를 두 번 클릭 합니다.  
  
4.  스크립트 구성 요소를 열려면는 **데이터 흐름** 탭을 클릭 한 다음 스크립트 구성 요소를 두 번 클릭 합니다.  
  
5.  클릭 **스크립트** 클릭 하 고 **스크립트 편집**합니다.  
  
6.  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSTA Tools for Applications (), 중단점을 설정, 해당 줄을 마우스 오른쪽 단추로 클릭 하 고, 가리킨 스크립트의 줄을 찾습니다 **중단점**, 클릭 하 고 **중단점 삽입**합니다.  
  
     코드 줄에 중단점 아이콘이 나타납니다.  
  
7.  **파일** 메뉴에서 **끝내기**를 클릭합니다.  
  
8.  **확인**을 클릭합니다.  
  
9. 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
  