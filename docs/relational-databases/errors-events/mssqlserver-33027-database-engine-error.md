---
title: MSSQLSERVER_33027 | Microsoft 문서
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 33027 (Database Engine error)
ms.assetid: bfdc626e-7958-4511-987d-3b687824e8af
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 880abcd92943e9a9083f69d7c41b6b33147c9ed1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47597521"
---
# <a name="mssqlserver33027"></a>MSSQLSERVER_33027
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>세부 정보  
  
|||  
|-|-|  
|제품 이름|SQL Server|  
|이벤트 ID|33027|  
|이벤트 원본|MSSQLSERVER|  
|구성 요소|SQLEngine|  
|심볼 이름|SEC_CRYPTOPROV_CANTLOADDLL|  
|메시지 텍스트|잘못된 Authenticode 서명 또는 잘못된 파일 경로로 인해 암호화 공급자 '%.*ls'을(를) 로드하지 못했습니다. 다른 오류가 있는지 이전 메시지를 확인하십시오.|  
  
## <a name="explanation"></a>설명  
SQL Server에서 DLL을 로드할 수 없어 SQL Server에서 위의 오류 메시지에 나열된 암호화 공급자를 사용할 수 없습니다. 이름이 잘못되었거나 Authenticode 서명이 잘못되었습니다.  
  
## <a name="user-action"></a>사용자 동작  
파일이 있고 SQL Server에 해당 위치에 액세스할 수 있는 권한이 있는지 확인합니다. 오류 로그에서 관련된 다른 메시지를 확인하거나 암호화 공급자에게 자세한 정보를 문의합니다.  
  
