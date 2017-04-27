---
title: "ODBC 원본 편집기(오류 출력 페이지) | Microsoft Docs"
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
  - "sql13.ssis.designer.odbcsource.errorhandling.f1"
ms.assetid: b2f6866c-db07-4cb3-9f38-889f8d2b03e6
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# ODBC 원본 편집기(오류 출력 페이지)
  **ODBC 원본 편집기** 대화 상자의 **오류 출력** 페이지를 사용하여 오류 처리 옵션을 선택할 수 있습니다.  
  
 ODBC 원본에 대한 자세한 내용은 [CDC Source](../../integration-services/data-flow/cdc-source.md)을 참조하십시오.  
  
## 작업 목록  
 **ODBC 원본 편집기 오류 출력 페이지를 열려면**  
  
-   [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]에서 ODBC 원본이 있는 [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] 패키지를 엽니다.  
  
-   **데이터 흐름** 탭에서 ODBC 원본을 두 번 클릭합니다.  
  
-   **ODBC 원본 편집기**에서 **오류 출력**을 클릭합니다.  
  
## 옵션  
  
### 입/출력  
 데이터 원본의 이름을 표시합니다.  
  
### 열  
 사용되지 않습니다.  
  
### 오류  
 ODBC 원본에서 흐름의 오류를 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.  
  
### 잘림  
 ODBC 원본에서 흐름의 잘림을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.  
  
### Description  
 사용되지 않습니다.  
  
### 이 값을 선택한 셀에 설정  
 오류나 잘림 발생 시 ODBC 원본에서 선택한 모든 셀을 처리하는 방법을 선택합니다. 오류 무시, 행 리디렉션 또는 구성 요소 실패를 지정할 수 있습니다.  
  
### 적용  
 선택한 셀에 오류 처리 옵션을 적용합니다.  
  
## 오류 처리 옵션  
 다음 옵션을 사용하여 ODBC 원본에서 오류 및 잘림을 처리하는 방법을 구성할 수 있습니다.  
  
### 구성 요소 실패  
 오류 또는 잘림이 발생하면 데이터 흐름 태스크가 실패합니다. 이것이 기본 동작입니다.  
  
### 오류 무시  
 오류 또는 잘림이 무시됩니다.  
  
### 흐름 리디렉션  
 오류 또는 잘림을 발생시키는 행이 ODBC 원본의 오류 출력으로 전송됩니다. 자세한 내용은 [ODBC Source](../../integration-services/data-flow/odbc-source.md)을 참조하세요.  
  
## 관련 항목:  
 [ODBC 원본 편집기&#40;연결 관리자 페이지&#41;](../../integration-services/data-flow/odbc-source-editor-connection-manager-page.md)   
 [ODBC 원본 편집기&#40;열 페이지&#41;](../../integration-services/data-flow/odbc-source-editor-columns-page.md)  
  
  