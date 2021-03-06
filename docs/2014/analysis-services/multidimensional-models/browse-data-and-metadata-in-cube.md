---
title: 데이터 및 큐브 메타 데이터 찾아보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: 5faf2a9d-df39-465f-9c81-a00d5cd63f5a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e074a41f6d9f5053562dd7b6be453644cb5fa176
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48076633"
---
# <a name="browse-data-and-metadata-in-cube"></a>큐브에서 데이터 및 메타데이터 찾아보기
  큐브 디자이너의 **브라우저** 탭에서 큐브 데이터를 검색할 수 있습니다. 이 뷰를 사용하여 큐브의 구조를 검토하고 데이터베이스 개체의 데이터, 계산, 형식, 보안을 확인할 수 있습니다. 보고 도구 또는 기타 클라이언트 애플리케이션에서 최종 사용자에게 큐브가 어떻게 표시되는지 신속하게 검토할 수 있습니다. 큐브 데이터를 검색할 때는 차원별로 데이터를 조회하고, 멤버를 드릴다운하고, 차원을 통해 데이터를 조각화할 수 있습니다.  
  
 큐브를 찾아보려면 먼저 큐브를 처리하고 다시 연결해야 합니다. 큐브를 처리한 후 큐브 디자이너의 **브라우저** 탭을 엽니다. 도구 모음에서 다시 연결 단추를 클릭하여 연결을 새로 고칩니다.  
  
 **브라우저** 탭에는 메타데이터, 필터 및 데이터라는 3가지 창이 있습니다. 메타데이터 창에서는 트리 형식으로 큐브의 구조를 검토할 수 있습니다. **브라우저** 탭 상단의 필터 창에서는 찾아볼 하위 큐브를 정의할 수 있습니다. 데이터 창에서는 결과 집합을 보고 차원 계층을 통해 드릴다운할 수 있습니다.  
  
## <a name="setting-up-the-browser"></a>브라우저 설정  
 큐브를 찾아보기 전 준비 단계로 먼저 사용할 큐브 뷰 또는 번역을 지정할 수 있습니다. 데이터 창에 측정값과 차원을 추가한 후 필터 창에서 적용할 필터를 지정합니다.  
  
##### <a name="specifying-a-perspective"></a>큐브 뷰 지정  
 **큐브 뷰** 목록에서 해당 큐브에 정의된 큐브 뷰를 선택합니다. 큐브 뷰는 큐브 디자이너의 **큐브 뷰** 탭에 정의되어 있습니다. 다른 큐브 뷰로 전환하려면 목록에서 원하는 큐브 뷰를 선택합니다.  
  
##### <a name="specifying-a-translation"></a>번역 지정  
 **언어** 목록에서 해당 큐브에 정의된 번역을 선택합니다. 번역은 큐브 디자이너의 **번역** 탭에 정의되어 있습니다. 기본적으로 **브라우저** 탭은 큐브의 **언어** 속성에 지정된 기본 언어로 캡션을 표시합니다. 다른 언어로 전환하려면 목록에서 원하는 언어를 선택합니다.  
  
##### <a name="formatting-the-data-pane"></a>데이터 창 서식 지정  
 데이터 창에서 캡션 및 셀의 서식을 지정할 수 있습니다. 서식을 지정할 셀 또는 캡션을 마우스 오른쪽 단추로 클릭한 다음 **명령 및 옵션**을 클릭합니다. 선택된 셀 또는 캡션에 따라 **명령 및 옵션** 대화 상자에 **서식**, **필터 및 그룹**, **보고서**및 **동작**에 대한 설정이 표시됩니다.  
  
## <a name="setting-up-the-data"></a>데이터 설정  
  
