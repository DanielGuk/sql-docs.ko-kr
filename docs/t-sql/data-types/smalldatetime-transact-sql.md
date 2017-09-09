---
title: smalldatetime (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 07/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- smalldatetime_TSQL
- smalldatetime
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], data types
- smalldatetime data type [SQL Server]
- dates [SQL Server], data types
- date and time [SQL Server], smalldatetime
- data types [SQL Server], date and time
ms.assetid: 68b74610-d54c-4c8e-b4b2-7e3747546ee0
caps.latest.revision: 50
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 07012d85a54292fa763a7b291d1b7318b6969ca4
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="smalldatetime-transact-sql"></a>smalldatetime(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

날짜와 시간을 정의합니다. 시간은 하루 24시간을 기준으로 하며 초는 항상 소수 자릿수 없이 0(:00)으로 표시됩니다.
  
> [!NOTE]  
>  사용 하 여는 **시간**, **날짜**, **datetime2** 및 **datetimeoffset** 새 작업에 대 한 데이터 형식입니다. 이러한 데이터 형식은 SQL 표준에 맞는 형식으로, 이식성이 높습니다. **시간**, **datetime2** 및 **datetimeoffset** 높아지며 초의 정밀도 됩니다. **datetimeoffset** 전체적으로 배포 된 응용 프로그램에 대 한 표준 시간대 지원을 제공 합니다.  
  
## <a name="smalldatetime-description"></a>smalldatetime 설명
  
|||  
|-|-|  
|구문|**smalldatetime**|  
|사용법|선언 @MySmalldatetime **smalldatetime**<br /><br /> 만들 테이블 Table1 (Column1 **smalldatetime** )|  
|기본 문자열 리터럴 형식<br /><br /> (하위 클라이언트에 대해 사용됨)|해당 사항 없음|  
|날짜 범위|1900-01-01부터 2079-06-06까지<br /><br /> 1900년 1월 1일부터 2079년 6월 6일까지|  
|시간 범위|00:00:00부터 23:59:59까지<br /><br /> 2007-05-09 23:59:59 다음 시간은 다음과 같음<br /><br /> 2007-05-10 00:00:00|  
|요소 범위|YYYY는 1900에서 2079사이에 속하는 4자리 숫자로, 연도를 나타냅니다.<br /><br /> MM은 01에서 12 사이에 속하는 두 자리 숫자로, 지정한 연도의 월을 나타냅니다.<br /><br /> DD는 월에 따라 01에서 31 사이에 속하는 두 자리 숫자로, 지정한 월의 일을 나타냅니다.<br /><br /> hh는 00에서 23 사이에 속하는 두 자리 숫자로, 시를 나타냅니다.<br /><br /> mm은 00에서 59 사이에 속하는 두 자리 숫자로, 분을 나타냅니다.<br /><br /> ss는 00에서 59 사이에 속하는 두 자리 숫자로, 초를 나타냅니다. 29.998초 이하의 값은 가장 가까운 분으로 반내림됩니다. 29.999초 이상의 값은 가장 가까운 분으로 반올림됩니다.|  
|문자 길이|최대 19자리|  
|저장소 크기|4바이트(고정)|  
|정확도|1분|  
|기본값|1900-01-01 00:00:00|  
|달력|일반 달력<br /><br /> (전체 연도 범위를 포함하지는 않음)|  
|사용자 정의 초 소수 부분 자릿수|아니요|  
|표준 시간대 오프셋 인식 및 유지|아니요|  
|일광 절약 시간제 인식|아니요|  
  
## <a name="ansi-and-iso-8601-compliance"></a>ANSI 및 ISO 8601 호환성  
**smalldatetime** 는 ANSI 또는 ISO 8601 규격이 아닙니다.
  
## <a name="converting-date-and-time-data"></a>날짜 및 시간 데이터를 변환합니다.
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 날짜 및 시간 데이터 형식을 변환할 때 날짜나 시간으로 인식되지 않는 값은 모두 무시됩니다. 날짜 및 시간 데이터와 함께 CAST 및 CONVERT 함수를 사용 하는 방법에 대 한 정보를 참조 하십시오. [CAST 및 convert&#40; Transact SQL &#41; ](../../t-sql/functions/cast-and-convert-transact-sql.md).
  
### <a name="converting-smalldatetime-to-other-date-and-time-types"></a>Smalldatetime을 다른 날짜 및 시간 형식으로 변환
이 섹션에서는 발생 하는 상황을 설명 때는 **smalldatetime** 데이터 형식을 다른 날짜 및 시간 데이터 형식으로 변환 됩니다.
  
변환의 경우 **날짜**, 연도, 월 및 일이 복사 됩니다. 다음 코드에서는 `smalldatetime` 값을 `date` 값으로 변환한 결과를 보여 줍니다.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @date date = @smalldatetime  
  
SELECT @smalldatetime AS '@smalldatetime', @date AS 'date';  
  
--Result  
--@smalldatetime          date  
------------------------- ----------  
--1955-12-13 12:43:00     1955-12-13  
--  
--(1 row(s) affected)  
```  
  
변환 됩니다 때 **time (n)**, 시, 분 및 초 복사 됩니다. 소수 자릿수 초는 0으로 설정됩니다. 다음 코드에서는 `smalldatetime` 값을 `time(4)` 값으로 변환한 결과를 보여 줍니다.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @time time(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @time AS 'time';  
  
--Result  
--@smalldatetime          time  
------------------------- -------------  
--1955-12-13 12:43:00     12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
변환 됩니다 때 **datetime**, **smalldatetime** 값에 복사 됩니다는 **datetime** 값입니다. 소수 자릿수 초는 0으로 설정됩니다. 다음 코드에서는 `smalldatetime` 값을 `datetime` 값으로 변환한 결과를 보여 줍니다.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime datetime = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime AS 'datetime';  
  
--Result  
--@smalldatetime          datetime  
------------------------- -----------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.000  
--  
--(1 row(s) affected)  
```  
  
변환의 경우 **datetimeoffset (n)**, **smalldatetime** 값에 복사 되는 **datetimeoffset (n)** 값입니다. 소수 자릿수 초는 0으로 설정되고 표준 시간대 오프셋은 +00:0으로 설정됩니다. 다음 코드에서는 `smalldatetime` 값을 `datetimeoffset(4)` 값으로 변환한 결과를 보여 줍니다.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetimeoffset datetimeoffset(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetimeoffset AS 'datetimeoffset(4)';  
  
--Result  
--@smalldatetime          datetimeoffset(4)  
------------------------- ------------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000 +00:0  
--  
--(1 row(s) affected)  
```  
  
변환에 **datetime2(n)**, **smalldatetime** 값에 복사 되는 **datetime2(n)** 값입니다. 소수 자릿수 초는 0으로 설정됩니다. 다음 코드에서는 `smalldatetime` 값을 `datetime2(4)` 값으로 변환한 결과를 보여 줍니다.
  
```sql
DECLARE @smalldatetime smalldatetime = '1955-12-13 12:43:10';  
DECLARE @datetime2 datetime2(4) = @smalldatetime;  
  
SELECT @smalldatetime AS '@smalldatetime', @datetime2 AS ' datetime2(4)';  
  
--Result  
--@smalldatetime           datetime2(4)  
------------------------- ------------------------  
--1955-12-13 12:43:00     1955-12-13 12:43:00.0000  
--  
--(1 row(s) affected)  
```  
  
## <a name="examples"></a>예  
  
### <a name="a-casting-string-literals-with-seconds-to-smalldatetime"></a>1. 초를 포함한 문자열 리터럴을 smalldatetime으로 캐스팅  
다음 예에서는 문자열 리터럴의 초를 `smalldatetime`으로 변환한 결과를 비교합니다.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29'     AS smalldatetime)  
    ,CAST('2007-05-08 12:35:30'     AS smalldatetime)  
    ,CAST('2007-05-08 12:59:59.998' AS smalldatetime);  
```  
  
|Input|출력|  
|---|---|
|2007-05-08 12:35:29|2007-05-08 12:35:00|  
|2007-05-08 12:35:30|2007-05-08 12:36:00|  
|2007-05-08 12:59:59.998|2007-05-08 13:00:00|  
  
### <a name="b-comparing-date-and-time-data-types"></a>2. 날짜 및 시간 데이터 형식 비교  
다음 예에서는 문자열을 각 날짜 및 시간 데이터 형식으로 캐스팅하는 결과를 비교합니다.
  
```sql
SELECT   
     CAST('2007-05-08 12:35:29. 1234567 +12:15' AS time(7)) AS 'time'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS date) AS 'date'   
    ,CAST('2007-05-08 12:35:29.123' AS smalldatetime) AS   
        'smalldatetime'   
    ,CAST('2007-05-08 12:35:29.123' AS datetime) AS 'datetime'   
    ,CAST('2007-05-08 12:35:29. 1234567 +12:15' AS datetime2(7)) AS   
        'datetime2'  
    ,CAST('2007-05-08 12:35:29.1234567 +12:15' AS datetimeoffset(7)) AS   
        'datetimeoffset';  
```  
  
|데이터 형식|출력|  
|---|---|
|**time**|12:35:29. 1234567|  
|**date**|2007-05-08|  
|**smalldatetime**|2007-05-08 12:35:00|  
|**datetime**|2007-05-08 12:35:29.123|  
|**datetime2**|2007-05-08 12:35:29. 1234567|  
|**datetimeoffset**|2007-05-08 12:35:29.1234567 +12:15|  
  
## <a name="see-also"></a>참고 항목
[CAST 및 CONVERT&#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)
  
  
