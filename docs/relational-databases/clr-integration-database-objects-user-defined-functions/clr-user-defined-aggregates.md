---
title: CLR 사용자 정의 집계 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- aggregate functions [CLR integration]
- custom aggregates [CLR integration]
- calculations [CLR integration]
- user-defined functions [CLR integration]
ms.assetid: bad9b7e8-5967-4afa-8dc8-6d840faf9372
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: d7194f151caf4495e448bbdde649d5bd77cc683c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47776671"
---
# <a name="clr-user-defined-aggregates"></a>CLR 사용자 정의 집계
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  집계 함수는 값 집합에 대한 계산을 수행하고 단일 값을 반환합니다. 일반적으로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 와 같은 기본 제공 집계 함수만 지원 했습니다 **합계** 하거나 **최대**, 입력된 스칼라 값 집합에서 작동 하 고 단일 집계를 생성 합니다. 해당 집합에서 값입니다. 이제 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]와 [!INCLUDE[msCoName](../../includes/msconame-md.md)] .NET Framework CLR(공용 언어 런타임)의 통합을 통해 개발자는 관리 코드로 사용자 지정 집계 함수를 만들어 [!INCLUDE[tsql](../../includes/tsql-md.md)]이나 다른 관리 코드에서 이러한 함수에 액세스할 수 있게 만들 수 있습니다.  
  
 다음 표에서는 이 섹션에서 다루는 항목을 나열합니다.  
  
 [CLR 사용자 정의 집계 요구 사항](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates-requirements.md)  
 CLR 사용자 정의 집계 함수를 구현하기 위한 요구 사항에 대해 간략히 설명합니다.  
  
 [CLR 사용자 정의 집계 함수 호출](../../relational-databases/clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregate-invoking-functions.md)  
 사용자 정의 집계를 호출하는 방법에 대해 설명합니다.  
  
  
