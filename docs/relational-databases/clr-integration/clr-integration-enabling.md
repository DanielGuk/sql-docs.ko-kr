---
title: CLR 통합을 사용 하도록 설정 | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 0e39d3805ea89f6f8bbf7a48488fc536796312b4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653351"
---
# <a name="clr-integration---enabling"></a>CLR 통합 - 사용
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  CLR(공용 언어 런타임) 통합 기능은 기본적으로 해제되어 있으며 CLR 통합을 사용하여 구현된 개체를 사용하려면 이 기능을 설정해야 합니다. CLR 통합을 사용 하도록 설정 하려면 사용 합니다 **clr** 옵션을 합니다 **sp_configure** 저장 프로시저 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:  
  
```sql  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 CLR 통합을 사용 하지 않도록 설정 하 여 수를 **clr** 옵션을 0입니다. CLR 통합 기능을 해제하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 모든 CLR 루틴 실행을 중지하고 모든 응용 프로그램 도메인을 언로드합니다.  
  
> [!NOTE]  
>  CLR 통합을 사용 하려면 ALTER SETTINGS 서버 수준 사용 권한은의 멤버에 의해 암시적 보유 하 고 있어야 합니다 **sysadmin** 하 고 **serveradmin** 고정 서버 역할입니다.  
  
> [!NOTE]  
>  많은 양의 메모리와 많은 수의 프로세서가 구성되어 있는 컴퓨터에서는 서버를 시작할 때 SQL Server의 CLR 통합 기능을 로드하지 못할 수 있습니다. 이 문제를 해결 하기 위해 사용 하 여 서버를 시작 합니다 **-gmemory_to_reserve** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스 시작 옵션 및 충분히 큰 메모리 값을 지정 합니다. 자세한 내용은 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)을(를) 참조하세요.  
  
> [!NOTE]  
>  경량 풀링에서는 CLR(공용 언어 런타임) 실행이 지원되지 않습니다. CLR 통합 기능을 설정하려면 먼저 경량 풀링 기능을 해제해야 합니다. 자세한 내용은 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled 서버 구성 옵션](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [RECONFIGURE&#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [GRANT&#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [서버 수준 역할](../../relational-databases/security/authentication-access/server-level-roles.md)  
  
  
