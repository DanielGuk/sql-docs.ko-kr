---
title: 지원 되는 동시성 모델 (Visual FoxPro ODBC 드라이버) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8528ecb2f34d3f0ef7120c7047865ab5f6c1a72
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47612671"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>지원되는 동시성 모델(Visual FoxPro ODBC 드라이버)
Visual FoxPro ODBC 드라이버 지원 *읽기 전용 동시성*합니다. 응용 프로그램에서 호출할 수 있습니다 [SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) SQL_CONCUR_READ_ONLY SQL_CONCURRENCY 옵션을 사용 하 여 합니다.  
  
 자세한 내용은 참조는 [ODBC 프로그래머 참조](../../odbc/reference/odbc-programmer-s-reference.md).  
  
## <a name="read-only-concurrency"></a>읽기 전용 동시성  
 커서를 업데이트할 수 없습니다.  
  
## <a name="row-versioning"></a>행 버전 관리(row versioning)  
 기본적으로 타임 스탬프가 지원 업데이트 시 행 버전 비교 됩니다.
