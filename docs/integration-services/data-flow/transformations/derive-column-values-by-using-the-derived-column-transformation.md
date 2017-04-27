---
title: "파생 열 변환을 사용하여 열 값 파생 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "열 [Integration Services]"
  - "파생 열"
  - "열 [Integration Services], 값"
  - "파생 열 변환"
ms.assetid: 28b07746-fc6f-42b2-b741-9de6fac3f29c
caps.latest.revision: 48
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 48
---
# 파생 열 변환을 사용하여 열 값 파생
  파생 열 변환을 추가 및 구성하려면 패키지에 적어도 하나 이상의 데이터 흐름 태스크와 하나의 원본이 이미 들어 있어야 합니다.  
  
 파생 열 변환은 식을 사용하여 기존 열의 값을 업데이트하거나 새 열에 값을 추가합니다. 새 열에 값을 추가하는 경우 **파생 열 변환 편집기** 대화 상자에서 식을 계산하고 열의 메타데이터를 적절히 정의합니다. 예를 들어 각각 DT_WSTR 데이터 형식이며 길이가 50인 두 개의 열을 식에서 두 열 값 사이에 공백을 두고 연결할 경우 새 열은 데이터 형식이 DT_WSTR이고 길이는 101이 됩니다. 새 열의 데이터 형식을 업데이트할 수 있습니다. 유일한 요구 사항은 데이터 형식이 삽입된 데이터와 호환되어야 한다는 것입니다. 예를 들어 정수 데이터 형식이 있는 열에 데이터 값을 할당할 경우 **파생 열 변환 편집기** 대화 상자에서 유효성 검사 오류가 발생합니다. 선택한 데이터 형식에 따라 열의 길이, 전체 자릿수, 소수 자릿수 및 코드 페이지를 지정할 수 있습니다.  
  
### 열 값을 파생하려면  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]에서 원하는 패키지가 들어 있는 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 프로젝트를 엽니다.  
  
2.  솔루션 탐색기에서 패키지를 두 번 클릭하여 엽니다.  
  
3.  **데이터 흐름** 탭을 클릭한 다음 **도구 상자**에서 파생 열 변환을 디자인 화면으로 끌어 옵니다.  
  
4.  원본이나 이전 변환에서 연결선을 파생 열 변환으로 끌어서 파생 열 변환을 데이터 흐름에 연결합니다.  
  
5.  파생 열 변환을 두 번 클릭합니다.  
  
6.  **파생 열 변환 편집기** 대화 상자에서 변수, 열, 함수 및 연산자를 표의 **식** 열로 끌어서 조건에 따라 사용할 식을 작성합니다. 또는 **식** 열에 식을 직접 입력할 수 있습니다.  
  
    > [!NOTE]  
    >  식이 올바르지 않으면 식 텍스트가 강조 표시되고 열의 도구 설명에 오류에 대한 설명이 제공됩니다.  
  
7.  **파생 열** 목록에서 **\<새 열로 추가>**를 선택하여 식의 계산 결과를 새 열에 기록하거나 기존 열을 선택하여 평가 결과를 업데이트합니다.  
  
     새 열을 사용하는 경우 **파생 열 변환 편집기** 대화 상자는 식을 계산하고 데이터 형식, 길이, 전체 자릿수, 소수 자릿수 및 코드 페이지에 따라 열에 데이터 형식을 할당합니다.  
  
8.  새 열을 사용하는 경우 **데이터 형식** 목록에서 데이터 형식을 선택합니다. 선택한 데이터 형식에 따라 선택적으로 **길이**, **전체 자릿수**, **소수 자릿수**및 **코드 페이지** 열에서 값을 업데이트합니다. 기존 열의 메타데이터는 변경할 수 없습니다.  
  
9. 선택적으로 **파생 열 이름** 열의 값을 수정합니다.  
  
10. 오류 출력을 구성하려면 **오류 출력 구성**을 클릭합니다. 자세한 내용은 [데이터 흐름 구성 요소에서 오류 출력 구성](../../../integration-services/troubleshooting/configure-an-error-output-in-a-data-flow-component.md)을 참조하세요.  
  
11. **확인**을 클릭합니다.  
  
12. 업데이트된 패키지를 저장하려면 **파일** 메뉴에서 **선택한 항목 저장** 을 클릭합니다.  
  
## 관련 항목:  
 [파생 열 변환](../../../integration-services/data-flow/transformations/derived-column-transformation.md)   
 [Integration Services 데이터 형식](../../../integration-services/data-flow/integration-services-data-types.md)   
 [Integration Services 변환](../../../integration-services/data-flow/transformations/integration-services-transformations.md)   
 [Integration Services 경로](../../../integration-services/data-flow/integration-services-paths.md)   
 [데이터 흐름 태스크](../../../integration-services/control-flow/data-flow-task.md)   
 [Integration Services&#40;SSIS&#41; 식](../../../integration-services/expressions/integration-services-ssis-expressions.md)  
  
  