---
title: 컬렉션 (Visual c + + 구문에 대 한 ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- ADO for Visual C++ syntax [ADO]
- syntax indexes [ADO], ADO for Visual C++ syntax
- collections [ADO], ADO for Visual C++ syntax
ms.assetid: 6a0109a0-f2d9-4f7c-8e1e-42763f9acaea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d94570a337f564588b2709fd292eab5ed5396dc4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47679881"
---
# <a name="collections-ado-for-visual-c-syntax"></a>컬렉션(Visual C++ 구문에 대한 ADO)
## <a name="parameters"></a>매개 변수  
  
### <a name="methods"></a>메서드  
  
```  
Append(IDispatch *Object);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Append 메서드(ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete 메서드(ADO 매개 변수 컬렉션)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh 메서드(ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>속성  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, _ADOParameter **ppvObject);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Count 속성(ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item 속성(ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="fields"></a>필드  
  
### <a name="methods"></a>메서드  
  
```  
Append(BSTR bstrName, DataTypeEnum Type, long DefinedSize, FieldAttributeEnum Attrib);  
Delete(VARIANT Index);  
Refresh(void);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Append 메서드(ADO)](../../../ado/reference/ado-api/append-method-ado.md)  
  
-   [Delete 메서드(ADO 매개 변수 컬렉션)](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)  
  
-   [Refresh 메서드(ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>속성  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOField **ppvObject);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Count 속성(ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item 속성(ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="errors"></a>오류  
  
### <a name="methods"></a>메서드  
  
```  
Clear(void);  
Refresh(void);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Clear 메서드(ADO)](../../../ado/reference/ado-api/clear-method-ado.md)  
  
-   [Refresh 메서드(ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>속성  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOError **ppvObject);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Count 속성(ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item 속성(ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="properties"></a>속성  
  
### <a name="methods"></a>메서드  
  
```  
Refresh(void);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Refresh 메서드(ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)  
  
### <a name="properties"></a>속성  
  
```  
get_Count(long *c);  
get_Item(VARIANT Index, ADOProperty **ppvObject);  
```  
  
 자세한 내용은 다음을 참조하세요.  
  
-   [Count 속성(ADO)](../../../ado/reference/ado-api/count-property-ado.md)  
  
-   [Item 속성(ADO)](../../../ado/reference/ado-api/item-property-ado.md)  
  
## <a name="see-also"></a>관련 항목  
 [Errors 컬렉션 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)   
 [필드 컬렉션 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameters 컬렉션 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Properties 컬렉션(ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
