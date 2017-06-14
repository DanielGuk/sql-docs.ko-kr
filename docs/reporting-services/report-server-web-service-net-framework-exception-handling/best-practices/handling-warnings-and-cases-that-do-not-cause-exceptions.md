---
title: "경고 및 예외를 발생 하는 사례를 처리 | Microsoft Docs"
ms.custom: 
ms.date: 03/06/2017
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
- exceptions [Reporting Services], warnings that don't cause
- warnings [Reporting Services]
ms.assetid: 475c0713-6265-44e7-9ebc-ebdd1b89e0af
caps.latest.revision: 30
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: f04bc59af4ff5bc1a761ae2e76101d4c601e49c9
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="handling-warnings-and-cases-that-do-not-cause-exceptions"></a>예외를 발생하지 않는 경고 및 사례 처리
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 경고 및 특정 오류에 대해 예외를 throw하지 않습니다. 예를 들어 <xref:ReportService2010.ReportingService2010.CreateCatalogItem%2A> 메서드를 사용하여 새 보고서를 보고서 서버에 게시하는 경우 발생하는 경고는 <xref:ReportService2010.Warning> 개체의 배열의 형태로 반환됩니다. 이러한 경고는 적절한 조치를 취할 수 있도록 처리되고 표시되어야 합니다.  
  
```vb  
Try  
   rs.CreateCatalogItem(name, parentFolder, False, definition, Nothing, warnings)  
  
   If Not (warnings.Length = 0) Then  
      Dim warning As Warning  
      For Each warning In warnings  
         Console.WriteLine(warning.Message)  
      Next warning  
   Else  
      Console.WriteLine("Report {0} created successfully with no warnings", name)  
   End If  
  
Catch ex As SoapException  
   Console.WriteLine(ex.Detail("Message").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.CreateCatalogItem("Report", name, parentFolder, false, definition, null, out warnings);  
  
   if (warnings.Length != 0)  
   {  
      foreach (Warning warning in warnings)  
      {  
         Console.WriteLine(warning.Message);  
      }  
   }  
   else  
      Console.WriteLine("Report {0} created successfully with no warnings", name);  
}  
  
catch (SoapException ex)  
{  
   Console.WriteLine(ex.Detail["Message"].InnerXml);  
}  
```  
  
 오류를 처리하는 또 하나의 방법은 특정 메서드의 반환 값을 평가하는 것입니다. 예를 들어 <xref:ReportService2010.ReportingService2010.FindItems%2A> 메서드를 사용하여 보고서 서버 데이터베이스의 특정 항목을 검색할 수 있습니다. 검색 조건과 일치하는 항목을 찾지 못할 경우 <xref:ReportService2010.CatalogItem> 개체의 null 배열이 반환됩니다. 배열을 평가 하 고를 확인 해야 **null**, 및 발견 된 항목이 없는 경우 알려 줍니다.  
  
## <a name="see-also"></a>관련 항목:  
 <xref:ReportService2010.CatalogItem>   
 [Reporting Services의 예외 처리 소개](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException 클래스](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  