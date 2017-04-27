---
title: "XML 보고서 데이터를 위한 XML 쿼리 구문(SSRS) | Microsoft Docs"
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
  - "네임스페이스 [Reporting Services]"
  - "데이터 처리 확장 프로그램 [Reporting Services], 데이터 원본"
  - "xmldp [Reporting Services]"
  - "XML [Reporting Services], 데이터 검색"
ms.assetid: d203886f-faa1-4a02-88f5-dd4c217181ef
caps.latest.revision: 49
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 49
---
# XML 보고서 데이터를 위한 XML 쿼리 구문(SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]에서는 XML 데이터 원본에 대한 데이터 집합을 만들 수 있습니다. 데이터 원본을 정의한 후 데이터 집합에 대한 쿼리를 만듭니다. 데이터 원본이 가리키는 XML 데이터의 형식에 따라 XML **Query** 나 요소 경로를 포함하여 데이터 집합 쿼리를 만듭니다. XML **쿼리**는 **\<Query>** 태그로 시작하며 데이터 원본에 따라 달라지는 네임스페이스와 XML 요소를 포함합니다. 요소 경로는 네임스페이스로부터 독립적이며 기본 XML 데이터에서 사용할 노드 및 노드 특성을 XPath 형식 구문으로 지정합니다. 요소 경로에 대한 자세한 내용은 [XML 보고서 데이터를 위한 요소 경로 구문&#40;SSRS&#41;](../../reporting-services/report-data/element-path-syntax-for-xml-report-data-ssrs.md)을 참조하세요.  
  
 다음과 같은 형식의 XML 데이터에 대한 XML 데이터 원본을 만들 수 있습니다.  
  
-   http 프로토콜을 사용하는 URL이 가리키는 XML 문서  
  
-   XML 데이터를 반환하는 웹 서비스 끝점  
  
-   포함 XML 데이터  
  
 XML **Query** 나 요소 경로를 지정하는 방법은 XML 데이터 형식에 따라 달라집니다.  
  
 XML 문서의 경우 XML **Query** 는 선택 사항입니다. 이 쿼리가 포함되어 있지 않으면 선택적 XML **ElementPath**를 포함할 수 있습니다. XML **ElementPath** 값에는 요소 경로 구문이 사용됩니다. 데이터 원본의 XML 데이터에 필요한 경우 XML **Query** 및 XML **ElementPath** 를 포함하여 네임스페이스를 올바르게 처리할 수 있습니다.  
  
 연결 문자열 URL이 가리키는 웹 서비스 끝점의 경우 XML **Query** 는 웹 서비스 메서드나 SOAP 동작 또는 둘 모두를 정의합니다. XML 데이터 공급자는 보고서에 사용할 XML 데이터를 검색하는 웹 서비스 요청을 만듭니다.  
  
> [!NOTE]  
>  웹 서비스 네임스페이스에 슬래시(**/)** 문자가 포함되어 있으면 XML 데이터 처리 확장 프로그램에서 해당 네임스페이스를 올바르게 가져올 수 있도록 웹 서비스 메서드와 SOAP 동작을 모두 포함하세요.  
  
 포함 XML 문서의 경우 XML **Query** 는 사용할 포함 XML 데이터를 정의하고 선택적 네임스페이스와 선택적 XML **ElementPath**를 포함합니다.  
  
## XML 데이터의 쿼리 매개 변수 지정  
 XML 문서의 쿼리 매개 변수를 지정할 수 있습니다.  
  
-   URL 요청의 경우 쿼리 매개 변수는 표준 URL 매개 변수로 포함됩니다.  
  
-   웹 서비스 요청의 경우 쿼리 매개 변수는 웹 서비스 메서드에 전달됩니다. 쿼리 매개 변수를 정의하려면 **데이터 집합 속성** 대화 상자의 **매개 변수** 페이지를 사용합니다. 자세한 내용은 [데이터 집합 속성 대화 상자, 매개 변수](../../reporting-services/report-data/dataset-properties-dialog-box-parameters.md)를 참조하세요.  
  
### 예제  
 다음 표의 예에서는 보고서 서버 웹 서비스, XML 문서 및 포함 XML 데이터에서 데이터를 검색하는 방법을 보여 줍니다.  
  
