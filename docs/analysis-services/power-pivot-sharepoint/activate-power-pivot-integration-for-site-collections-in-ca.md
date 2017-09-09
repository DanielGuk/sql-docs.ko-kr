---
title: "CA에서 사이트 모음에 대 한 파워 피벗 통합 활성화 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62a27e53-446a-42d7-b5db-c009e02d4904
caps.latest.revision: 8
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: e4c3c7403a6fefb42c15f8b4ba71af403195a057
ms.contentlocale: ko-kr
ms.lasthandoff: 09/01/2017

---
# <a name="activate-power-pivot-integration-for-site-collections-in-ca"></a>CA에서 사이트 모음에 대 한 파워 피벗 통합 활성화
  기존 팜 설치 옵션을 사용하여 SQL Server SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 설치하는 경우 특정 사이트 모음에 대해 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 기능 통합을 활성화해야 합니다. 새 서버 옵션을 사용해 SharePoint용 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 을 설치한 경우에는 SQL Server 설치 프로그램에서 배포를 구성할 때 루트 사이트 모음에 대해 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 기능 통합을 이미 활성화했기 때문에 이 태스크를 건너뛰어도 됩니다.  
  
 예약된 데이터 새로 고침용 구성 페이지, [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 갤러리 및 데이터 피드 라이브러리용 응용 프로그램 페이지 등의 응용 프로그램 페이지와 템플릿을 사이트에서 사용하려면 사이트 모음 수준에서 기능을 활성화해야 합니다.  
  
 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 쿼리 처리를 지원하는 각 사이트 모음에 대해 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합을 활성화해야 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
 사이트 모음 관리자여야 합니다.  
  
## <a name="activate-power-pivot-features"></a>파워 피벗 기능 활성화  
  
1.  SharePoint  사이트에서 **사이트 작업**을 클릭합니다.  
  
     기본적으로 SharePoint 웹 응용 프로그램은 포트 80을 통해 액세스됩니다. 즉, http://를 입력 하 여 SharePoint 사이트를 액세스할 종종 수\<컴퓨터 이름 > 루트 사이트 모음을 열려면 합니다.  
  
2.  **사이트 설정**을 클릭합니다.  
  
3.  사이트 컬렉션 관리에서 **사이트 컬렉션 기능**을 클릭합니다.  
  
4.  페이지 아래쪽으로 스크롤하여 **[!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 사이트 모음 기능**을 찾습니다.  
  
5.  **활성화**를 클릭합니다.  
  
6.  각 사이트를 열고 **사이트 작업**을 클릭하여 추가 사이트 모음에 대해 위 단계를 반복합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [중앙 관리에서 파워 피벗 서버 관리 및 구성](../../analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration.md)   
 [초기 구성 (SharePoint 용 파워 피벗)](http://msdn.microsoft.com/en-us/3a0ec2eb-017a-40db-b8d4-8aa8f4cdc146)   
 [SharePoint 2010용 파워 피벗 설치](http://msdn.microsoft.com/en-us/8d47dde7-c941-4280-a934-e2fe3f9a938f)  
  
  