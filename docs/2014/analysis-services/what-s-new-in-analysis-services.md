---
title: 새로운&#39;Analysis Services 및 Business Intelligence 기능 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
ms.assetid: aa69c299-b8f4-4969-86d8-b3292fe13f08
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a6b59ae2bd1c9d21704d87289b604feefa326f1e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48054343"
---
# <a name="what39s-new-in-analysis-services-and-business-intelligence"></a>새로운&#39;Analysis Services 및 Business Intelligence 기능
  다차원 모델에 대 한 Power View 보고서를 지 원하는 추가 기능에 대 한 예외를 사용 하 여 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 이전 릴리스에서 변경 되지 않습니다.  
  
 다른 방법은 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 제품 및이 릴리스에서 다른 기술 참조 [What's New in SQL Server 2014](../sql-server/what-s-new-in-sql-server-2016.md)합니다.  
  
## <a name="updates-to-design-tool-installation"></a>디자인 도구 설치에 대한 업데이트  
 이전에는 BIDS(Business Intelligence Development Studio)라고 하던 SSDT-BI([!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] for Business Intelligence)는 Analysis Services 모델, Reporting Services 보고서 및 Integration Services 패키지를 만드는 데 사용됩니다. 다음 위치에서 SSDT-BI를 다운로드할 수 있습니다.  
  
-   [Visual Studio 2013 용 SSDT-BI 다운로드](http://go.microsoft.com/fwlink/p/?LinkId=396526)  
  
-   [Visual Studio 2012 용 SSDT-BI 다운로드](http://go.microsoft.com/fwlink/p/?LinkID=273673)  
  
 이전 버전의 SSDT-BI 또는 BIDS가 컴퓨터에 설치되어 있는 경우 최신 버전이 이전 버전과 함께 설치됩니다. 특정 버전의 서버에 연결된 프로젝트 및 솔루션을 수정할 수 있도록 하기 위해 최신 및 이전 버전의 디자인 도구를 단일 워크스테이션에서 실행하는 것이 일반적입니다.  
  
> [!NOTE]  
>  Visual Studio 2012 및 Visual Studio 2013 버전의 SSDT를 다운로드할 수 있는 몇몇 사이트가 있습니다. 대부분의 다운로드에는 BI 프로젝트 템플릿이 포함되어 있지 않습니다. 위의 링크를 사용하면 올바른 버전을 얻을 수 있습니다. 비즈니스 인텔리전스 프로젝트 템플릿 폴더가 표시되는 경우 올바른 버전의 SSDT-BI가 설치되어 있는 것입니다. 이 폴더에는 Analysis Services, Reporting Services 및 Integration Services의 프로젝트 템플릿이 포함되어 있습니다. SSDT-BI를 설치한 방법에 따라 SQL Server 데이터베이스의 추가 프로젝트 템플릿이 표시될 수도 있습니다.  
  
 ![SSDT의 새 프로젝트 템플릿](media/ssdt-biprojects.png "SSDT의 새 프로젝트 템플릿")  
  
## <a name="features-recently-added-power-view-for-multidimensional-models"></a>최근에 추가된 기능: 다차원 모델에 대한 Power View  
 다차원 모델에 대한 Power View 보고서를 만드는 기능은 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 서비스 팩 1 누적 업데이트 4에서 처음 도입되었습니다. 다차원 모델용 Power View 기능은 이제 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]의 일부로 포함되어 있습니다.  
  
 **다차원 모델용 power View 보고서**  
  
 ![Power View 보고서](media/powerviewreport-wn.gif "Power View 보고서")  
  
 이 기능은 조직에서 다차원 모델(OLAP 큐브라고도 함)을 최신 클라이언트 보고 도구와 함께 사용할 수 있도록 하여 기존 BI 투자를 최대화하는 데 도움이 됩니다. 다차원 모델의 데이터 형식에 따라 테이블 및 행렬에서 거품형 차트 및 지도에 이르는 다양한 동적 시각화를 쉽게 만들 수 있습니다. 다차원 모델은 이제 DAX(Data Analysis Expressions)를 사용하는 쿼리도 지원합니다.  
  
 다차원 모델용 power View에서 기본 제공 Power View 보고 기능이 필요 [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] (SharePoint 모드에서). 다른 버전의 Power View(특히 Excel 2013의 Power View 추가 기능)는 다차원 모델을 지원하지 않습니다.  
  
 자세한 내용은 [다차원 모델용 Power View](http://msdn.microsoft.com/library/dn140246.aspx)를 참조하십시오.  
  
  
