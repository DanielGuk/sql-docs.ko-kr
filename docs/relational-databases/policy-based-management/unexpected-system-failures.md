---
title: "예기치 않은 시스템 오류 | Microsoft 문서"
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
- Best Practices [Database Engine]
ms.assetid: 1679bf9e-a2ef-4f90-8907-a002f7341a7d
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6ea8adc9d59ca0a41a5daf09168ff8e3aa709972
ms.lasthandoff: 04/11/2017

---
# <a name="unexpected-system-failures"></a>예기치 않은 시스템 오류
  이 규칙은 컴퓨터 이벤트 로그에서 SYSTEM 이벤트 6008을 검사합니다. 이 이벤트는 예기치 않은 시스템 종료를 나타냅니다. 시스템이 불안정하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 호스팅하는 데 필요한 안정성 및 무결성을 제공하지 않을 수 있습니다.  
  
## <a name="best-practices-recommendations"></a>최선의 구현 방법 권장 사항  
 서버가 예기치 않게 다시 시작되는 원인을 찾아 즉시 해결하거나 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 다른 컴퓨터로 이동합니다.  
  
  