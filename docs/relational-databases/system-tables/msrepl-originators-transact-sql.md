---
title: MSrepl_originators (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSrepl_originators_TSQL
- MSrepl_originators
dev_langs:
- TSQL
helpviewer_keywords:
- MSrepl_originators system table
ms.assetid: a3ac20a6-73f6-4fdc-ad5f-5f72746c9871
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e731baa8a0c0bbff2cea638712fcad10b9ec58e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647891"
---
# <a name="msreploriginators-transact-sql"></a>MSrepl_originators(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **MSrepl_originators** 테이블 트랜잭션이 시작 된 업데이트할 수 있는 각 구독자에 대 한 하나의 행을 포함 합니다. 이 테이블은 배포 데이터베이스에 저장됩니다.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|업데이트 구독자를 식별합니다.|  
|**publisher_database_id**|**int**|게시 데이터베이스를 식별합니다.|  
|**srvname**|**sysname**|업데이트 서버의 이름입니다.|  
|**dbname**|**sysname**|업데이트 데이터베이스의 이름입니다.|  
|**publication_id**|**int**|게시를 식별합니다.|  
|**dbversion**|**int**|데이터베이스 버전을 식별합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [복제 테이블 &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [복제 뷰&#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
