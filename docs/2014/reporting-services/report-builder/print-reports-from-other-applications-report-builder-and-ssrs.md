---
title: 다른 애플리케이션에서 보고서 인쇄(보고서 작성기 및 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: a5560581-fd57-4a45-b7ea-43b21a8a7419
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: b68fdf49527e83965a5c1a5c41ab185bdba0c463
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48185893"
---
# <a name="print-reports-from-other-applications-report-builder-and-ssrs"></a>다른 애플리케이션에서 보고서 인쇄(보고서 작성기 및 SSRS)
  보고서 작성기는 다른 애플리케이션에서 보고서를 쉽게 볼 수 있도록 내보내기 옵션을 제공합니다. `Export` 브라우저 또는 웹 기반 응용 프로그램에서 열면 보고서 위쪽에 표시 되는 보고서 도구 모음에서 사용할 수 있는 명령입니다. 보고서를 내보내면 다른 애플리케이션에서 보고서가 표시됩니다. 예를 들어 보고서를 Excel로 내보내면 해당 보고서가 [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]에서 열립니다. 애플리케이션에 사용하려는 특정 인쇄 기능이 있는 경우에만 인쇄 목적으로 보고서를 내보내는 것이 좋습니다.  
  
 다른 애플리케이션으로 보고서를 내보내려면 해당 애플리케이션이 설치되어 있어야 합니다. 예를 들어 Acrobat(PDF) 형식으로 보고서를 내보내려면 컴퓨터에 Adobe Acrobat Reader가 설치되어 있어야 합니다. TIFF 형식으로 보고서를 내보내도록 선택하면 TIFF 파일 형식에 연결된 보기 애플리케이션에서 보고서가 열립니다. 사용되는 애플리케이션은 설치되어 있는 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 버전에 따라 다르지만 일반적으로 Windows 사진 및 팩스 뷰어가 사용됩니다. 기본 해상도는 96DPI의 화면 해상도에 해당합니다. 프린터의 기능에 맞도록 Windows 사진 및 팩스 뷰어에서 해상도를 300DPI나 600DPI로 높일 수 있습니다. 해상도를 조정하는 방법은 Windows 제품 설명서를 참조하십시오.  
  
 MHTML이라고도 하는 웹 보관 파일을 선택하면 보고서가 기본 브라우저로 내보내집니다. 브라우저에서 인쇄하면 모든 페이지의 아래쪽에 보고서 경로 정보가 추가될 수 있습니다. 대부분의 경우 브라우저 옵션에서 경로 정보가 인쇄되지 않도록 설정할 수 있습니다. 자세한 내용은 사용하는 브라우저의 제품 설명서를 참조하십시오.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;](print-a-report-report-builder-and-ssrs.md)   
 [인쇄 컨트롤을 사용하여 브라우저에서 보고서 인쇄&#40;보고서 작성기 및 SSRS&#41;](print-reports-from-a-browser-with-the-print-control-report-builder-and-ssrs.md)   
 [보고서를 내보내는 &#40;보고서 작성기 및 SSRS&#41;](export-reports-report-builder-and-ssrs.md)   
 [다른 파일 형식으로 보고서 내보내기&#40;보고서 작성기 및 SSRS&#41;](../export-a-report-as-another-file-type-report-builder-and-ssrs.md)   
 [보고서 찾기, 보기 및 관리&#40;보고서 작성기 및 SSRS&#41;](finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  
