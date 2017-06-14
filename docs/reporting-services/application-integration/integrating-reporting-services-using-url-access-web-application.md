---
title: "웹 응용 프로그램에서 URL 액세스 사용 | Microsoft Docs"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- links [Reporting Services], URL access
- URL access [Reporting Services], Web applications
- POST requests
- direct addressing [Reporting Services]
- Web applications [Reporting Services]
- hyperlinks [Reporting Services]
ms.assetid: 39e7918c-ad2d-4ca6-b099-2dd4dbdb83dc
caps.latest.revision: 33
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f931c5bd79835f8cf2ce9ceb88078e9408ace71a
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="integrating-reporting-services-using-url-access---web-application"></a>URL 액세스를 사용 하 여-웹 응용 프로그램, 서비스 보고 통합
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 URL 액세스는 네트워크를 통해 개별 보고서에 액세스할 수 있도록 특별히 디자인되었습니다. 이런 유형의 액세스는 보고서 보기와 탐색을 사용자 지정 웹 응용 프로그램으로 통합하는 데 알맞습니다. 웹 응용 프로그램에서 URL 액세스를 사용하려면 다음 작업을 수행할 수 있습니다.  
  
-   URL을 웹 사이트 또는 포털의 특정 보고서 서버로 지정합니다.  
  
-   폼 POST 메서드를 사용하고 양식 필드를 사용하여 쿼리 문자열 매개 변수를 보고서 서버 URL에 전달합니다.  
  
## <a name="url-access-through-direct-addressing"></a>직접 주소 지정을 통한 URL 액세스  
 URL을 사용하여 보고서 서버 또는 보고서 서버 데이터베이스 항목에 액세스하려면 웹 브라우저나 응용 프로그램 내에서 URL 주소를 제공하기만 하면 됩니다. 또한 액세스할 보고서 또는 리소스의 모양에 영향을 줄 수 있는 매개 변수를 URL에 제공할 수도 있습니다. 웹 브라우저의 주소 표시줄을 통해 보고서 서버는 대상으로 지정할 수는 URL 또는 URL의 원본으로 사용할 수는 **IFrame** 큰 웹 응용 프로그램이 나 포털의 일부인 합니다. 포털의 다양한 웹 페이지에 보고서 하이퍼링크를 포함시키거나 보고서에 대해 특정 프레임을 대상으로 지정하거나 프로세스 도중에 새 브라우저 창을 열 수 있습니다.  
  
 다음 예에서 하이퍼링크는 "main"이라는 프레임을 대상으로 지정하며 이 프레임은 하이퍼링크를 포함하는 프레임과 다를 수 있습니다. 하이퍼링크는 웹 포털의 일부일 수 있습니다.  
  
```  
<a href="http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main" target="main" >  
   Click here for the Territory Sales Drilldown sample report  
</a>  
```  
  
 이전 예에서 장치 정보 설정 **LinkTarget** URL의 쿼리 문자열에 "main" 값으로 전달 됩니다. 그러면 보고서의 드릴스루 하이퍼링크도 이름이 "main"인 프레임을 대상으로 지정합니다.  
  
 장치 정보 설정에 대 한 자세한 내용은 참조 [장치 정보 설정을 렌더링 확장 프로그램에 전달](../../reporting-services/report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)합니다.  
  
 상당수의 서버와 브라우저에서는 URL에 허용되는 문자 수를 제한합니다. 일부의 경우 256자 제한이 적용됩니다. 이 제한을 해결하려면 폼 제출을 사용하여 POST 요청을 사용하면 됩니다.  
  
> [!NOTE]  
>  Internet Explorer의 URL 길이는 최대 2,083자입니다. 이 제한은 POST 및 GET 요청 URL 모두에 적용됩니다. 하지만 POST는 이름/값 쌍을 폼의 일부로 제출하는 경우 URL이 아닌 머리글로 전송되기 때문에 URL 크기에 제한받지 않습니다.  
  
## <a name="url-access-through-a-form-post-method"></a>폼 POST 메서드를 통한 URL 액세스  
 사용자가 URL 액세스를 사용하여 보고서 서버에서 데이터를 요청하면 HTTP 요청에 GET 메서드가 사용됩니다. 이것은 METHOD="GET"인 폼 제출과 같습니다. METHOD="GET"을 사용하는 URL 요청 또는 폼 제출은 서버나 웹 브라우저에서 처리할 수 있는 최대 문자 수의 제한을 받습니다.  
  
 POST 요청(METHOD="POST" 및 입력 필드)의 경우 이름/값 쌍이 URL이 아닌 머리글로 전송됩니다. 따라서 쿼리 문자열의 이름/값 쌍은 URL의 일부가 아니므로 더 길고 복잡한 매개 변수 목록을 제공할 수 있게 됩니다.  
  
 사용자는 직접 액세스를 사용하면 보고서 서버에 대한 URL을 볼 수 있으며 쿼리 문자열을 수정하거나 특정 URL 요청 및 보고서 서버 매개 변수를 나중에 사용하도록 메모할 수 있습니다.  
  
 다음 예제 HTML은 특정 URL로 보고서 서버를 대상으로 지정하고 쿼리 문자열 매개 변수를 폼 입력 필드의 일부로 전달하는 데 사용할 수 있는 폼의 사용을 보여 줍니다.  
  
```  
<FORM id="frmRender" action="http://server/reportserver?/SampleReports/  
   Territory Sales Drilldown" method="post" target="_self">  
   <INPUT type="hidden" name="rs:Command" value="Render">   
   <INPUT type="hidden" name="rc:LinkTarget" value="main">  
   <INPUT type="hidden" name="rs:Format" value="HTML4.0">  
   <INPUT type="submit" value="Button">  
</FORM>  
```  
  
 위의 예에서 사용자가 폼에 있는 단추를 클릭하면 보고서 서버가 현재 프레임에서 대상으로 지정된 HTML 렌더링 보고서를 반환합니다. 비슷한 URL 액세스 문자열은 다음과 같습니다.  
  
```  
http://server/reportserver?/SampleReports/Territory Sales   
Drilldown&rs:Command=Render&rc:LinkTarget=main&rs:Format=HTML4.0  
```  
  
## <a name="see-also"></a>관련 항목:  
 [응용 프로그램에 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-into-applications.md)   
 [URL 액세스를 사용 하 여 Reporting Services 통합](../../reporting-services/application-integration/integrating-reporting-services-using-url-access.md)   
 [URL 액세스를 사용 하 여 Windows 응용 프로그램](../../reporting-services/application-integration/integrating-reporting-services-using-url-access-windows-application.md)   
 [URL 액세스 &#40; Ssrs&#41;](../../reporting-services/url-access-ssrs.md)  
  
  