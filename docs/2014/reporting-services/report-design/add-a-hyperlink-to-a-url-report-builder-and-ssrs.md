---
title: URL에 하이퍼링크 추가(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b29f10762f421c76dd7adbbd341038771f135a04
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086623"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a>URL에 하이퍼링크 추가(보고서 작성기 및 SSRS)
  사용자가 보고서의 링크를 클릭하여 지정 URL에 대한 브라우저를 열 수 있게 하기 위해 보고서 항목에 하이퍼링크를 추가할 수 있습니다. 하이퍼링크는 정적 URL 및 URL을 반환하는 식이 될 수 있습니다. URL을 포함하는 데이터베이스에 필드가 있는 경우 식에 해당 필드가 포함될 수 있으므로 보고서에 하이퍼링크의 동적 목록이 생깁니다. 입력란, 이미지, 차트 및 계기에 하이퍼링크를 추가할 수 있습니다. 이때 사용자가 제공 URL에 액세스할 수 있는 권한이 있는지 확인해야 합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 보고서 서버에 대한 URL 요청을 사용하여 본인과 사용자에게 볼 수 있는 권한이 있는 보고서 서버의 보고서에 대해 URL을 지정할 수도 있습니다. 예를 들어 보고서를 지정한 다음 사용자가 처음으로 해당 보고서를 볼 때 문서 구조를 숨길 수 있습니다. 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 [Reporting Services 설명서](http://go.microsoft.com/fwlink/?linkid=121312)에서 [URL 액세스&#40;SSRS&#41;](../url-access-ssrs.md)를 참조하세요.  
  
 입력란, 이미지 또는 차트의 계산된 계열과 같이 **동작** 속성이 있는 모든 항목의 URL에 하이퍼링크를 추가할 수 있습니다. 정의한 동작은 사용자가 해당 보고서 항목을 클릭할 때 발생합니다. 자세한 내용은 [동작 속성 대화 상자&#40;보고서 작성기 및 SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) 및 [외부 항목에 대한 경로 지정&#40;보고서 작성기 및 SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)을 참조하세요.  
  
 빠르게 시작하려면 [자습서: 텍스트 서식 지정&#40;보고서 작성기&#41;](../tutorial-format-text-report-builder.md)을 참조하세요.  
  
> [!NOTE]  
>  데이터 집합 필드에 바인딩된 링크는 악의적 의도를 가진 사용자가 임의로 변경할 수도 있습니다. 자세한 내용은 msdn.microsoft.com의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][온라인 설명서](http://go.microsoft.com/fwlink/?LinkId=154888)에서 [보고서 및 리소스 보안](../security/secure-reports-and-resources.md)을 참조하세요.  
  
### <a name="to-add-a-hyperlink"></a>하이퍼링크를 추가하려면  
  
1.  보고서 디자인 뷰에서 링크를 추가하려는 입력란, 이미지 또는 차트를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2.  속성 대화 상자에서 **동작**을 클릭합니다.  
  
3.  **URL로 이동**을 선택합니다. 이 옵션에 대한 추가 섹션이 대화 상자에 나타납니다.  
  
4.  **URL 선택**에서 URL이나 URL로 계산되는 식을 입력 또는 선택하거나, 드롭다운 화살표를 클릭하고 URL이 들어 있는 필드 이름을 클릭합니다.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  (선택 사항) 텍스트가 자동으로 링크로 서식이 지정되지는 않습니다. 텍스트의 경우 텍스트가 링크임을 나타내기 위해 텍스트 색과 효과를 변경하는 것이 좋습니다. 예를 들어 리본 메뉴의 홈 탭에 있는 **글꼴** 섹션에서 색을 파란색으로 변경하고 효과를 밑줄로 변경합니다.  
  
7.  링크를 테스트하려면 **실행** 을 클릭하여 보고서를 미리 본 다음, 이 링크를 설정한 보고서 항목을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [대화형 정렬, 문서 구조 및 링크&#40;보고서 작성기 및 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md)   
 [문서 구조 만들기&#40;보고서 작성기 및 SSRS&#41;](create-a-document-map-report-builder-and-ssrs.md)  
  
  
