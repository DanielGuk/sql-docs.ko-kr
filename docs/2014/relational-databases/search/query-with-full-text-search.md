---
title: 전체 텍스트 검색을 사용한 쿼리 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- queries [full-text search], about full-text queries
- queries [full-text search], predicates
- full-text queries [SQL Server], about full-text queries
- full-text search [SQL Server], querying SQL Server
- full-text queries [SQL Server]
- queries [full-text search], functions
ms.assetid: 7624ba76-594b-4be5-ac10-c3ac4a3529bd
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e8c8867b932d291415f584f93a09478bbd05725
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48152723"
---
# <a name="query-with-full-text-search"></a>Query with Full-Text Search
  전체 텍스트 검색을 정의하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 전체 텍스트 쿼리는 전체 텍스트 조건자(CONTAINS 및 FREETEXT) 및 함수(CONTAINSTABLE 및 FREETEXTTABLE)를 사용합니다. 이러한 조건자와 함수는 다양한 형태의 쿼리 용어를 지원하는 많은 [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문을 지원합니다. 전체 텍스트 쿼리를 작성하려면 이러한 조건자와 함수를 사용하는 시기와 방법을 알아야 합니다.  
  
##  <a name="OV_ft_predicates"></a> 개요 전체 텍스트 조건자 (CONTAINS 및 FREETEXT)  
 CONTAINS 및 FREETEXT 조건자는 TRUE 또는 FALSE 값을 반환합니다. 이러한 조건자는 지정된 행이 전체 텍스트 쿼리와 일치하는지 여부를 확인하는 선택 조건을 지정하는 데에만 사용할 수 있습니다. 일치하는 행은 결과 집합에 반환됩니다. CONTAINS 및 FREETEXT는 SELECT 문의 WHERE 또는 HAVING 절에 지정됩니다. CONTAINS 및 FREETEXT는 LIKE와 BETWEEN 등의 다른 [!INCLUDE[tsql](../../includes/tsql-md.md)] 조건자와 결합할 수 있습니다.  
  
> [!NOTE]  
>  구문 및 이러한 조건자의 인수에 대 한 정보를 참조 하세요 [포함 &#40;TRANSACT-SQL&#41; ](/sql/t-sql/queries/contains-transact-sql) 하 고 [FREETEXT &#40;Transact SQL&#41;](/sql/t-sql/queries/freetext-transact-sql).  
  
 CONTAINS 또는 FREETEXT를 사용하면 검색할 테이블의 단일 열, 열 목록 또는 모든 열을 지정할 수 있으며, 경우에 따라 단어 분리, 형태소 분석, 동의어 사전 조회 및 의미 없는 단어 제거를 위해 지정된 전체 텍스트 쿼리에서 사용할 리소스의 언어를 지정할 수도 있습니다.  
  
 CONTAINS 및 FREETEXT는 다음과 같은 다양한 유형의 일치에 유용합니다.  
  
-   CONTAINS(또는 CONTAINSTABLE)를 사용하여 특정 단어나 구와 정확히 일치하거나 비슷하게 일치하는 단어를 검색하거나, 서로 근접한 단어를 검색하거나, 가중치 검색을 수행합니다. CONTAINS를 사용할 경우 검색할 텍스트를 지정하는 하나 이상의 검색 조건과 일치 여부를 결정하는 조건을 지정해야 합니다.  
  
     검색 조건 사이에 논리적 연산을 사용할 수 있습니다. 자세한 내용은 이 항목의 뒷부분에 나오는 [CONTAINS 및 CONTAINSTABLE에 부울 연산자 AND, OR, AND NOT 사용](#Using_Boolean_Operators)을 참조하세요.  
  
-   FREETEXT(또는 FREETEXTTABLE)를 사용하여 지정된 단어, 구 또는 문장( *freetext 문자열*)의 정확한 단어가 아닌 의미를 일치시킵니다. 지정된 열의 모든 용어나 용어 형태가 전체 텍스트 인덱스에 있으면 일치하는 항목이 생성됩니다.  
  
 CONTAINS 또는 FREETEXT 조건자에 네 부분으로 된 이름을 사용하여 연결된 서버의 대상 테이블에 대한 전체 텍스트 인덱싱된 열을 쿼리할 수 있습니다. 원격 서버에서 전체 텍스트 쿼리를 받도록 준비하려면 원격 서버의 대상 테이블 및 열에 대한 전체 텍스트 인덱스를 만든 다음 원격 서버를 연결된 서버로 추가합니다.  
  
> [!NOTE]  
>  데이터베이스 호환성 수준이 100으로 설정된 경우에는 [OUTPUT 절](/sql/t-sql/queries/output-clause-transact-sql) 에 전체 텍스트 조건자가 허용되지 않습니다.  
  
 
  
### <a name="examples"></a>예  
  
#### <a name="a-using-contains-with-simpleterm"></a>1. <simple_term>에 CONTAINS 사용  
 다음 예에서는 가격이 `$80.99`이고 `"Mountain"`이라는 단어가 포함된 모든 제품을 검색합니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Name, ListPrice  
FROM Production.Product  
WHERE ListPrice = 80.99  
   AND CONTAINS(Name, 'Mountain')  
GO  
```  
  
#### <a name="b-using-freetext-to-search-for-words-containing-specified-character-values"></a>2. FREETEXT를 사용하여 지정된 문자 값을 포함하는 단어 검색  
 다음 예에서는 vital, safety, components와 관련된 단어를 포함하는 문서를 모두 검색합니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Title  
FROM Production.Document  
WHERE FREETEXT (Document, 'vital safety components')  
GO  
```  
  
 
  
##  <a name="OV_ft_functions_CONTAINSTABLE_FREETEXTTABLE"></a> 전체 텍스트 함수 (CONTAINSTABLE 및 FREETEXTTABLE) 개요  
 CONTAINSTABLE 및 FREETEXTTABLE 함수는 일반 테이블 이름처럼 SELECT 문의 FROM 절에서 참조될 수 있습니다. 이러한 함수는 전체 텍스트 쿼리와 일치하는 행이 0개, 1개 또는 그 이상 있는 테이블을 반환합니다. 반환된 테이블에는 함수의 전체 텍스트 검색 조건에 지정된 선택 조건과 일치하는 기본 테이블의 행만 포함됩니다.  
  
> [!NOTE]  
>  구문 및 이러한 함수의 인수에 대 한 정보를 참조 하세요 [CONTAINSTABLE &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-functions/containstable-transact-sql) 하 고 [FREETEXTTABLE &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql).  
  
 이러한 함수 중 하나를 사용하는 쿼리는 다음과 같이 각 행에 대해 적절한 순위 값(RANK) 및 전체 텍스트 키(KEY)를 반환합니다.  
  
-   KEY 열  
  
     KEY 열은 반환된 행의 고유 값을 반환하며, 선택 조건을 지정하는 데 사용할 수 있습니다.  
  
-   RANK 열  
  
     RANK 열은 각 행이 선택 조건과 일치하는 정도를 나타내는 *순위 값* 을 반환합니다. 행의 텍스트 또는 문서 순위 값이 높을수록 지정된 전체 텍스트 쿼리에 대한 행의 관련성이 큽니다. 또한 여러 행에 동일한 순위가 지정될 수도 있습니다. 선택적 *top_n_by_rank* 매개 변수를 지정하면 반환될 일치 항목 수를 제한할 수 있습니다. 자세한 내용은 [RANK를 사용하여 검색 결과 제한](limit-search-results-with-rank.md)을 참조하세요.  
  
 이러한 함수 중 하나를 사용할 경우 전체 텍스트를 검색할 기본 테이블을 지정해야 합니다. 조건자와 마찬가지로 검색할 테이블의 단일 열, 열 목록 또는 모든 열을 지정할 수 있으며, 경우에 따라 전체 텍스트 쿼리에서 사용할 리소스의 언어를 지정할 수도 있습니다.  
  
 CONTAINSTABLE은 CONTAINS와 같은 유형의 일치에 유용하고 FREETEXTTABLE은 FREETEXT와 같은 유형의 일치에 유용합니다. 자세한 내용은 이 항목의 앞부분에 나오는 [전체 텍스트 조건자(CONTAINS 및 FREETEXT) 개요](#OV_ft_predicates)를 참조하세요. CONTAINSTABLE 및 FREETEXTTABLE 함수를 사용하는 쿼리를 실행할 경우 반환된 행을 원래 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 테이블의 행과 명시적으로 조인해야 합니다.  
  
 일반적으로 CONTAINSTABLE 또는 FREETEXTTABLE 결과는 기본 테이블과 조인되어야 합니다. 이러한 경우 고유 키 열 이름을 알아야 합니다. 모든 전체 텍스트 사용 테이블에서 생성되는 이 열은 해당 테이블에 고유 행을 강제 적용하는 데 사용됩니다(*고유**키 열*). 자세한 내용은 [전체 텍스트 인덱스 관리](../indexes/indexes.md)를 참조하세요.  
  
 
  
### <a name="examples"></a>예  
  
#### <a name="a-using-containstable"></a>1. CONTAINSTABLE 사용  
 다음 예에서는 **Description** 열에서 "light" 또는 "lightweight"라는 단어 근처에 "aluminum"이라는 단어가 포함된 모든 제품의 설명 ID와 설명을 반환합니다. 등급 값이 2 이상인 행만 반환됩니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT FT_TBL.ProductDescriptionID,  
   FT_TBL.Description,   
   KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL INNER JOIN  
   CONTAINSTABLE (Production.ProductDescription,  
      Description,   
      '(light NEAR aluminum) OR  
      (lightweight NEAR aluminum)'  
   ) AS KEY_TBL  
   ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK > 2  
ORDER BY KEY_TBL.RANK DESC;  
GO  
```  
  
#### <a name="b-using-freetexttable"></a>2. FREETEXTTABLE 사용  
 다음 예에서는 순위가 높은 행을 먼저 반환하고 SELECT 목록에 각 행의 순위를 추가하도록 FREETEXTTABLE 쿼리를 확장합니다. 쿼리를 지정 하려면 임을 알아야 **ProductDescriptionID** 에 대 한 고유 키 열을 `ProductDescription` 테이블입니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 다음은 순위 값이 10 이상인 행만 반환하도록 동일한 쿼리를 확장한 것입니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT KEY_TBL.RANK, FT_TBL.Description  
FROM Production.ProductDescription AS FT_TBL   
     INNER JOIN  
     FREETEXTTABLE(Production.ProductDescription, Description,  
                    'perfect all-around bike') AS KEY_TBL  
     ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
WHERE KEY_TBL.RANK >= 10  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 
  
##  <a name="Using_Boolean_Operators"></a> 부울 연산자 AND, OR, 사용 및 CONTAINS 및 CONTAINSTABLE에 없는 –  
 CONTAINS 조건자와 CONTAINSTABLE 함수는 동일한 검색 조건을 사용하며, 둘 다 논리적 연산을 수행하는 부울 연산자 AND, OR, AND NOT을 사용하여 여러 검색 단어를 결합할 수 있습니다. 예를 들어 AND를 사용하여 "latte"와 "New York-style bagel"이 둘 다 포함된 행을 찾거나 AND NOT을 사용하여 "bagel"은 포함되지만 "cream cheese"는 포함되지 않은 행을 찾을 수 있습니다.  
  
> [!NOTE]  
>  반면에 FREETEXT 및 FREETEXTTABLE은 부울 단어를 검색할 단어로 취급합니다.  
  
 CONTAINS를 논리 연산자 AND, OR 및 NOT을 사용하는 다른 조건자와 결합하는 방법은 [검색 조건&#40;Transact-SQL&#41;](/sql/t-sql/queries/search-condition-transact-sql)을 참조하세요.  
  
### <a name="example"></a>예제  
 다음 예에서는 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 데이터베이스의 ProductDescription 테이블을 사용합니다. 이 쿼리는 CONTAINS 조건자를 사용하여 설명 ID가 5와 같지 않고 "Aluminum"이라는 단어와 "spindle"이라는 단어가 모두 포함된 설명을 검색합니다. 검색 조건에는 AND 부울 연산자가 사용됩니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description  
FROM Production.ProductDescription  
WHERE ProductDescriptionID <> 5 AND  
   CONTAINS(Description, 'aluminum AND spindle')  
GO  
```  
  
 
  
##  <a name="Additional_Considerations"></a> 전체 텍스트 쿼리에 대 한 추가 고려 사항  
 전체 텍스트 쿼리를 작성할 때 다음 사항도 고려하십시오.  
  
-   LANGUAGE 옵션  
  
     많은 쿼리 용어는 단어 분리기 동작에 크게 의존합니다. 올바른 단어 분리기(및 형태소 분석기)를 사용하고 있는지 확인하려면 LANGUAGE 옵션을 지정하는 것이 좋습니다. 자세한 내용은 [전체 텍스트 인덱스 생성 시 언어 선택](choose-a-language-when-creating-a-full-text-index.md)을 참조하세요.  
  
-   중지 단어  
  
     전체 텍스트 쿼리를 정의할 때 전체 텍스트 엔진은 검색 조건에서 중지 단어(의미 없는 단어라고도 함)를 삭제합니다. 중지 단어란 "a", "and", "is", "the" 등과 같이 자주 사용되지만 일반적으로 특정 텍스트 검색에는 도움이 되지 않는 단어입니다. 중지 단어는 중지 목록에 나열됩니다. 인덱싱할 때 쿼리 또는 인덱스에서 생략된 중지 단어를 확인할 수 있도록 각 전체 텍스트 인덱스는 특정 중지 목록과 연결됩니다. 자세한 내용은 [전체 텍스트 검색에 사용할 중지 단어와 중지 목록 구성 및 관리](full-text-search.md)를 참조하세요.  
  
-   동의어 사전  
  
     FREETEXT 및 FREETEXTTABLE 쿼리에는 기본적으로 동의어 사전이 사용됩니다. CONTAINS 및 CONTAINSTABLE은 선택적 THESAURUS 인수를 지원합니다.  
  
-   대/소문자 구분  
  
     전체 텍스트 검색 쿼리는 대/소문자를 구분합니다. 그러나 일본어에는 철자 표준화 개념이 대/소문자를 구분하지 않는 것과 비슷한 여러 가지 음성 철자법이 있습니다(예: 가나를 구분하지 않음). 이러한 철자 표준화는 지원되지 않습니다.  
  

  
##  <a name="varbinary"></a> Varbinary (max) 및 xml 열 쿼리  
 `varbinary(max)`, `varbinary` 또는 `xml` 열이 전체 텍스트 인덱싱된 경우 다른 전체 텍스트 인덱싱된 열과 마찬가지로 전체 텍스트 조건자(CONTAINS 및 FREETEXT) 및 함수(CONTAINSTABLE 및 FREETEXTTABLE)를 사용하여 이러한 열을 쿼리할 수 있습니다.  
  
> [!IMPORTANT]  
>  전체 텍스트 검색은 이미지 열에서도 작동합니다. 그러나 합니다 `image` 데이터 형식의 이후 버전에서 제거 됩니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]합니다. 새 개발 작업에서는 이 데이터 형식을 사용하지 않도록 하고 현재 이 데이터 형식을 사용하는 애플리케이션은 수정하십시오. 사용 된 `varbinary(max)` 데이터 형식 대신 합니다.  
  
### <a name="varbinarymax-or-varbinary-data"></a>varbinary(max) 또는 varbinary 데이터  
 단일 `varbinary(max)` 또는 `varbinary` 열에 많은 문서 유형을 저장할 수 있습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 필터가 설치되어 있고 운영 체제에서 사용할 수 있는 문서 유형을 지원합니다. 각 문서의 문서 유형은 문서의 파일 확장명으로 식별됩니다. 예를 들어 .doc 파일 확장명의 경우 전체 텍스트 검색은 Microsoft Word 문서를 지원하는 필터를 사용합니다. 사용 가능한 문서 유형의 목록을 보려면 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) 카탈로그 뷰를 쿼리하세요.  
  
 전체 텍스트 엔진은 운영 체제에 설치된 기존 필터를 활용할 수 있습니다. 운영 체제 필터, 단어 분리기, 형태소 분석기를 사용하려면 먼저 다음과 같이 서버 인스턴스에 로드해야 합니다.  
  
```  
EXEC sp_fulltext_service @action='load_os_resources', @value=1  
```  
  
 `varbinary(max)` 열에 대한 전체 텍스트 인덱스를 만들려면 전체 텍스트 엔진이 `varbinary(max)` 열에 있는 문서의 파일 확장명에 액세스해야 합니다. 이 정보는 전체 텍스트 인덱스의 `varbinary(max)` 열에 연결해야 하는 테이블 열, 즉 유형 열에 저장되어야 합니다. 문서를 인덱싱할 때 전체 텍스트 엔진은 유형 열의 파일 확장명을 사용하여 사용할 필터를 식별합니다.  
  
 
  
### <a name="xml-data"></a>xml 데이터  
 `xml` 데이터 형식 열에만 XML 문서 및 조각을 저장 하 고 문서는 XML 필터만 사용 됩니다. 따라서 유형 열은 필요하지 않습니다. `xml` 열, 전체 텍스트 인덱스는 XML 요소의 내용을 인덱싱하지만 XML 태그입니다. 특성 값은 숫자 값이 아니면 전체 텍스트 인덱싱됩니다. 요소 태그는 토큰 경계로 사용됩니다. 여러 언어를 포함하는 올바른 형식의 XML 또는 HTML 문서와 조각이 지원됩니다.  
  
 에 대 한 쿼리 하는 방법에 대 한 자세한 내용은 `xml` 열을 참조 하세요 [XML 열을 사용 하 여 전체 텍스트 검색을 사용 하 여](../xml/use-full-text-search-with-xml-columns.md)합니다.  
  
 
  
##  <a name="supported"></a> 쿼리 용어에 지원 되는 형태  
 이 섹션에서는 전체 텍스트 조건자 및 행 집합 반환 함수에서 각 쿼리 형태에 제공하는 지원에 대해 간략히 설명합니다.  
  
> [!NOTE]  
>  쿼리 용어의 구문을 보려면 다음 표의 **지원 요소** 열에서 해당 링크를 클릭하세요.  
  
|쿼리 용어 형태|Description|지원 요소|  
|----------------------|-----------------|------------------|  
|하나 이상의 특정 단어 또는 구(*단순 단어*)|전체 텍스트 검색에서 단어(또는 *토큰*)는 지정된 언어의 언어 규칙에 따라 적절한 단어 분리기에 의해 경계가 식별되는 문자열입니다. 올바른 구는 여러 단어로 구성됩니다. 문장 부호는 있을 수도 있고 없을 수도 있습니다.<br /><br /> 예를 들어 "croissant"은 단어이고 "café au lait"는 구입니다. 이와 같은 단어 및 구를 단순 단어라고 합니다.<br /><br /> 자세한 내용은 이 항목 뒷부분의 [특정 단어 또는 구(단순 단어) 검색](#Simple_Term)을 참조하세요.|[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 은 정확히 일치하는 구를 검색합니다.<br /><br /> [FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 은 구를 여러 개의 단어로 나눕니다.|  
|특정 텍스트로 시작하는 단어 또는 그러한 단어를 포함하는 구(*접두사 단어*)|접두사 단어는 파생어를 만들거나 굴절형을 만들기 위해 단어 앞에 추가되는 문자열을 말합니다.<br /><br /> 단일 접두사 단어의 경우 지정된 단어로 시작하는 모든 단어가 결과 집합의 일부로 반환됩니다. 예를 들어 "auto*" 단어를 사용하면 "automatic", "automobile" 등이 검색됩니다.<br /><br /> 구의 경우 구에 포함된 각 단어가 접두사 단어로 간주됩니다. 예를 들어 "auto tran\*"은 "automatic transmission" 및 "automobile transducer"와 일치하지만 "automatic motor transmission"과는 일치하지 않습니다.<br /><br /> 자세한 내용은 이 항목 뒷부분의 [접두사(접두사 단어) 검색](#Prefix_Term)을 참조하세요.|[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|특정 단어의 굴절형(*생성 단어-굴절형*)|굴절형은 동사의 여러 시제 및 변화와 명사의 단수형 및 복수형을 의미합니다. 예를 들어 "drive"라는 단어의 굴절형을 검색한다고 가정합니다. 테이블의 여러 행에 "drive", "drives", "drove", "driving", "driven" 등의 단어가 포함되어 있는 경우 이러한 각 단어는 drive라는 단어를 활용하여 생성된 것이므로 모두 결과 집합에 포함됩니다.<br /><br /> 자세한 내용은 이 항목 뒷부분의 [특정 단어의 굴절형(생성 단어) 검색](#Inflectional_Generation_Term)을 참조하세요.|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 은 기본적으로 지정된 모든 단어의 굴절형을 검색합니다.<br /><br /> [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 은 선택적 INFLECTIONAL 인수를 지원합니다.|  
|특정 단어의 동의어 형태(*생성 단어-동의어 사전*)|동의어 사전은 단어에 대한 사용자 지정 동의어를 정의합니다. 예를 들어 동의어 사전에 "{car, automobile, truck, van}" 항목을 추가하면 "car"라는 단어의 동의어 형태를 검색할 수 있습니다. "automobile", "truck", "van" 또는 "car"라는 단어는 각각 "car"라는 단어를 포함하는 동의어 확장 집합에 속하므로 이러한 단어를 포함하는 쿼리된 테이블의 모든 행이 결과 집합에 나타납니다.<br /><br /> 동의어 사전 파일의 구조에 대한 자세한 내용은 [전체 텍스트 검색에 사용할 동의어 사전 파일 구성 및 관리](configure-and-manage-thesaurus-files-for-full-text-search.md)를 참조하세요.|[FREETEXT](/sql/t-sql/queries/freetext-transact-sql) 및 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 에는 기본적으로 동의어 사전이 사용됩니다.<br /><br /> [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 은 선택적 THESAURUS 인수를 지원합니다.|  
|다른 단어나 구와 근접한 단어나 구(*근접 단어*)|근접 단어는 서로 근접하는 단어나 구를 나타냅니다. 첫 번째 검색 단어와 마지막 검색 단어를 구분하는 검색 대상이 아닌 단어의 최대 개수를 지정할 수도 있습니다. 또한 임의의 순서나 지정한 순서로 단어 또는 구를 검색할 수 있습니다.<br /><br /> 예를 들어 "ice"라는 단어가 "hockey"라는 단어와 근접해 있거나 "ice skating"이라는 구가 "ice hockey"라는 구와 근접해 있는 행을 검색할 수 있습니다.<br /><br /> 자세한 내용은 [NEAR를 사용하여 근접 단어 검색](search-for-words-close-to-another-word-with-near.md)을 참조하세요.|[CONTAINS](/sql/t-sql/queries/contains-transact-sql) 및 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
|가중치를 사용하는 단어나 구(*가중치 단어*)|단어와 구 집합에서 각 단어와 구의 중요도를 나타내는 가중치입니다. 가중치는 0.0이 가장 낮고 1.0이 가장 높습니다.<br /><br /> 예를 들어 여러 단어를 검색하는 쿼리에서 각 검색 단어에 검색 조건에 있는 다른 단어에 대한 상대적 중요도를 나타내는 가중치를 할당할 수 있습니다. 이러한 쿼리 유형의 결과에서는 검색 단어에 지정한 상대적 가중치에 따라 관련성이 가장 높은 행이 먼저 반환됩니다. 결과 집합에는 지정된 단어(또는 단어 사이의 내용) 중 적어도 하나를 포함하는 문서 또는 행이 반환되지만 일부 결과는 검색된 여러 개의 단어와 관련된 가중치의 차이 때문에 다른 결과보다 관련이 높은 것으로 간주됩니다.<br /><br /> 자세한 내용은 이 항목 뒷부분의 [가중치를 사용하는 단어 또는 구(가중치 단어) 검색](#Weighted_Term)을 참조하세요.|[CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql)|  
  

  
###  <a name="Simple_Term"></a> 특정 단어 또는 구 (단순 단어) 검색  
 [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)또는 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 을 사용하여 테이블에서 특정 구를 검색할 수 있습니다. 예를 들어, 검색 하려는 경우는 `ProductReview` 테이블에 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] CONTAINS 조건자를 다음과 같이 사용할 수 있습니다 "learning curve" 라는 구가 포함 된 제품 설명을 모두 찾으려면 데이터베이스:  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments  
FROM Production.ProductReview  
WHERE CONTAINS(Comments, '"learning curve"')  
GO  
```  
  
 검색 조건(이 경우 "learning curve")은 매우 복잡할 수 있으며 하나 이상의 단어로 구성될 수 있습니다.  
  
 
  
###  <a name="Prefix_Term"></a> 접두사 (접두사 단어) 검색을 수행합니다.  
 [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 또는 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 을 사용하여 지정된 접두사가 포함된 단어나 구를 검색할 수 있습니다. 열에서 지정된 접두사로 시작하는 텍스트가 포함된 모든 항목이 반환됩니다. 예를 들어 `top`, `top``ple`및 `top``ping`에서와 같이 `top`- 접두사가 포함된 모든 행을 검색하려면 다음 쿼리를 사용합니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Description, ProductDescriptionID  
FROM Production.ProductDescription  
WHERE CONTAINS (Description, '"top*"' )  
GO  
```  
  
 별표(*) 앞에 지정된 텍스트와 일치하는 모든 텍스트가 반환됩니다. `CONTAINS (DESCRIPTION, 'top*')`에서와 같이 텍스트와 별표가 큰따옴표로 구분되지 않은 경우 전체 텍스트 검색은 별표를 와일드카드로 간주하지 않습니다.  
  
 접두사 단어가 구일 경우 구에 포함된 각 토큰이 별도의 접두사 단어로 간주되므로 접두사 단어로 시작하는 단어가 포함된 모든 행이 반환됩니다. 예를 들어 접두사 단어가 "light bread*"이면 "light breaded", "lightly breaded", "light bread" 등의 텍스트가 포함된 행이 검색되지만 "lightly toasted bread"는 반환되지 않습니다.  
  
 
  
###  <a name="Inflectional_Generation_Term"></a> (생성 단어) 특정 단어의 굴절 형 검색  
 [CONTAINS](/sql/t-sql/queries/contains-transact-sql), [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql), [FREETEXT](/sql/t-sql/queries/freetext-transact-sql)또는 [FREETEXTTABLE](/sql/relational-databases/system-functions/freetexttable-transact-sql) 을 사용하여 동사의 여러 시제나 변화 또는 명사의 단수형과 복수형을 모두 검색(굴절형 검색)하거나, 특정 단어의 동의어 형태를 모두 검색(동의어 검색)할 수 있습니다.  
  
 다음 예에서는 `Comments` 데이터베이스의 `ProductReview` 테이블에 있는 `AdventureWorks` 열에서 "foot"의 모든 형태("foot", "feet" 등)를 검색합니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT Comments, ReviewerName  
FROM Production.ProductReview  
WHERE CONTAINS (Comments, 'FORMSOF(INFLECTIONAL, "foot")')  
GO  
```  
  
> [!NOTE]  
>  전체 텍스트 검색에서는 동사의 다양한 시제와 변화 또는 명사의 단수형과 복수형을 모두 검색할 수 있는 형태소 분석기를 사용합니다. 형태소 분석기에 대한 자세한 내용은 [검색을 위해 단어 분리기와 형태소 분석기 구성 및 관리](configure-and-manage-word-breakers-and-stemmers-for-search.md)를 참조하세요.  
  

  
###  <a name="Weighted_Term"></a> 검색 단어 또는 구를 사용 하 여 가중치 (가중치 단어)  
 [CONTAINSTABLE](/sql/relational-databases/system-functions/containstable-transact-sql) 을 사용하여 단어나 구를 검색하고 가중치를 지정할 수 있습니다. 가중치는 0.0에서 1.0 사이의 숫자로 측정되며 단어와 구 집합에서 각 단어와 구의 중요도를 나타냅니다. 가중치 0.0이 가장 낮고 1.0이 가장 높습니다.  
  
 다음 예에서는 가중치를 사용하여 문자열 "Bay"로 시작하는 텍스트에 "Street" 또는 "View"가 있는 모든 고객 주소를 검색하는 쿼리를 보여 줍니다. 지정한 단어가 많이 포함된 행일수록 높은 가중치가 지정됩니다.  
  
```  
USE AdventureWorks2012  
GO  
  
SELECT AddressLine1, KEY_TBL.RANK   
FROM Person.Address AS Address INNER JOIN  
CONTAINSTABLE(Person.Address, AddressLine1, 'ISABOUT ("Bay*",   
         Street WEIGHT(0.9),   
         View WEIGHT(0.1)  
         ) ' ) AS KEY_TBL  
ON Address.AddressID = KEY_TBL.[KEY]  
ORDER BY KEY_TBL.RANK DESC  
GO  
```  
  
 가중치 단어는 단순 단어, 접두사 단어, 생성 단어 또는 근접 단어와 함께 사용할 수 있습니다.  
  

  
##  <a name="tokens"></a> 단어 분리기, 동의어 사전 및 중지 목록 조합의 토큰화 결과 보기  
 쿼리 문자열 입력에 특정 단어 분리기, 동의어 사전 및 중지 목록 조합을 적용하면 **sys.dm_fts_parser** 동적 관리 뷰를 사용하여 토큰화 결과를 볼 수 있습니다. 자세한 내용은 [sys.dm_fts_parser&#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-parser-transact-sql)를 참조하세요.  
  
 
  
## <a name="see-also"></a>관련 항목  
 [CONTAINS&#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql)   
 [CONTAINSTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/containstable-transact-sql)   
 [FREETEXT&#40;Transact-SQL&#41;](/sql/t-sql/queries/freetext-transact-sql)   
 [FREETEXTTABLE&#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/freetexttable-transact-sql)   
 [전체 텍스트 검색 쿼리 만들기&#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)   
 [전체 텍스트 쿼리 성능 향상](improve-the-performance-of-full-text-queries.md)  
  
  
