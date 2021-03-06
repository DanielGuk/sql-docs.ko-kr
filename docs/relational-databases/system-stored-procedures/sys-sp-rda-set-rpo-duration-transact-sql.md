---
title: sys.sp_rda_set_rpo_duration (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 11336658a557d9a2ceced08425a12963dd15782e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47685231"
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (Transact SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  확인 하려면 원격 Azure 데이터베이스를 전체 복원 지정 시간 복원은 필요한 경우 준비 테이블의 SQL Server 유지 하는 마이그레이션된 데이터의 시간 수를 설정 합니다.    
    
 자세한 내용은 참조 하세요. [Stretch Database 마이그레이션된 행을 일시적으로 유지 하 여 Azure 데이터에 대 한 데이터 손실의 위험을 줄입니다](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)합니다.  
   
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>구문    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>인수    
 [ @duration_hrs =] *duration_hrs*    
 시간입니다 (null이 아닌 정수 값)의 마이그레이션된 데이터를 유지 하려면 SQL Server는 현재 스트레치 사용 데이터베이스에 대 한 합니다. 기본 값 및 최 솟 값은 8 시간입니다.    
 
 > [!NOTE]
 > 더 높은 값에는 SQL Server에 더 많은 저장소 공간이 필요합니다.
    
## <a name="permissions"></a>사용 권한    
 Db_owner 권한이 필요합니다.    
    
## <a name="remarks"></a>Remarks    
 실행 하 여 현재 값을 가져올 [sys.sp_rda_get_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)합니다.    
    
## <a name="see-also"></a>관련 항목    
 [sys.sp_rda_get_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [스트레치 사용 데이터베이스 (Stretch Database)를 복원 합니다.](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)    
    
  
