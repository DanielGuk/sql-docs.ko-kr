---
title: DQS 도메인에 대해 지원되는 SQL Server 및 SSIS 데이터 형식 | Microsoft Docs
ms.custom: ''
ms.date: 11/08/2011
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 4931143a-b84d-478b-9b45-174128d36ed3
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: d1a7285c9bb75b49b2590a0e29363f7a2ce34a38
ms.sourcegitcommit: c19696d3d67161ce78aaa5340964da3256bf602d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2018
ms.locfileid: "52617543"
---
# <a name="supported-sql-server-and-ssis-data-types-for-dqs-domains"></a>DQS 도메인에 대해 지원되는 SQL Server 및 SSIS 데이터 형식

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  SQL Server 및 SQL Server Integration Services(SSIS)에는 여러 가지 데이터 형식이 있지만 DQS 도메인에 대해서는 Date, Decimal, Integer 및 String으로 4개의 데이터 형식이 있습니다. SQL Server 및 SSIS 데이터 형식이 DQS에서 모두 지원되지는 않습니다. 원본 데이터 형식이 DQS에서 지원되고 DQS 도메인 데이터 형식과 일치하는 경우에만 데이터 품질 활동을 수행하기 위해 DQS 도메인에 원본 데이터를 매핑할 수 있습니다. 이 항목에서는 지원되는 SQL Server 및 SSIS 데이터 형식 및 DQS의 4가지 각 도메인 데이터 형식에 대해 매핑할 수 있는 데이터 형식에 대한 정보를 제공합니다.  
  
> [!NOTE]  
>  .xlsx 및 .xls 파일에서는 처음 8개 행에서 가장 많이 사용된 데이터 형식에 의해 원본 열의 데이터 형식이 결정됩니다. 데이터 형식을 따르지 않는 셀에는 null 값이 지정됩니다. 마찬가지로 .csv 파일에서는 처음 8개 행에서 가장 많이 사용된 데이터 형식에 의해 원본 열의 데이터 형식이 결정됩니다.  
  
##  <a name="SQLServer"></a> 지원되는 SQL Server 데이터 형식  
 다음 표에서는 각 DQS 도메인 데이터 형식에 대해 지원되는 SQL Server 데이터 형식에 대한 정보를 제공합니다.  
  
|DQS 도메인 데이터 형식|지원되는 SQL Server 데이터 형식|  
|--------------------------|------------------------------------|  
|date|날짜|  
|Decimal|Decimal<br /><br /> FLOAT<br /><br /> money<br /><br /> NUMERIC<br /><br /> REAL<br /><br /> SMALLMONEY|  
|정수|BIGINT<br /><br /> ssNoversion<br /><br /> SMALLINT<br /><br /> TINYINT|  
|String|char<br /><br /> NCHAR<br /><br /> NVARCHAR<br /><br /> varchar|  
  
 다른 SQL Server 데이터 형식은 DQS에서 지원되지 않습니다. 모든 SQL Server 데이터 형식에 대한 자세한 내용은 [데이터 형식&#40;Transact-SQL&#41;](../t-sql/data-types/data-types-transact-sql.md)을 참조하세요.  
  
##  <a name="SSIS"></a> 지원되는 SSIS 데이터 형식  
 다음 표에서는 각 DQS 도메인 데이터 형식에 대해 지원되는 SSIS 데이터 형식에 대한 정보를 제공합니다.  
  
|DQS 도메인 데이터 형식|지원되는 SSIS 데이터 형식|  
|--------------------------|------------------------------|  
|date|DT_DATE|  
|Decimal|DT_DECIMAL<br /><br /> DT_NUMERIC<br /><br /> DT_R4<br /><br /> DT_R8|  
|정수|DT_I1<br /><br /> DT_I2<br /><br /> DT_I4<br /><br /> DT_I8<br /><br /> DT_U1<br /><br /> DT_U2<br /><br /> DT_U4<br /><br /> DT_U8|  
|String|DT_STR<br /><br /> DT_WSTR|  
  
 다른 SSIS 데이터 형식은 DQS에서 지원되지 않습니다. 모든 SSIS 데이터 형식에 대한 자세한 내용은 [Integration Services Data Types](../integration-services/data-flow/integration-services-data-types.md)을 참조하십시오.  
  
## <a name="see-also"></a>참고 항목  
 [도메인 관리](../data-quality-services/managing-a-domain.md)  
  
  
