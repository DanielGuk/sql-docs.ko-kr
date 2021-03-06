---
title: 생성, 변경 및 뷰를 제거 합니다. | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- views [SMO]
ms.assetid: 7d445c0e-77ef-4734-993b-e022de31df23
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 5e6069f4b80942ef6c7ebc4fa2be3326cf31e224
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47705671"
---
# <a name="creating-altering-and-removing-views"></a>뷰 생성, 변경 및 제거
[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]
  SMO([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects)에서 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 뷰는 <xref:Microsoft.SqlServer.Management.Smo.View> 개체로 표시됩니다.  
  
 <xref:Microsoft.SqlServer.Management.Smo.View.TextBody%2A> 개체의 <xref:Microsoft.SqlServer.Management.Smo.View> 속성이 뷰를 정의합니다. 에 해당 하는 것을 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 뷰 만들기에 대 한 SELECT 문의 합니다.  
  
## <a name="example"></a>예제  
 제공된 코드 예제를 사용하려면 애플리케이션을 만들 프로그래밍 환경, 프로그래밍 템플릿 및 프로그래밍 언어를 선택해야 합니다. 자세한 내용은 [Visual C 만들기&#35; Visual Studio.NET에서 SMO 프로젝트](../../../relational-databases/server-management-objects-smo/how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)합니다.  
  
## <a name="creating-altering-and-removing-a-view-in-visual-basic"></a>Visual Basic에서 뷰 생성, 변경 및 제거  
 이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다. 텍스트 모드를 사용 하 여 뷰가 만들어집니다 하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정 해야 합니다.  
  
```VBNET
'Connect to the local, default instance of SQL Server.
Dim srv As Server
srv = New Server
'Reference the AdventureWorks2012 2008R2 database.
Dim db As Database
db = srv.Databases("AdventureWorks2012")
'Define a View object variable by supplying the parent database, view name and schema in the constructor.
Dim myview As View
myview = New View(db, "Test_View", "Sales")
'Set the TextHeader and TextBody property to define the view.
myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"
myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"
'Create the view on the instance of SQL Server.
myview.Create()
'Remove the view.
myview.Drop()
```
  
## <a name="creating-altering-and-removing-a-view-in-visual-c"></a>Visual C#에서 뷰 생성, 변경 및 제거  
 이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다. 텍스트 모드를 사용 하 여 뷰가 만들어집니다 하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정 해야 합니다.  
  
```csharp  
{  
        //Connect to the local, default instance of SQL Server.   
        Server srv;   
        srv = new Server();   
        //Reference the AdventureWorks2012 database.   
        Database db;   
        db = srv.Databases["AdventureWorks2012"];   
        //Define a View object variable by supplying the parent database, view name and schema in the constructor.   
        View myview;   
        myview = new View(db, "Test_View", "Sales");   
        //Set the TextHeader and TextBody property to define the view.   
        myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS";   
        myview.TextBody = "SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID";   
        //Create the view on the instance of SQL Server.   
        myview.Create();   
        //Remove the view.   
        myview.Drop();   
        }  
```  
  
## <a name="creating-altering-and-removing-a-view-in-powershell"></a>PowerShell에서 뷰 생성, 변경 및 제거  
 이 코드 예제는 내부 조인을 사용하여 두 테이블을 조인한 뷰를 만드는 방법을 보여 줍니다. 텍스트 모드를 사용 하 여 뷰가 만들어집니다 하므로 <xref:Microsoft.SqlServer.Management.Smo.View.TextHeader%2A> 속성을 설정 해야 합니다.  
  
```powershell   
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item Adventureworks2012  
  
# Define a View object variable by supplying the parent database, view name and schema in the constructor.   
$myview  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.View `  
-argumentlist $db, "Test_View", "Sales"  
  
# Set the TextHeader and TextBody property to define the view.   
$myview.TextHeader = "CREATE VIEW [Sales].[Test_View] AS"  
$myview.TextBody ="SELECT h.SalesOrderID, d.OrderQty FROM Sales.SalesOrderHeader AS h INNER JOIN Sales.SalesOrderDetail AS d ON h.SalesOrderID = d.SalesOrderID"  
  
# Create the view on the instance of SQL Server.   
$myview.Create()  
  
# Remove the view.   
$myview.Drop();  
```  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.SqlServer.Management.Smo.View>  
  
  
