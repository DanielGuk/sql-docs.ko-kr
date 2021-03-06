---
title: DataSpace (ADO-WFC 구문) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- DataSpace collection [ADO], ADO/WFC syntax
ms.assetid: 950d45d8-07de-467b-b255-f9a7b997204c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 94a539fb2ba3285bd8bb5c3668879695598725a4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47718351"
---
# <a name="dataspace-ado---wfc-syntax"></a>데이터스페이스(ADO - WFC 구문)
합니다 **createObject** 메서드는 **DataSpace** 클라이언트 응용 프로그램 요청을 처리 하는 데 두 비즈니스 개체를 지정 하는 클래스 (*progid*) 및 통신 프로토콜 및 서버 (*연결*). **createObject** 반환 된 [ObjectProxy](../../../ado/reference/ado-api/objectproxy-ado-wfc-syntax.md) 서버를 나타내는 개체입니다.  
  
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="constructor"></a>생성자  
  
```  
public DataSpace()  
```  
  
### <a name="methods"></a>메서드  
  
```  
public static ObjectProxy DataSpace.createObject(String  
    progid, String connection)  
```  
  
### <a name="properties"></a>속성  
  
```  
public static int getInternetTimeout()  
public static void setInternetTimeout(int plInetTimeout)  
```  
  
## <a name="see-also"></a>관련 항목  
 [DataSpace 개체(RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)
