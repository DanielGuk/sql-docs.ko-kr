---
title: SQL Server 2017 및 2019에 대 한 Linux 리포지토리 구성 | Microsoft Docs
description: 확인 하 고 SQL Server 2019 및 Linux의 SQL Server 2017에 대 한 소스 리포지토리를 구성 합니다. 소스 리포지토리에 설치 및 업그레이드 하는 동안 적용 되는 SQL Server의 버전에 적용 됩니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 02/14/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 9b5d9e27db92ba048f0b6400c00313e81a1899f7
ms.sourcegitcommit: a2be75158491535c9a59583c51890e3457dc75d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51269448"
---
# <a name="configure-repositories-for-installing-and-upgrading-sql-server-on-linux"></a>설치 및 Linux의 SQL Server 업그레이드에 대 한 리포지토리 구성

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

이 문서에서는 Linux의 SQL Server 2017 및 SQL Server 2019 설치 및 업그레이드에 대 한 올바른 저장소를 구성 하는 방법을 설명 합니다.

> [!TIP]
> SQL Server 2019 preview 출시 되었습니다! 해를 사용 하 여이 문서에서는 새로운 **mssql-서버-미리 보기** 리포지토리. 다음의 지침을 사용 하 여를 설치 합니다 [설치 가이드](sql-server-linux-setup.md)합니다.

## <a id="repositories"></a>저장소

Linux의 SQL Server를 설치할 때 Microsoft 리포지토리를 구성 해야 합니다. 이 리포지토리는 데이터베이스 엔진 패키지를 얻는 데 **mssql server**, 및 관련 SQL Server 패키지 있습니다. 현재 세 가지 주요 리포지토리는:

| 리포지토리 | 이름 | Description |
|---|---|---|
| **미리 보기 (2017)** | **mssql-server** | SQL Server 2017 CTP 및 RC 리포지토리 (중단). |
| **미리 보기 (2019)** | **mssql-서버-미리 보기** | SQL Server 2019 미리 보기 및 RC 리포지토리입니다. |
| **CU** | **mssql-server-2017** | SQL Server 2017 CU (누적 업데이트) 리포지토리. |
| **GDR** | **mssql-server-2017-gdr** | 중요 업데이트의 경우에 SQL Server 2017 GDR 리포지토리. |

## <a id="cuversusgdr"></a> GDR 및 누적 업데이트

두 가지 유형인 각 배포 리포지토리는 두는 것이 반드시 합니다.

- **누적 업데이트 (CU)**: The CU (누적 업데이트) 리포지토리에 해당 릴리스 이후 기본 SQL Server 릴리스 및 버그 수정 또는 향상 된 기능에 대 한 패키지를 포함 합니다. 누적 업데이트 등 SQL Server 2017의 버전에 적용 됩니다. 이러한 일반 주기로 릴리스됩니다.

- **GDR**: The GDR 리포지토리에 해당 릴리스 이후 기본 SQL Server 릴리스 및만 중요 한 수정 사항 및 보안 업데이트 패키지를 포함 합니다. 이러한 업데이트는 다음 CU 릴리스에 추가 됩니다.

