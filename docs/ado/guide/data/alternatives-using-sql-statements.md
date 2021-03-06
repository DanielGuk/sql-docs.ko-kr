---
title: '대안: SQL 문을 사용 하 여 | Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b95e6f0bd2b702080b3580b8b9eeb80ac5b06e8d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47674261"
---
# <a name="alternatives-using-sql-statements"></a>대안: SQL 문 사용
ADO를 대체 하는 기본 제공 속성 및 메서드 데이터를 편집 하기 위한 명령을 사용할 수도 있습니다. 공급자에 따라이 섹션에 언급 된 모든 작업이 완료할 수 있습니다 데이터 원본에 명령을 전달 하 여 합니다. SQL UPDATE 문을 사용 하지 않고 데이터를 수정 하려면 예를 들어 사용할 수는 **값** 의 속성을 **필드**합니다. ADO 메서드 대신 데이터 원본에 새 레코드를 추가할 SQL INSERT 문은 사용할 수 있습니다 **AddNew**합니다. SQL 또는 공급자의 데이터 조작 언어에 대 한 자세한 내용은 데이터 원본의 설명서를 참조 합니다.  
  
 예를 들어, 다음 코드와 같이 데이터베이스에는 DELETE 문을 포함 하는 SQL 문자열을 전달할 수 있습니다.  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
