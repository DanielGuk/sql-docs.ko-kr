---
title: "조건자 이스케이프 문자 처럼 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LIKE predicate [ODBC]
- escape sequences [ODBC], LIKE predicate
ms.assetid: 185d6109-48cf-4981-bc40-ec2a4a90cafc
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 132359972cebd3dded36fb911a2ee8e561e5ca64
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="like-predicate-escape-character"></a>마찬가지로 조건자 이스케이프 문자
에 **같은** 조건자 백분율 기호 (%) 일치 항목 0 개 이상의 임의 문자 및 밑줄 (_) 하나의 문자를 찾습니다. 실제 백분율 기호는 하거나에 밑줄을 **같은** 조건자에 이스케이프 문자가 앞에 야 백분율 기호 또는 밑줄 합니다. 정의 하는 이스케이프 시퀀스는 **같은** 조건자 이스케이프 문자는:  
  
 **{이스케이프 '** *이스케이프 문자* **'을 (를)**  
  
 여기서 *이스케이프 문자* 데이터 소스에서 지 원하는 모든 문자입니다.  
  
 LIKE에 대 한 자세한 내용은 이스케이프 시퀀스를 참조 [이스케이프 시퀀스와 같은](../../../odbc/reference/appendixes/like-escape-sequence.md) 부록 c: SQL 문법에 있습니다.  
  
 예를 들어 다음 SQL 문을 이름이 "%AAA" 문자로 시작 하는 고객의 동일한 결과 집합을 만듭니다. 첫 번째 문은 이스케이프 시퀀스 구문을 사용합니다. 두 번째 문은 Microsoft® Access에 대 한 기본 구문을 사용 하 고 상호 운용 가능한 되지 않습니다. 두 번째 % 각 문자는 **같은** 조건자는 0 개 이상의 임의의 문자와 일치 하는 와일드 카드 문자입니다.  
  
```  
SELECT Name FROM Customers WHERE Name LIKE '\%AAA%' {escape '\'}  
  
SELECT Name FROM Customers WHERE Name LIKE '[%]AAA%'  
```  
  
 확인 하려면 여부는 **같은** 조건자 이스케이프 문자가 데이터 원본에 의해 지원 되는지, 응용 프로그램이 호출 **SQLGetInfo** SQL_LIKE_ESCAPE_CLAUSE 옵션을 사용 합니다.