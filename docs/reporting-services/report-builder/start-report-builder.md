---
title: "보고서 작성기 시작 | Microsoft Docs"
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
  - "보고서 작성기, 시작"
  - "보고서 작성기 시작"
  - "SharePoint 통합 [Reporting Services], 보고서 작성기 시작"
  - "보고서 작성기 시작"
ms.assetid: 8c8c7d2e-b315-418d-bf65-90e7685e4259
caps.latest.revision: 56
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 56
---
# 보고서 작성기 시작
  Microsoft [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]는 독립 실행형 보고서 제작 환경입니다. 보고서 작성기를 사용하면 페이지를 매긴 보고서를 만들어 기본 또는 SharePoint 통합 모드에서 설치된 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에 게시할 수 있습니다.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 웹 포털 또는 SharePoint 통합 모드의 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 처음으로 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]를 시작하면 Microsoft 다운로드 센터에서 다운로드하라는 메시지가 표시됩니다. 
 
![report-builder-get-report-builder](../../reporting-services/report-builder/media/report-builder-get-report-builder.png) 
 
 개발자나 관리자는 [Microsoft 다운로드 센터에서 컴퓨터에 보고서 작성기를 설치](http://go.microsoft.com/fwlink/?LinkID=219138)할 수도 있습니다. 자세한 내용은 [보고서 작성기 설치](../../reporting-services/install-windows/install-report-builder.md)의 "Systems Manager Server를 사용하여 보고서 작성기 설치"를 참조하세요.
 
 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]을 설치할 때 함께 설치되지 않으므로 별도로 다운로드하여 설치해야 합니다.  
  
 웹 포털 또는 SharePoint 사이트에서 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 를 시작할 때 이전 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 버전이 열리면 관리자에게 문의하세요. 그러면 관리자가 웹 포털이나 SharePoint 사이트의 버전을 업데이트할 수 있습니다.  
  
## [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 웹 포털에서 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 를 시작하려면  
  
1.  웹 브라우저의 주소 표시줄에 보고서 서버의 URL을 입력합니다. 기본적으로 이 URL은 http://\<*servername*>/reports입니다.  
  
2.  웹 포털의 위쪽 막대에서 **새로 만들기** > **페이지를 매긴 보고서**를 선택합니다.  
  
     ![PBI_SSMRP_NewMenu](../../reporting-services/mobile-reports/media/pbi-ssmrp-newmenu.png "PBI_SSMRP_NewMenu")  
  
     처음에는 [보고서 작성기를 설치](../../reporting-services/install-windows/install-report-builder.md)하라는 메시지가 표시됩니다. 
  
     그런 다음 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)]가 열립니다. 그러면 페이지를 매긴 보고서를 만들거나 보고서 서버의 보고서를 열 수 있습니다.  
  
## SharePoint 통합 모드에서 [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 를 시작하려면  
  
1.  원하는 라이브러리가 있는 SharePoint 사이트로 이동합니다.  
  
2.  라이브러리를 엽니다.  
  
3.  **문서**를 클릭합니다.  
  
4.  **새 문서** 메뉴에서 **보고서 작성기 보고서**를 클릭합니다.  
  
     이 작업을 처음 수행하면 SQL Server [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 마법사가 시작됩니다. 자세한 내용은 [Install Report Builder](../../reporting-services/install-windows/install-report-builder.md) 를 참조하십시오.  
  
     [!INCLUDE[ssRBnoversion](../../includes/ssrbnoversion-md.md)] 가 열립니다. 그러면 페이지를 매긴 보고서를 만들거나 보고서 서버의 보고서를 열 수 있습니다.  
  
     **참고**   **새 문서** 메뉴에 **보고서 작성기 보고서**, **보고서 작성기 모델**및 **보고서 데이터 원본**옵션이 나열되지 않는 경우 해당 콘텐츠 형식을 SharePoint 라이브러리에 추가해야 합니다. 자세한 내용은 [SharePoint 라이브러리에 Reporting Services 콘텐츠 형식 추가](../../reporting-services/report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)를 참조하세요.  
  
## 관련 항목:  
 [SQL Server 2016의 보고서 작성기](../../reporting-services/report-builder/report-builder-in-sql-server-2016.md)   
 [보고서 작성기에 대한 기본 옵션 설정](../../reporting-services/report-builder/set-default-options-for-report-builder.md)  
  
  