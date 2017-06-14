---
title: "데이터 처리 확장 프로그램에 대 한 Connection 클래스 구현 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- connections [Reporting Services], data processing extensions
- Connection class
- data processing extensions [Reporting Services], connections
ms.assetid: 7047d29e-a2c9-4e6f-ad02-635851a38ed7
caps.latest.revision: 42
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 1108be24704c38f0891e623fda02803e5f8c21e5
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="implementing-a-connection-class-for-a-data-processing-extension"></a>데이터 처리 확장 프로그램에 대한 Connection 클래스 구현
  **연결** 개체는 데이터베이스 연결 또는 유사한 리소스를 나타내며의 사용자에 대 한 시작 지점을 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램입니다. 유사한 동작의 모든 엔터티도 노출 될 수 있지만 데이터베이스 서버에 대 한 연결을 나타내는 한 **연결**합니다.  
  
 구현 하는 **연결** 개체를 구현 하는 클래스를 만들 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 을 선택적으로 구현 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>합니다.  
  
 구현에서 명령을 실행하려면 먼저 연결을 설정하여 열어두어야 합니다. 구현에서 클라이언트를 위해 연결을 암시적으로 열고 닫도록 하지 말고, 클라이언트가 연결을 명시적으로 열고 닫도록 구현에서 요구하도록 해야 합니다. 연결이 이루어지면 보안 검사를 수행합니다. [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] 데이터 처리 확장 프로그램에서 다른 클래스에 대한 기존 연결이 필요한 경우 데이터 원본 작업을 할 때 항상 보안 검사가 수행되도록 합니다.  
  
 필요한 연결의 속성이 연결 문자열로 나타납니다. [!INCLUDE[ssRS](../../../includes/ssrs-md.md)] 데이터 처리 확장 프로그램이 OLE DB에서 정의된 친숙한 이름/값 쌍 시스템을 사용하여 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection.ConnectionString%2A> 속성을 지원하도록 하는 것이 좋습니다.  
  
> [!NOTE]  
>  **연결** 풀링 연결이 나이 가능성을 줄이려면 명시 된 기타 기술을 고려해 야 할 수 있도록 개체는 대개 리소스를 많이 사용 하십시오.  
  
 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection>은 <xref:Microsoft.ReportingServices.Interfaces.IExtension>에서 상속됩니다. <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스는 연결 클래스 구현의 일부로 구현해야 합니다. <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스를 통해 클래스에서 지역화된 확장 프로그램 이름을 구현하고 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구성 파일에 저장된 확장 프로그램별 구성 정보를 처리할 수 있습니다.  
  
 프로그램 **연결** 개체에 포함 되어는 <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> 속성의 구현을 통해 <xref:Microsoft.ReportingServices.Interfaces.IExtension>합니다. 확장 프로그램의 사용자 인터페이스에서 보고서 관리자와 같이 친숙하고 지역화된 이름이 사용자에게 표시되도록 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 데이터 처리 확장 프로그램에서 <xref:Microsoft.ReportingServices.Interfaces.IExtension.LocalizedName%2A> 속성을 지원하는 것이 좋습니다.  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>또한 프로그램 **연결** 개체를 검색 하 고 RSReportServer.config 파일에 저장 된 사용자 지정 구성 데이터를 처리 합니다. 사용자 지정 구성 데이터를 처리하는 방법은 <xref:Microsoft.ReportingServices.Interfaces.IExtension.SetConfiguration%2A> 메서드를 참조하십시오.  
  
 <xref:Microsoft.ReportingServices.Interfaces.IExtension>을 구현하는 클래스는 나머지 데이터 처리 확장 프로그램 클래스가 언로드될 때 메모리에서 언로드되지 않습니다. 이 때문에 사용할 수 있습니다 프로그램 **확장** 클래스 간 연결 상태 정보를 저장 하거나 메모리에 캐시 될 수 있는 데이터를 저장할 수 있습니다. 프로그램 **확장** 보고서 서버가 실행 중인 상태로 클래스 메모리에 유지 됩니다.  
  
 확장할 수 있습니다 프로그램 **연결** 에 자격 증명에 대 한 지원을 포함 하도록 클래스 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 구현 하 여 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>합니다. 구현 하는 경우는 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.IntegratedSecurity%2A>, <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.UserName%2A>, 및 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension.Password%2A> 의 속성은 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension> 인터페이스를 사용 하도록 설정 하면는 **통합 보안** 확인란 및 **Username** 및 **암호** 의 텍스트 상자는 **데이터 원본** 보고서 디자이너의 대화 상자. 이를 통해 보고서 디자이너에서 인증을 지원하는 데이터 원본에 대한 자격 증명을 저장하고 검색할 수 있습니다. 자격 증명은 안전하게 저장되고 미리 보기 모드에서 보고서를 렌더링할 때 사용됩니다.  
  
> [!NOTE]  
>  <xref:Microsoft.ReportingServices.DataProcessing.IDbConnectionExtension>을 암시적으로 구현하려면 <xref:Microsoft.ReportingServices.DataProcessing.IDbConnection> 및 <xref:Microsoft.ReportingServices.Interfaces.IExtension> 인터페이스의 멤버를 구현해야 합니다.  
>   
>  샘플 **연결** 클래스 구현, 참조 [SQL Server Reporting Services 제품 샘플](http://go.microsoft.com/fwlink/?LinkId=177889)합니다.  
  
## <a name="see-also"></a>관련 항목:  
 [Reporting Services 확장 프로그램](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [데이터 처리 확장 프로그램 구현](../../../reporting-services/extensions/data-processing/implementing-a-data-processing-extension.md)   
 [Reporting Services 확장 프로그램 라이브러리](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  