---
title: Azure Active Directory 인증을 사용하여 연결 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f699c97aee04bfe2c6f29789be6f34b673408e7
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401156"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Azure Active Directory 인증을 사용하여 연결

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

이 문서에서는 SQL Server 용 Microsoft JDBC Driver 6.0을 사용 하 여 (또는 이상)는 Azure Active Directory 인증 기능을 사용 하는 Java 응용 프로그램을 개발 하는 방법에 정보를 제공 합니다.

Azure SQL Database v12에 연결 하는 메커니즘인 Azure Active Directory (AAD) 인증을 사용할 수 있습니다 Azure Active Directory에서 id를 사용 합니다. Azure Active Directory 인증을 사용하여 중앙에서 데이터베이스 사용자의 ID를 관리하고 SQL Server 인증 대신 사용할 수 있습니다. JDBC 드라이버를 사용 하면 Azure SQL DB에 연결 하려면 JDBC 연결 문자열에 Azure Active Directory 자격 증명을 지정할 수 있습니다. Azure Active Directory 인증을 구성 하는 방법에 대 한 내용은 [SQL Database에서 사용 하 여 Azure Active Directory 인증을 연결할](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)합니다. 

Azure Active Directory 인증을 지원 하기 위해 두 개의 새로운 연결 속성이 추가 되었습니다.
*   **인증**:이 속성을 사용 하 여 연결에 사용할 SQL 인증 방법을 나타냅니다. 가능한 값은: **ActiveDirectoryIntegrated**를 **ActiveDirectoryPassword**합니다 **SqlPassword**, 및 기본 **NotSpecified**.
    * 사용 하 여 ' authentication = ActiveDirectoryIntegrated' 통합된 Windows 인증을 사용 하 여 SQL Database에 연결 합니다. 이 인증 모드를 사용 하는 온-프레미스 ADFS Active Directory Federation Services ()는 클라우드에서 AAD 사용 하 여 페더레이션 해야 합니다. Kerberos 티켓을 뿐만 아니라 설정 된이 되 면 도메인 가입된 컴퓨터에 로그인 하는 경우 자격 증명을 묻지 않고 Azure SQL DB를 액세스할 수 있습니다. 
    * 사용 하 여 ' authentication = ActiveDirectoryPassword' Azure AD 사용자 이름 및 암호를 사용 하 여 SQL Database에 연결.
    * 사용 하 여 ' authentication = SqlPassword' 사용자 이름/사용자 이름 및 암호 속성을 사용 하 여 SQL Server에 연결 합니다.
    * 사용 하 여 ' 인증 NotSpecified =' 하거나 이러한 인증 방법을 필요할 경우 기본값으로 둡니다.

*   **accessToken**:이 속성을 사용 하 여 액세스 토큰을 사용 하 여 SQL database에 연결 합니다. accessToken은 DriverManager 클래스의 getconnection () 메서드의 속성 매개 변수를 사용 하 여 서만 설정할 수 있습니다. 연결 URL에 사용할 수 없습니다.  

자세한 내용은 인증 속성에 참조를 [연결 속성 설정](../../connect/jdbc/setting-the-connection-properties.md) 페이지입니다.  


## <a name="client-setup-requirements"></a>클라이언트 설치 요구 사항
다음 구성 요소가 클라이언트 컴퓨터에 설치 되어 있는지 확인 하세요.
* Java 7 이상
*   Microsoft JDBC Driver 6.0 (또는 이상) for SQL Server
*   액세스 토큰 기반 인증 모드를 사용 하는 경우 [azure-activedirectory-라이브러리-에-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) 및 해당 종속성이이 문서에서 예제를 실행 합니다. 자세한 내용은 **액세스 토큰을 사용 하 여 연결** 섹션입니다.
*   ActiveDirectoryPassword 인증 모드를 사용 하는 경우 [azure-activedirectory-라이브러리-에-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) 및 해당 종속성입니다. 자세한 내용은 **ActiveDirectoryPassword 인증 모드를 사용 하 여 연결** 섹션입니다.
*   ActiveDirectoryIntegrated 모드를 사용 하는 경우 azure-activedirectory-라이브러리-에-java 및 종속 하는 것이 해야 합니다. 자세한 내용은 **ActiveDirectoryIntegrated 인증 모드를 사용 하 여 연결** 섹션입니다.
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>ActiveDirectoryIntegrated 인증 모드를 사용 하 여 연결
 버전 6.4, Microsoft JDBC Driver에는 여러 플랫폼 (Windows/Linux 및 Mac)에서 Kerberos 티켓을 사용 하 여 ActiveDirectoryIntegrated 인증에 대 한 지원이 추가 되었습니다.
자세한 내용은 [Windows, Linux 및 Mac에서 설정 하는 Kerberos 티켓](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac) 대 한 자세한 내용은 합니다. 또는 Windows를에 sqljdbc_auth.dll JDBC 드라이버를 사용 하 여 ActiveDirectoryIntegrated 인증용 데도 수 있습니다.

