---
title: 평가 보고서 (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 168b7465-a6d6-4329-b46e-fc6c5a3f2d9d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: dd578c40c71b8be4a0567cc2cc1a516f795e288d
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47600166"
---
# <a name="assessment-report-oracletosql"></a>평가 보고서(OracleToSQL)
평가 보고서 창에 데이터베이스 개체의 변환 결과 보여 줍니다. [!INCLUDE[tsql](../../includes/tsql-md.md)] 구문을 마이그레이션 프로젝트의 비용과 복잡성을 예측할 수 있습니다.  
  
원본 메타 데이터 탐색기에서 변환할 개체를 선택할 평가 보고서에 액세스 하려면 마우스 오른쪽 단추로 클릭 **스키마** 하거나 **동의어**를 선택한 후 **보고서 만들기**합니다.  
  
## <a name="options"></a>변수  
  
|||  
|-|-|  
|용어|정의|  
|**변환 통계**|문 형식으로 변환 통계가 표시 됩니다. 이 창 될 때 스키마와 같은 그룹 개체를 표시 하거나 왼쪽된 창에서 코드 없이 개체를 선택 합니다.|  
|**범주별으로 개체**|범주별으로 개체의 수를 보여 줍니다. 이 창 그룹 개체를 작업 스키마와 같은 경우에 표시 되거나 왼쪽된 창에서 코드 없이 개체를 선택 합니다.|  
|**통계**|선택한 개체에 대 한 변환 통계가 표시 됩니다. 이 창의 왼쪽된 창에서 코드를 사용 하 여 개별 개체를 선택 하는 경우에 표시 됩니다. 확장 해야 할 수 있습니다 **통계**, 바로 위에 되는 **원본** 이 창을 보려면 창.|  
|**원본**|변환 되지 않은 코드를 강조 표시 및 선택한 개체에 대해 Oracle 코드를 보여 줍니다 [!INCLUDE[tsql](../../includes/tsql-md.md)]합니다. 이 창의 왼쪽된 창에서 코드를 사용 하 여 개별 개체를 선택 하는 경우에 표시 됩니다.<br /><br />책갈피의 선택을 취소 하는 줄 번호를 클릭 합니다. 창의 맨 위에 있는 단추를 사용 하는 코드를 통해 이동 합니다.|  
|**대상**|변환의 결과 보여 줍니다. [!INCLUDE[tsql](../../includes/tsql-md.md)] 선택한 개체 및 변환 되지 않은 코드에 대 한 오류 메시지에 대 한 코드입니다. 이 창의 왼쪽된 창에서 코드를 사용 하 여 개별 개체를 선택 하는 경우에 표시 됩니다.<br /><br />책갈피의 선택을 취소 하는 줄 번호를 클릭 합니다. 창의 맨 위에 있는 단추를 사용 하는 코드를 통해 이동 합니다.|  
|**메시지 창**|오류, 경고 및 평가 보고서를 만드는 동안 생성 된 정보 메시지를 보여 줍니다. 메시지 수로 그룹화 됩니다. 오류를 발생 시킨 코드를 보려면 클릭 **오류**를 **경고**, 또는 **정보**, 메시지의 범주를 확장 한 다음 메시지를 클릭 합니다.|  
  
