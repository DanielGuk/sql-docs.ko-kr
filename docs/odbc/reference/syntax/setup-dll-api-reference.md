---
title: "설치 DLL API 참조 | Microsoft Docs"
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
- ODBC drivers [ODBC], driver setup DLL
- driver setup DLL [ODBC]
ms.assetid: f9d03f17-1c0d-4e7c-9c04-8c316e07ef25
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1bd84a225c94c4141cb9c7f6a897731926384ea6
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="setup-dll-api-reference"></a>설치 프로그램 DLL API 참조
이 섹션에서는 드라이버 설치는 두 개의 구성 된 DLL API의 구문을 설명 (**ConfigDriver** 및 **ConfigDSN**). **ConfigDriver** 및 **ConfigDSN** 별도의 DLL을 설치 하거나 드라이버 DLL에에서 있을 수 있습니다.  
  
 이 섹션에서는 변환기 설치는 단일 함수 구성 된 DLL API의 구문을 설명 하는 또한 (**ConfigTranslator**). **ConfigTranslator** 변환기 DLL에에서 있을 수 있습니다 또는 별도의 DLL을 설치 합니다.  
  
 각 함수는 ODBC 도입 된 버전이 표시 되어 있습니다.  
  
 이 섹션에서는 다음 항목을 다룹니다.  
  
-   [ConfigDriver 함수](../../../odbc/reference/syntax/configdriver-function.md)  
  
-   [ConfigDSN 함수](../../../odbc/reference/syntax/configdsn-function.md)  
  
-   [ConfigTranslator 함수](../../../odbc/reference/syntax/configtranslator-function.md)