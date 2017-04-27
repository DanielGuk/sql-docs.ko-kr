---
title: "쿼리 저장소 사용 시나리오 | Microsoft 문서"
ms.custom:
- SQL2016_New_Updated
ms.date: 04/12/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-query-tuning
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Query Store, usage scenarios
ms.assetid: f5309285-ce93-472c-944b-9014dc8f001d
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: ce278d494e2d5ab7dfc82e244a9d6b8821099cc0
ms.lasthandoff: 04/11/2017

---
# <a name="query-store-usage-scenarios"></a>쿼리 저장소 사용 시나리오
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  쿼리 저장소는 예측 가능한 워크로드 성능을 추적하고 보장하는 것이 중요한 광범위한 시나리오에서 사용될 수 있습니다. 다음은 고려할 수 있는 몇 가지 예입니다.  
  
-   계획 선택 재발이 있는 쿼리 식별 및 수정  
  
-   상위 리소스 소비 쿼리 식별 및 조정  
  
-   A/B 테스트  
  
-   다음으로 업그레이드하는 동안 성능 안정성 유지 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   임시 워크로드 식별 및 개선  
  
## <a name="pinpoint-and-fix-queries-with-plan-choice-regressions"></a>계획 선택 재발이 있는 쿼리 식별 및 수정  
 일반 쿼리 실행 중 데이터 카디널리티가 변경되거나, 인덱스가 생성, 변경 또는 삭제되거나, 통계가 업데이트되는 등 중요한 입력이 달라졌기 때문에 쿼리 최적화 프로그램에서 다른 계획을 사용하도록 결정하는 경우가 있을 수 있습니다.  선택하는 대부분의 새 계획은 이전에 사용된 것보다 더 낫거나 거의 동일합니다. 그러나 새 계획이 훨씬 나쁜 경우도 있습니다. 이러한 상황을 계획 선택 변경 재발이라고 합니다. 쿼리 저장소 이전에는 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 사용자가 시간이 지남에 따라 사용된 실행 계획을 확인할 수 있는 기본 제공 데이터 저장소를 제공하지 않았기 때문에 이는 식별하고 수정하기 매우 어려운 문제였습니다.  
  
 이제 쿼리 저장소를 사용하여 다음을 신속하게 수행할 수 있습니다.  
  
-   관심 기간(지난 시간, 일, 주 등) 동안 실행 메트릭이 저하된 모든 쿼리를 식별할 수 있습니다. **에서** 재발된 쿼리 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 를 사용하여 분석을 가속화할 수 있습니다.  
  
-   재발된 쿼리 중에서 여러 계획이 있고 잘못된 계획 선택으로 인해 저하된 쿼리를 매우 쉽게 찾을 수 있습니다. **재발된 쿼리** 에서 **계획 요약** 창을 사용하여 재발된 쿼리에 대한 모든 계획과 시간에 따른 쿼리 성능을 시각화할 수 있습니다.  
  
