---
title: Tutorial 프로젝트를 Services 분석의 수정된 된 버전을 사용 하 여 | Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 93847b7e6cade7d77774603ba1852c16a5a783b7
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/10/2018
ms.locfileid: "34017700"
---
# <a name="lesson-4-1---using-a-modified-version-of-the-analysis-services-tutorial-project"></a>단원 4-1-Analysis Services Tutorial 프로젝트의 수정된 된 버전을 사용 하 여
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

이 자습서의 나머지 단원은 처음 세 단원에서 완료한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트의 향상된 버전을 기반으로 합니다. 추가 테이블과 명명된 계산이 **Adventure Works DW 2012** 데이터 원본 뷰에 추가되고 추가 차원이 프로젝트에 추가되었으며 이러한 새 차원이 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에 추가되었습니다. 또한 두 번째 팩트 테이블에서 가져온 측정값을 포함하는 두 번째 측정값 그룹이 추가되었습니다. 이 향상된 프로젝트를 사용하면 이미 배운 기술을 반복하지 않아도 비즈니스 인텔리전스 애플리케이션에 기능을 추가하는 방법을 계속 익힐 수 있습니다.  
  
자습서를 계속 진행하려면 먼저 향상된 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 다운로드하고 압축을 풀고 로드하고 처리해야 합니다.  이 단원의 지침을 사용하여 모든 단계를 수행했는지 확인합니다.  
  
## <a name="downloading-and-extracting-the-project-file"></a>프로젝트 파일 다운로드 및 압축 풀기  
  
1.  이 자습서와 함께 제공되는 샘플 프로젝트를 제공하는 다운로드 페이지로 이동하려면 [여기를 클릭](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks-analysis-services)하세요. 에 포함 된 자습서 프로젝트는 **adventure-works-다차원-자습서-projects.zip** 다운로드 합니다.  
  
2.  클릭 **adventure-works-다차원-자습서-projects.zip** 이 자습서에 대 한 프로젝트를 포함 하 여 패키지를 다운로드 합니다.  
  
    기본적으로 .zip 파일은 Downloads 폴더에 저장됩니다. .zip 파일을 짧은 경로 위치로 이동해야 합니다. 예를 들어 파일을 저장할 C:\Tutorials 폴더를 만듭니다.  그런 다음 .zip 파일에 포함된 파일의 압축을 풉니다. Downloads 폴더에 있는 긴 경로 파일의 압축을 풀면 1단원만 사용할 수 있습니다.  
  
3.  루트 드라이브 또는 루트 드라이브 근처에 하위 폴더(예: C:\Tutorial)를 만듭니다.  
  
4.  이동 된 **adventure-works-다차원-자습서-projects.zip** 하위 폴더에는 파일입니다.  
  
5.  이 파일을 마우스 오른쪽 단추로 클릭하고 **압축 풀기**를 선택합니다.  
  
6.  **Lesson 4 Start** 폴더로 이동하여 **Analysis Services Tutorial.sln** 파일을 찾습니다.  
  
## <a name="loading-and-processing-the-enhanced-project"></a>향상된 프로젝트 로드 및 처리  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]의 **파일** 메뉴에서 **솔루션 닫기** 를 클릭하여 사용하지 않을 파일을 닫습니다.  
  
2.  **파일** 메뉴에서 **열기**를 가리킨 다음 **프로젝트/솔루션**을 클릭합니다.  
  
3.  자습서 프로젝트 파일의 압축을 푼 위치를 찾습니다.  
  
    **Lesson 4 Start**폴더를 찾은 다음 Analysis Services Tutorial.sln을 두 번 클릭합니다.  
  
4.  향상된 버전의 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트를 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]의 로컬 인스턴스나 다른 인스턴스에 배포하고 처리가 제대로 완료되는지 확인합니다.  
  
## <a name="understanding-the-enhancements-to-the-project"></a>프로젝트의 향상된 기능 이해  
향상된 버전의 프로젝트는 처음 세 단원에서 완료한 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트 버전과 다릅니다. 그 차이에 대해서는 다음 섹션에서 설명합니다. 자습서의 나머지 단원을 계속 진행하기 전에 이 내용을 검토해 보십시오.  
  
