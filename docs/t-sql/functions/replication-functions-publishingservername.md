---
title: PUBLISHINGSERVERNAME (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 16
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a5aeeb414f9c980429d20f123e1f9c986b147eee
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="replication-functions---publishingservername"></a>PUBLISHINGSERVERNAME 복제 함수-
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  데이터베이스 미러링 세션에 참여하는 게시된 데이터베이스의 원래 게시자 이름을 반환합니다. 이 함수는 게시 데이터베이스의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 게시자 인스턴스에서 실행됩니다. 이 함수를 사용하여 게시된 데이터베이스의 원래 게시자를 확인할 수 있습니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
PUBLISHINGSERVERNAME()  
```  
  
## <a name="return-types"></a>반환 형식  
 **nvarchar**  
  
## <a name="remarks"></a>주의  
 PUBLISHINGSERVERNAME은 모든 유형의 복제에 사용됩니다.  
  
 데이터베이스 미러링 세션이 게시자와 미러링 파트너 인스턴스 간의 게시 데이터베이스에 있는 경우에는 PUBLISHINGSERVERNAME이 사용됩니다.  
  
 이 함수는 게시 데이터베이스의 컨텍스트 내에서 실행해야 합니다. PUBLISHINGSERVERNAME을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 미러 서버 인스턴스에 있는 게시 데이터베이스에서 실행하면 데이터베이스를 원래 게시한 게시자의 이름이 반환됩니다. 이 함수를 미러 서버 인스턴스에 있는 게시되지 않은 데이터베이스에서 실행하거나 장애 조치(Failover) 후 미러 서버 인스턴스에서 게시한 데이터베이스에서 실행하면 해당 미러 서버 인스턴스의 이름이 반환됩니다. 이 함수를 원래 게시자 인스턴스에서 실행하면 게시자 이름이 반환됩니다.  
  
## <a name="see-also"></a>관련 항목:  
 [데이터베이스 미러링 및 복제&#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-and-replication-sql-server.md)   
 [복제 함수 &#40; Transact SQL &#41;](http://msdn.microsoft.com/library/53702dee-de58-47d5-a552-7f32000f77d4)  
  
  