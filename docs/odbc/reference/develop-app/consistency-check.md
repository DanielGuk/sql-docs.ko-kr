---
title: "일관성 확인 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descriptors [ODBC], consistency checks
- consistency checks [ODBC]
ms.assetid: deb80efa-ad1f-4ea5-b334-9817cd279e5c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 81ecac0249bc5e981c95b319f64768d45b792b96
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="consistency-check"></a>일관성 확인
일관성 확인을 응용 프로그램에서 IPD, 카드가, APD의 SQL_DESC_DATA_PTR 필드가 설정 될 때마다 드라이버에 의해 수행 됩니다. 이 필드를 설정할 때마다 드라이버 SQL_DESC_TYPE 필드의 값과 같은 레코드의 SQL_DESC_TYPE 필드에 적용할 수 있는 값은 유효 하 고 일관성을 확인 합니다.  
  
 일반적으로 IPD의 SQL_DESC_DATA_PTR 필드가 설정 되지 않았습니다. 그러나 응용 프로그램 이렇게 하려면 IPD 필드의 일관성 확인을 적용 합니다. 값으로는 IPD의 SQL_DESC_DATA_PTR 필드가 설정 된 실제로 저장 되지 않으며, 호출 하 여 검색할 수 없습니다 **SQLGetDescField** 또는 **SQLGetDescRec**; 설정을 적용 하기 위해만 이루어집니다는 일관성 확인입니다. IRD에서 일관성 확인을 수행할 수 없습니다.  
  
 일관성 확인에 대 한 자세한 내용은 참조 하십시오. [SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)합니다.