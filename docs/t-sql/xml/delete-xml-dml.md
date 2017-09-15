---
title: delete (XML DML) | Microsoft Docs
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- XML DML [SQL Server]
- delete keyword
- delete statement [XML DML]
- deleting nodes
ms.assetid: b22c93a4-b84d-4356-af4c-6013322a4b71
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 57959308668cc5ea0455f6a4135c00482dbca15e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="delete-xml-dml"></a>delete(XML DML)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  XML 인스턴스에서 노드를 삭제합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
delete Expression  
```  
  
## <a name="arguments"></a>인수  
 *식*  
 삭제할 노드를 식별하는 XQuery 식입니다. 식에서 선택한 모든 노드 및 선택한 노드에 포함된 모든 노드와 값이 삭제됩니다. 에 설명 된 대로 [insert (XML DML)](../../t-sql/xml/insert-xml-dml.md),이 문서에 있는 기존 노드에 대 한 참조 여야 합니다. 생성된 노드여서는 안 됩니다. 식은 루트(/) 노드일 수 없습니다. 식이 빈 시퀀스를 반환할 경우 아무것도 삭제되지 않으며 오류가 반환되지 않습니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-deleting-nodes-from-a-document-stored-in-an-untyped-xml-variable"></a>1. 형식화되지 않은 xml 변수에 저장된 문서에서 노드 삭제  
 다음 예에서는 문서에서 여러 노드를 삭제하는 방법을 보여 줍니다. 변수에 XML 인스턴스가 할당 되는 먼저 **xml** 유형입니다. 그런 다음 이후의 delete XML DML 문이 문서에서 여러 노드를 삭제합니다.  
  
```  
DECLARE @myDoc xml  
SET @myDoc = '<?Instructions for=TheWC.exe ?>   
<Root>  
 <!-- instructions for the 1st work center -->  
<Location LocationID="10"   
            LaborHours="1.1"  
            MachineHours=".2" >Some text 1  
<step>Manufacturing step 1 at this work center</step>  
<step>Manufacturing step 2 at this work center</step>  
</Location>  
</Root>'  
SELECT @myDoc  
  
-- delete an attribute  
SET @myDoc.modify('  
  delete /Root/Location/@MachineHours  
')  
SELECT @myDoc  
  
-- delete an element  
SET @myDoc.modify('  
  delete /Root/Location/step[2]  
')  
SELECT @myDoc  
  
-- delete text node (in <Location>  
SET @myDoc.modify('  
  delete /Root/Location/text()  
')  
SELECT @myDoc  
  
-- delete all processing instructions  
SET @myDoc.modify('  
  delete //processing-instruction()  
')  
SELECT @myDoc  
```  
  
### <a name="b-deleting-nodes-from-a-document-stored-in-an-untyped-xml-column"></a>2. 형식화되지 않은 xml 열에 저장된 문서에서 노드 삭제  
 다음 예제에서는 **삭제** 의 두 번째 자식 요소를 제거 하는 XML DML 문은 <`Features`> 열에 저장 된 문서에서 합니다.  
  
```  
CREATE TABLE T (i int, x xml)  
go  
INSERT INTO T VALUES(1,'<Root>  
<ProductDescription ProductID="1" ProductName="Road Bike">  
<Features>  
  <Warranty>1 year parts and labor</Warranty>  
  <Maintenance>3 year parts and labor extended maintenance is available</Maintenance>  
</Features>  
</ProductDescription>  
</Root>')  
go  
-- verify the contents before delete  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
-- delete the second feature  
UPDATE T  
SET x.modify('delete /Root/ProductDescription/Features/*[2]')  
-- verify the deletion  
SELECT x.query(' //ProductDescription/Features')  
FROM T  
```  
  
 이전 쿼리에서 다음을 유의하세요.  
  
-   [modify () 메서드 (xml 데이터 형식)](../../t-sql/xml/modify-method-xml-data-type.md) 지정 하는 데 사용 되는 **삭제** XML DML 키워드입니다.  
  
-   [query () 메서드 (xml 데이터 형식)](../../t-sql/xml/query-method-xml-data-type.md) 문서를 쿼리 하는 데 사용 됩니다.  
  
### <a name="c-deleting-nodes-from-a-typed-xml-column"></a>3. 형식화된 xml 열에서 노드 삭제  
 이 예에서는 XML 문서에 저장 된 제조 지침에서 노드 삭제 형식화 된 **xml** 열입니다.  
  
 예제에서는 먼저 형식화 된 테이블 (T)을 만들 **xml** AdventureWorks 데이터베이스의 열입니다. 그런 다음 ProductModel 테이블의 Instructions 열에 있는 제조 지침 XML 인스턴스를 T 테이블로 복사하고 문서에서 하나 이상의 노드를 삭제합니다.  
  
```  
use AdventureWorks  
go  
drop table T  
go  
create table T(ProductModelID int primary key,   
Instructions xml (Production.ManuInstructionsSchemaCollection))  
go  
insert  T   
select ProductModelID, Instructions  
from Production.ProductModel  
where ProductModelID=7  
go  
select Instructions  
from T  
--1) insert <Location 1000/>. Note: <Root> must be singleton in the query  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  insert <MI:Location LocationID="1000"  LaborHours="1000" >  
           These are manu steps at location 1000.   
           <MI:step>New step1 instructions</MI:step>  
           Instructions for step 2 are here  
           <MI:step>New step 2 instructions</MI:step>  
         </MI:Location>  
  as first  
  into   (/MI:root)[1]  
')  
go  
select Instructions  
from T  
  
-- delete an attribute  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/@LaborHours)   
')  
go  
select Instructions  
from T  
-- delete text in <location>  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/text())   
')  
go  
select Instructions  
from T  
-- delete 2nd manu step at location 1000  
update T  
set Instructions.modify('  
  declare namespace MI="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions";  
  delete(/MI:root/MI:Location[@LocationID=1000]/MI:step[2])   
')  
go  
select Instructions  
from T  
-- cleanup  
drop table T  
go  
```  
  
## <a name="see-also"></a>관련 항목:  
 [형식화된 XML과 형식화되지 않은 XML 비교](../../relational-databases/xml/compare-typed-xml-to-untyped-xml.md)   
 [XML 데이터 인스턴스 만들기](../../relational-databases/xml/create-instances-of-xml-data.md)   
 [xml 데이터 형식 메서드](../../t-sql/xml/xml-data-type-methods.md)   
 [XML 데이터 수정 언어 &#40; XML DML &#41;](../../t-sql/xml/xml-data-modification-language-xml-dml.md)  
  
  
