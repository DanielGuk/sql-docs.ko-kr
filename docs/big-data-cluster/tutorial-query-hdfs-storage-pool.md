---
title: SQL Server 빅 데이터 클러스터에서 HDFS 쿼리 하는 방법 | Microsoft Docs
description: 이 자습서에는 SQL Server 2019 빅 데이터 클러스터 (미리 보기)에서 HDFS 데이터를 쿼리 하는 방법을 보여 줍니다. 저장소 풀의 데이터에 대 한 외부 테이블을 만들고 쿼리를 실행 합니다.
author: rothja
ms.author: jroth
manager: craigg
ms.date: 10/11/2018
ms.topic: tutorial
ms.prod: sql
ms.openlocfilehash: c6f0f01936d5b6e570c2bff53d19ae7a64f151ab
ms.sourcegitcommit: 38f35b2f7a226ded447edc6a36665eaa0376e06e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49644246"
---
# <a name="tutorial-query-hdfs-in-a-sql-server-big-data-cluster"></a>자습서: SQL Server 빅 데이터 클러스터에서 HDFS 쿼리

이 자습서에는 SQL Server 2019 빅 데이터 클러스터에서 HDFS 데이터를 쿼리 하는 방법을 보여 줍니다.

이 자습서에 알아봅니다 방법:

> [!div class="checklist"]
> * 빅 데이터 클러스터에서 HDFS 데이터를 가리키는 외부 테이블을 만듭니다.
> * 높은 가치의 데이터를 사용 하 여이 데이터 마스터 인스턴스를 조인 합니다.

> [!TIP]
> 원한다 면 다운로드 하 고이 자습서의 명령에 대 한 스크립트를 실행할 수 있습니다. 지침은 합니다 [데이터 가상화 샘플](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/sql-big-data-cluster/data-virtualization) github입니다.

## <a name="prerequisites"></a>필수 구성 요소

- [Kubernetes에서 빅 데이터 클러스터를 배포](deployment-guidance.md)합니다.
- [Azure Data Studio 및 SQL Server 2019 확장 설치](deploy-big-data-tools.md)합니다.
- [클러스터에 샘플 데이터 로드](#sampledata)합니다.

[!INCLUDE [Load sample data](../includes/big-data-cluster-load-sample-data.md)]

## <a name="create-an-external-table-to-hdfs"></a>HDFS에 외부 테이블 만들기

저장소 풀 HDFS에 저장 된 CSV 파일의 웹 클릭 동향 데이터를 포함 합니다. 다음 단계를 사용 하 여 해당 파일의 데이터에 액세스할 수 있는 외부 테이블을 정의 합니다.

1. Azure Data Studio, 빅 데이터 클러스터의 마스터 SQL Server 인스턴스에 연결 합니다. 자세한 내용은 [SQL Server 마스터 인스턴스에 연결할](deploy-big-data-tools.md#master)합니다.

2. 연결을 두 번 클릭 합니다 **서버** 창 마스터 SQL Server 인스턴스에 대 한 서버 대시보드를 표시 합니다. 선택 **새 쿼리**합니다.

   ![SQL Server 마스터 인스턴스 쿼리](./media/tutorial-query-hdfs-storage-pool/sql-server-master-instance-query.png)

3. 컨텍스트를 변경 하려면 다음 TRANSACT-SQL 명령을 실행 합니다 **Sales** 마스터 인스턴스에 있는 데이터베이스입니다.

   ```sql
   USE Sales
   GO
   ```

4. HDFS에서 읽을 CSV 파일의 형식을 정의 합니다. F5 키를 눌러 문을 실행 합니다.

   ```sql
   CREATE EXTERNAL FILE FORMAT csv_file
   WITH (
       FORMAT_TYPE = DELIMITEDTEXT,
       FORMAT_OPTIONS(
           FIELD_TERMINATOR = ',',
           STRING_DELIMITER = '"',
           FIRST_ROW = 2,
           USE_TYPE_DEFAULT = TRUE)
   );
   ```

5. 읽을 수 있는 외부 테이블 만들기는 `/clickstream_data` 저장소 풀에서. 합니다 **SqlStoragePool** 빅 데이터 클러스터의 마스터 인스턴스에서 액세스할 수 있습니다.

   ```sql
   CREATE EXTERNAL TABLE [web_clickstreams_hdfs]
   ("wcs_click_date_sk" BIGINT , "wcs_click_time_sk" BIGINT , "wcs_sales_sk" BIGINT , "wcs_item_sk" BIGINT , "wcs_web_page_sk" BIGINT , "wcs_user_sk" BIGINT)
   WITH
   (
       DATA_SOURCE = SqlStoragePool,
       LOCATION = '/clickstream_data',
       FILE_FORMAT = csv_file
   );
   GO
   ```

## <a name="query-the-data"></a>데이터를 쿼리 합니다.

HDFS 데이터를 조인 하려면 다음 쿼리를 실행 합니다 `web_clickstream_hdfs` 로컬의 관계형 데이터를 사용 하 여 외부 테이블 `Sales` 데이터베이스입니다.

```sql
SELECT  
    wcs_user_sk,
    SUM( CASE WHEN i_category = 'Books' THEN 1 ELSE 0 END) AS book_category_clicks,
    SUM( CASE WHEN i_category_id = 1 THEN 1 ELSE 0 END) AS [Home & Kitchen],
    SUM( CASE WHEN i_category_id = 2 THEN 1 ELSE 0 END) AS [Music],
    SUM( CASE WHEN i_category_id = 3 THEN 1 ELSE 0 END) AS [Books],
    SUM( CASE WHEN i_category_id = 4 THEN 1 ELSE 0 END) AS [Clothing & Accessories],
    SUM( CASE WHEN i_category_id = 5 THEN 1 ELSE 0 END) AS [Electronics],
    SUM( CASE WHEN i_category_id = 6 THEN 1 ELSE 0 END) AS [Tools & Home Improvement],
    SUM( CASE WHEN i_category_id = 7 THEN 1 ELSE 0 END) AS [Toys & Games],
    SUM( CASE WHEN i_category_id = 8 THEN 1 ELSE 0 END) AS [Movies & TV],
    SUM( CASE WHEN i_category_id = 9 THEN 1 ELSE 0 END) AS [Sports & Outdoors]
  FROM [dbo].[web_clickstreams_hdfs]
  INNER JOIN item it ON (wcs_item_sk = i_item_sk
                        AND wcs_user_sk IS NOT NULL)
GROUP BY  wcs_user_sk;
GO
```

## <a name="clean-up"></a>정리

이 자습서에 사용 되는 외부 테이블을 제거 하려면 다음 명령을 사용 합니다.

```sql
DROP EXTERNAL TABLE [dbo].[web_clickstreams_hdfs];
GO
```

## <a name="next-steps"></a>다음 단계

빅 데이터 클러스터에서 Oracle을 쿼리 하는 방법을 알아보려면 다음 문서로 이동 합니다.
> [!div class="nextstepaction"]
> [Oracle에서 데이터를 외부 쿼리](tutorial-query-oracle.md)
