---
title: "Invoke-ProcessASDatabase | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 66d5d154-88ce-4c2e-b1ef-e2d2f6fb1c44
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Invoke-ProcessASDatabase
  기본 메타데이터 유형에 따라 특정 **ProcessType** 또는 **RefreshType** 으로 지정된 **Database** 에서 **Process** 연산을 수행합니다.  
  
 다차원 메타데이터를 데이터베이스의 **ProcessType**에 사용합니다.(여기에는 호환성 수준이 1050, 1100 또는 1103인 테이블 형식 데이터베이스가 포함됩니다.)  
  
 호환성 수준 1200 이상의 테이블 형식 데이터베이스에 **RefreshType** 을(를) 사용합니다.  
  
## 구문  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-RefreshType] <RefreshType> {Full | ClearValues | Calculate |     DataOnly | Automatic | Add | Defragment} [-Server <string>] [-Credential <pscredential>] [-WhatIf] [-Confirm]     [<CommonParameters>]`  
  
 `Invoke-ProcessASDatabase [-DatabaseName] <string> [-ProcessType] <ProcessType> {ProcessFull | ProcessAdd |     ProcessUpdate | ProcessIndexes | ProcessData | ProcessDefault | ProcessClear | ProcessStructure |     ProcessClearStructureOnly | ProcessScriptCache | ProcessRecalc | ProcessDefrag} [-Server <string>] [-Credential     <pscredential>] [-WhatIf] [-Confirm]  [<CommonParameters>]`  
  
## Description  
 **Invoke-ProcessASDatabase** cmdlet은 사용자가 지정한 수준으로 데이터베이스를 처리합니다. 예를 들어, 호환성 수준이 1200인 테이블 형식 데이터베이스에 대해 **RefreshType**을 **Full**로 설정하여 기존 데이터를 모두 새로운 데이터로 덮어씁니다.  
  
 처리 유형(다차원) 또는 새로 고침 유형(테이블 형식)이 필요하며, 데이터베이스 또는 서버 매개 변수 앞 또는 뒤에 지정할 수 있습니다.  
  
-   다차원의 경우 [처리 옵션 및 설정&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)을 참조하세요.  
  
-   테이블 형식의 경우 [데이터베이스, 테이블 또는 파티션 처리&#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)를 참조하세요.  
  
## 매개 변수  
  
### -DatabaseName \<string>  
 테이블 형식 또는 다차원 데이터베이스가 처리되도록 지정합니다.  
  
|||  
|-|-|  
|필수 여부|true|  
|위치|0|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -Server\<Microsoft.AnalysisSevices.Server>  
 컨텍스트에 **SQLAS** 공급자 디렉터리를 사용하지 않는 경우에는 연결한 서버 인스턴스를 선택적으로 지정합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -RefreshType \<Microsoft.AnalysisServices.RefreshType>  
 호환성 수준 1200에서 테이블 형식 데이터베이스의 처리 유형을 지정합니다.  유효한 값은 Full, ClearValues, Calculate, DataOnly, Automatic, Add, 및 Defragment입니다. 설명 및 지침은 [데이터베이스, 테이블 또는 파티션 처리&#40;Analysis Services&#41;](../../analysis-services/tabular-models/process-database-table-or-partition-analysis-services.md)를 참조하세요.  
  
|||  
|-|-|  
|필수 여부|true|  
|위치|1.|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -ProcessType \<Microsoft.AnalysisServices.ProcessType>  
 호환성 수준 1050-1103에서 다차원 데이터베이스 또는 테이블 형식 데이터베이스의 처리 유형을 지정합니다. 유효한 값에는 ProcessFull, ProcessAdd, ProcessUpdate, ProcessIndexes, ProcessData, ProcessDefault, ProcessClear, ProcessStructure, ProcessCelarStructureOnly, ProcessScriptCache, 또는 ProcessRecalc가 포함됩니다. 설명 및 지침은 [처리 옵션 및 설정&#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-options-and-settings-analysis-services.md)을 참조하세요.  
  
|||  
|-|-|  
|필수 여부|true|  
|위치|1.|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -Credential  
 이 매개 변수를 지정하면 전달된 사용자 이름 및 암호를 사용하여 Analysis Server 인스턴스에 연결합니다. 자격 증명을 지정하지 않으면 스크립트를 실행하는 사용자의 기본 Windows 계정으로 간주됩니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
## -Whatif  
 연산을 실행하기 전에 연산의 영향에 대한 정보를 가져오려면 이 매개 변수를 포함합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
## -Confirm  
 연산을 실행하기 전에 예 또는 아니오 응답으로 연산을 확인하려면 이 매개 변수를 포함합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치||  
|기본값||  
|파이프라인 입력 허용||  
|와일드카드 문자 허용|false|  
  
## 예제 1(SQLAS 공급자)  
 이 예제는 **SQLAS** 공급자를 사용하여 기본 인스턴스에서 데이터베이스 목록으로 컨텍스트를 설정합니다.  데이터베이스 디렉터리의 콘텐츠를 나열하는 경우 모든 데이터베이스가 해당 프로세스 상태 및 읽기/쓰기 모드와 함께 표시됩니다.  
  
 데이터베이스 폴더에서 데이터베이스 이름만 지정하여 **Invoke-ProcessASDatabase**를 실행할 수 있습니다.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server > cd sqlas\ssas-srv-01\default\databases  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> dir  
. . . .  
PS SQLSERVER:\sqlas\ssas-srv-01\default\databases> Invoke-ProcessASDatabase "adventureworks"  
  
```  
  
 데이터베이스 유형에 따라 **RefreshType** 또는 **ProcessType**을 지정하라는 메시지가 표시됩니다.  
  
 처리 증명은 return 문에서 영향 개체 Microsoft.AnalysisServices.Tabular.ObjectImpact의 현재 상태입니다.  
  
 개체 상태 정보가 경우에 따라 캐시되기 때문에, 처리가 완료된 후에 디렉터리의 콘텐츠를 나열하면, 데이터베이스 상태에 ‘처리되지 않은’ 원래 설명자가 남아 있습니다. objectimact이 반환되었다면 데이터베이스가 실제 처리된 것이므로, 오해의 소지가 있습니다.  
  
 Management Studio에서 데이터베이스 속성 페이지를 확인하거나, 새 세션을 시작하거나, 데이터베이스 개체에서 처리 상태를 반환하여([Microsoft.AnalysisServices.ProcessableMajorObject.LastProcessed](https://msdn.microsoft.com/library/microsoft.analysisservices.processablemajorobject.lastprocessed.aspx)를 통해) 프로세스가 완료되었다는 것을 확인할 수 있습니다.  
  
## 예제 2  
 이 예제는 공급자 없이 cmdlet을 사용하는 동일한 연산을 보여줍니다. 서버 및 처리 유형을 지정하려면 추가적인 매개 변수가 필요합니다.  
  
```  
PS > import-module SQLPS -DisableNameChecking  
PS  SQL Server >  Invoke-ProcessASDatabase -databasename "AdventureWorks" -server '\\server-name\instancename' –ProcessType "ProcessFull"  
  
```  
  
## 관련 항목:  
 [Analysis services에서 테이블 형식 모델에 대한 호환성 수준](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  