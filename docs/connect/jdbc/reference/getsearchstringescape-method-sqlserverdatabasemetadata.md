---
title: "getSearchStringEscape 메서드 (SQLServerDatabaseMetaData) | Microsoft Docs"
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
- SQLServerDatabaseMetaData.getSearchStringEscape
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ea0f95d0-0238-4dc8-9f26-7ff9b65f30c3
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f1008cd0fdec7aa60d9d66c62cfb08ad84ca1cd5
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="getsearchstringescape-method-sqlserverdatabasemetadata"></a>getSearchStringEscape 메서드(SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  검색 된 **문자열** 와일드 카드 문자를 이스케이프를 사용할 수 있는 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public java.lang.String getSearchStringEscape()  
```  
  
## <a name="return-value"></a>반환 값  
 A **문자열** 문자열 이스케이프 와일드 카드 문자가 포함 됩니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 getSearchStringEscape 메서드는 java.sql.DatabaseMetaData 인터페이스의 getSearchStringEscape 메서드에 의해 지정 됩니다.  
  
 이 메서드는 메타데이터 패턴 검색에만 사용되며 반환 "\\"입니다. A **문자열** 검색 패턴에서 와일드 카드 ("%" 및 "_")를 이스케이프 하 고 백슬래시 앞에 추가 하 여 리터럴로 제공할 수 있습니다. 이것은 "\\%" "[%]" 및 "\\\_"를 "[\_]"입니다.  
  
## <a name="see-also"></a>관련 항목:  
 [SQLServerDatabaseMetaData 메서드](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 멤버](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 클래스](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  