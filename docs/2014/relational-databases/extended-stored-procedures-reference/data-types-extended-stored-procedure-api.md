---
title: 데이터 형식(확장 저장 프로시저 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a21e4154d0595a2bcf61cafbbeccb2d7b7599bde
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48115153"
---
# <a name="data-types-extended-stored-procedure-api"></a>데이터 형식(확장 저장 프로시저 API)
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 대신 CLR 통합을 사용하세요.  
  
 확장 저장 프로시저 API 데이터 형식을 사용하려면 프로그램에 Srv.h 헤더 파일을 포함합니다.  
  
|데이터 형식|SQL Server 데이터 형식|Description|  
|---------------|--------------------------|-----------------|  
|SRVBIGBINARY|`binary`|길이가 0-8000바이트인 `binary` 데이터 형식입니다.|  
|SRVBIGCHAR|`char`|길이가 0-8000바이트인 `character` 데이터 형식입니다.|  
|SRVBIGVARBINARY|`varbinary`|길이가 0-8000바이트인 가변 길이 `binary` 데이터 형식입니다.|  
|SRVBIGVARCHAR|`varchar`|길이가 0-8000바이트인 가변 길이 `character` 데이터 형식입니다.|  
|SRVBINARY|`binary`|`binary` 데이터 형식입니다.|  
|SRVBIT|`Bit`|`bit` 데이터 형식입니다.|  
|SRVBITN|`bit null`|`bit` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVCHAR|`char`|`character` 데이터 형식입니다.|  
|SRVDATETIME|`datetime`|8바이트 `datetime` 데이터 형식입니다.|  
|SRVDATETIM4|`smalldatetime`|4 바이트 `smalldatetime` 데이터 형식입니다.|  
|SRVDATETIMN|**datetime null**|`smalldatetime` 또는 `datetime` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVDECIMAL|`decimal`|`decimal` 데이터 형식입니다.|  
|SRVDECIMALN|`decimal null`|`decimal` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVFLT4|`real`|4 바이트 `real` 데이터 형식입니다.|  
|SRVFLT8|`float`|8바이트 `float` 데이터 형식입니다.|  
|SRVFLTN|`real` &#124; `float null`|`real` 또는 `float` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVIMAGE|`image`|`image` 데이터 형식입니다.|  
|SRVINT1|`tinyint`|1 바이트 `tinyint` 데이터 형식입니다.|  
|SRVINT2|`smallint`|2 바이트 `smallint` 데이터 형식입니다.|  
|SRVINT4|`int`|4 바이트 `int` 데이터 형식입니다.|  
|SRVINTN|`tinyint` &#124; `smallint` &#124; `int null`|`tinyint`, `smallint` 또는 `int` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVMONEY4|`smallmoney`|4 바이트 `smallmoney` 데이터 형식입니다.|  
|SRVMONEY|`money`|8바이트 `money` 데이터 형식입니다.|  
|SRVMONEYN|`money` &#124; `smallmoney null`|`smallmoney` 또는 `money` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVNCHAR|**nchar**|유니코드 `character` 데이터 형식입니다.|  
|SRVNTEXT|`ntext`|유니코드 `text` 데이터 형식입니다.|  
|SRVNUMERIC|`numeric`|`numeric` 데이터 형식입니다.|  
|SRVNUMERICN|`numeric null`|`numeric` 데이터 형식으로 null 값이 허용됩니다.|  
|SRVNVARCHAR|**nvarchar**|유니코드 가변 길이 `character` 데이터 형식입니다.|  
|SRVTEXT|`text`|`text` 데이터 형식입니다.|  
|SRVVARBINARY|`varbinary`|가변 길이 `binary` 데이터 형식입니다.|  
|SRVVARCHAR|`varchar`|가변 길이 `character` 데이터 형식입니다.|  
  
> [!IMPORTANT]  
>  확장 저장 프로시저의 원본 코드를 철저히 검토하고 프로덕션 서버에 DLL을 설치하기 전에 컴파일한 DLL을 테스트해야 합니다. 보안 검토 및 테스트에 대한 자세한 내용은 [Microsoft 웹 사이트](http://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409http://msdn.microsoft.com/security/)를 참조하십시오.  
  
  
