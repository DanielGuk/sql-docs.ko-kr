---
title: 서식 파일을 캐싱을 (SQLXML 4.0) | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c1081417757b8d4087155a232ac53d046e8f6a39
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48199066"
---
# <a name="template-caching-sqlxml-40"></a>템플릿 캐싱(SQLXML 4.0)
  템플릿 캐싱은 성능을 크게 개선합니다. 템플릿 캐싱이 설정되어 있으면 템플릿이 처음 실행될 때 메모리에 남아 있습니다. 따라서 후속 템플릿 실행 성능이 개선됩니다.  
  
 템플릿 캐시 크기를 설정하려면 레지스트리에 다음 키를 추가합니다.  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 템플릿 크기는 사용 가능한 메모리와 사용 중인 템플릿 개수에 따라 설정해야 합니다. 기본값인 **TemplateCacheSize** 크기는 31. 템플릿 액세스 속도가 느리다고 생각되면 캐시 크기를 늘리고, 메모리가 부족하면 캐시 크기를 줄일 수 있습니다.  
  
 성능 향상을 위해 좋습니다 설정 하는 **TemplateCacheSize** 보다 일반적으로 사용 되는 템플릿의 수입니다. 경우 **TemlateCacheSize** 작은 서식 있는 수보다 템플릿 증가의 수로 성능이 저하 됩니다. **TemplateCacheSize** 최대 128로 설정할 수 있습니다.  
  
 캐시된 템플릿이 사용될 때마다 템플릿을 새로 고쳐야 하는지 확인하기 위해 템플릿 파일의 수정 시간이 검사됩니다. 왜냐하면 캐시 복사본보다 디스크 복사본이 최신이기 때문입니다.  
  
> [!NOTE]  
>  템플릿 매개 변수와 명령 속성은 캐시되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [스키마 캐시 &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md)   
 [XSL 캐시 &#40;SQLXML 4.0&#41;](xsl-caching-sqlxml-4-0.md)  
  
  
