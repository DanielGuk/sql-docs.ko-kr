---
title: SQL Server XTP(메모리 내 OLTP) 성능 카운터 | Microsoft 문서
ms.custom: ''
ms.date: 04/06/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
s.technology: performance
ms.topic: conceptual
ms.assetid: fe3cbaf4-65f4-44c5-acc6-7b735cda0c5d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7b9d88f91cb85a097f39e7f40e919e384138cbc3
ms.sourcegitcommit: ca038f1ef180e4e1b27910bbc5d87822cd1ed176
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52158871"
---
# <a name="sql-server-xtp-in-memory-oltp-performance-counters"></a>SQL Server XTP(메모리 내 OLTP) 성능 카운터
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 메모리 내 OLTP 작업을 모니터링하기 위해 성능 모니터에서 사용할 수 있는 개체 및 카운터를 제공합니다. 개체 및 카운터는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 부터 컴퓨터의 특정 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]버전의 모든 인스턴스 간에 공유됩니다.  
  
 과거에는 개체 및 카운터 이름이 *XTP 커서*처럼 **XTP**로 시작되었습니다. [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]부터 이름은 이제 다음 패턴과 같습니다.  
  
-   **SQL Server** *\<version>* **XTP 커서**  
  
 *\<version>* 은 2016과 같은 값입니다.  
  
##  <a name="SQLServerPOs"></a> SQL Server XTP 성능 개체  
 다음 표에서는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능 개체에 대해 설명합니다.  
  
|성능 개체|설명|  
|------------------------|-----------------|  
|[SQL Server XTP 커서](../../relational-databases/performance-monitor/sql-server-xtp-cursors.md)|SQL Server XTP 커서 성능 개체에는 내부 메모리 내 OLTP 엔진 커서와 관련된 카운터가 포함됩니다. 커서는 메모리 내 OLTP 엔진이 [!INCLUDE[tsql](../../includes/tsql-md.md)] 쿼리를 처리하기 위해 사용하는 하위 수준의 기본 구성 요소입니다. 따라서 사용자는 일반적으로 이를 직접 제어하지 않습니다.|  
|[SQL Server XTP 데이터베이스](../../relational-databases/performance-monitor/sql-server-xtp-databases.md)|SQL Server XTP 데이터베이스 성능 개체는 메모리 내 OLTP 데이터베이스 관련 카운터를 제공합니다.|  
|[SQL Server XTP 가비지 수집](../../relational-databases/performance-monitor/sql-server-xtp-garbage-collection.md)|SQL Server XTP 가비지 수집 성능 개체에는 메모리 내 OLTP 엔진의 가비지 수집기와 관련된 카운터가 포함됩니다.|  
|[SQL Server 2016 XTP IO 관리자](../../relational-databases/performance-monitor/sql-server-xtp-io-governor.md)|SQL Server XTP IO 관리자 성능 개체에는 메모리 내 OLTP IO 속도 관리자와 관련된 카운터가 포함되어 있습니다.|
|[SQL Server XTP 가상 프로세서](../../relational-databases/performance-monitor/sql-server-xtp-phantom-processor.md)|SQL Server XTP 가상 프로세서 성능 개체에는 메모리 내 OLTP 엔진의 가상 처리 하위 시스템과 관련된 카운터가 포함됩니다. 이 구성 요소는 SERIALIZABLE 격리 수준에서 실행되는 트랜잭션에서 가상 행을 검색합니다.|  
|[SQL Server XTP 저장소](../../relational-databases/performance-monitor/sql-server-xtp-storage.md)|SQL Server XTP 저장소 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 메모리 내 OLTP 저장소 관련 카운터가 포함됩니다.|  
|[SQL Server XTP 트랜잭션 로그](../../relational-databases/performance-monitor/sql-server-xtp-transaction-log.md)|SQL Server XTP 트랜잭션 로그 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 메모리 내 OLTP 트랜잭션 로깅과 관련된 카운터가 포함됩니다.|  
|[SQL Server XTP 트랜잭션](../../relational-databases/performance-monitor/sql-server-xtp-transactions.md)|SQL Server XTP 트랜잭션 성능 개체에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 메모리 내 OLTP 엔진 트랜잭션과 관련된 카운터가 포함됩니다.|  
  
  
