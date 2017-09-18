---
title: "SQLGetFunctions (커서 라이브러리) | Microsoft Docs"
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
- SQLGetFunctions function [ODBC], Cursor Library
ms.assetid: 931acd12-4eb6-4a78-9a77-157a18a9a2d0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6d8ca656e63183df424de2ec45c823ac275ef69f
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetfunctions-cursor-library"></a>SQLGetFunctions (커서 라이브러리)
> [!IMPORTANT]  
>  이 기능은 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는이 기능을 사용 하지 마십시오 하 고 현재이 기능을 사용 하는 응용 프로그램은 수정 하세요. 드라이버의 커서 기능을 사용 하는 것이 좋습니다.  
  
 이 항목의 사용을 설명는 **SQLGetFunctions** 커서 라이브러리의 함수가 있습니다. 에 대 한 일반적인 내용은 **SQLGetFunctions**, 참조 [SQLGetFunctions 함수](../../../odbc/reference/syntax/sqlgetfunctions-function.md)합니다.  
  
 호출 하는 경우 **SQLGetFunctions**, 커서 라이브러리 지원 된다는 점을 반환 **SQLExtendedFetch**, **SQLFetchScroll**, **SQLSetPos**, 및 **SQLSetScrollOptions**, 드라이버에서 지 원하는 함수 외에도 합니다.