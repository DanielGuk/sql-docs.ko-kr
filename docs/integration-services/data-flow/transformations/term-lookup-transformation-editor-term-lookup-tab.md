---
title: "용어 조회 변환 편집기(용어 조회 탭) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.termlookup.termlookup.f1"
helpviewer_keywords: 
  - "용어 조회 변환 편집기"
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# 용어 조회 변환 편집기(용어 조회 탭)
  **용어 조회 변환 편집기** 대화 상자의 **용어 조회** 탭을 사용하여 입력 열을 참조 테이블의 조회 열로 매핑하고 각 출력 열의 별칭을 제공할 수 있습니다.  
  
 용어 조회 변환에 대한 자세한 내용은 [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)을 참조하십시오.  
  
## 옵션  
 **사용 가능한 입력 열**  
 확인란을 사용하여 변경되지 않은 출력 열로 전달할 입력 열을 선택합니다. 입력 열을 **사용 가능한 참조 열** 목록으로 끌어서 참조 테이블의 조회 열로 매핑할 수 있습니다. 입력 및 조회 열에 일치하는 지원 데이터 형식 DT_NTEXT 또는 DT_WSTR이 있어야 합니다. 매핑 선을 선택하고 마우스 오른쪽 단추를 클릭하여 [관계 만들기](../../../integration-services/data-flow/transformations/create-relationships.md) 대화 상자에서 매핑을 편집합니다.  
  
 **사용 가능한 참조 열**  
 참조 테이블에서 사용 가능한 열을 표시합니다. 일치시킬 용어 목록이 포함된 열을 선택합니다.  
  
 **통과 열**  
 사용 가능한 입력 열 목록에서 선택합니다. 선택 내용에 따라 **사용 가능한 입력 열** 테이블의 확인란이 달라집니다.  
  
 **출력 열 별칭**  
 각 출력 열의 별칭을 입력합니다. 기본값은 열 이름이지만 설명이 포함된 고유 이름을 임의로 선택할 수 있습니다.  
  
 **오류 출력 구성**  
 [오류 출력 구성](../Topic/Configure%20Error%20Output.md) 대화 상자를 사용하여 오류 발생의 원인이 되는 행에 대한 오류 처리 옵션을 지정할 수 있습니다.  
  
## 관련 항목:  
 [Integration Services 오류 및 메시지 참조](../../../integration-services/integration-services-error-and-message-reference.md)   
 [용어 조회 변환 편집기&#40;참조 테이블 탭&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [용어 조회 변환 편집기&#40;고급 탭&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [용어 추출 변환](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  