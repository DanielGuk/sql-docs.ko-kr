---
title: "열 속성(Visual Database Tools) | Microsoft 문서"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vdt.designers.properties.Column.ColumnIdentitySpec
- vdt.designers.properties.Column
- vdt.tablecolumn
- vdt.designers.properties.Column.ColumnComputedColumnSpec
- vdt.designers.properties.Column.ColumnFulltextSpec
ms.assetid: e549a2a8-4154-4ec8-b146-614564169b39
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: dfd26bcff6aa621967ab9295ac65a92718db9f8c
ms.lasthandoff: 04/11/2017

---
# <a name="column-properties-visual-database-tools"></a>열 속성(Visual Database Tools)
열 속성 집합에는 테이블 디자이너([!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 데이터베이스에서만 사용 가능) 내 **열 속성** 탭에서 볼 수 있는 전체 집합과 서버 탐색기를 사용하여 속성 창에서 볼 수 있는 하위 집합이 있습니다.  
  
> [!NOTE]  
> 이 항목의 속성은 사전순 대신 범주별로 정렬됩니다.  
  
> [!NOTE]  
> 활성 설정 또는 버전에 따라 표시되는 대화 상자 및 메뉴 명령이 도움말에 설명된 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다.  
  
## <a name="properties-window"></a>속성 창  
서버 탐색기에서 열을 선택하면 이러한 속성이 속성 창에 나타납니다.  
  
> [!NOTE]  
> 서버 탐색기를 사용하여 액세스할 수 있는 이러한 속성은 읽기 전용입니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 데이터베이스의 열 속성을 편집하려면 테이블 디자이너에서 해당 열을 선택합니다. 이러한 속성은 이 항목의 뒷부분에서 설명합니다.  
  
**ID 범주**  
확장하면 **이름** 및 **데이터베이스** 속성이 표시됩니다.  
  
**이름**  
열의 이름을 표시합니다.  
  
**데이터베이스**  
선택한 열에 대한 데이터 원본의 이름을 표시합니다. OLE DB에만 적용됩니다.  
  
**기타 범주**  
확장하면 나머지 속성이 표시됩니다.  
  
**데이터 형식**  
선택한 열의 데이터 형식을 표시합니다. 자세한 내용은 [데이터 형식(Transact-SQL)](http://msdn.microsoft.com/en-us/a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)을 참조하세요.  
  
**ID 증가값**  
ID 열의 각 후속 행에 대한 **ID 초기값** 에 추가할 증가값을 표시합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]에만 적용됩니다.  
  
**ID 초기값**  
ID 열에 대한 테이블의 첫 번째 행에 할당된 초기값을 표시합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]에만 적용됩니다.  
  
**ID**  
선택한 열이 테이블에 대한 ID 열인지 여부를 표시합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]에만 적용됩니다.  
  
**길이**  
문자 기반 데이터 형식에 허용되는 문자 수를 표시합니다.  
  
**Null 허용**  
열에 Null 값이 허용되는지 여부를 표시합니다.  
  
**전체 자릿수**  
숫자 데이터 형식에 허용되는 최대 자릿수를 표시합니다. 이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.  
  
**소수 자릿수**  
숫자 데이터 형식에 대해 소수점 오른쪽에 나타날 수 있는 최대 자릿수를 표시합니다. 이 값은 전체 자릿수보다 작거나 같아야 합니다. 이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다.  
  
## <a name="column-properties-tab"></a>열 속성 탭  
이러한 속성에 액세스하려면 서버 탐색기에서 열이 속하는 테이블을 마우스 오른쪽 단추로 클릭한 다음 **테이블 정의 열기**를 선택하고 테이블 디자이너에서 테이블 표의 행을 선택합니다.  
  
> [!NOTE]  
> 이러한 속성은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]에만 적용됩니다.  
  
**일반 범주**  
확장하면 **이름**, **Null 허용**, **데이터 형식**, **기본값 또는 바인딩**, **길이**, **정밀도**및 **소수 자릿수**가 표시됩니다.  
  
**이름**  
열의 이름을 표시합니다. 이름을 편집하려면 입력란에 입력합니다.  
  
