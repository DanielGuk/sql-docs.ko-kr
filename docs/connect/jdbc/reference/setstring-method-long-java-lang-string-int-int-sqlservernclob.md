---
title: setString 메서드 (long, java.lang.String, int, int)-NClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58a26b71787e154acec6add71ecc868b438c2dec
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47810731"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString 메서드(long, java.lang.String, int, int)(SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 오프셋 및 길이에 따라 NCLOB의 지정된 위치에서부터 지정된 문자열을 씁니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *pos*  
  
 **NCLOB**에 쓰기 시작할 위치이며, 첫 번째 위치는 1입니다.  
  
 *str*  
  
 **NCLOB**에 쓸 문자열입니다.  
  
 *offset*  
  
 쓸 문자를 읽기 시작할 *str*의 오프셋입니다.  
  
 *len*  
  
 쓸 문자 수입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 이 setString 메서드로 java.sql.NClob 인터페이스의 setString 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerNClob 메서드](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 멤버](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 클래스](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
