---
title: FILEPROPERTY (Transact SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- FILEPROPERTY_TSQL
- FILEPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- viewing file properties
- names [SQL Server], files
- displaying file properties
- file properties [SQL Server]
- FILEPROPERTY function
- file names [SQL Server], FILEPROPERTY
ms.assetid: b82244ed-d623-431f-aa06-8017349d847f
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 7078fecb77bad44fd6aa4c3ce0baf9565f1d6d3f
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="fileproperty-transact-sql"></a>FILEPROPERTY(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  현재 데이터베이스의 파일 이름과 속성 이름이 지정되면 지정된 파일 이름 속성 값을 반환합니다. 현재 데이터베이스에 없는 파일에 대해서는 NULL을 반환합니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```  
  
FILEPROPERTY ( file_name , property )  
```  
  
## <a name="arguments"></a>인수  
 *i l e _*  
 속성 정보를 반환할 현재 데이터베이스에 관련된 파일 이름이 포함된 식입니다. *file_name* 은 **nchar(128)**합니다.  
  
 *속성*  
 반환할 파일 속성의 이름이 포함된 식입니다. *속성* 은 **varchar (128)**, 다음 값 중 하나가 될 수 있습니다.  
  
|값|Description|반환 값|  
|-----------|-----------------|--------------------|  
|**IsReadOnly**|파일 그룹이 읽기 전용입니다.|1 = True<br /><br /> 0 = False<br /><br /> NULL = 입력이 잘못되었습니다.|  
|**IsPrimaryFile**|파일이 주 파일입니다.|1 = True<br /><br /> 0 = False<br /><br /> NULL = 입력이 잘못되었습니다.|  
|**IsLogFile**|파일이 로그 파일입니다.|1 = True<br /><br /> 0 = False<br /><br /> NULL = 입력이 잘못되었습니다.|  
|**SpaceUsed**|지정된 파일이 사용하는 공간의 크기입니다.|파일에 할당된 페이지 수|  
  
## <a name="return-types"></a>반환 형식  
 **int**  
  
## <a name="remarks"></a>주의  
 *file_name* 에 해당 하는 **이름** 열에는 **sys.master_files** 또는 **sys.database_files** 카탈로그 뷰.  
  
## <a name="examples"></a>예  
 다음 예에서는 `IsPrimaryFile` 데이터베이스에 있는 `AdventureWorks_Data` 파일 이름에 대한 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 속성의 설정을 반환합니다.  
  
```  
  
SELECT FILEPROPERTY('AdventureWorks2012_Data', 'IsPrimaryFile')AS [Primary File];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Primary File   
-------------  
1  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>관련 항목:  
 [FILEGROUPPROPERTY &#40; Transact SQL &#41;](../../t-sql/functions/filegroupproperty-transact-sql.md)   
 [메타 데이터 함수 &#40; Transact SQL &#41;](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sp_spaceused&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.database_files&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files&#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  