---
title: Reporting Services의 예외 처리 소개 | Microsoft Docs
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-server-web-service-net-framework-exception-handling
ms.topic: reference
helpviewer_keywords:
- Web service [Reporting Services], exception handling
- errors [Reporting Services]
- exceptions [Reporting Services]
- Report Server Web service, exception handling
- XML Web service [Reporting Services], exception handling
ms.assetid: 54381870-ce67-482b-aa83-6a838cdbf9b9
author: markingmyname
ms.author: maghan
ms.openlocfilehash: c176b969e8841bf2ae9b560ae27663790d28af48
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47724921"
---
# <a name="introducing-exception-handling-in-reporting-services"></a>Reporting Services의 예외 처리 소개
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 응용 프로그램이 보고서 서버 웹 서비스에서 처리할 수 없는 요청을 보낼 경우 이 서비스는 SOAP 예외를 클라이언트에 반환합니다. 보고서 서버 웹 서비스에서 throw된 예외에 대한 처리는 개발하는 응용 프로그램에서 중요한 부분입니다. 이러한 처리를 통해 오류 발생 시 사용자에게 유용한 정보를 반환할 수 있기 때문입니다.  
  
 이 섹션에는 예외 처리, 유효하지 않은 사용자 입력 방지, 사용자에게 의미 있는 오류 정보 반환 등에 대한 정보가 포함되어 있습니다. 예외 처리에 대한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK 설명서의 "Handling and Throwing Exceptions(예외 처리 및 Throw)"를 참조하세요.  
  
## <a name="in-this-section"></a>섹션 내용  
  
|항목|설명|  
|-----------|-----------------|  
|[Reporting Services의 예외 처리](../../reporting-services/report-server-web-service-net-framework-exception-handling/handling-exceptions-in-reporting-services.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서의 예외에 대해 개략적으로 설명하고 웹 서비스 반환 오류에서 SOAP의 역할에 대해 설명합니다.|  
|[Reporting Services 예외 처리에 관한 모범 사례](../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/best-practices-for-reporting-services-exception-handling.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서 예외를 처리하는 방법에 대한 권장 사항을 제공합니다.|  
|[Reporting Services SoapException 클래스](../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]의 **SoapException** 클래스에 대해 설명합니다.|  
  
## <a name="see-also"></a>참고 항목  
 [웹 서비스 및 .NET Framework를 사용하여 응용 프로그램 빌드](../../reporting-services/report-server-web-service/net-framework/building-applications-using-the-web-service-and-the-net-framework.md)  
  
  
