---
title: "사용 하 여 시도 하 고 Catch 블록 | Microsoft Docs"
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
- exceptions [Reporting Services], try/catch blocks
- try/catch blocks [Reporting Services]
ms.assetid: a7a9ef53-e3b6-4bf7-81f3-d85615954e6f
caps.latest.revision: 29
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 659707603a24ff8d59bfc1b001d80e8184c119e1
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="using-try-and-catch-blocks"></a>Try 및 Catch 블록을 사용 하 여
  조건문을 코드에 추가하여 보고서 서버에 대한 잘못된 요청을 제한한 후에는 try/catch 블록을 사용하여 적절한 예외 처리를 제공해야 합니다. 이를 통해 유효하지 않은 요청에 대한 또 하나의 보호막을 만들 수 있습니다. 보고서 서버에 대한 요청이 try 블록 안에 포함되어 있으며 이 요청으로 인해 보고서 서버에서 예외가 throw되는 경우 이 예외는 catch 블록에서 catch되므로 응용 프로그램이 갑자기 종료되는 것을 막을 수 있습니다. 예외가 catch되면 예외를 사용하여 사용자에게 다른 작업을 수행하도록 지시하거나 오류가 발생했음을 친숙한 방법으로 알려줄 수 있습니다. 그런 다음 finally 블록을 사용하여 리소스를 정리할 수 있습니다. 일반적인 예외 처리 계획을 생성하여 불필요한 try/catch 블록 중복을 피하는 것이 가장 이상적입니다.  
  
 다음 예에서는 try/catch 블록을 사용하여 예외 처리 코드의 안정성을 향상시킵니다.  
  
```  
// C#  
private void PublishReport()  
{  
   int index;  
   string reservedChar;  
   string message;  
  
   // Check the text value of the name text box for "/",  
   // a reserved character  
   index = nameTextBox.Text.IndexOf(@"/");  
  
   if ( index != -1) // The text contains the character  
   {  
      reservedChar = nameTextBox.Text.Substring(index, 1);  
      // Build a user-friendly error message  
      message = "The name of the report cannot contain the reserved character " +  
         "\"" + reservedChar + "\". " +  
         "Please enter a valid name for the report. " +  
         "For more information about reserved characters, " +  
         "consult the online documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      try  
      {  
         FileStream stream = File.OpenRead("MyReport.rdl");  
         definition = new Byte[stream.Length];  
         stream.Read(definition, 0, (int) stream.Length);  
         stream.Close();  
         // Create report with user-defined name  
         rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
         MessageBox.Show("Report: {0} created successfully", name);  
      }  
  
      // Catch expected exceptions beginning with the most specific,  
      // moving to the least specific  
      catch(IOException ex)  
      {  
         MessageBox.Show(ex.Message, "File IO Exception");  
      }  
  
      catch (SoapException ex)  
      {  
         // The exception is a SOAP exception, so use  
         // the Detail property's Message element.  
         MessageBox.Show(ex.Detail["Message"].InnerXml, "SOAP Exception");   
      }  
  
      catch (Exception ex)  
      {  
         MessageBox.Show(ex.Message, "General Exception");  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>관련 항목:  
 [Reporting Services의 예외 처리 소개](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException 클래스](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  