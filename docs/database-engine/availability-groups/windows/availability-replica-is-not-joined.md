---
title: "가용성 복제본이 조인되어 있지 않습니다. | Microsoft Docs"
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
  - "sql13.swb.agdashboard.arp4joined.issues.f1"
helpviewer_keywords: 
  - "가용성 그룹 [SQL Server], 정책"
ms.assetid: 9c0d10b1-9e12-430c-83b9-ca2bd0a3afc4
caps.latest.revision: 15
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 15
---
# 가용성 복제본이 조인되어 있지 않습니다.
    
## 소개  
  
|||  
|-|-|  
|**정책 이름**|가용성 복제본 조인 상태|  
|**문제점**|가용성 복제본이 조인되어 있지 않습니다.|  
|**범주**|**경고**|  
|**패싯**|가용성 복제본|  
  
## 설명  
 이 정책은 가용성 복제본의 조인 상태를 확인합니다. 가용성 복제본이 가용성 그룹에 추가되었지만 제대로 조인되지 않은 경우 정책은 비정상 상태입니다. 그렇지 않으면 정책은 정상 상태입니다.  
  
> [!NOTE]  
>  이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 릴리스에서의 가능한 원인 및 해결 방법은 TechNet Wiki의 [가용성 복제본이 조인되어 있지 않음](http://go.microsoft.com/fwlink/p/?LinkId=220859)을 참조하세요.  
  
## 가능한 원인  
 보조 복제본이 가용성 그룹에 조인되어 있지 않습니다. 가용성 복제본을 가용성 그룹에 성공적으로 조인하려면 조인 상태가 조인된 독립 실행형 인스턴스(1) 또는 조인된 장애 조치(Failover) 클러스터(2)여야 합니다.  
  
## 가능한 해결 방법  
 Transact-SQL, PowerShell 또는 SQL Server Management Studio를 사용하여 보조 복제본을 가용성 그룹에 조인합니다. 보조 복제본을 가용성 그룹에 조인하는 방법은 [가용성 그룹에 보조 복제본 조인(SQL Server)](http://msdn.microsoft.com/library/ff878473\(SQL.110\).aspx)을 참조하세요.  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On 대시보드 사용&#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  