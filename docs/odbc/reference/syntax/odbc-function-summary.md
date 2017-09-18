---
title: "ODBC 함수 요약 | Microsoft Docs"
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
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9441a955eaa4a9001b7acd655f7753e32f49e68e
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="odbc-function-summary"></a>ODBC 함수 요약
다음 표에서 ODBC 함수를 그룹화 하는 작업의 유형별로 목록과 규칙 지정 및 각 함수의 용도에 대 한 간략 한 설명을 포함 되어 있습니다. 규칙에 따라 지정에 대 한 자세한 내용은 참조 [ODBC 및 표준 CLI](../../../odbc/reference/odbc-and-the-standard-cli.md)합니다. 구문 및 각 함수에 대 한 의미 체계에 대 한 자세한 내용은 참조 [ODBC API 참조](../../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
 응용 프로그램에서 호출할 수는 **SQLGetInfo** 드라이버에 대 한 준수 정보는 함수입니다. 응용 프로그램이 호출할 수는 드라이버 특정 함수에 대 한 지원에 대 한 정보를 얻으려면 **SQLGetFunctions**합니다.  
  
|태스크|함수 이름|규칙|용도|  
|----------|-------------------|-----------------|-------------|  
|데이터 원본에 연결|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|환경, 연결, 문 또는 설명자 핸들을 가져옵니다.|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|데이터 원본 이름, 사용자 ID와 암호 여 특정 드라이버에 연결합니다.|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|연결 문자열 또는 드라이버 관리자와 드라이버는 사용자에 대 한 연결 대화 상자를 표시 하는 요청 하 여 특정 드라이버에 연결 합니다.|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|연속 된 수준의 연결 특성 및 유효한 특성 값을 반환합니다. 각 연결 특성에 대 한 값을 지정 하는 경우 데이터 원본에 연결 합니다.|  
|드라이버 및 데이터 원본에 대 한 정보 얻기|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|사용 가능한 데이터 원본 목록을 반환합니다.<br /><br /> 설치 된 드라이버와 해당 특성의 목록을 반환합니다.|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|특정 드라이버 및 데이터 원본에 대 한 정보를 반환합니다.|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|지원 되는 드라이버 함수를 반환 합니다.|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|지원 되는 데이터 형식에 대 한 정보를 반환 합니다.|  
|설정 하 고 드라이버 특성 검색|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|연결 특성을 설정합니다.<br /><br /> 연결 특성의 값을 반환 합니다.|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|환경 특성을 설정합니다.|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|환경 특성의 값을 반환합니다.|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|문 특성을 설정합니다.|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|문 특성의 값을 반환 합니다.|  
|설정 및 설명자 필드를 검색 합니다.|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|단일 설명자 필드의 값을 반환합니다.<br /><br /> 여러 설명자 필드의 값을 반환합니다.|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|단일 설명자 필드를 설정합니다.|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|여러 설명자 필드를 설정합니다.|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|다른 하나의 설명자 핸들에서 설명자 정보를 복사합니다.|  
|요청 SQL 준비|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|나중에 실행할 SQL 문을 준비합니다.|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|SQL 문의 매개 변수에 대 한 저장소를 할당합니다.|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|문 핸들에 연결 된 커서 이름을 반환 합니다.|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|커서 이름을 지정합니다.|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|커서 동작을 제어 하는 옵션을 설정 합니다.|  
|요청 제출|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|준비된 문을 실행합니다.<br /><br /> 문을 실행합니다.|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|드라이버에서 변환 되는 SQL 문의 텍스트를 반환 합니다.|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|문에서 특정 매개 변수에 대 한 설명을 반환합니다.|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|문에 매개 변수 개수를 반환합니다.|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|와 함께 사용할 **SQLPutData** 실행 시 매개 변수 데이터를 제공 합니다. (긴 데이터 값에 유용 합니다.)|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|매개 변수에 대해 데이터 값의 전체 또는 일부를 보냅니다. (긴 데이터 값에 유용 합니다.)|  
|결과 및 결과 대 한 정보 검색|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|삽입, 업데이트 또는 삭제 요청에 영향을 받는 행 수를 반환 합니다.<br /><br /> 결과 집합의 열 수를 반환합니다.|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|결과 집합의 열에에서 설명합니다.|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|결과 집합에 있는 열의 특성에 설명 합니다.|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|결과 열에 대 한 저장소를 할당 하 고 데이터 형식을 지정 합니다.|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|여러 결과 행을 반환합니다.|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|스크롤 가능한 결과 행을 반환합니다.|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|전체 또는 일부 반환 결과의 한 행의 한 열에 설정합니다. (긴 데이터 값에 유용 합니다.)|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|인출 된 데이터 블록 내에서 커서를 배치 하 고 행 집합의 데이터를 새로 고치려면 또는 업데이트 하거나 결과 집합의 데이터를 삭제 하는 응용 프로그램을 허용 합니다.|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|대량 삽입 및 대량 책갈피 수행 업데이트 등과 같은 작업을 삭제 하 고 책갈피 하 여 인출 합니다.|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|더 많은 결과 집합 사용 가능한 및,이 경우 다음 결과 집합에 대 한 처리를 초기화 합니다. 있는지 여부를 결정 합니다.|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|추가 진단 정보 (진단 데이터 구조의 단일 필드)를 반환합니다.|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|추가 진단 정보 (진단 데이터 구조의 여러 필드)를 반환합니다.|  
|데이터 원본 시스템 테이블 (카탈로그 함수)에 대 한 정보 얻기|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> 그룹 열기|열 및 하나 이상의 테이블에 대 한 연결된 권한 목록을 반환합니다.<br /><br /> 지정 된 테이블의 열 이름 목록을 반환합니다.|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|지정 된 테이블에 있는 외래 키를 구성 하는 열 이름의 목록을 반환 합니다.|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|테이블에 대 한 기본 키를 구성 하는 열 이름의 목록을 반환 합니다.|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|결과 집합에 지정 된 프로시저를 구성 하는 열 뿐만 아니라 입력 및 출력 매개 변수 목록을 반환 합니다.|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|특정 데이터 원본에 저장 된 프로시저 이름 목록을 반환 합니다.|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|그룹 열기|지정된 된 테이블의 행을 고유 하 게 식별 하는 열 또는 행에 있는 값이 트랜잭션에 의해 업데이트 될 때 자동으로 업데이트는 열의 최적 집합에 대 한 정보를 반환 합니다.|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|단일 테이블 및 테이블에 연결 된 인덱스의 목록에 대 한 통계를 반환 합니다.|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|테이블 및 각 테이블에 연결 된 권한 목록을 반환 합니다.|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|그룹 열기|특정 데이터 원본에 저장 된 테이블 이름 목록을 반환 합니다.|  
|문을 종료합니다.|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|문 처리 종료, 보류 중인 결과가 삭제 하 고, 필요에 따라 문 핸들에 연결 된 모든 리소스를 해제 합니다.|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|문 핸들에서 열려 있는 커서를 닫습니다.|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|문에서 처리를 취소합니다.|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|문 또는 연결에서 처리를 취소합니다.|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|커밋 또는 트랜잭션을 롤백합니다.|  
|연결 종료|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|연결을 닫습니다.<br /><br /> 환경, 연결, 문 또는 설명자 핸들을 해제합니다.|