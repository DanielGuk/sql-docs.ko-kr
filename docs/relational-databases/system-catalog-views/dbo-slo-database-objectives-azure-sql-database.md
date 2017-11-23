---
title: "dbo.slo_database_objectives (Azure SQL 데이터베이스) | Microsoft Docs"
ms.custom:
- MSDN content
- MSDN - SQL DB
ms.date: 06/10/2016
ms.prod: 
ms.reviewer: 
ms.service: sql-database
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dbo.slo_database_objectives
- dbo.slo_database_objectives_TSQL
- slo_database_objectives_TSQL
- slo_database_objectives
dev_langs: TSQL
helpviewer_keywords:
- slo_database_objectives
- dbo.slo_database_objectives
ms.assetid: a522569d-8cfc-4643-a170-1cd291e61eee
caps.latest.revision: "10"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8add6a50bfe0d6e8058b5894309b6cc3b783d86f
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/09/2017
---
# <a name="dboslodatabaseobjectives-azure-sql-database"></a>dbo.slo_database_objectives (Azure SQL 데이터베이스)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

    
> [!IMPORTANT]  
>  **이만 적용 됩니다 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11 합니다.**  
>   
>  에 대 한 [! 포함[ssSDSfull](../system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) (마스터)에서 ALTER DATABASE 작업에 대 한 합니다.   
  
 SQL Database의 SLO(서비스 수준 목표) 할당 상태를 반환합니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|database_name|**sysname**|데이터베이스의 이름입니다.|  
|current_slo|**sysname**|데이터베이스의 현재 SLO입니다.|  
|target_slo|**sysname**|SLO 변경 요청에 지정된 데이터베이스의 대상 SLO입니다.|  
|state_desc|**nvarchar**|SLO의 상태 변경 요청: 완료 또는 보류 중 상태입니다.|  
  
## <a name="permissions"></a>Permissions  
 이 뷰는 가상에 연결할 수 있는 권한 가진 모든 사용자 역할에 사용할 수 있는 **마스터** 데이터베이스입니다.  
  
## <a name="examples"></a>예  
  
```  
SELECT   
database_name=database_name.name   
    , current_slo=current_slo.name   
    , target_slo=target_slo.name   
    , state_desc=database_slo.state_desc   
FROM slo_database_objectives AS database_slo  
INNER JOIN slo_service_objectives AS current_slo ON database_slo.current_objective_id = current_slo.objective_id  
INNER JOIN slo_service_objectives AS target_slo ON database_slo.configured_objective_id = target_slo.objective_id  
INNER JOIN sys.databases AS database_name  ON database_slo.database_id = database_name.database_id;  
  
```  
  
## <a name="see-also"></a>관련 항목:  
 [Premium 데이터베이스 관리](http://go.microsoft.com/fwlink/?LinkID=311927)  
[sys.dm_operation_status(Azure SQL Database)](../system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md) 
