---
title: "일부 가용성 복제본의 연결이 해제됨 | Microsoft Docs"
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
  - "sql13.swb.agdashboard.agp7allconnected.issues.f1"
helpviewer_keywords: 
  - "가용성 그룹 [SQL Server], 정책"
ms.assetid: aea808be-6f0f-40c2-9aa2-a2a435ec6443
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# 일부 가용성 복제본의 연결이 해제됨
    
## 소개  
  
|||  
|-|-|  
|**정책 이름**|가용성 복제본 연결 상태|  
|**문제점**|일부 가용성 복제본의 연결이 해제됩니다.|  
|**범주**|**경고**|  
|**패싯**|가용성 그룹|  
  
## 설명  
 이 정책은 모든 가용성 복제본의 연결 상태를 롤업하며 연결이 해제된 가용성 복제본이 있는지 확인합니다. 가용성 복제본의 연결이 해제된 경우 정책은 비정상 상태에 있습니다. 그렇지 않으면 정책은 정상 상태입니다.  
  
> [!NOTE]  
>  이 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 릴리스의 경우 가능한 원인 및 해결 방법은 TechNet Wiki의 [일부 가용성 복제본의 연결이 해제됨](http://go.microsoft.com/fwlink/p/?LinkId=220855)을 참조하세요.  
  
## 가능한 원인  
 이 가용성 그룹의 하나 이상의 보조 복제본이 주 복제본에 연결되어 있지 않습니다. 연결 상태가 DISCONNECTED입니다.  
  
## 가능한 해결 방법  
 가용성 복제본 정책 상태를 사용하여 DISCONNECTED 상태인 가용성 복제본을 찾은 다음 가용성 복제본에서 문제를 해결합니다.  
  
## 참고 항목  
 [Always On 가용성 그룹 개요&#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Always On 대시보드 사용&#40;SQL Server Management Studio&#41;](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  