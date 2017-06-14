---
title: "ListReportServersInDatabase 메서드 (WMI MSReportServer_ConfigurationSetting) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- ListReportServersInDatabase (WMI MSReportServer_ConfigurationSetting Class)
apilocation:
- reportingservices.mof
apitype: MOFDef
helpviewer_keywords:
- ListReportServersInDatabase method
ms.assetid: a4bf5968-c46f-484f-a510-65e2dde65a0d
caps.latest.revision: 18
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 2bdc6ca4ca42bc8c66ebfbb292dff8c022e3cdf2
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="configurationsetting-method---listreportserversindatabase"></a>ListReportServersInDatabase ConfigurationSetting 메서드
  보고서 서버에 보안 정보에 대한 액세스 권한이 있는지 여부에 관계없이 보고서 서버 데이터베이스에 있는 보고서 서버 설치 목록을 반환합니다.  
  
## <a name="syntax"></a>구문  
  
```vb  
Public Sub ListReportServersInDatabase(ByRef MachineNames() As String, _  
    ByRef InstanceNames() As String, ByRef InstallationIDs() As String, _  
    ByRef IsInitialized() As Boolean, ByRef Length As Int32, _  
    ByRef HRESULT As Int32, ByRef ExtendedErrors() As String)  
```  
  
```csharp  
public void ListReportServersInDatabase (out string[] MachineNames,   
    out string[] InstanceNames, out string[] InstallationIDs,   
    out Boolean[] IsInitialized,out Int32 Length, out Int32 HRESULT,    
    out string[] ExtendedErrors);  
```  
  
## <a name="parameters"></a>매개 변수  
 *MachineNames[]*  
 [out] 데이터베이스에서 설치된 보고서 서버의 컴퓨터 이름이 들어 있는 배열입니다.  
  
 *InstanceNames[]*  
 [out] 데이터베이스에서 설치된 각 보고서 서버의 인스턴스 이름이 들어 있는 배열입니다.  
  
 *InstallationIDs[]*  
 [out] 데이터베이스에서 설치된 각 보고서 서버의 설치 ID가 들어 있는 배열입니다.  
  
 *IsInitialized[]*  
 [out] 데이터베이스에서 설치된 각 보고서 서버의 초기화 상태가 들어 있는 배열입니다.  
  
 *길이*  
 [out] 메서드에서 반환된 배열의 길이입니다. 반환된 모든 배열의 길이는 같습니다.  
  
 *HRESULT*  
 [out] 호출의 성공 여부를 나타내는 값입니다.  
  
 *ExtendedErrors[]*  
 [out] 호출에서 반환되는 추가 오류가 들어 있는 문자열 배열입니다.  
  
## <a name="return-value"></a>반환 값  
 메서드 호출의 성공 또는 실패를 나타내는 *HRESULT* 를 반환합니다. 0 값은 메서드 호출이 성공했음을 나타냅니다. 0 이외의 값은 오류가 발생했음을 나타냅니다.  
  
## <a name="remarks"></a>주의  
 ListReportServersInDatabase는 보고서 서버에 보안 정보에 대한 액세스 권한이 있는지 여부에 관계없이 보고서 서버 데이터베이스에 있는 보고서 서버 설치 목록을 나열하고 각 설치 정보가 들어 있는 일치하는 배열 집합을 반환합니다.  
  
## <a name="requirements"></a>요구 사항  
 **네임스페이스:** [!INCLUDE[ssRSWMInmspcA](../../includes/ssrswminmspca-md.md)]  
  
## <a name="see-also"></a>관련 항목:  
 [MSReportServer_ConfigurationSetting 멤버](../../reporting-services/wmi-provider-library-reference/msreportserver-configurationsetting-members.md)  
  
  