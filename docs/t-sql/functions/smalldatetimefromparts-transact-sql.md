---
title: SMALLDATETIMEFROMPARTS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SMALLDATETIMEFROMPARTS
- SMALLDATETIMEFROMPARTS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SMALLDATETIMEFROMPARTS function
ms.assetid: 7467fdab-e588-419c-9e29-42caec34a9ea
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7a07c71a03d396843c57c82a1e4944f82d976185
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47681851"
---
# <a name="smalldatetimefromparts-transact-sql"></a>SMALLDATETIMEFROMPARTS(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-all-md](../../includes/tsql-appliesto-ss2012-all-md.md)]

  지정된 날짜 및 시간에 대한 **smalldatetime** 값을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
SMALLDATETIMEFROMPARTS ( year, month, day, hour, minute )  
```  
  
## <a name="arguments"></a>인수  
 *year*  
 연도를 지정하는 정수 식입니다.  
  
 *month*  
 월을 지정하는 정수 식입니다.  
  
 *day*  
 일을 지정하는 정수 식입니다.  
  
 *hour*  
 시간을 지정하는 정수 식입니다.  
  
 *minute*  
 분을 지정하는 정수 식입니다.  
  
## <a name="return-types"></a>반환 형식  
 **smalldatetime**  
  
## <a name="remarks"></a>Remarks  
 이 함수는 완전히 초기화된 **smalldatetime** 값의 생성자와 비슷하게 동작합니다. 인수가 유효하지 않으면 오류가 발생합니다. 필수 인수가 Null일 경우에는 Null이 반환됩니다.  
  
 이 함수는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 이상 서버에 대해서는 원격으로 실행할 수 있지만 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 이전 버전이 설치되어 있는 서버에 대해서는 원격으로 실행할 수 없습니다.  
  
## <a name="examples"></a>예  
  
```  
SELECT SMALLDATETIMEFROMPARTS ( 2010, 12, 31, 23, 59 ) AS Result  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Result  
---------------------------  
2011-01-01 00:00:00  
  
(1 row(s) affected)  
```  
  