### <a name="data-source-view"></a>데이터 원본 뷰  
향상된 프로젝트의 데이터 원본 뷰에는 추가 팩트 테이블 하나와 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스에서 가져온 추가 차원 테이블 4개가 포함됩니다.  
  
데이터 원본 뷰의 테이블이 10개가 되면 <All Tables> 다이어그램이 복잡해지기 시작합니다. 이렇게 되면 테이블 간의 관계를 파악하고 특정 테이블을 찾기가 어려워집니다. 이 문제를 해결하기 위해 테이블은 두 개의 논리적 다이어그램인 **Internet Sales** 다이어그램과 **Reseller Sales** 다이어그램으로 구성됩니다. 이러한 다이어그램은 하나의 팩트 테이블 주위에 각각 구성됩니다. 논리적 다이어그램을 만들면 항상 하나의 다이어그램에서 모든 테이블과 관계를 보는 대신 데이터 원본 뷰에서 특정 테이블 하위 집합을 보면서 작업할 수 있습니다.  
  
#### <a name="internet-sales-diagram"></a>Internet Sales 다이어그램  
**Internet Sales** 다이어그램에는 인터넷을 통해 고객과 직접 이루어지는 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 제품 판매와 관련된 테이블이 있습니다. 다이어그램의 테이블은 1단원에서 **Adventure Works DW 2012** 데이터 원본 뷰에 추가한 차원 테이블 4개와 팩트 테이블 1개입니다. 이러한 테이블은 다음과 같습니다.  
  
-   **지리**  
  
-   **Customer**  
  
-   **날짜**  
  
-   **Product**  
  
-   **InternetSales**  
  
#### <a name="reseller-sales-diagram"></a>Reseller Sales 다이어그램  
**Reseller Sales** 다이어그램에는 대리점을 통한 [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 제품 판매와 관련된 테이블이 있습니다. 이 다이어그램에는 다음과 같이 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 데이터베이스에서 가져온 차원 테이블 7개와 팩트 테이블 1개가 있습니다.  
  
-   **Reseller**  
  
-   **홍보 행사**  
  
-   **SalesTerritory**  
  
-   **지리**  
  
-   **날짜**  
  
-   **Product**  
  
-   **Employee**  
  
-   **ResellerSales**  
  
**DimGeography**, **DimDate**및 **DimProduct** 테이블은 **Internet Sales** 다이어그램과 **Reseller Sales** 다이어그램 둘 다에서 사용됩니다. 차원 테이블을 여러 팩트 테이블에 연결할 수 있습니다.  
  
### <a name="database-and-cube-dimensions"></a>데이터베이스 및 큐브 차원  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 프로젝트에는 새 데이터베이스 차원 5개가 있고 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial 큐브에는 큐브 차원과 동일한 차원 5개가 있습니다. 이러한 차원은 명명된 계산, 컴퍼지션 멤버 키 및 표시 폴더를 사용하여 수정된 사용자 계층과 특성을 갖도록 정의되었습니다. 새로운 차원에 대해서는 다음 목록에서 설명합니다.  
  
Reseller 차원  
Reseller 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Reseller** 테이블을 기반으로 합니다.  
  
Promotion 차원  
Promotion 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Promotion** 테이블을 기반으로 합니다.  
  
Sales Territory 차원  
Sales Territory 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **SalesTerritory** 테이블을 기반으로 합니다.  
  
Employee 차원  
Employee 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Employee** 테이블을 기반으로 합니다.  
  
Geography 차원  
Geography 차원은 **Adventure Works DW 2012** 데이터 원본 뷰의 **Geography** 테이블을 기반으로 합니다.  
  
#### <a name="analysis-services-cube"></a>Analysis Services 큐브  
이제 **Analysis Services Tutorial** 큐브에는 두 개의 측정값 그룹, 즉 **InternetSales** 테이블을 기반으로 하는 원래의 측정값 그룹과 **Adventure Works DW 2012** 데이터 원본 뷰의 **ResellerSales** 테이블을 기반으로 하는 두 번째 측정값 그룹이 있습니다.  
  
## <a name="next-task-in-lesson"></a>단원의 다음 태스크  
[부모-자식 계층의 부모 특성 속성 정의](../analysis-services/lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
  
## <a name="see-also"></a>관련 항목:  
[Analysis Services 프로젝트 배포](../analysis-services/lesson-2-5-deploying-an-analysis-services-project.md)  
  
