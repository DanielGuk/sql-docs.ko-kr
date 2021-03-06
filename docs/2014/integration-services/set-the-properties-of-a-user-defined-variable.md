---
title: 사용자 정의 변수의 속성 설정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9cd85ac29d34f40e9473f28444c8b727543d6ecf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48075604"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>사용자 정의 변수의 속성 설정
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서 사용자 정의 변수의 속성을 설정하려면 다음 기능 중 하나를 사용합니다.  
  
-   변수 창.  
  
-   속성 창. **속성** 창에는 **변수** 창에서 사용할 수 없는 변수를 구성하기 위한 Description, EvaluateAsExpression, Expression, ReadOnly, ValueType 및 IncludeInDebugDump 속성이 나열됩니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]에서는 속성을 업데이트할 수 없는 시스템 변수 집합도 제공합니다(RaiseChangedEvent 속성은 제외).  
  
 **변수의 식 설정**  
  
 **속성** 창을 사용하여 사용자 정의 변수의 식을 설정하는 경우 다음을 참조하세요.  
  
-   변수 값은 Value 또는 Expression 속성에서 설정할 수 있습니다. 기본적으로 EvaluateAsExpression 속성 설정 `False` 변수의 값은 Value 속성에서 설정 됩니다. 값을 설정 하는 식을 사용 하려면 먼저 설정 해야 EvaluateAsExpression `True`, Expression 속성에서 식을 제공 합니다. Value 속성은 이 식의 계산 결과로 자동으로 설정됩니다.  
  
-   ValueType 속성에는 Value 속성에 있는 값의 데이터 형식이 포함됩니다. Value가 식에서 설정된 경우 ValueType은 해당 식의 계산 결과와 호환되는 데이터 형식으로 자동으로 업데이트됩니다. 값 0 및 ValueType 속성을 포함 하는 경우 포함 하는 예를 들어 **Int32** getdate ()에 다음 식을 설정, 현재 날짜 및 시간을 포함 하는 값 및 ValueType로 설정 된 `DateTime`합니다.  
  
-   변수에 대한 **속성** 창에서 **식 작성기** 대화 상자에 액세스할 수 있습니다. 이 도구를 사용하여 식 작성, 유효성 검사 및 계산을 수행할 수 있습니다. 자세한 내용은 [식 작성기](expressions/expression-builder.md) 및 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)을 참조하세요.  
  
 **변수** 창을 사용하여 사용자 정의 변수의 식을 설정하는 경우 다음을 참조하세요.  
  
-   식에 변수 값을 설정 하는 데 사용 하려면 먼저 변수 데이터 형식이 식의 평가 결과와 호환 되는지 확인 하 고 다음의 식을 제공 합니다 `Expression` 의 열을 **변수** 창. EvaluateAsExpression 속성을 **속성** 창이 자동으로 설정 된 `True`합니다.  
  
-   변수에 식을 할당할 경우 해당 변수 옆에 특수 아이콘 표식이 표시됩니다. 이 특수 아이콘 표식은 식이 설정되어 있는 연결 관리자 및 태스크 옆에도 표시됩니다.  
  
-   변수에 대한 **변수** 창에서 **식 작성기** 대화 상자에 액세스할 수 있습니다. 이 도구를 사용하여 식 작성, 유효성 검사 및 계산을 수행할 수 있습니다. 자세한 내용은 [식 작성기](expressions/expression-builder.md) 및 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)을 참조하세요.  
  
 둘 다에 **변수** 및 **속성** 창에서 변수에 식을 할당 하는 경우 및 `EvaluateAsExpression` 로 설정 된 `True`, 변수 데이터 형식을 변경할 수 없습니다.  
  
 **Namespace 및 Name 속성을 설정합니다.**  
  
 값을 `Name` 및 `Namespace` 속성은 Unicode Standard 2.0 또는 밑줄 (_)에 정의 된 대로 영문자를 사용 하 여 시작 해야 합니다. 후속 문자는 Unicode Standard 2.0에 정의된 문자 또는 숫자이거나 밑줄(\_)일 수 있습니다.  
  
## <a name="using-the-variables-window-to-set-properties"></a>변수 창을 사용하여 속성 설정  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>변수 창을 사용하여 변수의 속성을 설정하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.  
  
3.  **SSIS** 메뉴에서 **변수**를 클릭합니다.  
  
     **옵션** 대화 상자의 **키보드** 페이지에서 필요에 따라 선택한 키 조합에 View.Variables 명령을 매핑하여 **변수** 창을 표시할 수 있습니다.  
  
4.  필요에 따라 **변수** 창에서 **표 옵션**을 클릭하고 **변수** 창에 표시할 열을 선택한 다음 변수 목록에 적용할 필터를 선택합니다.  
  
5.  목록에서 변수를 선택 하 고 다음 값을 업데이트 합니다 `Name`, **데이터 형식**, `Value`를 `Namespace`를 **변경 이벤트 발생**, **설명,** 고 `Expression` 열입니다.  
  
6.  목록에서 변수를 선택하고 **변수 이동** 을 클릭하여 범위를 변경합니다.  
  
7.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.  
  
## <a name="using-the-properties-window-to-set-properties"></a>속성 창을 사용하여 속성 설정  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>속성 창을 사용하여 변수의 속성을 설정하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 마우스 오른쪽 단추로 클릭하여 엽니다.  
  
3.  **보기** 메뉴에서 **속성 창**을 클릭합니다.  
  
4.  [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에서 **패키지 탐색기** 탭을 클릭하고 패키지 노드를 확장합니다.  
  
5.  패키지 범위의 변수를 수정하려면 변수 노드를 확장합니다. 그렇지 않으면 수정할 변수가 있는 변수 노드를 찾을 때까지 이벤트 처리기 또는 실행 파일 노드를 확장합니다.  
  
6.  속성을 수정할 변수를 클릭합니다.  
  
7.  **속성** 창에서 읽기/쓰기 변수 속성을 업데이트합니다. 일부 속성은 사용자 정의 변수에 대해 읽기/읽기 전용입니다.  
  
     속성에 대한 자세한 내용은 [Integration Services&#40;SSIS&#41; 변수](integration-services-ssis-variables.md)를 참조하세요.  
  
8.  업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장**을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services &#40;SSIS&#41; 변수](integration-services-ssis-variables.md)   
 [패키지에서 변수 사용](../../2014/integration-services/use-variables-in-packages.md)   
 [패키지에서 사용자 정의 변수의 범위 추가, 삭제, 변경](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  
