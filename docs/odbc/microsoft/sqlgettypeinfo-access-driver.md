---
title: "SQLGetTypeInfo (Access 드라이버) | Microsoft Docs"
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
- Access driver [ODBC], SQLGetTypeInfo
- SQLGetTypeInfo function [ODBC], Access Driver
ms.assetid: a28b16eb-ca36-4297-9297-ecd7c107a84e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7f652b5e95fc9c2bf85643aa3633a6e30e6087bb
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgettypeinfo-access-driver"></a>SQLGetTypeInfo (Access 드라이버)
> [!NOTE]  
>  이 항목에서는 액세스 드라이버 관련 정보를 제공 합니다. 이 함수에 대 한 일반 정보에서 해당 항목을 참조 하십시오. [ODBC API 참조](../../odbc/reference/syntax/odbc-api-reference.md)합니다.  
  
 생성 된 테이블에 반환 된 (TYPE_NAME) 형식의 이름을 **SQLGetTypeInfo** 이름이 데이터 원본에서 가장 일반적으로 사용 됩니다.  
  
 SQL_ALL_EXCEPT_LIKE이 반환할 검색 가능한 열의 바이트에 대 한 카운터, Double, 단일, Long 및 Short 데이터 형식입니다. (값 다음 비교를 수행 하는 ODBC 정식 변환 함수를 사용 하 여 문자를 변환 하는 LIKE 기능을 구현할 수 있습니다.)