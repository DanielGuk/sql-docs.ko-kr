---
title: SYSUTCDATETIME(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/01/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SYSUTCDATETIME
- SYSUTCDATETIME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dates [SQL Server], functions
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- date and time [SQL Server], SYSUTCDATETIME
- SYSUTCDATETIME function [SQL Server]
- time [SQL Server], system
ms.assetid: f14fc2cd-9ea8-4daf-88f4-418cf523ab55
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 305fbf35deccf81c127e6b53f2c2b2f946c06aae
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47658071"
---
# <a name="sysutcdatetime-transact-sql"></a>SYSUTCDATETIME(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 실행되고 있는 컴퓨터의 날짜와 시간이 포함된 **datetime2** 값을 반환합니다. 날짜와 시간은 UTC 시간(Coordinated Universal Time)으로 반환됩니다. 소수 자릿수 초의 전체 자릿수는 1-7자리입니다. 기본 전체 자릿수는 7자리입니다.  
  
> [!NOTE]  
>  SYSDATETIME 및 SYSUTCDATE에는 GETDATE 및 GETUTCDATE보다 많은 소수 자릿수 초의 전체 자릿수가 있습니다. SYSDATETIMEOFFSET에는 시스템 표준 시간대 오프셋이 포함되어 있습니다. SYSDATETIME, SYSUTCDATE 및 SYSDATETIMEOFFSET은 모든 날짜 및 시간 유형의 변수에 할당할 수 있습니다.  
  
 모든 [!INCLUDE[tsql](../../includes/tsql-md.md)]의 날짜 및 시간 데이터 형식과 함수에 대한 개요는 [날짜 및 시간 데이터 형식과 함수](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)를 참조하세요.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
SYSUTCDATETIME ( )  
```  
  
## <a name="return-type"></a>반환 형식  
 **datetime2**  
  
## <a name="remarks"></a>Remarks  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문은 **datetime2** 식을 참조할 수 있는 모든 곳에서 SYSUTCDATETIME을 참조할 수 있습니다.  
  
 SYSUTCDATETIME은 비결정적 함수입니다. 열에서 이 함수를 참조하는 뷰와 식은 인덱싱될 수 없습니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 GetSystemTimeAsFileTime() Windows API를 사용하여 날짜 및 시간 값을 가져옵니다. 정확도는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스가 실행되고 있는 컴퓨터의 하드웨어와 Windows 버전에 따라 달라집니다. 이 API의 정밀도는 100나노초로 고정됩니다. 정확도는 GetSystemTimeAdjustment() Windows API를 사용하여 확인할 수 있습니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 현재 날짜 및 시간을 반환하는 6개의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 시스템 함수를 사용하여 시간, 날짜 또는 두 가지 모두 반환합니다. 값은 순차적으로 반환되므로 소수 자릿수 초가 서로 다를 수 있습니다.  
  
### <a name="a-showing-the-formats-that-are-returned-by-the-date-and-time-functions"></a>1. 날짜 및 시간 함수가 반환하는 형식 표시  
 다음 예에서는 날짜 및 시간 함수가 반환하는 다양한 형식을 보여 줍니다.  
  
```  
SELECT SYSDATETIME() AS SYSDATETIME  
    ,SYSDATETIMEOFFSET() AS SYSDATETIMEOFFSET  
    ,SYSUTCDATETIME() AS SYSUTCDATETIME  
    ,CURRENT_TIMESTAMP AS CURRENT_TIMESTAMP  
    ,GETDATE() AS GETDATE  
    ,GETUTCDATE() AS GETUTCDATE;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
SYSDATETIME()      2007-04-30 13:10:02.0474381
SYSDATETIMEOFFSET()2007-04-30 13:10:02.0474381 -07:00
SYSUTCDATETIME()   2007-04-30 20:10:02.0474381
CURRENT_TIMESTAMP  2007-04-30 13:10:02.047
GETDATE()          2007-04-30 13:10:02.047
GETUTCDATE()       2007-04-30 20:10:02.047
```  
  
### <a name="b-converting-date-and-time-to-date"></a>2. 날짜 및 시간을 날짜로 변환  
 다음 예에서는 날짜 및 시간 값을 `date`으로 변환하는 방법을 보여 줍니다.  
  
```  
SELECT CONVERT (date, SYSDATETIME())  
    ,CONVERT (date, SYSDATETIMEOFFSET())  
    ,CONVERT (date, SYSUTCDATETIME())  
    ,CONVERT (date, CURRENT_TIMESTAMP)  
    ,CONVERT (date, GETDATE())  
    ,CONVERT (date, GETUTCDATE());  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
2007-04-30
```  
  
### <a name="c-converting-date-and-time-values-to-time"></a>3. 날짜 및 시간을 시간으로 변환  
 다음 예에서는 날짜 및 시간 값을 `time`으로 변환하는 방법을 보여 줍니다.  
  
 ```
DECLARE @DATETIME DATETIME = GetDate();
DECLARE @TIME TIME
SELECT @TIME = CONVERT(time, @DATETIME)
SELECT @TIME AS 'Time', @DATETIME AS 'Date Time'
```
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Time             Date Time  
13:49:33.6330000 2009-04-22 13:49:33.633
```  
  
## <a name="see-also"></a>참고 항목  
 [CAST 및 CONVERT&#40;Transact-SQL&#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [날짜 및 시간 데이터 형식 및 함수&#40;Transact-SQL&#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)   
 [AT TIME ZONE &#40;Transact-SQL&#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


