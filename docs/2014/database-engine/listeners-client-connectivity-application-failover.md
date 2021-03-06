---
title: 가용성 그룹 수신기, 클라이언트 연결 및 응용 프로그램 장애 조치 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- read-only routing
- read-intent connections [AlwaysOn Availability Groups]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], read-only routing
- Availability Groups [SQL Server], client connectivity
ms.assetid: 76fb3eca-6b08-4610-8d79-64019dd56c44
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3bf28d011f1b1387bfbf04358d4575232c768d6d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48200333"
---
# <a name="availability-group-listeners-client-connectivity-and-application-failover-sql-server"></a>가용성 그룹 수신기, 클라이언트 연결 및 애플리케이션 장애 조치(failover)(SQL Server)
  이 항목에서는 [!INCLUDE[ssHADR](../includes/sshadr-md.md)] 클라이언트 연결 및 애플리케이션 장애 조치(failover) 기능에 대한 고려 사항에 대해 설명합니다.  
  
> [!NOTE]  
>  대부분의 일반 수신기 구성에서는 [!INCLUDE[tsql](../includes/tsql-md.md)] 문 또는 PowerShell cmdlet을 사용하여 첫 번째 가용성 그룹 수신기를 간단히 만들 수 있습니다. 자세한 내용은 이 항목의 뒷부분에 나오는 [관련 태스크](#RelatedTasks)를 참조하세요.  
  
 
  
##  <a name="AGlisteners"></a> 가용성 그룹 수신기  
 가용성 그룹 수신기를 만들어 지정된 가용성 그룹의 데이터베이스에 대한 클라이언트 연결을 제공할 수 있습니다. 가용성 그룹 수신기는 AlwaysOn 가용성 그룹의 주 복제본 또는 보조 복제본에 있는 데이터베이스에 액세스하기 위해 클라이언트가 연결할 수 있는 VNN(가상 네트워크 이름)입니다. 클라이언트를 연결할 SQL Server의 실제 인스턴스 이름을 모르더라도 가용성 그룹 수신기를 사용하면 클라이언트를 가용성 복제본에 연결할 수 있습니다.  현재 주 복제본의 현재 위치에 연결하기 위해 클라이언트 연결 문자열을 수정할 필요가 없습니다.  
  
 가용성 그룹 수신기는 DNS(Domain Name System) 수신기 이름, 수신기 포트 지정 및 하나 이상의 IP 주소로 구성됩니다. 가용성 그룹 수신기는 TCP 프로토콜만 지원합니다.  또한 수신기의 DNS 이름은 도메인 및 NetBIOS에서 고유해야 합니다.  새 가용성 그룹 수신기를 만들 경우 해당 수신기는 연결된 VNN(가상 네트워크 이름), VIP(가상 IP) 및 가용성 그룹 종속성이 있는 클러스터의 리소스가 됩니다. 클라이언트는 DNS를 사용하여 VNN을 여러 IP 주소로 확인한 다음 연결 요청이 성공하거나 연결 요청 시간이 초과될 때까지 각 주소로 연결을 시도합니다.  
  
 하나 이상의[읽기 가능한 보조 복제본](availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)에 대해 읽기 전용 라우팅을 구성할 경우 주 복제본에 대한 읽기 전용 클라이언트 연결은 읽기 가능한 보조 복제본으로 리디렉션됩니다. 주 복제본이 SQL Server의 인스턴스 중 하나에서 오프라인으로 전환되고 새로운 주 복제본이 SQL Server의 다른 인스턴스에서 온라인으로 연결되면 가용성 그룹 수신기를 사용하여 클라이언트를 새로운 주 복제본으로 연결할 수 있습니다.  
  
 가용성 그룹 수신기에 대한 자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)을 참조하세요.  
  
 
  
