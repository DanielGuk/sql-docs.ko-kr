---
title: 데이터베이스 엔진 서비스 시작 옵션 | Microsoft Docs
ms.custom: ''
ms.date: 11/23/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- single-user mode [SQL Server], startup option
- overriding default startup options
- minimal configuration mode [SQL Server], startup option
- default startup options
- temporarily override default startup options [SQL Server]
- startup options [SQL Server]
- starting SQL Server, options
- single-user mode [SQL Server], startup parameter
- overriding default startup parameters
- minimal configuration mode [SQL Server], startup parameter
- default startup parameters
- temporarily override default startup parameters [SQL Server]
- startup parameters [SQL Server]
- starting SQL Server, parameters
ms.assetid: d373298b-f6cf-458a-849d-7083ecb54ef5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1c9c330ab53b83eb46fa60002bc8aa6c0ed72e13
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52534672"
---
# <a name="database-engine-service-startup-options"></a>데이터베이스 엔진 서비스 시작 옵션
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  시작 옵션은 시작하는 동안 필요한 특정 파일 위치를 지정하고 일부 서버 차원의 조건을 지정합니다. 일반적으로 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에 문제가 발생하거나 예외적인 문제가 발생하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 고객 지원 서비스에서 시작 옵션을 사용하도록 지시하는 경우가 아니면 시작 옵션을 지정할 필요가 없습니다.  
  
> [!WARNING]  
>  시작 옵션을 잘못 사용하면 서버 성능에 영향을 주고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시작되지 않을 수 있습니다.  
>
>  "mssql" 사용자와 함께 Linux에서 SQL Server를 시작하여 향후 시작 문제를 방지합니다. 예: `sudo -u mssql /opt/mssql/bin/sqlservr [STARTUP OPTIONS]` 
  
