---
title: "SQL Server 컴퓨터 학습 서비스에 대 한 API 참조 | Microsoft Docs"
ms.custom: 
ms.date: 07/31/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1c776c43d66d01a2f721b5d3d8bc540741bf8b13
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---

# <a name="api-reference-for-sql-server-machine-learning-services"></a>SQL Server 컴퓨터 학습 서비스에 대 한 API 참조

이 문서에서는 기계 학습 SQL Server에서 사용 되는 Api에 대 한 참조 설명서에 대 한 링크를 제공 합니다. 

**적용 대상:** SQL Server 2016 R Services, SQL Server 2017 기계 학습 서비스

대부분의 경우 SQL Server는 Microsoft R Server 및 Microsoft 학습 서버 컴퓨터에 제공 되는 동일한 R 및 Python 라이브러리를 사용 합니다. 

> [!NOTE]
> 모든 Api에 대 한 설명서는 소스 코드에서 파생 되며 편집한 후 않습니다.

## <a name="r"></a>R

+ [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)

    원격 계산 컨텍스트 및 여러 데이터 원본을 지 원하는 확장 가능한 알고리즘입니다.

+ [MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)

    RevoScaleR을 필요로 하는 오른쪽에 대 한 알고리즘 및 변환 학습 신속 하 고 확장 가능한 시스템입니다.

+ [olapR](https://docs.microsoft.com/r-server/r-reference/olapr/olapr)

   OLAP 데이터 원본의 스키마를 읽고 MDX 쿼리를 실행 합니다.

+ [sqlrutils](https://docs.microsoft.com/r-server/r-reference/sqlrutils/sqlrutils)

    R 코드에서 올바른 형식의 저장된 프로시저를 생성 하기 위한 도우미 함수입니다.

+ [mrsdeploy](https://docs.microsoft.com/r-server/r-reference/mrsdeploy/mrsdeploy-package)

   게시 및 Python 또는 R 코드를 사용 하는 웹 서비스를 관리 하 고 콘솔 응용 프로그램에 대 한 원격 세션을 설정 하는 것에 대 한 함수입니다.

## <a name="python"></a>Python

+ [revoscalepy](https://docs.microsoft.com/r-server/python-reference/revoscalepy/revoscalepy-package)

    RevoScaleR 패키지 R 언어에 대 한 Python와 동일 합니다. 동일한 계산 컨텍스트 및 데이터 원본 지원합니다.

+ [Python 용 Microsoftml](https://docs.microsoft.com/r-server/python-reference/microsoftml/microsoftml-package)

    Python 해당 하는 MicrosoftML 오른쪽 지원에 대 한 패키지는 동일한 계산 컨텍스트 및 데이터 원본이 주고 빠르고 확장 가능한 알고리즘 및 Microsoft에서 변환 합니다.

## <a name="related-apis"></a>관련된 Api

+ [RevoPEMAR 함수 참조](https://docs.microsoft.com/r-server/r-reference/revopemar/pemar)

    병렬 알고리즘의 개발 지원

+ [RevoUtils](https://docs.microsoft.com/r-server/r-reference/revoutils/revoutils)

    RevoScaleR 환경 사용 하 여 사용 하기 위해 유틸리티 함수

## <a name="other"></a>기타

"방법" 항목 및 이러한 R 또는 SQL Server에서 Python Api 사용에 대 한 요약 여기 찾을 수 있습니다.

+ [SQL Server를 사용 하기 위한 scaleR 함수](scaler-functions-for-working-with-sql-server-data.md)
+ [Sqlrutils를 사용 하 여 저장된 프로시저를 생성 합니다.](generating-an-r-stored-procedure-for-r-code-using-the-sqlrutils-package.md)
+ [OlapR를 사용 하 여 R로 MDX 데이터 읽기](how-to-create-mdx-queries-using-olapr.md)
