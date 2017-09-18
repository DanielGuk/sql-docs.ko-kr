---
title: "드라이버 | Microsoft Docs"
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
- ODBC architecture [ODBC], drivers
- drivers [ODBC]
- drivers [ODBC], about drivers
ms.assetid: d6795d92-877e-44e1-b7d5-2ff2fd3989bd
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f25be027774c83a31077953eaf51ea8f643bf5e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="drivers"></a>드라이버
*드라이버* 는 ODBC api에서 함수를 구현 하는 라이브러리입니다. 각 작업은 특정 DBMS;에 특정 예를 들어 Oracle에 대 한 드라이버 Informix DBMS의 데이터에 직접 액세스할 수 없습니다. 기본 Dbms;의 기능을 제공 하는 드라이버 DBMS에 의해 지원 되지 않습니다는 기능을 구현 하 필요는 없습니다. 예를 들어 외부 조인 다음 모두 기본 DBMS를 지원 하지 않는 경우 드라이버를 해야 합니다. 주 예외가 Xbase, 같은 독립 실행형 데이터베이스 엔진, 갖지 않는 Dbms에 대 한 드라이버 최소한 최소한 SQL의 사용을 지원 하는 데이터베이스 엔진을 구현 해야 합니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [드라이버 작업](../../odbc/reference/driver-tasks.md)  
  
-   [드라이버 아키텍처](../../odbc/reference/driver-architecture.md)  
  
## <a name="see-also"></a>관련 항목:  
 [Microsoft 제공 ODBC 드라이버](../../odbc/microsoft/microsoft-supplied-odbc-drivers.md)