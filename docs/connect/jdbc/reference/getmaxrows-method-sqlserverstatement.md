---
title: "getMaxRows 메서드 (SQLServerStatement) | Microsoft Docs"
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
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d9f64d60a08727f239ca3eee4354fc094e06107a
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows 메서드 (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  행의 최대 수를 검색 하는 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 이 생성 되는 개체 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 개체에 포함 될 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>반환 값  
 **int** 행 또는 0의 최대 수 있는지 여부를 나타내는 제한이 없습니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getMaxRows 메서드는 java.sql.Statement 인터페이스의 getMaxRows 메서드에 의해 지정 됩니다.  
  
 이 getMaxRows 메서드는 항상 동적 스크롤 가능 커서에 대해 0을 반환합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerStatement 멤버](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 클래스](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  