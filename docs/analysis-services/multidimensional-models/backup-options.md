---
title: 백업 옵션 | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 62f5bf26f80ea1018a5a3330efa0f055021ff0f5
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145444"
---
# <a name="backup-options"></a>백업 옵션
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스는 여러 가지 방법으로 백업할 수 있지만 백업하기 위해서는 서버 관리자 권한과 데이터베이스 관리자 권한이 필요합니다. **에서** 백업 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]대화 상자를 열고 적절한 옵션 구성을 선택한 후 백업을 실행할 수 있습니다. 또는 파일에 이미 지정된 설정을 사용하는 스크립트를 만들어 저장하고 필요할 때마다 스크립트를 실행할 수 있습니다.  
  
## <a name="backup-and-synchronize"></a>백업 및 동기화  
 데이터베이스가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]원격 인스턴스에 있는 경우 동기화 기능을 사용하여 데이터베이스를 로컬 인스턴스로 백업할 수 있습니다. 이 방법으로 데이터베이스의 개발 빌드를 프로덕션으로 이동할 수 있습니다. 기존의 파일 기반 백업과 복원을 사용하여 개발 빌드를 프로덕션으로 이동할 수도 있으나 동기화를 사용하면 추가 기능을 이용할 수 있습니다. 예를 들어 개발 컴퓨터와 프로덕션 컴퓨터의 보안 설정이 다른 경우 동기화를 사용하면 해당 설정을 유지하고 역할을 제외한 모든 개체를 동기화할 수 있습니다. 또한 동기화는 일반적으로 원본 컴퓨터와 대상 컴퓨터에서 다른 개체에 대해 증분 업데이트를 수행합니다. 백업/복원 기능으로는 이러한 증분 백업을 사용할 수 없습니다. 자세한 내용은 [Synchronize Analysis Services Databases](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)을(를) 참조하세요.  
  
> [!IMPORTANT]  
>  Analysis Services 서비스 계정에는 각 파일에 대해 지정한 백업 위치에 쓸 수 있는 권한이 있어야 합니다. 또한 사용자는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에 대한 관리자 역할이나 백업할 데이터베이스에 대한 모든 권한(관리자 권한)이 있는 데이터베이스 역할의 멤버를 가지고 있어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [데이터베이스 백업 대화 상자&#40;Analysis Services - 다차원 데이터&#41;](http://msdn.microsoft.com/library/7811ce7d-6c37-4189-bfa6-ef36fb4932db)   
 [Analysis Services 데이터베이스 백업 및 복원](../../analysis-services/multidimensional-models/backup-and-restore-of-analysis-services-databases.md)   
 [Backup 요소&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/backup-element-xmla)   
 [데이터베이스 백업, 복원 및 동기화&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/backing-up-restoring-and-synchronizing-databases-xmla.md)  
  
  
