---
title: 열거 패싯 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- enumeration facets
ms.assetid: dec23a79-ddd6-4701-9721-55a2c435a34d
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0352161844580ade3a6305b2ed48f063e3fc154a
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51660023"
---
# <a name="enumeration-facets"></a>열거 패싯
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 패턴 패싯 형식이나 이러한 패싯을 위반하는 열거형의 XML 스키마를 거부합니다.  
  
## <a name="example"></a>예제  
 다음 스키마는 주요 열거 값이 대/소문자 값을 포함하기 때문에 거부됩니다. 또한 이 값이 소문자로만 값을 제한하는 패턴 값을 위반하기 때문에 거부됩니다.  
  
```  
CREATE XML SCHEMA COLLECTION MySampleCollection AS '  
<schema xmlns="https://www.w3.org/2001/XMLSchema" targetNamespace="https://ns" xmlns:ns="https://ns">  
    <simpleType name="MyST">  
       <restriction base="string">  
          <pattern value="[a-z]*"/>  
       </restriction>  
    </simpleType>  
  
    <simpleType name="MyST2">  
       <restriction base="ns:MyST">  
           <enumeration value="mYstring"/>  
       </restriction>  
    </simpleType>  
</schema>'  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
