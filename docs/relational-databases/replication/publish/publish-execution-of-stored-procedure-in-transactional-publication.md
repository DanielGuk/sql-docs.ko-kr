---
title: 트랜잭션 게시에서 저장 프로시저 실행 게시 | Microsoft 문서
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publishing [SQL Server replication], stored procedure execution
- stored procedures [SQL Server replication], publishing
ms.assetid: 1d3a3525-0bc5-466f-b097-5359dc74432d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 47cfb440c83f8d82ca92a7fbbcbee43ac8da53e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47610641"
---
# <a name="publish-execution-of-stored-procedure-in-transactional-publication"></a>트랜잭션 게시에서 저장 프로시저 실행 게시
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  **아티클 속성 - \<Article>** 대화 상자에서 해당 정의만이 아닌 저장 프로시저 실행을 게시하도록 지정합니다. 이 대화 상자는 새 게시 마법사 및 **게시 속성 - \<게시>** 대화 상자에서 사용할 수 있습니다. 마법사 사용 및 대화 상자 액세스에 대한 자세한 내용은 [게시 만들기](../../../relational-databases/replication/publish/create-a-publication.md) 및 [게시 속성 보기 및 수정](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)을 참조하세요.  
  
 프로시저 정의(CREATE PROCEDURE 문)는 구독이 초기화될 때 구독자로 복제되고 게시자에서 프로시저가 실행되면 복제가 구독자에서 해당하는 프로시저를 실행합니다.  
  
### <a name="to-publish-the-execution-of-a-stored-procedure"></a>저장 프로시저의 실행을 게시하려면  
  
1.  새 게시 마법사의 **아티클** 페이지 또는 **게시 속성 - \<게시>** 대화 상자에서 저장 프로시저를 선택합니다.  
  
2.  **아티클 속성**을 클릭한 다음 **선택한 저장 프로시저 아티클 속성 설정**을 클릭합니다.  
  
3.  **아티클 속성 - \<Article>** 대화 상자의 **복제** 옵션에 다음 값 중 하나를 지정합니다.  
  
    -   **저장 프로시저 실행**  
  
    -   **SP의 직렬화된 트랜잭션에서 실행**  
  
         이 옵션은 프로시저가 직렬화할 수 있는 트랜잭션의 컨텍스트 내에서 실행될 때만 프로시저 실행을 복제하기 때문에 권장됩니다. 저장 프로시저가 직렬화할 수 있는 트랜잭션 외부에서 실행되면 게시된 테이블의 데이터 변경 내용이 일련의 DML(데이터 조작 언어) 문으로 복제됩니다.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  **게시 속성 - \<게시>** 대화 상자에 있는 경우 **확인**을 클릭하여 대화 상자를 저장하고 닫습니다.  
  
## <a name="see-also"></a>참고 항목  
 [Publishing Stored Procedure Execution in Transactional Replication](../../../relational-databases/replication/transactional/publishing-stored-procedure-execution-in-transactional-replication.md)  
  
  
