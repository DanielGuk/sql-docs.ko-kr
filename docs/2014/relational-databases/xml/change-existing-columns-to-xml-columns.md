---
title: 기존 열을 XML 열로 변경 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- tables [XML]
ms.assetid: 0d951424-9862-41fe-bd46-127f1c059bcb
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ff63ea72b88658d9504030612f77bb948e7462ed
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48226523"
---
# <a name="change-existing-columns-to-xml-columns"></a>기존 열을 XML 열로 변경
  ALTER TABLE 문을 지원 합니다 `xml` 데이터 형식입니다. 예를 들어 모든 문자열 유형 열을 변경할 수 있습니다는 `xml` 데이터 형식입니다. 이 경우 열에 포함된 문서는 올바른 형식이어야 합니다. 또한 열 유형을 문자열에서 형식화된 xml로 변경할 경우 지정된 XSD 스키마에 대해 열에 있는 문서의 유효성을 검사합니다.  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 nvarchar(max))  
GO  
INSERT INTO T   
VALUES (1, '<Root><Product ProductID="1"/></Root>')  
GO  
ALTER TABLE T   
ALTER COLUMN Col2 xml  
GO  
```  
  
 `xml` 유형 열을 형식화되지 않은 XML에서 형식화된 XML로 변경할 수 있습니다. 이는 아래와 같이 함수의 반환값을 데이터 프레임으로 바로 변환하는 데 사용할 수 있음을 나타냅니다.  
  
```  
CREATE TABLE T (Col1 int primary key, Col2 xml)  
GO  
INSERT INTO T   
values (1, '<p1:ProductDescription ProductModelID="1"   
xmlns:p1="http://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelDescription">  
            </p1:ProductDescription>')  
GO   
-- Make it a typed xml column by specifying a schema collection.  
ALTER TABLE T   
ALTER COLUMN Col2 xml (Production.ProductDescriptionSchemaCollection)  
GO  
```  
  
> [!NOTE]  
>  XML 스키마 컬렉션인 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 이 `Production.ProductDescriptionSchemaCollection`데이터베이스의 일부로 생성되기 때문에 이 스크립트는 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 데이터베이스에 대해 실행됩니다.  
  
 이전 예에서는 지정된 컬렉션에 있는 XSD 스키마에 대해 열에 저장된 모든 인스턴스의 유효성을 검사하고 이러한 인스턴스를 형식화합니다. 지정한 스키마에 맞지 않는 XML 인스턴스가 열에 하나 이상 있을 경우 `ALTER TABLE` 문이 실패하고 형식화되지 않은 XML 열을 형식화된 XML로 변경할 수 없습니다.  
  
> [!NOTE]  
>  테이블이 큰 경우 수정 된 `xml` 유형 열 비용이 증가할 수 있습니다. 각 문서의 형식이 형식화된 XML로서 알맞은지 검사하고 유효성을 검사해야 하기 때문입니다.  
  
 형식화된 XML에 대한 자세한 내용은 [형식화된 XML과 형식화되지 않은 XML 비교](compare-typed-xml-to-untyped-xml.md)를 참조하세요.  
  
  
