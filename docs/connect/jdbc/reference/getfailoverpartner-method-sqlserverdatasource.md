---
title: getFailoverPartner 메서드 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39195742d8b6a2a03b0b2c835f47d0ba42735791
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730461"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>getFailoverPartner 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  데이터베이스 미러링 구성에 사용되는 장애 조치(Failover) 서버의 이름을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>반환 값  
 장애 조치(failover) 파트너의 이름이 들어 있는 **String**이며, 이름이 설정되어 있지 않은 경우 null입니다.  
  
## <a name="remarks"></a>Remarks  
 이 메서드에서 반환된 값은 [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) 메서드를 사용하여 설정된 장애 조치(failover) 파트너 이름을 반영합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
