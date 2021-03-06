---
title: 잘못된 요청 방지 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- invalid requests [Reporting Services]
- exceptions [Reporting Services], invalid requests
- valid requests [Reporting Services]
ms.assetid: 4a4a2d97-4c10-43a9-8298-ef5a820ea549
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d165b4137c8deb0afb232d58f0e19bb183ddf860
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098753"
---
# <a name="preventing-invalid-requests"></a>잘못된 요청 방지
  응용 프로그램 흐름을 분석하고 보고서 서버로 전송되는 요청이 유효한지 확인하여 일부 유형의 예외가 throw되지 않도록 할 수 있습니다. 예를 들어 사용자가 보고서의 이름, 데이터 원본 또는 기타 보고서 서버 항목을 추가하거나 갱신할 수 있는 응용 프로그램의 경우 사용자가 입력하는 텍스트의 유효성을 검사해야 합니다. 또한 요청을 보고서 서버로 보내기 전에 항상 예약 문자를 확인해야 합니다. 코드에서 **if**문 또는 기타 논리 구문을 사용하여 보고서 서버에 요청을 보내는 데 필요한 조건이 충족되지 않았음을 사용자에게 알립니다.  
  
 다음의 간단한 C# 예에서는 사용자가 이름에 슬래시(/) 문자가 포함된 보고서를 만들려고 시도할 때 오류 메시지를 표시합니다.  
  
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
         "see the help documentation";  
  
      MessageBox.Show(message, "Invalid Input Error");  
   }  
   else // Publish the report  
   {  
      Byte[] definition = null;  
      Warning[] warnings = {};  
      string name = nameTextBox.Text;  
  
      FileStream stream = File.OpenRead("MyReport.rdl");  
      definition = new Byte[stream.Length];  
      stream.Read(definition, 0, (int) stream.Length);  
      stream.Close();  
      // Create report with user-defined name  
      rs.CreateCatalogItem("Report", name, "/Samples", false, definition, null, out warnings);  
      MessageBox.Show("Report: {0} created successfully", name);  
   }  
}  
```  
  
 요청이 보고서 서버로 전송되기 전에 방지할 수 있는 오류 유형에 대한 자세한 내용은 [SoapException 오류 테이블](../soapexception-class/soapexception-errors-table.md)을 참조하세요. try/catch 블록을 사용하여 위의 예를 개선하는 방법은 [Try 및 Catch 블록 사용](using-try-and-catch-blocks.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Reporting Services의 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException 클래스](../soapexception-class/reporting-services-soapexception-class.md)  
  
  
