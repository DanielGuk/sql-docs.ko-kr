---
title: '스키마 요소를 제외 하 고 사용 하 여 결과 XML 문서 sql에서: mapped (SQLXML 4.0) | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- element does not map [SQLXML]
- annotated XSD schemas, excluding schema elements
- mapped annotation
- table mapping [SQLXML], excluding schema elements
- sql:mapped
- excluding schema elements
- element mapping [SQLXML], excluding schema elements
- column mapping [SQLXML]
- XSD schemas [SQLXML], excluding schema elements
- attribute mapping [SQLXML], excluding schema elements
- table/view mapping [SQLXML], excluding schema elements
ms.assetid: 7d2649dd-0038-4a2c-b16d-f80f7c306966
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 96afa13033fee6a2767fc1ad3f6b6761c4a8247f
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48222319"
---
# <a name="excluding-schema-elements-from-the-resulting-xml-document-using-sqlmapped-sqlxml-40"></a>sql:mapped를 사용하여 결과 XML 문서에서 스키마 요소 제외(SQLXML 4.0)
  기본 매핑 때문에 XSD 스키마의 모든 요소와 특성은 데이터베이스 테이블/뷰 및 열에 매핑됩니다. 그러나 어느 데이터베이스 테이블(뷰) 또는 열에도 매핑되지 않고 XML에 표시되지 않는 요소를 XSD 스키마에 만들려면 `sql:mapped` 주석을 지정할 수 있습니다.  
  
 `sql:mapped` 주석은 스키마를 수정할 수 없는 경우 또는 스키마가 데이터베이스에 저장되어 있지 않은 데이터를 포함하지만 다른 원본에서 XML의 유효성을 검사하는 데 사용되는 경우에 특히 유용합니다. `sql:mapped` 주석은 매핑되지 않은 요소 및 특성이 XML 문서에서 나타나지 않는다는 점에서 `sql:is-constant`와는 다릅니다.  
  
 `sql:mapped` 주석은 부울 값(0=false, 1=true)을 사용합니다. 허용되는 값은 0, 1, true 및 false입니다.  
  
## <a name="examples"></a>예  
 다음 예를 사용하여 작업 예제를 만들려면 특정 요구 사항이 충족되어야 합니다. 자세한 내용은 [SQLXML 예 실행에 대 한 요구 사항](../sqlxml/requirements-for-running-sqlxml-examples.md)합니다.  
  
### <a name="a-specifying-the-sqlmapped-annotation"></a>1. sql:mapped 주석 지정  
 다른 원본의 XSD 스키마가 있고, 이 XSD 스키마 구성를  **\<Person.Contact >** 사용 하 여 요소 **ContactID**를 **FirstName**를 **LastName**, 및 **HomeAddress** 특성입니다.  
  
 이 XSD 스키마는 AdventureWorks 데이터베이스의 Person.Contact 테이블에 매핑할 `sql:mapped` 에 지정 되어 합니다 **HomeAddress** Employees 테이블에 직원의 자택 주소가 저장 하지 않으므로 특성입니다. 따라서 매핑 스키마에 대해 XPath 쿼리를 지정할 경우 이 특성은 데이터베이스에 매핑되지 않으며 결과 XML 문서에 반환되지 않습니다.  
  
 스키마의 나머지 부분에 대해서는 기본 매핑이 수행됩니다. 합니다  **\<Person.Contact >** 요소는 Person.Contact 테이블에 매핑되고 모든 특성은 Person.Contact 테이블에서 동일한 이름 가진 열에 매핑됩니다.  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Person.Contact">  
    <xsd:complexType>  
      <xsd:attribute name="ContactID"   type="xsd:string"/>  
      <xsd:attribute name="FirstName"    type="xsd:string" />  
      <xsd:attribute name="LastName"     type="xsd:string" />  
      <xsd:attribute name="HomeAddress" type="xsd:string"   
                     sql:mapped="false" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
##### <a name="to-test-a-sample-xpath-query-against-the-schema"></a>스키마에 대해 예제 XPath 쿼리를 테스트하려면  
  
1.  위 스키마 코드를 복사한 후 텍스트 파일에 붙여넣습니다. 파일을 sql-mapped.xml로 저장합니다.  
  
2.  다음 템플릿을 복사한 후 텍스트 파일에 붙여넣습니다. 파일을 sql-mapped.xml을 저장한 디렉터리와 같은 디렉터리에 sql-mappedT.xml로 저장합니다.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="sql-mapped.xml">  
            /Person.Contact[@ContactID < 10]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     매핑 스키마(MySchema.xml)에 대해 지정된 디렉터리 경로는 템플릿이 저장된 디렉터리에 상대적입니다. 또한 다음과 같이 절대 경로를 지정할 수 있습니다.  
  
    ```  
    mapping-schema="C:\MyDir\sql-mapped.xml"  
    ```  
  
3.  SQLXML 4.0 테스트 스크립트(Sqlxml4test.vbs)를 만든 다음 이 스크립트를 사용하여 템플릿을 실행합니다.  
  
     자세한 내용은 [실행 SQLXML 쿼리에 ADO를 사용 하 여](../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)입니다.  
  
 결과 집합은 다음과 같습니다.  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Person.Contact ContactID="1" FirstName="Gustavo" LastName="Achong" />   
  <Person.Contact ContactID="2" FirstName="Catherine" LastName="Abel" />   
  <Person.Contact ContactID="3" FirstName="Kim" LastName="Abercrombie" />   
  <Person.Contact ContactID="4" FirstName="Humberto" LastName="Acevedo" />   
  <Person.Contact ContactID="5" FirstName="Pilar" LastName="Ackerman" />   
  <Person.Contact ContactID="6" FirstName="Frances" LastName="Adams" />   
  <Person.Contact ContactID="7" FirstName="Margaret" LastName="Smith" />   
  <Person.Contact ContactID="8" FirstName="Carla" LastName="Adams" />   
  <Person.Contact ContactID="9" FirstName="Jay" LastName="Adams" />   
</ROOT>  
```  
  
 매핑 스키마에서 `sql:mapped` 특성에 대해 0을 지정했기 때문에 ContactID, FirstName 및 LastName은 있지만 HomeAddress는 없습니다.  
  
## <a name="see-also"></a>관련 항목  
 [기본 매핑의 XSD 요소 및 특성 테이블 및 열을 &#40;SQLXML 4.0&#41;](default-mapping-of-xsd-elements-and-attributes-to-tables-and-columns-sqlxml-4-0.md)  
  
  
