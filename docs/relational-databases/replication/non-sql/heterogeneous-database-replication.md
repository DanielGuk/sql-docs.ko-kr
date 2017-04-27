---
title: "다른 유형의 데이터베이스 복제 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- heterogeneous database replication, about heterogeneous database replication
- replication [SQL Server], heterogeneous database replication
- heterogeneous database replication
ms.assetid: 3fd983ad-e206-45db-9054-417c9b5bb815
caps.latest.revision: 41
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6eee43a7755f2e018a7ed4e9f822983b03b7181a
ms.lasthandoff: 04/11/2017

---
# <a name="heterogeneous-database-replication"></a>다른 유형의 데이터베이스 복제
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서는 트랜잭션 및 스냅숏 복제에 대해 다음과 같이 다른 유형의 시나리오를 지원합니다.  
  
-   Oracle에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 데이터 게시  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에서[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 구독자로 데이터 게시  
  
 SQL Server 이외의 구독자에 대한 다른 유형의 복제는 지원되지 않습니다. Oracle 게시는 지원되지 않습니다. 데이터를 이동하려면 변경 데이터 캡처 및 [!INCLUDE[ssIS](../../../includes/ssis-md.md)]를 사용하여 솔루션을 만듭니다.  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
## <a name="publishing-data-from-oracle"></a>Oracle에서 데이터 게시  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용하여 Oracle에서 데이터를 게시할 수 있습니다. 이때 대부분의 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 스냅숏 및 트랜잭션 복제 기능을 동일한 방식으로 간단하게 사용할 수 있습니다. 다음 시나리오에 대해서는 Oracle에서 데이터를 게시하는 것이 가장 적합합니다.  
  
|시나리오|설명|  
|--------------|-----------------|  
|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework 응용 프로그램 배포|[!INCLUDE[msCoName](../../../includes/msconame-md.md)] 이외 데이터베이스에서 복제한 데이터 작업 시 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Visual Studio 및[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 를 사용하여 개발합니다.|  
|데이터 웨어하우징 준비 서버(staging server)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 준비 데이터베이스와[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스의 동기화를 유지합니다.|  
|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]로 마이그레이션|원본 시스템의 변경 내용을 복제하면서 실시간으로 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 에 대한 응용 프로그램을 테스트합니다. 마이그레이션에 만족하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 로 전환합니다.|  
  
 자세한 내용은 [Oracle 게시 개요](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)를 참조하세요.  
  
## <a name="publishing-data-to-non-sql-server-subscribers"></a>SQL Server 이외 구독자에 데이터 게시  
 다음[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 이외 데이터베이스는 스냅숏 및 트랜잭션 게시의 구독자로 지원됩니다.  
  
-   Oracle에서 지원하는 모든 플랫폼용 Oracle 제품  
  
-   AS400, MVS, Unix, Linux 및 Windows용 IBM DB2  
  
 자세한 내용은 [Non-SQL Server Subscribers](../../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)을(를) 참조하세요.  
  
  