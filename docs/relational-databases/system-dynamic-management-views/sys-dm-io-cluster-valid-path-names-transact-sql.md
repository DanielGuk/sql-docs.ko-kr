---
title: sys.dm_io_cluster_valid_path_names (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_io_cluster_valid_path_names
- dm_io_cluster_valid_path_names_TSQL
- sys.dm_io_cluster_valid_path_names_TSQL
- dm_io_cluster_valid_path_names
dev_langs:
- TSQL
helpviewer_keywords:
- dm_io_cluster_valid_path_names
- sys.dm_io_cluster_valid_path_names
- cluster valid path names
- csv name
- cluster shared volume names
ms.assetid: 5bc8a0e5-6c72-425b-8c58-f276eb9add2c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9ea5453465fe27cfe4456f7da1fdb2690c6953c3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47645247"
---
# <a name="sysdmioclustervalidpathnames-transact-sql"></a>sys.dm_io_cluster_valid_path_names(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  클러스터된 공유 볼륨을 비롯한 모든 유효한 공유 디스크에서 SQL Server 장애 조치(failover) 클러스터 인스턴스에 대한 정보를 반환합니다. 인스턴스가 클러스터되지 않은 경우 빈 행 집합이 반환됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**path_name**|**Nvarchar(512)**|데이터베이스 및 로그 파일의 루트 디렉터리로 사용할 수 있는 볼륨 탑재 지점 또는 드라이브 경로입니다. Null을 허용하지 않습니다.|  
|**cluster_owner_node**|**Nvarchar(64)**|드라이브의 현재 소유자입니다. CSV(클러스터 공유 볼륨)의 경우 소유자는 메타데이터 서버를 호스팅하는 노드입니다. Null을 허용하지 않습니다.|  
|**is_cluster_shared_volume**|**Bit**|이 경로가 위치한 드라이브가 클러스터 공유 볼륨이면 1을 반환하고, 그렇지 않으면 0을 반환합니다.|  
  
## <a name="remarks"></a>Remarks  
 SQL Server FCI(장애 조치(failover) 클러스터 인스턴스)는 데이터 및 로그 파일 저장을 위해 FCI의 모든 노드 간에 공유 저장소를 사용해야 합니다. 이 뷰에 나열된 디스크는 인스턴스와 연결된 클러스터 리소스 그룹에 있는 디스크이며 데이터 또는 로그 파일 저장에 사용할 수 있는 유일한 디스크입니다.  
  
> [!NOTE]  
>  이 보기 바뀝니다 [sys.dm_io_cluster_shared_drives &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md) 릴리스에서 합니다.  
  
## <a name="permissions"></a>사용 권한  
 사용자는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 대한 VIEW SERVER STATE 권한이 있어야 합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 sys.dm_io_cluster_valid_path_names를 사용하여 클러스터형 서버 인스턴스의 공유 드라이브를 결정합니다.  
  
```  
SELECT * FROM sys.dm_io_cluster_valid_path_names;  
```  
  
## <a name="see-also"></a>관련 항목  
 [sys.dm_os_cluster_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [동적 관리 뷰 및 함수&#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

