---
title: "사용자 지정 어셈블리 배포 | Microsoft Docs"
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
- deploying custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], deploying
- custom assemblies [Reporting Services], updating
- updating custom assemblies
ms.assetid: c6674cd8-0de7-4a5a-9e7c-12ffa49f6fd2
caps.latest.revision: 46
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: bae986bea4e252d15bce495892e60c2a7e7d6064
ms.contentlocale: ko-kr
ms.lasthandoff: 06/13/2017

---
# <a name="deploying-a-custom-assembly"></a>사용자 지정 어셈블리 배포
  사용자 지정 어셈블리를 배포 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], 보고서 디자이너와 보고서 서버 응용 프로그램 폴더의 어셈블리 배치 합니다. 사용자 지정 어셈블리 기본적으로 부여 **실행** 에서 권한을 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]합니다. 사용자 지정 어셈블리에 권한을 부여 하려면 실행 권한 이상의 권한이 보고서 서버에 대 한 rssrvpolicy.config 구성 파일 및 보고서 디자이너 미리 보기 창에 대 한 rspreviewpolicy.config 구성 파일을 편집 하려면 해야 합니다. 또는 GAC(전역 어셈블리 캐시)에 사용자 지정 어셈블리를 설치할 수도 있습니다.  
  
> [!NOTE]  
>  두 개의 모드에 대 한 보고서 디자이너 미리 보기는: 보고서 프로젝트를 시작할 때 실행 되는 팝업 미리 보기 창과 미리 보기 탭 **DebugLocal** 모드입니다. 미리 보기 탭을 사용 하 여 모든 보고서 식을 실행는 **FullTrust** 사용 권한 설정 및 보안 정책 설정을 적용 하지 않습니다. 팝업 미리 보기 창은 보고서 서버 기능을 시뮬레이션하기 위한 것이므로 보고서 디자이너에서 사용자 지정 어셈블리를 사용하기 위해 작업자나 관리자가 수정해야 하는 정책 구성 파일을 포함합니다. 또한 이 팝업 미리 보기는 사용자 지정 어셈블리를 잠급니다. 따라서 사용자 지정 어셈블리 코드를 수정하거나 업데이트하려면 미리 보기 창을 닫아야 합니다.  
  
###### <a name="to-deploy-a-custom-assembly-in-reporting-services"></a>Reporting Services에서 사용자 지정 어셈블리를 배포하려면  
  
1.  사용자 지정 어셈블리를 빌드 위치에서 보고서 서버 bin 폴더 또는 보고서 디자이너 폴더에 복사합니다. 보고서 서버 bin 폴더의 기본 위치는 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin입니다. 보고서 디자이너의 기본 위치는 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies입니다.  
  
     사용자 지정 어셈블리를 보고서 서버의 bin 폴더에 배치하면 사용자 지정 어셈블리를 참조하는 보고서를 게시할 수 있고, 보고서 디자이너 폴더에 배치하면 보고서 디자이너의 사용자 지정 어셈블리를 참조하는 보고서를 실행하고 디버깅할 수 있습니다.  
  
     사용자 지정 어셈블리 코드에 기본 실행 권한 이상의 권한을 부여해야 하는 경우 다음을 수행합니다.  
  
2.  해당하는 구성 파일을 엽니다. rssrvpolicy.config의 기본 위치는 %ProgramFiles%\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer입니다. rspreviewpolicy.config의 기본 위치는 %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies입니다.  
  
3.  사용자 지정 어셈블리에 대한 코드 그룹을 추가합니다. 자세한 내용은 참조 [보안 개발 &#40; Reporting services&#41; ](../../reporting-services/extensions/secure-development/secure-development-reporting-services.md).  
  
## <a name="updating-custom-assemblies"></a>사용자 지정 어셈블리 업데이트  
 게시된 다수의 보고서에서 현재 참조하고 있는 사용자 지정 어셈블리의 버전을 어느 시점에 업데이트해야 할 수 있습니다. 해당하는 어셈블리가 보고서 서버의 bin 디렉터리나 보고서 디자이너에 이미 있으며 어셈블리의 버전 번호가 높아지거나 어떤 식으로든 변경되는 경우 현재 게시된 보고서는 더 이상 올바르게 작동하지 않습니다. 참조 되는 어셈블리의 버전을 업데이트 해야 합니다는 **CodeModules** 보고서 정의의 요소는 보고서를 다시 게시 합니다. 사용자 지정 어셈블리를 자주 업데이트할 예정이며 현재 게시된 보고서에서 새 어셈블리를 참조해야 하는 경우에는 특정 어셈블리의 모든 업데이트에서 동일한 버전 사용을 고려해야 할 수도 있습니다.  
  
 현재 게시된 보고서에서 새 버전의 어셈블리를 참조할 필요가 없는 경우 사용자 지정 어셈블리를 전역 어셈블리 캐시에 배포할 수 있습니다. 전역 어셈블리 캐시에서는 동일한 어셈블리의 여러 버전을 유지 관리할 수 있으므로 현재 보고서에서 이전 버전의 어셈블리를 참조하고 새로 게시된 보고서에서 업데이트된 어셈블리를 참조할 수 있습니다. 또 다른 방법은 이전 어셈블리에 대한 모든 요청이 새 어셈블리로 리디렉션되도록 보고서 서버의 바인딩 리디렉션을 설정하는 것입니다. 이 경우 보고서 서버 Web.config 파일 및 보고서 서버 ReportService.exe.config 파일을 수정해야 합니다. 항목은 다음과 같습니다.  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <bindingRedirect oldVersion="1.0.0.0"  
                             newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>참고 항목  
 [보고서에서 사용자 지정 어셈블리 사용](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)   
 [어셈블리 및 전역 어셈블리 캐시 사용](http://go.microsoft.com/fwlink/?LinkId=63912)  
  
  