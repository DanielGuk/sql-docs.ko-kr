---
title: "데이터베이스 미러링 - Always On 가용성 그룹 - PowerShell | Microsoft Docs"
ms.custom: 
ms.date: 05/17/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], endpoint
ms.assetid: 6197bbe7-67d4-446d-ba5f-cabfa5df77f1
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 24895c94afd7c43be75d2fcf7f914cebc370497c
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="database-mirroring---always-on-availability-groups--powershell"></a>데이터베이스 미러링 - Always On 가용성 그룹 - PowerShell
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  이 항목에서는 PowerShell을 사용하여 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 에서 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 에 사용할 데이터베이스 미러링 끝점을 만드는 방법에 대해 설명합니다.  
  
 **항목 내용**  
  
-   **시작하기 전 주의 사항:**  [보안](#Security)  
  
-   **데이터베이스 미러링 끝점을 만드는 데 사용되는 도구:**  [PowerShell](#PowerShellProcedure)  
  
## <a name="before-you-begin"></a>시작하기 전에  
  
###  <a name="Security"></a> 보안  
  
> [!IMPORTANT]  
>  RC4 알고리즘은 더 이상 사용되지 않습니다. [!INCLUDE[ssNoteDepFutureDontUse](../../../includes/ssnotedepfuturedontuse-md.md)] AES를 사용하는 것이 좋습니다.  
  
####  <a name="Permissions"></a> 사용 권한  
 CREATE ENDPOINT 권한 또는 sysadmin 고정 서버 역할의 멤버 자격이 필요합니다. 자세한 내용은 [GRANT 끝점 사용 권한&#40;Transact-SQL&#41;](../../../t-sql/statements/grant-endpoint-permissions-transact-sql.md)을 참조하세요.  
  
##  <a name="PowerShellProcedure"></a> PowerShell 사용  
 **데이터베이스 미러링 끝점을 만들려면**  
  
1.  데이터베이스 미러링 끝점을 만들 서버 인스턴스로 디렉터리를 변경(**cd**)합니다.  
  
2.  **New-SqlHadrEndpoint** cmdlet을 사용하여 끝점을 만든 다음 **Set-SqlHadrEndpoint** 를 사용하여 끝점을 시작합니다.  
  
###  <a name="PShellExample"></a> 예제(PowerShell)  
 다음 PowerShell 명령은 SQL Server 인스턴스(*Machine*\\*Instance*)에 데이터베이스 미러링 끝점을 만듭니다. 이 끝점은 포트 5022를 사용합니다.  
  
> [!IMPORTANT]  
>  이 예는 데이터베이스 미러링 끝점이 현재 없는 서버 인스턴스에서만 작동합니다.  
  
```  
# Create the endpoint.  
$endpoint = New-SqlHadrEndpoint MyMirroringEndpoint -Port 5022 -Path SQLSERVER:\SQL\Machine\Instance  
  
# Start the endpoint  
Set-SqlHadrEndpoint -InputObject $endpoint -State "Started"  
  
```  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
 **데이터베이스 미러링 끝점을 구성하려면**  
  
-   [Windows 인증에 대한 데이터베이스 미러링 끝점 만들기&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [데이터베이스 미러링 끝점에 대한 인증서 사용&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
    -   [데이터베이스 미러링 끝점의 아웃바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
    -   [데이터베이스 미러링 끝점의 인바운드 연결에 대한 인증서 사용 허용&#40;Transact-SQL&#41;](../../../database-engine/database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)  
  
-   [서버 네트워크 주소 지정&#40;데이터베이스 미러링&#41;](../../../database-engine/database-mirroring/specify-a-server-network-address-database-mirroring.md)  
  
-   [가용성 복제본 추가 또는 수정 시 끝점 URL 지정&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 **데이터베이스 미러링 끝점에 대한 정보를 보려면**  
  
-   [sys.database_mirroring_endpoints&#40;Transact-SQL&#41;](../../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)  
  
## <a name="see-also"></a>참고 항목  
 [가용성 그룹 만들기&#40;Transact-SQL&#41;](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)   
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
