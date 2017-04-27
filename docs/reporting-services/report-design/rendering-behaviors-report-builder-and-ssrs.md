---
title: "렌더링 동작(보고서 작성기 및 SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8f873ef9-27a3-40e5-b58b-6774f8027a58
caps.latest.revision: 7
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 7
---
# 렌더링 동작(보고서 작성기 및 SSRS)
  보고서를 렌더링하는 경우 선택한 렌더러에 따라 보고서 본문 및 해당 내용에 특정 규칙이 적용됩니다. 여러 보고서 항목이 한 페이지에 함께 포함되는 방식은 다음과 같은 요소의 조합에 따라 결정됩니다.  
  
-   렌더링 규칙  
  
-   보고서 항목의 너비와 높이  
  
-   보고서 본문의 크기  
  
-   페이지의 너비와 높이  
  
-   렌더러별 페이징 지원  
  
 이 항목에서는 Reporting Services에서 적용하는 일반적인 규칙에 대해 설명합니다. 자세한 내용은 [보고서 항목 렌더링&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/rendering-report-items-report-builder-and-ssrs.md), [데이터 영역 렌더링&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/rendering-data-regions-report-builder-and-ssrs.md) 및 [데이터 렌더링&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/rendering-data-report-builder-and-ssrs.md)을 참조하세요.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## HTML, MHTML, Word 및 Excel 등 소프트 페이지 나누기 렌더러의 일반적인 동작  
 HTML 및 MHTML 형식을 사용하여 내보낸 보고서는 다양한 길이의 페이지가 표시되는 컴퓨터 화면 기반 환경에 최적화됩니다. 페이지 나누기는 보고서 본문 내의 근사 위치에서만 세로로 삽입됩니다. 이러한 근사 위치는 속성 창에서 설정하는 대화형 높이를 통해 결정됩니다. 예를 들어 대화형 높이가 5인치로 설정된 경우를 가정해 봅니다. 보고서가 렌더링되면 페이지 높이는 대략 5인치가 됩니다. Word 및 Excel에서는 논리적 페이지 나누기에 기반하여 페이지를 매기며 대화형 높이 설정을 무시합니다.  
  
> [!NOTE]  
>  소프트 페이지 나누기 렌더러에서 보고서가 표시되는 방식을 결정하려면 보고서 미리 보기를 사용합니다. 이 미리 보기에서 보고서는 HTML, MHTML, Word 또는 Excel 형식으로 렌더링된 보고서와 동일하게 표시됩니다.  
  
 HTML, MHTML, Word 또는 Excel로 보고서를 내보내는 경우 다음과 같은 일반적인 규칙이 적용됩니다.  
  
-   사용자가 명시적으로 삽입한 논리적 페이지 나누기가 보고서 항목에 적용됩니다. 예를 들어 각 그룹 사이에 페이지 나누기를 삽입한 경우 보고서가 렌더링될 때 해당 페이지 나누기가 적용됩니다.  
  
-   근사 레이아웃은 페이지 높이 및 보고서 항목이 나타나는 횟수를 기반으로 만들어집니다. 예를 들어 높이 .5인치의 입력란이 보고서에 5번 나타나면 2.5인치가 예약됩니다.  
  
-   소프트 페이지 나누기가 여러 개인 경우 대화형 높이 설정에 기반하여 삽입됩니다. HTML 및 ReportViewer 컨트롤에서 소프트 페이지 나누기를 표시하지 않고 명시적 페이지 나누기만을 사용하여 페이지 매김을 제어하려면 **interactive height** 값을 0 또는 매우 큰 숫자로 설정합니다.  
  
    > [!NOTE]  
    >  대화형 너비 설정은 소프트 페이지 나누기 렌더러에서 사용되지 않습니다.  
  
-   한 페이지에 함께 유지해야 하는 보고서 항목, 분리된 항목 및 창을 한 페이지에 포함하기 위해 보고서 페이지의 크기가 늘어날 수 있습니다. 따라서 보고서가 화면 너비보다 커질 수 있으며 이에 따라 슬라이더 막대를 사용하여 보고서를 보아야 할 수도 있습니다.  
  
-   페이지 매김은 세로로만 보고서에 적용됩니다.  
  
-   페이지 여백은 적용되지 않습니다.  
  
