---
title: "FILESTREAM 사용 데이터베이스 이동 | Microsoft 문서"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-blob
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], moving a FILESTREAM-enabled database
ms.assetid: dd4d270d-9283-431a-aa6b-e571fced1893
caps.latest.revision: 11
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 7af3800a6e604289944a340cee7f469654c495e2
ms.lasthandoff: 04/11/2017

---
# <a name="move-a-filestream-enabled-database"></a>FILESTREAM 사용 데이터베이스 이동
  이 항목에서는 FILESTREAM 사용 데이터베이스를 이동하는 방법을 보여 줍니다.  
  
> [!NOTE]  
>  이 항목의 예제에는 [FILESTREAM 사용 데이터베이스 만들기](../../relational-databases/blob/create-a-filestream-enabled-database.md)에서 만들어진 Archive 데이터베이스가 필요합니다.  
  
### <a name="to-move-a-filestream-enabled-database"></a>FILESTREAM 사용 데이터베이스를 이동하려면  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]에서 **새 쿼리** 를 클릭하여 쿼리 편집기를 엽니다.  
  
2.  다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다. 이 스크립트는 FILESTREAM 데이터베이스에서 사용하는 실제 데이터베이스 파일의 위치를 표시합니다.  
  
    ```tsql  
    USE Archive  
    GO  
    SELECT type_desc, name, physical_name from sys.database_files  
    ```  
  
3.  다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다. 이 코드는 `Archive` 데이터베이스를 오프라인 상태로 만듭니다.  
  
    ```tsql  
    USE master  
    EXEC sp_detach_db Archive  
    GO  
    ```  
  
4.  `C:\moved_location`이라는 폴더를 만든 다음 2단계에 나와 있는 파일과 폴더를 이 폴더로 이동합니다.  
  
5.  다음 [!INCLUDE[tsql](../../includes/tsql-md.md)] 스크립트를 쿼리 편집기에 복사한 다음 **실행**을 클릭합니다. 이 스크립트는 `Archive` 데이터베이스를 온라인 상태로 설정합니다.  
  
    ```tsql  
    CREATE DATABASE Archive ON  
    PRIMARY ( NAME = Arch1,  
        FILENAME = 'c:\moved_location\archdat1.mdf'),  
    FILEGROUP FileStreamGroup1 CONTAINS FILESTREAM( NAME = Arch3,  
        FILENAME = 'c:\moved_location\filestream1')  
    LOG ON  ( NAME = Archlog1,  
        FILENAME = 'c:\moved_location\archlog1.ldf')  
    FOR ATTACH  
    GO  
    ```  
  
## <a name="see-also"></a>참고 항목  
 [sp_detach_db&#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)  
  
  