---
title: "setClob 메서드 (int, java.io.Reader) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b3727da-0480-4cea-b8b1-abda90699b84
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 15e98db2d71d49aba4484ea3f5e40e5099282a7d
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="setclob-method-int-javaioreader"></a>setClob 메서드(int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  지정된 된 Reader 개체를 지정된 된 매개 변수를 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public final void setClob(int parameterIndex,  
                          java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>매개 변수  
 *parameterIndex*  
  
 **int** 매개 변수 인덱스를 나타내는입니다.  
  
 *판독기*  
  
 판독기 개체입니다.  
  
## <a name="exceptions"></a>예외  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>주의  
 이 setClob 메서드는 java.sql.PreparedStatement 인터페이스의 setClob 메서드에 의해 지정 됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [setClob 메서드 &#40; SQLServerPreparedStatement &#41;](../../../connect/jdbc/reference/setclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 멤버](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  