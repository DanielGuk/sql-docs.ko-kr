---
title: 영향을 받는 개체 (OracleToSQL) 선택 및 구성 | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Columns Comparison Settings
- Selection of Affected Objects
ms.assetid: 545eeda2-9829-4187-a858-619a96b4b71d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 4034beae4e022379de1cb9cac83f982f512bdc7a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47688301"
---
# <a name="selecting-and-configuring-affected-objects-oracletosql"></a>영향을 받는 개체 선택 및 구성(OracleToSQL)
이 페이지에서 테이블을 선택할 수 있습니다 하 고 SSMA 이전 단계에서 선택한 개체에 대 한 실행 결과 확인 하는 경우 외래 키에는 변경 내용 비교 해야 합니다. 또한 확인 매개 변수를 사용자 지정할 수 있습니다.  
  
## <a name="selection-of-affected-objects"></a>영향을 받는 개체 선택  
창의 왼쪽에 있는 Oracle 개체 트리에서 테이블과 외래 키를 확인는 변경 될 동일한 비교 해야 합니다.  
  
레이블이 지정 된 링크가 표시는 SSMA 테스터를 확인 하지 못하면 이러한 개체 중 하나가 **선택한 일부 개체에 오류가 포함 되어** 개체 트리 아래에 있는 합니다. 이러한 개체를 비교할 수 없습니다는 이유는 이유를 표시 하 고 잘못 된 개체의 선택을 취소 하려면이 링크를 클릭 합니다.  
  
## <a name="table"></a>Table  
테이블 탭을 선택한 테이블의 그리드 보기를 포함 합니다. 눈금에는 선택한 테이블에 대 한 다음 정보가 들어 있습니다.  
  
-   열 이름  
  
-   데이터 형식  
  
-   전체 자릿수  
  
-   소수 자릿수  
  
-   규칙  
  
-   Default  
  
-   ID  
  
-   Null 허용  
  
## <a name="sql"></a>Sql  
SQL 탭에 "Create table" 선택한 테이블의 SQL입니다.  
  
## <a name="data"></a>data  
데이터 탭에는 선택한 테이블에 데이터가 표시 됩니다.  
  
## <a name="properties"></a>속성  
속성 탭에는 선택한 테이블의 속성이 표시 됩니다. 다음 필드는 속성 탭 아래에 표시 합니다.  
  
-   만들거나 마지막으로 수정한 날짜  
  
-   개체 이름  
  
## <a name="columns-comparison-settings"></a>열 비교 설정  
테이블 열에 대 한 비교 규칙을 설정 **열 비교** 페이지입니다. 다음 설정을 할 수 있습니다.  
  
### <a name="use-during-test-comparisons"></a>테스트 비교 중에 사용  
이 열은 테스트 결과 확인에 참여 하는 경우를 결정 합니다.  
  
-   선택 하면 **True**, SSMA는 Oracle에서 SQL Server에 있는 열의 내용을 사용 하 여 테스트를 실행 한 후이 열의 내용을 비교 합니다. 
  
-   선택 하면**False**, 열 결과 확인에서 제외 됩니다.  
  
### <a name="use-custom-scale"></a>사용자 지정 크기 조정 사용  
숫자 데이터 형식의 열에 대 한 비교에 대 한 사용자 지정 확장을 설정할 수 있습니다.  
  
-   선택 하면 **True**, 숫자 값에 따라 반올림 됩니다 합니다 **비교 확장** 비교 하기 전에 값입니다.  
  
-   선택 하면**False**, 숫자 비교를 정확 하 게 됩니다.  
  
### <a name="comparing-scale"></a>배율 비교  
  
-   경우에만 사용할 수는 **사용 하 여 사용자 지정 크기 조정** 옵션을 설정 **True**합니다. 숫자 비교에 대 한 전체 자릿수입니다.  
  
### <a name="date-time-comparing"></a>날짜 시간 비교  
정의 방법: 날짜/시간 값을 비교 합니다.  
  
-   선택 하는 경우 **전체 날짜 비교**, 두 플랫폼 모두에서 값의 전체 비교 수행 됩니다.  
  
-   선택 하는 경우 **날짜만 비교**, 시간 부분 무시 됩니다.  
  
-   선택 하는 경우 **시간만 비교**, 날짜 파트는 무시 됩니다.  
  
-   선택 하는 경우 **무시 밀리초**, 초까지 결과 비교 합니다.  
  
-   선택 하는 경우 **무시 날짜 및 시간 (밀리초)**, 결과 초의 소수 부분 시간 부분으로만 비교 및 무시 됩니다.  
  
### <a name="ignore-strings-case"></a>문자열의 대/소문자 무시  
비교의 대/소문자 구분을 제어합니다.  
  
-   선택 하면 **True**, 비교는 대/소문자 구분 됩니다.  
  
-   선택 하면 **False**, 비교는 대/소문자를 고려 합니다.  
  
## <a name="comparing-sql"></a>SQL 비교  
SSMA 테스터에서 생성 한 SELECT 문을 볼 수 있습니다 합니다 **비교 SQL** 페이지입니다. 테스터-행 단위에서 이러한 문의 결과 집합을 비교 합니다. Oracle 결과 집합의 다음 각 행은 SQL Server에서 생성 된 결과 집합의 다음 행으로 같아야 합니다.
  
사용자 지정 확인을 제공 하려면 이러한 SELECT 문을 편집할 수 있습니다. 문을 SQL Server 및 Oracle에서 변경 내용을 저장을 사용 합니다 **적용** 원본 및 대상 SQL에서 해당 단추입니다.  
  
## <a name="next-step"></a>다음 단계  
[호출 순서 사용자 지정 &#40;OracleToSQL&#41;](../../ssma/oracle/customizing-calls-order-oracletosql.md)  
  
## <a name="see-also"></a>관련 항목  
[테스트 사례 준비 완료 &#40;OracleToSQL&#41;](../../ssma/oracle/finishing-test-case-preparation-oracletosql.md)  
[테스트 사례 실행 &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[마이그레이션된 데이터베이스 개체 테스트 &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
