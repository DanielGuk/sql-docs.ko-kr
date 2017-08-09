---
title: "테스트 사례 (SybaseToSQL) 실행 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Tester Component,Execution Steps
ms.assetid: 195ffdef-cfde-4bf4-a3ae-e7402bb07972
caps.latest.revision: 6
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 80c335253aef5dd676ece990cb34feb5d67da829
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="running-test-cases-sybasetosql"></a>테스트 사례 (SybaseToSQL) 실행
SSMA 테스터는 테스트 사례를 실행 하면 테스트를 위해 선택한 개체를 실행 하 고 확인 결과 대 한 보고서를 만듭니다. 결과 두 플랫폼 모두에서 동일한 경우에 테스트에 성공 합니다. Sybase 사이 개체의 관계 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 현재 SSMA 프로젝트에 대 한 스키마 매핑이 설정에 따라 결정 됩니다.  
  
성공적인 테스트에 대 한 필요한 요구 사항은 모든 Sybase 개체 변환 되 고 대상 데이터베이스에 로드입니다. 또한 테이블 데이터를 두 플랫폼 모두에 있는 테이블의 내용이 동기화 마이그레이션해야 합니다.  
  
## <a name="run-test-case"></a>테스트 사례 실행  
실행 하려면 테스트 사례 준비:  
  
1.  클릭는 **실행** 단추입니다.  
  
2.  에 **Sybase 연결할** 대화 상자에서 연결 정보를 입력 한 다음 클릭 **연결**합니다.  
  
테스트 완료 되 면 테스트 사례 보고서가 생성 됩니다. 클릭는 **보고서** 보려는 단추는 [테스트 사례 보고서 보기 &#40; SybaseToSQL &#41; ](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md). 테스트 (테스트 사례 보고서)의 결과에 자동으로 저장 되는 [테스트 리포지토리를 사용 하 여 &#40; SybaseToSQL &#41; ](../../ssma/sybase/using-test-repositories-sybasetosql.md) 나중에 사용할 수 있습니다.  
  
## <a name="test-case-execution-steps"></a>테스트 사례 실행 단계  
  
### <a name="prerequisites"></a>필수 구성 요소  
SSMA 테스터는 테스트를 시작 하기 전에 테스트 실행에 대 한 모든 필수 조건이 충족 하는 경우를 확인 합니다. 일부 조건이 충족 되지 않은 경우 오류 메시지가 나타납니다.  
  
### <a name="initialization"></a>초기화  
이 단계에서 SSMA 테스터 만듭니다 보조 개체 (테이블, 트리거 및 뷰) 모두에 Sybase 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다. 추적 테이블에서 변경 내용을 영향을 받는 테이블 비교 모드는 하는 경우 확인을 위해 선택 허용 **만 변경**합니다.  
  
확인 된 테이블 이름이 USER_TABLE 이라고 가정 합니다. 이러한 테이블에 대 한 다음과 같은 보조 개체는 Sybase에서 생성 됩니다.  
  
다음 개체는 SSMATESTER2005db 또는 SSMATESTER2008db 데이터베이스에서 및 Sybase에서 만들어집니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] ssmatesterdb_syb 데이터베이스에 있습니다.  
  
|이름|유형|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|트리거|확인 된 테이블에 변경 내용을 감사 하는 트리거.|  
|USER_TABLE$ Aud|테이블|덮어쓴 및 삭제 된 행을 저장 하는 테이블입니다.|  
|USER_TABLE$ AudID|테이블|새로운 기능과 변경 된 행을 저장 하는 테이블입니다.|  
|USER_TABLE|보기|테이블 수정의 단순화 된 표현입니다.|  
|새 USER_TABLE $|보기|삽입 되거나 덮어쓴 행의 단순화 된 표현입니다.|  
|USER_TABLE$ new_id|보기|삽입 되거나 변경 된 행의 id입니다.|  
|이전 USER_TABLE $|보기|덮어쓴 및 삭제 된 행의 단순화 된 표현입니다.|  
  
Sybase에서 확인 된 테이블의 데이터베이스에서 다음과 같은 개체를 만들 및 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]합니다.  
  
|이름|유형|Description|  
|--------|--------|---------------|  
|USER_TABLE$ Trg|트리거|확인 된 테이블에 변경 내용을 감사 하는 트리거.|  
  
### <a name="test-object-calls"></a>테스트 개체 호출  
이 단계에서 SSMA 테스터 호출에서 테스트를 위해 선택한 각 개체, 결과 비교 하 고 보고서를 보여 줍니다.  
  
### <a name="finalization"></a>종료  
종료 하는 동안 SSMA 테스터에서 생성 된 보조 개체를 정리는 **초기화** 단계입니다.  
  
## <a name="next-step"></a>다음 단계  
[테스트 사례 보고서 보기 &#40; SybaseToSQL &#41;](../../ssma/sybase/viewing-test-case-reports-sybasetosql.md)  
  
## <a name="see-also"></a>참고 항목  
[선택 하 고 테스트 &#40; 개체를 구성 합니다. SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-objects-to-test-sybasetosql.md)  
[선택 하 고 영향을 받는 개체 &#40; 구성 합니다. SybaseToSQL &#41;](../../ssma/sybase/selecting-and-configuring-affected-objects-sybasetosql.md)  
[데이터베이스 개체 &#40; 마이그레이션 테스트 SybaseToSQL &#41;](../../ssma/sybase/testing-migrated-database-objects-sybasetosql.md)  
  
