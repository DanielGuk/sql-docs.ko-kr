---
title: "서버에 연결(로그인 페이지) 데이터베이스 엔진 | Microsoft 문서"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.swb.connecttosqlserver.login.f1
ms.assetid: e08cfbc3-bed5-4401-a13b-1c66d902fe32
caps.latest.revision: 6
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 1556c7facc4a671767fe2d6c061b4f6655ba521b
ms.lasthandoff: 04/11/2017

---
# <a name="connect-to-server-login-page-database-engine"></a>서버에 연결(로그인 페이지) 데이터베이스 엔진
[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]에 연결할 때 이 탭을 사용하여 옵션을 확인하거나 지정할 수 있습니다.  
  
> [!NOTE]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증으로 연결하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 및 Windows 인증 모드로 구성해야 합니다. 인증 모드를 확인하고 인증 모드를 변경하는 방법에 대한 자세한 내용은 [방법: 서버 인증 모드 변경](http://msdn.microsoft.com/en-us/79babcf8-19fd-4495-b8eb-453dc575cac0)을 참조하세요.  
  
## <a name="options"></a>옵션  
**서버 유형**  
개체 탐색기에서 서버를 등록할 때 연결할 서버 유형을 [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services 또는 Integration Services 중에서 선택합니다. 대화 상자의 나머지 부분에는 선택한 서버 유형에 적용되는 옵션만 표시됩니다. 등록된 서버에서 서버를 등록하는 경우 **서버 유형** 상자는 읽기 전용이며 등록된 서버 구성 요소에 표시된 서버 유형과 일치합니다. 다른 유형의 서버를 등록하려면 새 서버를 등록하기 전에 등록된 서버 도구 모음에서 [!INCLUDE[ssDE](../../includes/ssde_md.md)], Analysis Services, Reporting Services 또는 Integration Services를 선택합니다.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 를 통해 [!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)]데이터베이스 엔진 인스턴스에 연결할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증을 사용해야 하며 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 데이터베이스를 지정해야 합니다. **연결 암호화** 확인란을 선택해야 합니다.  
  
기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 는 **master**에 연결됩니다. 사용자 데이터베이스를 지정하면 개체 탐색기에서 해당 데이터베이스와 해당 개체만 볼 수 있습니다. **master**에 연결하면 모든 데이터베이스를 볼 수 있습니다. 자세한 내용은 [Microsoft Azure SQL Database 개요](http://go.microsoft.com/fwlink/?LinkId=163948)를 참조하세요.  
  
**서버 이름**  
연결할 서버 인스턴스를 선택합니다. 마지막으로 연결한 서버 인스턴스가 기본적으로 표시됩니다.  
  
**인증**  
[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]인스턴스에 연결할 때는 두 가지 인증 모드를 사용할 수 있습니다.  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 를 통해 [!INCLUDE[ssSDS](../../includes/sssds_md.md)]데이터베이스 엔진 인스턴스에 연결할 때는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증을 사용해야 하며 **서버에 연결** 대화 상자의 **연결 속성** 탭에서 데이터베이스를 지정해야 합니다. **연결 암호화** 확인란을 선택해야 합니다.  
  
기본적으로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 는 **master**에 연결됩니다. 사용자 데이터베이스를 지정하면 개체 탐색기에서 해당 데이터베이스와 해당 개체만 볼 수 있습니다. **master**에 연결하면 모든 데이터베이스를 볼 수 있습니다. 자세한 내용은 [Microsoft Azure SQL Database 개요](http://go.microsoft.com/fwlink/?LinkId=163948)를 참조하세요.  
  
**Windows 인증**  
[!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 인증 모드에서는 사용자가 Windows 사용자 계정을 통해 연결할 수 있습니다.  
  
**SQL Server 인증(SQL Server 인증(SQL Server Authentication))**  
사용자가 지정한 로그인 이름과 암호를 사용하여 트러스트되지 않은 연결로부터 연결하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 로그인 계정이 설정되고 지정한 암호가 전에 기록한 암호와 일치하는지를 확인하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 가 자체적으로 인증을 수행합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에 로그인 계정이 설정되어 있지 않으면 인증이 실패하고 오류 메시지가 나타납니다.  
  
> [!IMPORTANT]  
> 가능하면 Windows 인증을 사용하세요.  
  
**Active Directory 유니버설 인증**  
Active Directory 유니버설 인증은 Azure MFA(Multi-Factor Authentication)를 지원하는 대화형 워크플로입니다. Azure MFA를 사용하면 간단한 로그인 프로세스에 대한 사용자 요구를 충족하는 동시에 데이터 및 응용 프로그램에 대한 액세스를 보호할 수 있습니다. 이 인증은 전화 통화, 문자 메시지, PIN을 사용하는 스마트 카드, 모바일 앱 알림 등 다양하고 간단한 인증 옵션으로 강력한 인증을 제공하여 사용자가 원하는 방법을 선택할 수 있도록 합니다. 사용자 계정이 MFA에 맞게 구성된 경우 대화형 인증 워크플로에는 팝업 대화 상자, 스마트 카드 사용 등을 통한 추가 사용자 작업이 필요합니다. 사용자 계정이 MFA에 맞게 구성된 경우 사용자가 연결하려면 Azure 유니버설 인증을 선택해야 합니다. 사용자 계정에 MFA가 필요하지 않은 경우에도 사용자는 다른 두 가지 Azure Active Directory 인증 옵션을 사용할 수 있습니다. 자세한 내용은 [SQL Database 및 SQL Data Warehouse를 사용한 Azure AD MFA에 대한 SSMS 지원](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)을 참조하세요. SSMS 버전 16.3 이상이 필요합니다(2016년 8월).
  
**Active Directory 암호 인증**  
Azure Active Directory 인증은 Azure AD(Azure Active Directory)에서 ID를 사용하여 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] 에 연결하는 메커니즘입니다.  Azure로 페더레이션되지 않은 도메인에서 자격 증명을 사용하여 Windows에 로그인하는 경우 또는 초기 도메인이나 클라이언트 도메인에 따라 Azure AD를 사용하는 Azure AD 인증을 사용하는 경우 [!INCLUDE[ssSDS](../../includes/sssds_md.md)] 에 연결하는 데 이 방법을 사용합니다. 자세한 내용은 [Azure Active Directory 인증을 사용하여 SQL 데이터베이스에 연결](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)을 참조하세요.  
  
**Active Directory 통합 인증**  
Azure Active Directory 인증은 Azure AD(Azure Active Directory)에서 ID를 사용하여 [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssSDSfull](../../includes/sssdsfull_md.md)] 에 연결하는 메커니즘입니다. 페더레이션된 도메인에서 Azure Active Directory 자격 증명을 사용하여 Windows에 로그인하는 경우 [!INCLUDE[ssSDS](../../includes/sssds_md.md)] 에 연결하는 데 이 방법을 사용합니다. 자세한 내용은 [Azure Active Directory 인증을 사용하여 SQL 데이터베이스에 연결](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)을 참조하세요.  
  
**사용자 이름**  
연결에 사용할 Windows 사용자 이름입니다. 이 옵션은 **Active Directory 암호 인증**을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다. **Windows 인증**을 선택하는 경우에는 읽기 전용입니다.  
  
**로그인**  
연결 시 사용할 로그인을 입력합니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 사용할 수 있습니다.  
  
**암호**  
로그인 암호를 입력합니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 편집할 수 있습니다.  
  
**암호 저장**  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 에서 입력한 암호를 저장하려면 클릭합니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 인증을 사용하여 연결하도록 선택한 경우에만 표시됩니다.  
  
**Connect**  
위에서 선택한 서버에 연결하려면 클릭합니다.  
  
**옵션**  
대화 상자를 변경하여 암호 저장과 같은 추가 서버 연결 옵션을 숨기려면 클릭합니다.  
  
