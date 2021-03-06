---
title: 형식 및 멤버 System.Data.dll에 허용 되지 않는 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- host protection attributes [CLR integration]
- common language runtime [SQL Server], host protection attributes
ms.assetid: ee5f55e9-fbef-401a-be18-a2e5873c8720
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 4233bc1ddd98d6fe678d9d37f1acd7a4b66b687e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48143203"
---
# <a name="disallowed-types-and-members-in-systemdatadll"></a>System.Data.dll에 허용되지 않는 유형 및 멤버
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 형식 또는 멤버에는 사용할 수 없게 하는 공용 언어 통합 (CLR) 프로그래밍을 `HostProtectionAttribute` 를 지정 하는 `System.Security.Permissions.HostProtectionResource` 열거형의 값을 사용 하 여 `ExternalProcessMgmt`, `ExternalThreading`, `MayLeakOnAbort`, `SecurityInfrastructure`, `SelfAffectingProcessMgmnt`, `SelfAffectingThreading`, **: SharedState**합니다 `Synchronization`, 또는 `UI`합니다. 다음 표에는 HPA(호스트 보호 특성) 값이 허용되지 않는 System.Data.dll 어셈블리의 멤버 및 유형이 나열되어 있습니다.  
  
> [!NOTE]  
>  이 목록은 지원되는 어셈블리에서 생성되었습니다. 자세한 내용은 [Supported .NET Framework Libraries](../clr-integration/database-objects/supported-net-framework-libraries.md)을 참조하세요.  
  
|유형 또는 멤버|HPA 값|  
|--------------------|--------------------|  
|System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteReader()|ExternalThreading|  
|System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency..ctor()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Start()|ExternalThreading|  
|System.Data.SqlClient.SqlDependency.Stop()|ExternalThreading|  
|System.Data.TypedDataSetGenerator|SharedState, Synchronization|  
|System.Xml.XmlDataDocument|Synchronization|  
  
## <a name="see-also"></a>관련 항목  
 [호스트 보호 특성 및 CLR 통합 프로그래밍](host-protection-attributes-and-clr-integration-programming.md)   
 [Microsoft.VisualBasic.dll에 허용 되지 않는 유형 및 멤버](disallowed-types-and-members-in-microsoft-visualbasic-dll.md)   
 [Mscorlib.dll에 허용 되지 않는 유형 및 멤버](disallowed-types-and-members-in-mscorlib-dll.md)   
 [Disallowed Types and Members in System.dll](disallowed-types-and-members-in-system-dll.md)   
 [System.Core.dll에 허용되지 않는 형식 및 멤버](disallowed-types-and-members-in-system-core-dll.md)  
  
  
