---
title: "allTablesAreSelectable 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs"
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
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d605d9c9725c5819af595115292e1cc3752ec0c
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>allTablesAreSelectable 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  현재 사용자에 의해 반환 되는 모든 테이블을 사용 하는 권한이 있는지 여부를 검색 된 [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) SELECT 문에서 메서드.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 사용자에 게 권한이를 호출 하는 경우 모든 테이블을 사용 합니다. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 allTablesAreSelectable 메서드는 java.sql.DatabaseMetaData 인터페이스의 allTablesAreSelectable 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  