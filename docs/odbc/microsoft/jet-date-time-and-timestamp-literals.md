---
title: 'Jet: 날짜, 시간 및 타임 스탬프 리터럴 | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2325cd7e4a10e91f351aa2107c64c0978b843fa6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47825841"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 날짜, 시간, 타임스탬프 리터럴
최대 상호 운용성을 위해 응용 프로그램 이스케이프 절 구문을 사용 하 여 ODBC 정식 형식으로 날짜 리터럴을 전달 해야:  
  
-   날짜 리터럴 {d '*값*'을 (를), 여기서 *값을 지정*e는 "yyyy-월-일" 형식  
  
-   시간 리터럴에 대 한 {t '*값*'을 (를), 여기서 *값을 지정*e는 "hh: mm:"  
  
 타임 스탬프 리터럴에 대 한 {ts'*값*'} 여기서 *값을 지정*형태로 e는 "h:mm: ss yyyy-월-일 [. f...]"입니다.
