---
title: '2 단원: 웹 참조 추가 | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a2c2b8b8-6b13-45ca-ab3b-1582447b6807
author: craigg-msft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: be009e76b1de70b405cf8b4e3faff2c1461f6dcd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48102513"
---
# <a name="lesson-2-adding-a-web-reference"></a>2단원: 웹 참조 추가
  웹 서비스 검색은 클라이언트에서 웹 서비스를 찾고 해당 서비스에 대한 설명을 얻는 과정입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 웹 서비스 검색 과정에는 미리 결정된 알고리즘을 따르는 웹 사이트를 질의하는 과정이 포함됩니다. 이러한 과정의 목적은 WSDL(웹 서비스 설명 언어)을 사용하는 XML 문서인 서비스 설명을 찾는 것입니다.  
  
 서비스 설명은 사용할 수 있는 서비스 및 이러한 서비스와 상호 작용하는 방법을 설명합니다. 서비스 설명이 없으면 웹 서비스와 프로그래밍 방식으로 상호 작용할 수 없습니다.  
  
 사용자의 응용 프로그램에는 웹 서비스와 통신하기 위한 방법과 실행할 때 웹 서비스를 찾을 수 있는 방법이 있어야 합니다. 웹 서비스에 대한 웹 참조를 프로젝트에 추가하면 웹 서비스와 상호 작용하고 웹 서비스의 로컬 표시를 제공하는 프록시 클래스를 생성할 수 있습니다. 자세한 내용은 "하는 방법에:: 생성 된 XML 웹 서비스 프록시"를 참조 하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 설명서.  
  
### <a name="to-add-a-web-reference"></a>웹 참조를 추가하려면  
  
1.  에 **프로젝트** 메뉴에서 클릭 **서비스 참조 추가**합니다.  
  
2.  에 **서비스 참조 추가** 대화 상자, 클릭 **고급**합니다.  
  
3.  에 **서비스 참조 설정** 대화 상자, 클릭 **웹 참조 추가**합니다.  
  
4.  에 **URL** 상자를 **웹 참조 추가** 대화 상자와 같은 서비스에 대 한 설명은 보고서 서버 웹 서비스를 얻을 수 있는 URL 입력 http://localhost/reportserver/reportservice2010.asmx합니다. 다음을 클릭 합니다 **이동** 웹 서비스에 대 한 정보를 검색 하는 단추입니다.  
  
     \- 또는-  
  
     보고서 서버 웹 서비스를 로컬 컴퓨터에 있는 경우 클릭 합니다 **로컬 컴퓨터의 웹 서비스** 브라우저 창에서 링크 합니다. 그런 다음 나타나는 목록에서 ReportService2010 웹 서비스에 대한 링크를 클릭합니다.  
  
5.  에 **웹 참조 이름** 상자에서이 웹 참조에 사용할 네임 스페이스인 reportservice2010으로 웹 참조 이름을 바꿉니다.  
  
6.  클릭 **참조 추가** 대상 웹 서비스에 대 한 웹 참조를 추가 합니다.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]는 서비스 설명을 다운로드하고 사용자 응용 프로그램과 보고서 서버 웹 서비스 간에 상호 작용할 프록시 클래스를 생성합니다. 웹 참조가 작동할 수 있도록 <xref:System.Web.Services> 네임스페이스에 대한 참조도 추가해야 합니다.  
  
7.  프로젝트 메뉴에서 **참조 추가**를 클릭합니다.  
  
8.  **참조 추가** 대화 상자의 **.NET** 탭에서 **System.Web.Services**를 선택하고 **확인**을 클릭합니다.  
  
 자세한 내용은 [SOAP API 액세스](../reporting-services/report-server-web-service/accessing-the-soap-api.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [보고서 서버 웹 서비스](../reporting-services/report-server-web-service/report-server-web-service.md)   
 [3 단원: 웹 서비스 액세스](../../2014/tutorials/lesson-3-accessing-the-web-service.md)   
 [Visual Basic 또는 Visual C를 사용 하 여 보고서 서버 웹 서비스에 액세스&#35; &#40;SSRS 자습서&#41;](../../2014/tutorials/access-report-server-web-service-vb-vcsharp-ssrs-tutorial.md)  
  
  
