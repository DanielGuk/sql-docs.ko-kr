---
title: "SQLSetScrollOptions (커서 라이브러리) | Microsoft Docs"
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
- SQLSetScrollOptions function [ODBC], Cursor Library
ms.assetid: c5c0ac6d-a6c1-4077-8186-1644df1944f8
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c029dbb9906c4d7d738e0e705dd02e437b6c1bec
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-cursor-library"></a>SQLSetScrollOptions (커서 라이브러리)
> [!IMPORTANT]  
>  이 기능은 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는이 기능을 사용 하지 마십시오 하 고 현재이 기능을 사용 하는 응용 프로그램은 수정 하세요. 드라이버의 커서 기능을 사용 하는 것이 좋습니다.  
  
 이 항목의 사용을 설명는 **SQLSetScrollOptions** 커서 라이브러리의 함수가 있습니다. 에 대 한 일반적인 내용은 **SQLSetScrollOptions**, 참조 [SQLSetScrollOptions 함수](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)합니다.  
  
 커서 라이브러리가 지원 **SQLSetScrollOptions** ; 이전 버전과 호환성을 위해서만 응용 프로그램 대신 사용 해야 SQL_ATTR_CURSOR_TYPE, SQL_ATTR_CONCURRENCY 마우스 SQL_ATTR_ROW_ARRAY_SIZE 문 특성입니다.