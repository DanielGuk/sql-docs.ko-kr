---
title: bcp_exec | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apiname:
- bcp_exec
apilocation:
- sqlncli11.dll
apitype: DLLExport
helpviewer_keywords:
- bcp_exec function
ms.assetid: b23ea2cc-8545-4873-b0c1-57e76b0a3a7b
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 762384c9bd57db037b894e8522f0eb0d4b5d2392
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47627301"
---
# <a name="bcpexec"></a>bcp_exec
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  데이터베이스 테이블과 사용자 파일 간에 데이터에 대한 전체 대량 복사를 실행합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
RETCODE bcp_exec (  
        HDBC hdbc,  
        LPDBINT pnRowsProcessed);  
```  
  
## <a name="arguments"></a>인수  
 *hdbc*  
 대량 복사가 가능한 ODBC 연결 핸들입니다.  
  
 *pnRowsProcessed*  
 DBINT에 대한 포인터입니다. **bcp_exec** 함수는 성공적으로 복사된 행 수로 이 DBINT를 채웁니다. *pnRowsProcessed* 가 NULL이면 **bcp_exec**에서 이 인수를 무시합니다.  
  
## <a name="returns"></a>반환 값  
 SUCCEED, SUCCEED_ASYNC 또는 FAIL. 모든 행이 복사되면 **bcp_exec** 함수가 SUCCEED를 반환합니다 비동기 대량 복사 작업이 보류 중이면**bcp_exec** 가 SUCCEED_ASYNC를 반환합니다. **bcp_exec** 완전히 실패 또는 오류를 생성 하는 행 수가 다음을 사용 하 여 BCPMAXERRS에 지정 된 값에 도달할 경우 FAIL을 반환 합니다 [bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)합니다. BCPMAXERRS의 기본값은 10입니다. BCPMAXERRS 옵션은 데이터 파일에서 행을 읽는 동안 공급자가 발견하는 구문 오류의 수에만 영향을 주고 서버로 전송되는 행 수에는 영향을 주지 않습니다. 행에서 오류를 발견하면 서버에서 일괄 처리를 중단합니다. 성공적으로 복사된 행 수를 보려면 *pnRowsProcessed* 매개 변수를 확인하십시오.  
  
## <a name="remarks"></a>Remarks  
 이 함수는 값에 따라 데이터베이스 테이블 또는 그 반대의 경우는 사용자 파일 간에 데이터를 복사 합니다 *eDirection* 에 매개 변수 [bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)합니다.  
  
 **bcp_exec**를 호출하기 전에 올바른 사용자 파일 이름을 지정하여 **bcp_init** 를 호출합니다. 그렇게 하지 않으면 오류가 반환됩니다.  
  
 **bcp_exec** 는 무한정 보류될 수 있는 유일한 대량 복사 함수입니다. 따라서 비동기 모드를 지원하는 유일한 대량 복사 함수입니다. 비동기 모드를 설정 하려면 사용 하 여 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) 호출 하기 전에 SQL_ATTR_ASYNC_ENABLE을 sql_async_enable_on으로 설정 하려면 **bcp_exec**합니다. 완료 테스트를 하려면 같은 매개 변수를 사용하여 **bcp_exec** 를 호출합니다. 대량 복사가 완료되지 않은 경우 **bcp_exec** 가 SUCCEED_ASYNC를 반환합니다. 또한 서버로 전송된 행 수에 대한 상태 개수를 *pnRowsProcessed* 에 반환합니다. 서버로 전송된 행은 일괄 처리의 끝에 도달할 때까지 커밋되지 않습니다.  
  
 대량 복사에서 시작 하 여 중단에 대 한 내용은 변경 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]를 참조 하십시오 [대량 복사 작업 수행 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md).  
  
## <a name="example"></a>예제  
 다음 예에서는 **bcp_exec**를 사용하는 방법을 보여 줍니다.  
  
```  
// Variables like henv not specified.  
HDBC      hdbc;  
DBINT      nRowsProcessed;  
  
// Application initiation, get an ODBC environment handle, allocate the  
// hdbc, and so on.  
...   
  
// Enable bulk copy prior to connecting on allocated hdbc.  
SQLSetConnectAttr(hdbc, SQL_COPT_SS_BCP, (SQLPOINTER) SQL_BCP_ON,  
   SQL_IS_INTEGER);  
  
// Connect to the data source, return on error.  
if (!SQL_SUCCEEDED(SQLConnect(hdbc, _T("myDSN"), SQL_NTS,  
   _T("myUser"), SQL_NTS, _T("myPwd"), SQL_NTS)))  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Initialize bulk copy.   
if (bcp_init(hdbc, _T("pubs..authors"), _T("authors.sav"), NULL, DB_OUT)  
   == FAIL)  
   {  
   // Raise error and return.  
   return;  
   }  
  
// Now, execute the bulk copy.   
if (bcp_exec(hdbc, &nRowsProcessed) == FAIL)  
   {  
   if (nRowsProcessed == -1)  
      {  
      printf_s("No rows processed on bulk copy execution.\n");  
      }  
   else  
      {  
      printf_s("Incomplete bulk copy.   Only %ld row%s copied.\n",  
         nRowsProcessed, (nRowsProcessed == 1) ? "": "s");  
      }  
   return;  
   }  
  
printf_s("%ld rows processed.\n", nRowsProcessed);  
  
// Carry on.  
```  
  
## <a name="see-also"></a>관련 항목  
 [대량 복사 함수](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
