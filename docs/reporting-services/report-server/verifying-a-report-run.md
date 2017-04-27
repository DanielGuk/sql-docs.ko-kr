---
title: "보고서 실행 확인 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "감사 [Reporting Services]"
  - "보고서 실행 확인"
  - "로그 [Reporting Services], 보고서 실행 확인"
  - "보고서 실행 데이터 [Reporting Services]"
  - " 상태 정보 [Reporting Services] "
  - "보고서 처리 [Reporting Services] 실행 확인"
  - "보고서 실행 검사"
ms.assetid: 18a98f2f-6b40-454e-9b37-568ed1a96458
caps.latest.revision: 37
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 37
---
# 보고서 실행 확인
  보고서 처리 상태에 대한 정보를 보려면 로그 파일을 사용하거나 보고서 관리자에서 보고서와 함께 표시되는 상태 정보를 참조할 수 있습니다.  
  
## 보고서 실행 데이터 원본  
 보고서 실행 로그는 보고서 이름, 보고서를 실행한 사용자 이름, 보고서 실행 시간 및 보고서 배포에 사용되는 배달 확장 프로그램 등 보고서 실행에 대한 포괄적인 정보를 제공합니다. 이 데이터를 확인하고 분석하려면 쿼리하고 보고서를 작성하기 쉬운 데이터베이스 테이블로 보고서 실행 로그를 복사할 수 있습니다.  
  
 로그 파일에는 보고서 실행 및 다른 서버 작업에 대한 여러 항목이 포함됩니다. 로그 파일에는 매우 다양한 데이터가 있기 때문에 보고서가 마지막으로 실행된 시간만 확인하려는 경우에는 보고서 관리자를 사용하는 것이 좋습니다. 다른 정보가 필요하면 로그 파일을 검토해야 합니다.  
  
> [!NOTE]  
>  보고서 관리자에는 요청 시에 실행되는 보고서의 처리 시간은 표시되지 않습니다.  
  
 다음 표에서는 다양한 종류의 보고서에 대한 처리 날짜 및 시간을 확인하는 방법을 설명합니다.  
  
|보고서 종류|날짜 및 시간 정보 표시 위치|정보 확인 방법|  
|-----------------------------|-----------------------------------------------|-----------------------------------------------|  
|보고서 스냅숏으로 실행되는 보고서|내용 페이지. 자세한 내용은 [내용 페이지&#40;보고서 관리자&#41;](../Topic/Contents%20Page%20\(Report%20Manager\).md)를 참조하세요.|1) 보고서가 포함된 폴더를 찾습니다.<br /><br /> 2) 폴더를 자세히 보기로 설정합니다.<br /><br /> 3) **실행 날짜** 열에서 날짜 및 시간을 확인합니다.|  
|보고서 기록의 스냅숏|기록 속성 페이지. 자세한 내용은 [스냅숏 옵션 속성 페이지&#40;보고서 관리자&#41;](../Topic/Snapshot%20Options%20Properties%20Page%20\(Report%20Manager\).md)를 참조하세요.|1) 보고서를 엽니다.<br /><br /> 2) **속성** 페이지를 클릭합니다.<br /><br /> 3) **기록** 탭을 클릭합니다.<br /><br /> 4) **실행 날짜** 열에서 날짜 및 시간을 확인합니다.|  
|캐시된 보고서|캐시된 보고서를 만들고 새로 고치는 데 사용되는 일정|1) 보고서를 엽니다.<br /><br /> 2) **속성** 페이지를 클릭합니다.<br /><br /> 3) **실행** 탭을 클릭합니다.<br /><br /> 4) 일정을 엽니다.|  
  
## 관련 항목:  
 [Reporting Services 로그 파일 및 소스](../../reporting-services/report-server/reporting-services-log-files-and-sources.md)   
 [보고서 처리 속성 설정](../../reporting-services/report-server/set-report-processing-properties.md)   
 [보고서 관리자&#40;SSRS 기본 모드&#41;](../Topic/Report%20Manager%20%20\(SSRS%20Native%20Mode\).md)  
  
  