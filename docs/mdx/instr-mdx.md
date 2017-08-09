---
title: Instr (MDX) | Microsoft Docs
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 5638c358-47da-40ad-b988-1a5214c05492
caps.latest.revision: 6
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 59c741dbecfb75b370bf2cc4ce103f00b695345d
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="instr-mdx"></a>Instr (MDX)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  다른 문자열 내에서 한 문자열의 시작 위치를 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```  
InStr([start, ]searched_string, search_string[, compare])  
```  
  
## <a name="arguments"></a>인수  
 *시작*  
 (선택 사항) 각 검색의 시작 위치를 설정하는 숫자 식입니다. 이 값을 생략하면 첫 번째 문자 위치에서 검색이 시작됩니다. start가 null인 경우에는 함수 반환 값이 정의되지 않습니다.  
  
 *searched_string*  
 검색할 문자열 식입니다.  
  
 *search_string*  
 검색할 문자열 식입니다.  
  
 *비교*  
 (선택 사항) 정수 값입니다. 이 인수는 항상 무시되며, 다른 호환을 위해 정의 된 **Instr** 다른 언어의 함수입니다.  
  
## <a name="return-value"></a>반환 값  
 정수 값의 시작 위치와 *String2* 에 *String1*합니다.  
  
 또한 **InStr** 함수는 조건에 따라 다음 표에 나열 된 값을 반환 합니다.  
  
|조건|반환 값|  
|---------------|------------------|  
|String1의 길이가 0인 경우|영(0)|  
|String1이 Null인 경우|정의되지 않음|  
|String2의 길이가 0인 경우|start|  
|String2가 Null인 경우|정의되지 않음|  
|String2를 찾을 수 없는 경우|영(0)|  
|start가 Len(String2)보다 큰 경우|영(0)|  
  
## <a name="remarks"></a>주의  
  
> [!WARNING]  
>  **Instr** 항상 대/소문자 구분 비교를 수행 합니다.  
  
## <a name="example"></a>예제  
 다음 예제에서는의 사용법을 보여 줍니다.는 **Instr** 함수 및 다른 표시 시나리오 발생 합니다.  
  
```  
with   
    member [Date].[Date].[Results] as "Results"  
    member measures.[lowercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[uppercase found in lowercase string] as InStr( "abcdefghijklmnñopqrstuvwxyz", "O")  
    member measures.[searched string is empty]            as InStr( "", "o")  
    member measures.[searched string is null]             as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[search string is empty]              as InStr( "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is empty start 10]     as InStr(10, "abcdefghijklmnñopqrstuvwxyz", "")  
    member measures.[search string is null]               as iif(IsError(InStr( null, "o")), "Is Error", iif(IsNull(InStr( null, "o")), "Is Null","Is undefined"))  
    member measures.[found from start 10]                 as InStr( 10, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NOT found from start 17]             as InStr( 17, "abcdefghijklmnñopqrstuvwxyz", "o")  
    member measures.[NULL start]                          as iif(IsError(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Error", iif(IsNull(InStr( null, "abcdefghijklmnñopqrstuvwxyz", "o")), "Is Null","Is undefined"))  
    member measures.[start greater than searched length]  as InStr( 170, "abcdefghijklmnñopqrstuvwxyz", "o")  
  
select  [Results] on columns,  
       { measures.[lowercase found in lowercase string]  
       , measures.[uppercase found in lowercase string]  
       , measures.[searched string is empty]  
       , measures.[searched string is null]  
       , measures.[search string is empty]  
       , measures.[search string is empty start 10]  
       , measures.[search string is null]  
       , measures.[found from start 10]  
       , measures.[NOT found from start 17]  
       , measures.[NULL start]   
       , measures.[start greater than searched length]  
       } on rows  
  
from [Adventure Works]  
```  
  
 다음 표에서는 얻게 되는 결과를 보여 줍니다.  
  
|||  
|-|-|  
||결과|  
|소문자 문자열에 소문자가 있습니다.|16|  
|소문자 문자열에 대문자가 있습니다.|16|  
|검색된 문자열이 비어 있습니다.|0|  
|검색된 문자열이 null입니다.|정의되지 않음|  
|검색 문자열이 비어 있습니다.|1.|  
|검색 문자열이 비어 있습니다(start 10).|10|  
|검색 문자열이 null입니다.|정의되지 않음|  
|start 10에서 찾았습니다.|16|  
|start 17에서 찾을 수 없습니다.|0|  
|NULL start|정의되지 않음|  
|start가 검색된 길이보다 큽니다.|0|  
  
  
