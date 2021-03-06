---
title: CompoundCurve | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: ae357f9b-e3e2-4cdf-af02-012acda2e466
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6f109dcab6d7cf6280e15cdfb1bb2f5ad3b2f041
ms.sourcegitcommit: 87f29b23d5ab174248dab5d558830eeca2a6a0a4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51018148"
---
# <a name="compoundcurve"></a>CompoundCurve
  `CompoundCurve`는 geometry 또는 geography 유형의 연속적인 `CircularString` 또는 `LineString` 인스턴스가 하나 이상 포함된 컬렉션입니다.  
  
> [!IMPORTANT]  
>  자세한 설명 및 예가이 릴리스의 새로운 공간 기능에 대 한 포함 된 `CompoundCurve` 하위 유형, 백서를 다운로드 [SQL Server 2012의 새로운 공간 기능](http://go.microsoft.com/fwlink/?LinkId=226407)합니다.  
  
 빈 `CompoundCurve` 인스턴스를 인스턴스화할 수 있지만 `CompoundCurve`가 유효한 인스턴스가 되려면 다음 조건을 충족해야 합니다.  
  
1.  적어도 하나의 `CircularString` 또는 `LineString` 인스턴스를 포함해야 합니다.  
  
2.  `CircularString` 또는 `LineString` 인스턴스의 시퀀스는 연속적이어야 합니다.  
  
 경우는 `CompoundCurve` 여러 개의 시퀀스를 포함 `CircularString` 고 `LineString` 인스턴스의 종료 끝점 마지막 인스턴스를 제외한 모든 인스턴스의 시퀀스에서 다음 인스턴스의 시작 끝점 이어야 합니다. 즉, 시퀀스에서 이전 인스턴스의 끝 점이 (4 3 7 2)인 경우 시퀀스에서 다음 인스턴스의 시작 점은 (4 3 7 2)여야 합니다. 점의 Z(높이) 및 M(측정값) 값도 동일해야 합니다. 두 점이 다른 경우 `System.FormatException` 이 발생합니다. `CircularString`의 점은 Z 또는 M 값을 가지고 있지 않아도 됩니다. 이전 인스턴스의 종료 점에 대해 Z 또는 M 값이 지정되지 않은 경우 다음 인스턴스의 시작 점은 Z 또는 M 값을 포함할 수 없습니다. 이전 시퀀스의 종료 점이 (4 3)이면 다음 시퀀스의 시작 점은 (4 3)이어야 하지 (4 3 7 2)일 수는 없습니다. `CompoundCurve` 인스턴스의 모든 점은 Z 값을 가지고 있지 않거나 같은 Z 값을 가지고 있어야 합니다.  
  
## <a name="compoundcurve-instances"></a>CompoundCurve 인스턴스  
 다음 그림에서는 유효한 `CompoundCurve` 형식을 보여 줍니다.  
  
 ![](../../database-engine/media/f278742e-b861-4555-8b51-3d972b7602bf.png "f278742e-b861-4555-8b51-3d972b7602bf")  
  
### <a name="accepted-instances"></a>허용되는 인스턴스  
 `CompoundCurve` 인스턴스는 빈 인스턴스이거나 다음 조건을 충족하는 경우 허용됩니다.  
  
1.  `CompoundCurve` 인스턴스에 포함된 모든 인스턴스가 허용되는 원호 세그먼트 인스턴스인 경우. 허용되는 원호 세그먼트 인스턴스에 대한 자세한 내용은 [LineString](linestring.md) 및 [CircularString](circularstring.md)을 참조하세요.  
  
2.  `CompoundCurve` 인스턴스의 모든 원호 세그먼트가 연결되어 있는 경우. 즉, 이어지는 각 원호 세그먼트의 첫 번째 점이 앞에 있는 원호 세그먼트의 마지막 점과 같아야 합니다.  
  
    > [!NOTE]  
    >  여기에는 Z와 M 좌표가 포함됩니다. 따라서 네 후보 X, Y, Z 및 M이 모두 같아야 합니다.  
  
3.  포함된 인스턴스 중 비어 있는 인스턴스가 없는 경우  
  
 다음 예에서는 허용되는 `CompoundCurve` 인스턴스를 보여 줍니다.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
```  
  
 다음 예에서는 허용되지 않는 `CompoundCurve` 인스턴스를 보여 줍니다. 이 인스턴스에서는 `System.FormatException`이 발생합니다.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING EMPTY)';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (1 0, 2 0))';  
```  
  
### <a name="valid-instances"></a>유효한 인스턴스  
 `CompoundCurve` 인스턴스는 다음 조건을 충족하는 경우 유효합니다.  
  
1.  `CompoundCurve` 인스턴스가 허용되는 경우  
  
2.  `CompoundCurve` 인스턴스에 포함된 모든 원호 세그먼트 인스턴스가 유효한 인스턴스인 경우  
  
 다음 예에서는 유효한 `CompoundCurve` 인스턴스를 보여 줍니다.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE EMPTY';  
DECLARE @g2 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 0, 0 1, -1 0), (-1 0, 2 0))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
  