-   기록에서 이전 계획이 더 나은 것으로 증명된 경우 이를 적용합니다. **재발된 쿼리** 에서 **계획 적용** 단추를 사용하여 쿼리에 대해 선택한 계획을 적용합니다.  
  
 ![query-store-usage-1](../../relational-databases/performance/media/query-store-usage-1.png "query-store-usage-1")  
  
 이 시나리오에 대한 자세한 설명은 [쿼리 저장소: 데이터베이스를 위한 항공 데이터 레코더](https://azure.microsoft.com/blog/query-store-a-flight-data-recorder-for-your-database/) 블로그를 참조하세요.  
  
## <a name="identify-and-tune-top-resource-consuming-queries"></a>상위 리소스 소비 쿼리 식별 및 조정  
 워크로드에서 수천 개의 쿼리를 생성할 수 있지만 일반적으로 그 중 소수의 쿼리만 대부분의 시스템 리소스를 사용하므로 주의가 필요합니다. 리소스를 많이 사용하는 상위 쿼리 중에서 추가 조정을 통해 개선할 수 있는 쿼리 또는 재발된 쿼리를 찾습니다.  
  
 탐색을 시작하는 가장 쉬운 방법은 **에서** 상위 리소스 소비 쿼리 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]를 여는 것입니다.  사용자 인터페이스는 상위 리소스 소비 쿼리를 나타내는 막대 그래프(왼쪽), 선택한 쿼리에 대한 계획 요약(오른쪽) 및 선택한 계획에 대한 시각적 쿼리 계획(아래쪽), 이렇게 세 개의 창으로 구분되어 있습니다. **구성** 을 클릭하여 분석할 쿼리 수 및 관심 있는 시간 간격을 제어할 수 있습니다. 또한 다양한 리소스 소비 차원(기간, CPU, 메모리, IO, 실행 횟수)과 기준선(평균, 최소값, 최대값, 합계, 표준 편차) 간에 선택할 수 있습니다.  
  
 ![query-store-usage-2](../../relational-databases/performance/media/query-store-usage-2.png "query-store-usage-2")  
  
 오른쪽의 계획 요약을 보고 실행 기록을 분석한 후 다른 계획과 해당 런타임 통계에 대해 자세히 알아볼 수 있습니다. 아래쪽 창을 사용하여 다른 계획을 검사하거나 나란히 렌더링하여 시각적으로 비교(비교 단추 사용)할 수 있습니다.  
  
 최적 상태가 아닌 성능의 쿼리를 식별한 경우 수행할 작업은 문제의 성격에 따라 다릅니다.  
  
1.  쿼리가 여러 계획으로 실행되고 마지막 계획이 이전 계획보다 훨씬 나쁜 경우 계획 적용 메커니즘을 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에서 향후 실행에 최적 계획을 사용하도록 할 수 있습니다.  
  
2.  최적화 프로그램이 XML 계획에서 누락된 인덱스를 제안하는지 확인합니다. 그런 경우 누락된 인덱스를 만든 다음 쿼리 저장소를 사용하여 쿼리 성능을 평가합니다.  
  
3.  쿼리에 사용된 기본 테이블에 대한 통계가 최신 상태인지 확인합니다.  
  
4.  쿼리에 사용된 인덱스가 조각 모음되었는지 확인합니다.  
  
5.  부담이 큰 쿼리는 다시 작성하는 것이 좋습니다. 예를 들어 쿼리 매개 변수화를 활용하고 동적 SQL의 사용을 줄입니다. 데이터를 읽을 때의 최적 논리를 구현합니다(응용 프로그램 쪽이 아니라 데이터베이스 쪽에서 데이터 필터링 적용).  
  
## <a name="ab-testing"></a>A/B 테스트  
 쿼리 저장소를 사용하여 예정된 응용 프로그램 변경 이전과 이후의 워크로드 성능을 비교할 수 있습니다.  다음 목록에는 쿼리 저장소를 사용하여 환경 또는 응용 프로그램 변경이 워크로드 성능에 미치는 영향을 평가할 수 있는 몇 가지 예제가 포함되어 있습니다.  
  
-   새 응용 프로그램 버전 출시  
  
-   서버에 새 하드웨어 추가  
  
-   부담이 큰 쿼리에서 참조하는 테이블에 누락된 인덱스 만들기  
  
