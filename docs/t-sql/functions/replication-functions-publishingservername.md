---
title: PUBLISHINGSERVERNAME(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- PUBLISHINGSERVERNAME_TSQL
- PUBLISHINGSERVERNAME
dev_langs:
- TSQL
helpviewer_keywords:
- PUBLISHINGSERVERNAME function
- Publishers [SQL Server replication], names
ms.assetid: e7c278e5-ab23-419e-ab3e-3bb20b0636df
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f115ea901a6fe7462ee40664a84a39ae4cfc3012
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51699041"
---
# <a name="replication-functions---publishingservername"></a>복제 함수 - PUBLISHINGSERVERNAME
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 미러링 세션에 참여하는 게시된 데이터베이스의 원래 게시자 이름을 반환합니다. 이 함수는 게시 데이터베이스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 인스턴스에서 실행됩니다. 이 함수를 사용하여 게시된 데이터베이스의 원래 게시자를 확인할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>반환 형식  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 PUBLISHINGSERVERNAME은 모든 유형의 복제에 사용됩니다.  
  
 데이터베이스 미러링 세션이 게시자와 미러링 파트너 인스턴스 간의 게시 데이터베이스에 있는 경우에는 PUBLISHINGSERVERNAME이 사용됩니다.  
  
 이 함수는 게시 데이터베이스의 컨텍스트 내에서 실행해야 합니다. PUBLISHINGSERVERNAME을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 미러 서버 인스턴스에 있는 게시 데이터베이스에서 실행하면 데이터베이스를 원래 게시한 게시자의 이름이 반환됩니다. 이 함수를 미러 서버 인스턴스에 있는 게시되지 않은 데이터베이스에서 실행하거나 장애 조치(Failover) 후 미러 서버 인스턴스에서 게시한 데이터베이스에서 실행하면 해당 미러 서버 인스턴스의 이름이 반환됩니다. 이 함수를 원래 게시자 인스턴스에서 실행하면 게시자 이름이 반환됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [복제 함수&#40;Transact-SQL&#41;](https://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  