## PDF, 이미지 및 인쇄 등 하드 페이지 나누기 렌더러의 일반적인 동작  
 PDF 및 이미지를 사용하여 내보낸 보고서는 페이지 크기가 일정한 책 또는 인쇄물 환경에 최적화됩니다. 페이지 나누기는 보고서 본문 내의 특정 위치에 세로 및 가로로 삽입됩니다. 이러한 특정 위치는 페이지 너비 및 페이지 높이 설정을 통해 결정됩니다.  
  
> [!NOTE]  
>  하드 페이지 나누기 렌더러에서 보고서가 표시되는 방식을 결정하려면 인쇄 미리 보기를 사용합니다. 이 미리 보기에서 보고서는 PDF, 이미지 형식으로 렌더링된 보고서와 동일하게 표시됩니다.  
  
-   페이지 번호는 왼쪽에서 오른쪽으로 매겨진 다음 위에서 아래로 매겨집니다.  
  
-   사용자가 명시적으로 삽입한 논리적 페이지 나누기가 보고서 항목에 적용됩니다. 이러한 페이지 나누기로 인해 특정 보고서 항목에 의해 다른 보고서 항목이 다음 페이지에서 시작할 수도 있습니다.  
  
-   한 페이지에 유지해야 하는 여러 보고서 항목에서 물리적 페이지 나누기가 발생하면 해당 항목 모두가 다음 페이지로 이동합니다.  
  
-   페이지 크기 제약 조건으로 인해 모든 항목을 한 페이지에 유지하지 못하거나 여러 항목을 반복하지 못할 수도 있습니다. 이러한 경우 렌더러에서는 다른 항목과 함께 반복하는 규칙을 무시하여 해당 보고서 항목이 페이지 크기에 맞도록 할 수도 있습니다.  
  
-   입력란이 너무 커져 사용 가능한 세로 페이지 영역을 벗어나는 경우처럼 특정 항목을 한 페이지에 함께 유지할 수 없는 경우에는 해당 항목이 물리적 페이지 경계에서 잘리고 다음 페이지에서 계속됩니다.  
  
-   페이지 매김은 세로 및 가로로 보고서에 적용됩니다.  
  
    > [!NOTE]  
    >  대화형 너비 설정은 하드 페이지 나누기 렌더러에서 사용되지 않습니다.  
  
## 보고서 항목 간의 최소 간격  
 보고서 항목은 해당 내용을 포함하기 위해 보고서 본문 내에서 크기가 늘어납니다. 예를 들어 행렬 데이터 영역은 일반적으로 보고서 렌더링 시 페이지에서 가로 및 아래쪽으로 확대되고, 입력란의 높이는 식에서 반환하는 데이터에 따라 조정됩니다.  
  
 렌더러에서는 사용자가 보고서 레이아웃에 정의한 보고서 항목 간의 최소 간격을 유지합니다. 보고서 레이아웃에서 특정 보고서 항목을 다른 보고서 항목 근처에 배치하는 경우 두 보고서 항목 간의 거리는 보고서가 가로 또는 세로 방향으로 확장될 때 유지해야 하는 최소 거리가 됩니다. 예를 들어 보고서에 행렬 데이터 영역을 추가한 다음 해당 행렬로부터 .25인치 오른쪽에 사각형을 추가하면 행렬이 확장될 때 행렬과 사각형 간의 간격이 .25인치로 유지됩니다. 각 항목은 오른쪽으로 이동하여 해당 항목과 그 왼쪽에 있는 항목 사이에 최소 거리를 유지합니다.  
  
## 페이지 머리글 및 바닥글  
 페이지 머리글 및 바닥글은 렌더링되는 각 페이지의 맨 위와 맨 아래에 나타납니다. 페이지 머리글 및 바닥글의 서식을 지정하여 테두리 색, 테두리 스타일 및 테두리 두께를 설정할 수 있습니다. 배경색 또는 배경 이미지를 추가할 수도 있습니다. 이러한 서식 옵션은 사용자가 선택한 서식에 따라 모두 렌더링됩니다.  
  
 HTML 또는 MHTML 렌더링 형식으로 렌더링되는 경우 페이지 머리글 및 바닥글에는 다음과 같은 규칙이 적용됩니다.  
  
