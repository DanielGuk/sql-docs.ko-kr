---
title: "분산 가용성 그룹(SQL Server) | Microsoft Docs"
ms.custom: 
ms.date: 06/20/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-high-availability
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Availability Groups [SQL Server], distributed
ms.assetid: 
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: f1d8e15bcdbf3d9fa8ccb4b3fc92c309b8f11055
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="distributed-availability-groups"></a>분산 가용성 그룹

분산 가용성 그룹은 기존의 Always On 가용성 그룹 기능의 변형으로서 SQL Server 2016에서 도입된 새로운 기능입니다. 이 문서에서는 분산 가용성 그룹의 몇 가지 측면을 명확히 하고 기존 [SQL Server 설명서](https://docs.microsoft.com/en-us/sql/sql-server/sql-server-technical-documentation)를 보완합니다.

> [!NOTE]
> "DAG"는 Exchange 데이터베이스 가용성 그룹 기능에 대한 약어로 이미 사용되고 있으므로 *분산 가용성 그룹*에 대한 공식적인 약어가 아닙니다. 이 Exchange 기능은 SQL Server 가용성 그룹 또는 분산 가용성 그룹과는 관련이 없습니다.

분산 가용성 그룹을 구성하려면 [분산 가용성 그룹 구성](configure-distributed-availability-groups.md)을 참조하세요.

## <a name="understand-distributed-availability-groups"></a>분산 가용성 그룹 이해

분산 가용성 그룹은 별도의 두 가용성 그룹에 걸쳐 있는 특별한 유형의 가용성 그룹입니다. 기본 가용성 그룹은 서로 다른 두 WSFC(Windows Server 장애 조치 클러스터링)에서 구성됩니다. 분산 가용성 그룹에 참여하는 가용성 그룹은 동일한 위치에 있을 필요는 없습니다. 실제, 가상, 온-프레미스, 공용 클라우드 또는 가용성 그룹 배포를 지원하는 모든 위치에 있을 수 있습니다. 두 가용성 그룹이 통신할 수 있는 한 이러한 가용성 그룹을 포함한 분산 가용성 그룹을 구성할 수 있습니다.

기존 가용성 그룹에는 WSFC 클러스터에 구성된 리소스가 있습니다. 분산 가용성 그룹은 WSFC 클러스터에 아무 것도 구성하지 않습니다. 분산 가용성 그룹에 관한 모든 항목은 SQL Server 내에서 유지 관리됩니다. 분산 가용성 그룹에 대한 정보를 확인하는 방법은 [분산 가용성 그룹 정보 보기](#viewing-distributed-availability-group-information)를 참조하세요. 

분산 가용성 그룹의 경우 기본 가용성 그룹에 수신기가 있어야 합니다. 기존 가용성 그룹에서와 같이 독립 실행형 인스턴스에 대한 기본 서버 이름(또는 SQL Server FCI(장애 조치 클러스터 인스턴스)의 경우 네트워크 이름 리소스와 연결된 값)을 제공하는 대신, 매개 변수를 만들 때 ENDPOINT_URL 매개 변수를 사용하여 분산 가용성 그룹에 대해 구성된 수신기를 지정합니다. 분산 가용성 그룹의 기본 가용성 그룹마다 수신기가 있지만, 분산 가용성 그룹에는 수신기가 없습니다.

다음 그림에서는 각각 고유한 WSFC 클러스터에 구성된 두 개의 가용성 그룹 (AG 1 및 AG 2)에 걸친 분산 가용성 그룹의 고급 수준을 보여 줍니다. 분산 가용성 그룹에는 총 4개의 복제본이 있으며, 각 가용성 그룹에는 2개의 복제본이 있습니다. 각 가용성 그룹마다 최대 수의 복제본을 지원할 수 있으므로 Standard Edition 기반 분산 가용성 그룹에는 최대 4개의 복제본이 있고, Enterprise Edition 기반 분산 가용성 그룹에는 최대 18개의 복제본이 있을 수 있습니다.

<a name="fig1"></a> ![분산 가용성 그룹에 대한 상위 수준 보기][1]

분산 가용성 그룹에서 데이터 이동을 동기 또는 비동기로 구성할 수 있습니다. 그러나 데이터 이동은 기존 가용성 그룹에 비해 분산 가용성 그룹 내에서 약간 다릅니다. 각 가용성 그룹에는 하나의 주 복제본이 있지만 삽입, 업데이트 및 삭제를 허용할 수 있는 분산 가용성 그룹에 참여하는 데이터베이스 복사본은 하나만 있습니다. 다음 그림에서 보여 주듯이 AG 1은 주 가용성 그룹입니다. 주 복제본은 AG 1의 보조 복제본과 AG 2의 주 복제본 모두로 트랜잭션을 보냅니다. 그런 다음 AG 2의 주 복제본은 AG 2의 보조 복제본을 계속 업데이트합니다. 


![분산 가용성 그룹 및 데이터 이동][2]

AG 2의 주 복제본에서 삽입, 업데이트 및 삭제할 수 있도록 하는 유일한 방법은 AG 1에서 분산 가용성 그룹을 수동으로 장애 조치하는 것입니다. 앞의 그림에서 AG 1에는 쓰기 가능한 데이터베이스 복사본이 있으므로, 장애 조치를 실행하면 AG 2는 삽입, 업데이트 및 삭제를 처리할 수 있는 가용성 그룹이 됩니다. 하나의 분산 가용성 그룹을 다른 그룹으로 장애 조치하는 방법에 대한 자세한 내용은 [보조 가용성 그룹으로 장애 조치]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups)를 참조하세요.

> [!NOTE]
> SQL Server 2016의 분산 가용성 그룹은 FORCE_FAILOVER_ALLOW_DATA_LOSS 옵션을 사용하여 하나의 가용성 그룹에서 다른 그룹으로의 장애 조치만 지원합니다.

## <a name="sql-server-version-and-edition-requirements-for-distributed-availability-groups"></a>분산 가용성 그룹에 대한 SQL Server 버전 및 버전 요구 사항

분산 가용성 그룹은 현재 동일한 주요 SQL Server 버전으로 만든 가용성 그룹에서만 작동합니다. 예를 들어 분산 가용성 그룹에 참여하는 모든 가용성 그룹은 현재 SQL Server 2016을 사용하여 만들어야 합니다. SQL Server 2012 또는 2014에는 분산 가용성 그룹 기능이 없으므로 이러한 버전으로 만든 가용성 그룹은 분산 가용성 그룹에 참여할 수 없습니다. 

> [!NOTE]
> 분산 가용성 그룹은 Standard 또는 Enterprise 버전으로 구성할 수 있지만, 분산 가용성 그룹에서 버전을 혼합하는 것은 지원되지 않습니다.

별도의 두 개 가용성 그룹이 있으므로 분산 가용성 그룹에 참여하는 복제본에 서비스 팩 또는 누적 업데이트를 설치하는 프로세스는 기존 가용성 그룹과는 약간 다릅니다.

1. 먼저 분산 가용성 그룹에서 두 번째 가용성 그룹의 복제본을 업데이트함으로써 시작합니다.

2. 분산 가용성 그룹에서 주 가용성 그룹의 복제본을 패치합니다.

3. 표준 가용성 그룹과 마찬가지로, 주 가용성 그룹을 자체 복제본 중 하나(보조 가용성 그룹의 주 가용성 그룹이 아님)로 장애 조치하고 패치합니다. 주 복제본 이외의 복제본이 없으면 두 번째 가용성 그룹으로의 수동 장애 조치가 필요합니다.

> [!NOTE]
> SQL Server의 이후 버전에서는 이전 버전이 동일한 분산 가용성 그룹에 참여할 수 있는지에 대해 발표하지 않았습니다. 이 시나리오를 사용하도록 설정한 경우 분산 가용성 그룹은 SQL Server 버전 업그레이드 계획의 일부가 될 수 있습니다.

### <a name="windows-server-versions-and-distributed-availability-groups"></a>Windows Server 버전 및 분산 가용성 그룹

분산 가용성 그룹은 여러 가용성 그룹에 걸쳐 있고, 각각 고유한 기본 WSFC 클러스터에 있으며, SQL Server 전용 구조입니다.  즉, 개별 가용성 그룹을 포함하는 WSFC 클러스터에는 서로 다른 주요 버전의 Windows Server가 있을 수 있습니다. 이전 섹션에서 설명한 대로 SQL Server의 주요 버전은 동일해야 합니다. 다음 그림에서는 [첫 번째 그림](#fig1)과 매우 비슷하게 분산 가용성 그룹에 참여하는 AG 1 및 AG 2를 보여 주지만, 각 WSFC 클러스터는 서로 다른 버전의 Windows Server입니다.


![서로 다른 버전의 Windows Server를 사용하는 WSFC 클러스터에 포함된 분산 가용성 그룹][3]

개별 WSFC 클러스터와 해당 가용성 그룹은 기존 규칙을 따릅니다. 즉, 도메인에 조인되거나 조인되지 않을 수 있습니다(Windows Server 2016 이상). 서로 다른 두 가용성 그룹을 하나의 분산 가용성 그룹에 결합하는 경우 다음 네 가지 시나리오가 있습니다.

* 두 WSFC 클러스터가 모두 동일한 도메인에 가입됩니다.
* 각 WSFC 클러스터마다 서로 다른 도메인에 가입됩니다.
* 한 WSFC 클러스터는 도메인에 가입되고, 다른 하나의 WSFC 클러스터는 도메인에 가입되지 않습니다.
* 두 WSFC 클러스터가 모두 도메인에 가입되지 않습니다.

두 WSFC 클러스터가 모두 동일한 도메인(트러스트된 도메인이 아님)에 가입된 경우 분산 가용성 그룹을 만들 때 별도의 작업을 수행할 필요가 없습니다. 동일한 도메인에 가입되지 않은 가용성 그룹 및 WSFC 클러스터의 경우, 도메인 독립 가용성 그룹에 대한 가용성 그룹을 만드는 방식과 같이 인증서를 사용하여 분산 가용성 그룹을 작동하도록 합니다. 분산 가용성 그룹에 대한 인증서를 구성하는 방법을 알아보려면 [도메인 독립 가용성 그룹 만들기](domain-independent-availability-groups.md#create-a-domain-independent-availability-group)의 3-13 단계를 수행합니다.

분산 가용성 그룹을 사용하는 경우 주 가용성 그룹 각각의 주 복제본에는 서로의 인증서가 있어야 합니다. 인증서를 사용하지 않는 끝점이 이미 있는 경우 [ALTER ENDPOINT](https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-endpoint-transact-sql)를 사용하여 인증서 사용을 반영하도록 해당 끝점을 재구성합니다.

## <a name="distributed-availability-group-usage-scenarios"></a>분산 가용성 그룹 사용 시나리오

분산 가용성 그룹을 사용하는 세 가지 주요 시나리오는 다음과 같습니다. 

* [재해 복구 및 더 쉬운 다중 사이트 구성](#disaster-recovery-and-multi-site-scenarios)
* [새 하드웨어 또는 구성으로 마이그레이션(새 하드웨어 사용, 기본 운영 체제 변경 등)](#migration-using-a-distributed-availability-group)
* [여러 가용성 그룹을 확장하여 단일 가용성 그룹에서 읽기 가능한 복제본 수를 8개 이상으로 늘리는 경우](#scaling-out-readable-replicas-with-distributed-accessibility-groups)

### <a name="disaster-recovery-and-multi-site-scenarios"></a>재해 복구 및 다중 사이트 시나리오

기존 가용성 그룹에서는 모든 서버가 동일한 WSFC 클러스터에 속해야 하므로 여러 데이터 센터를 확장할 수 있습니다. 다음 그림에서는 데이터 흐름을 포함하여 기존 다중 사이트 가용성 그룹에 대한 아키텍처를 보여 줍니다. 모든 보조 복제본에 트랜잭션을 보내는 주 복제본이 하나만 있습니다. 이 구성은 몇 가지 방식에서 분산 가용성 그룹보다 덜 효율적입니다. 예를 들어 Active Directory(해당하는 경우) 및 WSFC 클러스터의 쿼럼에 대한 미러링 모니터 서버와 같은 항목을 구현해야 합니다. 또한 노드 응답 변경과 같이 WSFC 클러스터의 다른 측면을 고려해야 할 수도 있습니다.

![기존 다중 사이트 가용성 그룹][4]

분산 가용성 그룹은 여러 데이터 센터에 걸쳐 있는 가용성 그룹에 대해 더 유연한 배포 시나리오를 제공합니다. 이전에 [로그 전달]( https://docs.microsoft.com/en-us/sql/database-engine/log-shipping/about-log-shipping-sql-server)과 같은 기능을 사용한 분산 가용성 그룹도 사용할 수 있습니다. 그러나 기존 가용성 그룹과 달리 분산 가용성 그룹은 트랜잭션 적용을 지연할 수 없습니다. 즉, 데이터를 잘못 업데이트하거나 삭제하는 사용자의 실수가 발생하는 경우 가용성 그룹 또는 분산 가용성 그룹에서 도움을 줄 수 없습니다.

분산 가용성 그룹은 느슨하게 결합되어 있으며, 이 경우 단일 WSFC 클러스터가 필요하지 않으며 SQL Server에서 유지 관리됩니다. WSFC 클러스터는 개별적으로 유지 관리되며 동기화는 주로 두 개의 가용성 그룹 간에 비동기이므로 다른 사이트에서 재해 복구를 구성하는 것이 더 쉽습니다. 각 가용성 그룹의 주 복제본은 자체의 보조 복제본을 동기화합니다.

* 분산 가용성 그룹에 대해서는 수동 장애 조치만 지원됩니다. 데이터 센터를 전환하는 재해 복구 상황에서는 자동 장애 조치를 구성하면 안됩니다(드문 경우는 제외). 
* CrossSubnetThreshold와 같이 다중 사이트 또는 서브넷 WSFC 클러스터에 대한 기존 항목 또는 매개 변수 중 일부를 설정할 필요는 거의 없지만, 데이터 전송을 위해 다른 계층의 네트워크 대기 시간은 여전히 확인해야 합니다. 차이점은 각 WSFC 클러스터마다 자체의 가용성을 유지한다는 것입니다. 클러스터는 4개 노드로 구성된 하나의 큰 엔터티가 아닙니다. 앞의 그림과 같이 별도의 2개 노드 WSFC 클러스터 두 개가 있습니다.  
* 이 방법은 재난 복구를 위해 사용되므로 비동기 데이터 이동을 사용하는 것이 좋습니다.
* 주 복제본과 두 번째 가용성 그룹에 속한 보조 복제본 중 하나 이상의 복제본 간에 동기 데이터 이동을 구성하고 분산 가용성 그룹에서 동기 데이터 이동을 구성하는 경우, 분산 가용성 그룹은 모든 동기 복사본에서 해당 데이터를 가지고 있다고 승인할 때까지 대기합니다.

### <a name="migrate-by-using-a-distributed-availability-group"></a>분산 가용성 그룹을 사용하여 마이그레이션

분산 가용성 그룹은 서로 완전히 다른 두 가지 가용성 그룹 구성을 지원하므로 재해 복구 및 다중 사이트 시나리오뿐만 아니라 마이그레이션 시나리오도 사용할 수 있습니다. 새 하드웨어 또는 가상 컴퓨터(공용 클라우드의 온-프레미스 또는 IaaS)로 마이그레이션하는 경우, 분산 가용성 그룹을 구성하면 이전에 백업, 복사 및 복원 또는 로그 전달을 사용했던 마이그레이션이 발생할 수 있습니다. 

마이그레이션 기능은 동일한 SQL Server 버전을 유지하면서 기본 OS를 변경하거나 업그레이드하는 시나리오에서 특히 유용합니다. Windows Server 2016은 동일한 하드웨어에서 Windows Server 2012 R2의 롤링 업그레이드를 허용하지만, 대부분의 사용자는 새 하드웨어 또는 가상 컴퓨터를 배포하도록 선택합니다. 

새 구성으로의 마이그레이션을 완료하려면 프로세스가 완료되었을 때 원래 가용성 그룹에 대한 모든 데이터 트래픽을 중지하고 분산 가용성 그룹을 동기 데이터 이동으로 변경합니다. 이렇게 하면 두 번째 가용성 그룹의 주 복제본이 완전히 동기화되므로 데이터가 손실되지 않습니다. 동기화를 확인한 후에는 분산 가용성 그룹을 [보조 가용성 그룹으로 장애 조치](https://msdn.microsoft.com/en-US/library/mt651673.aspx) 섹션의 두 번째 가용성 그룹으로 장애 조치합니다.

마이그레이션 후에 이제 두 번째 가용성 그룹이 새로운 주 가용성 그룹인 경우 다음 중 하나를 수행해야 할 수 있습니다.

* 보조 가용성 그룹의 수신기의 이름을 바꾸거나(원래 주 가용성 그룹에서 이전 이름을 삭제하거나 이름을 바꿀 수도 있음), 응용 프로그램 및 사용자가 새 구성에 액세스할 수 있도록 원래 주 가용성 그룹의 수신기로 다시 만듭니다 .
* 이름 바꾸기 또는 다시 만들기가 불가능한 경우 응용 프로그램 및 사용자를 두 번째 가용성 그룹의 수신기에 지정합니다.

### <a name="scale-out-readable-replicas-with-distributed-availability-groups"></a>분산 가용성 그룹을 사용하여 읽기 가능한 복제본 확장

단일 분산 가용성 그룹에는 필요에 따라 최대 16개의 보조 복제본이 포함될 수 있습니다. 따라서 다른 가용성 그룹의 두 개 주 복제본을 포함하여 최대 18개의 읽기용 복사본을 갖출 수 있습니다. 이 방법은 둘 이상의 사이트에서 다양한 응용 프로그램에 보고하기 위해 거의 실시간으로 액세스할 수 있음을 의미합니다.

분산 가용성 그룹을 사용하면 단일 가용성 그룹에서만 가능한 규모 이상으로 읽기 전용 팜을 확장할 수 있습니다. 분산 가용성 그룹은 다음 두 가지 방법으로 읽기 가능한 복제본을 확장할 수 있습니다.

* 데이터베이스가 복구에 없더라도 분산 가용성 그룹에 있는 두 번째 가용성 그룹의 주 복제본을 사용하여 다른 분산 가용성 그룹을 만들 수 있습니다.
* 첫 번째 가용성 그룹의 주 복제본을 사용하여 다른 분산 가용성 그룹을 만들 수도 있습니다.

즉, 주 복제본은 서로 다른 두 개의 분산 가용성 그룹에 참여할 수 있습니다. 다음 그림에서는 AG 1과 AG 2가 모두 분산 AG 1에 참여하고 있는 한편, AG 2와 AG 3은 분산 AG 2에 참여하고 있습니다. AG 2의 주 복제본은 분산 AG 1의 보조 복제본과 분산 AG 2의 주 복제본입니다.

![분산 가용성 그룹을 사용한 읽기 복제본 확장][5]

다음 그림에서는 서로 다른 두 가지 분산 가용성 그룹, 즉 분산 AG 1(AG 1과 AG 2로 구성)과 분산 AG 2(AG 1과 AG 3으로 구성)에 대한 주 복제본인 AG 1을 보여 줍니다.


![분산 가용성 그룹 예제를 사용한 또 다른 읽기 복제본 확장][6]


앞의 두 예제 모두에서는 세 개의 가용성 그룹에 최대 27개의 복제본이 있을 수 있습니다. 이러한 복제본은 모두 읽기 전용 쿼리에 사용할 수 있습니다. 

[읽기 전용 라우팅]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server)은 현재 분산 가용성 그룹에서 작동하지 않습니다. 수신기를 사용하여 연결하는 경우 모든 쿼리는 주 복제본으로 이동합니다. 그렇지 않으면 모든 복제본을 보조 복제본으로 연결하고 직접 액세스할 수 있도록 각 복제본을 구성해야 합니다. 이 동작은 SQL Server 2016 또는 이후 버전의 SQL Server에 대한 업데이트에서 변경될 수 있습니다.

## <a name="initialize-secondary-availability-groups-in-a-distributed-availability-group"></a>분산 가용성 그룹의 보조 가용성 그룹 초기화

분산 가용성 그룹은 두 번째 가용성 그룹의 주 복제본을 초기화하는 데 사용되는 중요한 방법인 [자동 시드]( https://docs.microsoft.com/en-us/sql/database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group)로 설계되었습니다. 다음을 수행하면 두 번째 가용성 그룹의 주 복제본에 대한 전체 데이터베이스 복원이 가능합니다.

1. WITH NORECOVERY를 사용하여 데이터베이스 백업을 복원합니다.
2. 필요한 경우 WITH NORECOVERY를 사용하여 적절한 트랜잭션 로그 백업을 복원합니다.
3. 데이터베이스 이름을 지정하지 않고 SEEDING_MODE를 AUTOMATIC으로 설정된 두 번째 가용성 그룹을 만듭니다.
4. 자동 시드를 사용하여 분산 가용성 그룹을 만듭니다.

두 번째 가용성 그룹의 주 복제본을 분산 가용성 그룹에 추가하면, 이 복제본이 첫 번째 가용성 그룹의 주 데이터베이스와 대조하여 검사되고 시드를 통해 데이터베이스를 원본까지 catch합니다. 몇 가지 주의 사항이 있습니다.

* 두 번째 가용성 그룹의 주 복제본에 있는 `sys.dm_hadr_automatic_seeding`에 표시된 출력에는 "Seeding Check Message Timeout(시드 중 확인 메시지 시간 초과)"라는 이유로 `current_state`가 FAILED(실패)로 표시됩니다.

* 두 번째 가용성 그룹의 주 복제본에 있는 현재 SQL Server 로그에는 시드가 작동하고 [LSN]( https://docs.microsoft.com/en-us/sql/relational-databases/sql-server-transaction-log-architecture-and-management-guide)이 동기화되었다고 표시됩니다.

* 첫 번째 가용성 그룹의 주 복제본에 있는 `sys.dm_hadr_automatic_seeding`에 표시된 출력에는 current_state가 COMPLETED(완료)로 표시됩니다. 

* 시드에는 분산 가용성 그룹과 다른 동작도 있습니다. 두 번째 복제본에서 시드를 시작하려면 복제본에서 `ALTER AVAILABILITY GROUP [AGName] GRANT CREATE ANY DATABASE` 명령을 실행해야 합니다. 이 조건은 기본 가용성 그룹에 참여하는 모든 보조 복제본에 여전히 적용되지만, 두 번째 가용성 그룹의 주 복제본에는 이미 분산 가용성 그룹에 추가된 후 시드를 시작할 수 있는 권한이 있습니다. 

### <a name="view-distributed-availability-group-information"></a>분산 가용성 그룹 정보 보기 
    
앞에서 설명한 대로 분산 가용성 그룹은 SQL Server 전용 구조이며 기본 WSFC 클러스터에는 표시되지 않습니다. 다음 그림에서는 각각 자체의 가용성 그룹이 있는 서로 다른 두 WSFC 클러스터(CLUSTER_A 및 CLUSTER_B)를 보여 줍니다. 여기서는 CLUSTER_A의 AG 1 및 CLUSTER_B의 AG 2에 대해서만 설명합니다. 

<!-- ![Two WSFC clusters with multiple availability groups through PowerShell Get-ClusterGroup command][7]  -->
<a name="fig7"></a>
```
PS C:\> Get-ClusterGroup -Cluster CLUSTER_A

Name                            OwnerNode             State
----                            ---------             -----
AG1                             DENNIS                Online Available Storage               GLEN                  Offline Cluster Group                   JY                    Online New_RoR                         DENNIS                Online Old_RoR                         DENNIS                Online SeedingAG                       DENNIS                Online


PS C:\> Get-ClusterGroup -Cluster CLUSTER_B

Name                            OwnerNode             State
----                            ---------             -----
AG2                             TOMMY                 Online Available Storage               JC                    Offline Cluster Group                   JC                    Online
```

All detailed information about a distributed availability group is in SQL Server, specifically in the availability-group dynamic management views. Currently, the only information shown in SQL Server Management Studio for a distributed availability group is on the primary replica for the availability groups. As shown in the following figure, under the Availability Groups folder, SQL Server Management Studio shows that there is a distributed availability group. The figure shows AG1 as a primary replica for an individual availability group that's local to that instance, not for a distributed availability group.

![View in SQL Server Management Studio of the primary replica on the first WSFC cluster of a distributed availability group][8]


However, if you right-click the distributed availability group, no options are available (see the following figure), and the expanded Availability Databases, Availability Group Listeners, and Availability Replicas folders are all empty. SQL Server Management Studio 16 displays this result, but it might change in a future version of SQL Server Management Studio.

![No options available for action][9]

As shown in the following figure, secondary replicas show nothing in SQL Server Management Studio related to the distributed availability group. These availability group names map to the roles shown in the previous [CLUSTER_A WSFC cluster](#fig7) image.

![View in SQL Server Management Studio of a secondary replica][10]

The same concepts hold true when you use the dynamic management views. By using the following query, you can see all the availability groups (regular and distributed) and the nodes participating in them. This result is displayed only if you query the primary replica in one of the WSFC clusters that are participating in the distributed availability group. There is a new column in the dynamic management view `sys.availability_groups` named `is_distributed`, which is 1 when the availability group is a distributed availability group. To see this column:

```
SELECT ag.[name] as 'AG Name', ag.Is_Distributed, ar.replica_server_name as 'Replica Name' FROM    sys.availability_groups ag, sys.availability_replicas ar       
WHERE   ag.group_id = ar.group_id
```

An example of output from the second WSFC cluster that's participating in a distributed availability group is shown in the following figure. SPAG1 is composed of two replicas: DENNIS and JY. However, the distributed availability group named SPDistAG has the names of the two participating availability groups (SPAG1 and SPAG2) rather than the names of the instances, as with a traditional availability group. 

![Example output of the preceding query][11]

In SQL Server Management Studio, any status shown on the Dashboard and other areas are for local synchronization only within that availability group. To display the health of a distributed availability group, query the dynamic management views. The following example query extends and refines the previous query:

```
SELECT ag.[name] as 'AG Name', ag.is_distributed, ar.replica_server_name as 'Underlying AG', ars.role_desc as 'Role', ars.synchronization_health_desc as 'Sync Status' FROM    sys.availability_groups ag, sys.availability_replicas ar,       
sys.dm_hadr_availability_replica_states ars       
WHERE   ar.replica_id = ars.replica_id and     ag.group_id = ar.group_id and ag.is_distributed = 1
```
       
       
![Distributed availability group status][12]


To further extend the previous query, you can also see the underlying performance via the dynamic management views by adding in `sys.dm_hadr_database_replicas_states`. The dynamic management view currently stores information about the second availability group only. The following example query, run on the primary availability group, produces the sample output shown below:

```
SELECT ag.[name] as 'Distributed AG Name', ar.replica_server_name as 'Underlying AG', dbs.[name] as 'DB', ars.role_desc as 'Role', drs.synchronization_health_desc as 'Sync Status', drs.log_send_queue_size, drs.log_send_rate, drs.redo_queue_size, drs.redo_rate FROM    sys.databases dbs, sys.availability_groups ag, sys.availablity_replicas ar, sys.dm_hadr_availability_replica_states ars, sys.dm_hadr_database_replica_states drs WHERE   drs.group_id = ag.group_id and ar.replica_id = ars.replica_id and ars.replica_id = drs.replica_id and dbs.database_id = drs.database_id and ag.is_distributed = 1
```

![Performance information for a distributed availability group][13]


### Next steps 

* [Use the availability group wizard (SQL Server Management Studio)](use-the-availability-group-wizard-sql-server-management-studio.md)

* [Use the new availability group dialog box (SQL Server Management Studio)](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)
 
* [Create an availability group with Transact-SQL](create-an-availability-group-transact-sql.md)

This content was written by [Allan Hirt](http://mvp.microsoft.com/en-us/PublicProfile/4025254?fullName=Allan%20Hirt), Microsoft Most Valued Professional.

<!--Image references-->
[1]: ./media/dag-01-high-level-view-distributed-ag.png
[2]: ./media/dag-02-distributed-ag-data-movement.png
[3]: ./media/dag-03-distributed-ags-wsfcs-different-versions-windows-server.png
[4]: ./media/dag-04-traditional-multi-site-ag.png
[5]: ./media/dag-05-scaling-out-reads-with-distributed-ags.png
[6]: ./media/dag-06-another-scaling-out-reads-using-distributed-ags-example.png
[7]: ./media/dag-07-two-wsfcs-multiple-ags-through-get-clustergroup-command.png
[8]: ./media/dag-08-view-smss-primary-replica-first-wsfc-distributed-ag.png
[9]: ./media/dag-09-no-options-available-action.png
[10]: ./media/dag-10-view-ssms-secondary-replica.png
[11]: ./media/dag-11-example-output-of-query-above.png
[12]: ./media/dag-12-distributed-ag-status.png
[13]: ./media/dag-13-performance-information-distributed-ag.png

 
