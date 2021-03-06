---
title: '[^](와일드카드 - 일치하지 않는 문자)(Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 12/06/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- wildcard
- '[^]_TSQL'
- '[^]'
- Not Match
dev_langs:
- TSQL
helpviewer_keywords:
- wildcard characters [SQL Server]
- '[^] (wildcard - character(s) not to match)'
ms.assetid: b970038f-f4e7-4a5d-96f6-51e3248c6aef
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: edf8419cc41d58b4ca96891037f066ca48aced8b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47652646"
---
# <a name="-wildcard---characters-not-to-match-transact-sql"></a>\[^\](와일드카드 - 일치하지 않는 문자)(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  대괄호 사이에 지정된 범위 또는 집합에 없는 하나의 문자에 대응합니다.  
  
## <a name="examples"></a>예  
 다음 예에서는 [^] 연산자를 사용하여 `Contact`로 시작하고 세 번째 문자가 `Al`가 아닌 이름을 가진 사람을 `a` 테이블에서 모두 찾습니다.  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM Person.Person  
WHERE FirstName LIKE 'Al[^a]%'  
ORDER BY FirstName;  
```  
  
## <a name="see-also"></a>참고 항목  
 [LIKE &#40;Transact-SQL&#41;](../../t-sql/language-elements/like-transact-sql.md)   
 [PATINDEX&#40;Transact-SQL&#41;](../../t-sql/functions/patindex-transact-sql.md)   
 [%&#40;와일드카드 - 일치하는 문자&#41;&#40;Transact-SQL&#41;](../../t-sql/language-elements/percent-character-wildcard-character-s-to-match-transact-sql.md)   
  [&#91;&#93; &#40;와일드카드 - 일치하는 문자&#41;&#40;Transact-SQL&#41;](../../t-sql/language-elements/wildcard-character-s-to-match-transact-sql.md)   
 [\_&#40;와일드카드 - 문자 하나와 일치&#41;&#40;Transact-SQL&#41;](../../t-sql/language-elements/wildcard-match-one-character-transact-sql.md)  
  
  