## <a name="about-startup-options"></a>시작 옵션 정보  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 설치할 때 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 레지스트리에 기본 시작 옵션 집합이 기록됩니다. 이 시작 옵션을 사용하여 대체 master 데이터베이스 파일, master 데이터베이스 로그 파일 또는 오류 로그 파일 등을 지정할 수 있습니다. [!INCLUDE[ssDE](../../includes/ssde-md.md)] 에서 필요한 파일을 찾지 못하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 시작되지 않습니다.  
  
 시작 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 사용하여 설정할 수 있습니다. 자세한 내용은 [서버 시작 옵션 구성&#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)을 참조하세요.  
  
## <a name="list-of-startup-options"></a>시작 옵션 목록  
### <a name="default-startup-options"></a>기본 시작 옵션  
|Options|설명|  
|-----------------------------|-----------------|  
|**-d**  *master_file_path*|master 데이터베이스 파일의 정규화된 경로입니다. 일반적으로 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\master.mdf입니다. 이 옵션이 제공되지 않으면 기존의 레지스트리 매개 변수를 사용합니다.|  
|**-e** *error_log_path*|오류 로그 파일의 정규화된 경로입니다. 일반적으로 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\LOG\ERRORLOG입니다. 이 옵션이 제공되지 않으면 기존의 레지스트리 매개 변수를 사용합니다.|  
|**-l**  *master_log_path*|master 데이터베이스 로그 파일의 정규화된 경로입니다. 일반적으로 C:\Program Files\Microsoft SQL Server\MSSQL.*n*\MSSQL\Data\mastlog.ldf입니다. 이 옵션을 지정하지 않으면 기존의 레지스트리 매개 변수가 사용됩니다.|  
  
### <a name="other-startup-options"></a>다른 시작 옵션   
|Options |설명|   
|---------------------------|-----------------|  
|**-c**|명령 프롬프트에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작할 때 시작 시간을 단축시킵니다. 일반적으로 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 서비스 제어 관리자를 호출하여 서비스로 시작됩니다. [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 은 명령 프롬프트에서 시작하는 경우 서비스로 시작되지 않으므로 **-c** 를 사용하여 이 단계를 건너뛸 수 있습니다.|  
|**-f**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 최소 구성으로 시작합니다. 예를 들어 오버 커밋 메모리 같은 구성 값의 설정 때문에 서버를 시작할 수 없을 경우에 유용합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 최소 구성 모드로 시작하면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 단일 사용자 모드로 실행됩니다. 자세한 내용은 뒷부분에 나오는 **-m** 에 대한 설명을 참조하세요.|  
|**-g**  *memory_to_reserve*|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스 내 그리고 [max_server_memory](../../database-engine/configure-windows/server-memory-server-configuration-options.md) 서버 설정에 의해 설정된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 풀 외 범위에 메모리를 할당하기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]가 사용할 수 있는 메모리를 메가바이트(MB) 단위의 정수로 지정합니다. 메모리 풀 외부의 메모리는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 확장 프로시저 .dll 파일, 분산 쿼리에서 참조하는 OLE DB Provider 및 [!INCLUDE[tsql](../../includes/tsql-md.md)] 문에서 참조되는 자동화 개체 같은 항목을 로드하는 데 사용하는 영역입니다. 기본값은 256MB입니다.<br /><br /> 이 옵션을 사용하면 메모리 할당을 튜닝하는 데 도움이 될 수 있으나 실제 메모리가 운영 체제에서 애플리케이션에 사용할 수 있도록 구성된 가상 메모리 한계보다 큰 경우에만 사용할 수 있습니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 의 메모리 사용 요청이 불규칙하고 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 프로세스의 가상 주소 공간이 전부 사용되는 대량 메모리 구성에서 사용하는 것이 적합합니다. 이 옵션을 제대로 사용하지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 시작할 수 없거나 런타임 오류가 발생할 수도 있습니다.<br /><br /> **오류 로그에서 다음 경고가 표시되지 않으면** -g [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 매개 변수의 기본값을 사용해야 합니다.<br /> "실패한 가상 메모리 할당 바이트: FAIL_VIRTUAL_RESERVE \<크기>"<br /> "실패한 가상 메모리 할당 바이트: FAIL_VIRTUAL_COMMIT \<크기>"<br /><br /> 이 메시지에 따르면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 는 확장 저장 프로시저 .dll 파일이나 자동화 개체 등의 항목에 필요한 공간을 찾기 위해 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 메모리 풀의 일부를 없애려고 합니다. 이 경우 **-g** 스위치로 예약되는 메모리 양을 늘려 보세요.<br /><br /> 기본값보다 낮은 값을 사용하면 SQL Server Memory Manager 및 스레드 스택에서 관리하는 메모리 풀의 사용 가능한 메모리 양을 증가시켜 확장 저장 프로시저, 분산 쿼리, 자동화 개체 등을 사용하지 않는 시스템에서 메모리 집중형 작업에 대한 성능상의 이점을 제공할 수 있습니다.|  
|**-kDecimalNumber**| 이 시작 매개 변수는 초당 체크포인트 I/O 요청 수를 제한하며 **DecimalNumber**는 초당 체크포인트 속도(MB)를 나타냅니다.  이 값을 변경하면 백업 수행이나, 복구 프로세스 처리 속도에 영향을 미칠 수 있으므로 주의가 필요합니다. 이 시작 매개 변수에 대한 자세한 내용은 [-k 매개 변수](https://support.microsoft.com/en-us/help/929240/fix-i-o-requests-that-are-generated-by-the-checkpoint-process-may-caus)를 소개하는 핫픽스를 참조하세요.| 
|**-m**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스를 단일 사용자 모드로 시작하면 한 사용자만 연결할 수 있으며 CHECKPOINT 프로세스가 시작되지 않습니다. CHECKPOINT는 디스크 캐시에 있는 완료된 트랜잭션이 정기적으로 데이터베이스 디바이스에 기록되도록 합니다. 일반적으로 이 옵션은 복구해야 할 시스템 데이터베이스에 문제가 발생했을 때 사용합니다. sp_configure allow updates 옵션을 설정합니다. 기본적으로 allow updates는 사용할 수 없습니다. 단일 사용자 모드로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하면 컴퓨터에서 로컬 Administrators 그룹의 모든 멤버가 sysadmin 고정 서버 역할의 멤버로 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에 연결할 수 있습니다. 자세한 내용은 [시스템 관리자가 잠겨 있는 경우 SQL Server에 연결](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)을 참조하세요. 단일 사용자 모드에 대한 자세한 내용은 [단일 사용자 모드로 SQL Server 시작](../../database-engine/configure-windows/start-sql-server-in-single-user-mode.md)을 참조하세요.|  
|**-mClient Application Name**|지정된 클라이언트 애플리케이션에 대한 연결 수를 제한합니다. 예를 들어 `-mSQLCMD`  는 연결 수를 단일 연결로 제한하며 이 경우 연결은 스스로 SQLCMD 클라이언트 프로그램으로 인식해야 합니다. 단일 사용자 모드에서 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 를 시작하며 알 수 없는 클라이언트 애플리케이션에서 사용 가능한 유일한 연결을 사용할 경우 이 옵션을 사용합니다. SSMS 쿼리 편집기와 연결하려면 `"Microsoft SQL Server Management Studio - Query" ` 를 사용합니다. SSMS 쿼리 편집기 옵션은 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 구성 관리자 도구를 사용하여 구성할 수 없습니다. 도구에서 거부된 대시 문자가 포함되어 있기 때문입니다.<br /><br /> 클라이언트 애플리케이션 이름은 대/소문자를 구분합니다. 큰따옴표는 애플리케이션 이름에 공백이나 특수 문자가 포함되어 있는 경우 필요합니다.<br /><br />**명령줄에서 시작하는 예제:**<br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlserver -s MSSQLSERVER -m"Microsoft SQL Server Management Studio - Query"` <br /><br />`C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\sqlserver -s MSSQLSERVER -mSQLCMD` <br /><br /> **보안 정보:** 이 옵션을 보안 기능으로는 사용하지 마세요. 클라이언트 애플리케이션에서 클라이언트 애플리케이션 이름을 제공하므로 연결 문자열의 일부로 잘못된 이름을 제공할 수 있습니다.|  
|**-n**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트를 기록하는 데 Windows 응용 프로그램 로그를 사용하지 않습니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] -n **으로**인스턴스를 시작하는 경우 **-e** 시작 옵션도 사용하는 것이 좋습니다. 그렇지 않으면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 이벤트가 로깅되지 않습니다.|  
|**-s**|명명된 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]인스턴스를 시작할 수 있습니다. **-s** 매개 변수를 설정하지 않으면 기본 인스턴스가 시작을 시도합니다. **sqlservr.exe**를 시작하기 전에 명령 프롬프트에서 해당 인스턴스에 적합한 BINN 디렉터리로 전환해야 합니다. 예를 들어 Instance1이 이진 파일에 대해 `\mssql$Instance1`을 사용할 경우, 사용자는 `\mssql$Instance1\binn` 디렉터리에서 **sqlservr.exe -s instance1**을 시작해야 합니다.|  
|**-T**  *trace#*|지정된 추적 플래그( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace#*) 적용 시*인스턴스를 시작해야 함을 나타냅니다. 추적 플래그는 비표준 동작으로 서버를 시작하는 데 사용합니다. 자세한 내용은 [추적 플래그&#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)를 참조하세요.<br /><br /> **중요:** **-T** 옵션으로 추적 플래그를 지정할 때 추적 플래그 번호를 전달하려면 대문자 "T"를 입력합니다. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 소문자 "t"도 사용할 수 있지만 그럴 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 지원 엔지니어에게만 필요한 다른 내부 추적 플래그가 설정됩니다. 제어판 시작 창에서 지정한 매개 변수를 읽을 수 없습니다.|  
|**-x**|다음 모니터링 기능을 해제합니다.<br /> - [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 성능 모니터 카운터<br /> - CPU 시간과 캐시 적중률 통계 유지<br /> - DBCC SQLPERF 명령에 대한 정보 수집<br /> - 일부 동적 관리 뷰에 대한 정보 수집<br /> - 여러 확장 이벤트 이벤트 지점<br /><br /> **경고:** **–x** 시작 옵션을 사용할 경우 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 성능 및 기능 문제를 진단하는 데 사용할 수 있는 정보가 크게 줄어듭니다.|  
|**-E**|파일 그룹의 각 파일에 할당되는 익스텐트의 수를 늘립니다. 이 옵션은 인덱스 또는 데이터 검색을 실행하는 사용자 수가 제한되는 데이터 웨어하우스 애플리케이션에 유용합니다. 성능에 부정적인 영향을 줄 수 있으므로 다른 애플리케이션에서는 이 옵션을 사용하면 안 됩니다. 이 옵션은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]32비트 릴리스에서는 지원되지 않습니다.|  
  
## <a name="using-startup-options-for-troubleshooting"></a>문제 해결을 위한 시작 옵션 사용  
 단일 사용자 모드 및 최소 구성 모드와 같은 일부 시작 옵션은 주로 문제 해결에서 사용됩니다. sqlservr.exe를 수동으로 시작하는 동안 명령줄에서 **–m** 또는 **–f** 옵션을 사용하여 문제 해결을 위해 서버를 시작하면 가장 간단합니다.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] net start **를 사용하여**를 시작하는 경우에는 시작 옵션에 하이픈(-) 대신 슬래시(/)를 사용합니다.  
  
## <a name="using-startup-options-during-normal-operations"></a>정상적인 작업 중 시작 옵션 사용  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]를 시작할 때마다 사용하는 시작 옵션이 있을 수 있습니다. 이러한 옵션(예: **–g** 또는 추적 플래그로 시작)은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자를 통해 시작 매개 변수를 구성하면 가장 쉽게 설정할 수 있습니다. 이러한 도구는 시작 옵션을 레지스트리 키로 저장하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 가 항상 이 시작 옵션으로 시작할 수 있게 됩니다.  
  
## <a name="compatibility-support"></a>호환성 지원  
 **-h**  매개 변수는 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]에서 지원되지 않습니다. 이 매개 변수는 이전 버전 32비트 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스에서 AWE가 설정된 경우 Hot Add 메모리 메타데이터에 대해 가상 주소 공간을 예약하는 데 사용되었습니다. 자세한 내용은 [SQL Server 2016에서 지원되지 않는 SQL Server 기능](https://msdn.microsoft.com/library/0678bfbc-5d3f-44f4-89c0-13e8e52404da)을 참조하세요.  
  
## <a name="related-tasks"></a>관련 작업  
[scan for startup procs 서버 구성 옵션 구성](../../database-engine/configure-windows/configure-the-scan-for-startup-procs-server-configuration-option.md)  
[데이터베이스 엔진, SQL Server 에이전트 또는 SQL Server Browser 서비스 시작, 중지, 일시 중지, 재개 및 다시 시작](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)
[서버 시작 옵션 구성 &#40;SQL Server 구성 관리자&#41;](../../database-engine/configure-windows/scm-services-configure-server-startup-options.md)
  
## <a name="see-also"></a>참고 항목  
 [CHECKPOINT&#40;Transact-SQL&#41;](../../t-sql/language-elements/checkpoint-transact-sql.md)   
 [sqlservr 응용 프로그램](../../tools/sqlservr-application.md)  
  
  
