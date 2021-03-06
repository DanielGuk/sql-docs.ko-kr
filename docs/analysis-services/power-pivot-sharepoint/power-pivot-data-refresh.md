---
title: Power Pivot 데이터 새로 고침 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ppvt-sharepoint
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 2647d94f0f1d8edc1d5c6ef9b364167f330e30a2
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981445"
---
# <a name="power-pivot-data-refresh"></a>Power Pivot 데이터 새로 고침
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터가 포함된 통합 문서를 만든 후 통합 문서를 만들기 위해 원래 사용했던 원본의 업데이트된 정보를 가져오기 위해 쿼리나 명령을 다시 실행하여 정기적으로 데이터를 새로 고칠 수 있습니다. 이 프로세스를 **데이터 새로 고침**이라고 하며, [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]에서 요청 시 또는 SharePoint 팜의 애플리케이션 서버에서 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 프로세스로 실행되는 예약된 작업으로 데이터를 새로 고칠 수 있습니다. 참조 항목:  
  
-   [SharePoint 2010을 사용 하 여 파워 피벗 데이터 새로 고침](http://msdn.microsoft.com/01b54e6f-66e5-485c-acaa-3f9aa53119c9)  
  
-   [파워 피벗 구성 무인된 데이터 새로 고침 계정 (SharePoint 용 파워 피벗)](http://msdn.microsoft.com/81401eac-c619-4fad-ad3e-599e7a6f8493)  
  
-   [Power Pivot 데이터 새로 고침 (SharePoint 용 파워 피벗)에 대 한 저장 된 자격 증명 구성](http://msdn.microsoft.com/987eff0f-bcfe-4bbd-81e0-9aca993a2a75)  
  
-   [일정 데이터 새로 고침 (SharePoint 용 파워 피벗)](http://msdn.microsoft.com/8571208f-6aae-4058-83c6-9f916f5e2f9b)  
  
-   [데이터 새로 고침 기록 보기&#40;SharePoint용 파워 피벗&#41;](../../analysis-services/power-pivot-sharepoint/view-data-refresh-history-power-pivot-for-sharepoint.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] SharePoint Server 2013 Excel Services 데이터 새로 고침에 다른 아키텍처를 사용 하 고 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 모델입니다. SharePoint 2013 지원 아키텍처는 Excel Services를 기본 구성 요소로 사용하여 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 데이터 모델을 로드합니다. 이전에 사용한 데이터 새로 고침 아키텍처는 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스와 SharePoint 모드의 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 를 사용하여 데이터 모델을 로드했습니다. 자세한 내용은 다음 항목을 참조하세요.  
>   
>  -   [SharePoint 2013에서 파워 피벗 데이터 새로 고침](../../analysis-services/power-pivot-sharepoint/power-pivot-data-refresh-with-sharepoint-2013.md)  
> -   [통합 문서 업그레이드 및 예약된 데이터 새로 고침&#40;SharePoint 2013&#41;](../../analysis-services/instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)  
  
  
