---
title: "스크립트 태스크 편집기(스크립트 페이지) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scripttask.script.f1"
helpviewer_keywords: 
  - "스크립트 태스크 편집기"
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# 스크립트 태스크 편집기(스크립트 페이지)
  **스크립트 태스크 편집기** 대화 상자의 **스크립트** 페이지를 사용하여 스크립트 속성을 설정하고 스크립트에서 액세스할 수 있는 변수를 지정할 수 있습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] 와 그 이후 버전에서는 모든 스크립트가 미리 컴파일됩니다. 그러나 이전 버전에서는 **PrecompileScriptIntoBinaryCode** 속성을 설정하여 스크립트가 미리 컴파일되었음을 지정해야 합니다.  
  
 스크립트 태스크에 대한 자세한 내용은 [Script Task](../../integration-services/control-flow/script-task.md) 및 [Configuring the Script Task in the Script Task Editor](../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)을 참조하십시오. 스크립트 태스크 프로그래밍 방법은 [Extending the Package with the Script Task](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)을 참조하십시오.  
  
## 옵션  
 **ScriptLanguage**  
 태스크에 대한 스크립트 언어를 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic 또는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# 중에서 선택합니다.  
  
 태스크에 대한 스크립트를 작성한 후에는 **ScriptLanguage** 속성의 값을 변경할 수 없습니다.  
  
 스크립트 태스크에 대한 스크립트 언어를 설정하려면 **옵션** 대화 상자의 **일반** 페이지에서 **스크립트 언어** 옵션을 사용하십시오. 자세한 내용은 [General Page](../Topic/General%20Page.md)을 참조하세요.  
  
 **EntryPoint**  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임이 스크립트 태스크 코드에 대한 진입점으로 호출하는 메서드를 지정합니다. 지정된 메서드는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] VSTA([!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications) 프로젝트의 ScriptMain 클래스에 있어야 합니다. ScriptMain 클래스는 스크립트 템플릿에서 생성하는 기본 클래스입니다.  
  
 VSTA 프로젝트에서 메서드 이름을 변경한 경우 **EntryPoint** 속성의 값을 변경해야 합니다.  
  
 **ReadOnlyVariables**  
 스크립트에 사용할 수 있는 읽기 전용 변수 목록을 쉼표로 구분하여 입력하거나 줄임표 단추(**…**)를 클릭하고 **변수 선택** 대화 상자에서 변수를 선택합니다.  
  
> [!NOTE]  
>  변수 이름은 대/소문자를 구분합니다.  
  
 **ReadWriteVariables**  
 스크립트에 사용할 수 있는 읽기/쓰기 변수 목록을 쉼표로 구분하여 입력하거나 줄임표 단추(**…**)를 클릭하고 **변수 선택** 대화 상자에서 변수를 선택합니다.  
  
> [!NOTE]  
>  변수 이름은 대/소문자를 구분합니다.  
  
 **스크립트 편집**  
 스크립트를 작성하거나 수정할 수 있는 VSTA IDE가 열립니다.  
  
## 관련 항목:  
 [Integration Services 오류 및 메시지 참조](../../integration-services/integration-services-error-and-message-reference.md)   
 [일반 페이지](../Topic/General%20Page.md)   
 [스크립트 태스크 편집기&#40;일반 페이지&#41;](../../integration-services/control-flow/script-task-editor-general-page.md)   
 [식 페이지](../../integration-services/expressions/expressions-page.md)   
 [스크립트 태스크 예](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integration Services&#40;SSIS&#41; 변수](../../integration-services/integration-services-ssis-variables.md)   
 [패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
  