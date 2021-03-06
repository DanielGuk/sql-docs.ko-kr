---
title: 필드 (ADO-WFC 구문) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Field collection [ADO], ADO/WFC syntax
ms.assetid: 7e01cb24-2338-4f92-ad46-8d97248e1a4d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 709629c6ef42b8ffeb65959ab9491bbe3c178ab3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47613841"
---
# <a name="field-ado---wfc-syntax"></a>필드(ADO - WFC 구문)
## <a name="package-commswfcdata"></a>package com.ms.wfc.data  
  
### <a name="methods"></a>메서드  
  
```  
public void appendChunk(byte[] bytes)  
public void appendChunk(char[] chars)  
public void appendChunk(String chars)  
public byte[] getByteChunk(int len)  
public char[] getCharChunk(int len)  
public String getStringChunk(int len)  
```  
  
### <a name="properties"></a>속성  
  
```  
public int getActualSize()  
public int getAttributes()  
public void setAttributes(int pl)  
public com.ms.com.IUnknown getDataFormat()  
public void setDataFormat(com.ms.com.IUnknown format)  
```  
  
 (자세한 내용은 com.ms.wfc.data.IDataFormat 인터페이스에 대 한 설명서 참조).  
  
```  
public int getDefinedSize()  
public void setDefinedSize(int pl)  
public String getName()  
public int getNumericScale()  
public void setNumericScale(byte pbNumericScale)  
public Variant getOriginalValue()  
public int getPrecision()  
public void setPrecision(byte pbPrecision)  
public int getType()  
public void setType(int pDataType)  
public Variant getUnderlyingValue()  
public Variant getValue()  
public void setValue(Variant value)  
public AdoProperties getProperties()  
```  
  
### <a name="field-accessor-methods"></a>필드 접근자 메서드  
 합니다 [값](../../../ado/reference/ado-api/value-property-ado.md) 의 속성을 [필드](../../../ado/reference/ado-api/field-object.md) 개체는 개체의 콘텐츠를 가져오거나 설정 합니다. 콘텐츠는 변형에 값을 할당할 수 있는 개체의 형식 및 여러 데이터 형식으로 표시 됩니다.  
  
 ADO/WFC 구현를 **값** 속성을 합니다 **getValue** ; VARIANT를 반환 하는 메서드 및 **setValue** VARIANT를 인수로 사용 하는 메서드를 합니다. 변형은 Microsoft Visual Basic 같은 특정 언어에서 매우 효율적입니다.  
  
 외에 **값** 속성인 ADO/WFC 제공 *접근자* Java 데이터 형식 가져오기 및 설정의 콘텐츠를 사용 하는 방법 **필드** 개체입니다. 이러한 메서드 중 대부분은 폼의 이름이 **가져오기 * * * DataType* 또는 **설정 * * * DataType*합니다.  
  
 두 가지 주목할 만한 예외가 있습니다: 중 하나는 **getObject** 메서드는 지정 된 클래스도 강제 변환할 개체를 반환 합니다. 방법이 없는 **getNull** 속성 대신는 **isNull** 필드가 null 인지 여부를 나타내는 부울 값을 반환 하는 속성입니다.  
  
```  
public native boolean getBoolean();  
public void setBoolean(boolean v)  
public native byte getByte();  
public void setByte(byte v)  
public native byte[] getBytes();  
public void setBytes(byte[] v)  
public native double getDouble();  
public void setDouble(double v)  
public native float getFloat();  
public void setFloat(float v)  
public native int getInt();  
public void setInt(int v)  
public native long getLong();  
public void setLong(long v)  
public native short getShort();  
public void setShort(short v)  
public native String getString();  
public void setString(String v)  
public native boolean isNull();  
public void setNull()  
public Object getObject()  
public Object getObject(Class c)  
public void setObject(Object value)  
```  
  
## <a name="see-also"></a>관련 항목  
 [Field 개체](../../../ado/reference/ado-api/field-object.md)
