---
title: MSreplication_objects (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSreplication_objects
- MSreplication_objects_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_objects system table
ms.assetid: 08f9710d-976d-448e-bead-ac9835e87bc5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cfced92c3cd2cd789ebafb9ee7b03919b4a28612
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47785578"
---
# <a name="msreplicationobjects-transact-sql"></a>MSreplication_objects(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSreplication_objects** 구독자 데이터베이스에서 복제를 사용 하 여 연결 된 각 개체에 대해 하나의 행을 포함 하는 테이블입니다. 이 테이블은 구독 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**publisher**|**sysname**|게시자의 이름입니다.|  
|**publisher_db**|**sysname**|게시자 데이터베이스의 이름입니다.|  
|**게시**|**sysname**|게시의 이름입니다.|  
|**object_name**|**sysname**|개체 이름입니다.|  
|**object_type**|**char(2)**|개체 형식입니다.<br /><br /> **u** = 테이블입니다.<br /><br /> **t** = 트리거.<br /><br /> **p** = 저장된 프로시저입니다.|  
|**article**|**sysname**|개체가 연결된 아티클의 이름입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블&#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
