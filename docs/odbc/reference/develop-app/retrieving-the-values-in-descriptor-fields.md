---
title: "설명자 필드의 값을 검색할 | Microsoft Docs"
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
- descriptors [ODBC], retrieving or setting field values
ms.assetid: c05b180f-c2b0-437b-8d1c-ce7f4da93287
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: f86dd2e2cb625da359c677fedd297b510fee8593
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="retrieving-the-values-in-descriptor-fields"></a>설명자 필드에 값 검색
응용 프로그램에서 호출할 수 **SQLGetDescField** 설명자 레코드의 단일 필드를 가져올 수 있습니다. **SQLGetDescField** ODBC에 정의 된 모든 설명자 필드에 시작 및 끝 드라이버에서 정의 된 필드에도 응용 프로그램 액세스를 제공 합니다.  
  
 **SQLGetDescRec** 열 또는 매개 변수 데이터의 저장소 및 데이터 형식에 영향을 주는 여러 설명자 필드의 설정을 검색 하기 위해 호출할 수 있습니다.