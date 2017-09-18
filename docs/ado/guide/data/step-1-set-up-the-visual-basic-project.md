---
title: "1 단계: Visual Basic 프로젝트 설정 | Microsoft Docs"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 77d3bfa5-fc9f-4a72-93b4-790c7d227988
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7b27969d78328118f98911c68eb555357bc3118
ms.contentlocale: ko-kr
ms.lasthandoff: 09/09/2017

---
# <a name="step-1-set-up-the-visual-basic-project"></a>1 단계: Visual Basic 프로젝트 설정
이 시나리오에서는 Microsoft Visual Basic 6.0, 2.5 이상의 ADO 및 Microsoft OLE DB Provider for Internet Publishing 시스템에 설치 되어 있는 가정 합니다. 먼저 새 프로젝트를 만들고 일부 컨트롤은 프로젝트의 기본 폼을 추가 합니다.  
  
### <a name="to-create-an-ado-project"></a>ADO 프로젝트를 만들려면  
  
1.  Microsoft Visual Basic에서는 새 표준 EXE 프로젝트를 만듭니다.  
  
2.  프로젝트 메뉴에서 참조를 선택 합니다.  
  
3.  "Microsoft ActiveX 데이터 개체 2.5 라이브러리"를 선택 하 고 확인을 클릭 합니다.  
  
### <a name="to-insert-controls-on-the-main-form"></a>기본 폼에 컨트롤을 삽입 합니다.  
  
1.  ListBox 컨트롤 Form1을 추가 합니다. 해당 이름 속성을 설정 **lstMain**합니다.  
  
2.  Form1에 다른 ListBox 컨트롤을 추가 합니다. 해당 이름 속성을 설정 **lstDetails**합니다.  
  
3.  Form1에 TextBox 컨트롤을 추가 합니다. 해당 이름 속성을 설정 **txtDetails**합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [인터넷 게시 시나리오](../../../ado/guide/data/internet-publishing-scenario.md)   
 [2단계: 기본 목록 상자 초기화](../../../ado/guide/data/step-2-initialize-the-main-list-box.md)