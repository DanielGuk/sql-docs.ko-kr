---
title: sys.trace_columns (Transact SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.trace_columns
- trace_columns
- trace_columns_TSQL
- sys.trace_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.trace_columns catalog view
ms.assetid: 5c48eb09-9e9b-45dd-b151-ca39b026ece5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: beda27214f6ef805b84e9897e7f0dd48f424a79f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47835481"
---
# <a name="systracecolumns-transact-sql"></a>sys.trace_columns(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  합니다 **sys.trace_columns** 카탈로그 뷰는 모든 추적 이벤트 열 목록을 포함 합니다. 지정된 버전의 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]에서는 이러한 열이 변경되지 않습니다.  
  
 지원 되는 추적 이벤트의 전체 목록은 참조 하세요 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)합니다.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 대신 확장 이벤트 카탈로그 뷰를 사용하십시오.  
  
|열 이름|데이터 형식|Description|  
|-----------------|---------------|-----------------|  
|**trace_column_id**|**smallint**|이 열의 고유 ID입니다.|  
|**name**|**nvarchar(128)**|이 열의 고유 이름입니다. 이 매개 변수는 지역화되지 않았습니다.|  
|**type_name**|**nvarchar(128)**|이 열의 데이터 형식 이름입니다.|  
|**max_size**|**int**|이 열의 최대 데이터 크기(바이트)입니다.|  
|**is_filterable**|**bit**|필터 사양에서 열을 사용할 수 있는지 여부를 나타냅니다.<br /><br /> 0 = false<br /><br /> 1 = true|  
|**is_repeatable**|**bit**|"반복되는 열" 데이터에서 열을 참조할 수 있는지 여부를 나타냅니다.<br /><br /> 0 = false<br /><br /> 1 = true|  
|**is_repeated_base**|**bit**|참조하는 반복되는 데이터의 고유 키로 이 열이 사용되는지 여부를 나타냅니다.<br /><br /> 0 = false<br /><br /> 1 = true|  
  
## <a name="permissions"></a>사용 권한  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 자세한 내용은 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [개체 카탈로그 뷰 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.traces &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-traces-transact-sql.md)   
 [sys.trace_categories &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_events &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
