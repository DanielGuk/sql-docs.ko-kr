---
title: "getXAConnection 메서드 () | Microsoft Docs"
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
- SQLServerXADataSource.getXAConnection ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b2710613-78b1-438f-b996-c7ae6f34381a
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6fd5681b0ece55e113d03c9ee21950f1cae19f43
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getxaconnection-method-"></a>getXAConnection 메서드()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  분산 트랜잭션에 사용할 수 있는 실제 데이터베이스 연결을 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public javax.sql.XAConnection getXAConnection()  
```  
  
## <a name="return-value"></a>반환 값  
 XAConnection 개체입니다.  
  
## <a name="exceptions"></a>예외  
 java.sql.SQLException  
  
## <a name="remarks"></a>주의  
 이 getXAConnection 메서드는 javax.sql.XADataSource 인터페이스의 getXAConnection 메서드에 의해 지정 됩니다.  
  
> [!NOTE]  
>  이 메서드는 일반적으로 XA 연결 풀 구현에서 호출되며 일반적인 JDBC 응용 프로그램 코드에서는 호출되지 않습니다.  
  
## <a name="see-also"></a>관련 항목:  
 [getXAConnection 메서드 &#40; SQLServerXADataSource &#41;](../../../connect/jdbc/reference/getxaconnection-method-sqlserverxadatasource.md)   
 [SQLServerXADataSource 메서드](../../../connect/jdbc/reference/sqlserverxadatasource-methods.md)   
 [SQLServerXADataSource 멤버](../../../connect/jdbc/reference/sqlserverxadatasource-members.md)   
 [SQLServerXADataSource 클래스](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)  
  
  