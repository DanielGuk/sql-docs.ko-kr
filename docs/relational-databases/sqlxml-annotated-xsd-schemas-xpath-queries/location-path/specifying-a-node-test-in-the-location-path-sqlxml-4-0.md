---
title: 위치 경로 (SQLXML 4.0)에서 노드 테스트 지정 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: douglaslMS
ms.author: douglasl
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2883b1645dfe1114fc40f63c576797b477ae0ea5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47792021"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a>위치 경로에 노드 테스트 지정(SQLXML 4.0)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  노드 테스트는 위치 단계에서 선택되는 노드 유형을 지정합니다. 모든 축 (**자식**를 **부모**를 **특성**, 또는 **자체**) 주 노드 형식이 있습니다. 에 대 한 합니다 **특성** 축의 주 노드 유형은입니다  **\<특성 >** 합니다. 에 대 한 합니다 **부모**, **자식**, 및 **셀프** 축 주 노드 유형은입니다  **\<요소 >** 합니다.  
  
> [!NOTE]  
>  와일드카드 노드 테스트 *(예: `child::*`)는 지원되지 않습니다.  
  
## <a name="node-test-example-1"></a>노드 테스트: 예제 1  
 위치 경로 `child::Customer` 선택  **\<고객 >** 컨텍스트 노드의 요소 자식이 있습니다.  
  
 이 예에서는 `child`가 축이고 `Customer`가 노드 테스트입니다. 에 대 한 주 노드 유형은 합니다 **자식** 축은  **\<요소 >** 합니다. 따라서 노드 테스트는 TRUE를  **\<고객 >** 노드를  **\<요소 >** 노드. 컨텍스트 노드의 없으면  **\<고객 >** 자식 노드의 빈 집합이 반환 됩니다.  
  
## <a name="node-test-example-2"></a>노드 테스트: 예제 2  
 위치 경로 `attribute::CustomerID` 를 선택 합니다 **CustomerID** 컨텍스트 노드의 특성입니다.  
  
 이 예에서는 `attribute`가 축이고 `CustomerID`가 노드 테스트입니다. 주 노드 유형의 합니다 **특성** 축은  **\<특성 >** 합니다. 따라서 노드 테스트는 TRUE **CustomerID** 되는  **\<특성 >** 노드. 컨텍스트 노드의 없으면 **CustomerID**, 빈 노드 집합이 반환 됩니다.  
  
> [!NOTE]  
>  이 구현의 XPath 위치 단계를 참조 하는 경우에  **\<요소 >** 요소나  **\<특성 >** 오류가 생성 되는 스키마에서 선언 되지 않은 형식. 이 동작은 빈 노드 집합을 반환하는 MSXML에서의 XPath 구현과는 다릅니다.  
  
## <a name="abbreviated-syntax-for-the-axes"></a>축의 축약형 구문  
 위치 경로에 대한 다음 축약형 구문이 지원됩니다.  
  
-   `attribute::`는 `@` 기호로 축약할 수 있습니다.  
  
     위치 경로 `Customer[@CustomerID="ALFKI"]`는 `child::Customer[attribute::CustomerID="ALFKI"]`와 같습니다.  
  
-   `child::`는 위치 단계에서 생략할 수 있습니다.  
  
     따라서 **자식** 이 기본 축입니다. 위치 경로 `Customer/Order`는 `child::Customer/child::Order`와 같습니다.  
  
-   `self::node()`는 한 개의 마침표(.)로 축약할 수 있으며, `parent::node()`는 두 개의 마침표(..)로 축약할 수 있습니다.  
  
  
