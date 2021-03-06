---
title: sqlsrv_prepare | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_prepare
apitype: NA
helpviewer_keywords:
- executing queries
- API Reference, sqlsrv_prepare
- sqlsrv_prepare
ms.assetid: 8c74c697-3296-4f5d-8fb9-e361f53f19a6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dc82d2860bf5e927556103a6c508b1cd662e4b42
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602923"
---
# <a name="sqlsrvprepare"></a>sqlsrv_prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

지정된 연결과 관련된 문 리소스를 만듭니다. 이 함수는 여러 개의 쿼리를 실행하는 데 유용합니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
sqlsrv_prepare(resource $conn, string $tsql [, array $params [, array $options]])  
```  
  
#### <a name="parameters"></a>매개 변수  
*$conn*: 만들어진 문과 연결된 연결 리소스입니다.  
  
*$tsql*: 만들어진 명령문에 해당하는 Transact-SQL 식입니다.  
  
*$params* [선택 사항]: 매개 변수가 있는 쿼리의 매개 변수에 해당하는 값의 **배열**입니다. 배열의 각 요소는 다음 중 하나일 수 있습니다.
  
-   리터럴 값입니다.  
  
-   PHP 변수에 대한 참조입니다.  
  
-   다음 구조체를 가진 **배열** 입니다.  
  
    ```  
    array(&$value [, $direction [, $phpType [, $sqlType]]])  
    ```  
  
    > [!NOTE]  
    > 쿼리 매개 변수로 전달된 변수는 값 대신 참조로 전달되어야 합니다. 예를 들어 `&$myVariable` 대신 `$myVariable`을 전달합니다. by-value 매개 변수가 있는 쿼리가 실행될 때 PHP 경고가 발생합니다.  
  
    다음 표에서는 이러한 배열 요소를 설명합니다.  
  
    |요소|설명|  
    |-----------|---------------|  
    |*&$value*|PHP 변수에 대한 리터럴 값 또는 참조입니다.|  
    |*$direction*[선택 사항]|매개 변수 방향을 나타내기 위해 사용되는 다음 **SQLSRV_PARAM_\*** 상수 중 하나입니다. **SQLSRV_PARAM_IN**, **SQLSRV_PARAM_OUT**, **SQLSRV_PARAM_INOUT**. 기본값은 **SQLSRV_PARAM_IN**입니다.<br /><br />PHP 상수에 대한 자세한 내용은 [상수&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)를 참조하세요.|  
    |*$phpType*[선택 사항]|반환된 값의 PHP 데이터 형식을 지정하는 **SQLSRV_PHPTYPE_\*** 상수입니다.|  
    |*$sqlType*[선택 사항]|입력 값의 SQL Server 데이터 형식을 지정하는 **SQLSRV_SQLTYPE_\*** 상수입니다.|  
  
*$options* [선택 사항]: 쿼리 속성을 설정하는 결합형 배열입니다. 다음 표는 지원되는 키와 해당 값을 나열합니다.  
  
|Key|지원되는 값|설명|  
|-------|--------------------|---------------|  
|QueryTimeout|양의 정수 값입니다.|쿼리 시간 제한(초)을 설정합니다. 기본적으로 드라이버가 결과를 무한정 기다립니다.|  
|SendStreamParamsAtExec|**true** 또는 **false**<br /><br />기본값은 **true**입니다.|실행 시 모든 스트림 데이터를 보내거나(**true**) 스트림 데이터를 청크로 보내도록(**false**) 드라이버를 구성합니다. 기본적으로 이 값은 **true**로 설정되어 있습니다. 자세한 내용은 [sqlsrv_send_stream_data](../../connect/php/sqlsrv-send-stream-data.md)을 참조하세요.|  
|스크롤 가능|SQLSRV_CURSOR_FORWARD<br /><br />SQLSRV_CURSOR_STATIC<br /><br />SQLSRV_CURSOR_DYNAMIC<br /><br />SQLSRV_CURSOR_KEYSET<br /><br />SQLSRV_CURSOR_CLIENT_BUFFERED|이러한 값에 대한 자세한 내용은 [커서 유형 지정 및 행 선택](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)을 참조하세요.|  
  
## <a name="return-value"></a>반환 값  
문 리소스입니다. 문 리소스를 만들 수 없는 경우 **false** 가 반환됩니다.  
  
## <a name="remarks"></a>Remarks  
변수를 매개 변수로 사용하는 문을 준비할 때 변수가 문에 바인딩됩니다. 이는 변수 값을 업데이트하는 경우 다음에 문을 실행할 때 업데이트된 매개 변수 값으로 실행한다는 것입니다.  
  
**sqlsrv_prepare**와 **sqlsrv_execute**의 조합은 문 준비와 문 실행을 두 개의 함수 호출로 분리하고 매개 변수가 있는 쿼리를 실행하는 데 사용할 수 있습니다. 이 함수는 각 실행에 다른 매개 변수 값을 사용하여 문을 여러 번 실행하는 데 이상적입니다.  
  
많은 양의 정보를 읽고 쓰기 위한 대체 전략은 [SQL 문 일괄 처리](../../odbc/reference/develop-app/batches-of-sql-statements.md) 및 [BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md)를 참조하세요.  
  
자세한 내용은 [방법: SQLSRV 드라이버를 사용하여 날짜 및 시간 형식을 문자열로 검색](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)을 참조하세요.  
  
## <a name="example"></a>예제  
다음 예제에서는 문을 준비하고 실행합니다. 명령문은 실행될 때([sqlsrv_execute 참조](../../connect/php/sqlsrv-execute.md)) AdventureWorks 데이터베이스의 *Sales.SalesOrderDetail* 테이블에 있는 필드를 업데이트합니다. 이 예제에서는 SQL Server 및 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 데이터베이스가 로컬 컴퓨터에 설치된 것으로 가정합니다. 모든 출력은 명령줄에서 예제가 실행될 때 콘솔에 기록됩니다.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up Transact-SQL query. */  
$tsql = "UPDATE Sales.SalesOrderDetail   
         SET OrderQty = ?   
         WHERE SalesOrderDetailID = ?";  
  
/* Assign parameter values. */  
$param1 = 5;  
$param2 = 10;  
$params = array(&$param1, &$param2);  
  
/* Prepare the statement. */  
if ($stmt = sqlsrv_prepare($conn, $tsql, $params)) {
    echo "Statement prepared.\n";  
} else {  
    echo "Statement could not be prepared.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement. */  
if (sqlsrv_execute($stmt)) {  
    echo "Statement executed.\n";  
} else {  
    echo "Statement could not be executed.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Free the statement and connection resources. */  
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
## <a name="example"></a>예제  
다음 예제에서는 문을 준비한 다음 다른 매개 변수 값으로 다시 실행하는 방법을 보여 줍니다. 예제에서는 AdventureWorks 데이터베이스의 *Sales.SalesOrderDetail* 테이블에 있는 *OrderQty* 열을 업데이트합니다. 업데이트가 발생한 후 업데이트가 성공했는지 확인하기 위해 데이터베이스가 쿼리됩니다. 이 예제에서는 SQL Server 및 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 데이터베이스가 로컬 컴퓨터에 설치된 것으로 가정합니다. 모든 출력은 명령줄에서 예제가 실행될 때 콘솔에 기록됩니다.  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array("Database"=>"AdventureWorks");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
     echo "Could not connect.\n";  
     die(print_r(sqlsrv_errors(), true));  
}  
  
/* Define the parameterized query. */  
$tsql = "UPDATE Sales.SalesOrderDetail  
         SET OrderQty = ?  
         WHERE SalesOrderDetailID = ?";  
  
/* Initialize parameters and prepare the statement. Variables $qty  
and $id are bound to the statement, $stmt1. */  
$qty = 0; $id = 0;  
$stmt1 = sqlsrv_prepare($conn, $tsql, array(&$qty, &$id));  
if ($stmt1) {  
    echo "Statement 1 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Set up the SalesOrderDetailID and OrderQty information. This array  
maps the order ID to order quantity in key=>value pairs. */  
$orders = array(1=>10, 2=>20, 3=>30);  
  
/* Execute the statement for each order. */  
foreach ($orders as $id => $qty) {  
    // Because $id and $qty are bound to $stmt1, their updated  
    // values are used with each execution of the statement.   
    if (sqlsrv_execute($stmt1) === false) {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
echo "Orders updated.\n";  
  
/* Free $stmt1 resources.  This allows $id and $qty to be bound to a different statement.*/  
sqlsrv_free_stmt($stmt1);  
  
/* Now verify that the results were successfully written by selecting   
the newly inserted rows. */  
$tsql = "SELECT OrderQty   
         FROM Sales.SalesOrderDetail   
         WHERE SalesOrderDetailID = ?";  
  
/* Prepare the statement. Variable $id is bound to $stmt2. */  
$stmt2 = sqlsrv_prepare($conn, $tsql, array(&$id));  
if ($stmt2) {  
    echo "Statement 2 prepared.\n";  
} else {  
    echo "Error in statement preparation.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
/* Execute the statement for each order. */  
foreach (array_keys($orders) as $id)  
{  
    /* Because $id is bound to $stmt2, its updated value   
    is used with each execution of the statement. */  
    if (sqlsrv_execute($stmt2)) {  
        sqlsrv_fetch($stmt2);  
        $quantity = sqlsrv_get_field($stmt2, 0);  
        echo "Order $id is for $quantity units.\n";  
    } else {  
        echo "Error in statement execution.\n";  
        die(print_r(sqlsrv_errors(), true));  
    }  
}  
  
/* Free $stmt2 and connection resources. */  
sqlsrv_free_stmt($stmt2);  
sqlsrv_close($conn);  
?>  
```  
  
