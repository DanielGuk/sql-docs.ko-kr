---
title: 트랜잭션을 사용 하 여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- SQL Server Management Objects, transactions
- transactions [SMO]
- SMO [SQL Server], transactions
ms.assetid: 399aded8-bee3-4cfb-a671-1877c7d0de9f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d9f7984be9f48a3651d5dc804faabbc0cd9625f3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48086163"
---
# <a name="using-transactions"></a>트랜잭션 사용
  SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Object)에서 트랜잭션 처리는 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 사용하여 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 대한 연결을 통해 수행됩니다. <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 개체를 참조 합니다 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 의 속성은 <xref:Microsoft.SqlServer.Management.Smo.Server> 연결 되 면 개체입니다. <xref:Microsoft.SqlServer.Management.Common.DataTransferProgressEventType.StartTransaction>, <xref:Microsoft.SqlServer.Management.Common.ServerConnection.RollBackTransaction%2A> 및 <xref:Microsoft.SqlServer.Management.Common.ServerConnection.CommitTransaction%2A>과 같은 메서드는 <xref:Microsoft.SqlServer.Management.Smo.Server.ConnectionContext%2A> 개체 속성에 속합니다.  
  
## <a name="see-also"></a>관련 항목  
 [SMO 프로그램 만들기](creating-smo-programs.md)  
  
  
