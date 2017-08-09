---
title: "스크립트 구성 요소와 데이터 흐름 확장 | Microsoft Docs"
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
dev_langs:
- VB
helpviewer_keywords:
- data flow task [Integration Services], components
- data flow [Integration Services], extending
- debugging [Integration Services], components
- code design mode [Integration Services]
- metadata [Integration Services]
- scripts [Integration Services], extending data flow
- data flow components [Integration Services], Script component
- components [Integration Services], data flow
- Script component [Integration Services], about Script component
- Script component [Integration Services]
- data flow [Integration Services], components
ms.assetid: 072bc4b8-363a-4131-87c3-240338e2fa5c
caps.latest.revision: 46
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: c58a854082fcbd12333be63995e4fcdf2d55aac7
ms.contentlocale: ko-kr
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-data-flow-with-the-script-component"></a>Extending the Data Flow with the Script Component
  스크립트 구성 요소 확장의 데이터 흐름 기능 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 로 작성 된 사용자 지정 코드를 사용 하 여 패키지 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#으로 컴파일하여 패키지 실행 시 실행 합니다. 스크립트 구성 요소를 사용하면 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]에서 제공하는 원본, 변환 및 대상이 개발자의 요구 사항을 완전히 만족시키지 못하는 경우 사용자 지정 데이터 흐름 원본, 변환 또는 대상을 손쉽게 개발할 수 있습니다. 필요한 입력 및 출력으로 구성 요소를 구성한 후에는 이 구성 요소에서 필요한 모든 인프라 코드를 자동으로 작성하므로 개발자는 사용자 지정 처리에 필요한 코드에만 집중하면 됩니다.  
  
 데이터 흐름에서 자동으로 생성 된 클래스를 통해 포함 하는 패키지와 스크립트 구성 요소 상호 작용 하는 **ComponentWrapper** 및 **BufferWrapper** 프로젝트 인스턴스인 항목의는 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent> 및 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptBuffer> 각각. 이러한 클래스는 연결, 변수 및 기타 패키지 항목을 형식화된 개체로 사용할 수 있도록 하고 입력과 출력을 관리합니다. 또한 스크립트 구성 요소에서는 사용자 지정 기능을 구현하는 데 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 네임스페이스 및 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 클래스 라이브러리뿐 아니라 사용자 지정 어셈블리도 사용합니다.  
  
 스크립트 구성 요소 및 해당 구성 요소가 생성하는 인프라 코드를 사용하면 사용자 지정 데이터 흐름 구성 요소를 개발하는 과정이 훨씬 간단해집니다. 그러나 스크립트 구성 요소의 작동 방식을 이해 하려면 하면 유용할 수 섹션 [사용자 지정 데이터 흐름 구성 요소 개발](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md) 는 사용자 지정 데이터 흐름 구성 요소를 개발 하는 단계를 이해 하 합니다.  
  
 여러 패키지에서 재사용할 원본, 변환 또는 대상을 만들 경우에는 스크립트 구성 요소를 사용하는 대신 사용자 지정 구성 요소를 개발하는 것이 좋습니다. 자세한 내용은 [사용자 지정 데이터 흐름 구성 요소 개발](../../../integration-services/extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)을 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
 다음 항목에서는 스크립트 구성 요소에 대해 자세히 설명합니다.  
  
 [스크립트 구성 요소 편집기에서 스크립트 구성 요소 구성](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)  
 속성에서 구성 하는 **스크립트 변환 편집기** 스크립트 구성 요소 코드의 성능 및 기능에 영향을 줍니다.  
  
 [코딩 및 스크립트 구성 요소 디버깅](../../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)  
 사용 된 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 응용 프로그램 (VSTA) 개발 환경 위한 스크립트 구성 요소에 포함 된 스크립트를 개발 도구입니다.  
  
 [스크립트 구성 요소 개체 모델 이해](../../../integration-services/extending-packages-scripting/data-flow-script-component/understanding-the-script-component-object-model.md)  
 새 스크립트 구성 요소 프로젝트에는 몇 개의 클래스와 자동 생성된 속성 및 메서드가 있는 세 개의 프로젝트 항목이 포함됩니다.  
  
 [스크립트 구성 요소에서 변수 사용](../../../integration-services/extending-packages-scripting/data-flow-script-component/using-variables-in-the-script-component.md)  
 **ComponentWrapper** 프로젝트 항목 패키지 변수에 대 한 강력한 형식의 접근자 속성이 포함 되어 있습니다.  
  
 [스크립트 구성 요소에서 데이터 원본에 연결](../../../integration-services/extending-packages-scripting/data-flow-script-component/connecting-to-data-sources-in-the-script-component.md)  
 **ComponentWrapper** 프로젝트 항목에는 또한 패키지에 정의 된 연결에 대 한 강력한 형식의 접근자 속성이 포함 되어 있습니다.  
  
 [스크립트 구성 요소에서 이벤트 발생](../../../integration-services/extending-packages-scripting/data-flow-script-component/raising-events-in-the-script-component.md)  
 문제 및 오류에 대한 알림을 제공하는 이벤트를 발생시킬 수 있습니다.  
  
 [스크립트 구성 요소의 로깅](../../../integration-services/extending-packages-scripting/data-flow-script-component/logging-in-the-script-component.md)  
 패키지에서 사용하도록 설정된 로그 공급자에 정보를 기록할 수 있습니다.  
  
 [특정 유형의 스크립트 구성 요소 개발](../../../integration-services/extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)  
 간단한 예를 통해 스크립트 구성 요소를 사용하여 데이터 흐름 원본, 변환 및 대상을 개발하는 방법을 설명하고 보여 줍니다.  
  
 [추가 스크립트 구성 요소 예제](../../../integration-services/extending-packages-scripting-data-flow-script-component-examples/additional-script-component-examples.md)  
 간단한 예를 통해 스크립트 구성 요소의 가능한 몇 가지 사용 방법을 설명하고 보여 줍니다.  
  
## <a name="see-also"></a>참고 항목  
 [스크립트 구성 요소](../../../integration-services/data-flow/transformations/script-component.md)   
 [스크립트 태스크와 스크립트 구성 요소를 비교합니다.](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  