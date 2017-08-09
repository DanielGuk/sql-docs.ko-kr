---
title: "변수 값 파일 (OracleToSQL) 만들기 | Microsoft Docs"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Variable Value File Creation
- Variable Value File, Variable Value File Validation
ms.assetid: f583d81a-8e34-41b1-8100-ee3a6a82213b
caps.latest.revision: 26
author: sabotta
ms.author: carlasab
manager: v-thobro
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 3ba4def7c054b0d5a65a8ac93698cf6cb432845a
ms.contentlocale: ko-kr
ms.lasthandoff: 08/02/2017

---
# <a name="creating-variable-value-files-oracletosql"></a>변수 값 파일 (OracleToSQL) 만들기
변수 값 파일은 다른 하나의 서버 마이그레이션의 자주 변경 하는 원본 또는 대상 서버 이름이 같은 명령의 매개 변수 값을 구성 하는 XML 파일입니다. 데이터베이스 마이그레이션 다 수 발생 하는 경우 원본 서버의 각 값을 저장 하기 위한 여러 변수 파일을 만든 포함 마스터 스크립트 파일에서 참조 되는 **– v** 명령줄에서 전환 합니다. 이렇게 하면 여러 변수 파일에서 변수 값이 포함 된 몇 가지 스크립트 파일에 정적 값을 유지 관리 합니다.  
  
> [!NOTE]  
> 1.  변수 이름은 접두사를 $ (달러) 기호 접미사. 변수는 변수 값 파일의 값이 지정 되지 않은 경우에 콘솔 실행 프로세스 시간으로 인해 발생 하는 스크립트 파일의 구문 분석 하는 동안 오류가 발생 합니다.  
> 2.  The escape character for **$** is **$$**. 매개 변수 또는 정적 값의 값에 포함 된 경우  **$**  (달러) 기호를 다음  **$$**  변수 대신 문자로 취급 되도록 지정 해야 합니다.  
> 3.  유지 관리 용이성을 위해 변수를 선언할 수 내부 `‘variable-group’` 사용자의 논리적 분리에 대 한 요소는 변수를 정의 합니다.  사용 현황이 요소는 필수입니다.  
  
**예:**  
  
**예제 1:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$project_folder$" value="<project-folder>"/>  
  
    <variable name="$project_name$" value="<project-name>"/>  
  
    <variable name="$project_overwrite$" value="<true/false>"/>  
  
    <variable name="$project_type$" value="<project-type>"/>  
  
  </variable-group>  
  
</variables>  
```  
**예제 2:**  
  
```  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="<server-name>"/>  
  
      <variable name="$TargetDB$" value="<database-name>"/>  
  
      <variable name="$TargetUserName$" value="<user-name>"/>  
  
      <variable name="$TargetPassword$" value="<password>"/>  
  
      <variable name="$TrustedConnection$" value="<true/false>"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="<object-name>"/>  
  
      <variable name="$ObjectName2$" value="<object-name>"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="next-step"></a>다음 단계  
운영 콘솔에 다음 단계는 [만드는 서버 연결 파일 &#40; OracleToSQL &#41;](../../ssma/oracle/creating-the-server-connection-files-oracletosql.md)  
  
## <a name="see-also"></a>관련 항목:  
[서버 파일 (Oracle) 만들기](http://msdn.microsoft.com/en-us/002f129e-0868-48ad-a4b4-c68b5007e12e)  
  
