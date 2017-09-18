---
title: "ChangePassword 메서드 (ADOX) | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
apitype: COM
f1_keywords:
- _User25::raw_ChangePassword
- _User25::ChangePassword
helpviewer_keywords:
- ChangePassword method [ADOX]
ms.assetid: d187fbc6-5fac-4abb-803d-bf344dcf0302
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 18dd53bc701cf6a4b77c8e77f5b1851aff57f2ba
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="changepassword-method-adox"></a>ChangePassword 메서드 (ADOX)
암호를 변경 하면는 [사용자](../../../ado/reference/adox-api/user-object-adox.md) 계정.  
  
## <a name="syntax"></a>구문  
  
```  
  
User.ChangePassword OldPassword, NewPassword  
```  
  
#### <a name="parameters"></a>매개 변수  
 *OldPassword*  
 A **문자열** 기존 사용자의 암호를 지정 하는 값입니다. 없으면 사용자 현재 암호를 사용 하 여 빈 문자열 ("")에 대 한 *OldPassword*합니다.  
  
 *새 암호*  
 A **문자열** 새 암호를 지정 하는 값입니다.  
  
## <a name="remarks"></a>주의  
 보안상의 이유로 새 암호 외에도 이전 암호를 지정 해야 합니다.  
  
 공급자 트러스트를 받을 대상 속성의 관리를 지원 하지 않는 경우 오류가 발생 합니다.  
  
## <a name="applies-to"></a>적용 대상  
 [User 개체(ADOX)](../../../ado/reference/adox-api/user-object-adox.md)  
  
## <a name="see-also"></a>관련 항목:  
 [Groups 및 Users Append, ChangePassword 메서드 예제(VB)](../../../ado/reference/adox-api/groups-and-users-append-changepassword-methods-example-vb.md)