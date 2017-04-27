---
title: "Remove-PowerPivotServiceApplication cmdlet | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 2742b2a3-927c-4e7c-bd7d-43c072fa01ab
caps.latest.revision: 11
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 11
---
# Remove-PowerPivotServiceApplication cmdlet
  [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 삭제합니다.  
  
 **적용 대상:** SharePoint 2010 및 SharePoint 2013  
  
## 구문  
  
```  
Remove-PowerPivotServiceApplication [-Identity <SPGeminiServiceApplicationPipeBind>] [-DeleteAll <switch>] [-RemoveData <switch>] [-Confirm <switch>] [<CommonParameters>]  
```  
  
## Description  
 Remove-PowerPivotServiceApplication cmdlet은 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 팜에서 삭제합니다. DeleteAll을 사용하여 모든 서비스 인스턴스를 한 번에 삭제하거나 Identity 매개 변수를 사용하여 단일 인스턴스를 제거할 수 있습니다. 인스턴스 정보를 가져오려면 Get-PowerPivotServiceApplication을 실행하여 팜의 모든 인스턴스를 반환합니다.  
  
 서비스 응용 프로그램 데이터베이스 및 캐시된 파일을 선택적으로 제거하려면 RemoveData 매개 변수를 사용합니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 통합 문서가 콘텐츠 라이브러리에 유지되기는 하지만 더 이상 작동하지 않게 됩니다.  
  
## 매개 변수  
  
### -Identity \<SPGeminiServiceApplicationPipeBind>  
 팜에 있는 단일 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램의 GUID를 지정합니다. 응용 프로그램을 하나만 제거하고 다른 서비스 응용 프로그램은 그대로 두려면 GUID를 지정해야 합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|0|  
|기본값||  
|파이프라인 입력 허용|true|  
|와일드카드 문자 허용|false|  
  
### -Confirm \<switch>  
 명령을 실행하기 전 확인 메시지를 표시합니다. 이 값은 기본적으로 설정되어 있습니다. 명령에서 확인 응답을 무시하려면 명령에 Confirm:$false를 지정합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -DeleteAll \<switch>  
 모든 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 삭제하지만 서비스 응용 프로그램 데이터베이스와 팜의 서비스 인스턴스 개체는 삭제하지 않습니다. [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 시스템 서비스 및 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 엔진 서비스 개체는 인스턴스화된 상태로 유지되지만 사용할 수는 없습니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### -RemoveData \<switch>  
 데이터 새로 고침 일정, 통합 문서 사용 데이터, 로드된 데이터를 추적하는 데 사용되는 인스턴스 맵 및 기타 내부 데이터가 포함된 서비스 응용 프로그램 데이터베이스를 제거합니다.  
  
|||  
|-|-|  
|필수 여부|false|  
|위치|명명됨|  
|기본값||  
|파이프라인 입력 허용|false|  
|와일드카드 문자 허용|false|  
  
### \<CommonParameters>  
 이 cmdlet은 공통 매개 변수 Verbose, Debug, ErrorAction, ErrorVariable, WarningAction, WarningVariable, OutBuffer 및 OutVariable을 지원합니다. 자세한 내용은 [About_CommonParameters](http://go.microsoft.com/fwlink/?linkID=227825)를 참조하세요.  
  
## 입/출력  
 입력 유형은 cmdlet에 파이프할 수 있는 개체 유형입니다. 반환 유형은 cmdlet에서 반환하는 개체 유형입니다.  
  
|||  
|-|-|  
|입력|없음|  
|출력|없음|  
  
## 예제 1  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop  
```  
  
 이 예에서는 단일 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 삭제하지만 해당 데이터베이스나 캐시는 제거하지 않습니다. identity를 지정하지 않으면 identity를 지정하라는 메시지가 표시됩니다.  
  
## 예제 2  
  
```  
C:\PS>Remove-PowerPivotServiceApplication -DeleteAll  
```  
  
 이 예에서는 팜의 모든 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램을 삭제합니다. 데이터베이스와 캐시는 삭제되지 않습니다.  
  
## 예 3  
  
```  
CC:\PS>Remove-PowerPivotServiceApplication -identity 12345678-90ab-cdef-ghijklmnop -RemoveData  
```  
  
 이 예에서는 단일 [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] 서비스 응용 프로그램과 해당 데이터베이스 및 캐시 파일을 삭제합니다.  
  
  