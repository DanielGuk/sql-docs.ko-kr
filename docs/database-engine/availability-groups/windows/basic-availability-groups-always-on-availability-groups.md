---
title: 기본 가용성 그룹(Always On 가용성 그룹) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2018
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 285adbc7-ac9b-40f6-b4a9-3f1591d3b632
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: d20e1ce1c3a951e47861b68a819844528c104cbb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47771431"
---
# <a name="basic-availability-groups-always-on-availability-groups"></a>기본 가용성 그룹(Always On 가용성 그룹)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Always On 기본 가용성 그룹은 SQL Server 2016 및 SQL Server 2017 Standard Edition에 대한 고가용성 솔루션을 제공합니다. 기본 가용성 그룹은 단일 데이터베이스에 장애 조치(failover) 환경을 지원합니다. 기존의(고급) Enterprise Edition [Always On 가용성 그룹&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)과 매우 유사하게 생성 및 관리됩니다. 기본 가용성 그룹의 차이점과 제한 사항은 이 문서에 요약되어 있습니다.  
  
## <a name="features"></a>기능  
 Always On 기본 가용성 그룹은 더 이상 사용되지 않는 데이터베이스 미러링 기능을 대체하며 비슷한 수준의 기능 지원을 제공합니다. 기본 가용성 그룹은 주 데이터베이스를 사용하여 단일 복제본을 유지 관리합니다. 이 복제본은 동기 커밋 모드 또는 비동기 커밋 모드를 사용할 수 있습니다. 가용성 모드에 대한 자세한 내용은 [가용성 모드&#40;Always On 가용성 그룹&#41;](../../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)를 참조하세요. 보조 복제본은 장애 조치(Failover)를 취할 필요가 없다면 비활성 상태로 유지됩니다. 장애 조치(failover)는 주 역할 할당과 보조 역할 할당을 뒤바꿔서 보조 복제본이 주 활성 데이터베이스가 되도록 합니다. 장애 조치에 대한 자세한 내용은 [장애 조치(Failover) 및 장애 조치(Failover) 모드&#40;Always On 가용성 그룹&#41;](../../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)를 참조하세요. 기본 가용성 그룹은 온-프레미스와 Microsoft Azure를 포괄하는 하이브리드 환경에서 작동이 가능합니다.  
  
## <a name="limitations"></a>제한 사항  
 기본 가용성 그룹은 SQL Server 2016 Enterprise Edition의 고급 가용성 그룹에 비해 기능의 하위 집합을 사용합니다. 기본 가용성 그룹에는 다음과 같은 제한 사항이 포함됩니다.  
  
- 두 개의 복제본(주 및 보조)으로 제한됩니다.  
  
- 보조 복제본에 대한 읽기 권한이 없습니다.  
  
- 보조 복제본에 대한 백업이 없습니다.  

- 보조 복제본에 대한 무결성 검사가 없습니다. 

- SQL Server 2016 CTP3(Community Technology Preview 3) 이전 버전의 SQL Server를 실행하는 서버에서 호스팅되는 복제본은 지원되지 않습니다.  

- 하나의 가용성 데이터베이스가 지원됩니다.  
  
- 기본 가용성 그룹은 고급 가용성 그룹으로 업그레이드할 수 없습니다. 그룹을 삭제하고 SQL Server 2016 Enterprise Edition에서만 실행되는 서버를 포함하는 그룹에 다시 추가해야 합니다.  
  
- 기본 가용성 그룹은 Standard Edition 서버에 대해서만 지원됩니다. 

- 기본 가용성 그룹은 분산 가용성 그룹의 일부가 될 수 없습니다. 
  
## <a name="configuration"></a>Configuration  
 Always On 기본 가용성 그룹은 두 개의 SQL Server 2016 Standard Edition 서버에서 만들 수 있습니다. 기본 가용성 그룹을 만드는 경우에는, 만드는 동안 두 개의 복제본을 모두 지정해야 합니다.  
  
 기본 가용성 그룹을 만들려면 **CREATE AVAILABILITY GROUP** transact-SQL 명령을 사용하고 **WITH BASIC** 옵션을 지정합니다(기본값: **ADVANCED**). 17.8 버전부터 SQL Server Management Studio에서 UI를 사용하여 기본 가용성 그룹을 만들 수도 있습니다. 자세한 내용은 [CREATE AVAILABILITY GROUP&#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)을 참조하세요. 
  
> [!NOTE]  
>  기본 가용성 그룹에 대한 제한 사항은 **WITH BASIC** 가 지정된 경우 **CREATE AVAILABILITY GROUP** 명령에 적용됩니다. 예를 들어, 읽기 액세스를 허용하는 기본 가용성 그룹을 만들려고 하면 오류가 발생합니다. 그 밖의 제한 사항이 동일한 방식으로 적용됩니다. 자세한 내용은 이 문서의 제한 사항 섹션을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