##### <a name="adding-or-removing-measures"></a>측정값 추가 또는 제거  
 메타데이터 창에서 작업 영역의 하단 오른쪽에 있는 큰 창인 데이터 창의 세부 정보 영역으로 찾아볼 측정값을 끌어 놓습니다. 다른 측정값을 끌어 놓으면 열로 추가됩니다. 추가 측정값을 끌어다 놓을 위치를 알려주는 세로 선이 표시됩니다. **측정값** 폴더를 끌어 놓으면 해당 폴더의 모든 측정값이 세부 정보 영역에 추가됩니다.  
  
 세부 정보 영역에서 측정값을 제거하려면 데이터 창 밖으로 해당 측정값을 끌어 놓거나 마우스 오른쪽 단추를 클릭한 다음 바로 가기 메뉴에서 **삭제** 를 클릭합니다.  
  
##### <a name="adding-or-removing-dimensions"></a>차원 추가 또는 제거  
 계층이나 차원을 행 또는 필터 영역으로 끌어 놓습니다.  
  
 여러 차원을 사용하려면 Excel에서 분석 기능을 사용합니다. Excel에서 분석은 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]와 동일한 컴퓨터에 설치될 경우 Excel을 시작하는 바로 가기입니다. Excel은 현재 데이터베이스에 대한 기존 연결 및 측정값과 차원이 미리 채워진 피벗 테이블 필드 목록을 포함하는 통합 문서를 엽니다. 자세한 내용은 [Excel에서 분석&#40;브라우저 탭, 큐브 디자이너&#41;&#40;Analysis Services - 다차원 데이터&#41;](../analyze-in-excel-browser-cube-designer-analysis-services-multidimensional-data.md)을 참조하세요.  
  
 차원을 제거하려면 데이터 창 밖으로 해당 차원을 끌어 놓거나 마우스 오른쪽 단추를 클릭한 다음 바로 가기 메뉴에서 **삭제**를 클릭합니다.  
  
##### <a name="adding-or-removing-filters"></a>필터 추가 또는 제거  
 다음 두 가지 방법으로 필터를 추가할 수 있습니다.  
  
-   메타데이터 창의 차원을 확장한 후 필터 창으로 계층을 끌어 놓습니다.  
  
     \- 또는-  
  
-   에 **차원** 열의 합니다 **필터** 창 클릭  **\<차원 선택 >** 목록에서 차원을 선택한 다음 클릭  **\<계층 선택 >** 에 **계층** 목록에서 계층을 선택 합니다.  
  
 계층을 지정한 후 연산자와 필터 식을 지정합니다. 다음 표에 연산자와 필터 식에 대한 설명이 나와 있습니다.  
  
|연산자|필터 식|Description|  
|--------------|-----------------------|-----------------|  
|같음|하나 이상의 멤버|값이 지정된 멤버와 일치해야 합니다.<br /><br /> (부모-자식 계층을 제외한 특성 계층의 경우 여러 멤버를 선택할 수 있으며, 그 외 계층은 하나의 멤버만 선택할 수 있습니다.)|  
|같지 않음|하나 이상의 멤버|값이 지정된 멤버와 달라야 합니다.<br /><br /> (부모-자식 계층을 제외한 특성 계층의 경우 여러 멤버를 선택할 수 있으며, 그 외 계층은 하나의 멤버만 선택할 수 있습니다.)|  
|입력|하나 이상의 명명된 집합|값이 지정된 명명된 집합에 포함되어야 합니다.<br /><br /> (특성 계층에서만 지원됩니다.)|  
|포함 안 함|하나 이상의 명명된 집합|값이 지정된 명명된 집합에 포함되지 않아야 합니다.<br /><br /> (특성 계층에서만 지원됩니다.)|  
|범위(포함)|범위를 나타내는 하나 또는 두 개의 구분 멤버|값이 구분 멤버 사이에 있거나 구분 멤버와 같아야 합니다. 구분 멤버가 서로 같거나 한 멤버만 지정된 경우 범위로 간주되지 않으며 모든 값이 허용됩니다.<br /><br /> 특성 계층에서만 지원됩니다. 범위는 계층 수준이 동일해야 합니다. 제한이 없는 범위는 현재 지원되지 않습니다.|  
|범위(제외)|범위를 나타내는 하나 또는 두 개의 구분 멤버|값이 구분 멤버 사이에 있어야 합니다. 구분 멤버가 서로 같거나 한 멤버만 지정된 경우 값이 구분 멤버보다 크거나 작아야 합니다.<br /><br /> 특성 계층에서만 지원됩니다. 범위는 계층 수준이 동일해야 합니다. 제한이 없는 범위는 현재 지원되지 않습니다.|  
|MDX|멤버 집합을 반환하는 MDX 식|값이 계산 멤버 집합에 포함되어야 합니다. 이 옵션을 선택하면 MDX 식을 작성할 수 있는 **계산 멤버 작성기** 대화 상자가 표시됩니다.|  
  
 필터 식에 여러 멤버를 지정할 수 있는 사용자 정의 계층의 경우 지정된 모든 멤버는 동일한 수준에 동일한 부모를 공유해야 합니다. 부모-자식 계층의 경우 이 제한 사항이 적용되지 않습니다.  
  
## <a name="working-with-data"></a>데이터 작업  
  
##### <a name="drilling-down-into-a-member"></a>멤버로 드릴다운  
 특정 멤버로 드릴다운하려면 멤버 옆의 더하기 기호(+)를 클릭하거나 멤버를 두 번 클릭합니다.  
  
##### <a name="slicing-through-cube-dimensions"></a>큐브 차원을 통해 조각화  
 큐브 데이터를 필터링하려면 최상위 열 머리글에서 드롭다운 목록 상자를 클릭합니다. 계층을 확장한 후 원하는 수준의 멤버를 선택하거나 지우면 해당 멤버 및 그 하위 항목이 모두 표시되거나 숨겨집니다. **(모두)** 옆의 확인란을 선택 해제하면 해당 계층 구조의 모든 멤버가 지워집니다.  
  
 차원에 이 필터를 설정한 후 데이터 창에서 마우스 오른쪽 단추를 클릭한 다음 **자동 필터**를 클릭하여 해당 필터를 설정 또는 해제할 수 있습니다.  
  
##### <a name="filtering-data"></a>데이터 필터링  
 필터 영역을 사용하여 찾아볼 하위 큐브를 정의할 수 있습니다. 필터 창에서 차원을 클릭하거나 메타데이터 창에서 차원을 확장한 후 필터 창으로 계층을 끌어 놓아 필터를 추가할 수 있습니다. 그런 다음 **연산자** 및 **필터 식**을 지정합니다.  
  
##### <a name="performing-actions"></a>동작 수행  
 데이터 창에서 머리글 또는 셀의 삼각형 표식은 수행할 수 있는 동작이 있음을 나타냅니다. 각 동작은 차원, 수준, 멤버 또는 큐브 셀에 대해 적용됩니다. 머리글 개체 위로 마우스 포인터를 이동하면 수행 가능한 동작 목록이 표시됩니다. 셀에서 삼각형 표식을 클릭하면 메뉴가 나타나 관련 프로세스를 시작할 수 있습니다.  
  
 보안을 위해 **브라우저** 탭에서는 다음 동작만 지원합니다.  
  
-   URL  
  
-   행 집합  
  
-   드릴스루  
  
 명령줄, 문 및 소유 동작은 지원되지 않습니다. URL 동작은 링크된 웹 페이지에 따라 안전하지 않을 수도 있습니다.  
  
##### <a name="viewing-member-properties-and-cube-cell-information"></a>멤버 속성 및 큐브 셀 정보 보기  
 차원 개체 또는 셀 값에 대한 정보를 보려면 셀 위로 마우스 포인터를 이동합니다.  
  
##### <a name="showing-or-hiding-empty-cells"></a>빈 셀 표시 또는 숨기기  
 데이터 창에서 마우스 오른쪽 단추를 클릭한 후 **빈 셀 표시**를 클릭하여 데이터 표의 빈 셀을 숨길 수 있습니다.  
  
  
