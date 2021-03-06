---
title: Integration Services 서버의 패키지 목록 보기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: 67a992d1-7524-4f4b-b3d8-ebd9e5ea82a8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 9ccb817e44acce8a8854894230b6ae62ecd21dd3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48069803"
---
# <a name="view-the-list-of-packages-on-the-integration-services-server"></a>Integration Services 서버의 패키지 목록 보기
  다음 두 가지 방법 중 하나를 사용하여 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 저장된 패키지 목록을 볼 수 있습니다.  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] 액세스  
 서버에 저장된 패키지 목록을 보려면 [catalog.packages&#40;SSISDB 데이터베이스&#41;](/sql/integration-services/system-views/catalog-packages-ssisdb-database) 뷰를 쿼리합니다.  
  
 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]를 사용하는 경우 다음을 수행합니다.  
 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 개체 탐색기를 사용하여 서버에 저장된 패키지를 보려면 아래 절차를 따릅니다.  
  
### <a name="to-view-packages-using-includessmanstudiofullincludesssmanstudiofull-mdmd"></a>사용 하 여 패키지를 보려면 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]  
  
1.  [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]에서 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 서버에 연결합니다. 즉, [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 데이터베이스를 호스팅하는 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 인스턴스에 연결합니다.  
  
2.  개체 탐색기에서 트리를 확장하여 **Integration Services 카탈로그** 노드를 표시합니다.  
  
3.  **Integration Services 카탈로그** 노드를 확장하여 **SSISDB** 노드를 표시합니다.  
  
4.  **SSISDB** 노드를 확장하여 하나 이상의 폴더 목록을 표시합니다. 각 폴더에는 **프로젝트** 폴더에 있는 하나 이상의 프로젝트가 포함되며 각 프로젝트에는 **패키지** 폴더의 패키지가 하나 이상 포함됩니다.  
  
  
