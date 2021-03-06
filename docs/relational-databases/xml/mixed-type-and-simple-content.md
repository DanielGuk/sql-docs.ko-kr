---
title: 혼합 형식 및 단순 내용 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- mixed types [SQL Server]
ms.assetid: 6ea1f11d-e64b-4ebb-ab68-4eb6e4027665
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: ea0036898d14e86e02b1625bbff494423a1b2292
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51674922"
---
# <a name="mixed-type-and-simple-content"></a>혼합 형식 및 단순 내용
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서는 혼합 형식을 단순 내용으로 제한할 수 없습니다.  
  
## <a name="example"></a>예제  
 아래의 XML 스키마 컬렉션에서 `myComplexTypeA` 는 혼합 형식으로 비워둘 수 있습니다. 즉 해당 요소의 `minOccurs` 가 모두 0으로 설정됩니다. `myComplexTypeB` 선언에서처럼 혼합 형식을 단순 내용으로 제한하려는 시도는 지원되지 않습니다. 따라서 다음과 같은 XML 스키마 컬렉션을 만들 수 없습니다.  
  
```  
CREATE XML SCHEMA COLLECTION SC AS '  
<schema xmlns="https://www.w3.org/2001/XMLSchema" targetNamespace="https://ns" xmlns:ns="https://ns"  
xmlns:ns1="https://ns1">  
  
    <complexType name="myComplexTypeA" mixed="true">  
        <sequence>  
            <element name="a" type="string" minOccurs="0"/>  
            <element name="b" type="string" minOccurs="0" maxOccurs="23"/>  
        </sequence>  
    </complexType>  
  
    <complexType name="myComplexTypeB">  
        <simpleContent>  
            <restriction base="ns:myComplexTypeA">  
                <simpleType>  
                    <restriction base="int">  
                        <minExclusive value="25"/>  
                    </restriction>  
                </simpleType>  
            </restriction>  
        </simpleContent>  
    </complexType>  
</schema>  
'  
GO  
```  
  
## <a name="see-also"></a>참고 항목  
 [서버의 XML 스키마 컬렉션에 대한 요구 사항 및 제한 사항](../../relational-databases/xml/requirements-and-limitations-for-xml-schema-collections-on-the-server.md)  
  
  
