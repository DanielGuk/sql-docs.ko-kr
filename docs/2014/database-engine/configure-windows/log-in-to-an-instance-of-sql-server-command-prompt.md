---
title: SQL Server 인스턴스에 로그인(명령 프롬프트) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- logins [SQL Server], named instance of SQL Server
- log ins [SQL Server]
- logins [SQL Server], default instance of SQL Server
- command prompt [SQL Server], logins
- logging in [SQL Server]
ms.assetid: f67c11e3-c519-40c9-82c1-07efa9d9985e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d6ba115fef26547528175e012322c1043f019211
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48067983"
---
# <a name="log-in-to-an-instance-of-sql-server-command-prompt"></a>SQL Server 인스턴스에 로그인(명령 프롬프트)
  이 항목에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에 대한 연결을 테스트하고 **sqlcmd** 유틸리티를 사용하는 방법에 대해 설명합니다.  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-log-in-to-the-default-instance-of-sql-server"></a>SQL Server의 기본 인스턴스에 로그인하려면  
  
1.  명령 프롬프트에서 다음 명령을 입력하여 Windows 인증을 통해 연결합니다.  
  
    ```  
    sqlcmd [ /E ] [ /S servername ]  
  
    ```  
  
#### <a name="to-log-in-to-a-named-instance-of-sql-server"></a>SQL Server의 명명된 인스턴스에 로그인하려면  
  
1.  명령 프롬프트에서 다음 명령을 입력하여 Windows 인증을 통해 연결합니다.  
  
    ```  
    sqlcmd [ /E ] /S servername\instancename  
  
    ```  
  
## <a name="see-also"></a>관련 항목  
 [sqlcmd 유틸리티](../../tools/sqlcmd-utility.md)   
 [osql 유틸리티](../../tools/osql-utility.md)  
  
  
