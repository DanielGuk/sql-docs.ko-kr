---
title: ".NET Framework 데이터 공급자와 Always Encrypted를 사용하여 개발 | Microsoft 문서"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-security
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 827e509e-3c4f-4820-aa37-cebf0f7bbf80
caps.latest.revision: 11
author: stevestein
ms.author: sstein
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 09253894ace06e9bd0b6a515e133eb8e2f5860a1
ms.lasthandoff: 04/11/2017

---
# <a name="develop-using-always-encrypted-with-net-framework-data-provider"></a>.NET Framework 데이터 공급자와 Always Encrypted를 사용하여 개발
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

이 문서는 [상시 암호화](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) 및 [.NET Framework Data Provider for SQL Server](https://msdn.microsoft.com/library/kb9s9ks0(v=vs.110).aspx)를 사용하여 .NET 응용 프로그램을 개발하는 방법에 대한 정보를 제공합니다.

Always Encrypted를 사용하면 클라이언트 응용 프로그램이 중요한 데이터를 암호화하고 해당 데이터 또는 암호화 키를 SQL Server 또는 Azure SQL Database에 표시하지 않을 수 있습니다. .NET Framework Data Provider for SQL Server 등의 상시 암호화 지원 드라이버는 클라이언트 응용 프로그램의 중요한 데이터를 투명하게 암호화하고 암호 해독합니다. 이 드라이버는 중요 데이터베이스 열에 해당하는 쿼리 매개 변수를 자동으로 확인하고(Always Encrypted를 사용하여 보호) 데이터를 SQL Server 또는 Azure SQL Database로 전달하기 전에 이러한 매개 변수의 값을 암호화합니다. 마찬가지로, 이 드라이버는 쿼리 결과의 암호화된 데이터베이스 열에서 검색한 데이터의 암호를 투명하게 해독합니다. 자세한 내용은 [상시 암호화(데이터베이스 엔진)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)를 참조하세요.


## <a name="prerequisites"></a>필수 구성 요소

- 데이터베이스에서 상시 암호화를 구성합니다. 상시 암호화를 구성하려면 상시 암호화 키를 프로비전하고 선택한 데이터베이스 열에 대한 암호화를 설정해야 합니다. 데이터베이스에 상시 암호화가 구성되지 않은 경우 [상시 암호화 시작](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_5)의 지침을 따르세요.
- 개발 컴퓨터에 .NET Framework 버전 4.6 이상이 설치되어 있는지 확인합니다. 자세한 내용은 [.NET Framework 4.6](https://msdn.microsoft.com/library/w0x726c2(v=vs.110).aspx)을 참조하세요. 또한 개발 환경에서 .NET Framework 버전 4.6 이상이 대상 .NET Framework 버전으로 구성되어 있는지 확인해야 합니다. Visual Studio를 사용하는 경우 [방법:.NET Framework 버전 대상 지정](https://msdn.microsoft.com/library/bb398202.aspx)을 참조하세요. 

> [!NOTE]
> 특히 .NET Framework의 버전에 따라 상시 암호화에 대한 지원 수준이 달라집니다. 자세한 내용은 아래의 상시 암호화 API 참조 섹션을 참조하세요. 

## <a name="enabling-always-encrypted-for-application-queries"></a>응용 프로그램 쿼리에 대해 Always Encrypted 사용
매개 변수 암호화를 설정하고 암호화된 열을 대상으로 하는 쿼리 결과의 암호를 해독하는 가장 쉬운 방법은 열 암호화 설정 연결 문자열 키워드 값을 **enabled**로 설정하는 것입니다.

다음은 상시 암호화를 사용하는 연결 문자열의 예제입니다.
```
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
SqlConnection connection = new SqlConnection(connectionString);
```

다음은 SqlConnectionStringBuilder.ColumnEncryptionSetting 속성을 사용하는 예제입니다.

```
SqlConnectionStringBuilder strbldr = new SqlConnectionStringBuilder();
strbldr.DataSource = "server63";
strbldr.InitialCatalog = "Clinic";
strbldr.IntegratedSecurity = true;
strbldr.ColumnEncryptionSetting = SqlConnectionColumnEncryptionSetting.Enabled;
SqlConnection connection = new SqlConnection(strbldr.ConnectionString);
```

상시 암호화는 개별 쿼리에도 사용할 수 있습니다. 아래의 **상시 암호화의 성능 영향 제어** 섹션을 참조하세요.
암호화 또는 암호 해독을 위해 상시 암호화를 사용하는 것은 적절하지 않습니다. 다음을 확인해야 합니다.
- 응용 프로그램에는 *VIEW ANY COLUMN MASTER KEY DEFINITION* 및 *VIEW ANY COLUMN ENCRYPTION KEY DEFINITION* 데이터베이스 권한이 있으며 데이터베이스에서 상시 암호화 키에 대한 메타데이터에 액세스하는 데 필요합니다. 자세한 내용은 [상시 암호화의 권한 섹션(데이터베이스 엔진)](https://msdn.microsoft.com/library/mt163865.aspx#Anchor_7)을 참조하세요.
- 응용 프로그램은 열 암호화 키를 보호하는 열 마스터 키에 액세스하여 쿼리된 데이터베이스 열을 암호화할 수 있습니다.

## <a name="retrieving-and-modifying-data-in-encrypted-columns"></a>암호화된 열에서 데이터 검색 및 수정

응용 프로그램 쿼리에 대해 상시 암호화를 설정하면 [System.Data.SqlClient Namespace](https://msdn.microsoft.com/library/ms254937(v=vs.110).aspx)에 정의된 표준 ADO.NET API( [ADO.NET에서 데이터 검색 및 수정](https://msdn.microsoft.com/library/kb9s9ks0(v=vs.110).aspx) 참조) 또는 [.NET Framework Data Provider for SQL Server](https://msdn.microsoft.com/library/system.data.sqlclient.aspx)API를 사용하여 암호화된 데이터베이스 열에서 데이터를 검색하거나 수정할 수 있습니다. 응용 프로그램에 필요한 데이터베이스 권한이 있고 열 마스터 키에 액세스할 수 있는 경우 데이터베이스 스키마의 열에 설정된 SQL Server 데이터 형식에 따라 .NET Framework Data Provider for SQL Server에서 암호화된 열을 대상으로 하는 쿼리 매개 변수를 암호화하고 .NET 형식의 일반 텍스트 값을 반환하는 암호화된 열에서 검색된 데이터의 암호를 해독합니다.
상시 암호화를 사용하지 않는 경우 암호화된 열을 대상으로 하는 매개 변수가 있는 쿼리가 실패합니다. 쿼리에 암호화된 열을 대상으로 하는 매개 변수가 없는 경우 쿼리가 암호화된 열에서 데이터를 검색할 수 있습니다. 그러나 .NET Framework Data Provider for SQL Server는 암호화된 열에서 검색된 값을 해독하지 않고 응용 프로그램에서 암호화된 이진 데이터(바이트 배열)를 수신합니다.

아래 표에서는 상시 암호화 사용 여부에 따른 쿼리 동작을 요약합니다.

|쿼리 특성 | 상시 암호화가 설정되고 응용 프로그램에서 키 및 키 메타데이터에 액세스할 수 있는 경우|상시 암호화가 설정되고 응용 프로그램에서 키 또는 키 메타데이터에 액세스할 수 없는 경우 | 상시 암호화를 사용하지 않는 경우|
|:---|:---|:---|:---|
| 암호화된 열을 대상으로 하는 매개 변수가 있는 쿼리 | 매개 변수 값이 투명하게 암호화됩니다. | 오류 | 오류|
| 암호화된 열에서 데이터를 검색하는데, 암호화된 열을 대상으로 하는 매개 변수가 없는 쿼리| 암호화된 열의 결과가 투명하게 암호 해독됩니다. 응용 프로그램에서 암호화된 열에 대해 구성된 SQL Server 형식에 해당하는 .NET 데이터 형식의 일반 텍스트 값을 수신합니다. | 오류 | 암호화된 열의 결과가 암호 해독되지 않습니다. 응용 프로그램에서 암호화된 값을 바이트 배열(byte[])로 수신합니다. 

다음 예제에는 암호화된 열에서 데이터를 검색 및 수정하는 방법을 설명합니다. 이 예제에서는 대상 테이블에 아래의 스키마가 있다고 가정합니다. SSN 및 BirthDate 열은 암호화되어 있습니다.


```
CREATE TABLE [dbo].[Patients]([PatientId] [int] IDENTITY(1,1), 
 [SSN] [char](11) COLLATE Latin1_General_BIN2 
 ENCRYPTED WITH (ENCRYPTION_TYPE = DETERMINISTIC, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL,
 [FirstName] [nvarchar](50) NULL,
 [LastName] [nvarchar](50) NULL, 
 [BirthDate] [date] 
 ENCRYPTED WITH (ENCRYPTION_TYPE = RANDOMIZED, 
 ALGORITHM = 'AEAD_AES_256_CBC_HMAC_SHA_256', 
 COLUMN_ENCRYPTION_KEY = CEK1) NOT NULL
 PRIMARY KEY CLUSTERED ([PatientId] ASC) ON [PRIMARY])
 GO
```

### <a name="inserting-data-example"></a>데이터 예제 삽입

이 예제에서는 Patients 테이블에 행을 삽입합니다. 다음에 유의하세요.
- 샘플 코드에는 암호화에 대한 내용이 없습니다. .NET Framework Data Provider for SQL Server에서는 암호화된 열을 대상으로 하는 *paramSSN* 및 *paramBirthdate* 매개 변수를 자동으로 검색하고 암호화합니다. 이렇게 하면 응용 프로그램에 투명하게 암호화할 수 있습니다. 
- 암호화된 열을 포함하여 데이터베이스 열에 삽입된 값은 [SqlParameter](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.aspx) 개체로 전달됩니다. **SqlParameter** 를 사용하여 암호화되지 않은 열에 값을 전달하는 것은 선택 사항이지만(그러나 SQL 삽입을 방지할 수 있으므로 매우 권장됨) 암호화된 열을 대상으로 하는 값에 필요합니다. SSN 또는 BirthDate 열에 삽입된 값이 쿼리 문에 포함된 리터럴로 전달된 경우 .NET Framework Data Provider for SQL Server에서 암호화된 대상 열의 값을 확인할 수 없어 값을 암호화하지 않으므로 쿼리가 실패합니다. 결과적으로, 암호화된 열과 호환 불가능한 것으로 간주하여 서버에서 거부합니다.
- SSN 열을 대상으로 하는 매개 변수의 데이터 형식은 ANSI(비 유니코드) 문자열이며 char/varchar SQL Server 데이터 형식에 매핑됩니다. 매개 변수 형식이 유니코드 문자열(String)로 설정되어 nchar/nvarchar에 매핑되는 경우 상시 암호화가 암호화된 nchar/nvarchar 값을 암호화된 char/varchar 값으로 변환하는 것을 지원하지 않으므로 쿼리가 실패합니다. 데이터 형식 매핑에 대한 자세한 내용은 [SQL Server 데이터 형식 매핑](https://msdn.microsoft.com/library/cc716729.aspx) 을 참조하세요.
- BirthDate 열에 삽입되는 매개 변수의 데이터 형식은 [SqlParameter.DbType 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.sqldbtype.aspx)을 사용할 때 적용되는 SQL Server 데이터 형식으로 .NET 형식을 암시적으로 매핑하지 않고 [SqlParameter.SqlDbType 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.dbtype.aspx)을 사용하여 명시적으로 대상 SQL Server 데이터 형식으로 설정됩니다. 기본적으로 [DateTime 구조체](https://msdn.microsoft.com/library/system.datetime.aspx) 는 SQL Server 데이터 형식 datetime에 매핑됩니다. BirthDate 열의 데이터 형식이 date이고 상시 암호화는 암호화된 datetime 값을 암호화된 date 값으로 변환하는 것을 지원하지 않으므로 기본 매핑 시 오류가 발생합니다. 

```
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
using (SqlConnection connection = new SqlConnection(strbldr.ConnectionString))
{
   using (SqlCommand cmd = connection.CreateCommand())
   {
      cmd.CommandText = @"INSERT INTO [dbo].[Patients] ([SSN], [FirstName], [LastName], [BirthDate]) VALUES (@SSN, @FirstName, @LastName, @BirthDate);";

      SqlParameter paramSSN = cmd.CreateParameter();
      paramSSN.ParameterName = @"@SSN";
      paramSSN.DbType = DbType.AnsiStringFixedLength;
      paramSSN.Direction = ParameterDirection.Input;
      paramSSN.Value = "795-73-9838";
      paramSSN.Size = 11;
      cmd.Parameters.Add(paramSSN);

      SqlParameter paramFirstName = cmd.CreateParameter();
      paramFirstName.ParameterName = @"@FirstName";
      paramFirstName.DbType = DbType.String;
      paramFirstName.Direction = ParameterDirection.Input;
      paramFirstName.Value = "Catherine";
      paramFirstName.Size = 50;
      cmd.Parameters.Add(paramFirstName);

      SqlParameter paramLastName = cmd.CreateParameter();
      paramLastName.ParameterName = @"@LastName";
      paramLastName.DbType = DbType.String;
      paramLastName.Direction = ParameterDirection.Input;
      paramLastName.Value = "Abel";
      paramLastName.Size = 50;
      cmd.Parameters.Add(paramLastName);

      SqlParameter paramBirthdate = cmd.CreateParameter();
      paramBirthdate.ParameterName = @"@BirthDate";
      paramBirthdate.SqlDbType = SqlDbType.Date;
      paramBirthdate.Direction = ParameterDirection.Input;
      paramBirthdate.Value = new DateTime(1996, 09, 10);
      cmd.Parameters.Add(paramBirthdate);

      cmd.ExecuteNonQuery();
   } 
}
```

### <a name="retrieving-plaintext-data-example"></a>일반 텍스트 데이터 검색 예제

다음 예제에서는 암호화된 값을 기준으로 데이터를 필터링하고 암호화된 열에서 일반 텍스트 데이터를 검색하는 방법을 보여 줍니다. 다음에 유의하세요.
- SSN 열에서 필터링하기 위해 WHERE 절에 사용된 값을 SqlParameter를 사용하여 전달해야 합니다. 그러므로 .NET Framework Data Provider for SQL Server는 데이터베이스로 전달하기 전에 이 값을 투명하게 암호화할 수 있습니다.
- .NET Framework Data Provider for SQL Server가 SSN 및 BirthDate 열에서 검색한 데이터의 암호를 투명하게 해독하므로 프로그램에서 인쇄되는 모든 값은 일반 텍스트입니다.


> [!NOTE]
> 결정적 암호화를 사용하여 암호화된 경우 쿼리에서 열에 대해 동등 비교를 수행할 수 있습니다. 자세한 내용은 *상시 암호화(데이터베이스 엔진)* 의 [결정적 또는 임의 암호화 선택](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)섹션을 참조하세요.

```
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true; Column Encryption Setting=enabled";
    
using (SqlConnection connection = new SqlConnection(strbldr.ConnectionString))
 {
    using (SqlCommand cmd = connection.CreateCommand())
 {

 cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN=@SSN";
 SqlParameter paramSSN = cmd.CreateParameter();
 paramSSN.ParameterName = @"@SSN";
 paramSSN.DbType = DbType.AnsiStringFixedLength;
 paramSSN.Direction = ParameterDirection.Input;
 paramSSN.Value = "795-73-9838";
 paramSSN.Size = 11;
 cmd.Parameters.Add(paramSSN);
 using (SqlDataReader reader = cmd.ExecuteReader())
 {
   if (reader.HasRows)
 {
 while (reader.Read())
 {
    Console.WriteLine(@"{0}, {1}, {2}, {3}", reader[0], reader[1], reader[2], ((DateTime)reader[3]).ToShortDateString());
 }
```

### <a name="retrieving-encrypted-data-example"></a>암호화된 데이터 검색 예제

상시 암호화를 사용하지 않는 경우에도 쿼리에 암호화된 열을 대상으로 하는 매개 변수가 없으면 암호화된 열에서 데이터를 검색할 수 있습니다.

다음 예제에서는 암호화된 열에서 암호화된 이진 데이터를 검색하는 방법을 보여 줍니다. 다음에 유의하세요.

- 연결 문자열에서는 상시 암호화를 사용하지 않으므로 쿼리에서 SSN 및 BirthDate의 암호화된 값을 바이트 배열로 반환합니다(프로그램에서 값을 문자열로 변환).
- 암호화된 열을 대상으로 하는 매개 변수가 없으면 상시 암호화를 사용하지 않고 암호화된 열에서 데이터를 검색하는 쿼리에 매개 변수가 있을 수 있습니다. 위의 쿼리는 LastName을 기준으로 필터링되며 데이터베이스에서 암호화되지 않습니다. 쿼리가 SSN 또는 BirthDate를 기준으로 필터링되면 쿼리가 실패합니다.


```
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
                
using (SqlConnection connection = new SqlConnection(connectionString))
{
   connection.Open();
   using (SqlCommand cmd = connection.CreateCommand())
   {
      cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName]=@LastName";
      SqlParameter paramLastName = cmd.CreateParameter();
      paramLastName.ParameterName = @"@LastName";
      paramLastName.DbType = DbType.String;
      paramLastName.Direction = ParameterDirection.Input;
      paramLastName.Value = "Abel";
      paramLastName.Size = 50;
      cmd.Parameters.Add(paramLastName);
      using (SqlDataReader reader = cmd.ExecuteReader())
      {
         if (reader.HasRows)
         {
            while (reader.Read())
         {
         Console.WriteLine(@"{0}, {1}, {2}, {3}", BitConverter.ToString((byte[])reader[0]), reader[1], reader[2], BitConverter.ToString((byte[])reader[3]));
      }
   }
}
```

### <a name="avoiding-common-problems-when-querying-encrypted-columns"></a>암호화된 열 쿼리 시 일반적인 문제 방지

이 섹션에서는 .NET 응용 프로그램에서 암호화된 열을 쿼리할 때 발생하는 일반적인 오류 범주와 이를 방지하는 방법을 설명합니다.

### <a name="unsupported-data-type-conversion-errors"></a>지원되지 않는 데이터 형식 변환 오류

상시 암호화는 암호화된 데이터 형식에 대해 몇 가지 변환을 지원합니다. 지원되는 형식 변환의 자세한 목록은 [Always Encrypted(데이터베이스 엔진)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md) 를 참조하세요. 데이터 형식 변환 오류를 방지하려면 다음을 수행합니다.

- 매개 변수의 SQL Server 데이터 형식이 대상 열의 형식과 동일하도록 암호화된 열을 대상으로 하는 매개 변수의 형식을 설정합니다. 그렇지 않으면 매개 변수의 SQL Server 데이터 형식을 열의 대상 형식으로 변환할 수 없습니다. SqlParameter.SqlDbType 속성을 사용하면 .NET 데이터 형식을 특정 SQL Server 데이터 형식으로 매핑할 수 있습니다.
- SQL Server 데이터 형식이 decimal 및 numeric인 열을 대상으로 하는 매개 변수의 정밀도 및 배율이 대상 열에 대해 구성된 정밀도 및 배율과 동일한지 확인합니다.  
- 대상 열의 값을 수정하는 쿼리에서 SQL Server 데이터 형식이 datetime2, datetimeoffset 또는 time인 열을 대상으로 하는 매개 변수의 정밀도가 대상 열의 정밀도보다 크지 않은지 확인합니다.  

### <a name="errors-due-to-passing-plaintext-instead-of-encrypted-values"></a>암호화된 값 대신 일반 텍스트를 전달하여 발생하는 오류

암호화된 열을 대상으로 하는 모든 값은 응용 프로그램 내에서 암호화해야 합니다. 암호화된 열에서 삽입/수정하거나 일반 텍스트 값을 기준으로 필터링하면 다음과 같은 오류가 발생합니다.


```
System.Data.SqlClient.SqlException (0x80131904): Operand type clash: varchar is incompatible with varchar(8000) encrypted with (encryption_type = 'DETERMINISTIC', encryption_algorithm_name = 'AEAD_AES_256_CBC_HMAC_SHA_256', column_encryption_key_name = 'CEK_Auto1', column_encryption_key_database_name = 'Clinic') collation_name = 'SQL_Latin1_General_CP1_CI_AS'
```

이러한 오류를 방지하려면 다음을 확인합니다.
- 암호화된 열을 대상으로 하는 응용 프로그램 쿼리에 대해 Always Encrypted가 설정되어 있어야 합니다(특정 쿼리에 대한 [SqlCommand](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommand.aspx) 개체 또는 연결 문자열).
- SqlParameter를 사용하여 암호화된 열을 대상으로 하는 데이터를 전송합니다. 다음 예제에서는 SqlParameter 개체에 리터럴을 전달하지 않고 암호화된 열(SSN)에서 리터럴/상수를 기준으로 잘못 필터링한 쿼리를 보여 줍니다. 


```
using (SqlCommand cmd = connection.CreateCommand())
{
   cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE SSN='795-73-9838'";
cmd.ExecuteNonQuery();
}
```

## <a name="working-with-column-master-key-stores"></a>열 마스터 키 저장소 작업

매개 변수 값을 암호화하거나 쿼리 결과의 데이터 암호를 해독하려면 대상 열에 대해 구성된 열 암호화 키가 .NET Framework Data Provider for SQL Server에 있어야 합니다. 열 암호화 키는 데이터베이스 메타데이터에 암호화된 형태로 저장됩니다. 각 열 암호화 키에는 열 암호화 키를 암호화하는 데 사용된 해당 열 마스터 키가 있습니다. 데이터베이스 메타데이터에는 열 마스터 키가 저장되지 않습니다. 특정 열 마스터 키가 포함된 키 저장소와 키 저장소에서의 키 위치에 대한 정보만 저장됩니다.

열 암호화 키의 일반 텍스트 값을 가져오려면 .NET Framework Data Provider for SQL Server에서 먼저 열 암호화 키와 해당 열 마스터 키에 대한 메타데이터를 가져온 다음 메타데이터에서 이 정보를 사용하여 열 마스터 키가 포함된 키 저장소에 연결하고 암호화된 열 암호화 키의 암호를 해독합니다. .NET Framework Data Provider for SQL Server는 열 마스터 키 저장소 공급자를 사용하여 키 저장소와 통신합니다. 열 마스터 키 저장소 공급자는 [SqlColumnEncryptionKeyStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptionkeystoreprovider.aspx)클래스에서 파생된 클래스 인스턴스입니다.


열 암호화 키를 받는 프로세스는 다음과 같습니다.

1.    Always Encrypted가 쿼리에 대해 사용하도록 설정된 경우 .NET Framework Data Provider for SQL Server는 쿼리에 매개 변수가 있으면 매개 변수 대상이 암호화된 열에 대한 암호화 메타데이터를 검색하도록 **sys.sp_describe_parameter_encryption** 을 호출합니다. 쿼리 결과에 암호화된 데이터가 포함된 경우 SQL Server는 암호화 메타데이터를 자동으로 연결합니다. 열 마스터 키 정보에는 다음이 포함됩니다.
    - 열 마스터 키를 포함하는 키 저장소를 캡슐화하는 키 저장소 공급자의 이름. 
    - 키 저장소에서 열 마스터 키의 위치를 지정하는 키 경로.
    
    열 암호화 키 정보에는 다음이 포함됩니다.

    - 열 암호화 키의 암호화된 값.
    - 열 암호화 키를 암호화하는 데 사용된 알고리즘의 이름
2.    .NET Framework Data Provider for SQL Server는 열 마스터 키 저장소 공급자 이름을 사용하여 내부 데이터 구조에서 공급자 개체(SqlColumnEncryptionKeyStoreProvider 클래스에서 파생된 클래스 인스턴스)를 조회합니다.
3.    열 암호화 키를 해독하기 위해.NET Framework Data Provider for SQL Server는 암호화된 열 암호화 키를 생성하는 데 사용된 열 마스터 키 경로, 열 암호화 키의 암호화된 값 및 암호화 알고리즘 이름을 통과하여 SqlColumnEncryptionKeyStoreProvider.DecryptColumnEncryptionKey 메서드를 호출합니다.




### <a name="using-built-in-column-master-key-store-providers"></a>기본 제공 열 마스터 키 저장소 공급자 사용

.NET Framework Data Provider for SQL Server에는 다음 열 마스터 키 저장소 공급자가 기본 제공되며 특정 공급자 이름이 미리 등록되어 있습니다(공급자 조회에 사용).


| 클래스 | 설명 | 공급자 (조회) 이름 |
|:---|:---|:---|
|SqlColumnEncryptionCertificateStoreProvider 클래스| Windows 인증서 저장소에 대한 공급자입니다. | MSSQL_CERTIFICATE_STORE |
|[SqlColumnEncryptionCngProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx) <br><br>**참고:** 이 공급자는 .NET Framework 4.6.1 이상 버전에서 사용할 수 있습니다. |[Microsoft 암호화 API: 차세대(CNG) API](https://msdn.microsoft.com/library/windows/desktop/aa376210.aspx)를 지원하는 키 저장소 공급자입니다. 일반적으로 이 저장소의 형식은 하드웨어 보안 모듈로서, 디지털 키를 보호 및 관리하고 암호화 프로세스를 제공하는 물리적 장치입니다.  | MSSQL_CNG_STORE|
| [SqlColumnEncryptionCspProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx)<br><br>**참고:** 이 공급자는 .NET Framework 4.6.1 이상 버전에서 사용할 수 있습니다.| [Microsoft CAPI(암호화 API)](https://msdn.microsoft.com/library/aa266944.aspx)를 지원하는 키 저장소 공급자입니다. 일반적으로 이 저장소의 형식은 하드웨어 보안 모듈로서, 디지털 키를 보호 및 관리하고 암호화 프로세스를 제공하는 물리적 장치입니다.| MSSQL_CSP_PROVIDER |
  
이러한 공급자를 사용하기 위해 응용 프로그램 코드를 변경할 필요는 없지만 다음에 유의하세요.

- 사용자 또는 DBA는 열 마스터 키 메타데이터에 구성된 공급자 이름이 정확하고 열 마스터 키 경로가 특정 공급자에 대해 적합한 키 경로 형식을 준수해야 합니다. [CREATE COLUMN MASTER KEY(Transact-SQL)](https://msdn.microsoft.com/library/mt146393.aspx) 문을 실행할 때 적합한 공급자 이름 및 키 경로를 자동으로 생성하는 SQL Server Management Studio 등의 도구를 사용하여 키를 구성하는 것이 좋습니다. 자세한 내용은 [SQL Server Management Studio를 사용하여 Always Encrypted 구성](../../../relational-databases/security/encryption/configure-always-encrypted-using-sql-server-management-studio.md) 및 [PowerShell을 사용하여 Always Encrypted 구성](../../../relational-databases/security/encryption/configure-always-encrypted-using-powershell.md)을 참조하세요.
- 응용 프로그램에서 키 저장소의 키에 액세스할 수 있어야 합니다. 이는 키 저장소를 기준으로 응용 프로그램 액세스를 키 및/또는 키 저장소에 부여하거나 다른 키 저장소 관련 구성 단계를 수행하는 것과 관련이 있습니다. 예를 들어 CNG 또는 CAPI(예: 하드웨어 보안 모듈)를 구현하는 키 저장소에 액세스하려면 저장소에 대한 CNG 또는 CAPI를 구현하는 라이브러리가 응용 프로그램에 설치되었는지 확인해야 합니다. 자세한 내용은 [열 마스터 키 만들기 및 저장(상시 암호화)](../../../relational-databases/security/encryption/create-and-store-column-master-keys-always-encrypted.md)를 참조하세요.

### <a name="using-azure-key-vault-provider"></a>Azure Key Vault 공급자 사용

Azure 주요 자격 증명 모음은 상시 암호화에 대한 열 마스터 키를 저장 및 관리하는 편리한 옵션입니다(특히 응용 프로그램이 Azure에서 호스트되는 경우). .NET Framework Data Provider for SQL Server에서는 Azure 주요 자격 증명 모음용 열 마스터 키 저장소 공급자가 기본 제공되지 않지만 Nuget 패키지로 사용할 수 있으므로 응용 프로그램과 쉽게 통합할 수 있습니다. 자세한 내용은 [상시 암호화 - 데이터 암호화를 사용하여 SQL 데이터베이스의 중요 데이터를 보호하고 Azure 주요 자격 증명 모음에 암호화 키 저장](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted-azure-key-vault/)을 참조하세요.

### <a name="implementing-a-custom-column-master-key-store-provider"></a>사용자 지정 열 마스터 키 저장소 공급자 구현

기존 공급자에서 지원하지 않는 열 마스터 키를 키 저장소에 저장하려는 경우 [SqlColumnEncryptionCngProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx) 를 확장하고 [SqlConnection.RegisterColumnEncryptionKeyStoreProviders](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.registercolumnencryptionkeystoreproviders.aspx) 메서드를 사용하여 공급자를 등록하여 사용자 지정 공급자를 구현할 수 있습니다.


```
public class MyCustomKeyStoreProvider : SqlColumnEncryptionKeyStoreProvider
    {
        public override byte[] EncryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] columnEncryptionKey)
        {
            // Logic for encrypting a column encrypted key.
        }
        public override byte[] DecryptColumnEncryptionKey(string masterKeyPath, string encryptionAlgorithm, byte[] EncryptedColumnEncryptionKey)
        {
            // Logic for decrypting a column encrypted key.
        }
    }  
    class Program
    {
        static void Main(string[] args)
        {
            Dictionary\<string, SqlColumnEncryptionKeyStoreProvider> providers =
               new Dictionary\<string, SqlColumnEncryptionKeyStoreProvider>();
            providers.Add("MY_CUSTOM_STORE", customProvider);
            SqlConnection.RegisterColumnEncryptionKeyStoreProviders(providers);
            providers.Add(SqlColumnEncryptionCertificateStoreProvider.ProviderName, customProvider);
            SqlConnection.RegisterColumnEncryptionKeyStoreProviders(providers); 
       // ...
        }

    }
```
 
### <a name="using-column-master-key-store-providers-for-programmatic-key-provisioning"></a>열 마스터 키 저장소 공급자를 사용하여 프로그래밍 방식으로 키 프로비전

암호화된 열에 액세스할 때 .NET Framework Data Provider for SQL Server는 올바른 열 마스터 키 저장소를 투명하게 찾고 호출하여 열 암호화 키의 암호를 해독합니다. 일반적으로 정상적인 응용 프로그램 코드는 열 마스터 키 저장소 공급자를 직접 호출하지 않습니다. 그러나 명시적으로 공급자를 시작 및 호출하여 프로그래밍 방식으로 상시 암호화 키를 프로비전 및 관리하고, 암호화된 열 암호화 키를 생성하고, 열 암호화 키의 암호를 해독할 수 있습니다(예: 열 마스터 키 순환의 일부로). 자세한 내용은 [상시 암호화를 위한 키 관리 개요](../../../relational-databases/security/encryption/overview-of-key-management-for-always-encrypted.md)를 참조하세요.
사용자 지정 키 저장소 공급자를 사용하는 경우에만 고유한 키 관리 도구를 구현해야 합니다. 기본 제공 공급자가 있는 키 저장소 또는 Azure 주요 자격 증명 모음에 저장된 키를 사용할 때는 SQL Server Management Studio 또는 PowerShell 등 기존 도구를 사용하여 키를 관리 및 프로비전할 수 있습니다.
아래 예제에서는 열 암호화 키를 생성하고 [SqlColumnEncryptionCertificateStoreProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncertificatestoreprovider.aspx) 를 사용하여 인증서로 키를 암호화하는 방법을 보여 줍니다.


```
using System.Security.Cryptography;
static void Main(string[] args)
{
    byte[] EncryptedColumnEncryptionKey = GetEncryptedColumnEncryptonKey(); 
    Console.WriteLine("0x" + BitConverter.ToString(EncryptedColumnEncryptionKey).Replace("-", "")); 
    Console.ReadKey();
}

static byte[]  GetEncryptedColumnEncryptonKey()
{
    int cekLength = 32;
    String certificateStoreLocation = "CurrentUser";
    String certificateThumbprint = "698C7F8E21B2158E9AED4978ADB147CF66574180";
    // Generate the plaintext column encryption key.
    byte[] columnEncryptionKey = new byte[cekLength];
    RNGCryptoServiceProvider rngCsp = new RNGCryptoServiceProvider();
    rngCsp.GetBytes(columnEncryptionKey);

    // Encrypt the column encryption key with a certificate.
    string keyPath = String.Format(@"{0}/My/{1}", certificateStoreLocation, certificateThumbprint);
    SqlColumnEncryptionCertificateStoreProvider provider = new SqlColumnEncryptionCertificateStoreProvider();
    return provider.EncryptColumnEncryptionKey(keyPath, @"RSA_OAEP", columnEncryptionKey); 
}
```


## <a name="controlling-performance-impact-of-always-encrypted"></a>상시 암호화의 성능 영향 제어

상시 암호화는 클라이언트 쪽 암호화 기술이므로 데이터베이스가 아닌 클라이언트 쪽에서 대부분의 성능 오버헤드가 발생합니다. 암호화 및 암호 해독 작업의 비용 외에 클라이언트 쪽 성능 오버헤드의 원인은 다음과 같습니다.
- 쿼리 매개 변수에 대한 메타데이터를 검색하기 위해 데이터베이스에 대한 추가 왕복
- 열 마스터 키에 액세스하기 위한 열 마스터 키 저장소 호출

이 섹션에서는 .NET Framework Provider for SQL Server의 기본 성능을 최적화하고 위의 두 성능 요소 영향을 제어할 수 있는 방법에 대해 설명합니다.

### <a name="controlling-round-trips-to-retrieve-metadata-for-query-parameters"></a>쿼리 매개 변수에 대한 메타데이터를 검색하기 위한 왕복 제어

연결에 대한 Always Encrypted가 설정된 경우 기본적으로 .NET Framework Data Provider for SQL Server는 매개 변수가 있는 각 쿼리에 대해 [sys.sp_describe_parameter_encryption](https://msdn.microsoft.com/library/mt631693.aspx) 을 호출하고 매개 변수 값 없이 쿼리 문을 SQL Server에 전달합니다. **sys.sp_describe_parameter_encryption** 은 쿼리 문을 분석하여 암호화해야 하는 매개 변수가 있는지 확인하고, 있는 경우 .NET Framework Data Provider for SQL Server에서 매개 변수 값을 암호화할 수 있도록 이러한 각 매개 변수에 대해 암호화 관련 정보를 반환합니다. 위의 동작은 클라이언트 응용 프로그램에 대한 높은 수준의 투명도를 보장합니다. 응용 프로그램(및 응용 프로그램 개발자)에서는 암호화된 열을 대상으로 하는 값이 SqlParameter 개체의 .NET Framework Data Provider for SQL Server에 전달되는 한 어떤 쿼리가 암호화된 열에 액세스하는지 유의하지 않아도 됩니다.


### <a name="query-metadata-caching"></a>쿼리 메타데이터 캐싱

.NET framework 4.6.2 이상 버전에서 .NET Framework Data Provider for SQL Server는 각 쿼리 문에 대해 **sys.sp_describe_parameter_encryption** 결과를 캐시합니다. 결과적으로 동일한 쿼리 문이 여러 번 실행될 경우 드라이버는 **sys.sp_describe_parameter_encryption** 을 한 번만 호출합니다. 쿼리 문에 대한 암호화 메타데이터 캐싱은 실제로 데이터베이스에서 메타데이터를 가져오는 성능 비용을 절감해 줍니다. 캐싱은 기본적으로 사용하도록 설정됩니다. [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionquerymetadatacacheenabled.aspx) 을 false로 설정하여 매개 변수 메타데이터 캐싱을 사용하지 않도록 설정할 수 있습니다. 하지만 아래 설명된 경우와 같이 아주 드문 경우를 제외하고는 권장되지 않습니다.

두 개의 서로 다른 스키마 s1 및 s2가 있는 데이터베이스를 고려해 보세요. 각 스키마에는 이름이 같은 테이블 t가 있습니다. 암호화 관련 속성을 제외하면 s1.t 및 s2.t 테이블 정의가 동일합니다. 이름이 c인 열이 s1.t에 있고 암호화되지 않았으며, s2.t에서는 암호화되어 있습니다. 데이터베이스에 두 사용자 u1 및 u2가 있습니다. u1 사용자에 대한 기본 스키마는 s1입니다. u2에 대한 기본 스키마는 s2입니다. .NET 응용 프로그램에서는 데이터베이스에 대한 두 가지 연결이 열립니다. 한 연결에서는 u1 사용자를 가장하고, 다른 연결에서는 u2 사용자를 가장합니다. 응용 프로그램은 사용자 u1에 대한 연결을 통해 c열을 대상으로 하는 매개 변수가 포함된 쿼리를 보냅니다(쿼리에서 스키마를 지정하지 않으면 기본 사용자 스키마로 가정). 다음으로 응용 프로그램에서 u2 사용자에 대한 연결을 통해 동일한 쿼리를 보냅니다. 쿼리 메타데이터 캐싱을 사용하는 경우에는 첫 번째 쿼리 후 캐시가 c열, 쿼리 매개 변수 대상이 암호화되지 않았음을 나타내는 메타데이터로 채워집니다. 두 번째 쿼리에 동일한 쿼리 문이 있으므로 캐시에 저장된 정보가 사용됩니다. 결과적으로 드라이버는 매개 변수를 암호화하지 않고 쿼리를 보내(대상 열 s2.t.c는 암호화되었으므로 정확하지는 않음) 서버에 전달되는 매개 변수의 일반 텍스트 값이 누락됩니다. 서버는 해당 비호환성을 감지하여 드라이버가 강제로 캐시를 새로 고치도록 합니다. 따라서 응용 프로그램에서 올바르게 암호화된 매개 변수 값이 포함된 쿼리를 다시 보냅니다. 이러한 경우 서버에 중요한 정보가 누락되는 것을 방지하기 위해 캐싱을 사용하지 않도록 설정해야 합니다. 




### <a name="setting-always-encrypted-at-the-query-level"></a>쿼리 수준에서 상시 암호화 설정

매개 변수화된 쿼리의 암호화 메타데이터 검색을 위한 성능 영향을 제어하려면 연결이 아닌 개별 쿼리에 대해 상시 암호화를 설정합니다. 이렇게 하면 암호화된 열을 대상으로 하는 매개 변수가 있는 쿼리에 대해서만 **sys.sp_describe_parameter_encryption** 을 호출할 수 있습니다. 단, 이 경우 암호화의 투명성이 저하될 수 있습니다. 데이터베이스 열의 암호화 속성을 변경한 경우 스키마 변경에 맞게 응용 프로그램 코드를 변경해야 할 수 있습니다.

> [!NOTE]
> 쿼리 수준에서 Always Encrypted를 설정하면 .NET 4.6.2 이상 버전에서 성능상의 혜택이 제한되어 매개 변수 암호화 메타데이터 캐싱이 구현됩니다.

개별 쿼리의 Always Encrypted 동작을 제어하려면  [SqlCommand](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommand.aspx) 및 [SqlCommandColumnEncryptionSetting](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx)의 이 생성자를 사용해야 합니다. 다음은 몇 가지 유용한 지침입니다.
- 대부분이 데이터베이스 연결 액세스 암호화된 열을 통해 전송하는 클라이언트 응용 프로그램을 쿼리하는 경우:
    - **열 암호화 설정** 연결 문자열 키워드를 *사용*으로 설정합니다.
    - 암호화된 모든 열을 액세스하지 않는 개별 쿼리에 대해 **SqlCommandColumnEncryptionSetting.Disabled** 를 설정합니다. 이렇게 하면 sys.sp_describe_parameter_encryption이 호출되지 않고 결과 집합 값의 암호 해독도 시도되지 않습니다.
    - 암호화를 요구하는 매개 변수가 없지만 암호화된 열에서 데이터를 검색하는 개별 쿼리에 대해 **SqlCommandColumnEncryptionSetting.ResultSet** 을 설정합니다. sys.sp_describe_parameter_encryption 호출 및 매개 변수 암호화가 사용되지 않습니다. 쿼리가 암호화 열에서 결과를 해독할 수 없습니다.
- 대부분이 암호화된 열에 액세스하지 않는 데이터베이스 연결을 통해 보내는 클라이언트 응용 프로그램을 쿼리하는 경우:
    - **열 암호화 설정** 연결 문자열 키워드를 **사용 안 함**으로 설정합니다.
    - 암호화해야 하는 모든 매개 변수가 있는 개별 쿼리에 대해 **SqlCommandColumnEncryptionSetting.Enabled** 를 설정합니다. 이렇게 하면 sys.sp_describe_parameter_encryption이 호출될 뿐만 아니라 암호화된 열에서 검색된 모든 쿼리 결과의 암호가 해독됩니다.
    - 암호화를 요구하는 매개 변수가 없지만 암호화된 열에서 데이터를 검색하는 쿼리에 대해 **SqlCommandColumnEncryptionSetting.ResultSet** 을 설정합니다. sys.sp_describe_parameter_encryption 호출 및 매개 변수 암호화가 사용되지 않습니다. 쿼리가 암호화 열에서 결과를 해독할 수 없습니다.

아래 예제에서는 데이터베이스 연결에 대해 상시 암호화가 사용되지 않습니다. 응용 프로그램에서 실행하는 쿼리에는 암호화되지 않은 LastName 열을 대상으로 하는 매개 변수가 있습니다. 쿼리는 암호화된 SSN 및 BirthDate 열에서 데이터를 검색합니다. 이러한 경우 암호화 메타데이터를 검색할 때 sys.sp_describe_parameter_encryption을 호출하지 않아도 됩니다. 그러나 응용 프로그램에서 두 암호화된 열에서 일반 텍스트 값을 가져올 수 있도록 쿼리 결과에 대한 암호 해독을 설정해야 합니다. 이러한 기능을 위해 SqlCommandColumnEncryptionSetting.ResultSet 설정이 사용됩니다.



```
string connectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
using (SqlConnection connection = new SqlConnection(connectionString))
{
    connection.Open();
    using (SqlCommand cmd = new SqlCommand(@"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [LastName]=@LastName",
connection, null, SqlCommandColumnEncryptionSetting.ResultSetOnly))
    {
        SqlParameter paramLastName = cmd.CreateParameter();
        paramLastName.ParameterName = @"@LastName";
        paramLastName.DbType = DbType.String;
        paramLastName.Direction = ParameterDirection.Input;
        paramLastName.Value = "Abel";
        paramLastName.Size = 50;
        cmd.Parameters.Add(paramLastName);
        using (SqlDataReader reader = cmd.ExecuteReader())
            {
               if (reader.HasRows)
               {
                  while (reader.Read())
                  {
                     Console.WriteLine(@"{0}, {1}, {2}, {3}", reader[0], reader[1], reader[2], ((DateTime)reader[3]).ToShortDateString());
                  }
               }
            }
  } 
}
```


### <a name="column-encryption-key-caching"></a>열 암호화 키 캐싱

열 마스터 키 저장소에 대한 호출 수를 줄여 열 암호화 키의 암호를 해독하기 위해 .NET Framework Data Provider for SQL Server에서는 일반 텍스트 열 암호화 키를 메모리에 캐시합니다. 데이터베이스 메타데이터에서 암호화된 열 암호화 키 값을 받은 후 드라이버는 제일 먼저 암호화된 키 값에 해당하는 일반 텍스트 열 암호화 키를 찾습니다. 드라이버는 캐시에서 암호화된 열 암호화 키 값을 찾을 수 없는 경우에만 열 마스터 키가 포함된 키 저장소를 호출합니다.

> [!NOTE]
> .NET Framework 4.6 및 4.6.1에서는 캐시의 열 암호화 키 항목이 제거되지 않습니다. 즉, 드라이버는 응용 프로그램 수명 중 한 번만 특정 암호화된 열 암호화 키에 대해 키 저장소에 연결합니다.

.NET framework 4.6.2 이상 버전에서 캐시 항목은 보안상의 이유로 구성 가능한 TTL(Time-to-Live) 시간 간격 후 제거됩니다. 기본 TTL(Time-to-Live) 값은 2시간입니다. 응용 프로그램에서 열 암호화 키를 일반 텍스트로 캐시할 수 있는 시간에 대해 좀 더 엄격한 보안 요구 사항이 있을 경우에는 [SqlConnection.ColumnEncryptionKeyCacheTtl 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionkeycachettl.aspx)을 사용하여 변경할 수 있습니다. 


## <a name="enabling-additional-protection-for-a-compromised-sql-server"></a>손상된 SQL Server에 대한 추가 보호를 사용하도록 설정

기본적으로 *.NET Framework Data Provider for SQL Server* 는 데이터베이스 시스템(SQL Server 또는 Azure SQL Database)을 사용하여 데이터베이스의 어떤 열을 어떻게 암호화할지 고려하여 메타데이터를 제공합니다. 암호화 메타데이터는.응용 프로그램에서 입력하지 않고 NET Framework Data Provider for SQL Server를 사용하여 쿼리 매개 변수를 암호화하고 쿼리 결과를 해독할 수 있어 응용 프로그램에 필요한 수정을 크게 줄였습니다. 그러나 SQL Server 프로세스가 손상되고, SQL Server가 .NET Framework Data Provider for SQL Server에 전송하는 메타데이터를 공격자가 손상시킨 경우에는 공격자가 중요한 정보를 훔쳤을 수도 있습니다. 이 섹션에서는 이러한 종류의 공격에 대해 추가 보호 수준을 낮은 가격으로 제공하는 데 도움이 되는 API에 대해 설명합니다. 

### <a name="forcing-parameter-encryption"></a>매개 변수 강제 암호화 

.NET Framework Data Provider for SQL Server에서 SQL Server에 매개 변수가 있는 쿼리를 보내기 전에 [sys.sp_describe_parameter_encryption](../../../relational-databases/system-stored-procedures/sp-describe-parameter-encryption-transact-sql.md)을 호출하여 쿼리 문을 분석하고 쿼리에서 암호화해야 할 매개 변수에 대한 정보를 제공하라는 요청을 받게 됩니다. 손상된 SQL Server 인스턴스는 매개 변수에서 암호화된 열을 대상으로 지정하지 않았다고 알리는 메타데이터를 보내 실제로 열은 데이터베이스에서 암호화되어 있어도 NET Framework Data Provider for SQL Server에서는 오해할 수 있습니다. 결과적으로 .NET Framework Data Provider for SQL Server는 매개 변수 값을 암호화하지 않고 일반 텍스트로 손상된 SQL Server 인스턴스에 보냅니다.

이러한 공격을 방지하기 위해 응용 프로그램은 매개 변수에 대한 [SqlParameter.ForceColumnEncryption 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.forcecolumnencryption.aspx) 을 true로 설정할 수 있습니다. 이렇게 하면 서버에서 수신한 메타데이터에서 매개 변수를 암호화하지 않아도 된다고 나타낼 경우 .NET Framework Data Provider for SQL Server에서는 예외를 throw합니다.

**SqlParameter.ForceColumnEncryption 속성** 을 사용하면 보안이 강화되지만 클라이언트 응용 프로그램에 대한 암호화 투명도는 줄어듭니다. 데이터베이스 스키마를 업데이트하여 암호화된 열 집합을 변경하려면 응용 프로그램도 변경해야 할 수 있습니다.

다음 코드 예제에서는 **SqlParameter.ForceColumnEncryption 속성** 을 사용하여 주민 등록 번호를 데이터베이스에 일반 텍스트로 보내지 않도록 하는 방법을 보여 줍니다. 



```
SqlCommand cmd = _sqlconn.CreateCommand(); 

// Use parameterized queries to access Always Encrypted data. 
 
cmd.CommandText = @"SELECT [SSN], [FirstName], [LastName], [BirthDate] FROM [dbo].[Patients] WHERE [SSN] = @SSN;"; 

SqlParameter paramSSN = cmd.CreateParameter(); 
paramSSN.ParameterName = @"@SSN"; 
paramSSN.DbType = DbType.AnsiStringFixedLength; 
paramSSN.Direction = ParameterDirection.Input; 
paramSSN.Value = ssn; 
paramSSN.Size = 11; 
paramSSN.ForceColumnEncryption = true; 
cmd.Parameters.Add(paramSSN); 

SqlDataReader reader = cmd.ExecuteReader();
```
 

### <a name="configuring-trusted-column-master-key-paths"></a>신뢰할 수 있는 열 마스터 키 경로 구성 

암호화된 열을 대상으로 하는 쿼리 매개 변수와, 암호화된 열에서 검색된 결과에 대해 SQL Server에서 반환하는 암호화 메타데이터에는 키 저장소와, 키 저장소에 있는 키의 위치를 식별하는 열 마스터 키의 키 경로가 포함되어 있습니다. SQL Server 인스턴스가 손상되면.NET Framework Data Provider for SQL Server를 공격자가 조정하는 위치로 연결하는 키 경로를 보낼 수 있습니다. 이렇게 하면 응용 프로그램에서 인증해야 하는 키 저장소의 경우 자격 증명에 누수가 발생할 수도 있습니다. 

이러한 공격을 방지하기 위해 응용 프로그램에서는 [SqlConnection.ColumnEncryptionTrustedMasterKeyPaths 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptiontrustedmasterkeypaths.aspx)을 사용하여 지정된 서버에 대해 신뢰할 수 있는 키 경로 목록을 지정할 수 있습니다. .NET Framework Data Provider for SQL Server에서 신뢰할 수 있는 키 경로 목록 외부에 있는 키 경로를 수신하면 예외가 throw됩니다. 

신뢰할 수 있는 키 경로를 설정하면 응용 프로그램 보안이 개선되지만 열 마스터 키를 이동할 때마다 즉 열 마스터 키 경로가 변경될 때마다 응용 프로그램 코드 및/또는 구성을 변경해야 합니다. 

다음 예제에서는 신뢰할 수 있는 열 마스터 키 경로 구성하는 방법을 보여 줍니다.


```
// Configure trusted key paths to protect against fake key paths sent by a compromised SQL Server instance 
// First, create a list of trusted key paths for your server 
List<string> trustedKeyPathList = new List<string>(); 
trustedKeyPathList.Add("CurrentUser/my/425CFBB9DDDD081BB0061534CE6AB06CB5283F5Ea"); 

// Register the trusted key path list for your server 

SqlConnection.ColumnEncryptionTrustedMasterKeyPaths.Add(serverName, trustedKeyPathList);
```
 



## <a name="copying-encrypted-data-using-sqlbulkcopy"></a>SqlBulkCopy를 사용하여 암호화된 데이터 복사

SqlBulkCopy를 사용하면 데이터의 암호를 해독하지 않고 한 테이블에서 암호화되어 저장된 데이터를 다른 테이블에 복사할 수 있습니다. 이렇게 하려면 다음을 수행합니다.

- 대상 테이블의 암호화 구성이 원본 테이블의 구성과 일치하는지 확인합니다. 특히 두 테이블에 동일한 암호화 열이 있고 동일한 암호화 형식 및 암호화 키를 사용하여 열이 암호화되어야 합니다. 참고: 대상 열 중 하나가 해당 원본 열과 다르게 암호화된 경우 복사 작업 후 대상 테이블의 데이터 암호를 해독할 수 없습니다. 데이터가 손상됩니다.
- 상시 암호화를 사용하지 않고 원본 테이블과 대상 테이블에 대한 데이터베이스 연결을 구성합니다. 
- AllowEncryptedValueModifications 옵션을 설정합니다( [SqlBulkCopyOptions](https://msdn.microsoft.com/library/system.data.sqlclient.sqlbulkcopyoptions.aspx)참조). 참고: AllowEncryptedValueModifications를 지정하면 .NET Framework Data Provider for SQL Server가 데이터가 암호화되었는지 여부 또는 동일한 암호화 형식, 알고리즘 및 키를 대상 열로 사용하여 올바르게 암호화되었는지 확인하지 않아 데이터베이스가 손상될 수 있으므로 주의하여 사용합니다.

AllowEncryptedValueModifications 옵션은 .NET Framework 4.6.1 이상 버전에서 사용할 수 있습니다.

다음은 한 테이블에서 다른 테이블로 데이터를 복사하는 예제입니다. SSN 및 BirthDate 열은 암호화된 것으로 간주됩니다.
        

```
static public void CopyTablesUsingBulk(string sourceTable, string targetTable)
{
   string sourceConnectionString = "Data Source=server63; Initial Catalog=Clinic; Integrated Security=true";
   string targetConnectionString = "Data Source= server64; Initial Catalog=Clinic; Integrated Security=true";
   using (SqlConnection connSource = new SqlConnection(sourceConnectionString))
   {
      connSource.Open();
      using (SqlCommand cmd = new SqlCommand(string.Format("SELECT [PatientID], [SSN], [FirstName], [LastName], [BirthDate] FROM {0}", sourceTable), connSource))
      {
         using (SqlDataReader reader = cmd.ExecuteReader())
         {
            SqlBulkCopy copy = new SqlBulkCopy(targetConnectionString, SqlBulkCopyOptions.KeepIdentity | SqlBulkCopyOptions.AllowEncryptedValueModifications);
            copy.EnableStreaming = true;
            copy.DestinationTableName = targetTable;
            copy.WriteToServer(reader);
         }
      }
}
```


## <a name="always-encrypted-api-reference"></a>Always Encrypted API 참조

**Namespace:** [System.Data.SqlClient](https://msdn.microsoft.com/library/system.data.sqlclient.aspx)

**어셈블리:** System.Data(System.Data.dll에서)




|이름|설명|도입된 .NET 버전
|:---|:---|:---
|[SqlColumnEncryptionCertificateStoreProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncertificatestoreprovider.aspx)|Windows 인증서 저장소에 대한 키 저장소 공급자입니다.|  4.6
|[SqlColumnEncryptionCngProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncngprovider.aspx)|Microsoft 암호화 API: 차세대(CNG)에 대한 키 저장소 공급자입니다.|  4.6.1
|[SqlColumnEncryptionCspProvider 클래스](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptioncspprovider.aspx)|CSP(암호화 서비스 공급자)를 기반으로 하는 Microsoft CAPI에 대한 키 저장소 공급자입니다.|4.6.1  
|[SqlColumnEncryptionKeyStoreProvider](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcolumnencryptionkeystoreprovider.aspx)|키 저장소 공급자의 기본 클래스입니다.|  4.6
|[SqlCommandColumnEncryptionSetting 열거형](https://msdn.microsoft.com/library/system.data.sqlclient.sqlcommandcolumnencryptionsetting.aspx)|데이터베이스 연결에 대한 암호화 및 암호 해독을 활성화하는 설정입니다.|4.6  
|[SqlConnectionColumnEncryptionSetting 열거형](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnectioncolumnencryptionsetting.aspx)|개별 쿼리에 대한 상시 암호화의 동작을 제어하는 설정입니다.|4.6  
| [SqlConnectionStringBuilder.ColumnEncryptionSetting 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnectionstringbuilder.columnencryptionsetting.aspx)|연결 문자열에서 상시 암호화를 가져오고 설정합니다.|4.6|
| [SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionquerymetadatacacheenabled.aspx) | 암호화 쿼리 메타데이터 캐싱을 사용하거나 사용하지 않도록 설정합니다. | 4.6.2
| [SqlConnection.ColumnEncryptionKeyCacheTtl 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptionkeycachettl.aspx) | 열 암호화 키 캐시에서 항목에 대한 TTL(Time-to-Live)을 가져와 설정합니다. | 4.6.2
|[SqlConnection.ColumnEncryptionTrustedMasterKeyPaths 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.columnencryptiontrustedmasterkeypaths.aspx)|데이터베이스 서버에 대해 신뢰할 수 있는 키 경로 목록을 설정할 수 있습니다. 응용 프로그램 쿼리를 처리하는 동안 드라이버에서 목록에 없는 키 경로를 수신하면 쿼리가 실패합니다. 이 속성은 손상된 SQL Server가 가짜 키 쌍을 제공하여 키 저장소 자격 증명을 유출하는 보안 공격에 대한 추가 보호를 제공합니다.|  4.6
|[SqlConnection.RegisterColumnEncryptionKeyStoreProviders 메서드](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.registercolumnencryptionkeystoreproviders.aspx)|사용자 지정 키 저장소 공급자를 등록할 수 있습니다. 키 저장소 공급자 이름을 키 저장소 공급자 구현에 매핑하는 사전입니다.|  4.6
|[SqlCommand 생성자(문자열, SqlConnection, SqlTransaction, SqlCommandColumnEncryptionSetting)](https://msdn.microsoft.com/library/dn956511\(v=vs.110\).aspx)|개별 쿼리에 대한 상시 암호화의 동작을 제어할 수 있습니다.|  4.6
|[SqlParameter.ForceColumnEncryption 속성](https://msdn.microsoft.com/library/system.data.sqlclient.sqlparameter.forcecolumnencryption.aspx)|매개 변수의 암호화를 적용합니다. SQL Server가 매개 변수를 암호화하지 않아도 되는 것을 드라이버에 알리는 경우 매개 변수를 사용하는 쿼리는 실패합니다. 이 속성은 데이터 노출을 야기할 수 있는 잘못된 암호화 메타데이터를 클라이언트에게 제공하는 손상된 SQL Server를 포함하는 보안 공격에 대한 추가 보호를 제공합니다.|4.6  
|새 [연결 문자열](https://msdn.microsoft.com/library/system.data.sqlclient.sqlconnection.connectionstring.aspx) 키워드: `Column Encryption Setting=enabled`|연결에 대해 상시 암호화 기능을 사용하거나 사용하지 않습니다.| 4.6 
  

## <a name="see-also"></a>참고 항목

- [상시 암호화(데이터베이스 엔진)](../../../relational-databases/security/encryption/always-encrypted-database-engine.md)
- [상시 암호화 블로그](http://blogs.msdn.com/b/sqlsecurity/archive/tags/always-encrypted/)
- [SQL 데이터베이스 자습서: 상시 암호화로 중요한 데이터 보호](https://azure.microsoft.com/documentation/articles/sql-database-always-encrypted/)

















