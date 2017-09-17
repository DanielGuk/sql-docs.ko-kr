---
title: "드라이버 버전 가져오기 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e241d72-16da-4ada-ac67-e6308394108f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2322c3ece650fb05fe19fd55e36f79e73db7d32d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getting-the-driver-version"></a>드라이버 버전 가져오기
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  설치 된 버전 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 에서 다음과 같은 방법으로 확인할 수 있습니다.  
  
-   호출 된 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) 메서드 [getDriverMajorVersion](../../connect/jdbc/reference/getdrivermajorversion-method-sqlserverdatabasemetadata.md), [getDriverMinorVersion](../../connect/jdbc/reference/getdriverminorversion-method-sqlserverdatabasemetadata.md), 또는 [getDriverVersion](../../connect/jdbc/reference/getdriverversion-method-sqlserverdatabasemetadata.md)합니다.  
  
-   버전은 제품 배포의 readme.txt 파일에 표시됩니다.  
  
 JDBC 드라이버 이름은에서 반환할 수는 또한는 [getDriverName](../../connect/jdbc/reference/getdrivername-method-sqlserverdatabasemetadata.md) SQLServerDatabaseMetaData 클래스에 메서드를 호출 합니다. 예를 들어 이 메서드는 "SQL Server용 Microsoft JDBC Driver 4.0"을 반환합니다.  
  
 다음은 SQLServerDatabaseMetaData 클래스의 메서드를 호출에서 출력의 예입니다.  
  
 `getDriverName = Microsoft JDBC Driver 4.0 for SQL Server`  
  
 `getDriverMajorVersion = 4`  
  
 `getDriverMinorVersion = 0`  
  
 `getDriverVersion = 4.0.`*xxx.x*  
  
 여기서 "xxx.x"는 최종 버전 번호입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [JDBC 드라이버 관련 문제 진단](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  