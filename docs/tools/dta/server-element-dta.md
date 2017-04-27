---
title: "Server 요소(DTA) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "XML"
helpviewer_keywords: 
  - "Server 요소"
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Server 요소(DTA)
  튜닝할 데이터베이스가 상주하는 서버에 대한 식별 정보를 포함합니다.  
  
## 구문  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## 요소 특징  
  
|특징|설명|  
|--------------------|-----------------|  
|**데이터 형식 및 길이**|없음|  
|**기본값**|없음|  
|**발생 빈도**|각 **DTAInput** 요소 당 한 번씩만 필요합니다.|  
  
## 요소 관계  
  
|관계|요소|  
|------------------|--------------|  
|**부모 요소**|[DTAInput 요소&#40;DTA&#41;](../../tools/dta/dtainput-element-dta.md)|  
|**자식 요소**|[Server의 Name 요소&#40;DTA&#41;](../../tools/dta/name-element-for-server-dta.md)<br /><br /> [Server의 Database 요소&#40;DTA&#41;](../../tools/dta/database-element-for-server-dta.md)|  
  
## 주의  
 **Server** 요소에 하나의 **DTAInput** 요소만 지정할 수 있습니다. 이 요소는 DTA XML 스키마에서 **ServerDetailsTypecomplexType** 이름입니다. 이 **Server** 요소와 **Configuration** 요소의 자식 요소를 혼동하지 마십시오. 자세한 내용은 [Configuration의 Server 요소&#40;DTA&#41;](../../tools/dta/server-element-for-configuration-dta.md)를 참조하세요.  
  
## 예제  
 다음 예에서는 SERVER001에 있는 **AdventureWorks** 데이터베이스의 **Sales.SalesPerson** 테이블을 지정하는 방법을 보여 줍니다.  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## 참고 항목  
 [XML 입력 파일 참조&#40;데이터베이스 엔진 튜닝 관리자&#41;](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  