---
title: 중첩 FOR XML 쿼리 사용 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- FOR XML clause, nested FOR XML queries
- queries [XML in SQL Server], nested FOR XML
- nested FOR XML queries
ms.assetid: 7604161a-a958-446d-b102-7dee432979d0
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: a804585f215b7328890d2f0400c77307af7b1b4b
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211143"
---
# <a name="use-nested-for-xml-queries"></a>중첩 FOR XML 쿼리 사용
  합니다 `xml` 데이터 형식 및 [FOR XML 쿼리의 TYPE 지시어](type-directive-in-for-xml-queries.md) 클라이언트와 서버에서 처리할 FOR XML 쿼리에 의해 반환 된 XML을 사용 하도록 설정 합니다.  
  
## <a name="processing-with-xml-type-variables"></a>xml 유형 변수를 사용하여 처리  
 FOR XML 쿼리 결과를 `xml` 유형의 변수에 할당하거나 XQuery를 사용하여 결과를 쿼리하고 추가 처리를 위해 이 결과를 `xml` 유형의 변수에 할당할 수 있습니다.  
  
```  
DECLARE @x xml  
SET @x=(SELECT ProductModelID, Name  
        FROM Production.ProductModel  
        WHERE ProductModelID=122 or ProductModelID=119  
        FOR XML RAW, TYPE)  
SELECT @x  
-- Result  
--<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
--<row ProductModelID="119" Name="Bike Wash" />  
```  
  
 또한 변수, 반환 된 XML을 처리할 수 있습니다 `@x`, 중 하나를 사용 하 여는 `xml` 데이터 형식 메서드. 예를 들어 `ProductModelID` value() 메서드 [를 사용하여](/sql/t-sql/xml/value-method-xml-data-type)특성 값을 검색할 수 있습니다.  
  
```  
DECLARE @i int;  
SET @i = (SELECT @x.value('/row[1]/@ProductModelID[1]', 'int'));  
SELECT @i;  
```  
  
 다음 예에서 `FOR XML` 지시어가 `TYPE` 절에 지정되어 있기 때문에 `FOR XML` 쿼리 결과는 `xml` 유형으로 반환됩니다.  
  
```  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=119 or ProductModelID=122  
FOR XML RAW, TYPE,ROOT('myRoot');  
  
```  
  
 다음은 결과입니다.  
  
```  
<myRoot>  
  <row ProductModelID="122" Name="All-Purpose Bike Stand" />  
  <row ProductModelID="119" Name="Bike Wash" />  
</myRoot>  
```  
  
 결과의 길이가 `xml` 형식을 지정할 수 있습니다 중 하나는 `xml` 다음 쿼리에서와에서 같이 데이터 형식에이 XML에 대해 직접 메서드. 쿼리에서는 [query() 메서드(xml 데이터 형식)](/sql/t-sql/xml/query-method-xml-data-type)를 사용하여 <`row`> 요소의 첫 번째 <`myRoot`> 요소 자식을 검색합니다.  
  
```  
SELECT  (SELECT ProductModelID, Name  
         FROM Production.ProductModel  
         WHERE ProductModelID=119 or ProductModelID=122  
         FOR XML RAW, TYPE,ROOT('myRoot')).query('/myRoot[1]/row[1]');  
  
```  
  
 다음은 결과입니다.  
  
```  
<row ProductModelID="122" Name="All-Purpose Bike Stand" />  
```  
  
## <a name="returning-inner-for-xml-query-results-to-outer-queries-as-xml-type-instances"></a>내부 FOR XML 쿼리 결과를 외부 쿼리에 xml 유형 인스턴스로 반환  
 중첩 된 작성할 수 있습니다 `FOR XML` 으로 내부 쿼리 결과가 반환 됩니다 여기서 쿼리는 `xml` 외부 쿼리할 형식입니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
```  
SELECT Col1,   
       Col2,   
       ( SELECT Col3, Col4   
        FROM  T2  
        WHERE T2.Col = T1.Col  
        ...  
        FOR XML AUTO, TYPE )  
FROM T1  
WHERE ...  
FOR XML AUTO, TYPE;  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   내부 `FOR XML` 쿼리에서 생성된 XML이 외부 `FOR XML`에서 생성된 XML에 추가됩니다.  
  
-   내부 쿼리는 `TYPE` 지시어를 지정합니다. 따라서 내부 쿼리에서 반환된 XML 데이터는 `xml` 유형입니다. TYPE 지시어를 지정하지 않으면 내부 `FOR XML` 쿼리의 결과가 `nvarchar(max)`로 반환되고 XML 데이터가 올바르게 수정됩니다.  
  
## <a name="controlling-the-shape-of-resulting-xml-data"></a>결과 XML 데이터의 형식 제어  
 중첩 FOR XML 쿼리를 사용하면 결과 XML 데이터 형식을 보다 자유롭게 정의할 수 있습니다. 중첩 FOR XML 쿼리를 사용하여 일부는 특성 중심이고 일부는 요소 중심인 XML을 생성할 수 있습니다.  
  
 중첩 FOR XML 쿼리로 특성 중심 및 요소 중심 XML을 모두 지정하는 방법은 [FOR XML 쿼리와 중첩 FOR XML 쿼리 비교](../xml/for-xml-query-compared-to-nested-for-xml-query.md) 및 [중첩 FOR XML 쿼리로 XML 구체화](../xml/shape-xml-with-nested-for-xml-queries.md)를 참조하세요.  
  
 중첩된 AUTO 모드 FOR XML 쿼리를 지정하여 형제를 포함하는 XML 계층을 생성할 수 있습니다. 자세한 내용은 [중첩 AUTO 모드 쿼리를 사용하여 형제 생성](../xml/generate-siblings-with-a-nested-auto-mode-query.md)을 참조하세요.  
  
 사용하는 모드에 관계없이 중첩된 FOR XML 쿼리를 사용하면 결과 XML 형식을 보다 자유롭게 설명할 수 있습니다. EXPLICIT 모드 쿼리 대신 이러한 쿼리를 사용할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 항목에서는 중첩 FOR XML 쿼리의 예를 제공합니다.  
  
 [FOR XML 쿼리와 중첩 FOR XML 쿼리 비교](../xml/for-xml-query-compared-to-nested-for-xml-query.md)  
 단일 수준 FOR XML 쿼리를 중첩 FOR XML 쿼리와 비교합니다. 이 예에서는 특성 중심 및 요소 중심 XML 둘 모두를 쿼리 결과로 지정하는 방법을 보여 줍니다.  
  
 [중첩 AUTO 모드 쿼리를 사용하여 형제 생성](../xml/generate-siblings-with-a-nested-auto-mode-query.md)  
 중첩 AUTO 모드 쿼리를 사용하여 형제를 생성하는 방법을 보여 줍니다.  
  
 [ASP.NET에서 중첩 FOR XML 쿼리 사용](use-nested-for-xml-queries-in-asp-net.md)  
 ASPX 애플리케이션이 FOR XML을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 XML을 반환할 수 있는 방법을 보여 줍니다.  
  
 [중첩 FOR XML 쿼리로 XML 구체화](../xml/shape-xml-with-nested-for-xml-queries.md)  
 중첩 FOR XML 쿼리를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 만들어진 XML 문서의 구조를 제어하는 방법을 보여 줍니다.  
  
  
