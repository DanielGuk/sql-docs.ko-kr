---
title: PowerShell의 SQL Server 식별자 | Microsoft 문서
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
helpviewer_keywords:
- Cmdlets [SQL Server], Encode-Sqlname
- PowerShell [SQL Server], identifiers
- Encode-Sqlname cmdlet
- PowerShell [SQL Server], Encode-Sqlname
- Decode-Sqlname cmdlet
- PowerShell [SQL Server], Decode-Sqlname
- identifiers [SQL Server], PowerShell
- Cmdlets [SQL Server], Decode-Sqlname
ms.assetid: 651099b0-33b4-453a-a864-b067f21eb8b9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 654bd3d29de94401fc95d1a5d4d580f299b95297
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47824341"
---
# <a name="sql-server-identifiers-in-powershell"></a>PowerShell의 SQL Server 식별자
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

Windows PowerShell의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 Windows PowerShell 경로에서 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자를 사용합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자는 Windows PowerShell이 경로에서 지원하지 않는 문자를 포함할 수 있습니다. Windows PowerShell 경로에서 식별자를 사용할 때는 이러한 문자를 이스케이프 처리하거나 특수 인코딩을 사용해야 합니다.  
  
> [!NOTE]
> SQL Server PowerShell 모듈은 **SqlServer**와 **SQLPS**의 두 가지가 있습니다. **SQLPS** 모듈은 (이전 버전과의 호환성을 위해) SQL Server 설치에 포함되어 있지만 더 이상 업데이트되지는 않습니다. 최신 PowerShell 모듈은 **SqlServer** 모듈입니다. **SqlServer** 모듈은 **SQLPS**에 업데이트된 버전의 cmdlet이 포함되어 있으며, 최신 SQL 기능을 지원하는 새로운 cmdlet도 포함되어 있습니다.  
> 이전 버전의 **SqlServer** 모듈은 SSMS(SQL Server Management Studio)에 *포함되었습니다*(SSMS 16.x 버전만 해당). SSMS 17.0 이상이 포함된 PowerShell을 사용하려면 PowerShell 갤러리에서 **SqlServer** 모듈을 설치해야 합니다.
> **SqlServer** 모듈을 설치하려면 [SQL Server PowerShell 설치](download-sql-server-ps-module.md)를 참조하세요.


## <a name="sql-server-identifiers-in-windows-powershell-paths"></a>Windows PowerShell 경로의 SQL Server 식별자  
 Windows PowerShell 공급자는 Windows 파일 시스템과 유사한 경로 구조를 사용하여 데이터 계층 구조를 표시합니다. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 공급자는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체에 대한 경로를 구현합니다. [!INCLUDE[ssDE](../includes/ssde-md.md)]의 경우 드라이브는 SQLSERVER:로 설정되고 첫 번째 폴더는 \SQL로 설정되며 데이터베이스 개체는 컨테이너 및 항목으로 참조됩니다. 다음은 기본 [!INCLUDE[ssSampleDBobject](../includes/sssampledbobject-md.md)] 인스턴스에서 [!INCLUDE[ssDE](../includes/ssde-md.md)]데이터베이스의 Purchasing 스키마에 있는 Vendor 테이블에 대한 경로입니다.  
  
```  
SQLSERVER:\SQL\MyComputer\DEFAULT\Databases\AdventureWorks2012\Tables\Purchasing.Vendor  
```  
  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자는 테이블 또는 열 이름과 같은 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 개체의 이름입니다. 다음과 같이 두 가지 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 식별자 유형이 있습니다.  
  
-   일반 식별자는 Windows PowerShell 경로에서도 지원되는 문자 집합으로 제한됩니다. 이러한 이름은 변경하지 않고 Windows PowerShell 경로에 사용할 수 있습니다.  
  
-   구분 식별자에는 Windows PowerShell 경로 이름에서 지원되지 않는 문자를 사용할 수 있습니다. 구분 식별자가 대괄호로 묶이면(예: [IdentifierName]) 대괄호로 묶은 식별자라고 하고 큰따옴표로 묶이면(예: "IdentifierName") 따옴표 붙은 식별자라고 합니다. 구분 식별자가 Windows PowerShell 경로에 지원되지 않는 문자를 사용하는 경우 해당 식별자를 컨테이너 또는 항목 이름으로 사용하기 전에 문자를 인코딩하거나 이스케이프 처리해야 합니다. 인코딩은 모든 문자에 대해 작동합니다. 콜론 문자(:)와 같은 일부 문자는 이스케이프 처리되지 않습니다.  
  
## <a name="sql-server-identifiers-in-cmdlets"></a>cmdlet의 SQL Server 식별자  
 일부 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] cmdlet에는 식별자를 입력으로 사용하는 매개 변수가 있습니다. 매개 변수 값은 일반적으로 따옴표가 붙은 문자열 상수나 문자열 변수로 제공됩니다. 식별자가 문자열 상수나 변수로 제공되면 Windows PowerShell에서 지원하는 문자 집합과 충돌하지 않습니다.  
  
## <a name="sql-server-identifier-tasks"></a>SQL Server 식별자 태스크  
  
|태스크 설명|아티클|  
|----------------------|-----------|  
|인스턴스가 실행 중인 컴퓨터 이름을 포함하여 인스턴스 이름을 지정하는 방법에 대해 설명합니다.|[SQL Server PowerShell 공급자에 인스턴스 지정](specify-instances-in-the-sql-server-powershell-provider.md)|  
|Windows PowerShell 경로에서 지원되지 않는 구분 식별자의 문자에 대한 16진수 인코딩을 지정하는 방법에 대해 설명합니다. 또한 16진수 문자를 해독하는 방법에 대해 설명합니다.|[SQL Server 식별자 인코딩 및 디코딩](encode-and-decode-sql-server-identifiers.md)|  
|PowerShell 경로에서 지원되지 않는 문자에 대해 Windows PowerShell 이스케이프 문자를 사용하는 방법에 대해 설명합니다.|[SQL Server 식별자 이스케이프](escape-sql-server-identifiers.md)|  
  
## <a name="see-also"></a>참고 항목  
 [SQL Server PowerShell Provider](sql-server-powershell-provider.md)   
 [SQL Server PowerShell](sql-server-powershell.md)   
 [데이터베이스 식별자](../relational-databases/databases/database-identifiers.md)  
  
  
