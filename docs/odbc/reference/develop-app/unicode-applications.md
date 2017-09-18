---
title: "유니코드 응용 프로그램 | Microsoft Docs"
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
- Unicode [ODBC], compiling as Unicode application
- Unicode [ODBC], functions
- compiling Unicode applications [ODBC]
- functions [ODBC], Unicode functions
ms.assetid: 7986c623-2792-4e77-bfee-c86cbf84f08d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c99c74a1a294d7d43774fe9d53d169eece98d3ad
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="unicode-applications"></a>유니코드 응용 프로그램
두 가지 방법 중 하나에서 유니코드 응용 프로그램으로 응용 프로그램을 다시 컴파일할 수 있습니다.  
  
-   유니코드 포함 **#define** 에 응용 프로그램에는 Sqlucode.h 헤더 파일이 포함 되어 있습니다.  
  
-   컴파일러의 유니코드 옵션으로 응용 프로그램을 컴파일하십시오. (이 옵션은 다를 수 다른 컴파일러에 대 한 합니다.)  
  
 유니코드 응용 프로그램에 ANSI 응용 프로그램으로 변환 하려면 응용 프로그램을 저장 하 고 유니코드 데이터 전달를 기록 합니다. 또한 대 SQLPOINTER 인수를 지원 하는 함수에 대 한 호출 된 바이트 수를 사용 하도록 변환 되어야 합니다.  
  
 응용 프로그램 (접미사) 없이 ODBC API 함수를 호출 하는 경우 응용 프로그램이 유니코드 응용 프로그램으로 컴파일되면 드라이버 관리자 유니코드 응용 프로그램으로 응용 프로그램을 인식 하 고는 (된유니코드함수에대한함수호출변환* W* 접미사) 기본 드라이버가 유니코드를 지원 합니다. ANSI 응용 프로그램이 호출 접미사 없이 함수를 하면 기본 드라이버 ANSI 지 원하는 경우 드라이버 관리자를 ANSI 것을 변환 합니다. 모두 응용 프로그램 및 드라이버를 지 원하는 동일한 문자 인코딩을 지정 하는 경우 ANSI 응용 프로그램에 대 한 예외) (사용 하 여 드라이버를 통해 호출 드라이버 관리자에 전달 합니다.  
  
 응용 프로그램에서 모두 유니코드 함수를 호출할 수 있습니다 (으로 *W* 접미사) 및 ANSI 함수 (유무에 관계 없이 *A* 접미사). 유니코드 및 ANSI 함수 호출을 혼합할 수 있습니다. 그러나 커서 라이브러리를 사용할 경우, 유니코드 및 ANSI 함수 호출 혼합할 수 없습니다. 커서 라이브러리는 유니코드 또는 ANSI를 혼합 하지 않습니다.  
  
 유니코드 응용 프로그램 또는 ANSI 응용 프로그램으로 컴파일할 수 있도록 응용 프로그램을 작성할 수 있습니다. 이 경우 문자 데이터 형식 SQL_C_TCHAR로 선언할 수 있습니다. 응용 프로그램이 유니코드 응용 프로그램으로 컴파일된 또는 ANSI 응용 프로그램으로 컴파일할 경우 SQL_C_CHAR를 삽입 하는 경우 SQL_C_WCHAR를 삽입 하는 매크로입니다. Length 인수의 크기 변경 (문자열 데이터 형식)에 대 한 응용 프로그램 프로그래머 대 SQLPOINTER 해당 인수로 사용 하는 함수의 주의 해야 ANSI 또는 유니코드 응용 프로그램 인지에 따라 합니다.  
  
 세 가지 방법 중 하나에 함수를 호출할 수 있습니다: 유니코드 전용 함수 호출으로 (으로 *W* 접미사), ANSI 전용 함수 호출으로 (으로 *A* 접미사), 또는 접미사 없음 ODBC 함수 호출으로 합니다. 함수는 세 가지 형식에 대 한 인수는 동일 합니다. SQLCHAR의 함수만 \* 인수 또는 대 SQLPOINTER 인수 문자열을 가리키는 유니코드 및 ANSI 양식이 필요 합니다. 와 같은 문자 유형으로 선언 될 수 있는 인수를 사용 하는 함수에 대 한 **SQLBindCol** 또는 **SQLGetData** (헤드가 없습니다 유니코드와 ANSI 양식)을 유니코드 형식으로 인수를 선언할 수 있습니다 ANSI 입력 하거나 형식 인수를 SQL_C_TCHAR 매크로 C의 경우. 자세한 내용은 참조 [유니코드 데이터](../../../odbc/reference/develop-app/unicode-data.md)합니다.  
  
 유니코드 응용 프로그램으로 작업할 수에 사용할 수 있는 유니코드 드라이버가 없는 경우에 응용 프로그램을 작성할 수 있습니다. 드라이버 관리자 ANSI 유니코드 함수 및 데이터 형식이 매핑됩니다. 에 유니코드에서 ANSI 매핑 수행할 수 있는 몇 가지 제한 사항이 있습니다. 사용 하도록 유니코드 응용 프로그램에 대 한 유니코드 드라이버의 존재를 성능이 향상 되 고 유니코드에서 ANSI 매핑에 내재 된 제한 사항이 제거 됩니다.