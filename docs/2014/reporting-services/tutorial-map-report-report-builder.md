---
title: '자습서: 맵 보고서(보고서 작성기) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 8d831356-7efa-40cc-ae95-383b3eecf833
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 2218fdb184fb4fe67d110b95c42f10f761ef3975
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48098853"
---
# <a name="tutorial-map-report-report-builder"></a>자습서: 지도 보고서(보고서 작성기)
  이 자습서는 지리적 배경에 대한 보고서 데이터를 표시하는 데 사용할 수 있는 지도 기능을 이해하는 데 도움을 주기 위해 작성되었습니다.  
  
 지도는 일반적으로 점, 선 및 다각형으로 구성된 공간 데이터를 기반으로 합니다. 예를 들어 다각형으로는 군의 경계를 나타내고, 선으로는 도로를 나타내며, 점으로는 도시의 위치를 나타낼 수 있습니다. 각 공간 데이터 형식은 별도의 지도 계층에 지도 요소 집합으로 표시됩니다.  
  
 지도 요소의 모양을 변경하려면 지도 요소를 데이터 집합의 분석 데이터와 일치시키는 값이 있는 필드를 지정합니다. 또한 데이터의 범위에 따라 색, 크기 또는 기타 속성을 변경하는 규칙을 정의할 수도 있습니다.  
  
 이 자습서에서는 뉴욕 주의 군에 있는 상점 위치를 표시하는 지도 보고서를 작성합니다.  
  
##  <a name="BackToTop"></a> 학습할 내용  
 이 자습서에서는 다음 작업 방법을 배웁니다.  
  
