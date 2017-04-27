---
title: "정책 기반 관리 패싯 작업 | Microsoft 문서"
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
- viewing Policy-Based Management facets
- facets [Policy-Based Management], copying
- facets [Policy-Based Management], viewing
- copying Policy-Based Management facets
ms.assetid: 88d025c4-07c2-4e4d-8634-204249a8c82c
caps.latest.revision: 29
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8e7ea0859fb39ea23886b650a71b9f818de76c72
ms.lasthandoff: 04/11/2017

---
# <a name="working-with-policy-based-management-facets"></a>정책 기반 관리 패싯 작업
  정책 기반 관리 패싯은 관리하려는 영역과 관련된 논리적 속성 집합입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에는 여러 가지의 미리 정의된 패싯이 있습니다. 예를 들어 기본적으로 해제되는 기능을 속성으로 정의하는 노출 영역 구성 패싯이 있습니다.  
  
 유사한 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 환경을 여러 개 관리하는 경우 하나의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스에서 패싯을 구성하고 패싯 상태를 파일에 복사한 다음 해당 파일을 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 정책으로 가져올 수 있습니다. 상태가 정책으로 변환되면 정책을 다른 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스, 인스턴스 개체, 데이터베이스 또는 데이터베이스 개체에 적용할 수 있습니다.  
  
 이 항목에서는 패싯 상태를 XML 파일에 복사하는 방법에 대해 설명합니다.  
  
##  <a name="BeforeYouBegin"></a> 사용 권한  
 이 항목의 절차를 수행하려면 msdb 데이터베이스에서 PolicyAdministratorRole 역할의 멤버 자격이 필요합니다.  
  
## <a name="viewing-and-copying-facet-states"></a>패싯 상태 보기 및 복사  
 [SQL Server 개체의 정책 기반 관리 패싯 보기](../../relational-databases/policy-based-management/view-the-policy-based-management-facets-on-a-sql-server-object.md)  
  
 [XML 파일로 정책 기반 관리 패싯 상태 복사](../../relational-databases/policy-based-management/copy-a-policy-based-management-facet-state-to-an-xml-file.md)  
  
## <a name="see-also"></a>참고 항목  
 [정책 기반 관리를 사용하여 서버 관리](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)  
  
  