---
title: GenerateDatabaseUpgradeScript 메서드(WMI MSReportServer_ConfigurationSetting) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
api_name:
- GenerateDatabaseUpgradeScript (WMI MSReportServer_ConfigurationSetting Class)
api_location:
- reportingservices.mof
topic_type:
- apiref
helpviewer_keywords:
- GenerateDatabaseUpgradeScript method
ms.assetid: 88534e8e-2877-41cd-b5c2-b1d33a0fd203
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 553afbfe7e6ad274261172740d7d55b27729b546
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48057303"
---
# <a name="generatedatabaseupgradescript-method-wmi-msreportserverconfigurationsetting"></a>GenerateDatabaseUpgradeScript 메서드(WMI MSReportServer_ConfigurationSetting)
  보고서 서버 데이터베이스를 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 스키마로 업그레이드하는 데 사용할 수 있는 스크립트를 생성합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub GenerateDatabaseUpgradeScript(DatabaseName as String, _  
    ServerVersion as String, ByRef Script as String, _  
    ByRef HRESULT as Int32)  
```  
  
```csharp  
public void GenerateDatabaseUpgradeScript (string DatabaseName,   
    string ServerVersion, out string Script,   
    out Int32 HRESULT);  
```  
  
## <a name="parameters"></a>매개 변수  
 *Databasename*  
 업그레이드할 보고서 서버 데이터베이스의 이름이 들어 있는 문자열입니다.  
  
 *ServerVersion*  
 보고서 서버의 버전이 들어 있는 문자열입니다.  
  
 *스크립트*  
 [out] 생성된 SQL 스크립트가 들어 있는 문자열입니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>Remarks  
 생성된 스크립트는 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]및 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]을 지원합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목  
 [MSReportServer_ConfigurationSetting 멤버](msreportserver-configurationsetting-members.md)  
  
  
