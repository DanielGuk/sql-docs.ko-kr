---
title: sp_db_selective_xml_index (TRANSACT-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_db_selective_xml_index_TSQL
- sp_db_selective_xml_index
dev_langs:
- TSQL
helpviewer_keywords:
- sp_db_selective_xml_index procedure
ms.assetid: 017301a2-4a23-4e68-82af-134f3d4892b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 07145e608c850a877a984c7467da6b8974f0d151
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47744601"
---
# <a name="spdbselectivexmlindex-transact-sql"></a>sp_db_selective_xml_index(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 데이터베이스에서 선택적 XML 인덱스 기능을 설정 및 해제합니다. 매개 변수 없이 호출할 경우, 특정 데이터베이스에서 선택적 XML 인덱스가 설정되어 있으면 저장 프로시저에서 1을 반환합니다.  
  
> [!NOTE]  
>  이 저장된 프로시저를 사용 하 여 선택적 XML 인덱스를 해제 하려면 데이터베이스 해야 단순 복구 모드로 설정 하 여 사용 하는 [ALTER DATABASE SET 옵션 &#40;TRANSACT-SQL&#41; ](../../t-sql/statements/alter-database-transact-sql-set-options.md) 명령입니다.  
  
 ![항목 링크 아이콘](../../database-engine/configure-windows/media/topic-link.gif "항목 링크 아이콘") [Transact-SQL 구문 규칙](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>구문  
  
```sql  
  
      sys.sp_db_selective_xml_index[[ @db_name = ] 'db_name'],   
[[ @action = ] 'action']  
```  
  
## <a name="arguments"></a>인수  
 [ **= @ db_name** ] **'***db_name***'**  
 선택적 XML 인덱스를 설정 또는 해제할 데이터베이스 이름입니다. 하는 경우 *db_name* 가 NULL 이면 현재 데이터베이스로 간주 됩니다.  
  
 [  **@action =** ] **'***동작***'**  
 인덱스를 설정 또는 해제할지 여부를 결정합니다. 'on', ‘true’, ‘off’ 또는 ‘false’가 아닌 다른 값을 전달하면 오류가 발생합니다.  
  
```  
  
Allowed values: 'on', 'off', 'true', 'false'  
```  
  
## <a name="return-code-values"></a>반환 코드 값  
 **1** 특정 데이터베이스에서 선택적 XML 인덱스를 사용 하는 경우.  
  
## <a name="examples"></a>예  
  
### <a name="a-enable-selective-xml-index-functionality"></a>1. 선택적 XML 인덱스 기능 설정  
 다음 예에서는 현재 데이터베이스에서 선택적 XML 인덱스를 설정합니다.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'on';  
GO  
```  
  
 다음 예에서는 AdventureWorks2012 데이터베이스에서 선택적 XML 인덱스를 설정합니다.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'true';  
GO  
```  
  
### <a name="b-disable-selective-xml-index-functionality"></a>2. 선택적 XML 인덱스 기능 해제  
 다음 예에서는 현재 데이터베이스에서 선택적 XML 인덱스를 해제합니다.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = NULL  
  , @action = N'off';  
GO  
```  
  
 다음 예에서는 AdventureWorks2012 데이터베이스에서 선택적 XML 인덱스를 해제합니다.  
  
```  
EXECUTE sys.sp_db_selective_xml_index  
    @db_name = N'AdventureWorks2012'  
  , @action = N'false';  
GO  
```  
  
### <a name="c-detect-if-selective-xml-index-is-enabled"></a>3. 선택적 XML 인덱스가 설정되어 있는지 확인  
 다음 예에서는 선택적 XML 인덱스가 설정되어 있는지 확인합니다. 선택적 XML 인덱스가 설정되어 있으면 1이 반환됩니다.  
  
```  
EXECUTE sys.sp_db_selective_xml_index;  
GO  
```  
  
## <a name="see-also"></a>관련 항목  
 [SXI&#40;선택적 XML 인덱스&#41;](../../relational-databases/xml/selective-xml-indexes-sxi.md)  
  
  
