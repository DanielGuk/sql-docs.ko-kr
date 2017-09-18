---
title: "SQLGetStmtOption (커서 라이브러리) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Cursor Library
ms.assetid: 986170b3-fba8-4323-9224-60b381c7effb
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 17f6a57b37b95c3a295ffd3bb5270ae82e955aba
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetstmtoption-cursor-library"></a>SQLGetStmtOption (커서 라이브러리)
> [!IMPORTANT]  
>  이 기능은 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는이 기능을 사용 하지 마십시오 하 고 현재이 기능을 사용 하는 응용 프로그램은 수정 하세요. 드라이버의 커서 기능을 사용 하는 것이 좋습니다.  
  
 이 항목의 사용을 설명는 **SQLGetStmtOption** 커서 라이브러리의 함수가 있습니다. 에 대 한 일반적인 내용은 **SQLGetStmtOption**, 참조 [SQLGetStmtOption 함수](../../../odbc/reference/syntax/sqlgetstmtoption-function.md)합니다.  
  
 커서 라이브러리는 다음 문 옵션을 지원 합니다. **SQLGetStmtOption**:  
  
|||  
|-|-|  
|SQL_BIND_TYPE|SQL_ROW_NUMBER|  
|SQL_CONCURRENCY|SQL_ROWSET_SIZE|  
|에서는 SQL_CURSOR_TYPE|SQL_SIMULATE_CURSOR|  
|SQL_GET_BOOKMARK||