---
title: "supportsStoredFunctionsUsingCallSyntax 메서드 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e5c0579-84b5-4717-b128-0bcd512f6022
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: de585c13ec1d8234cdf9087525b2eb1c8c2e99ed
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="supportsstoredfunctionsusingcallsyntax-method-sqlserverdatabasemetadata"></a>supportsStoredFunctionsUsingCallSyntax 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  현재 데이터베이스에서 저장 프로시저 이스케이프 구문을 사용하여 사용자 정의 또는 공급업체 정의 함수를 호출할 수 있는지 여부를 나타냅니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean supportsStoredFunctionsUsingCallSyntax()  
```  
  
## <a name="return-value"></a>반환 값  
 **true 이면** 지원 되는 경우. 그렇지 않으면 **false**입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 supportsStoredFunctionsUsingCallSyntax 메서드는 java.sql.DatabaseMetaData 인터페이스의 supportsStoredFunctionsUsingCallSyntax 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  