---
title: "정책 기반 관리 저장소 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0426d583d1ada35c7ad3e36d4fe1a621e9754360
ms.lasthandoff: 04/11/2017

---
# <a name="policy-based-management-storage"></a>정책 기반 관리 저장소
  정책은 msdb 데이터베이스에 저장됩니다. 정책 또는 조건이 변경되면 msdb를 백업해야 합니다. 자세한 내용은 [시스템 데이터베이스 백업 및 복원&#40;SQL Server&#41](../../relational-databases/backup-restore/back-up-and-restore-of-system-databases-sql-server.md)를 참조하세요.  
  
## <a name="storing-policies"></a>정책 저장  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 모니터링하는 데 사용할 수 있는 정책이 포함되어 있습니다. 기본적으로 이러한 정책은 [!INCLUDE[ssDE](../../includes/ssde-md.md)]에 설치되어 있지 않지만 기본 설치 위치인 C:\Program Files\Microsoft SQL Server\130\Tools\Policies\DatabaseEngine\1033에서 가져올 수 있습니다.  
  
 **파일/새로 만들기** 메뉴를 사용한 다음 파일에 정책을 저장하여 정책을 직접 만들 수 있습니다. 이렇게 하면 [!INCLUDE[ssDE](../../includes/ssde-md.md)]인스턴스에 연결되어 있지 않는 경우 정책을 만들 수 있습니다.  
  
 현재 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스에서 평가한 정책의 정책 기록은 msdb 시스템 테이블에서 유지 관리됩니다. 다른 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 인스턴스 또는 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에 적용된 정책의 정책 기록은 보존되지 않습니다.  
  
  