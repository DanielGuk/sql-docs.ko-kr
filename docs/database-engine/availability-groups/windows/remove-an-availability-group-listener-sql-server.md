---
title: "가용성 그룹 수신기 제거(SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.availabilitygroup.removeaglistener.default.f1"
helpviewer_keywords: 
  - "가용성 그룹 [SQL Server], 수신기"
ms.assetid: fd9bba9a-d29f-4c23-8ecd-aaa049ed5f1b
caps.latest.revision: 14
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 14
---
# 가용성 그룹 수신기 제거(SQL Server)
  이 항목에서는 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]에서 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)] 또는 PowerShell을 사용하여 Always On 가용성 그룹에서 가용성 그룹 수신기를 제거하는 방법에 대해 설명합니다.  
  
-   **시작하기 전에:**  
  
     [필수 구성 요소](#Prerequisites)  
  
     [권장 사항](#Recommendations)  
  
     [보안](#Security)  
  
-   **수신기를 제거하려면:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> 시작하기 전 주의 사항  
  
###  <a name="Prerequisites"></a> 필수 구성 요소  
  
-   주 복제본을 호스팅하는 서버 인스턴스에 연결되어 있어야 합니다.  
  
###  <a name="Recommendations"></a> 권장 사항  
 가용성 그룹 수신기를 삭제하기 전에 해당 가용성 그룹 수신기를 사용 중인 응용 프로그램이 없는지 확인하는 것이 좋습니다.  
  
###  <a name="Security"></a> 보안  
  
####  <a name="Permissions"></a> 사용 권한  
 가용성 그룹에 대한 ALTER AVAILABILITY GROUP 권한, CONTROL AVAILABILITY GROUP 권한, ALTER ANY AVAILABILITY GROUP 권한 또는 CONTROL SERVER 권한이 필요합니다.  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio 사용  
 **가용성 그룹 수신기를 제거하려면**  
  
1.  개체 탐색기에서 주 복제본을 호스팅하는 서버 인스턴스에 연결하고 서버 트리를 확장할 서버 이름을 클릭합니다.  
  
2.  **Always On 고가용성** 노드 및 **가용성 그룹** 노드를 확장합니다.  
  
3.  가용성 그룹의 노드를 확장하고 **가용성 그룹 수신기** 노드를 확장합니다.  
  
4.  제거할 수신기를 마우스 오른쪽 단추로 클릭한 다음 **삭제** 명령을 선택합니다.  
  
5.  **가용성 그룹에서 수신기 제거** 대화 상자가 열립니다. 자세한 내용은 이 항목의 뒷부분에 나와 있는 [가용성 그룹에서 수신기 제거](#AgListenerPropertiesDialog)를 참조하세요.  
  
###  <a name="AgListenerPropertiesDialog"></a> 가용성 그룹에서 수신기 제거(대화 상자)  
 **이름**  
 제거할 수신기의 이름입니다.  
  
 **결과**  
 **성공** 또는 **오류** 링크가 표시됩니다. 링크를 클릭하여 자세한 내용을 확인할 수 있습니다.  
  
##  <a name="TsqlProcedure"></a> Transact-SQL 사용  
 **가용성 그룹 수신기를 제거하려면**  
  
1.  주 복제본을 호스팅하는 서버 인스턴스에 연결합니다.  
  
2.  다음과 같은 [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) 문을 사용합니다.  
  
     ALTER AVAILABILITY GROUP *group_name* REMOVE LISTENER **‘***dns_name***’**  
  
     여기서 *group_name*은 가용성 그룹의 이름이고, *dns_name*은 가용성 그룹 수신기의 DNS 이름입니다.  
  
     다음 예에서는 `AccountsAG` 가용성 그룹의 수신기를 삭제합니다. DNS 이름은 AccountsAG_Listener입니다.  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG REMOVE LISTENER ‘AccountsAG_Listener’;  
    ```  
  
##  <a name="PowerShellProcedure"></a> PowerShell 사용  
 **가용성 그룹 수신기를 제거하려면**  
  
1.  기본값(**cd**)을 주 복제본을 호스트하는 서버 인스턴스로 설정합니다.  
  
2.  기본 제공 **Remove-Item** cmdlet을 사용하여 수신기를 제거합니다. 예를 들어 다음 명령은 `MyListener`라는 가용성 그룹에서 `MyAg`라는 수신기를 제거합니다.  
  
    ```  
    Remove-Item `   
    SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AGListeners\MyListener  
    ```  
  
    > [!NOTE]  
    >  cmdlet의 구문을 보려면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 환경에서 **Get-Help** cmdlet을 사용합니다. 자세한 내용은 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)을 참조하세요.  
  
##  <a name="RelatedTasks"></a> 관련 태스크  
  
-   [가용성 그룹 수신기 만들기 또는 구성&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [가용성 그룹 수신기 속성 보기&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/view-availability-group-listener-properties-sql-server.md)  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [가용성 그룹 수신기, 클라이언트 연결 및 응용 프로그램 장애 조치(failover)&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)  
  
  