> [!NOTE]  
>  Excel에서 머리글 및 바닥글을 렌더링하는 방법에 대한 자세한 내용은 [Microsoft Excel로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)를 참조하세요. Word에서 머리글 및 바닥글을 렌더링하는 방법에 대한 자세한 내용은 [Microsoft Word로 내보내기&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/exporting-to-microsoft-word-report-builder-and-ssrs.md)를 참조하세요.  
  
-   머리글 및 바닥글은 사용 가능한 페이지 영역 내의 모든 페이지에서 맨 위와 맨 아래에 렌더링되어 나타납니다.  
  
-   머리글 또는 바닥글이 숨겨져 있는 페이지의 경우 머리글 또는 바닥글이 렌더링되지는 않지만 사용 가능한 페이지 영역 내에서 머리글 또는 바닥글의 높이는 계속 예약되어 있습니다.  
  
-   머리글 또는 바닥글의 내용이 커져 머리글 또는 바닥글의 경계를 벗어나면 해당 내용을 포함할 수 있도록 머리글 또는 바닥글의 크기가 늘어납니다.  
  
 PDF 또는 이미지 렌더링 형식으로 렌더링되는 경우 페이지 머리글 및 바닥글에는 다음과 같은 규칙이 적용됩니다.  
  
-   머리글 또는 바닥글은 사용 가능한 페이지 영역 내의 모든 페이지에서 맨 위와 맨 아래에 렌더링됩니다.  
  
-   머리글 또는 바닥글이 숨겨져 있는 페이지의 경우 머리글 또는 바닥글이 렌더링되지는 않지만 사용 가능한 페이지 영역 내에서 머리글 또는 바닥글의 높이는 계속 예약되어 있습니다.  
  
-   머리글 및 바닥글의 크기가 늘어나거나 줄어들지 않습니다. 머리글 또는 바닥글은 모든 페이지에서 지정된 높이에 렌더링되며 이 높이는 사용자가 머리글 또는 바닥글을 만들 때 지정합니다.  
  
-   보고서 내에 있는 열의 수와 상관없이 페이지당 하나의 머리글과 바닥글만 있습니다.  
  
-   머리글 또는 바닥글의 내용이 커져 머리글 또는 바닥글의 경계를 벗어나는 경우 해당 내용이 잘립니다.  
  
-   하위 보고서로 보고서가 렌더링되는 경우 원본 .rdl 파일에 정의된 머리글 및 바닥글은 렌더링되지 않습니다.  
  
## 논리적 페이지 나누기  
 논리적 페이지 나누기는 보고서 항목 또는 그룹의 앞이나 뒤에 사용자가 삽입하는 페이지 나누기입니다. 페이지 나누기는 보고서를 렌더링하거나 내보낼 때 보고서를 최적의 상태로 보기 위해 보고서 내용을 보고서 페이지에 맞추는 방식을 결정하는 데 도움이 됩니다.  
  
 논리적 페이지 나누기를 렌더링하는 경우 다음과 같은 규칙이 적용됩니다.  
  
-   항상 숨겨져 있는 보고서 항목 및 다른 보고서 항목을 클릭하여 표시 유형이 제어되는 보고서 항목에 대해서는 논리적 페이지 나누기가 무시됩니다.  
  
-   조건부로 표시되는 항목을 보고서 렌더링 시점에서 볼 수 있는 경우 해당 항목에 논리적 페이지 나누기가 적용됩니다.  
  
-   논리적 페이지 나누기가 적용되는 보고서 항목과 피어 보고서 항목 간의 간격은 그대로 유지됩니다.  
  
-   보고서 항목 앞에 논리적 페이지 나누기를 삽입하면 해당 보고서 항목이 다음 페이지에서 시작됩니다. 해당 보고서 항목은 다음 페이지의 맨 위에 렌더링됩니다.  
  
-   테이블 또는 행렬 셀의 항목에 대해 정의한 논리적 페이지 나누기는 유지되지 않습니다. 목록의 항목은 이 규칙에서 예외입니다.  
  
## 관련 항목:  
 [여러 보고서 렌더링 확장 프로그램의 대화형 기능&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/interactive functionality - different report rendering extensions.md)   
 [HTML로 렌더링&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-builder/rendering-to-html-report-builder-and-ssrs.md)   
 [페이지 레이아웃 및 렌더링&#40;보고서 작성기 및 SSRS&#41;](../../reporting-services/report-design/page-layout-and-rendering-report-builder-and-ssrs.md)  
  
  