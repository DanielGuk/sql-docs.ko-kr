---
title: VSTA로 스크립트 마이그레이션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- SSIS Script task, converting scripts
- Script component [Integration Services], converting scripts
- Script task [Integration Services], converting scripts
- SSIS Script component, converting scripts
ms.assetid: d685098b-86a1-46bf-939a-63d56951e009
author: mashamsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: b23d85aa038acae6631dedf64417c65e745baf90
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084437"
---
# <a name="migrate-scripts-to-vsta"></a>VSTA로 스크립트 마이그레이션
  업그레이드 하는 경우 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 패키지를 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 모든 스크립트 태스크 또는 스크립트 구성 요소를로 마이그레이션합니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA). VSTA는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 사용하는 스크립팅 환경입니다. [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]를 위한 스크립팅 환경인 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 됩니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 응용 프로그램 (VSA).  
  
 스크립트 태스크나 스크립트 구성 요소의 스크립트에서 인터페이스를 참조하는 경우에는 패키지를 업그레이드하기 전에 해당 참조를 수정해야 합니다. 그렇지 않으면 사용하는 업그레이드 방법에 따라 패키지 업그레이드가 실패하거나 스크립트의 유효성 검사가 실패하게 됩니다. 이러한 참조를 수정 하려면 IDTS에 대 한 참조를 바꿀*xxx*해당 하는 IDTS에 대 한 참조를 사용 하 여 90 인터페이스*xxx*100 인터페이스입니다.  
  
 스크립트를 마이그레이션하고 패키지를 업그레이드 하는 방법에 대 한 자세한 내용은 참조 하세요. [Integration Services 패키지 업그레이드](../../integration-services/install-windows/upgrade-integration-services-packages.md)합니다.  
  
## <a name="understanding-migration-failures"></a>마이그레이션 오류 이해  
 스크립트를 마이그레이션할 때 다음과 같은 이유로 마이그레이션이 실패할 수 있습니다.  
  
-   VSA 스크립트의 진입점 이름이 바뀐 경우  
  
     진입점은 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 런타임이 VSTA 프로젝트의 `ScriptMain` 클래스에서 스크립트 태스크 코드에 대한 진입점으로 호출하는 메서드를 지정합니다. `ScriptMain` 클래스는 스크립트 템플릿이 생성하는 기본 클래스입니다.  
  
-   VSA 스크립트에 진입점이 없거나 여러 개 있는 경우  
  
-   어셈블리 참조를 추가할 수 없는 경우  
  
-   `ScriptMain` 클래스는 `ScriptObjectModelSSIS` 클래스뿐만 아니라 다른 클래스에서도 상속되도록 수정되었습니다. [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 다중 상속을 지원 하지 않습니다.  
  
 사용 하는 VSA 스크립트를 변환할 수 없습니다 [!INCLUDE[vbprvblong](../../includes/vbprvblong-md.md)] 를 사용 하는 VSTA 스크립트로 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]합니다. 그러나 사용 하는 새 VSTA 스크립트를 만들 수 있습니다 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[csharp_orcas_long](../../includes/csharp-orcas-long-md.md)]합니다. 자세한 내용은은 [스크립트 태스크 코딩 및 디버깅](../../integration-services/control-flow/script-task.md) 및 [스크립트 구성 요소 코딩 및 디버깅](../../integration-services/data-flow/transformations/script-component.md)을 참조하십시오.  
  
## <a name="see-also"></a>관련 항목  
 [스크립팅을 사용한 패키지 확장](../../relational-databases/server-management-objects-smo/tasks/scripting.md)  
  
  
