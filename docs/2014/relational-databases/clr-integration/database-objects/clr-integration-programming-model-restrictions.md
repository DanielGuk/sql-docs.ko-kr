---
title: CLR 통합 프로그래밍 모델 제한 사항 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- common language runtime [SQL Server], programming model restrictions
- assemblies [CLR integration], CREATE ASSEMBLY checks
- programming model restrictions [CLR integration]
- assemblies [CLR integration], runtime checks
ms.assetid: 2446afc2-9d21-42d3-9847-7733d3074de9
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: a7b7dfcbd9d7cc7407ed33cc0ea00e93df839b93
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48187943"
---
# <a name="clr-integration-programming-model-restrictions"></a>CLR 통합 프로그래밍 모델 제한 사항
  관리 되는 저장 프로시저나 다른 관리 되는 데이터베이스 개체를 작성할 때 가지 특정 코드 검사를 수행한 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스에 처음 등록 될 때 관리 코드 어셈블리에서 검사를 사용 하 여는 `CREATE ASSEMBLY` 문 및 런타임에도 합니다. 실제로 런타임에 접근할 수 없는 코드 경로가 어셈블리에 있을 수 있으므로 관리 코드는 런타임에도 검사됩니다.  따라서 특히 클라이언트 환경에서 실행되는 '안전하지 않은' 코드가 있는 경우 어셈블리가 차단되지 않고 호스팅된 CLR에서 실행되지 않도록 유연성 있게 타사 어셈블리를 등록할 수 있습니다. 관리 코드가 충족 해야 하는 요구 사항으로 어셈블리를 등록 하는 여부에 따라 달라 집니다 `SAFE`, `EXTERNAL_ACCESS`, 또는 `UNSAFE`, `SAFE` 가 가장 엄격 함 및 아래에 나열 되어 있습니다.  
  
 관리 코드 어셈블리에 적용되는 제한뿐 아니라 부여되는 코드 보안 권한도 있습니다. CLR(공용 언어 런타임)은 관리 코드에 대해 CAS(코드 액세스 보안)라는 보안 모델을 지원합니다. 이 모델에서는 코드 ID를 기반으로 어셈블리에 사용 권한이 부여됩니다. `SAFE`, `EXTERNAL_ACCESS` 및 `UNSAFE` 어셈블리에는 서로 다른 CAS 권한이 있습니다. 자세한 내용은 [CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md)합니다.  
  
## <a name="create-assembly-checks"></a>CREATE ASSEMBLY 검사  
 `CREATE ASSEMBLY` 문을 실행하면 각 보안 수준에 대해 다음과 같은 검사가 수행됩니다.  감사가 실패하면 오류 메시지와 함께 `CREATE ASSEMBLY`가 실패합니다.  
  
### <a name="global-any-security-level"></a>전역(모든 보안 수준)  
 참조된 모든 어셈블리가 다음 조건을 하나 이상 충족해야 합니다.  
  
-   어셈블리가 데이터베이스에 이미 등록되었습니다.  
  
-   어셈블리가 지원되는 어셈블리 중 하나입니다. 자세한 내용은 [Supported .NET Framework Libraries](supported-net-framework-libraries.md)을 참조하세요.  
  
-   사용 중인 `CREATE ASSEMBLY FROM`  *\<위치 >,* 에서 사용할 수 있는 모든 참조 된 어셈블리 및 해당 종속성  *\<위치 >* 합니다.  
  
-   사용 중인 `CREATE ASSEMBLY FROM`  *\<바이트... >를* 바이트를 구분 하는 모든 참조를 통해 지정 됩니다.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 모든 `EXTERNAL_ACCESS` 어셈블리가 다음 조건을 충족해야 합니다.  
  
-   정적 필드가 정보 저장에 사용되지 않습니다. 읽기 전용 정적 필드는 허용됩니다.  
  
-   PEVerify 테스트에 통과합니다. MSIL 코드 및 관련된 메타데이터가 형식 안전성 요구 사항을 충족하는지 확인하는 PEVerify 도구(peverify.exe)는 .NET Framework SDK에 포함되어 있습니다.  
  
-   예를 들어 `SynchronizationAttribute` 클래스를 사용한 동기화가 사용되지 않습니다.  
  
-   파이널라이저 메서드가 사용되지 않습니다.  
  
 다음과 같은 사용자 지정 특성은 `EXTERNAL_ACCESS` 어셈블리에서 허용되지 않습니다.  
  
-   System.ContextStaticAttribute  
  
-   System.MTAThreadAttribute  
  
-   System.Runtime.CompilerServices.MethodImplAttribute  
  
-   System.Runtime.CompilerServices.CompilationRelaxationsAttribute  
  
-   System.Runtime.Remoting.Contexts.ContextAttribute  
  
-   System.Runtime.Remoting.Contexts.SynchronizationAttribute  
  
-   System.Runtime.InteropServices.DllImportAttribute  
  
-   System.Security.Permissions.CodeAccessSecurityAttribute  
  
-   System.Security.SuppressUnmanagedCodeSecurityAttribute  
  
-   System.Security.UnverifiableCodeAttribute  
  
-   System.STAThreadAttribute  
  
-   System.ThreadStaticAttribute  
  
### <a name="safe"></a>SAFE  
  
-   모든 `EXTERNAL_ACCESS` 어셈블리 조건이 검사됩니다.  
  
## <a name="runtime-checks"></a>런타임 검사  
 런타임에 코드 어셈블리에서 다음 조건이 검사됩니다. 이러한 조건 중 하나가 발견되면 관리 코드를 실행할 수 없으며 예외가 throw됩니다.  
  
### <a name="unsafe"></a>UNSAFE  
 명시적으로 바이트 배열에서 `System.Reflection.Assembly.Load()` 메서드를 호출하거나 암시적으로 `Reflection.Emit` 네임스페이스를 사용하여 어셈블리를 로드할 수 없습니다.  
  
### <a name="externalaccess"></a>EXTERNAL_ACCESS  
 모든 `UNSAFE` 조건이 검사됩니다.  
  
 지원되는 어셈블리 목록에서 다음 HPA(호스트 보호 특성) 값이 주석으로 추가된 유형과 멤버는 모두 허용되지 않습니다.  
  
-   SelfAffectingProcessMgmt  
  
-   SelfAffectingThreading  
  
-   Synchronization  
  
-   SharedState  
  
-   ExternalProcessMgmt  
  
-   ExternalThreading  
  
-   SecurityInfrastructure  
  
-   MayLeakOnAbort  
  
-   UI  
  
 Hpa 및 지원 되는 어셈블리의 허용 되지 않는 형식 및 멤버 목록에 대 한 자세한 내용은 참조 하세요. [호스트 보호 특성 및 CLR 통합 프로그래밍](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)합니다.  
  
### <a name="safe"></a>SAFE  
 모든 `EXTERNAL_ACCESS` 조건이 검사됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [지원 되는.NET Framework 라이브러리](supported-net-framework-libraries.md)   
 [CLR 통합 코드 액세스 보안](../security/clr-integration-code-access-security.md)   
 [호스트 보호 특성 및 CLR 통합 프로그래밍](../../clr-integration-security-host-protection-attributes/host-protection-attributes-and-clr-integration-programming.md)   
 [어셈블리 만들기](../assemblies/creating-an-assembly.md)  
  
  
