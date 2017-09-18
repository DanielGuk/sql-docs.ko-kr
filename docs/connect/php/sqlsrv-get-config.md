---
title: sqlsrv_get_config | Microsoft Docs
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
- sqlsrv_get_config
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_get_config
- sqlsrv_get_config
ms.assetid: ce2befc2-af98-45bb-8d41-60f1674dccfc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5712c6f98da82b422e76a7cb6c8d07adac86b5e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsrvgetconfig"></a>sqlsrv_get_config
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

지정된 구성 설정의 현재 값을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_get_config( string $setting )  
```  
  
#### <a name="parameters"></a>매개 변수  
*$setting*: 값을 반환할 구성 설정입니다. 구성이 가능한 설정 목록을 보려면 [sqlsrv_configure](../../connect/php/sqlsrv-configure.md)를 참조하세요.  
  
## <a name="return-value"></a>반환 값  
*$setting* 매개 변수에서 지정한 설정 값입니다. 잘못된 설정이 지정된 경우 **false** 가 반환되고 오류가 오류 수집에 추가됩니다.  
  
## <a name="remarks"></a>주의  
경우 **false** 반환한 **sqlsrv_get_config**, 호출 해야 [sqlsrv_errors](../../connect/php/sqlsrv-errors.md) 아니면 오류가 발생 하는지 확인 하려면 **false** 는 지정한 설정의 값은 *$setting* 매개 변수입니다.  
  
## <a name="see-also"></a>관련 항목:  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)  
[sqlsrv_configure](../../connect/php/sqlsrv-configure.md)  
[sqlsrv_errors](../../connect/php/sqlsrv-errors.md)  
  