-   행 수준 보안을 위한 보안 정책 적용. 자세한 내용은 [쿼리 저장소를 사용하여 행 수준 보안 최적화](http://blogs.msdn.com/b/sqlsecurity/archive/2015/07/21/optimizing-rls-performance-with-the-query-store.aspx)를 참조하세요.  
  
-   OLTP 응용 프로그램에서 자주 수정되는 테이블에 임시 시스템 버전 추가  
  
 이러한 시나리오에서는 다음 워크플로를 적용합니다.  
  
1.  계획된 변경 전에 쿼리 저장소와 함께 워크로드를 실행하여 성능 기준선을 생성합니다.  
  
2.  제어되는 시점에서 응용 프로그램 변경을 적용합니다.  
  
3.  변경 후 시스템의 성능 이미지를 생성할 수 있는 충분한 시간 동안 워크로드를 계속 실행합니다.  
  
4.  1과 3의 결과를 비교합니다.  
  
    1.  	**전체 데이터베이스 사용량** 을 열어 전체 데이터베이스에 대한 영향을 확인합니다.  
  
    2.  **상위 리소스 소비 쿼리** 를 열거나 [!INCLUDE[tsql](../../includes/tsql-md.md)]을 사용한 사용자 고유 분석을 실행하여 가장 중요한 쿼리에 미치는 변경의 영향을 분석합니다.  
  
5.  변경을 유지할지 또는 롤백(새로운 성능이 허용되지 않는 경우)을 수행할지 결정합니다.  
  
 다음 그림에서는 누락된 인덱스를 만드는 경우 쿼리 저장소 분석(4단계)을 보여 줍니다. **상위 리소스 소비 쿼리** /계획 요약 창을 열어 인덱스 만들기의 영향을 받는 쿼리에 대해 이 뷰를 가져옵니다.  
  
 ![query-store-usage-3](../../relational-databases/performance/media/query-store-usage-3.png "query-store-usage-3")  
  
 또한 나란히 렌더링하여 인덱스 만들기 이전과 이후의 계획을 비교할 수 있습니다. 도구 모음에 빨간색 사각형으로 표시된 "별도 창에서 선택한 쿼리에 대한 계획 비교" 도구 모음 옵션을 사용합니다.  
  
 ![query-store-usage-4](../../relational-databases/performance/media/query-store-usage-4.png "query-store-usage-4")  
  
 인덱스 만들기 이전 계획(plan_id  = 1, 위)에 누락된 인덱스 힌트가 있으며, Clustered Index Scan이 쿼리에서 가장 부담이 큰 연산자였음을 검사할 수 있습니다(빨간색 사각형).  
  
 이제 누락된 인덱스 만들기 이후 계획(plan_id = 15, 아래)에 전체 쿼리 비용을 줄이고 성능을 개선하는 Index Seek(비클러스터형)가 있습니다(녹색 사각형).  
  
 분석에 따라, 쿼리 성능이 향상되었으므로 인덱스를 유지할 수 있습니다.  
  
## <a name="keep-performance-stability-during-the-upgrade-to-sql-server-2016"></a>SQL Server 2016로 업그레이드하는 동안 성능 안정성 유지  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]이전에는 사용자가 최신 플랫폼 버전으로 업그레이드하는 동안 성능 회귀 위험에 노출되었습니다. 이러한 이유로 새 비트가 설치되는 즉시 최신 버전의 쿼리 최적화 프로그램이 활성화되었습니다.  
  
 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 부터 쿼리 최적화 프로그램의 모든 변경 내용이 최신 `COMPATIBILITY_LEVEL`에 연결되므로 계획이 업그레이드 시점에 즉시 변경되지 않고 사용자가 `COMPATIBILITY_LEVEL` 을 최신 상태로 변경하는 경우에 변경됩니다. 이 기능은 쿼리 저장소와 함께 업그레이드 프로세스에서 쿼리 성능에 대한 뛰어난 제어 수준을 제공합니다. 아래 그림에 권장 업그레이드 워크플로가 표시되어 있습니다.  
  
 ![query-store-usage-5](../../relational-databases/performance/media/query-store-usage-5.png "query-store-usage-5")  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 을 변경하지 않고 `COMPATIBILITY_LEVEL`을 업그레이드합니다. 최신 쿼리 최적화 프로그램에 노출되는 것이 아니라 쿼리 저장소를 포함하는 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 기능을 제공합니다.  
  
2.  쿼리 저장소 사용: 쿼리 및 계획을 캡처하고 이전 `COMPATIBILITY_LEVEL`을 사용하여 성능 기준선을 설정합니다. 모든 계획을 캡처하고 안정적인 기준선을 얻을 때까지 이 단계를 계속 유지합니다.  
  
3.  최신 호환성 수준으로 이동: 워크로드를 최신 쿼리 최적화 프로그램에 노출하여 잠재적으로 새 계획을 만들 수 있도록 합니다.  
  
4.  분석 및 재발 수정에 쿼리 저장소 사용: 대부분의 경우 새 쿼리 최적화 프로그램은 향상된 계획을 생성합니다. 그러나 쿼리 저장소는 계획 선택 재발을 식별하고 계획 적용 메커니즘을 사용하여 이를 수정하는 간편한 방법을 제공합니다.  
  
## <a name="identify-and-improve-ad-hoc-workloads"></a>임시 워크로드 식별 및 개선  
 일부 워크로드에는 전체 응용 프로그램 성능을 개선하기 위해 조정할 수 있는 주요 쿼리가 없습니다. 이러한 워크로드에는 일반적으로 각각 시스템 리소스의 일부를 소비하는 비교적 많은 수의 여러 쿼리가 있는 것이 특징입니다. 이러한 쿼리는 거의 실행되지 않으므로(일반적으로 한 번만 실행되므로 임시 쿼리라고 함) 해당 런타임 소비는 중요하지 않습니다. 반면, 응용 프로그램이 항상 완전히 새로운 쿼리를 생성하는 경우에는 시스템 리소스의 상당 부분이 최적화되지 않은 쿼리 컴파일에 소비됩니다. 이는 많은 수의 쿼리와 계획이 예약된 공간을 차지하는 경우 쿼리 저장소에 이상적인 상황이 아닙니다. 즉, 쿼리 저장소가 매우 빠르게 읽기 전용 모드로 전환될 수 있습니다. **크기 기반 정리 정책** (쿼리 저장소를 항상 실행되도록 유지하는 데[매우 권장됨](https://msdn.microsoft.com/library/mt604821.aspx) )을 활성화한 경우 백그라운드 프로세스에서 쿼리 저장소 구조를 정리하므로 대부분의 시간 동안 상당한 시스템 리소스가 소비됩니다.  
  
 **상위 리소스 소비 쿼리** 뷰는 워크로드의 임시 특성에 대한 첫 번째 표시를 제공합니다.  
  
 ![query-store-usage-6](../../relational-databases/performance/media/query-store-usage-6.png "query-store-usage-6")  
  
 **실행 수** 메트릭을 사용하여 상위 쿼리가 임시 쿼리인지 분석합니다( `QUERY_CAPTURE_MODE = ALL`을 사용하여 쿼리 저장소를 실행해야 함). 위 다이어그램에서는 **상위 리소스 소비 쿼리** 의 90%가 한 번만 실행되는 것을 볼 수 있습니다.  
  
 또는 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 실행하여 시스템의 총 쿼리 텍스트 수, 쿼리 수 및 계획 수를 파악하고 query_hash와 plan_hash를 비교하여 차이점을 확인할 수 있습니다.  
  
```  
/*Do cardinality analysis when suspect on ad-hoc workloads*/  
SELECT COUNT(*) AS CountQueryTextRows FROM sys.query_store_query_text;  
SELECT COUNT(*) AS CountQueryRows FROM sys.query_store_query;  
SELECT COUNT(DISTINCT query_hash) AS CountDifferentQueryRows FROM  sys.query_store_query;  
SELECT COUNT(*) AS CountPlanRows FROM sys.query_store_plan;  
SELECT COUNT(DISTINCT query_plan_hash) AS  CountDifferentPlanRows FROM  sys.query_store_plan;  
```  
  
 이것은 임시 쿼리가 있는 워크로드에서 얻을 수 있는 하나의 잠재적 결과입니다.  
  
 ![query-store-usage-7](../../relational-databases/performance/media/query-store-usage-7.png "query-store-usage-7")  
  
 쿼리 결과는 쿼리 저장소에 많은 수의 쿼리와 계획이 있음에도 불구하고 해당 query_hash와 plan_hash가 실제로 다르지 않음을 보여 줍니다. 고유한 쿼리 텍스트와 고유한 query_hash 간의 비율(1보다 훨씬 큼)은 워크로드가 매개 변수화하기 적절한 후보임을 나타냅니다. 쿼리 간에 쿼리 텍스트의 일부로 제공된 문자열 상수(매개 변수)만 다를 뿐이기 때문입니다.  
  
 일반적으로 이러한 상황은 응용 프로그램에서 쿼리를 생성(저장 프로시저 또는 매개 변수화된 쿼리를 호출하는 대신)하는 경우 또는 응용 프로그램이 기본적으로 쿼리를 생성하는 개체-관계형 매핑 프레임워크에 의존하는 경우에 발생합니다.  
  
 응용 프로그램 코드에 대한 제어 권한이 있는 경우 저장 프로시저 또는 매개 변수화된 쿼리를 활용하도록 데이터 액세스 계층을 다시 작성하는 것이 좋습니다. 그러나 전체 데이터베이스(모든 쿼리) 또는 query_hash가 동일한 개별 쿼리 템플릿에 대해 쿼리 매개 변수화를 적용하여 응용 프로그램을 변경하지 않고 이 상황을 크게 개선할 수도 있습니다.  
  
 개별 쿼리 템플릿을 사용하는 접근 방식에서는 계획 지침을 만들어야 합니다.  
  
```  
  
/*Apply plan guide for the selected query template*/  
DECLARE @stmt nvarchar(max);  
DECLARE @params nvarchar(max);  
EXEC sp_get_query_template   
    N'<your query text goes here>',  
    @stmt OUTPUT,   
    @params OUTPUT;  
  
EXEC sp_create_plan_guide   
    N'TemplateGuide1',   
    @stmt,   
    N'TEMPLATE',   
    NULL,   
    @params,   
    N'OPTION (PARAMETERIZATION FORCED)';  
```  
  
 계획 지침이 있는 솔루션이 더 정확하지만 여기에는 추가 작업이 필요합니다.  
  
 모든 쿼리(또는 대부분의 쿼리)가 자동 매개 변수화에 적합한 경우 전체 데이터베이스에 대해 `FORCED PARAMETERIZATION` 을 변경하는 것이 더 나은 옵션일 수 있습니다.  
  
```  
  
/*Apply forced parameterization for entire database*/  
ALTER DATABASE <database name> SET PARAMETERIZATION  FORCED;  
```  
  
 이 단계 중 하나를 적용하면 **상위 리소스 소비 쿼리** 에 워크로드의 다른 그림이 표시됩니다.  
  
 ![query-store-usage-8](../../relational-databases/performance/media/query-store-usage-8.png "query-store-usage-8")  
  
 경우에 따라 응용 프로그램이 자동 매개 변수화에 적합하지 않은 많은 쿼리를 생성할 수 있습니다. 이 경우 시스템에 많은 쿼리가 표시되지만 고유한 쿼리와 고유한 query_hash 간의 비율은 1에 가까울 수 있습니다.  
  
 이 경우 ‘optimize for ad hoc workloads’를 설정하여 다시 실행되지 않을 가능성이 큰 쿼리에서 캐시 메모리가 낭비되는 것을 방지할 수 있습니다. 쿼리 저장소에서 이러한 쿼리의 캡처를 방지하려면 `QUERY_CAPTURE_MODE` 를 `AUTO`로 설정합니다.  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
  
sp_configure 'optimize for ad hoc workloads', 1;  
GO  
RECONFIGURE;  
GO  
  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE CLEAR;  
ALTER DATABASE  [QueryStoreTest] SET QUERY_STORE = ON   
    (OPERATION_MODE = READ_WRITE, QUERY_CAPTURE_MODE = AUTO);  
```  
  
## <a name="see-also"></a>참고 항목  
 [쿼리 저장소를 사용하여 성능 모니터링](../../relational-databases/performance/monitoring-performance-by-using-the-query-store.md)   
 [쿼리 저장소에 대한 모범 사례](../../relational-databases/performance/best-practice-with-the-query-store.md)  
  
  