|XML 데이터 원본|쿼리 예|  
|---------------------|-------------------|  
|웹 서비스 XML 데이터(<xref:ReportService2010.ReportingService2010.ListChildren%2A> 메서드 사용)|`<Query>`<br /><br /> `<Method Name="ListChildren" Namespace="http://schemas.microsoft.com/sqlserver/2005/06/30/reporting/reportingservices" />`<br /><br /> `</Query>`|  
|웹 서비스 XML 데이터(SoapAction 사용)|`<Query xmlns=namespace>`<br /><br /> `<SoapAction>http://schemas/microsoft.com/sqlserver/2005/03/23/reporting/reportingservices/ListChildren</SoapAction>`<br /><br /> `</Query>`|  
|네임스페이스를 사용하는 XML 문서 또는 포함 XML 데이터<br /><br /> 요소 경로의 네임스페이스를 지정하는 쿼리 요소|`<Query xmlns:es="http://schemas.microsoft.com/StandardSchemas/ExtendedSales">`<br /><br /> `<ElementPath>/Customers/Customer/Orders/Order/es:LineItems/es:LineItem</ElementPath>`<br /><br /> `</Query>`|  
|포함 XML 문서|`<Query>`<br /><br /> `<XmlData>`<br /><br /> `<Customers>`<br /><br /> `<Customer ID="1">Bobby</Customer>`<br /><br /> `</Customers>`<br /><br /> `</XmlData>`<br /><br /> `<ElementPath>Customer {@}</ElementPath>`<br /><br /> `</Query>`|  
|기본값을 사용하는 XML 문서|*No query*입니다.<br /><br /> 요소 경로는 XML 문서 자체에서 파생되며 네임스페이스로부터 독립적입니다.|  
  
> [!NOTE]  
>  첫 번째 웹 서비스 예에서는 <xref:ReportService2006.ReportingService2006.ListChildren%2A> 메서드를 사용하는 보고서 서버의 내용을 나열합니다. 이 쿼리를 실행하려면 새 데이터 원본을 만들고 연결 문자열을 http://localhost/reportserver/reportservice2006.asmx로 설정해야 합니다. <xref:ReportService2006.ReportingService2006.ListChildren%2A> 메서드는 두 개의 매개 변수(**Item** 및 **Recursive**)를 사용합니다. **Item**의 기본값을 **/**로, **Recursive**의 기본값을 **1**로 설정합니다.  
  
## 네임스페이스 지정  
 XML **Query** 요소를 사용하여 데이터 원본의 XML 데이터에 사용된 네임스페이스를 지정할 수 있습니다. 다음 XML 쿼리에서는 **sales**네임스페이스를 사용합니다. `sales:LineItems` 및 `sales:LineItem`의 XML **ElementPath** 노드는 **sales** 네임스페이스를 사용합니다.  
  
```  
<Query xmlns:sales=  
"http://schemas.microsoft.com/StandardSchemas/ExtendedSales">  
   <SoapAction>  
      http://schemas.microsoft.com/SalesWebService/ListOrders   
   </SoapAction>  
   <ElementPath>  
      Customers/Customer/Orders/Order/sales:LineItems/sales:LineItem  
   </ElementPath>  
</Query>  
```  
  
 기본 네임스페이스가 빈 상태로 유지되도록 데이터 공급자 네임스페이스를 지정하려면 **xmldp**를 사용합니다. 이는 다음 예에서 확인할 수 있습니다.  
  
### 예제  
 다음 예에서는 XML 문서 DPNamespace.xml을 사용하며 이 문서는 표 아래에 제공되어 있습니다. 이 표에서는 네임스페이스 접두사가 포함된 XML ElementPath 구문의 두 가지 예를 보여 줍니다.  
  
|XML 쿼리 요소|데이터 집합의 결과 필드|  
|-----------------------|-------------------------------------|  
|\<Query/>|값 A: http://schemas.microsoft.com/...<br /><br /> 값 B: http://schemas.microsoft.com/...<br /><br /> 값 C: http://schemas.microsoft.com/...|  
|`<xmldp:Query xmlns:xmldp="http://schemas.microsoft.com/sqlserver/2005/02/reporting/XmlDPQuery" xmlns:ns="http://schemas.microsoft.com/...">`<br /><br /> `<xmldp:ElementPath>Root {}/ns:Element2/Node</xmldp:ElementPath>`<br /><br /> `</xmldp:Query>`|Value D<br /><br /> Value E<br /><br /> Value F|  
  
#### XML 문서: DPNamespace.xml  
 이 XML을 복사한 후 보고서 디자이너에서 XML 데이터 원본으로 사용할 수 있는 URL(예: http://localhost/DPNamespace.xml)에 저장할 수 있습니다.  
  
```  
<Root xmlns:ns="http://schemas.microsoft.com/...">  
   <ns:Element1>  
      <Node>Value A</Node>  
      <Node>Value B</Node>  
      <Node>Value C</Node>  
   </ns:Element1>  
   <ns:Element2>  
      <Node>Value D</Node>  
      <Node>Value E</Node>  
      <Node>Value F</Node>  
   </ns:Element2>  
</Root>  
```  
  
## 관련 항목:  
 [XML 연결 형식&#40;SSRS&#41;](../../reporting-services/report-data/xml-connection-type-ssrs.md)   
 [Reporting Services&#40;SSRS&#41; 자습서](../../reporting-services/reporting-services-tutorials-ssrs.md)  
  
  