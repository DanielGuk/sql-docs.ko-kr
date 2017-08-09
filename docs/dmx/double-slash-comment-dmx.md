---
title: "/ / (주석) (DMX) 이중 슬래시 | Microsoft Docs"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- DMX
helpviewer_keywords:
- double forward slashes
- commenting characters
- // (comment)
ms.assetid: c2ab9ca1-9fc9-4162-97f9-a9433d189220
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d778536fe2fcc01374d4e10d2d9935766ad975e8
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="double-slash-comment-dmx"></a>이중 슬래시 (/ / 주석) (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]에서 실행되지 않는 텍스트 문자열을 나타냅니다. 주석을 DMX(Data Mining Extensions) 문 안에 중첩하거나 코드 줄 끝에 포함하거나 별도의 줄에 삽입할 수 있습니다.  
  
## <a name="syntax"></a>구문  
  
```  
  
// Comment_Text   
```  
  
#### <a name="parameters"></a>매개 변수  
 *Comment_Text*  
 주석 텍스트를 포함하는 문자열입니다.  
  
## <a name="remarks"></a>주의  
 한 줄로 된 주석에만 //를 사용합니다. //를 사용하여 삽입한 주석은 줄 바꿈 문자로 구분됩니다.  
  
 주석의 길이에는 제한이 없습니다.  
  
 DMX에서 다른 종류의 주석 사용 하는 방법에 대 한 자세한 내용은 참조 [의견 &#40; DMX &#41;](../dmx/comments-dmx.md)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [슬래시 별 &#40; 설명 &#41; &#40; DMX &#41;](../dmx/slash-star-comment-dmx.md)   
 [-&#40; 설명 &#41; &#40; DMX &#41; 요약](../dmx/comment-dmx-summary.md)   
 [Data Mining Extensions &#40; DMX &#41; 연산자 참조](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [연산자 &#40; DMX &#41;](../dmx/operators-dmx.md)  
  
  
