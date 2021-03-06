---
title: 선행 제약 조건 편집기 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: c321d7a3850cf91b996262265492b88a6773f446
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48217303"
---
# <a name="precedence-constraint-editor"></a>선행 제약 조건 편집기
  **선행 제약 조건 편집기** 대화 상자를 사용하여 선행 제약 조건을 구성할 수 있습니다.  
  
## <a name="options"></a>변수  
 **평가 작업**  
 선행 제약 조건에서 사용하는 평가 작업을 지정합니다. 작업에는 **제약 조건**, **식**, **식 및 제약 조건**, **식 또는 제약 조건**이 있습니다.  
  
 **Value**  
 제약 조건 값을 **성공**, **실패**또는 **완료**로 지정합니다.  
  
> [!NOTE]  
>  선행 제약 조건 줄은 **성공**인 경우 녹색으로 표시되고 **실패**인 경우 강조 표시되고 **완료**인 경우 파란색으로 표시됩니다.  
  
 **식**  
 **식**, **식 및 제약 조건**또는 **식 또는 제약 조건**작업을 사용하는 경우 식을 입력하거나 식 작성기를 실행하여 식을 만듭니다. 식은 부울로 계산되어야 합니다.  
  
 **테스트**  
 식의 유효성을 검사합니다.  
  
 **논리적 AND**  
 동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다. 모든 제약 조건으로 계산 되어야 `True`합니다.  
  
> [!NOTE]  
>  이 유형의 선행 제약 조건은 녹색 실선으로 표시되거나 강조 표시되거나 파란색 실선으로 표시됩니다.  
  
 **논리적 OR**  
 동일한 실행 파일의 여러 선행 제약 조건을 함께 평가하도록 지정하려면 선택합니다. 하나 이상의 제약 조건으로 계산 되어야 `True`합니다.  
  
> [!NOTE]  
>  이 유형의 선행 제약 조건은 녹색 점선으로 표시되거나 강조 표시되거나 파란색 점선으로 표시됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [선행 제약 조건](control-flow/precedence-constraints.md)   
 [Integration Services 태스크](control-flow/integration-services-tasks.md)   
 [Integration Services 컨테이너](control-flow/integration-services-containers.md)   
 [Integration Services&#40;SSIS&#41; 식](expressions/integration-services-ssis-expressions.md)  
  
  
