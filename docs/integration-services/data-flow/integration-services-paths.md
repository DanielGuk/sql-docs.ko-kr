---
title: "Integration Services 경로 | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.patheditor.general.f1"
  - "sql13.dts.designer.patheditor.metadata.f1"
  - "sql13.dts.designer.patheditor.visualizers.f1"
helpviewer_keywords: 
  - "경로 [Integration Services], 경로 정보"
  - "데이터 흐름 [Integration Services], 경로"
  - "경로 [Integration Services]"
  - "대상 [Integration Services], 경로"
  - "원본 [Integration Services], 경로"
ms.assetid: 6c4629a9-2ede-4011-9101-3b342249640e
caps.latest.revision: 41
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# Integration Services 경로
  경로는 하나의 데이터 흐름 구성 요소의 출력을 다른 구성 요소의 입력에 연결함으로써 데이터 흐름의 두 구성 요소를 연결합니다. 경로에는 원본과 대상이 있습니다. 예를 들어 경로가 OLE DB 원본과 정렬 변환을 연결하는 경우 OLE DB 원본은 경로의 원본이며, 정렬 변환은 경로의 대상입니다. 원본은 경로가 시작되는 구성 요소이며, 대상은 경로가 끝나는 구성 요소입니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 패키지를 실행하는 경우에는 데이터 뷰어를 경로에 연결하여 데이터 흐름의 데이터를 볼 수 있습니다. 표에 데이터를 표시하도록 데이터 뷰어를 구성할 수 있습니다. 데이터 뷰어는 유용한 디버깅 도구입니다. 자세한 내용은 [Debugging Data Flow](../../integration-services/troubleshooting/debugging-data-flow.md)을 참조하세요.  
  
## 경로 구성  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너는 경로 속성을 설정하고, 경로를 통과하는 데이터 열의 메타데이터를 보고, 데이터 뷰어를 구성할 수 있는 **데이터 흐름 경로 편집기** 대화 상자를 제공합니다.  
  
 구성 가능한 경로 속성에는 경로의 이름, 설명 및 주석이 포함됩니다. 또한 경로를 프로그래밍 방식으로 구성할 수 있습니다. 자세한 내용은 [프로그래밍 방식으로 데이터 흐름 구성 요소 연결](../../integration-services/building-packages-programmatically/connecting-data-flow-components-programmatically.md)을 참조하세요.  
  
 경로 주석에는 **디자이너의** 데이터 흐름 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 탭에서 디자인 화면에 표시된 경로 원본의 이름 또는 경로 이름이 표시됩니다. 경로 주석은 데이터 흐름, 제어 흐름 및 이벤트 처리기에 추가할 수 있는 주석과 비슷합니다. 단지 경로 주석은 경로에 연결되며, 다른 주석은 **디자이너의**데이터 흐름 **,**제어 흐름 **및**이벤트 처리기 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 테이블에 표시된다는 점만 다릅니다.  
  
 메타데이터에는 이전 구성 요소의 출력에 있는 각 열의 이름, 데이터 형식, 전체 자릿수, 소수 자릿수, 길이, 코드 페이지 및 원본 구성 요소가 표시됩니다. 원본 구성 요소는 해당 열을 만든 데이터 흐름 구성 요소입니다. 이러한 구성 요소는 데이터 흐름에서 첫 번째 구성 요소일 수도 있으며, 아닐 수도 있습니다. 예를 들어 UNION ALL 및 정렬 변환은 해당 열을 만들며, 이는 출력 열에 대한 원본이 됩니다. 반대로 열 복사 변환은 열을 변경하지 않은 상태로 전달하거나 입력 열을 복사하여 새 열을 만들 수도 있습니다. 열 복사 변환은 새로운 열에 대해서만 원본 구성 요소가 됩니다.  
  
 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 사용하거나 프로그래밍 방식으로 속성을 설정할 수 있습니다.  
  
 **데이터 흐름 경로 편집기** 대화 상자에서 설정할 수 있는 속성에 대한 자세한 내용을 보려면 다음 항목 중 하나를 클릭하십시오.  
  
-   [데이터 흐름 경로 편집기&#40;일반 페이지&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(General%20Page\).md)  
  
-   [데이터 흐름 경로 편집기&#40;메타데이터 페이지&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Metadata%20Page\).md)  
  
-   [데이터 흐름 경로 편집기&#40;데이터 뷰어 페이지&#41;](../Topic/Data%20Flow%20Path%20Editor%20\(Data%20Viewers%20Page\).md)  
  
 프로그래밍 방식으로 설정할 수 있는 속성에 대한 자세한 내용은 [Path Properties](../Topic/Path%20Properties.md)을 참조하십시오.  
  
## 관련 작업  
  
-   [데이터 흐름 경로 편집기를 사용하여 경로 메타데이터 보기](../Topic/View%20Path%20Metadata%20in%20the%20Data%20Flow%20Path%20Editor.md)  
  
-   [데이터 흐름의 구성 요소 연결](../../integration-services/data-flow/connect-components-in-a-data-flow.md)  
  
## 관련 항목:  
 [데이터 흐름](../../integration-services/data-flow/data-flow.md)  
  
  