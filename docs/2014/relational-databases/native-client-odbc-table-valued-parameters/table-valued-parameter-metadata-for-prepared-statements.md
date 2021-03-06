---
title: 준비 된 문의 테이블 반환 매개 변수 메타 데이터 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), metadata for prepared statements
ms.assetid: fd2fc705-2e98-4011-9822-c7e6cca4a535
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43ef41affecd131626da17ec7d608249437abed6
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48210613"
---
# <a name="table-valued-parameter-metadata-for-prepared-statements"></a>준비된 문의 테이블 반환 매개 변수 메타데이터
  응용 프로그램 SQLNumParams 및 SQLDescribeParam를 통해 준비 된 프로시저 호출에 대 한 메타 데이터를 가져올 수 있습니다. 테이블 반환 매개 변수의 *DataTypePtr* 이 SQL_SS_TABLE로 설정 합니다. 추가 메타 데이터는 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME에 대 한 SQLGetDescField 통해 사용할 수 있습니다.  
  
 SQL_CA_SS_TYPE_NAME, SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME 사용할 수 있습니다 SQLColumns를 사용 하 여 테이블 반환 매개 변수를 사용 하 여 연결 하는 테이블 형식의 열 메타 데이터를 가져옵니다. 이 경우 SQLColumns를 호출 하기 전에 SQL_SOPT_SS_NAME_SCOPE는 sql_ss_name_scope_table_type으로 설정 되어야 합니다. 그리고 응용 프로그램이 테이블 반환 매개 변수 열 메타데이터 검색을 마치면 SQL_SOPT_SS_NAME_SCOPE를 기본값인 SQL_SS_NAME_SCOPE_TABLE로 다시 설정해야 합니다.  
  
 SQL_CA_SS_TYPE_NAME , SQL_CA_SS_CATALOG_NAME 및 SQL_CA_SS_SCHEMA_NAME을 CLR 사용자 정의 형식 매개 변수에 사용할 수도 있습니다.  
  
 저장 프로시저 호출이 아닌 준비된 문의 테이블 반환 매개 변수 메타데이터는 가져올 수 없습니다. 이렇게 하려고 하면 응용 프로그램에서 SQLSTATE 42000이고 메시지가 "구문 오류 또는 액세스 위반입니다."인 SQL_ERROR가 반환됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [테이블 반환 매개 변수 &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  
