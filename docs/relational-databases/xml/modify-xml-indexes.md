---
title: "XML 인덱스 수정 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML indexes [SQL Server], modifying
- modifying indexes
ms.assetid: 24d50fe1-c6ec-49e6-91a3-9791851ba53d
caps.latest.revision: 12
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2605bd79960ff302a89cdbb88f24ae1c36882d5f
ms.lasthandoff: 04/11/2017

---
# <a name="modify-xml-indexes"></a>XML 인덱스 수정
  [ALTER INDEX&#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)[!INCLUDE[tsql](../../includes/tsql-md.md)] DDL 문은 기존의 XML 인덱스와 비 XML 인덱스를 수정하는 데 사용할 수 없습니다. 그러나 모든 ALTER INDEX 옵션을 XML 인덱스에 사용할 수 있는 것은 아닙니다. XML 인덱스를 수정할 때 다음 옵션은 유효하지 않습니다.  
  
-   다시 작성 및 설정 옵션인 IGNORE_DUP_KEY는 XML 인덱스에 대해 유효하지 않습니다. 다시 작성 옵션 ONLINE은 보조 XML 인덱스에 대해 OFF로 설정해야 합니다. DROP_EXISTING 옵션은 ALTER INDEX 문에서 허용되지 않습니다.  
  
-   사용자 테이블에서 PRIMARY KEY 제약 조건을 수정하면 자동으로 XML 인덱스에 전파되지 않습니다. 사용자는 먼저 XML 인덱스를 삭제한 다음 다시 작성해야 합니다.  
  
-   ALTER INDEX ALL이 지정되면 비-XML 인덱스 및 XML 인덱스 모두에 적용됩니다. 인덱싱 옵션은 두 가지 인덱스 유형에 모두 유효하지 않도록 지정할 수 있습니다. 이 경우 전체 문이 실패합니다.  
  
## <a name="example-modifying-an-xml-index"></a>예제: XML 인덱스 수정  
 다음 예에서는 XML 인덱스가 생성되고 `ALLOW_ROW_LOCKS` 옵션을 `OFF`로 설정하여 수정됩니다. `ALLOW_ROW_LOCKS` 가 `OFF`일 때는 행이 잠기지 않고 페이지 수준 및 테이블 수준의 잠금을 사용하여 지정된 인덱스에 대한 액세스가 설정됩니다.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
-- Create primary XML index.   
CREATE PRIMARY XML INDEX PIdx_T_XmlCol   
ON T(XmlCol)  
GO  
-- Note the type 3 is index on XML type.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
  
-- Modify and set an index option.  
ALTER INDEX PIdx_T_XmlCol on T   
SET (ALLOW_ROW_LOCKS = OFF)  
```  
  
## <a name="example-disabling-and-enabling-an-xml-index"></a>예제: XML 인덱스 활성화 및 비활성화  
 기본적으로 XML 인덱스는 활성화됩니다. XML 인덱스가 비활성화되어 있는 경우 XML 열에 대해 실행되는 쿼리에서는 해당 XML 인덱스를 사용할 수 없습니다. XML 인덱스를 활성화하려면 `ALTER INDEX` 옵션과 함께 `REBUILD` 를 사용합니다.  
  
```  
CREATE TABLE T (Col1 INT PRIMARY KEY, XmlCol XML)  
GO  
CREATE PRIMARY XML INDEX PIdx_T_XmlCol ON T(XmlCol)  
GO  
ALTER INDEX PIdx_T_XmlCol on T DISABLE  
Go  
-- Verify index is disabled.  
SELECT *  
FROM sys.xml_indexes  
WHERE object_id = object_id('T')  
AND name='PIdx_T_XmlCol'  
-- Rebuild the index.  
ALTER INDEX PIdx_T_XmlCol on T REBUILD  
Go  
```  
  
## <a name="see-also"></a>참고 항목  
 [XML 인덱스&#40;SQL Server&#41;](../../relational-databases/xml/xml-indexes-sql-server.md)  
  
  