---
title: SQL Server 가져오기 및 내보내기 마법사 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
helpviewer_keywords:
- exporting data
- mapping files [Integration Services]
- SQL Server Import and Export Wizard
- SSIS packages, creating
- packages [Integration Services], copying
- Integration Services packages, creating
- packages [Integration Services], creating
- SQL Server Integration Services packages, creating
- Import and Export Wizard
- copying data [Integration Services]
- importing data, SSIS packages
- sources [Integration Services], copying data
ms.assetid: c0e4d867-b2a9-4b2a-844b-2fe45be88f81
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: bf8b2906e3e4915abeb76782743394e536bd62d3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48053209"
---
# <a name="sql-server-import-and-export-wizard"></a>SQL Server 가져오기 및 내보내기 마법사
  합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사를 만드는 가장 간단한 방법을 제공을 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 원본에서 대상 데이터를 복사 하는 패키지입니다.  
  
> [!NOTE]  
>  64비트 컴퓨터의 경우 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에서는 64비트 버전의 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사(DTSWizard.exe)를 설치합니다. 그러나 Access 또는 Excel 등의 일부 데이터 원본은 32비트 공급자만 제공합니다. 이러한 데이터 원본을 사용하려면 32비트 버전의 마법사를 설치하여 실행해야 합니다. 마법사의 32 비트 버전을 설치 하려면 클라이언트 도구를 선택 하거나 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 설치 중입니다.  
  
 시작 메뉴, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 또는 명령 프롬프트에서 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 가져오기 및 내보내기 마법사를 시작할 수 있습니다. 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사를 실행](start-the-sql-server-import-and-export-wizard.md)합니다.  
  
 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 데이터를 복사할 수 있는 데이터 원본에서는 관리 되는 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 데이터 공급자 또는 네이티브 OLE DB 공급자를 사용할 수 있습니다. 사용 가능한 공급자 목록에는 다음 데이터 원본이 포함됩니다.  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   플랫 파일  
  
-   Microsoft Office Access  
  
-   Microsoft Office Excel  
  
 일부 마법사 기능은 마법사를 시작하는 환경에 따라 다르게 작동합니다.  
  
-   시작 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]를 선택 하 여 패키지를 즉시 실행 하는 **즉시 실행** 확인란 합니다. 기본적으로 이 확인란이 선택되어 있으므로 패키지가 즉시 실행됩니다.  
  
     패키지를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에 저장할지, 아니면 파일 시스템에 저장할지를 결정할 수도 있습니다. 패키지를 저장하도록 선택할 경우에는 패키지 보호 수준도 지정해야 합니다. 패키지 보호 수준에 대 한 자세한 내용은 참조 하세요. [Sensitive Data in Packages에 대 한 액세스 제어](../security/access-control-for-sensitive-data-in-packages.md)입니다.  
  
     후 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사가 패키지를 만들고 데이터를 복사를 사용할 수 있습니다는 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너를 열고 태스크, 변환 및 이벤트 기반 논리를 추가 하 여 저장된 된 패키지를 변경 합니다.  
  
    > [!NOTE]  
    >  [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], 마법사에서 만든 패키지를 저장 하는 옵션이 제공 되지 않습니다.  
  
-   시작 하는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서를 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], 마법사를 완료할 단계로 패키지를 실행할 수 없습니다. 대신 마법사를 시작한 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 프로젝트에 패키지가 추가됩니다. 그런 다음 패키지를 실행하거나 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 디자이너에서 태스크, 변환 및 이벤트 기반 논리를 추가하여 패키지를 확장할 수 있습니다.  
  
 자세한 내용은 [SQL Server 가져오기 및 내보내기 마법사를 실행](start-the-sql-server-import-and-export-wizard.md)합니다.  
  
## <a name="permissions-required-by-the-import-and-export-wizard"></a>가져오기 및 내보내기 마법사에 필요한 권한  
 완료는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 성공적으로 적어도 다음 권한이 있어야 합니다.  
  
-   원본 및 대상 데이터베이스나 파일 공유에 연결할 수 있는 권한. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], 서버 및 데이터베이스에 해당 하는 로그인의 권한이이 필요 합니다.  
  
-   원본 데이터베이스나 파일의 데이터를 읽을 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 원본 테이블 및 뷰에 대 한 SELECT 권한이 필요 합니다.  
  
-   대상 데이터베이스나 파일에 데이터를 쓸 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], 대상 테이블에 대 한 INSERT 권한이 필요 합니다.  
  
-   새 대상 데이터베이스나 테이블 또는 파일을 만들려는 경우 새 데이터베이스나 테이블 또는 파일을 만들 수 있는 권한. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 CREATE DATABASE 또는 CREATE TABLE 권한이 필요합니다.  
  
-   Msdb 데이터베이스 또는 파일 시스템에 쓸 수 있는 충분 한 권한 마법사로 만든 패키지를 저장 하려면. [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)], msdb 데이터베이스에 대 한 INSERT 권한이 필요 합니다.  
  
## <a name="mapping-data-types-in-the-import-and-export-wizard"></a>가져오기 및 내보내기 마법사에서 데이터 형식 매핑  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 최소한의 변환 기능을 제공 합니다. 새로운 대상 테이블 및 파일에서 열의 이름, 데이터 형식 및 데이터 형식 속성을 설정하는 것 이외의 열 수준 변환은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사에서 지원되지 않습니다.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사는 매핑을 사용 하는 파일 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 다른 한 데이터베이스 버전 또는 시스템 데이터 형식을 매핑할 제공 합니다. 예를 들어 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서 Oracle로 매핑할 수 있습니다. XML 형식의 매핑 파일은 기본적으로 C:\Program Files\Microsoft SQL Server\100\DTS\MappingFiles에 설치됩니다. 비즈니스에서 데이터 형식 간에 다른 매핑을 필요로 하는 경우 매핑을 업데이트하여 마법사가 수행하는 매핑에 적용할 수 있습니다. 예를 들어, 하려는 경우는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **nchar** 매핑하려면 db2 데이터 형식 **그래픽** 데이터 형식 대신 DB2 **VARGRAPHIC** 데이터 형식에서 데이터를 전송 하는 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] DB2로 변경 합니다 **nchar** 사용 하려면 SqlClientToIBMDB2.xml 매핑 파일의 매핑 **그래픽** 대신 **VARGRAPHIC.**  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]에는 가장 일반적으로 사용되는 원본과 대상 조합 간 매핑이 포함되어 있으므로 새 매핑 파일을 Mapping Files 디렉터리에 추가하여 추가 원본 및 대상을 지원할 수 있습니다. 새 매핑 파일은 게시된 XSD 스키마를 따라야 하며 원본과 대상의 고유한 조합 간에 매핑해야 합니다.  
  
> [!NOTE]  
>  기존 매핑 파일을 편집 하거나 새 매핑 파일을 폴더에 추가 하면 닫은 후 다시 열어야 합니다 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가져오기 및 내보내기 마법사 또는 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 새롭거나 변경 된 파일이 인식 합니다.  
  
## <a name="external-resources"></a>외부 리소스  
  
-   비디오 [(SQL Server 비디오) Excel로 SQL Server 데이터 내보내기](http://go.microsoft.com/fwlink/?LinkID=200975), technet.microsoft.com  
  
-   CodePlex 샘플 [ODBC에서 사용 하 여 플랫 파일 마법사 내보내기 자습서: 단원 패키지](http://go.microsoft.com/fwlink/?LinkId=217657), msftisprodsamples.codeplex.com  
  
  