> [!CAUTION]  
> 기존 쿼리, 뷰, 사용자 정의 함수, 저장 프로시저 또는 프로그램에서 해당 열을 참조하는 경우 이름을 수정하면 이러한 개체를 사용할 수 없게 됩니다.  
  
**Null 허용**  
열의 데이터 형식에 Null 값이 허용되는지 여부를 표시합니다.  
  
**데이터 형식**  
선택한 열의 데이터 형식을 표시합니다. 이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다. 자세한 내용은 [데이터 형식(Transact-SQL)](http://msdn.microsoft.com/en-us/a54f7373-b247-4d61-8fb8-7f2ec7a8d0a4)을 참조하세요.  
  
**기본값 또는 바인딩**  
이 열에 대해 지정한 값이 없는 경우 이 열에 대한 기본값을 표시합니다. 드롭다운 목록에는 데이터 원본에 정의된 모든 전역 기본값이 포함되어 있습니다. 열을 전역 기본값에 바인딩하려면 드롭다운 목록에서 선택합니다. 열에 대한 기본 제약 조건을 만들려면 직접 기본값을 텍스트로 입력합니다.  
  
**길이**  
문자 기반 데이터 형식에 허용되는 문자 수를 표시합니다. 이 속성은 문자 기반 데이터 형식에 대해서만 사용할 수 있습니다.  
  
**전체 자릿수**  
숫자 데이터 형식에 허용되는 최대 자릿수를 표시합니다. 이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다. 이 속성은 숫자 데이터 형식에만 사용할 수 있습니다.  
  
**소수 자릿수**  
숫자 데이터 형식에 대해 소수점 오른쪽에 나타날 수 있는 최대 자릿수를 표시합니다. 이 값은 전체 자릿수보다 작거나 같아야 합니다. 이 속성은 숫자가 아닌 데이터 형식에 대해 **0** 을 표시합니다. 이 속성은 숫자 데이터 형식에만 사용할 수 있습니다.  
  
**테이블 디자이너 범주**  
확장하면 나머지 속성이 표시됩니다.  
  
**데이터 정렬**  
선택한 열에 대한 데이터 정렬 설정을 표시합니다. 이 설정을 변경하려면 **데이터 정렬** 을 클릭한 다음 값의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.  
  
**계산 열 사양 범주**  
확장하면 **수식** 및 **지속됨**의 속성이 표시됩니다. 계산 열인 경우 수식도 표시됩니다. 수식을 편집하려면 이 범주를 확장한 다음 **수식** 속성에서 편집합니다.  
  
**수식**  
선택한 계산 열에서 사용하는 수식을 표시합니다. 이 필드에서 수식을 입력 또는 변경할 수 있습니다.  
  
**지속됨**  
계산 열을 데이터 원본과 함께 저장할 수 있습니다. 지속형 계산 열은 인덱싱할 수 있습니다.  
  
**압축 데이터 형식**  
필드의 데이터 형식에 대한 정보를 SQL CREATE TABLE 문과 동일한 형식으로 표시합니다. 예를 들어 최대 길이가 20자인 가변 길이 문자열을 포함하는 필드는 "varchar(20)"으로 나타납니다. 이 속성을 변경하려면 직접 값을 입력합니다.  
  
**Description**  
열에 대한 설명을 표시합니다. 전체 설명을 보거나 편집하려면 설명을 클릭한 다음 속성의 오른쪽에 있는 줄임표 **(...)** 를 클릭합니다.  
  
**전체 텍스트 사양 범주**  
확장하면 전체 텍스트 열의 속성이 표시됩니다.  
  
**전체 텍스트가 인덱싱됨**  
이 열이 전체 텍스트 인덱싱되었는지 여부를 나타냅니다. 이 열의 데이터 형식이 전체 텍스트로 검색 가능한 경우 및 이 열이 속하는 테이블에 전체 텍스트 인덱스가 지정되어 있는 경우에만 이 속성을 **예** 로 설정할 수 있습니다. 이 값을 변경하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 새 값을 선택합니다.  
  
**전체 텍스트 형식 열**  
IMAGE 유형 열의 문서 유형을 정의하는 데 사용되는 열을 표시합니다. IMAGE 데이터 형식을 사용하여 .doc 파일에서 .xml 파일에 이르는 문서를 저장할 수 있습니다.  
  
**언어**  
열을 인덱싱하는 데 사용되는 언어를 나타냅니다.  
  
**통계 의미 체계**  
선택한 열에 대해 통계 의미 체계 인덱싱을 사용하도록 설정할지 여부를 선택합니다. 자세한 내용은 [의미 체계 검색 자리 표시자](http://msdn.microsoft.com/en-us/cd8faa9d-07db-420d-93f4-a2ea7c974b97)를 참조하세요.  
  
**통계 의미 체계** 를 선택하기 전에 **언어**를 선택했으며 선택한 언어에 연결된 의미 체계 언어 모델이 없으면 **통계 의미 체계** 옵션은 **아니요** 로 설정되며 수정할 수 없습니다. **언어** 를 선택하기 전에 **통계 의미 체계** 옵션에 대해 **예**를 선택한 경우 **언어** 열에서 사용할 수 있는 언어는 의미 체계 언어 모델이 지원되는 언어로 제한됩니다.  
  
**SQL Server 이외 구독자가 있음**  
열에 Microsoft SQL Server 이외의 구독자가 있는지 여부를 표시합니다.  
  
**ID 사양 범주**  
확장하면 **ID**, **ID 증가값**및 **ID 초기값**의 속성이 표시됩니다.  
  
**ID**  
선택한 열이 테이블에 대한 ID 열인지 여부를 표시합니다. 속성을 변경하려면 테이블 디자이너에서 테이블을 연 다음 **속성** 창에서 속성을 편집합니다. 이 설정은 *int*와 같은 번호 기반 데이터 형식의 열에만 적용됩니다.  
  
**ID 증가값**  
각 후속 행에 대한 **ID 초기값** 에 추가할 증가값을 표시합니다. 이 셀에 값을 입력하지 않으면 기본적으로 값 1이 지정됩니다. 이 속성을 편집하려면 직접 새 값을 입력합니다.  
  
**ID 초기값**  
테이블의 첫 번째 행에 할당된 값을 표시합니다. 이 셀에 값을 입력하지 않으면 기본적으로 값 1이 지정됩니다. 이 속성을 편집하려면 직접 새 값을 입력합니다.  
  
**명확함**  
선택한 열의 데이터 형식을 확실하게 결정할 수 있는지 여부를 표시합니다.  
  
**DTS 게시됨**  
열의 DTS 게시 여부를 표시합니다.  
  
**인덱싱 가능**  
선택한 열을 인덱싱할 수 있는지 여부를 표시합니다. 예를 들어 비결정적 계산 열은 인덱싱할 수 없습니다.  
  
**병합 게시됨**  
열의 병합 게시 여부를 표시합니다.  
  
**복제용 아님**  
복제하는 동안 원래 ID 값의 유지 여부를 나타냅니다. 이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다.  
  
**복제됨**  
이 열이 다른 위치에 복제되었는지 여부를 표시합니다.  
  
**RowGuid**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에서 열을 ROWGUID로 사용하는지 여부를 나타냅니다. 데이터 형식이 **uniqueidentifier** 인 열에 대해서만 이 값을 **예**로 설정할 수 있습니다. 이 속성을 편집하려면 해당 값을 클릭하고 드롭다운 목록을 확장한 다음 다른 값을 선택합니다.  
  
**크기**  
열의 데이터 형식에 허용되는 크기(바이트)를 표시합니다. 예를 들어 **nchar** 데이터 형식의 경우 길이가 10(문자 수)까지 허용되며 유니코드 문자 집합의 경우에는 크기가 20까지 허용될 수 있습니다.  
  
> [!NOTE]  
> **varchar(max)** 데이터 형식의 길이는 각 행에 따라 다릅니다. sp_help는 **varchar(max)** 열의 길이로 (-1)을 반환합니다. [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] 는 열 크기로 -1을 표시합니다.  
  
