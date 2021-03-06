---
title: 폴더 만들기, 삭제 또는 수정(보고서 관리자) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing folders
- modifying folders
- deleting folders
- folders [Reporting Services], creating
- folders [Reporting Services], deleting
- folders [Reporting Services], modifying
ms.assetid: d62159a8-ec67-4e28-a9f1-05a9250065bb
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 89b1476adadf6b409d68dbf524a9352d6b7cb6ab
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48129343"
---
# <a name="create-delete-or-modify-a-folder-report-manager"></a>폴더 만들기, 삭제 또는 수정(보고서 관리자)
  폴더를 만들어 보고서 서버에 게시하는 항목을 구성하고 관리할 수 있습니다. 폴더를 만들면 관심 있는 보고서를 찾는 데 도움이 될 수 있습니다. 내용 관리자의 경우 폴더는 사용 권한을 적용하는 프레임워크를 제공합니다. 개발 중인 보고서나 배포되면 안 되는 보고서에 대한 액세스를 제한하기 위해 특정 폴더에 역할 할당을 만들 수 있습니다.  
  
### <a name="to-create-a-folder"></a>폴더를 만들려면  
  
1.  [보고서 관리자&#40;SSRS 기본 모드&#41;](../report-manager-ssrs-native-mode.md)를 시작합니다.  
  
2.  보고서 관리자에서 홈 폴더를 선택하고 **새 폴더**를 클릭합니다. 또는 기존 폴더 아래에 폴더를 만들려면 **내용** 페이지에서 해당 폴더로 이동한 후 폴더를 클릭하여 엽니다. 그런 후 **새 폴더**를 클릭합니다.  
  
     **새 폴더** 페이지가 열립니다.  
  
3.  폴더 이름을 입력합니다. 폴더 이름에 공백을 사용할 수 있지만 다음과 같은 URL 인코딩용으로 예약된 문자는 사용할 수 없습니다. ; ? : \@ & = +, $ / * \< > |. 한 번에 여러 개의 폴더 이름을 입력하여 여러 폴더를 만들 수는 없습니다.  
  
4.  설명을 입력합니다(옵션).  
  
5.  **내용** 페이지의 기본 보기에서 폴더를 표시하지 않으려면 **목록 뷰에서 숨기기** 를 선택합니다. **내용** 페이지에서 **자세한 정보 표시** 를 클릭하면 숨겨진 폴더가 표시됩니다.  
  
6.  **확인**을 클릭합니다.  
  
### <a name="to-delete-a-folder"></a>폴더를 삭제하려면  
  
1.  보고서 관리자에서 **내용** 페이지로 이동한 다음 수정할 항목을 찾습니다.  
  
2.  항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.  
  
3.  드롭다운 메뉴에서 **삭제**를 클릭합니다.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-modify-or-delete-a-folder"></a>폴더를 수정하거나 삭제하려면  
  
1.  보고서 관리자에서 **내용** 페이지로 이동한 다음 수정할 항목을 찾습니다.  
  
2.  항목 위로 마우스를 이동하여 드롭다운 화살표를 클릭합니다.  
  
3.  드롭다운 메뉴에서 **관리**를 클릭합니다. 일반 속성 페이지가 열립니다.  
  
4.  폴더 위치를 변경하려면 **이동**을 클릭합니다. 대상 폴더의 위치를 입력하거나 트리에서 대상 폴더를 선택한 후 **확인**을 클릭합니다.  
  
5.  또는 다음과 같은 방법으로 폴더 속성을 수정합니다.  
  
    -   폴더에 대한 표시 텍스트를 수정하려면 이름이나 설명을 입력합니다.  
  
    -   **내용** 페이지에서 폴더를 기본 보기로 표시하려면 **목록 뷰에서 숨기기**의 선택을 취소합니다.  
  
6.  또는 폴더 및 해당 내용을 제거하려면 **삭제**를 클릭합니다.  
  
7.  **적용** 을 클릭하여 변경 내용을 저장합니다.  
  
## <a name="see-also"></a>관련 항목  
 [새 폴더 페이지 &#40;보고서 관리자&#41;](../new-folder-page-report-manager.md)   
 [페이지 콘텐츠를 &#40;보고서 관리자&#41;](../contents-page-report-manager.md)   
 [보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