각 CU는 하며 GDR 릴리스는 전체 SQL Server 패키지 및 해당 저장소에 대 한 모든 이전 업데이트를 포함합니다. CU 릴리스에 GDR 릴리스에서 업데이트는 SQL Server에 대 한 구성된 리포지토리를 변경 하 여 지원 됩니다. 할 수도 있습니다 [다운 그레이드](sql-server-linux-setup.md#rollback) 주요 버전 내에서 모든 릴리스를 (예: 2017)입니다.

> [!NOTE]
> CU로 GDR 버전에서 업데이트할 수 있습니다 리포지토리를 변경 하 여 언제 든 지 릴리스 합니다. 업데이트를 CU에서 릴리스에서 GDR 릴리스로 지원 되지 않습니다. 

## <a id="configure"></a> 리포지토리 구성

다음 섹션에서는 다음과 같은 지원 되는 플랫폼에 대 한 리포지토리를 구성 하 고 확인 하는 방법을 설명 합니다.

- [Red Hat Enterprise Server](#rhel)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#sles)

## <a id="rhel"></a> RHEL 리포지토리 구성
Red Hat Enterprise Server (RHEL) 리포지토리를 구성 하려면 다음 단계를 사용 합니다.

### <a name="check-for-previously-configured-repositories-rhel"></a>이전에 구성한 리포지토리 (RHEL)에 대 한 확인
먼저 SQL Server 리포지토리에 이미 등록 여부를 확인 합니다.

1. 파일을 확인 합니다 **/etc/yum.repos.d** 다음 명령을 사용 하 여 디렉터리:

   ```bash
   sudo ls /etc/yum.repos.d
   ```

2. 와 같은 SQL Server 디렉터리를 구성 하는 파일을 찾습니다 **mssql server.repo**합니다.

3. 파일의 내용을 출력 합니다.

   ```bash
   sudo cat /etc/yum.repos.d/mssql-server.repo
   ```

4. 합니다 **이름을** 속성이 구성 된 저장소입니다. 테이블을 사용 하 여 식별할 수 있습니다 합니다 [리포지토리](#repositories) 이 문서의 섹션입니다.

### <a name="remove-old-repository-rhel"></a>이전 리포지토리 (RHEL)를 제거 합니다.
필요한 경우 다음 명령 사용 하 여 이전 저장소를 제거 합니다.

```bash
sudo rm -rf /etc/yum.repos.d/mssql-server.repo
```

이 명령은 이전 섹션에서 식별 된 파일 이름이 있는지 가정 **mssql server.repo**합니다.

### <a name="configure-new-repository-rhel"></a>새 리포지토리 (RHEL) 구성
SQL Server 설치 및 업그레이드를 위해 사용 하는 새 저장소를 구성 합니다. 선택한 리포지토리를 구성 하려면 다음 명령 중 하나를 사용 합니다.

| 리포지토리 | 버전 | Command |
|---|---|---|
| **미리 보기 (2019)** | 2019 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo curl -o /etc/yum.repos.d/mssql-server.repo https://packages.microsoft.com/config/rhel/7/mssql-server-2017-gdr.repo` |

## <a id="sles"></a> SLES 리포지토리 구성
SLES에서 리포지토리를 구성 하려면 다음 단계를 사용 합니다.

### <a name="check-for-previously-configured-repositories-sles"></a>이전에 구성한 리포지토리 (SLES)에 대 한 확인
먼저 SQL Server 리포지토리에 이미 등록 여부를 확인 합니다.

1. 사용 하 여 **zypper 정보** 이전에 구성 된 모든 리포지토리 정보를 가져옵니다.

   ```bash
   sudo zypper info mssql-server
   ```

2. 합니다 **리포지토리** 속성이 구성 된 저장소입니다. 테이블을 사용 하 여 식별할 수 있습니다 합니다 [리포지토리](#repositories) 이 문서의 섹션입니다.

### <a name="remove-old-repository-sles"></a>이전 리포지토리 (SLES)를 제거 합니다.
필요한 경우 이전 저장소를 제거 합니다. 이전에 구성 된 저장소의 유형에 따라 다음 명령 중 하나를 사용 합니다.

| 리포지토리 | 제거할 명령 |
|---|---|
| **미리 보기 (2017)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server'` |
| **미리 보기 (2019)** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-preview'` |
| **CU** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017'` |
| **GDR** | `sudo zypper removerepo 'packages-microsoft-com-mssql-server-2017-gdr'`|

### <a name="configure-new-repository-sles"></a>새 리포지토리 (SLES) 구성
SQL Server 설치 및 업그레이드를 위해 사용 하는 새 저장소를 구성 합니다. 선택한 리포지토리를 구성 하려면 다음 명령 중 하나를 사용 합니다.

| 리포지토리 | 버전 | Command |
|---|---|---|
| **미리 보기 (2019)** | 2019 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-preview.repo` |
| **CU** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo` |
| **GDR** | 2017 | `sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017-gdr.repo` |

## <a id="ubuntu"></a> Ubuntu 리포지토리 구성
Ubuntu에서 리포지토리를 구성 하려면 다음 단계를 사용 합니다.

### <a name="check-for-previously-configured-repositories-ubuntu"></a>이전에 구성한 리포지토리 (Ubuntu)에 대 한 확인
먼저 SQL Server 리포지토리에 이미 등록 여부를 확인 합니다.

1. 내용을 확인 합니다 **/etc/apt/sources.list** 파일입니다.

   ```bash
   sudo cat /etc/apt/sources.list
   ```

2. Mssql server에 대 한 패키지 URL을 검사 합니다. 테이블을 사용 하 여 식별할 수 있습니다 합니다 [리포지토리](#repositories) 이 문서의 섹션입니다.

### <a name="remove-old-repository-ubuntu"></a>이전 리포지토리 (Ubuntu)를 제거 합니다.
필요한 경우 이전 저장소를 제거 합니다. 이전에 구성 된 저장소의 유형에 따라 다음 명령 중 하나를 사용 합니다.

| 리포지토리 | 제거할 명령 |
|---|---|
| **미리 보기 (2017)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server xenial main'` |
| **미리 보기 (2019)** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview xenial main'` |
| **CU** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017 xenial main'` | 
| **GDR** | `sudo add-apt-repository -r 'deb [arch=amd64] https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr xenial main'` |

### <a name="configure-new-repository-ubuntu"></a>새 리포지토리 (Ubuntu) 구성
SQL Server 설치 및 업그레이드를 위해 사용 하는 새 저장소를 구성 합니다.

1. 공용 리포지토리 GPG 키를 가져옵니다.

   ```bash
   sudo curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
   ```

2. 선택한 리포지토리를 구성 하려면 다음 명령 중 하나를 사용 합니다.

   | 리포지토리 | 버전 | Command |
   |---|---|---|
   | **미리 보기 (2019)** | 2019 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-preview.list)"` |
   | **CU** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017.list)"` |
   | **GDR** | 2017 | `sudo add-apt-repository "$(curl https://packages.microsoft.com/config/ubuntu/16.04/mssql-server-2017-gdr.list)"` |

3. 실행할 **apt get 업데이트**합니다.

   ```bash
   sudo apt-get update
   ```

## <a name="next-steps"></a>다음 단계

올바른 저장소를 구성한 후 진행할 수 있습니다 [설치](sql-server-linux-setup.md#platforms) 하거나 [업데이트](sql-server-linux-setup.md#upgrade) 새 저장소에서 SQL Server 및 모든 관련 패키지 있습니다.

> [!IMPORTANT]
> 와 같은 설치 문서 중 하나를 사용 하려는 경우이 시점 합니다 [퀵 스타트](sql-server-linux-setup.md#platforms), 대상 리포지토리에 이미 구성한 기억 합니다. 이 자습서에서는 해당 단계를 반복 하지 않습니다. 퀵 스타트 CU 리포지토리를 사용 하기 때문에 이것이 GDR 리포지토리를 구성 하는 경우에 특히 그렇습니다.

Linux의 SQL Server 2017을 설치 하는 방법에 대 한 자세한 내용은 참조 하세요. [Linux의 SQL Server에 대 한 설치 지침은](sql-server-linux-setup.md)합니다.
