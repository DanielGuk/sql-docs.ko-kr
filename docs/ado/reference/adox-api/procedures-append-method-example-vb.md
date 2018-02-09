---
title: "메서드 예제 (VB)를 추가 하는 프로시저 | Microsoft Docs"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: ado
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Append method [ADOX], Visual Basic example
ms.assetid: ce83b966-474b-4f57-8eb9-370996dfc5c0
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8982cc8970cfbb79912688b038f1745d9d4b5612
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/09/2018
---
# <a name="procedures-append-method-example-vb"></a>메서드 예제 (VB)를 추가 하는 절차
다음 코드에 사용 하는 방법을 보여 줍니다는 [명령](../../../ado/reference/ado-api/command-object-ado.md) 개체 및 [프로시저](../../../ado/reference/adox-api/procedures-collection-adox.md) 컬렉션 [Append](../../../ado/reference/adox-api/append-method-adox-procedures.md) 메서드를 기본 데이터 원본에 새 프로시저를 만듭니다.  
  
```  
' BeginCreateProcedureVB  
Sub Main()  
    On Error GoTo CreateProcedureError  
  
    Dim cnn As New ADODB.Connection  
    Dim cmd As New ADODB.Command  
    Dim prm As ADODB.Parameter  
    Dim cat As New ADOX.Catalog  
  
    ' Open the Connection  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Create the parameterized command (Microsoft Jet specific)  
    Set cmd.ActiveConnection = cnn  
    cmd.CommandText = "PARAMETERS [CustId] Text;" & _  
    "Select * From Customers Where CustomerId = [CustId]"  
  
    ' Open the Catalog  
    Set cat.ActiveConnection = cnn  
  
    ' Create the new Procedure  
    cat.Procedures.Append "CustomerById", cmd  
  
    'Clean  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CreateProcedureError:  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCreateProcedureVB  
```  
  
## <a name="see-also"></a>관련 항목:  
 [ActiveConnection 속성 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Append 메서드 (ADOX 프로시저)](../../../ado/reference/adox-api/append-method-adox-procedures.md)   
 [카탈로그 개체 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [프로시저 개체 (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Procedures 컬렉션(ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