> [!NOTE]
> 값을 바인딩하는 경우 입력으로 문자열을 사용 하는 것이 좋습니다.는 [소수 또는 숫자 열](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql) PHP에 대 한 전체 자릿수를 제한적으로 되도록 정밀도 정확도 [부동 소수점 숫자](https://php.net/manual/en/language.types.float.php)합니다. 값의 범위 밖에 있는 경우 특히 bigint 열에도 마찬가지는 [정수](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)합니다.

## <a name="example"></a>예제  
이 코드 샘플에는 입력된 매개 변수로 10 진수 값을 바인딩하는 방법을 보여 줍니다.  

```
<?php
$serverName = "(local)";
$connectionInfo = array("Database"=>"YourTestDB");  
$conn = sqlsrv_connect($serverName, $connectionInfo);  
if ($conn === false) {  
    echo "Could not connect.\n";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Assume TestTable exists with a decimal field 
$input = "9223372036854.80000";
$params = array($input);
$stmt = sqlsrv_prepare($conn, "INSERT INTO TestTable (DecimalCol) VALUES (?)", $params);
sqlsrv_execute($stmt);

sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  

?>
```

## <a name="see-also"></a>참고 항목  
[SQLSRV 드라이버 API 참조](../../connect/php/sqlsrv-driver-api-reference.md)

[방법: 매개 변수가 있는 쿼리 수행](../../connect/php/how-to-perform-parameterized-queries.md)

[설명서의 코드 예제 정보](../../connect/php/about-code-examples-in-the-documentation.md)

[방법: 데이터를 스트림으로 전송](../../connect/php/how-to-send-data-as-a-stream.md)

[방향 매개 변수 사용](../../connect/php/using-directional-parameters.md)

[데이터 검색](../../connect/php/retrieving-data.md)

[데이터 업데이트&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)

