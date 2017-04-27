---
title: "Errors and Warnings 데이터 열 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "오류 및 경고 이벤트 범주 [SQL Server]"
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
caps.latest.revision: 24
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 24
---
# Errors and Warnings 데이터 열
  Security Audit 이벤트 범주에는 다음과 같은 이벤트 클래스가 있습니다.  
  
-   Error 클래스  
  
 다음 표에서는 이 이벤트 클래스에 대한 데이터 열을 나열합니다.  
  
## Error 이벤트 클래스 - 데이터 열  
  
|**열 이름**|**열 ID**|**열 유형**|**열 설명**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1.|이벤트 클래스는 이벤트를 분류하는 데 사용됩니다.|  
|StartTime|3|5|이벤트가 시작된 시간을 포함합니다(사용 가능한 경우). 필터링 형식은 'YYYY-MM-DD' 및 'YYYY-MM-DD HH:MM:SS'입니다.|  
|SessionType|8|8|오류를 발생시킨 엔터티의 유형을 포함합니다.|  
|Severity|22|1.|오류 이벤트와 연결된 예외의 심각도 수준을 포함합니다. 값은 다음과 같습니다.<br /><br /> 0 = 성공<br /><br /> 1 = 알림<br /><br /> 2 = 경고<br /><br /> 3 = 오류|  
|성공|23|1.|오류 이벤트의 성공 또는 실패를 포함합니다. 값은 다음과 같습니다.<br /><br /> 0 = 실패<br /><br /> 1 = 성공|  
|오류|24|1.|오류 이벤트와 연결된 모든 오류의 오류 번호를 포함합니다.|  
|ConnectionID|25|1.|오류 이벤트와 연결된 고유 연결 ID를 포함합니다.|  
|DatabaseName|28|8|오류 이벤트가 발생한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 이름을 포함합니다.|  
|NTUserName|32|8|오류 이벤트와 연결된 Windows 사용자 이름을 포함합니다.|  
|NTDomainName|33|8|로그인 이벤트와 연결된 Windows 도메인 계정을 포함합니다.|  
|ClientHostName|35|8|클라이언트를 실행 중인 컴퓨터의 이름을 포함합니다. 클라이언트가 호스트 이름을 제공하면 이 데이터 열이 채워집니다.|  
|ClientProcessID|36|1.|클라이언트 응용 프로그램의 프로세스 ID를 포함합니다.|  
|ApplicationName|37|8|서버 연결을 만든 클라이언트 응용 프로그램의 이름을 포함합니다. 이 열은 프로그램의 표시 이름이 아니라 응용 프로그램에서 전달한 값으로 채워집니다.|  
|SessionID|39|8|오류 이벤트와 연결된 사용자 세션을 고유하게 식별하는 SPID(서버 프로세스 ID)를 포함합니다. SPID는 XMLA(XML for Analysis)에서 사용하는 세션 GUID와 정확히 일치합니다.|  
|SPID|41|1.|오류 이벤트와 연결된 사용자 세션을 고유하게 식별하는 SPID(서버 프로세스 ID)를 포함합니다. SPID는 XMLA(XML for Analysis)에서 사용하는 세션 GUID와 정확히 일치합니다.|  
|TextData|42|9|오류 이벤트와 연결된 텍스트 데이터를 포함합니다.|  
|ServerName|43|8|오류 이벤트가 발생한 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스를 실행하는 서버의 이름을 포함합니다.|  
  
## 관련 항목:  
 [Security Audit 이벤트 범주](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  