---
title: 프로젝트 설정 (동기화) (MySQLToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 42061ff7-e6e7-497b-a0d9-440b9cf5986c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: e82fa9d02fdbfe876f4097c54c6877c3a3a81fee
ms.sourcegitcommit: 5d6e1c827752c3aa2d02c4c7653aefb2736fffc3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2018
ms.locfileid: "49072087"
---
# <a name="project-settings-synchronization-mysqltosql"></a>프로젝트 설정(동기화)(MySQLToSQL)
동기화 **프로젝트 설정** SQL Server 데이터베이스 개체를 사용 하 여 MySQL 데이터베이스 개체는 동기화 하는 방법을 구성할 수 있습니다.  
  
MySQL 데이터베이스에서 개체를 새로 고치기 위한 및 SQL Server 데이터베이스를 사용 하 여 개체를 동기화 하는 것에 대 한 기본 설정을 지정 하는 기본 동작입니다. 자세한 내용은 [데이터베이스에서 새로 고침 &#40;MySQLToSQL&#41;](../../ssma/mysql/refresh-from-database-mysqltosql.md)  
  
동일한 설정을 포함 하는 두 개의 다른 동기화 페이지에 액세스할 수 있습니다.  
  
-   에 모든 향후 SSMA 프로젝트에 대 한 설정을 지정 하려면 합니다 **도구** 메뉴에서 클릭 **DefaultProject 설정**를 클릭 하 고 **동기화** 왼쪽 창의 맨 아래에서.  
  
-   현재 프로젝트에 대 한 설정을 지정 하는 **도구** 메뉴에서 클릭 **프로젝트 설정**, 클릭 하 고 **동기화** 왼쪽 창의 맨 아래에서.  
  
## <a name="options"></a>변수  
  
##### <a name="misc"></a>기타  
  
##### <a name="attempts"></a>시도  
SQL Server로 로드 하기 위해 수행할 개체 전달 횟수에 대 한 정보를 제공 합니다. SQL Server 개체를 로드 한 패스가 여러 개 일반적으로 수행 됩니다. 첫 번째 단계에서는 외래 키 등을 로드 하지 못한 개체에서 다음 단계를 성공적으로 로드할 수 있습니다.  
  
기본적으로 값은 2입니다.  
  
## <a name="synchronization-for-mysql"></a>MySQL에 대 한 동기화  
  
##### <a name="action-on-local-and-remote-object-change"></a>로컬 및 원격 개체 변경 시 동작  
SSMA에 데이터베이스 서버 개체 정의가 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   데이터베이스에서 새로 고침을 선택 하면 SSMA는 조건이 충족 되 면 메타 데이터에 데이터베이스 정의 로드 됩니다.  
  
-   Skip을 선택 하면 SSMA 새로 고침 작업을 수행 하지 않습니다.  
  
##### <a name="action-on-local-object-change"></a>로컬 개체 변경 시 동작  
SSMA에서 개체 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
##### <a name="action-on-remote-object-change"></a>원격 개체 변경 시 동작  
데이터베이스 서버에는 개체가 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>로컬 개체 메타 데이터가 누락 된 경우 작업  
로컬 메타 데이터를 사용할 수 없는 경우 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다  
  
## <a name="synchronization-for-sql-server"></a>SQL Server에 대 한 동기화  
  
##### <a name="action-on-local-and-remote-object-change"></a>로컬 및 원격 개체 변경 시 동작  
SSMA에 데이터베이스 서버 개체 정의가 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **데이터베이스에 쓸**, 조건이 충족 될 때 SSMA SSMA 메타 데이터 내용에 따라 데이터베이스의 개체를 업데이트 합니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
##### <a name="action-on-local-object-change"></a>로컬 개체 변경 시 동작  
SSMA에서 개체 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **데이터베이스에 쓸**, 조건이 충족 될 때 SSMA SSMA 메타 데이터 내용에 따라 데이터베이스에 개체를 업데이트 합니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
##### <a name="action-on-remote-object-change"></a>원격 개체 변경 시 동작  
데이터베이스 서버에는 개체가 변경 될 때 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, 조건이 충족 되 면 SSMA 메타 데이터를 데이터베이스 정의 로드 됩니다.  
  
-   선택 하는 경우 **데이터베이스에 쓸**, 조건이 충족 될 때 SSMA SSMA 메타 데이터 내용에 따라 데이터베이스에 개체를 업데이트 합니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
##### <a name="action-when-local-object-metadata-is-missing"></a>로컬 개체 메타 데이터가 누락 된 경우 작업  
로컬 메타 데이터를 사용할 수 없는 경우 동기화 대화 상자에서 기본값을 지정 합니다.  
  
-   선택 하는 경우 **데이터베이스에서 새로 고침**, SSMA는 조건이 충족 되 면 데이터베이스 옵션에서 새로 고침을 선택 합니다.  
  
-   선택 하는 경우 **데이터베이스에 쓸**, 조건이 충족 되 면 SSMA 데이터베이스에서 개체가 삭제 됩니다.  
  
-   선택 하는 경우 **Skip**, SSMA 새로 고침 작업을 수행 하지 것입니다.  
  
