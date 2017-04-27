---
title: "HEX(SSIS 식) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "16진수 데이터"
  - "HEX 함수"
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
caps.latest.revision: 36
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 36
---
# HEX(SSIS 식)
  정수의 16진수 값을 나타내는 문자열을 반환합니다.  
  
## 구문  
  
```  
  
HEX(integer_expression)  
```  
  
## 인수  
 *integer_expression*  
 부호 있는 정수 또는 부호 없는 정수입니다.  
  
## 결과 형식  
 DT_WSTR  
  
## 주의  
 *integer_expression*이 null이면 HEX는 null을 반환합니다.  
  
 *integer_expression* 인수는 정수여야 합니다. 자세한 내용은 [Integration Services Data Types](../../integration-services/data-flow/integration-services-data-types.md)을 참조하세요.  
  
 반환 결과는 0x 접두사와 같은 한정자를 포함하지 않습니다. 접두사를 포함하려면 +(연결) 연산자를 사용합니다. 자세한 내용은 [+&#40;연결&#41;&#40;SSIS 식&#41;](../../integration-services/expressions/concatenate-ssis-expression.md)를 참조하세요.  
  
 HEX 표기에 사용되는 문자 A - F는 대문자로 표시됩니다.  
  
 정수 데이터 형식의 결과 문자열 길이는 다음과 같습니다.  
  
-   DT_I1과 DT_UI1은 최대 길이가 2인 문자열을 반환합니다.  
  
-   DT_I2와 DT_UI2는 최대 길이가 4인 문자열을 반환합니다.  
  
-   DT_I4와 DT_UI4는 최대 길이가 8인 문자열을 반환합니다.  
  
-   DT_I8과 DT_UI8은 최대 길이가 16인 문자열을 반환합니다.  
  
## 식 예  
 이 예에서는 숫자 리터럴을 사용합니다. 이 함수는 값 190을 반환합니다.  
  
```  
HEX(400)   
```  
  
 이 예에서는 **ReorderPoint** 열을 사용합니다. 열 데이터 형식은 **smallint**입니다. **ReorderPoint** 가 750이면 2EE를 반환합니다.  
  
```  
HEX(ReorderPoint)   
```  
  
 이 예에서는 시스템 변수 **LocaleID**를 사용합니다. **LocaleID** 가 1033이면 409를 반환합니다.  
  
```  
HEX(@LocaleID)  
```  
  
## 관련 항목:  
 [함수&#40;SSIS 식&#41;](../../integration-services/expressions/functions-ssis-expression.md)  
  
  