> [!NOTE]
>  이전 버전의 드라이버를 사용 하는 경우이 확인 [링크](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md) 이 인증 모드를 사용 하는 데 필요한 각 종속성에 대 한 합니다. 

다음 예제에서는 사용 하는 방법 ' authentication = ActiveDirectoryIntegrated' 모드입니다. Azure Active Directory와 페더레이션된 도메인 가입된 컴퓨터에서이 예제를 실행 합니다. 에 Azure AD 사용자 또는 그룹 중 하나를 나타내는 포함 된 데이터베이스 사용자 속한, 데이터베이스에 있어야 하 CONNECT 권한이 있어야 합니다. 

클라이언트 컴퓨터에서 예제를 실행 하기 전에 (에 예제를 실행 하려는)를 다운로드 합니다 [azure-activedirectory-라이브러리-에-java 라이브러리](https://github.com/AzureAD/azure-activedirectory-library-for-java) 및 해당 종속성을 Java 빌드 경로에 포함

서버/데이터베이스 이름을 예를 실행 하기 전에 다음 줄에서 사용자 서버/데이터베이스의 이름을 바꿉니다.

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

ActiveDirectoryIntegrated 인증 모드를 사용 하는 예제는:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADIntegrated {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Kerberos 티켓을 사용 하 여 클라이언트 컴퓨터에서이 예제를 자동으로 실행 되며 암호가 필요 합니다. 연결이 설정 되는 경우 다음과 같은 메시지가 표시 됩니다.
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Windows, Linux 및 Mac에서 Kerberos 티켓을 설정 합니다.

Windows 도메인 계정에 현재 사용자를 연결 하는 Kerberos 티켓을 설정 해야 합니다. 주요 단계 요약이 아래 포함 되어 있습니다.

#### <a name="windows"></a>Windows
JDK가 함께 `kinit`, 로그온 TGT 키 배포 센터 (KDC)에서 도메인을 사용할 수 있는 Azure Active Directory와 페더레이션 되는 컴퓨터를 가입 합니다.

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>1 단계: 티켓 부여 티켓 검색
- **실행**: Windows
- **작업**:
  - 명령을 사용 하 여 `kinit username@DOMAIN.COMPANY.COM` TGT는 KDC에서 가져오려는 다음 라는 메시지가 나타납니다. 도메인 암호입니다.
  - 사용 하 여 `klist` 보려면 티켓을 사용할 수 있습니다. Kinit를 성공적으로 수행 되었으면 krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM에서에서 티켓을 표시 됩니다.

> [!NOTE]
>  지정 해야 할 수도 있습니다는 `.ini` 파일을 `-Djava.security.krb5.conf` KDC 찾을 응용 프로그램에 대 한 합니다.

#### <a name="linux-and-mac"></a>Linux 및 Mac

##### <a name="requirements"></a>요구 사항
Kerberos 도메인 컨트롤러를 쿼리 하는 Windows 도메인에 가입 된 컴퓨터에 액세스 합니다.

##### <a name="step-1-find-kerberos-kdc"></a>1 단계: Kerberos KDC를 찾기
- **실행**: Windows 명령줄
- **동작**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (여기서 "DOMAIN.COMPANY.COM" 매핑 도메인의 이름으로)
- **샘플 출력**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **정보를 추출할** DC 이름,이 경우 `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>2 단계: krb5.conf에서 KDC를 구성합니다.
- **실행**: Linux/Mac
- **작업**: 원하는 편집기에서 /etc/krb5.conf를 편집 합니다. 다음 키 구성
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  그런 다음, krb5.conf 파일 및 종료

> [!NOTE]
>  도메인 모두 대문자 여야 합니다.

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>3 단계: 테스트 티켓 부여 티켓 검색
- **실행**: Linux/Mac
- **작업**:
  - 명령을 사용 하 여 `kinit username@DOMAIN.COMPANY.COM` TGT는 KDC에서 가져오려는 다음 라는 메시지가 나타납니다. 도메인 암호입니다.
  - 사용 하 여 `klist` 보려면 티켓을 사용할 수 있습니다. Kinit를 성공적으로 수행 되었으면 krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM에서에서 티켓을 표시 됩니다.

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>ActiveDirectoryPassword 인증 모드를 사용 하 여 연결
다음 예제에서는 사용 하는 방법 ' authentication = ActiveDirectoryPassword' 모드입니다.

전에 빌드 및 예제를 실행 합니다.
1.  클라이언트 컴퓨터에 (에 예제를 실행 하려는)를 다운로드 합니다 [azure-activedirectory-라이브러리-에-java 라이브러리](https://github.com/AzureAD/azure-activedirectory-library-for-java) 및 해당 종속성을 Java 빌드 경로에 포함
2.  코드의 다음 줄을 찾습니다 하 고 서버/데이터베이스 이름에 서버/데이터베이스 이름으로 바꿉니다.
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  코드의 다음 줄을 찾습니다 하 고 사용자 이름으로 연결 하려면 AAD 사용자의 이름으로 바꿉니다.
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

ActiveDirectoryPassword 인증 모드를 사용 하는 예제는:
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADUserPassword {
    
    public static void main(String[] args) throws Exception{
        
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
연결을 설정할 경우 출력으로 다음과 같은 메시지가 표시 됩니다.
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> 포함 된 사용자 데이터베이스 존재 해야 합니다 및 포함된 된 데이터베이스 사용자를 나타내는 지정 된 Azure AD 사용자 또는 그룹을 지정 된 Azure AD 사용자에 속하는, 데이터베이스에 존재 해야 하며 (제외: Azure Active Directory CONNECT 권한이 있어야 합니다. 서버 관리자 또는 그룹)

## <a name="connecting-using-access-token"></a>액세스 토큰을 사용 하 여 연결
응용 프로그램/서비스는 Azure Active Directory에서 액세스 토큰을 검색 하 고는 사용 하 여 SQL Azure 데이터베이스에 연결할 수 있습니다.

> [!NOTE] 
> **accessToken** DriverManager 클래스의 getconnection () 메서드의 속성 매개 변수를 사용 하 여 설정할 수만 있습니다. 연결 문자열에 사용할 수 없습니다.

아래 예제에서는 액세스 토큰 기반 인증을 사용 하 여 Azure SQL Database에 연결 하는 간단한 Java 응용 프로그램을 포함 합니다. 을 빌드하고 예제를 실행 하기 전에 다음 단계를 수행 합니다.
1.  서비스에 대 한 Azure Active Directory에서 응용 프로그램 계정을 만듭니다.
    1. Azure Portal에 로그인합니다.
    2. Azure Active Directory 왼쪽 탐색 창에서 클릭 합니다.
    3. "앱 등록" 탭을 클릭 합니다.
    4. 서랍에서 "새 응용 프로그램 등록"을 클릭 합니다.
    5. Mytokentest 응용 프로그램에 대 한 친숙 한 이름으로 입력 하 고 "웹 앱/API"를 선택 합니다.
    6. 로그온 URL 필요 하지 않습니다. 아무 것도 제공할: "https://mytokentest" 입니다.
    7. 맨 아래에서 "만들기"를 클릭 합니다.
    9. Azure portal에서 계속 하는 동안 응용 프로그램의 "설정" 탭을 클릭 하 고 "속성" 탭을 엽니다.
    10. "응용 프로그램 ID" (즉, 클라이언트 ID) 값을 찾아 복사 제외 하 고, 나중에 필요 (예를 들어 1846943b-ad04-4808-aa13-4702d908b5c1) 응용 프로그램을 구성 하는 경우. 다음 스냅숏을 참조 합니다.
    11. [키] 섹션에서 이름 필드에 입력 키의 기간을 선택 하 고 (값 필드를 비워 두십시오) 구성을 저장 하 여 키를 만듭니다. 값 필드 해야 저장 한 후 생성 된 값을 복사를 자동으로 입력 합니다. 클라이언트 비밀입니다.
    12. 왼쪽 패널에 Azure Active Directory를 클릭 합니다. "앱 등록"에서 "끝점" 탭을 찾습니다. 이 STS URL를 "OATH 2.0 토큰 끝점"에서 URL을 복사 합니다.
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Azure Active Directory 관리자 및 사용자 응용 프로그램에 대 한 포함된 된 데이터베이스 사용자는 T-SQL 명령 프로 비전을 사용 하 여 Azure SQL 서버의 사용자 데이터베이스에 로그인 합니다. 자세한 내용은 참조는 [SQL Database 또는 SQL Data Warehouse에서 사용 하 여 Azure Active Directory 인증에 연결](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/) 포함 된 데이터베이스 사용자와 Azure Active Directory 관리자를 만드는 방법에 대 한 자세한 내용은 합니다.

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  클라이언트 컴퓨터에 (에 예제를 실행 하려는)를 다운로드 합니다 [azure-activedirectory-라이브러리-에-java](https://github.com/AzureAD/azure-activedirectory-library-for-java) 라이브러리 및 해당 종속성을 Java 빌드 경로에 포함. 이 특정 예제를 실행 하려면 azure-activedirectory-라이브러리-에-java만 필요 하다는 참고 합니다. 이 예제에서는이 라이브러리에서 Api를 사용 하 여 Azure AAD에서 액세스 토큰을 검색. 액세스 토큰을 이미 있는 경우이 단계를 건너뛸 수 있습니다. 액세스 토큰을 검색 하는 예제에서 섹션을 제거 해야 하는 참고 합니다.

다음 예의 값을 사용 하 여 STS URL, 클라이언트 ID, 클라이언트 암호, 서버 및 데이터베이스 이름을 바꿉니다.

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD.
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;

public class AADTokenBased {

    public static void main(String[] args) throws Exception {

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);

        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {

            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

연결이 성공 하면 출력으로 다음과 같은 메시지가 표시 됩니다.
```java
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