###  <a name="AGlConfig"></a> 가용성 그룹 수신기 구성  
 가용성 그룹 수신기는 다음에 의해 정의됩니다.  
  
 고유 DNS 이름  
 이것은 VNN(가상 네트워크 이름)이라고도 합니다. DNS 호스트 이름에 대한 Active Directory 명명 규칙이 적용됩니다. 자세한 내용은 [컴퓨터, 도메인, 사이트 및 OU에 대한 Active Directory 명명 규칙(](http://support.microsoft.com/kb/909264) KB 문서를 참조하세요.  
  
 하나 이상의 VIP(가상 IP 주소)  
 VIP는 가용성 그룹이 장애 조치(failover)할 수 있는 하나 이상의 서브넷에 대해 구성됩니다.  
  
 IP 주소 구성  
 지정된 가용성 그룹 수신기의 경우 IP 주소는 DHCP(동적 호스트 구성 프로토콜) 또는 하나 이상의 고정 IP 주소를 사용합니다.  
  
-   DHCP(동적 호스트 구성 프로토콜)  
  
     가용성 그룹이 단일 서브넷에 있는 경우 DHCP를 사용하도록 가용성 그룹 수신기 IP 주소를 구성할 수 있습니다. 사전 프로덕션 환경의 경우 DHCP를 사용하면 별도의 서브넷에서 원격 사이트에 대한 재해 복구를 수행할 필요가 없는 가용성 그룹을 쉽게 설정할 수 있습니다. 하지만 프로덕션 환경에서는 DHCP를 가용성 그룹 수신기와 함께 사용하지 않는 것이 좋습니다. 작동이 중단하고 DHCP IP 임대가 만료된 경우 수신기 DNS 이름과 연결된 새 DHCP IP 주소를 다시 등록하는 데 시간이 추가로 소요되기 때문입니다. 시간이 추가로 소요되면 클라이언트 연결이 실패합니다.  
  
-   고정 IP 주소  
  
     프로덕션 환경에서는 가용성 그룹 수신기에서 고정 IP 주소를 사용하는 것이 좋습니다. 또한 가용성 그룹이 다중 서브넷 도메인에서 여러 서브넷으로 확장될 경우 가용성 그룹 수신기는 고정 IP 주소를 사용해야 합니다.  
  
 혼합 네트워크 구성과 여러 서브넷의 DHCP는 가용성 그룹 수신기에 대해 지원되지 않습니다. 이는 장애 조치(failover)가 발생할 때 동적 IP가 만료되거나 해제되어 전체 고가용성이 위험해질 수 있기 때문입니다.  
  
###  <a name="SelectListenerPort"></a> 가용성 그룹 수신기 포트 선택  
 가용성 그룹 수신기를 구성할 때 포트를 지정해야 합니다.  클라이언트 연결 문자열을 간소화하기 위해 기본 포트를 1433으로 구성할 수 있습니다. 1433을 사용하는 경우에는 연결 문자열에서 포트 번호를 지정할 필요가 없습니다.   또한 가용성 그룹 수신기마다 별도의 가상 네트워크 이름이 있으므로 단일 WSFC에 구성된 각 가용성 그룹 수신기가 동일한 기본 포트 1433을 참조하도록 구성할 수 있습니다.  
  
 비표준 수신기 포트를 지정할 수도 있지만, 이렇게 할 경우 가용성 그룹 수신기에 연결할 때마다 연결 문자열에서 대상 포트를 명시적으로 지정해야 합니다.  또한 비표준 포트의 경우 방화벽에 대한 열기 권한이 있어야 합니다.  
  
 가용성 그룹 수신기 VNN에 대해 기본 포트 1433을 사용할 경우 클러스터 노드에 이 포트를 사용 중인 다른 서비스가 없어야 합니다. 그렇지 않으면 포트 충돌이 발생합니다.  
  
 SQL Server의 인스턴스 중 하나가 인스턴스 수신기를 통해 TCP 포트 1433을 이미 수신 중이고 컴퓨터에 포트 1433을 수신 중인 다른 서비스(SQL Server의 추가 인스턴스 포함)가 없는 경우에는 가용성 그룹 수신기와 포트 충돌이 발생하지 않습니다.  이는 가용성 그룹 수신기가 동일한 서비스 프로세스 내에서 동일한 TCP 포트를 공유할 수 있기 때문입니다.  그러나 SQL Server의 여러 인스턴스에서 동일한 포트를 동시에 수신하도록 구성하면 안 됩니다.  
  
##  <a name="ConnectToPrimary"></a> 수신기를 사용하여 주 복제본에 연결  
 읽기/쓰기 액세스를 위해 가용성 그룹 수신기를 사용하여 주 복제본에 연결하려면 연결 문자열에서 가용성 그룹 수신기 DNS 이름을 지정합니다.  가용성 그룹 주 복제본이 새 복제본으로 변경되면 가용성 그룹 수신기의 네트워크 이름을 사용하는 기존 연결이 끊어집니다.  그러면 가용성 그룹 수신기에 대한 새 연결이 새 주 복제본에 전달됩니다. ADO.NET 공급자(System.Data.SqlClient)에 대한 기본 연결 문자열의 예는 다음과 같습니다.  
  
```  
Server=tcp: AGListener,1433;Database=MyDB;IntegratedSecurity=SSPI  
```  
  
 가용성 그룹 수신기 서버 이름을 사용하는 대신 주 복제본 또는 보조 복제본의 SQL Server 이름 인스턴스를 직접 참조하도록 선택할 수 있지만, 이렇게 할 경우 새 연결이 현재 주 복제본에 자동으로 전달되지 않습니다.  또한 읽기 전용 라우팅의 이점도 누릴 수 없게 됩니다.  
  
##  <a name="ConnectToSecondary"></a> 수신기를 사용하여 읽기 전용 보조 복제본에 연결(읽기 전용 라우팅)  
 *읽기 전용 라우팅* 은 가용성 그룹 수신기에 대한 들어오는 연결을 읽기 전용 작업을 허용하도록 구성된 보조 복제본에 라우팅하는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 의 기능을 말합니다. 가용성 그룹 수신기 이름을 참조하는 들어오는 연결은 다음과 같은 경우 읽기 전용 복제본에 자동으로 라우팅될 수 있습니다.  
  
-   최소 하나 이상의 보조 복제본이 읽기 전용 액세스로 설정되고 각 읽기 전용 보조 복제본과 주 복제본은 읽기 전용 라우팅을 지원하도록 구성됩니다. 자세한 내용은 이 섹션의 뒷부분에 나오는 [읽기 전용 라우팅을 위해 가용성 복제본을 구성하려면](#ConfigureARsForROR)을 참조하세요.  
  
-   연결 문자열은 가용성 그룹 수신기를 참조하며 들어오는 연결의 애플리케이션 의도는 ODBC 또는 OLEDB 연결 문자열이나 연결 특성 또는 속성에서 **Application Intent=ReadOnly** 키워드를 사용하는 등과 같은 방법으로 읽기 전용으로 설정됩니다. 자세한 내용은 이 섹션 뒷부분에 있는 [읽기 전용 애플리케이션 의도 및 읽기 전용 라우팅](#ReadOnlyAppIntent)을 참조하세요.  
  
###  <a name="ConfigureARsForROR"></a> 읽기 전용 라우팅에 대한 가용성 복제본을 구성하려면  
 데이터베이스 관리자는 다음과 같이 가용성 복제본을 구성해야 합니다.  
  
1.  읽기 가능한 보조 복제본으로 구성하려는 각 가용성 복제본에 대해 데이터베이스 관리자는 보조 역할에서만 효과가 있는 다음과 같은 설정을 구성해야 합니다.  
  
    -   연결 액세스를 "모두" 또는 "읽기 전용"으로 설정해야 합니다.  
  
    -   읽기 전용 라우팅 URL을 지정해야 합니다.  
  
2.  이러한 각 복제본에 대해 주 역할에 대한 읽기 전용 라우팅 목록을 지정해야 합니다. 하나 이상의 서버 이름을 라우팅 대상으로 지정합니다.  
  
####  <a name="RelatedTasksROR"></a> 관련 태스크  
  
-   [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
###  <a name="ReadOnlyAppIntent"></a> 읽기 전용 응용 프로그램 의도 및 읽기 전용 라우팅  
 애플리케이션 의도 연결 문자열 속성은 가용성 그룹 데이터베이스의 읽기/쓰기 또는 읽기 전용 버전에 전달할 클라이언트 애플리케이션의 요청을 나타냅니다. 읽기 전용 라우팅을 사용하려면 가용성 그룹 수신기에 연결할 때 클라이언트가 연결 문자열에 애플리케이션의 읽기 전용 의도를 사용해야 합니다. 읽기 전용 애플리케이션 의도가 없으면 가용성 그룹 수신기에 대한 연결이 주 복제본의 데이터베이스에 전송됩니다.  
  
 애플리케이션 의도 특성은 로그인 중에 클라이언트의 세션에 저장됩니다. 그러면 SQL Server의 인스턴스에서 이 의도를 처리하고 보조 복제본에 있는 대상 데이터베이스의 현재 읽기/쓰기 상태와 가용성 그룹의 구성에 따라 수행할 작업을 결정합니다.  
  
 읽기 전용 애플리케이션 의도를 지정하는 ADO.NET 공급자(System.Data.SqlClient)에 대한 연결 문자열의 예는 다음과 같습니다.  
  
```  
Server=tcp:AGListener,1433;Database=AdventureWorks;IntegratedSecurity=SSPI;ApplicationIntent=ReadOnly  
```  
  
 이 연결 문자열 예에서 클라이언트는 포트 1433에서 `AGListener` 라는 가용성 그룹 수신기에 연결을 시도합니다. 가용성 그룹 수신기가 1433에서 수신하는 경우 포트를 생략할 수도 있습니다.  연결 문자열에는 `ApplicationIntent` 속성으로 설정 `ReadOnly`,이 *읽기 전용 연결 문자열*합니다.  이 설정이 없으면 서버에서 연결에 대한 읽기 전용 라우팅을 시도하지 않습니다.  
  
 가용성 그룹의 주 데이터베이스는 들어오는 읽기 전용 라우팅 요청을 처리한 다음 주 복제본에 조인되고 읽기 전용 라우팅을 위해 구성된 온라인 읽기 전용 복제본을 찾습니다.  클라이언트는 주 복제본 서버에서 연결 정보를 다시 받고 식별된 읽기 전용 복제본에 연결합니다.  
  
 애플리케이션 의도는 클라이언트 드라이버에서 SQL Server의 하위 인스턴스로 보낼 수 있습니다.  이 경우에는 애플리케이션의 읽기 전용 의도가 무시되고 연결이 정상적으로 진행됩니다.  
  
 응용 프로그램 의도 연결 속성 설정 하지 않으면 읽기 전용 라우팅을 무시할 수 있습니다 `ReadOnly` (기본값은 지정 하지 않을 경우 `ReadWrite` 로그인 하는 동안) 사용 하는 대신 SQL Server의 주 복제본 인스턴스에 직접 연결 하거나 가용성 그룹 수신기 이름입니다.  또한 읽기 전용 복제본에 직접 연결하면 읽기 전용 라우팅이 발생하지 않습니다.  
  
####  <a name="RelatedTasksApps"></a> 관련 태스크  
  
-   [고가용성 재해 복구를 위한 SQL Server Native Client 지원](../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [SQL Server Native Client에서 연결 문자열 키워드 사용](../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
##  <a name="BypassAGl"></a> 가용성 그룹 수신기 무시  
 가용성 그룹 수신기에서 장애 조치(Failover) 리디렉션 및 읽기 전용 라우팅을 지원하지만 클라이언트 연결에서 해당 기능을 사용할 필요는 없습니다. 클라이언트 연결에서 가용성 그룹 수신기에 연결하는 대신 SQL Server의 인스턴스를 직접 참조할 수도 있습니다.  
  
 SQL Server의 인스턴스에서 가용성 그룹 수신기를 사용하거나 다른 인스턴스 엔드포인트를 사용하여 연결이 로그인되는지 여부는 관계가 없습니다.  SQL Server 인스턴스는 대상 데이터베이스의 상태를 확인하고 가용성 그룹의 구성과 인스턴스에 대한 데이터베이스의 현재 상태를 기반으로 연결을 허용하거나 허용하지 않습니다.  예를 들어 클라이언트 애플리케이션이 SQL Server 포트의 인스턴스에 직접 연결하고 가용성 그룹에 호스팅된 대상 데이터베이스에 연결하고 대상 데이터베이스가 기본 온라인 상태인 경우 연결이 성공합니다.  대상 데이터베이스가 오프라인 상태이거나 전환 상태이면 데이터베이스 연결이 실패합니다.  
  
 보조 복제본이 하나만 있고 사용자 연결을 허용하는 않는 경우 데이터베이스 미러링을 [!INCLUDE[ssHADR](../includes/sshadr-md.md)]로 마이그레이션하는 동안 애플리케이션에서 데이터베이스 미러링 연결 문자열을 지정할 수 있습니다. 자세한 내용은 이 섹션의 뒷부분에 나오는 [가용성 그룹에 데이터베이스 미러링 연결 문자열 사용](#DbmConnectionString)을 참조하세요.  
  
###  <a name="DbmConnectionString"></a> 가용성 그룹에 데이터베이스 미러링 연결 문자열 사용  
 가용성 그룹에 보조 복제본이 하나만 있고 보조 복제본에 대한 읽기 액세스를 허용하도록 구성되어 있지 않은 경우, 클라이언트에서는 데이터베이스 미러링 연결 문자열을 사용하여 주 복제본에 연결할 수 있습니다. 가용성 그룹에 두 개의 가용성 복제본(주 복제본과 보조 복제본)만 포함되도록 제한한 경우 이 방법은 데이터베이스 미러링의 기존 애플리케이션을 가용성 그룹으로 마이그레이션하는 데 유용합니다. 보조 복제본을 더 추가하려면 가용성 그룹의 가용성 그룹 수신기를 만들고 가용성 그룹 수신기 DNS 이름을 사용하도록 애플리케이션을 업데이트해야 합니다.  
  
 데이터베이스 미러링 연결 문자열을 사용할 경우 클라이언트에서는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client나 .NET Framework Data Provider for [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]를 사용할 수 있습니다. 연결하려는 가용성 복제본을 처음에 호스팅할 서버 인스턴스를 식별하려면 클라이언트가 제공하는 연결 문자열에 최소한 하나의 서버 인스턴스 이름, 즉 *초기 파트너 이름*이 있어야 합니다. 필요한 경우 연결 문자열에 다른 서버 인스턴스의 이름, 즉 *장애 조치(failover) 파트너 이름*을 제공하여 초기에 보조 복제본을 호스팅할 서버 인스턴스를 장애 조치(failover) 파트너 이름으로 식별할 수도 있습니다.  
  
 데이터베이스 미러링 연결 문자열에 대한 자세한 내용은 [데이터베이스 미러링 세션에 클라이언트 연결&#40;SQL Server&#41;](database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)을 참조하세요.  
  
##  <a name="CCBehaviorOnFailover"></a> 장애 조치(Failover) 시 클라이언트 연결 동작  
 가용성 그룹 장애 조치(failover)가 발생하면 가용성 그룹에 대한 기존의 영구 연결이 종료되므로 클라이언트는 동일한 주 데이터베이스 또는 읽기 전용 보조 데이터베이스로 계속 작업하려면 새 연결을 설정해야 합니다.  서버측에서 장애 조치(failover)가 수행 중인 동안에는 가용성 그룹에 연결할 수 없으며, 주 데이터베이스가 다시 온라인으로 전환될 때까지 클라이언트 애플리케이션에서 연결을 다시 시도합니다.  
  
 클라이언트 애플리케이션의 연결 시도 중에 연결 제한 시간 이전에 가용성 그룹이 다시 온라인으로 전환되는 경우에는 내부적으로 연결을 재시도하는 과정에서 클라이언트 드라이버가 성공적으로 연결될 수 있으며 이 경우 애플리케이션에 오류가 표시되지 않습니다.  
  
##  <a name="SupportAgMultiSubnetFailover"></a> 가용성 그룹 다중 서브넷 장애 조치(Failover) 지원  
 연결 문자열에서 MultiSubnetFailover 연결 옵션을 지원하는 클라이언트 라이브러리를 사용 중인 경우 사용하는 공급자의 구문에 따라 MultiSubnetFailover를 "True"나 "Yes"로 설정하여 다른 서브넷에 대한 가용성 그룹 장애 조치(failover)를 최적화할 수 있습니다.  
  
> [!NOTE]  
>  가용성 그룹 수신기와 SQL Server 장애 조치(Failover) 클러스터 인스턴스 이름에 대한 단일 및 다중 서브넷 연결 모두에 대해 이 설정을 사용하는 것이 좋습니다.  이 옵션을 사용하면 단일 서브넷 시나리오에 대해서도 최적화가 추가됩니다.  
  
 합니다 `MultiSubnetFailover` 연결 옵션은 TCP 네트워크 프로토콜에만 작동 하 고 및 가상 네트워크 이름을 연결 하는 모든 가용성 그룹 수신기에 연결할 때만 지원 됩니다 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]합니다.  
  
 다중 서브넷 장애 조치(failover)를 사용하는 ADO.NET 공급자(System.Data.SqlClient) 연결 문자열의 예는 다음과 같습니다.  
  
```  
Server=tcp:AGListener,1433;Database=AdventureWorks;IntegratedSecurity=SSPI; MultiSubnetFailover=True  
```  
  
 합니다 `MultiSubnetFailover` 연결 옵션 설정 해야 `True` 가용성 그룹이 단일 서브넷에만 적용 되는 경우에 합니다.  그러면 나중에 클라이언트 연결 문자열을 변경하지 않고도 서브넷 확장을 지원하도록 새 클라이언트를 미리 구성하여 단일 서브넷 장애 조치(failover)에 대한 장애 조치(failover) 성능을 최적화할 수 있습니다.  하지만 `MultiSubnetFailover` 연결 옵션이 필요 하지 않습니다, 더 빠른 서브넷 장애 조치의 이점을 제공 합니다.  클라이언트 드라이버가 가용성 그룹과 병렬로 연결된 각 IP 주소에 대해 TCP 소켓을 열려고 하기 때문입니다.  클라이언트 드라이버는 첫 번째 IP가 응답할 때까지 기다린 다음 성공적으로 응답하면 해당 IP를 사용하여 연결합니다.  
  
##  <a name="SSLcertificates"></a> 가용성 그룹 수신기 및 SSL 인증서  
 가용성 그룹 수신기에 연결할 때 SQL Server의 참여 인스턴스에서 SSL 인증서를 세션 암호화와 함께 사용하는 경우 암호화를 적용하려면 연결하는 클라이언트 드라이버가 SSL 인증서에서 Subject Alternate 이름을 지원해야 합니다.  인증서 Subject Alternative 이름에 대한 SQL Server 드라이버 지원은 ADO.NET(SqlClient), Microsoft JDBC 및 SNAC(SQL Native Client)에 포함될 계획입니다.  
  
 인증서의 Subject Alternate 이름에 모든 가용성 그룹 수신기 목록을 설정하여 참여하는 각 서버 노드에 대해 X.509 인증서를 구성해야 합니다.  
  
 예를 들어 WSFC에 `AG1_listener.Adventure-Works.com`, `AG2_listener.Adventure-Works.com`및 `AG3_listener.Adventure-Works.com`이라는 세 개의 가용성 그룹 수신기가 있는 경우 인증서에 대한 Subject Alternative 이름은 다음과 같습니다.  
  
```  
CN = ServerFQDN  
SAN = ServerFQDN,AG1_listener.Adventure-Works.com, AG2_listener.Adventure-Works.com, AG3_listener.Adventure-Works.com  
```  
  
##  <a name="SPNs"></a> 가용성 그룹 수신기 및 SPN(서버 보안 주체 이름)  
 가용성 그룹 수신기에 대한 클라이언트 연결에 Kerberos를 사용하려면 도메인 관리자가 Active Directory에서 각 가용성 그룹에 대해 SPN(서버 보안 주체 이름)을 구성해야 합니다. SPN을 등록할 때 가용성 복제본을 호스트하는 서버 인스턴스의 서비스 계정을 사용해야 합니다.  SPN을 모든 복제본에 대해 사용하려면 가용성 그룹을 호스팅하는 WSFC 클러스터의 모든 인스턴스에 대해 동일한 서비스 계정을 사용해야 합니다.  
  
 `setspn` Windows 명령줄 도구를 사용하여 SPN을 구성할 수 있습니다.  예를 들어 `AG1listener.Adventure-Works.com` 도메인 계정에서 실행하도록 구성된 모든 SQL Server 인스턴스 집합에 호스팅되는 `corp/svclogin2`이라는 가용성 그룹에 대한 SPN을 구성하려면  
  
```  
setspn -A MSSQLSvc/AG1listener.Adventure-Works.com:1433 corp/svclogin2  
```  
  
 SQL Server에 대한 SPN을 수동으로 등록하는 방법은 [Kerberos 연결의 서비스 사용자 이름 등록](configure-windows/register-a-service-principal-name-for-kerberos-connections.md)을 참조하세요.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [AlwaysOn 클라이언트 연결 &#40;SQL Server&#41;](availability-groups/windows/always-on-client-connectivity-sql-server.md)
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;](availability-groups/windows/view-availability-group-listener-properties-sql-server.md)  
  
-   [가용성 그룹 수신기 제거&#40;SQL Server&#41;](availability-groups/windows/remove-an-availability-group-listener-sql-server.md)  
  
-   [가용성 복제본에 대한 읽기 전용 액세스 구성&#40;SQL Server&#41;](availability-groups/windows/configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [가용성 그룹에 대한 읽기 전용 라우팅 구성&#40;SQL Server&#41;](availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
##  <a name="RelatedContent"></a> 관련 내용  
  
-   [Microsoft SQL Server AlwaysOn 솔루션 가이드 고가용성 및 재해 복구](http://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [Introduction to the Availability Group Listener](http://blogs.msdn.com/b/sqlalwayson/archive/2012/01/16/introduction-to-the-availability-group-listener.aspx)(가용성 그룹 수신기 소개)(SQL Server AlwaysOn 팀 블로그)  
  
-   [SQL Server AlwaysOn 팀 블로그: 공식 SQL Server AlwaysOn 팀 블로그](http://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>관련 항목  
 [AlwaysOn 가용성 그룹 개요 &#40;SQL Server&#41;](availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [AlwaysOn 클라이언트 연결 &#40;SQL Server&#41;](availability-groups/windows/always-on-client-connectivity-sql-server.md)  
 [가용성 복제본에 대한 클라이언트 연결 액세스 정보&#40;SQL Server&#41;](availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [활성 보조: 읽기 가능한 보조 복제본 &#40;AlwaysOn 가용성 그룹&#41;](availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)   
 [데이터베이스 미러링 세션에 클라이언트 연결&#40;SQL Server&#41;](database-mirroring/connect-clients-to-a-database-mirroring-session-sql-server.md)
  
  
