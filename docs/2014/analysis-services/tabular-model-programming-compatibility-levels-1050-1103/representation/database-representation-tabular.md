---
title: Representation(Tabular) 데이터베이스 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: 16a233fb-f83b-4ca1-acb5-6186eca0a62c
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 02fd33d8adf1ccee042f09c8b102401d5ba94435
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48116285"
---
# <a name="database-representationtabular"></a>데이터베이스 표현(테이블 형식)
  테이블 형식 모드에서 데이터베이스는 테이블 형식 모델의 모든 개체에 대한 컨테이너입니다.  
  
## <a name="database-representation"></a>데이터베이스 표현  
 데이터베이스는 테이블 형식 모델을 형성하는 모든 개체가 있는 위치입니다. 개발자는 데이터베이스에 포함된 연결, 테이블, 역할 등의 개체를 찾습니다.  
  
### <a name="database-in-amo"></a>AMO의 데이터베이스  
 AMO를 사용하여 테이블 형식 모델 데이터베이스를 관리하는 경우 AMO의 <xref:Microsoft.AnalysisServices.Database> 개체는 테이블 형식 모델의 데이터베이스 논리 개체에 일 대 일로 일치합니다.  
  
> [!NOTE]  
>  AMO에서 사용자가 데이터베이스 개체에 액세스하려면 서버 개체에 대한 액세스 권한을 가지고 해당 개체에 연결해야 합니다.  
  
### <a name="database-in-adomdnet"></a>ADOMD.Net의 데이터베이스  
 ADOMD를 사용하여 테이블 형식 모델 데이터베이스를 확인하고 쿼리하는 경우 특정 데이터베이스에 대한 연결은 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 개체를 통해 얻습니다.  
  
 다음 코드 조각을 사용하여 특정 데이터베이스에 직접 연결할 수 있습니다.  
  
```csharp  
using ADOMD = Microsoft.AnalysisServices.AdomdClient;  
…  
   ADOMD.AdomdConnection currrentCnx = new ADOMD.AdomdConnection("Data Source=<<server\instance>>;Catalog=<<database>>");  
   currrentCnx.Open();  
…  
  
```  
  
 또한 닫히지 않은 기존 연결 개체에 대해 다음 코드에서와 같이 현재 데이터베이스를 다른 데이터베이스로 변경할 수 있습니다.  
  
```csharp  
currentCnx.ChangeDatabase("myOtherDatabase");  
  
```  
  
## <a name="database-in-amo"></a>AMO의 데이터베이스  
 AMO를 사용하여 데이터베이스 개체를 관리할 때는 먼저 <xref:Microsoft.AnalysisServices.Server> 개체로 시작하여 데이터베이스 컬렉션에서 데이터베이스를 검색하거나 새 데이터베이스를 컬렉션에 추가하여 데이터베이스를 만듭니다.  
  
 다음 코드 조각에서는 서버에 연결하기 위한 단계를 보여 주고 존재하지 않는 데이터베이스를 확인한 후 빈 데이터베이스를 만드는 방법을 보여 줍니다.  
  
```  
  
AMO.Server CurrentServer = new AMO.Server();  
try  
{  
    CurrentServer.Connect(currentServerName);  
}  
catch (Exception cnxException)  
{  
    MessageBox.Show(string.Format("Error while trying to connect to server: [{0}]\nError message: {1}", currentServerName, cnxException.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    return;  
}  
newDatabaseName = DatabaseName.Text;  
if (CurrentServer.Databases.Contains(newDatabaseName))  
{  
    return;  
}  
try  
{  
    AMO.Database newDatabase = CurrentServer.Databases.Add(newDatabaseName);  
  
    CurrentServer.Update();  
}  
catch (Exception createDBxc)  
{  
    MessageBox.Show(String.Format("Database [{0}] couldn't be created.\n{1}", newDatabaseName, createDBxc.Message), "AMO to Tabular message", MessageBoxButtons.OK, MessageBoxIcon.Error);  
    newDatabaseAvailable = false;  
}  
  
```  
  
 AMO를 사용 하 여 데이터베이스 표현을 만들고 조작 하는 방법에 대 한 실용적인 이해, Tabular AMO 2012 예제의 원본 코드를 참조 하세요. 특히 다음 원본 파일을 체크: Database.cs 합니다. 예제 코드는 여기에서 설명한 논리적 개념에 대한 지원으로만 제공되며 프로덕션 환경에서 사용해서는 안 됩니다.  
  
  
