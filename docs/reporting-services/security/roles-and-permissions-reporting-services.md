---
title: "역할 및 권한(Reporting Services) | Microsoft Docs"
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
  - "액세스 제어 [Reporting Services]"
  - "사용 권한 [Reporting Services], 사용 권한 정보"
  - "보안 [Reporting Services], ID 및 액세스 제어"
  - "인증 [Reporting Services]"
  - "권한 [Reporting Services]"
  - "보안 [Reporting Services], 역할 기반"
  - "ID [Reporting Services]"
ms.assetid: eea655fe-43ed-418d-8233-b288a8f4daa4
caps.latest.revision: 18
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 18
---
# 역할 및 권한(Reporting Services)
  Reporting Services는 인증 하위 시스템 및 역할 기반 권한 부여 모델을 제공합니다. 인증 및 권한 부여 모델은 보고서 서버가 기본 모드에서 실행되는지, SharePoint 모드에서 실행되는지에 따라 달라집니다. 보고서 서버가 SharePoint 배포에 속하는 경우 SharePoint 권한에 따라 보고서 서버에 액세스할 수 있는 사용자가 결정됩니다.  
  
## 기본 모드에 대한 ID 및 액세스 제어  
 기본 인증은 Windows 인증 및 통합 보안을 기반으로 합니다. 보고서 서버가 여러 인증 요청에 응답할 수 있도록 인증 설정을 변경할 수 있으며, 기본 보안 기능을 사용자가 제공하는 사용자 지정 인증 확장 프로그램으로 바꿀 수도 있습니다.  
  
 권한 부여는 사용자가 보안 주체에 할당하는 역할을 기반으로 합니다. 각 역할은 관련 태스크 집합으로 구성되어 있으며 이러한 태스크는 관련 작업으로 구성되어 있습니다. 예를 들어 **보고서 관리** 태스크는 보고서 보기, 보고서 추가, 보고서 업데이트, 보고서 삭제, 보고서 예약, 보고서 속성 업데이트와 같은 보고서 서버 작업에 대한 액세스 권한을 부여합니다.  
  
## SharePoint 모드에 대한 ID 및 액세스 제어  
 SharePoint 통합 모드에서 인증 및 권한 부여는 이러한 요청이 보고서 서버에 도달하기 전에 SharePoint 사이트에서 처리됩니다. 인증 구성 방식에 따라 SharePoint 사이트의 요청에 보안 토큰이나 신뢰할 수 있는 사용자 이름이 포함됩니다. SharePoint 사용자 및 그룹에 대해 설정한 사용 권한은 SharePoint 라이브러리에 있는 보고서 서버 항목에 대한 액세스 권한을 부여합니다.  
  
## 섹션 내용  
 [기본 모드 보고서 서버에 대한 사용 권한 부여](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
 내용 및 작업에 대한 액세스 권한을 제공하는 역할 기반 권한 부여 모델에 대해 설명합니다.  
  
 [SharePoint 사이트의 보고서 서버 항목에 대한 사용 권한 부여](../../reporting-services/security/granting-permissions-on-report-server-items-on-a-sharepoint-site.md)  
 SharePoint 그룹, 사용 권한 수준 및 사용 권한을 사용하여 보고서 서버에 대한 액세스를 제어하는 방법에 대해 설명합니다.  
  
## 관련 항목:  
 [보고서 서버 인증](../../reporting-services/security/authentication-with-the-report-server.md)   
 [기본 모드 보고서 서버에 대한 사용 권한 부여](../../reporting-services/security/granting-permissions-on-a-native-mode-report-server.md)  
  
  