```  
  
 `CircularString` 인스턴스가 유효하므로 `@g3`은 유효합니다. 유효성에 대 한 자세한 내용은 합니다 `CircularString` 인스턴스를 참조 하십시오 [CircularString](circularstring.md)합니다.  
  
 다음 예에서는 유효하지 않은 `CompoundCurve` 인스턴스를 보여 줍니다.  
  
```  
DECLARE @g1 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 1 1, 1 1), (1 1, 3 5, 5 4, 3 5))';  
DECLARE @g2 geometry = 'COMPOUNDCURVE((1 1, 1 1))';  
DECLARE @g3 geometry = 'COMPOUNDCURVE(CIRCULARSTRING(1 1, 2 3, 1 1))';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid();  
```  
  
 두 번째 인스턴스가 유효한 LineString 인스턴스가 아니기 때문에 `@g1`은 잘못되었습니다. `LineString` 인스턴스가 잘못되었기 때문에 `@g2`은 잘못되었습니다. `CircularString` 인스턴스가 잘못되었기 때문에 `@g3`은 잘못되었습니다. 올바른 대 한 자세한 내용은 `CircularString` 하 고 `LineString` 인스턴스를 참조 하세요 [CircularString](circularstring.md) 하 고 [LineString](linestring.md)합니다.  
  
## <a name="examples"></a>예  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-compooundcurve"></a>1. 빈 CompooundCurve를 사용하여 기하 도형 인스턴스 인스턴스화  
 다음 예에서는 빈 `CompoundCurve` 인스턴스를 만드는 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE EMPTY');  
```  
  
### <a name="b-declaring-and-instantiating-a-geometry-instance-using-a-compoundcurve-in-the-same-statement"></a>2. 동일한 문에서 CompoundCurve를 사용하여 기하 도형 인스턴스 선언 및 인스턴스화  
 다음 예에서는 동일한 문에서 `geometry` 을 사용하여 `CompoundCurve`인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g geometry = 'COMPOUNDCURVE ((2 2, 0 0),CIRCULARSTRING (0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0))';  
```  
  
### <a name="c-instantiating-a-geography-instance-with-a-compoundcurve"></a>3. CompoundCurve를 사용하여 지리 인스턴스 인스턴스화  
 다음 예에서는 `CompoundCurve`를 사용하여 `geography` 인스턴스를 선언하고 초기화하는 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
```  
  
### <a name="d-storing-a-square-in-a-compoundcurve-instance"></a>4. CompoundCurve 인스턴스에 사각형 저장  
 다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 사각형을 저장하는 두 가지 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g1 geometry, @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3), (1 3, 3 3),(3 3, 3 1), (3 1, 1 1))');  
SET @g2 = geometry::Parse('COMPOUNDCURVE((1 1, 1 3, 3 3, 3 1, 1 1))');  
SELECT @g1.STLength(), @g2.STLength();  
```  
  
 `@g1` 및 `@g2` 의 길이는 같습니다. 이 예에서는 `CompoundCurve` 인스턴스가 하나 이상의 `LineString` 인스턴스를 저장할 수 있음을 알 수 있습니다.  
  
### <a name="e-instantiating-a-geometry-instance-using-a-compoundcurve-with-multiple-circularstrings"></a>5. 여러 CircularString을 포함하는 CompoundCurve를 사용하여 기하 도형 인스턴스 인스턴스화  
 다음 예에서는 서로 다른 두 `CircularString` 인스턴스를 사용하여 `CompoundCurve`를 초기화하는 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT @g.STLength();  
```  
  
 이는 다음 출력을 생성합니다. 12.566370… 4∏와 동일합니다. 예에서 `CompoundCurve` 인스턴스는 반지름이 2인 원을 저장합니다. 앞의 두 코드 예에서는 `CompoundCurve`를 사용할 필요가 없었습니다. 첫 번째 예의 경우 `LineString` 인스턴스를 사용하면 더 간단했을 것이고 두 번째 예의 경우 `CircularString` 인스턴스를 사용하면 더 간단했을 것입니다. 하지만 다음 예에서는 `CompoundCurve` 를 사용하는 것이 더 좋은 경우를 보여 줍니다.  
  
