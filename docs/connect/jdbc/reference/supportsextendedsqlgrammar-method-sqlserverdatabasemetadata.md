---
title: "supportsExtendedSQLGrammar 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.supportsExtendedSQLGrammar
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8deb1987-c4e3-4599-8e37-0a04ec20b480
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8f806bb459ba6fb5bdab1a2649f5871ddf252e3e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="supportsextendedsqlgrammar-method-sqlserverdatabasemetadata"></a>supportsExtendedSQLGrammar 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  이 데이터베이스에서 ODBC 확장 SQL 문법을 지원하는지 여부를 검색합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean supportsExtendedSQLGrammar()  
```  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 지원 되는 경우. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 supportsExtendedSQLGrammer 메서드는 java.sql.DatabaseMetaData 인터페이스의 supportsExtendedSQLGrammer 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  