---
title: SQL Server Machine Learning 서비스 (R, Python, Java) linux 설치 | Microsoft Docs
description: 이 문서에서는 Red Hat 및 Ubuntu에서 SQL Server Machine Learning Services (R, Python, Java)를 설치 하는 방법을 설명 합니다.
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.date: 10/09/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: machine-learning
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 8433f705b41782c61950cb74f76f694d61cd548d
ms.sourcegitcommit: 485e4e05d88813d2a8bb8e7296dbd721d125f940
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49100454"
---
# <a name="install-sql-server-2019-machine-learning-services-r-python-java-on-linux"></a>SQL Server 2019 Machine Learning 서비스 (R, Python, Java) linux 설치

[SQL Server Machine Learning Services](../advanced-analytics/what-is-sql-server-machine-learning.md) 이 미리 보기 릴리스의 SQL Server 2019부터 Linux 운영 체제에서 실행 합니다. R 및 Python에 대 한 확장 프로그램을 학습 하는 컴퓨터 또는 Java 프로그래밍 확장을 설치 하려면이 문서의 단계를 수행 합니다. 

기계 학습 및 확장 프로그래밍는 데이터베이스 엔진에 추가 된 기능입니다. 수 있지만 [데이터베이스 엔진 및 Machine Learning 서비스를 동시에 설치](#install-all), 설치 및 추가 하기 전에 모든 문제를 해결할 수 있도록 먼저 SQL Server 데이터베이스 엔진을 구성 하는 것이 좋습니다 구성 요소입니다. 

SQL Server Linux 소스 리포지토리에서 R, Python 및 Java 확장 패키지 위치는입니다. 이미 구성한 경우 데이터베이스 엔진에 대 한 소스 리포지토리에 설치, mssql-mlservices 동일한 리포지토리 등록을 사용 하 여 패키지 설치 명령을 실행할 수 있습니다.

## <a name="prerequisites"></a>필수 구성 요소

+ Linux 운영 체제 여야 [SQL Server에서 지 원하는](sql-server-linux-release-notes-2019.md#supported-platforms), 온-프레미스에서 또는 Docker 컨테이너에서 실행 중입니다.

+ SQL Server 2019 데이터베이스 엔진 인스턴스가 있어야 합니다. 

   + [Red Hat Enterprise Linux(RHEL)](quickstart-install-connect-red-hat.md)

   + [SUSE Enterprise Linux Server](quickstart-install-connect-suse.md)

   + [Ubuntu](quickstart-install-connect-ubuntu.md)

+ R 이기 [Microsoft R Open](#mro) mssql mlsservices R 패키지에 대 한 합니다. 

<a name="mro"></a>

### <a name="microsoft-r-open-mro-installation"></a>Microsoft R Open (MRO) 설치

Microsoft의 기본 배포 R의 RevoScaleR, MicrosoftML, 및 Machine Learning 서비스를 사용 하 여 설치 된 다른 R 패키지를 사용 하 여 필수 구성 요소 이며

필요한 버전이 MRO 3.4.4를 보여 줍니다.

MRO를 설치 하려면 다음 두 가지 방법 중 하나를 선택 합니다.

+ MRAN에서 MRO tarball을 다운로드 하 고, 압축을 풉니다 install.sh 스크립트를 실행 합니다. 따르면 합니다 [MRAN에 대 한 설치 지침](https://mran.microsoft.com/releases/3.4.4) 이 방법을 사용 하려는 경우.

+ 또는 등록 된 **packages.microsoft.com** MRO 배포로 구성 된 세 개의 패키지를 설치 하려면 아래 설명 된 대로 리포지토리: microsoft r-오픈 mro, microsoft-r-오픈-mkl, 및 microsoft-r-오픈-foreachiterators 합니다. 

다음 명령을 제공 MRO 리포지토리를 등록 합니다. 등록 후, r 등과 같이 mssql-mlservices-mml-다른 R 패키지를 설치 하기 위한 명령이 하면 패키지 종속성으로 MRO 자동으로 포함 됩니다.

#### <a name="mro-on-ubuntu"></a>Ubuntu에서 MRO

```bash
# Install as root
sudo su

# Optionally, if your system does not have the https apt transport option
apt-get install apt-transport-https

# Add the **azure-cli** repo to your apt sources list
AZ_REPO=$(lsb_release -cs)

echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | sudo tee /etc/apt/sources.list.d/azure-cli.list

# Set the location of the package repo the "prod" directory containing the distribution.
# This example specifies 16.04. Replace with 14.04 if you want that version
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the repo
dpkg -i packages-microsoft-prod.deb
```

#### <a name="mro-on-rhel"></a>RHEL에서 MRO

```bash
# Import the Microsoft repository key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Create local `azure-cli` repository
sudo sh -c 'echo -e "[azure-cli]\nname=Azure CLI\nbaseurl=https://packages.microsoft.com/yumrepos/azure-cli\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/azure-cli.repo'

# Set the location of the package repo at the "prod" directory
# The following command is for version 7.x
# For 6.x, replace 7 with 6 to get that version
rpm -Uvh https://packages.microsoft.com/config/rhel/7/packages-microsoft-prod.rpm
```
#### <a name="mro-on-suse"></a>SUSE에서 MRO

```bash
# Install as root
sudo su

# Set the location of the package repo at the "prod" directory containing the distribution
# This example is for SLES12, the only supported version of SUSE in Machine Learning Server
zypper ar -f https://packages.microsoft.com/sles/12/prod packages-microsoft-com

# Update packages on your system:
zypper update
```

## <a name="package-list"></a>패키지 목록

인터넷에 연결 된 장치에서 패키지는 다운로드 되 고 각 운영 체제에 대 한 패키지 설치 관리자를 사용 하 여 데이터베이스 엔진 독립적으로 설치 합니다. 다음 표에서 사용 가능한 모든 패키지를 설명 하지만 인터넷에 연결 된 설치 하기만 하면 *하나의* R 또는 Python 패키지를 특정 기능 조합 합니다.

| 패키지 이름 | 에 적용 됩니다. | Description |
|--------------|----------|-------------|
|mssql-서버-확장성  | All | 확장성 프레임 워크를 R, Python 또는 Java 코드를 실행 하는 데 사용 합니다. |
|mssql-서버-확장성-java | Java | Java 실행 환경에 로드 하기 위한 Java 확장입니다. 추가 라이브러리 없거나 Java에 대 한 패키지 있습니다. |
| microsoft openmpi  | Python, R | Linux에서 병렬화 Revo * 라이브러리에서 사용 되는 인터페이스를 전달 하는 메시지입니다. |
| [microsoft-r-오픈 *](#mro) | R | R의 오픈 소스 배포는 세 가지 패키지로 구성 됩니다. |
| mssql-mlservices-python | Python | Anaconda 및 Python의 오픈 소스 배포 합니다. |
|mssql mlservices-mlm py  | Python | 전체 설치 합니다. Revoscalepy, microsoftml, 미리 학습 된 모델 이미지 기능화 (featurization) 및 텍스트 감정 분석을 위해 제공 합니다.| 
|mssql mlservices-mml py  | Python | 부분 설치 합니다. Revoscalepy를 microsoftml를 제공합니다. <br/>미리 학습 된 모델에서 제외 됩니다. | 
|mssql mlservices-패키지 py  | Python | 부분 설치 합니다. Revoscalepy를 제공합니다. <br/>미리 학습 된 모델과 microsoftml 제외합니다. | 
|mssql mlservices-mlm r  | R | 전체 설치 합니다. SqlRUtils RevoScaleR, MicrosoftML, olapR을 미리 학습 된 이미지 기능화 (featurization) 및 텍스트 감정 분석을 위해 모델을 제공 합니다.| 
|mssql mlservices-mml r  | R | 부분 설치 합니다. RevoScaleR, MicrosoftML, sqlRUtils olapR를 제공합니다. <br/>미리 학습 된 모델에서 제외 됩니다.  |
|mssql mlservices-패키지 r  | R | 부분 설치 합니다. RevoScaleR sqlRUtils, olapR를 제공합니다. <br/>미리 학습 된 모델과 MicrosoftML 제외합니다. | 

<a name="RHEL"></a>

## <a name="rhel-commands"></a>RHEL 명령

설치할 *하나* R 패키지 및 모든 *하나* Python 패키지 및 해당 기능을 원하는 경우 Java 합니다. 각 R 및 Python 패키지 번들 기능을 포함합니다. 필요한 기능 집합을 제공 하는 패키지를 선택 합니다. 종속 패키지를 자동으로 포함 됩니다.

> [!Tip]
> 실행 가능한 경우 `yum clean all` 설치 하기 전에 시스템에서 패키지를 새로 고쳐야 합니다.

### <a name="example-1----full-installation"></a>예제 1-전체 설치 

R 및 Python에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi 확장 (R, Python, Java) 기계 학습 라이브러리와 미리 학습 된 모델을 포함합니다. R 및 Python에 대 한 전체 및 최소 설치-미리 학습 된 모델-하지 않고 기계 학습 라이브러리와 같은 사이 것 대체할 `mssql-mlservices-mml-r-9.4.5*` 고 `mssql-mlservices-mml-py-9.4.5*` 대신 합니다.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-mlm-py-9.4.5*
sudo yum install mssql-mlservices-mlm-r-9.4.5* 
sudo yum install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>예제 2-최소 설치 

R 및 Python, Java 확장에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi core Revo * 라이브러리를 포함합니다. 미리 학습 된 모델 및 machine learning R 및 Python에 대 한 라이브러리를 제외 합니다. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo yum install mssql-mlservices-packages-py-9.4.5*
sudo yum install mssql-mlservices-packages-r-9.4.5*
sudo yum install mssql-server-extensibility-java
```

<a name="ubuntu"></a>

## <a name="ubuntu-commands"></a>Ubuntu 명령

설치할 *하나* R 패키지 및 모든 *하나* Python 패키지 및 해당 기능을 원하는 경우 Java 합니다. 각 R 및 Python 패키지 번들 기능을 포함합니다. 필요한 기능 집합을 제공 하는 패키지를 선택 합니다. 종속 패키지를 자동으로 포함 됩니다.

> [!Tip]
> 실행 가능한 경우 `apt-get update` 설치 하기 전에 시스템에서 패키지를 새로 고쳐야 합니다. 또한 Ubuntu의 docker 이미지 일부 https apt 전송 옵션이 없을 수 있습니다. 설치를 사용 하 여 `apt-get install apt-transport-https`입니다.

<!---
### Prerequisite for 18.04

Running mssql-mlservices R libraries on Ubuntu 18.04 requires **libpng12** from the Linux Kernel archives. This package is no longer included in the standard distribution and must be installed manually. To get this library, run the following commands:

```bash
wget https://mirrors.kernel.org/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.54-1ubuntu1_amd64.deb
dpkg -i libpng12-0_1.2.54-1ubuntu1_amd64.deb
```--->

### <a name="example-1----full-installation"></a>예제 1-전체 설치 

R 및 Python에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi 확장 (R, Python, Java) 기계 학습 라이브러리와 미리 학습 된 모델을 포함합니다. R 및 Python을 전체 사이의 최소 하려는 경우 설치-machine learning 라이브러리와 같은 미리 학습 된 모델-않고 대신 mssql mlservices-mml r 및 mssql mlservices-mml py 대신 합니다.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# There is no asterisk in this full install
sudo apt-get install mssql-mlservices-mlm-py 
sudo apt-get install mssql-mlservices-mlm-r 
sudo apt-get install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>예제 2-최소 설치 

R 및 Python, Java 확장에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi core Revo * 라이브러리를 포함합니다. 미리 학습 된 모델 및 machine learning R 및 Python에 대 한 라이브러리를 제외 합니다. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java
# No aasterisk
sudo apt-get install mssql-mlservices-packages-py
sudo apt-get install mssql-mlservices-packages-r
sudo apt-get install mssql-server-extensibility-java
```

<a name="suse"></a>

## <a name="suse-commands"></a>SUSE 명령

설치할 *하나* R 패키지 및 모든 *하나* Python 패키지 및 해당 기능을 원하는 경우 Java 합니다. 각 R 및 Python 패키지 번들 기능을 포함합니다. 필요한 기능 집합을 제공 하는 패키지를 선택 합니다. 종속 패키지를 자동으로 포함 됩니다. 

### <a name="example-1----full-installation"></a>예제 1-전체 설치 

R 및 Python에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi 확장 (R, Python, Java) 기계 학습 라이브러리와 미리 학습 된 모델을 포함합니다. R 및 Python에 대 한 전체 및 최소 설치-미리 학습 된 모델-하지 않고 기계 학습 라이브러리와 같은 사이 것 대체할 `mssql-mlservices-mml-r-9.4.5*` 고 `mssql-mlservices-mml-py-9.4.5*` 대신 합니다.

```bash
# Install as root or sudo
# Add everything (all R, Python, Java)
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-mlm-py-9.4.5*
sudo zypper install mssql-mlservices-mlm-r-9.4.5* 
sudo zypper install mssql-server-extensibility-java
```

### <a name="example-2---minimum-installation"></a>예제 2-최소 설치 

R 및 Python, Java 확장에 대 한 오픈 소스 R 및 Python 확장성 프레임 워크, microsoft-openmpi core Revo * 라이브러리를 포함합니다. 미리 학습 된 모델 및 machine learning R 및 Python에 대 한 라이브러리를 제외 합니다. 

```bash
# Install as root or sudo
# Minimum install of R, Python, Java extensions
# Be sure to include -9.4.5* in mlsservices package names
sudo zypper install mssql-mlservices-packages-py-9.4.5*
sudo zypper install mssql-mlservices-packages-r-9.4.5*
sudo zypper install mssql-server-extensibility-java
```

## <a name="post-install-config-required"></a>설치 후 구성 (필수)

추가 구성은 주로 통해 합니다 [mssql-conf 도구](sql-server-linux-configure-mssql-conf.md)합니다.


1. SQL Server 실행 패드 서비스를 실행 하는 데 mssql 사용자 계정을 추가 합니다.

  ```bash
  sudo /opt/mssql/bin/mssql-conf setup
  ```

2. 오픈 소스 R 및 Python에 대 한 사용권 계약에 동의 합니다. 이 작업을 수행 하는 방법은 여러 가지가 있습니다. 이전에 SQL Server 라이선스를 수락 하 고 추가 하는 R 또는 Python 확장 이제, 다음 명령은 다음과 같습니다. 해당 약관에 동의

  ```bash
  # Run as SUDO or root
  # Use set + EULA 
    sudo /opt/mssql/bin/mssql-conf set EULA accepteulaml Y
  ```

  대체 하는 워크플로 라이선스 계약 하는 SQL Server 데이터베이스 엔진, 아직 수락 하지 않은 경우 설치 검색 mssql mlservices 패키지 EULA 동의 하 라는 메시지가 표시 되 면 `mssql-conf setup` 실행 됩니다. EULA 매개 변수에 대 한 자세한 내용은 참조 하세요. [mssql-conf 도구를 사용 하 여 SQL Server 구성](sql-server-linux-configure-mssql-conf.md#mlservices-eula)합니다.

3. SQL Server 실행 패드 서비스와 데이터베이스 엔진 인스턴스를 다시 시작 합니다.

  ```bash
  systemctl restart mssql-launchpadd

  systemctl restart mssql-server.service
  ```

4. SQL Server Management Studio 또는 TRANSACT-SQL을 실행 하는 다른 도구에서 외부 스크립트 실행을 사용 하도록 설정 합니다. 

  ```bash
  EXEC sp_configure 'external scripts enabled', 1 
  RECONFIGURE WITH OVERRIDE 
  ```

## <a name="verify-installation"></a>설치 확인

(MicrosoftML, RevoScaleR 및 기타)의 R 라이브러리에서 찾을 수 있습니다 `/opt/mssql/mlservices/libraries/RServer`합니다.

Python 라이브러리 (microsoftml 및 revoscalepy)에서 찾을 수 있습니다 `/opt/mssql/mlservices/libraries/PythonServer`합니다.

SQL Server 쿼리 도구를 사용 하 여 SQL Server에서 R 실행을 테스트 하려면 다음 SQL 명령을 실행 합니다. 스크립트가 실행 되지 않으면 서비스를 다시 시작을 시도 `sudo systemctl restart mssql-server`합니다.

```r
EXEC sp_execute_external_script   
@language =N'R', 
@script=N' 
OutputDataSet <- InputDataSet', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```
 
SQL Server에서 Python 실행을 테스트 하려면 다음 SQL 명령을 실행 합니다. 
 
```python
EXEC sp_execute_external_script  
@language =N'Python', 
@script=N' 
OutputDataSet = InputDataSet; 
', 
@input_data_1 =N'SELECT 1 AS hello' 
WITH RESULT SETS (([hello] int not null)); 
GO 
```

<a name="install-all"></a>

## <a name="chained-installation"></a>연결 된 설치

설치 하 고 R, Python 또는 Java 패키지 및 데이터베이스 엔진을 설치 하는 명령에 매개 변수를 추가 하 여 프로시저 하나에서 데이터베이스 엔진 및 Machine Learning 서비스를 구성할 수 있습니다. 

다음 예제에서는 Yum 패키지 관리자를 사용 하 여 같은 결합 된 패키지 설치의 "템플릿" 보여 줍니다. 데이터베이스 엔진을 설치 하 고 확장성 프레임 워크 패키지를 종속성으로 끌어오는 Java 언어 확장을 추가 합니다.

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java 
```

모든 확장 프로그램 (Java, R, Python)를 사용 하 여 확장 된 예제는 다음과 같습니다.

```bash
sudo yum install -y mssql-server mssql-server-extensibility-java mssql-mlservices-packages-r-9.4.5* mssql-mlservices-packages-py-9.4.5*
```

R 필수 구성 요소를 제외 하 고 동일한 경로에서 찾을 모든 패키지를이 예제에서 사용 합니다. 에서는 R을 추가 하면 [열림-r microsoft 패키지 리포지토리를 등록](#mro) MRO 가져올 추가 단계로. MRO는 R 확장에 대 한 필수 구성 요소입니다. 인터넷에 연결 된 컴퓨터에서 MRO 검색 되어 자동으로 설치 R 확장의 일부로 두 리포지토리를 구성 하는 것으로 가정 합니다.

설치 후 전체 설치를 구성 하 고 사용권 계약 동의 하려면 mssql-conf 도구를 사용 해야 합니다. 오픈 소스 R 및 Python 구성 요소에 대해 허용 되지 않은 Eula 자동으로 감지 하 고 SQL Server에 대 한 EULA와 함께에 동의 하 라는 메시지가 표시 됩니다.

```bash
sudo /opt/mssql/bin/mssql-conf setup MSSQL_PID=Developer 
```

## <a name="unattended-installation"></a>무인된 설치

사용 하는 [무인된 설치](https://docs.microsoft.com/sql/linux/sql-server-linux-setup?view=sql-server-2017#unattended) 데이터베이스 엔진의 경우 mssql mlservices 및 Eula에 대 한 패키지를 추가 합니다.

설정 하거나 mssql-conf 도구 사용권 계약 동의 묻는 회수 합니다. 이미 SQL Server 데이터베이스 엔진을 구성 하 고 해당 EULA를 수락, 하는 경우 오픈 소스 R 및 Python 배포에 대 한 mlservices 별 EULA 매개 변수 중 하나를 사용 합니다.

```bash
sudo /opt/mssql/bin/mssql-conf setup accept-eula-ml
```

EULA 동의의 모든 가능한 순열에 설명 되어 있습니다 [mssql-conf 도구를 사용 하 여 Linux에서 SQL Server 구성](sql-server-linux-configure-mssql-conf.md#mlservices-eula)합니다.

## <a name="offline-installation"></a>오프라인 설치

수행 합니다 [오프 라인 설치](sql-server-linux-setup.md#offline) 에 패키지를 설치 하는 단계를 설명 합니다. 다운로드 사이트를 찾아 다음 아래 패키지 목록을 사용 하 여 특정 패키지를 다운로드 합니다.

> [!Tip]
> 패키지 종속성을 확인 하는 명령을 도움이 될 수 있는 다양 한 패키지 관리 도구를 제공 합니다. Yum을 사용 하 여 `sudo yum deplist [package]`입니다. Ubuntu를 사용 하 여 `sudo apt-get install --reinstall --download-only [package name]` 뒤에 `dpkg -I [package name].deb`입니다.


#### <a name="download-site"></a>다운로드 사이트

패키지를 다운로드할 수 있습니다 [ https://packages.microsoft.com/ ](https://packages.microsoft.com/)합니다. 모든 R, Python 및 Java에 대 한 mlservices 패키지는 데이터베이스 엔진 패키지와 함께 배치 합니다. 기본 mlservices 패키지 버전이 9.4.5 합니다. 오픈-micrososoft-r 패키지를 다른 폴더의 경우

#### <a name="rhel7-paths"></a>RHEL/7 경로

|||
|--|----|
| mssql/mlservices 패키지 | [https://packages.microsoft.com/rhel/7/mssql-server-preview/](https://packages.microsoft.com/rhel/7/mssql-server-preview/) |
| microsoft r 열린 패키지 | [https://packages.microsoft.com/rhel/7/prod/](https://packages.microsoft.com/rhel/7/prod/) | 


#### <a name="ubuntu1604-paths"></a>Ubuntu 16.04/경로

|||
|--|----|
| mssql/mlservices 패키지 | [https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/mssql-server-preview/pool/main/m/) |
| microsoft r 열린 패키지 | [https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/](https://packages.microsoft.com/ubuntu/16.04/prod/pool/main/m/) | 

#### <a name="sles12-paths"></a>SLES/12 경로

|||
|--|----|
| mssql/mlservices 패키지 | [ https://packages.microsoft.com/sles/12/mssql-server-preview/](https://packages.microsoft.com/sles/12/mssql-server-preview/) |
| microsoft r 열린 패키지 | [https://packages.microsoft.com/sles/12/prod/](https://packages.microsoft.com/sles/12/prod/) | 

#### <a name="package-list"></a>패키지 목록

확장 프로그램에 따라 사용 하 여, 특정 언어에 필요한 패키지를 다운로드 해야 합니다. 플랫폼 정보를 포함 하는 정확한 파일 이름 있지만 아래 파일 이름을 가까이 있는 파일을 결정할 수 있습니다.

```
# Core packages 
mssql-server-15.0.1000
mssql-server-extensibility-15.0.1000

# Java
mssql-server-extensibility-java-15.0.1000

# R
microsoft-openmpi-3.0.0
microsoft-r-open-foreachiterators-3.4.4
microsoft-r-open-mkl-3.4.4
microsoft-r-open-mro-3.4.4
mssql-mlservices-packages-r-9.4.5
mssql-mlservices-mlm-r-9.4.5
mssql-mlservices-mml-r-9.4.5

# Python
microsoft-openmpi-3.0.0
mssql-mlservices-python-9.4.5
mssql-mlservices-packages-py-9.4.5
mssql-mlservices-mlm-py-9.4.5
mssql-mlservices-mml-py-9.4.5 
```

## <a name="add-more-rpython-packages"></a>R/Python 패키지가 더 이상 표시를 추가 합니다. 
 
다른 R 및 Python 패키지를 설치 하 고 SQL Server 2019에 대해 실행 되는 스크립트에서 사용할 수 있습니다.

### <a name="r-packages"></a>R 패키지 
 
1. R 세션을 시작 합니다.

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R 
   ```

2. 호출 하는 R 패키지 설치 [붙이기](https://mran.microsoft.com/package/glue) 패키지 설치를 테스트 합니다.

   ```r
   # install.packages("glue",lib="/opt/mssql/mlservices/libraries/RServer") 
   ```
   또는 명령줄에서 R 패키지를 설치할 수 있습니다. 

   ```r
   # sudo /opt/mssql/mlservices/bin/R/R CMD INSTALL -l /opt/mssql/mlservices/libraries/RServer glue_1.1.1.tar.gz 
   ```

3. R 패키지를 가져올 [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)합니다.

   ```r
   EXEC sp_execute_external_script  
   @language = N'R', 
   @script = N'library(glue)' 
   ```

### <a name="python-packages"></a>Python 패키지 
 
1. 라는 Python 패키지 설치 [httpie](https://httpie.org/) pip를 사용 하 여 합니다. 

   ```python
   # sudo /opt/mssql/mlservices/bin/python/python -m pip install httpie 
   ``` 

2. Python 패키지에서 가져올 [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md)합니다.
 
   ```python
   EXEC sp_execute_external_script  
   @language = N'Python',  
   @script = N'import httpie' 
   ```

## <a name="limitations-in-ctp-20"></a>CTP 2.0의에서 제한 사항

이 CTP 릴리스에서 다음과 같은 제한이 있습니다.

+ 묵시적된 인증 현재 사용할 수 없는 경우 Linux에서 Machine Learning 서비스에서 이번에 데이터 또는 기타 리소스에 액세스 하는 진행 중인 R 또는 Python 스크립트에서 서버에 다시 연결할 수 없습니다. 

+ [CREATE EXTERNAL LIBRARY](../t-sql/statements/create-external-library-transact-sql.md) (R 패키지를 데이터베이스에 저장)를 현재 사용할 수 없습니다 linux 및 Python을 지원 하지 않습니다.  

### <a name="resource-governance"></a>리소스 거 버 넌 스

Linux 및 Windows에 대 한 사이 패리티가 [리소스 거 버 넌 스](../t-sql/statements/create-external-resource-pool-transact-sql.md) 외부 리소스 풀에 대 한 통계 [sys.dm_resource_governor_external_resource_pools](../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pools.md) 현재 Linux에서 서로 다른 단위입니다. 단위는 예정 된 CTP에 정렬 됩니다.
 
| 열 이름   | Description | Linux의 값 | 
|---------------|--------------|---------------|
|peak_memory_kb | 최대 리소스 풀에 사용 되는 메모리 양입니다. | Linux에서이 통계 값은 memory.max_usage_in_bytes CGroups 메모리 하위 시스템을에서 소싱 된 |
|write_io_count | 총 쓰기 Io 리소스 관리자 통계를 다시 설정한 후 실행 합니다. | Linux에서이 통계 CGroups blkio 하위 시스템 쓰기 행의 값은 blkio.throttle.io_serviced에서에서 소싱 된 | 
|read_io_count | 총 읽기 Io 리소스 관리자 통계를 다시 설정한 후 실행 합니다. | Linux에서이 통계는 읽기 행에 값 blkio.throttle.io_serviced 인 CGroups blkio 하위 시스템을에서 소싱 된 | 
|total_cpu_kernel_ms | 누적 CPU 사용자 커널 시간 리소스 관리자 통계를 다시 설정한 후 시간 (밀리초)입니다. | Linux에서이 통계 CGroups cpuacct 하위 시스템 사용자 행 값은 cpuacct.stat에서에서 소싱 된 |  
|total_cpu_user_ms | 리소스 관리자 통계를 다시 설정한 후 시간 (밀리초)의 누적 CPU 사용자 시간이 있습니다.| Linux에서이 통계 CGroups cpuacct 하위 시스템 시스템 행 값의 값은 cpuacct.stat에서에서 소싱 된 | 
|active_processes_count | 요청 시 실행 되는 외부 프로세스의 수입니다.| Linux에서이 통계 값은 pids.current GGroups pid 하위 시스템을에서 소싱 된 | 

## <a name="next-steps"></a>다음 단계

R 개발자가 몇 가지 간단한 예제를 사용 하 여 시작할 수 있습니다 및 SQL Server를 사용 하 여 R을 작동 하는 방법의 기본 사항을 알아봅니다. 다음 단계를 다음 링크를 참조 하세요.

+ [자습서: T-SQL에서 R 실행](../advanced-analytics/tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [자습서: R 개발자를 위한 데이터베이스 내 분석](../advanced-analytics/tutorials/sqldev-in-database-r-for-sql-developers.md)

Python 개발자는 이러한 자습서를 수행 하 여 SQL Server를 사용 하 여 Python을 사용 하는 방법을 배울 수 있습니다.

+ [자습서: t-sql로 Python 실행](../advanced-analytics/tutorials/run-python-using-t-sql.md)
+ [Python 개발자를 위한 자습서: 데이터베이스 내 분석](../advanced-analytics/tutorials/sqldev-in-database-python-for-sql-developers.md)

실제 시나리오를 기반으로 하는 기계 학습의 예제를 보려면 [기계 학습 자습서](../advanced-analytics/tutorials/machine-learning-services-tutorials.md)합니다.
