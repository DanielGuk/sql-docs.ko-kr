---
title: 개체 처리 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 711909975507e7382fff80d9b83483d54aad4c6f
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145668"
---
# <a name="processing-objects-xmla"></a>개체 처리(XMLA)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], 처리가 단계 또는 일련의 단계를 전환 하는 데이터를 비즈니스 분석용 정보로 합니다. 처리 방법은 개체 유형에 따라 달라지지만 처리는 항상 데이터를 정보로 변환하는 과정의 일부입니다.  
  
 프로세스에는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 사용할 수는 [프로세스](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) 명령입니다. `Process` 명령이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 처리할 수 있는 개체는 다음과 같습니다.  
  
-   큐브  
  
-   데이터베이스  
  
-   차원  
  
-   측정값 그룹  
  
-   마이닝 모델  
  
-   마이닝 구조  
  
-   파티션  
  
 `Process` 명령에는 개체 처리를 제어하기 위해 설정할 수 있는 다양한 속성이 있습니다. 제어할 수 있는 `Process` 명령의 속성으로는 처리량, 처리할 개체, 아웃오브 라인 바인딩 사용 여부, 오류 해결 방법 및 쓰기 저장(writeback) 테이블 관리 방법이 있습니다.  
  
## <a name="specifying-processing-options"></a>처리 옵션 지정  
 합니다 [형식](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) 의 속성을 `Process` 명령 개체를 처리할 때 사용할 처리 옵션을 지정 합니다. 처리 옵션에 대한 자세한 내용은 [처리 옵션 및 설정&#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md)을 참조하세요.  
  
 다음 표에서는 `Type` 속성에 대한 상수와 각 상수를 사용하여 처리할 수 있는 다양한 개체를 보여 줍니다.  
  
|`Type` 값|적용 가능한 개체|  
|--------------------|------------------------|  
|*ProcessFull*|큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션|  
|*ProcessAdd*|차원, 파티션|  
|*ProcessUpdate*|차원|  
|*ProcessIndexes*|차원, 큐브, 측정값 그룹, 파티션|  
|*ProcessData*|차원, 큐브, 측정값 그룹, 파티션|  
|*ProcessDefault*|큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션|  
|*ProcessClear*|큐브, 데이터베이스, 차원, 측정값 그룹, 마이닝 모델, 마이닝 구조, 파티션|  
|*ProcessStructure*|큐브, 마이닝 구조|  
|*ProcessClearStructureOnly*|마이닝 구조|  
|*ProcessScriptCache*|Cube|  
  
 처리에 대 한 자세한 내용은 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 개체를 참조 하세요 [다차원 모델 개체 처리](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)합니다.  
  
## <a name="specifying-objects-to-be-processed"></a>처리할 개체 지정  
 [개체](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) 의 속성을 `Process` 명령을 처리할 개체의 개체 식별자를 포함 합니다. `Process` 명령에는 한 개체만 지정할 수 있지만 개체를 처리할 때 모든 자식 개체도 처리됩니다. 예를 들어 큐브의 측정값 그룹을 처리하면 해당 측정 그룹의 모든 파티션이 처리되고, 데이터베이스를 처리하면 데이터베이스에 포함된 큐브, 차원 및 마이닝 구조 등의 모든 개체가 처리됩니다.  
  
 `ProcessAffectedObjects` 명령의 `Process` 특성을 true로 설정하면 지정된 개체 처리 작업의 영향을 받는 관련 개체도 모두 처리됩니다. 예를 들어 차원을 사용 하 여 증분 업데이트 되는 *ProcessUpdate* 처리 옵션을 `Process` 명령을 추가 또는 삭제 되는 멤버로 인해 집계가 무효화 된 파티션의 이기도 처리 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 경우 `ProcessAffectedObjects` 설정을 true로 합니다. 이 경우 단일 `Process` 명령이 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스의 여러 개체를 처리할 수 있지만 `Process` 명령에 지정된 단일 개체 이외에 추가로 처리되어야 하는 개체는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 결정합니다.  
  
 하지만 `Process` 명령 내에서 `Batch` 명령을 여러 개 사용하면 차원과 같은 여러 개체를 동시에 처리할 수 있습니다. 일괄 처리 작업을 수행하면 `ProcessAffectedObjects` 특성을 사용할 때보다 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 수행되는 개체의 순차 및 병렬 처리를 보다 세부적으로 제어할 수 있으며 대규모 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스의 처리 방법을 조정할 수 있습니다. 일괄 처리 작업을 수행 하는 방법에 대 한 자세한 내용은 참조 하세요. [일괄 처리 작업 수행 &#40;XMLA&#41;](performing-batch-operations-xmla.md)합니다.  
  
## <a name="specifying-out-of-line-bindings"></a>아웃오브 라인 바인딩 지정  
 경우는 `Process` 명령이 포함 되어 있지는 `Batch` 명령인 있습니다에서 아웃오브 라인 바인딩을 선택적으로 지정할 수는 [바인딩](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), 및 [DataSourceView ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) 의 속성을 `Process` 처리할 개체에 대 한 명령입니다. 아웃오브 라인 바인딩은 `Process` 명령이 실행되는 동안에만 바인딩이 존재하는 데이터 원본, 데이터 원본 뷰 및 기타 개체에 대한 참조로, 처리되는 개체에 연결된 기존 바인딩을 모두 재정의합니다. 아웃오브 라인 바인딩을 지정하지 않으면 처리할 개체에 현재 연결되어 있는 바인딩이 사용됩니다.  
  
 아웃오브 라인 바인딩은 다음과 같은 경우에 사용됩니다.  
  
-   행이 두 번 계산되지 않도록 기존 팩트 테이블에 대한 필터나 대체 팩트 테이블을 지정해야 하는 파티션을 증분 처리하는 경우  
  
-   데이터 흐름 태스크를 사용 하 여 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 차원, 마이닝 모델 또는 파티션을 처리 하는 동안 데이터를 제공 합니다.  
  
 아웃오브 라인 바인딩은 ASSL(Analysis Services Scripting Language)의 일부로 설명됩니다. ASSL의 아웃오브 라인 바인딩에 대 한 자세한 내용은 참조 하세요. [데이터 원본 및 바인딩 &#40;SSAS 다차원&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)합니다.  
  
### <a name="incrementally-updating-partitions"></a>파티션 증분 업데이트  
 파티션에 대해 지정된 바인딩은 파티션 내에서 이미 집계된 팩트 테이블 데이터를 참조하기 때문에 이미 처리된 파티션을 증분 업데이트하려면 아웃오브 라인 바인딩이 필요합니다. `Process` 명령을 사용하여 이미 처리된 파티션을 증분 업데이트하는 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 다음과 같은 동작을 수행합니다.  
  
-   증분 업데이트할 파티션과 동일한 구조의 임시 파티션을 만듭니다.  
  
-   `Process` 명령에 지정된 아웃오브 라인 바인딩을 사용하여 임시 파티션을 처리합니다.  
  
-   임시 파티션을 선택된 기존 파티션과 병합합니다.  
  
 XML for Analysis (XMLA) 사용 하 여 파티션을 병합 하는 방법에 대 한 자세한 내용은 참조 하세요. [파티션 병합 &#40;XMLA&#41;](merging-partitions-xmla.md)합니다.  
  
## <a name="handling-processing-errors"></a>처리 오류 해결  
 합니다 [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) 의 속성을 `Process` 명령을 사용 하면 개체를 처리 하는 동안 발생 한 오류를 처리 하는 방법을 지정할 수 있습니다. 예를 들어 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 차원을 처리하는 동안 키 특성의 키 열에 중복 값이 있는 경우 특성 키는 고유해야 하므로 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 에서는 중복 레코드를 삭제합니다. 기반으로 합니다 [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) 속성을 `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 수:  
  
-   오류를 무시하고 차원을 계속 처리합니다.  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서 중복 키가 있음을 알리는 메시지를 반환하고 처리를 계속합니다.  
  
 `ErrorConfiguration` 명령을 실행하는 동안 `Process`에서 옵션을 제공하는 유사한 경우가 많이 있습니다.  
  
## <a name="managing-writeback-tables"></a>쓰기 저장(writeback) 테이블 관리  
 `Process` 명령을 실행하는 동안 아직 완전히 처리되지 않은 쓰기 가능한 파티션이나 그러한 파티션에 대한 큐브 또는 측정값 그룹이 발생한다면 해당 파티션에 대한 쓰기 저장(writeback) 테이블이 아직 존재하지 않는 것일 수 있습니다. [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) 속성을는 `Process` 명령은 확인 여부를 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 쓰기 저장 테이블을 만들어야 합니다.  
  
## <a name="examples"></a>예  
  
### <a name="description"></a>Description  
 다음 예제에서는 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 예제 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스를 완전히 처리합니다.  
  
### <a name="code"></a>코드  
  
```  
<Process xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a>Description  
 다음 예제에서는 증분 방식으로 처리 하는 **Internet_Sales_2004** 의 파티션 합니다 **Internet Sales** 측정값 그룹을 **Adventure Works DW** 큐브에서 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 샘플 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 데이터베이스입니다. `Process` 명령은 주문에 대 한 집계 2006 년 12 월 31 일 이후 날짜에 추가 파티션을 아웃오브 라인 쿼리 바인딩을 사용 하 여는 `Bindings` 의 속성을 `Process` 를 생성할 팩트 테이블 행을 검색 하는 명령 파티션에 추가할 집계 합니다.  
  
### <a name="code"></a>코드  
  
```  
<Process ProcessAffectedObjects="true" xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