### <a name="f-using-a-compoundcurve-to-store-a-semicircle"></a>6. CompoundCurve를 사용하여 반원 저장  
 다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 반원을 저장합니다.  
  
```tsql  
DECLARE @g geometry;  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 0 2))');  
SELECT @g.STLength();  
```  
  
### <a name="g-storing-multiple-circularstring-and-linestring-instances-in-a-compoundcurve"></a>7. CompoundCurve에 여러 개의 CircularString 및 LineString 인스턴스 저장  
 다음 예에서는 `CircularString` 를 사용하여 여러 개의 `LineString` 및 `CompoundCurve`인스턴스를 저장하는 방법을 보여 줍니다.  
  
```tsql  
DECLARE @g geometry  
SET @g = geometry::Parse('COMPOUNDCURVE((3 5, 3 3), CIRCULARSTRING(3 3, 5 1, 7 3), (7 3, 7 5), CIRCULARSTRING(7 5, 5 7, 3 5))');  
SELECT @g.STLength();  
```  
  
### <a name="h-storing-instances-with-z-and-m-values"></a>8. Z 및 M 값이 있는 인스턴스 저장  
 다음 예에서는 `CompoundCurve` 인스턴스를 사용하여 Z 값과 M 값이 모두 있는 `CircularString` 및 `LineString` 인스턴스 시퀀스를 저장하는 방법을 보여 줍니다.  
  
```tsql  
SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(7 5 4 2, 5 7 4 2, 3 5 4 2), (3 5 4 2, 8 7 4 2))');  
```  
  
### <a name="i-illustrating-why-circularstring-instances-must-be-explicitly-declared"></a>9. CircularString 인스턴스를 명시적으로 선언해야 하는 이유에 대한 설명  
 다음 예에서는 `CircularString` 인스턴스를 명시적으로 선언해야 하는 이유를 보여 줍니다. 프로그래머는 `CompoundCurve` 인스턴스에 원을 저장하려고 합니다.  
  
```tsql  
DECLARE @g1 geometry;    
DECLARE @g2 geometry;  
SET @g1 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), (4 2, 2 4, 0 2))');  
SELECT 'Circle One', @g1.STLength() AS Perimeter;  -- gives an inaccurate amount  
SET @g2 = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(0 2, 2 0, 4 2), CIRCULARSTRING(4 2, 2 4, 0 2))');  
SELECT 'Circle Two', @g2.STLength() AS Perimeter;  -- now we get an accurate amount  
```  
  
 다음과 같은 출력이 생성됩니다.  
  
```  
Circle One11.940039…  
Circle Two12.566370…  
```  
  
 Circle Two의 둘레는 대략 4∏로 이 값은 둘레의 실제 값입니다. 하지만 Circle One의 둘레는 매우 부정확합니다. Circle One의 `CompoundCurve` 인스턴스는 하나의 원호 세그먼트(ABC)와 두 개의 선분(CD, DA)을 저장합니다. 원을 정의하려면 `CompoundCurve` 인스턴스는 두 개의 원호 세그먼트(ABC, CDA)를 저장해야 합니다. 1 `LineString` 인스턴스는 Circle One의 `CompoundCurve` 인스턴스에 두 번째 점 집합(4 2, 2 4, 0 2)을 정의합니다. `CircularString` 내부에서 `CompoundCurve`인스턴스를 명시적으로 선언해야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [STIsValid&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STLength&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint&#40;geometry 데이터 형식&#41;](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [LineString](linestring.md)   
 [CircularString](circularstring.md)   
 [공간 데이터 형식 개요](spatial-data-types-overview.md)   
 [점](point.md)  
  
  
