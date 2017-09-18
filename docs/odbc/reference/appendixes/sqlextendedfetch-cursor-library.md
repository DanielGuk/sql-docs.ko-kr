---
title: "SQLExtendedFetch (커서 라이브러리) | Microsoft Docs"
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
- SQLExtendedFetch function [ODBC], Cursor Library
ms.assetid: 06fbf06f-127b-475c-b636-7b784918475d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9c39b299dc2f42fdf1eb51010e7b4fac2bb9bcfd
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlextendedfetch-cursor-library"></a>SQLExtendedFetch (커서 라이브러리)
> [!IMPORTANT]  
>  이 기능은 나중 버전의 Windows에서 제거 됩니다. 새 개발 작업에서는이 기능을 사용 하지 마십시오 하 고 현재이 기능을 사용 하는 응용 프로그램은 수정 하세요. 드라이버의 커서 기능을 사용 하는 것이 좋습니다.  
  
 이 항목의 사용을 설명는 **SQLExtendedFetch** 커서 라이브러리의 함수가 있습니다. 에 대 한 일반적인 내용은 **SQLExtendedFetch**, 참조 [SQLExtendedFetch 함수](../../../odbc/reference/syntax/sqlextendedfetch-function.md)합니다.  
  
 커서 라이브러리 구현 **SQLExtendedFetch** 반복적으로 호출 하 여 **SQLFetch** 드라이버에서입니다.  
  
 커서 라이브러리 호출을 지 원하는 **SQLExtendedFetch** 와 *FetchOrientation* 에서는 SQL_FETCH_BOOKMARK의 합니다.  
  
 커서 라이브러리를 사용 하는 경우에 대 한 호출이 **SQLExtendedFetch** 에 대 한 호출 함께 **SQLFetchScroll** 또는 **SQLFetch**합니다.