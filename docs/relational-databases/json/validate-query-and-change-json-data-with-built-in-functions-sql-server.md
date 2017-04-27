---
title: "기본 제공 함수를 사용하여 JSON 데이터 유효성 검사, 쿼리, 변경(SQL Server) | Microsoft 문서"
ms.custom:
- SQL2016_New_Updated
ms.date: 06/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-json
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JSON, built-in functions
- functions (JSON)
ms.assetid: 6b6c7673-d818-4fa9-8708-b4ed79cb1b41
caps.latest.revision: 21
author: douglaslMS
ms.author: douglasl
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d9cdb66be3f6831ad5c2a61258c25425f98c0988
ms.lasthandoff: 04/11/2017

---
# <a name="validate-query-and-change-json-data-with-built-in-functions-sql-server"></a>기본 함수를 사용하여 JSON 데이터 유효성 검사, 쿼리, 변경(SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  JSON의 기본 지원에는 이 항목에서 설명하는 다음의 기본 제공 함수가 포함됩니다.  
  
-   [ISJSON](#ISJSON) 은 문자열에 유효한 JSON이 포함되어 있는지 여부를 테스트합니다.  
  
-   [JSON_VALUE](#VALUE) JSON 문자열에서 스칼라 값을 추출합니다.  
  
-   [JSON_QUERY](#QUERY) 는 JSON 문자열에서 개체 또는 배열을 추출합니다.  
  
-   [JSON_MODIFY](#MODIFY) 는 JSON 문자열의 속성 값을 업데이트하고 업데이트된 JSON 문자열을 반환합니다.  
 
## <a name="json-text-for-the-examples-on-this-page"></a>이 페이지의 예제에 대한 JSON 텍스트
이 페이지의 예제에서는 복잡한 요소가 포함된 다음 JSON 텍스트를 사용합니다.

```json  
DECLARE @jsonInfo NVARCHAR(MAX)

SET @jsonInfo=N'{  
     "info":{    
       "type":1,  
       "address":{    
         "town":"Bristol",  
         "county":"Avon",  
         "country":"England"  
       },  
       "tags":["Sport", "Water polo"]  
    },  
    "type":"Basic"  
 }' 
``` 

##  <a name="ISJSON"></a> ISJSON 함수를 사용하여 JSON 텍스트의 유효성을 검사합니다.  
 **ISJSON** 함수는 문자열에 유효한 JSON이 포함되어 있는지 여부를 테스트합니다.  
  
 다음 예는 열에 유효한 JSON이 포함된 경우 JSON을 반환합니다.  
  
```tsql  
SELECT id,json_col
FROM tab1
WHERE ISJSON(json_col)>0 
```  
  
 자세한 내용은 [ISJSON&#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)을 참조하세요.  
  
##  <a name="VALUE"></a> JSON_VALUE 함수를 사용하여 JSON 텍스트에서 값을 추출합니다.  
 **JSON_VALUE** 함수는 JSON 문자열에서 스칼라 값을 추출합니다.  
  
 다음 예제는 JSON 속성 값을 로컬 변수로 추출합니다.  
  
```tsql  
SET @town=JSON_VALUE(@jsonInfo,'$.info.address.town')  
```  
  
 자세한 내용은 [JSON_VALUE&#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)을 참조하세요.  
  
##  <a name="QUERY"></a> JSON_QUERY 함수를 사용하여 JSON 텍스트에서 개체 또는 배열 추출  
 **JSON_QUERY** 함수는 JSON 문자열에서 개체 또는 배열을 추출합니다.  
 
 다음 예제는 쿼리 결과에 JSON 조각을 반환하는 방법을 보여줍니다.  
  
```tsql  
SELECT FirstName,LastName,JSON_QUERY(jsonInfo,'$.info.address') AS Address
FROM Person.Person
ORDER BY LastName
```  
  
 자세한 내용은 [JSON_QUERY&#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)을 참조하세요.  
  
##  <a name="JSONCompare"></a> JSON_VALUE 및 JSON_QUERY 비교  
 **JSON_VALUE** 와 **JSON_QUERY** 간의 주요 차이점은 **JSON_VALUE** 는 스칼라 값을 반환하고 **JSON_QUERY** 는 개체 또는 배열을 반환한다는 점입니다.  
  
 다음 예제의 JSON 쿼리를 살펴보십시오.  
  
```json  
{
    "a": "[1,2]",
    "b": [1, 2],
    "c": "hi"
}  
```  
  
 이 예제 JSON 텍스트에서 데이터 멤버 "a"와 "c"는 문자열 값이며 데이터 멤버 "b"는 배열입니다. **JSON_VALUE** 및 **JSON_QUERY** 는 다음 결과를 반환합니다.  
  
|Query|**JSON_VALUE** 는 다음을 반환합니다.|**JSON_QUERY** 는 다음을 반환합니다.|  
|-----------|-----------------------------|-----------------------------|  
|**$**|NULL 또는 오류|`{ "a": "[1,2]", "b": [1,2], "c":"hi"}`|  
|**$.a**|[1,2]|NULL 또는 오류|  
|**$.b**|NULL 또는 오류|[1,2]|  
|**$.b[0]**|1|NULL 또는 오류|  
|**$.c**|hi|NULL 또는 오류|  
  
## <a name="test-jsonvalue-and-jsonquery-with-the-adventureworks-sample-database"></a>AdventureWorks 예제 데이터베이스로 JSON_VALUE 및 JSON_QUERY 테스트  
 JSON 데이터가 포함된 AdventureWorks 예제 데이터베이스로 다음 예제를 실행하여 이 항목에서 설명하는 기본 제공 함수를 테스트합니다. AdventureWorks 예제 데이터베이스를 가져오려면 [여기를 클릭](http://www.microsoft.com/en-us/download/details.aspx?id=49502)하십시오.  
  
 다음 예제에서 SalesOrder_json 테이블의 정보 예에는 JSON 텍스트가 포함되어 있습니다.  
  
### <a name="example-1---return-both-standard-columns-and-json-data"></a>예제 1 - 두 표준 열과 JSON 데이터 반환  
 다음 쿼리는 표준 관계형 열과 JSON 열의 값을 모두 반환합니다.  
  
```tsql  
SELECT SalesOrderNumber,OrderDate,Status,ShipDate,Status,AccountNumber,TotalDue,
 JSON_QUERY(Info,'$.ShippingInfo') ShippingInfo,
 JSON_QUERY(Info,'$.BillingInfo') BillingInfo,
 JSON_VALUE(Info,'$.SalesPerson.Name') SalesPerson,
 JSON_VALUE(Info,'$.ShippingInfo.City') City,
 JSON_VALUE(Info,'$.Customer.Name') Customer,
 JSON_QUERY(OrderItems,'$') OrderItems
FROM Sales.SalesOrder_json
WHERE ISJSON(Info)>0
```  
  
### <a name="example-2--aggregate-and-filter-json-values"></a>예제 2 - JSON 값 집계 및 필터링  
 다음 쿼리는 고객 이름(JSON에 저장)과 상태(일반 열에 저장)를 기준으로 소계를 집계합니다. 그런 다음 시(JSON에 저장) 및 OrderDate(일반 열에 저장)을 기준으로 결과를 필터링합니다.  
  
```tsql  
DECLARE @territoryid INT;
DECLARE @city NVARCHAR(32);

SET @territoryid=3;

SET @city=N'Seattle';

SELECT JSON_VALUE(Info,'$.Customer.Name') AS Customer,Status,SUM(SubTotal) AS Total
FROM Sales.SalesOrder_json
WHERE TerritoryID=@territoryid
 AND JSON_VALUE(Info,'$.ShippingInfo.City')=@city
 AND OrderDate>'1/1/2015'
GROUP BY JSON_VALUE(Info,'$.Customer.Name'),Status
HAVING SUM(SubTotal)>1000
```  
  
##  <a name="MODIFY"></a> JSON_MODIFY 함수를 사용하여 JSON 텍스트의 속성 값을 업데이트합니다.  
 **JSON_MODIFY**  함수는 JSON 문자열의 속성 값을 업데이트하고 업데이트된 JSON 문자열을 반환합니다.  
  
 다음 예제에서는 JSON이 포함된 변수에서 속성 값을 업데이트합니다.  
  
```tsql  
SET @info=JSON_MODIFY(@jsonInfo,"$.info.address[0].town",'London')    
```  
  
 자세한 내용은 [JSON_MODIFY&#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)을 참조하세요.  
  
## <a name="learn-more-about-built-in-json-support-in-sql-server"></a>SQL Server의 기본 제공 JSON 지원에 대해 자세히 알아보기  
 [Microsoft 프로그램 관리자인 Jovan Popovic의 블로그 게시물](http://blogs.msdn.com/b/sqlserverstorageengine/archive/tags/json/)  
  
## <a name="see-also"></a>참고 항목  
 [ISJSON&#40;Transact-SQL&#41;](../../t-sql/functions/isjson-transact-sql.md)   
 [JSON_VALUE&#40;Transact-SQL&#41;](../../t-sql/functions/json-value-transact-sql.md)   
 [JSON_QUERY&#40;Transact-SQL&#41;](../../t-sql/functions/json-query-transact-sql.md)   
 [JSON_MODIFY&#40;Transact-SQL&#41;](../../t-sql/functions/json-modify-transact-sql.md)   
 [JSON 경로 식&#40;SQL Server&#41;](../../relational-databases/json/json-path-expressions-sql-server.md)  
  
  
