---
title: getTrustServerCertificate 메서드 (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- getTrustServerCertificate Method (SQLServerDataSource)
apilocation:
- getTrustServerCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: e4f443cc-b5d7-4859-81df-836a8642ed07
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 008b0c0263ec73f0f316820c92ba5d70ca286d62
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745531"
---
# <a name="gettrustservercertificate-method-sqlserverdatasource"></a>getTrustServerCertificate 메서드(SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  trustServerCertificate 속성이 사용되는지 여부를 나타내는 **Boolean** 값을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
public boolean getTrustServerCertificate()  
```  
  
## <a name="return-value"></a>반환 값  
 trustServerCertificate가 사용되면 **true**이고, 그렇지 않으면 **false**입니다.  
  
## <a name="remarks"></a>Remarks  
 trustServerCertificate 속성이 **true**로 설정되어 있으면 통신 계층이 SSL을 사용하여 암호화된 경우 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL(Secure Sockets Layer) 인증서가 자동으로 트러스트됩니다. 즉, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 인증서의 유효성을 검사하지 않습니다. 기본 값은 **false**입니다.  
  
 trustServerCertificate 속성이 **false**로 설정되어 있으면 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]에서는 서버 SSL 인증서의 유효성을 검사합니다.  
  
## <a name="see-also"></a>참고 항목  
 [SQLServerDataSource 멤버](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 클래스](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