1.  [지도 마법사에서 다각형 계층을 사용 하 여 지도 만들기](#Map)  
  
2.  [상점 위치 표시 하려면 지도 점 계층 추가](#PointLayer)  
  
3.  [경로 표시 하려면 지도 선 계층 추가](#LineLayer)  
  
4.  [Bing Maps 타일 배경 추가](#TileLayer)  
  
5.  [계층을 투명 하 게 만들기](#Transparent)  
  
6.  [판매량을 기준으로 군 색 변경](#Vary)  
  
    1.  [공간 및 분석 데이터 간의 관계 만들기](#Relationship)  
  
    2.  [다각형 색 규칙을 지정 합니다.](#ColorRules)  
  
    3.  [색 눈금의 데이터 서식을 통화로 지정](#ColorScale)  
  
    4.  [새 범례 만들기](#NewLegend)  
  
    5.  [연결 범례와 색 규칙](#Associate)  
  
    6.  [데이터가 없는 군에서 색 지우기](#NoData)  
  
7.  [사용자 지정 점 추가](#CustomPoint)  
  
8.  [지도 보기 가운데](#CenterView)  
  
9. [보고서 제목 추가](#Title)  
  
10. [보고서 저장](#Save)  
  
> [!NOTE]  
>  이 자습서에서 마법사의 단계는 두 개의 절차로 통합됩니다. 하나는 데이터 집합을 만드는 절차이고 다른 하나는 테이블을 만드는 절차입니다. 보고서 서버를 찾고, 데이터 원본을 선택하고, 데이터 집합을 만들고, 마법사를 실행하는 방법에 대한 단계별 지침은 이 시리즈의 첫 번째 자습서인 [자습서: 기본 테이블 보고서 만들기&#40;보고서 작성기&#41;](../reporting-services/tutorial-creating-a-basic-table-report-report-builder.md)를 참조하세요.  
  
 이 자습서에 소요되는 예상 시간: 30분  
  
## <a name="requirements"></a>요구 사항  
 요구 사항에 대한 자세한 내용은 [자습서의 필수 조건&#40;보고서 작성기&#41;](../reporting-services/report-builder-tutorials.md)을 참조하세요.  
  
##  <a name="Map"></a> 1. 지도 마법사에서 다각형 계층을 사용하여 지도 만들기  
 지도 갤러리에서 보고서에 뉴욕 주의 군을 표시하는 계층이 하나 있는 지도를 추가합니다. 각 군의 모양은 지도 갤러리의 지도에 포함된 공간 데이터를 기반으로 하는 다각형으로 되어 있습니다.  
  
#### <a name="to-add-a-map-with-the-map-wizard-in-a-new-report"></a>새 보고서에서 지도 마법사를 사용하여 지도를 추가하려면  
  
1.  클릭 **시작**, 가리킨 **프로그램**를 가리킨 [!INCLUDE[ssCurrentUI](../includes/sscurrentui-md.md)] **보고서 작성기**를 클릭 하 고 **보고서 작성기**.  
  
     시작 대화 상자가 나타납니다.  
  
    > [!NOTE]  
    >  시작 대화 상자가 나타나지 않으면 보고서 작성기 단추에서 클릭 **새로 만들기**합니다.  
  
2.  왼쪽된 창에 있는지를 확인 **보고서** 을 선택 합니다.  
  
3.  오른쪽 창에서 **지도 마법사**를 클릭합니다.  
  
4.  **만들기**를 클릭합니다.  
  
5.  **공간 데이터의 원본 선택** 페이지에서 **지도 갤러리** 을 선택 합니다.  
  
6.  지도 갤러리 창의 확장 **States by County** 아래에서 **USA**를 클릭 하 고 **뉴욕**합니다.  
  
     지도 미리 보기 창에 뉴욕 주 지도가 표시됩니다.  
  
7.  **다음**을 클릭합니다.  
  
8.  에 **선택 공간 데이터 및 지도 보기 옵션** 페이지에서 기본값을 사용 합니다. 기본적으로 지도 갤러리의 지도 요소는 보고서 정의에 자동으로 포함됩니다.  
  
9. **다음**을 클릭합니다.  
  
10. **지도 시각화 선택** 페이지에서 **기본 지도** 가 선택되어 있는지 확인하고 **다음**을 클릭합니다.  
  
11. **색 테마 및 데이터 시각화 선택** 페이지에서 **레이블 표시** 옵션을 선택합니다.  
  
12. **단색 지도** 옵션이 선택되어 있으면 선택을 취소합니다.  
  
13. **데이터 필드** 드롭 다운 목록 #COUNTYNAME를 클릭 합니다. 마법사의 지도 미리 보기 창에 다음 항목이 표시됩니다.  
  
    -   **지도 제목**텍스트가 포함된 제목  
  
    -   뉴욕의 군을 표시하는 지도. 각 군이 다른 색이고 군 이름이 군 지역 위의 적절한 곳에 나타납니다.  
  
    -   제목과 항목 1 ~ 5의 목록이 포함된 범례  
  
    -   값 1 ~ 160이 포함되고 색이 없는 색 눈금  
  
    -   킬로미터(km) 및 마일(mi)이 표시되는 거리 눈금  
  
14. **마침**을 클릭합니다.  
  
     디자인 화면에 지도가 추가됩니다.  
  
15. 지도를 선택 하 고 표시를 클릭 합니다 **지도 계층 창**합니다. 합니다 **지도 계층 창** 계층 유형의 다각형 계층이 하나 표시 **Embedded**합니다. 각 군은 이 계층의 포함된 지도 요소입니다.  
  
    > [!NOTE]  
    >  표시 되지 않으면 합니다 **지도 계층** 창 보기의 외부에 현재 표시 될 수 있습니다. 디자인 뷰 창의 아래쪽에 있는 스크롤 막대를 사용하여 뷰를 변경합니다. 또는 합니다 **뷰** 탭을 선택 취소 합니다 **속성** 또는 **보고서 데이터** 디자인 화면 영역을 더 제공 하는 옵션입니다.  
  
16. 지도 제목을 마우스 오른쪽 단추로 누른 **제목 속성**합니다.  
  
17. 제목 텍스트를 바꿉니다 **Sales by Store**합니다.  
  
18. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
19. 보고서를 미리 봅니다.  
  
 렌더링된 보고서에 지도 제목, 지도 및 거리 눈금이 표시됩니다. 군은 지도 다각형 계층에 있습니다. 각 군은 색상표의 색으로 구분되지만 해당 색은 데이터와 연결되어 있지 않은 다각형으로 되어 있습니다. 거리 눈금에는 킬로미터와 마일 단위로 거리가 표시됩니다.  
  
 각 군과 연결된 분석 데이터가 없기 때문에 지도 범례와 색 눈금은 아직 표시되지 않습니다. 이 자습서의 뒷부분에서 분석 데이터를 추가합니다.  
  
##  <a name="PointLayer"></a> 2. 지도 점 계층을 추가하여 상점 위치 표시  
 지도 계층 마법사를 사용하여 상점의 위치를 표시하는 점 계층을 추가할 수 있습니다.  
  
> [!NOTE]  
>  이 자습서의 쿼리에는 데이터 값이 포함되어 있으므로 외부 데이터 원본이 필요하지 않습니다. 따라서 쿼리가 상당히 길어집니다. 비즈니스 환경에서는 쿼리에 데이터가 포함되지 않을 것입니다. 이 자습서의 쿼리는 학습용으로만 제공됩니다.  
  
#### <a name="to-add-a-point-layer-based-on-a-sql-server-spatial-query"></a>SQL Server 공간 쿼리에 따라 점 계층을 추가하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다. 도구 모음에서 **새 계층 마법사** 단추 ![rs_IconMapLayerWizard](../../2014/tutorials/media/rs-iconmaplayerwizard.gif "rs_IconMapLayerWizard")를 클릭합니다.  
  
3.  **공간 데이터의 원본 선택** 페이지에서 **SQL Server 공간 쿼리**를 선택하고 **다음**을 클릭합니다.  
  
4.  에 **SQL Server 공간 데이터가 있는 데이터 집합 선택** 페이지에서 **SQL Server 공간 데이터가 있는 새 데이터 집합을 추가**를 클릭 하 고 **다음**합니다.  
  
5.  **SQL Server 공간 데이터 원본에 대한 연결을 선택하십시오.** 페이지에서 기존 데이터 원본을 선택하거나 보고서 서버로 이동한 후 데이터 원본을 선택합니다.  
  
6.  **다음**을 클릭합니다.  
  
7.  쿼리 페이지의 디자인을 누릅니다 **텍스트로 편집**합니다.  
  
8.  쿼리 창에서 다음 텍스트를 붙여 넣습니다.  
  
    ```  
    Select 114 as StoreKey, 'Contoso Albany Store' as StoreName, 1125 as SellingArea, 'Albany' as City, 'Albany' as County,   
     CAST(1000000 as money) as Sales, CAST('POINT(-73.7472924218681 42.6564617079878)' as geography) AS SpatialLocation  
    UNION ALL SELECT 115 AS StoreKey, 'Contoso New York No.1 Store' AS  StoreName, 500 as SellingArea, 'New York' AS City, 'New York City' as County,  
     CAST('2000000' as money) as Sales, CAST('POINT(-73.9922069374483 40.7549638237402)' as geography) AS SpatialLocation  
    UNION ALL Select 116 as StoreKey, 'Contoso Rochester No.1 Store' as StoreName, 462 as SellingArea, 'Rochester' as City,  'Monroe' as County,    
     CAST(3000000 as money) as Sales, CAST('POINT(-77.624041566786 43.1547066024338)' as geography)  AS SpatialLocation  
    UNION ALL Select 117 as StoreKey, 'Contoso New York No.2 Store' as StoreName, 700 as SellingArea, 'New York' as City,'New York City' as County,    
      CAST(4000000 as money) as Sales, CAST('POINT(-73.9712488 40.7830603)' as geography) AS SpatialLocation  
    UNION ALL Select 118 as StoreKey, 'Contoso Syracuse Store' as StoreName, 680 as SellingArea, 'Syracuse' as City, 'Onondaga' as County,  
     CAST(5000000 as money) as Sales, CAST('POINT(-76.1349120532546 43.0610223535974)' as geography) AS SpatialLocation  
    UNION ALL Select 120 as StoreKey, 'Contoso Plattsburgh Store' as StoreName, 560 as SellingArea, 'Plattsburgh' as City,  'Clinton' as County,  
     CAST(6000000 as money) as Sales, CAST('POINT(-73.4728622833178 44.7028831413324)' as geography) AS SpatialLocation  
    UNION ALL Select 121 as StoreKey, 'Contoso Brooklyn Store' as StoreName, 1125 as SellingArea, 'Brooklyn' as City, 'New York City' as County,  
     CAST(7000000 as money) as Sales, CAST('POINT (-73.9638533447143 40.6785123489351)' as geography) AS SpatialLocation  
    UNION ALL Select 122 as StoreKey, 'Contoso Oswego Store' as StoreName, 500 as SellingArea, 'Oswego' as City, 'Oswego' as County,    
     CAST(8000000 as money) as Sales, CAST('POINT(-76.4602850815536 43.4353224527794)' as geography) AS SpatialLocation  
    UNION ALL Select 123 as StoreKey, 'Contoso Ithaca Store' as StoreName, 460 as SellingArea, 'Ithaca' as City, 'Tompkins' as County,  
     CAST(9000000 as money) as Sales, CAST('POINT(-76.5001866085881 42.4310489934743)' as geography) AS SpatialLocation  
    UNION ALL Select 124 as StoreKey, 'Contoso Rochester No.2 Store' as StoreName, 700 as SellingArea, 'Rochester' as City, 'Monroe' as County,    
     CAST(100000 as money) as Sales, CAST('POINT(-77.6240415667866 43.1547066024338)' as geography) AS SpatialLocation  
    UNION ALL Select 125 as StoreKey, 'Contoso Queens Store' as StoreName, 700 as SellingArea,'Queens' as City, 'New York City' as County,  
     CAST(500000 as money) as Sales, CAST('POINT(-73.7930979029883 40.7152781765927)' as geography) AS SpatialLocation  
    UNION ALL Select 126 as StoreKey, 'Contoso Elmira Store' as StoreName, 680 as SellingArea, 'Elmira' as City, 'Chemung' as County,  
     CAST(800000 as money) as Sales, CAST('POINT(-76.7397414783301 42.0736492742663)' as geography) AS SpatialLocation  
    UNION ALL Select 127 as StoreKey, 'Contoso Poestenkill Store' as StoreName, 455 as SellingArea, 'Poestenkill' as City, 'Rensselaer' as County,    
    CAST(1500000 as money) as Sales, CAST('POINT(-73.5626737425063 42.6940551238618)' as geography) AS SpatialLocation  
    ```  
  
9. 쿼리 디자이너 도구 모음에서 **실행** (**!**)을 클릭합니다.  
  
     결과 집합에 일곱 개의 열이 표시 됩니다: StoreKey, StoreName, SellingArea, City, County, Sales 및 SpatialLocation 합니다. 이 데이터는 소비재를 판매하는 뉴욕 주의 상점 집합을 나타냅니다. 결과 집합의 각 행에는 상점 식별자, 상점 이름, 제품 전시 구역, 상점이 있는 도시와 군, 판매량 합계, 경도와 위도로 나타낸 공간 위치 등이 포함됩니다. 전시 구역의 범위는 455제곱피트(42제곱미터)부터 1125제곱피트(105제곱미터)까지입니다.  
  
10. **다음**을 클릭합니다.  
  
     DataSet1이라는 보고서 데이터 집합이 만들어집니다. 마법사를 완료한 후 보고서 데이터를 사용하여 해당 필드 컬렉션을 볼 수 있습니다.  
  
11. 에 **공간 데이터를 선택 하 고 지도 보기 옵션** 페이지에서 **공간 필드** 는 `SpatialLocation` 하 고는 **계층 유형** 는 **지점**. 이 페이지의 다른 기본값을 적용합니다.  
  
     지도 보기에 각 상점의 위치를 표시하는 원이 표시됩니다.  
  
12. **다음**을 클릭합니다.  
  
13. 분석 데이터에 따라 달라지는 표식을 표시하는 지도 유형을 지정합니다. 지도 시각화 선택 페이지에서 클릭 **분석 표식 지도**를 클릭 하 고 **다음**합니다.  
  
14. 에 **분석 데이터 집합 선택** 페이지에서 DataSet1을 클릭 합니다. 이 데이터 집합에는 새 점 계층에 표시될 분석 데이터와 공간 데이터가 모두 들어 있습니다.  
  
15. **다음**을 클릭합니다.  
  
16. 에 **색 테마 및 데이터 시각화 선택** 페이지에서의 선택을 취소 합니다 **표식 색을 사용 하 여 데이터 시각화** 옵션을 선택한 다음 옵션을 선택 **표식 유형을 사용 하 여 시각화할 데이터**.  
  
17. **데이터 필드**, 선택 `[Sum(SellingArea)]` 는 제품을 전시 하기을 마련 하는 저장소 영역의 크기에 따라 표식 유형을 변경 합니다.  
  
18. **마침**을 클릭합니다.  
  
     보고서에 지도 계층이 추가됩니다. 범례에 SellingArea 값에 따른 표식 유형이 표시됩니다.  
  
     지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다. **지도 계층** 창에 공간 데이터 원본 유형이 **DataRegion**인 새 계층 PointLayer1이 표시됩니다.  
  
19. 범례 제목을 추가합니다. 범례 제목을 마우스 오른쪽 단추로 누른 **범례 제목 속성**합니다.  
  
20. 제목 삭제 유형과 **Display Area (Square Feet)** 합니다.  
  
21. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
22. 마법사를 통해 설정된 기본값을 확인합니다. 에 **지도 계층 창**점 계층을 마우스 오른쪽 단추로 클릭 한 다음 클릭 **표식 유형 규칙**합니다.  
  
     에 **일반** 탭에 표식이 범례에 나타나는 순서 대로 나열 됩니다. 에 **배포** 하위 범위의 수가 탭은 5입니다. 에 **범례** 탭에서 범례 텍스트를로 각 범위의 시작 및 끝 값을 표시 합니다.  
  
23. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
24. 보고서를 미리 봅니다.  
  
 지도에 뉴욕 주에 있는 상점의 위치가 표시됩니다. 각 상점의 표식 유형은 전시 구역에 따라 다릅니다. 이 자습서에는 다섯 개의 전시 구역 범위가 자동으로 계산되어 있습니다.  
  
##  <a name="LineLayer"></a> 3. 지도 선 계층을 추가하여 경로 표시  
 지도 계층 마법사를 사용하여 두 상점 간의 경로를 표시하는 지도 계층을 추가할 수 있습니다. 이 자습서에서는 세 개의 상점 위치를 연결하는 경로를 만듭니다. 비즈니스 애플리케이션에서 이 경로는 상점 간 최적 경로일 수 있습니다.  
  
#### <a name="to-add-a-line-layer-to-map"></a>선 계층을 지도에 추가하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다. 도구 모음에서 클릭 **새 계층 마법사**합니다.  
  
3.  **공간 데이터의 원본 선택** 페이지에서 **SQL Server 공간 쿼리** 를 선택하고 **다음**을 클릭합니다.  
  
4.  **SQL Server 공간 데이터가 있는 데이터 집합을 선택하십시오.** 페이지에서 **SQL Server 공간 데이터가 있는 새 데이터 집합 추가** 를 클릭하고 **다음**을 클릭합니다.  
  
5.  에 **SQL Server 공간 데이터 원본에 대 한 연결 선택**, 첫 번째 절차에서 만든 데이터 원본인 DataSource1을 선택 합니다.  
  
6.  **다음**을 클릭합니다.  
  
7.  **쿼리 디자인** 페이지에서 **텍스트로 편집**을 클릭합니다. 쿼리 디자이너가 텍스트 기반 모드로 전환됩니다.  
  
8.  쿼리 창에서 다음 텍스트를 붙여 넣습니다.  
  
    ```  
    SELECT N'Path' AS Name, CAST('LINESTRING(  
       -76.5001866085881 42.4310489934743,  
       -76.4602850815536 43.4353224527794,  
       -73.4728622833178 44.7028831413324)' AS geography) as Route  
    ```  
  
9. **다음**을 클릭합니다.  
  
     지도에 세 개의 상점을 연결하는 경로가 표시됩니다.  
  
10. **공간 데이터 및 지도 보기 옵션 선택** 페이지에서 **공간 필드** 가 **Route** 이고 **계층 유형** 이 **선**인지 확인합니다. 다른 기본값을 적용합니다.  
  
     지도 보기에 뉴욕 주 북부에 있는 한 상점에서 뉴욕 주 남부에 있는 한 상점까지의 경로가 표시됩니다.  
  
11. **다음**을 클릭합니다.  
  
12. **지도 시각화 선택** 페이지에서 **기본 선 지도**를 클릭하고 **다음**을 클릭합니다.  
  
13. **색 테마 및 데이터 시각화 선택**에서 **단색 지도**옵션을 선택합니다. 경로가 선택한 테마에 따라 단색으로 표시됩니다.  
  
14. **마침**을 클릭합니다.  
  
 지도 공간 데이터 원본 유형 사용 하 여 새 선 계층이 표시 됩니다 **데이터 집합**합니다. 이 예제에서 공간 데이터는 데이터 집합에서 제공되지만 분석 데이터가 선과 연결되어 있지 않습니다.  
  
##  <a name="TileLayer"></a> 4. Bing Maps 타일 배경 추가  
 Bing Maps 타일 배경을 표시하는 지도 계층을 추가합니다.  
  
#### <a name="to-add-a-virtual-earth-tile-background"></a>Virtual Earth 타일 배경을 추가하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다. 도구 모음에서 클릭 **계층 추가**![rs_IconMapAddLayer](../../2014/tutorials/media/rs-iconmapaddlayer.gif "rs_IconMapAddLayer")합니다.  
  
3.  드롭다운 목록에서 **타일 계층**을 클릭합니다.  
  
     **지도 계층** 창의 마지막 계층은 TileLayer1입니다. 기본적으로 타일 계층에는 도로 지도 스타일이 표시됩니다.  
  
    > [!NOTE]  
    >  마법사의 **공간 데이터 및 지도 보기 옵션 선택** 페이지에서 타일 계층을 추가할 수도 있습니다. 이렇게 하려면 **이 지도 보기에 대해 Bing 지도 배경 추가**를 선택합니다. 렌더링된 보고서의 타일 배경에 현재 지도 뷰포트 중심과 확대/축소 수준에 해당하는 Bing Maps 타일이 표시됩니다.  
  
4.  TileLayer1에서 아래쪽 화살표를 클릭 한 다음 클릭 **타일 속성**합니다.  
  
5.  **형식**를 선택 **항공**합니다. 항공 보기에는 텍스트가 포함되지 않습니다.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
##  <a name="Transparent"></a> 5. 계층을 투명하게 만들기  
 한 계층의 항목이 다른 계층을 통과하여 표시되도록 하려면 원하는 효과를 얻을 때까지 계층의 순서와 각 계층의 투명도를 조정합니다.  
  
#### <a name="to-set-the-transparency-of-a-layer"></a>계층의 투명도를 설정하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.  
  
3.  PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 클릭 **계층 데이터**입니다. **지도 다각형 계층 속성** 대화 상자가 열립니다.  
  
4.  **표시 유형**을 클릭합니다.  
  
5.  **투명도 (%)**, 형식 **30**합니다.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 디자인 화면에 군이 반투명으로 표시됩니다.  
  
##  <a name="Vary"></a> 6. 판매량을 기준으로 군 색 변경  
 보고서 처리기가 지도 마법사의 마지막 페이지에서 선택한 테마에 따라 색상표에서 색 값을 자동으로 할당하기 때문에 다각형 계층에 있는 각 군의 색은 서로 다릅니다.  
  
 다음 단계에서는 특정 색을 각 군의 상점별 판매량 범위와 연결하는 색 규칙을 지정합니다. 빨강-노랑-녹색은 상대적인 높은-중간-낮은 판매량을 나타냅니다. 통화를 표시하도록 색 눈금의 형식을 지정합니다. 새 범례에서 연간 판매량 범위를 표시합니다. 상점이 없는 군의 경우 연결된 데이터가 없음을 표시하기 위해 색을 사용하지 않습니다.  
  
###  <a name="Relationship"></a> 6a 합니다. 공간 데이터와 분석 데이터 간의 관계 만들기  
 분석 데이터에 따른 색으로 군 모양을 변경하려면 먼저 분석 데이터를 공간 데이터와 연결해야 합니다. 이 자습서에서는 일치시킬 군 이름을 사용합니다.  
  
##### <a name="to-build-a-relationship-between-spatial-data-and-analytical-data"></a>공간 데이터와 분석 데이터 간의 관계를 만들려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.  
  
3.  PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 클릭 **계층 데이터**입니다. **지도 다각형 계층 속성** 대화 상자가 열립니다.  
  
4.  **분석 데이터**를 클릭합니다.  
  
5.  드롭다운 목록에서 DataSet1을 선택합니다. 이 데이터 집합은 군에 대한 공간 데이터 쿼리를 지정했을 때 마법사에서 만들어진 것입니다.  
  
6.  **일치 시킬 필드**, 클릭 **추가**합니다. 새 행이 추가됩니다.  
  
7.  **공간 데이터 집합에서**, 드롭 다운 목록에서 COUNTYNAME을 클릭 합니다.  
  
8.  **분석 데이터 집합에서**, 드롭 다운 목록에서 [County]를 클릭 합니다.  
  
9. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
10. 보고서를 미리 봅니다.  
  
 공간 데이터 원본과 분석 데이터 집합에서 일치 필드를 지정하면 보고서 처리기가 지도 요소에 따라 분석 데이터를 그룹화할 수 있습니다. 데이터 바인딩된 지도 요소에는 지정한 값에 대한 성공적인 일치 항목이 있습니다.  
  
 상점이 있는 각 군은 마법사에서 선택한 스타일의 색상표를 기반으로 하는 색으로 표시됩니다.  
  
###  <a name="ColorRules"></a> 6b 합니다. 다각형에 대한 색 규칙 지정  
 상점 판매량을 기반으로 각 군의 색을 변경하는 규칙을 만들려면 범위 값, 표시할 범위 내의 하위 범위 수 및 사용할 색을 지정해야 합니다.  
  
##### <a name="to-specify-color-rules-for-all-polygons-that-have-associated-data"></a>연결된 데이터가 있는 모든 다각형에 대한 색 규칙을 지정하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 클릭 **다각형 색 규칙**합니다. **지도 색 규칙 속성** 대화 상자가 열립니다. 색 규칙 옵션 **색상표를 사용하여 데이터 시각화** 가 선택되어 있습니다. 이 옵션은 마법사에서 설정된 것입니다.  
  
3.  **색 범위를 사용하여 데이터 시각화**를 선택합니다. 색상표 옵션이 시작 색, 중간 색 및 마지막 색 옵션으로 바뀝니다.  
  
4.  군별 판매량에 대한 범위 값을 정의합니다. **데이터 필드**의 드롭다운 목록에서 `[Sum(Sales)]`을 선택합니다.  
  
5.  통화가 천 단위로 표시되도록 형식을 변경하려면 식을 다음과 같이 변경합니다. `=Sum(Fields!Sales.Value)/1000`  
  
6.  **시작 색** 을 **빨강**으로 변경합니다.  
  
7.  **마지막 색** 을 **녹색**으로 변경합니다.  
  
     **빨강** 은 낮은 판매량 값을 나타내고, **노랑** 은 중간 판매량 값을 나타내며, **녹색** 은 높은 판매량 값을 나타냅니다. 보고서 처리기는 이러한 값과 **분포** 페이지에서 선택한 옵션에 따라 색의 범위를 계산합니다.  
  
8.  **분포**를 클릭합니다.  
  
9. 분포 유형이 **최적**인지 확인합니다. 5단계에 있는 식의 경우 최적 분포는 각 범위에 있는 항목 수와 각 범위 간격의 균형을 맞추는 하위 범위로 값을 나눕니다.  
  
10. 이 페이지에 있는 다른 옵션에 기본값을 적용합니다. 최적 배포 유형을 선택하는 경우 보고서가 실행될 때 하위 범위의 수가 계산됩니다.  
  
11. **범례**를 클릭합니다.  
  
12. **색 눈금 옵션**에서 **색 눈금에 표시** 가 선택되어 있는지 확인합니다.  
  
13. **이 범례에 표시**의 드롭다운 목록에서 빈 줄을 선택합니다. 이제부터 색 눈금에서만 색 범위가 표시됩니다.  
  
14. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 색 눈금에 빨강, 주황, 노랑, 황록색 및 녹색이 표시됩니다. 각 색은 군별 판매량에 따라 자동으로 계산되는 판매량 범위를 나타냅니다.  
  
###  <a name="ColorScale"></a> 6 c입니다. 색 눈금의 데이터 형식을 통화로 지정  
 기본적으로 데이터는 일반 형식을 사용하지만 사용자 지정 형식을 적용할 수도 있습니다.  
  
##### <a name="to-set-the-format-for-the-color-scale"></a>색 눈금의 형식을 설정하려면  
  
1.  색 눈금을 마우스 오른쪽 단추로 누른 **색 눈금 속성**합니다.  
  
2.  클릭 **번호**합니다.  
  
3.  **범주**, 클릭 **통화**합니다.  
  
4.  **소수 자릿수**, 형식 **0**합니다. 이 형식은 통화에 소수 자릿수가 없음을 지정합니다.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  보고서를 미리 봅니다.  
  
 색 눈금에 각 범위에 대한 통화 형식으로 연간 판매량이 표시됩니다.  
  
###  <a name="NewLegend"></a> 6 d입니다. 새 범례 만들기  
 기본적으로 모든 규칙은 첫 번째 범례에 표시됩니다. 지도의 표시를 향상시키기 위해 범례를 추가할 수 있습니다.  
  
 기본 표시를 변경하려면 새 범례를 만들고 지도 계층에 대한 규칙 결과를 새 범례와 연결합니다.  
  
##### <a name="to-create-a-new-legend"></a>새 범례를 만들려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  뷰포트 외부 지도 마우스 오른쪽 단추로 누른 **범례 추가**합니다. 새 범례가 지도의 기본 위치에 추가됩니다.  
  
3.  범례를 마우스 오른쪽 단추로 누른 **범례 속성**합니다.  
  
4.  **위치 옵션**에서 뷰포트에 상대적으로 범례의 위치를 지정 하는 위치를 클릭 합니다. 디자인 화면의 지도가 변경되어 선택 항목의 효과를 표시합니다.  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
6.  클릭 **Title** 의 범례는 범례 제목을 선택 합니다.  
  
7.  클릭 **Title** 텍스트 삽입 모드로 돌아갑니다. 바꿉니다 **제목** 하 여 **Sales (Thousands)**, 다음 텍스트 외부를 클릭 합니다.  
  
 범례가 확장되어 제목이 표시됩니다.  
  
###  <a name="Associate"></a> 6e 합니다. 범례와 색 규칙 연결  
 각 범례에는 하나 이상의 규칙 결과 집합이 표시될 수 있습니다.  
  
##### <a name="to-associate-a-legend-with-color-rules"></a>범례를 색 규칙과 연결하려면  
  
1.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.  
  
2.  PolygonLayer1에서 아래쪽 화살표를 클릭 한 다음 클릭 **다각형 색 규칙**합니다. **지도 색 규칙 속성** 대화 상자가 열립니다.  
  
3.  **범례**를 클릭합니다.  
  
4.  **색 눈금 옵션**의 선택을 취소 **색 눈금에 표시**합니다.  
  
5.  **범례 옵션**, 드롭 다운 목록에서 Legend2를 선택 합니다. 범례 텍스트 옵션이 나타납니다. 기본적으로 범례 텍스트는 일반 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식 문자열을 사용하여 형식이 지정됩니다. N0의 0은 소수 자릿수가 표시되지 않도록 지정합니다.  
  
6.  **범례 텍스트**, 소수 자릿수 없이 사용 하 여 통화를 지정 하려면 다음 형식을 사용 합니다. `#FROMVALUE {C0} - #TOVALUE {C0}`  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
     디자인 화면의 범례에 통화로 형식이 지정된 예제 데이터를 사용하여 색 범위가 표시됩니다.  
  
8.  보고서를 미리 봅니다.  
  
 연결된 상점과 판매량이 있는 군은 색 규칙에 따라 표시되고 판매량이 없는 군은 무색으로 표시됩니다.  
  
###  <a name="NoData"></a> 6f 합니다. 데이터가 없는 군의 색 변경  
 계층에 있는 모든 지도 요소의 기본 표시 옵션을 설정할 수 있습니다. 색 규칙은 이러한 표시 옵션보다 우선합니다.  
  
##### <a name="to-set-the-display-properties-for-all-elements-on-a-layer"></a>계층의 모든 요소에 대한 표시 속성을 설정하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다.  
  
3.  PolygonLayer1에서 아래쪽 화살표를 클릭한 다음 **다각형 속성**을 클릭합니다. **지도 다각형 속성** 대화 상자가 열립니다. 규칙 기반 표시 옵션이 적용되기 전에 이 대화 상자의 표시 옵션 집합이 계층에 있는 모든 다각형에 적용됩니다.  
  
4.  클릭 **채우기**합니다.  
  
5.  채우기 스타일 임을 확인 **실선입니다.** 인지 확인합니다. 그라데이션과 패턴이 모든 색에 적용됩니다.  
  
6.  **Color**, 아래쪽 화살표를 클릭 하 고 클릭 **연한 강철색**합니다.  
  
7.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
8.  보고서를 미리 봅니다.  
  
 연결된 데이터가 없는 군은 파란색으로 표시되고 에 연결 된 분석 데이터가 있는 군만 표시 합니다 **빨간색** 를 통해 **녹색** 지정한 색 규칙.  
  
##  <a name="CustomPoint"></a> 7. 사용자 지정 점 추가  
 아직 건설 되지 않은 하는 새 저장소를 나타내기 지점을 지정 하 고 사용 합니다 **압정** 표식 유형입니다.  
  
#### <a name="to-add-a-custom-point"></a>사용자 지정 점을 추가하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  지도를 두 번 클릭하여 **지도 계층** 창을 표시합니다. 도구 모음에서 클릭 **계층 추가**를 클릭 하 고 **점 계층**합니다.  
  
     새 점 계층이 지도에 추가됩니다. 기본적으로 점 계층의 공간 데이터 형식은 **포함**입니다.  
  
3.  PointLayer2에서 아래쪽 화살표를 클릭 한 다음 클릭 **점 추가**합니다.  
  
4.  지도 뷰포트로 포인터를 이동합니다. 커서는 십자 기호로 변경됩니다.  
  
5.  점을 추가할 지도의 위치를 클릭합니다. 이 자습서에서는 경로의 시작 부분 옆에 있는 군의 한 위치를 클릭합니다. 원으로 표시된 점이 계층의 클릭한 위치에 추가됩니다. 기본적으로 점이 선택됩니다.  
  
6.  추가한 점을 마우스 오른쪽 단추로 클릭하고 **포함 점 속성**을 클릭합니다.  
  
7.  옵션을 선택 **이 계층의 점 옵션 무시**합니다. 추가 페이지가 대화 상자에 나타납니다. 여기서 설정한 값은 계층 또는 색 규칙에 대한 표시 옵션보다 우선합니다.  
  
8.  클릭 **표식**합니다.  
  
9. 에 대 한 **표식 유형을**를 선택 **별**합니다.  
  
10. [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
11. 보고서를 미리 봅니다.  
  
 추가한 새 점이으로 표시 됩니다는 **별**합니다.  
  
#### <a name="to-add-a-label-for-the-custom-point"></a>사용자 지정 점에 대한 레이블을 추가하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  추가 방금 지점을 마우스 오른쪽 단추로 누른 **포함 점 속성**합니다.  
  
3.  클릭 **레이블을**합니다.  
  
4.  **레이블 텍스트**, 형식 **New Store**합니다.  
  
5.  **배치**에서 **위쪽**을 클릭합니다.  
  
6.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
7.  보고서를 미리 봅니다.  
  
 레이블이 상점 위치 위에 나타납니다.  
  
##  <a name="CenterView"></a> 지도 보기 가운데  
 지도 뷰포트 중심 및 확대/축소 수준을 변경합니다.  
  
#### <a name="to-change-the-viewport"></a>뷰포트를 변경하려면  
  
1.  지도 뷰포트를 마우스 오른쪽 단추로 누른 **뷰포트 속성**합니다.  
  
2.  클릭 **중심 및 확대/축소**합니다.  
  
3.  확인 옵션 **보기 중심 및 확대/축소 수준 설정** 을 선택 합니다.  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
5.  지도 뷰포트를 마우스 왼쪽 단추로 클릭하고 뷰포트의 중심을 원하는 위치로 끕니다.  
  
6.  마우스 휠을 사용하여 뷰포트의 확대/축소 수준을 변경합니다.  
  
7.  보고서를 미리 봅니다.  
  
 디자인 뷰의 화면과 보기에 지도가 예제 데이터를 기반으로 표시됩니다. 렌더링된 보고서에서는 지도 보기가 지정한 보기의 가운데에 표시됩니다.  
  
##  <a name="Title"></a> 보고서 제목 추가  
  
#### <a name="to-add-a-report-title"></a>보고서 제목을 추가하려면  
  
1.  디자인 화면에서 **제목을 추가하려면 클릭하십시오.** 를 클릭합니다.  
  
2.  **Sales in New York Stores** 를 입력한 다음 입력란 바깥쪽을 클릭합니다.  
  
 이 제목은 보고서 맨 위에 나타납니다. 페이지 머리글이 정의되지 않았을 때 보고서 본문의 맨 위에 있는 항목은 보고서 머리글에 해당합니다.  
  
##  <a name="Save"></a> 보고서 저장  
  
#### <a name="to-save-the-report"></a>보고서를 저장하려면  
  
1.  디자인 뷰로 전환합니다.  
  
2.  보고서 작성기 단추에서 **다른 이름으로 저장**을 클릭합니다.  
  
3.  **이름**에 **Store Sales in New York**을 입력합니다.  
  
 **저장**을 클릭합니다.  
  
## <a name="next-steps"></a>다음 단계  
 보고서에 지도를 추가하는 방법에 대한 연습을 완료했습니다.  
  
 자세한 내용은 [맵 &#40;보고서 작성기 및 SSRS&#41; ](report-design/maps-report-builder-and-ssrs.md) 및 블로그 [지도 조정의 공간 데이터를 SQL Server Reporting Services](http://go.microsoft.com/fwlink/?LinkId=152771) blogs.msdn.com에서.  
  
 다른 자습서를 참조 하세요 [자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md)합니다.  
  
## <a name="see-also"></a>관련 항목  
 [자습서 &#40;보고서 작성기&#41;](report-builder-tutorials.md)   
 [SQL Server 2014의에서 보고서 작성기](report-builder/report-builder-in-sql-server-2016.md)   
 [지도 마법사 및 지도 계층 마법사&#40;보고서 작성기 및 SSRS&#41;](report-design/map-wizard-and-map-layer-wizard-report-builder-and-ssrs.md)   
 [규칙 및 분석 데이터를 사용하여 다각형, 선 및 점 표시 변경&#40;보고서 작성기 및 SSRS&#41;](report-design/vary-polygon-line-and-point-display-by-rules-and-analytical-data.md)  
  
  
