---
title: 비율 샘플링 변환 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.percentagesamplingtransformation.f1
helpviewer_keywords:
- Percentage Sampling Transformation Editor
ms.assetid: 2c40d804-26a3-4d35-809b-bc923d83d451
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 14776d4f26d324b60619aef2bfa3fad9c0deadaf
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48183623"
---
# <a name="percentage-sampling-transformation-editor"></a>비율 샘플링 변환 편집기
  **비율 샘플링 변환 편집기** 대화 상자에서 지정한 행의 백분율을 사용하여 입력 부분을 샘플로 분할할 수 있습니다. 이 변환으로 인해 입력이 두 개의 별도 출력으로 나뉩니다.  
  
 비율 샘플링 변환에 대한 자세한 내용은 [Percentage Sampling Transformation](data-flow/transformations/percentage-sampling-transformation.md)을 참조하십시오.  
  
## <a name="options"></a>변수  
 **행의 백분율**  
 입력에서 샘플로 사용할 행의 백분율을 지정합니다.  
  
 이 속성의 값은 속성 식을 사용하여 지정할 수 있습니다.  
  
 **샘플 출력 이름**  
 샘플링한 행이 포함될 출력에 사용할 고유 이름을 제공합니다. 제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.  
  
 **선택하지 않은 출력 이름**  
 샘플링에서 제외된 행이 포함될 출력에 사용할 고유 이름을 제공합니다. 제공한 이름은 [!INCLUDE[ssIS](../includes/ssis-md.md)] 디자이너에 표시됩니다.  
  
 **다음과 같은 임의 초기값 사용**  
 변환에서 샘플을 만드는 데 사용하는 난수 생성기에 샘플링 초기값을 지정합니다. 이 옵션은 개발 및 테스트 용도로만 사용하는 것이 좋습니다. 임의 초기값을 지정하지 않으면 Microsoft Windows 틱 수가 사용됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [행 샘플링 변환](data-flow/transformations/row-sampling-transformation.md)  
  
  
