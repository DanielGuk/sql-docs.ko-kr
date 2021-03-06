---
title: 추가 및 CreateParameter 메서드 예제 (VB) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- CreateParameter method [ADO], Visual Basic example
- Append method [ADO], Visual Basic example
ms.assetid: 46908cbd-434f-43e7-a794-ed0be0e0c0a7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 58f8bb0cab715df78926b6a4a70027ff25bcba1b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47741921"
---
# <a name="append-and-createparameter-methods-example-vb"></a>Append 및 CreateParameter 메서드 예제(VB)
이 예제에서는 합니다 [Append](../../../ado/reference/ado-api/append-method-ado.md) 및 [CreateParameter](../../../ado/reference/ado-api/createparameter-method-ado.md) 입력된 매개 변수를 사용 하 여 저장된 프로시저를 실행 하는 방법입니다.  
  
```  
'BeginAppendVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset, command and connection variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdByRoyalty As ADODB.Command  
    Dim prmByRoyalty As ADODB.Parameter  
    Dim rstByRoyalty As ADODB.Recordset  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
    Dim strSQLByRoyalty As String  
     'record variables  
    Dim intRoyalty As Integer  
    Dim strAuthorID As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open command object with one parameter  
    Set cmdByRoyalty = New ADODB.Command  
    cmdByRoyalty.CommandText = "byroyalty"  
    cmdByRoyalty.CommandType = adCmdStoredProc  
  
    ' Get parameter value and append parameter  
    intRoyalty = Trim(InputBox("Enter royalty:"))  
    Set prmByRoyalty = cmdByRoyalty.CreateParameter("percentage", adInteger, adParamInput)  
    cmdByRoyalty.Parameters.Append prmByRoyalty  
    prmByRoyalty.Value = intRoyalty  
  
    ' Create recordset by executing the command  
    Set cmdByRoyalty.ActiveConnection = Cnxn  
    Set rstByRoyalty = cmdByRoyalty.Execute  
  
    ' Open the Authors Table to get author names for display  
    ' and set cursor client-side  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adUseClient, adLockOptimistic, adCmdTable  
  
    ' Print recordset adding author names from Authors table  
    Debug.Print "Authors with " & intRoyalty & " percent royalty"  
  
    Do Until rstByRoyalty.EOF  
        strAuthorID = rstByRoyalty!au_id  
        Debug.Print "   " & rstByRoyalty!au_id & ", ";  
        rstAuthors.Filter = "au_id = '" & strAuthorID & "'"  
        Debug.Print rstAuthors!au_fname & " " & rstAuthors!au_lname  
        rstByRoyalty.MoveNext  
    Loop  
  
    ' clean up  
    rstByRoyalty.Close  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstByRoyalty = Nothing  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstByRoyalty Is Nothing Then  
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close  
    End If  
    Set rstByRoyalty = Nothing  
  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndAppendVB  
```  
  
## <a name="see-also"></a>관련 항목  
 [Append 메서드 (ADO)](../../../ado/reference/ado-api/append-method-ado.md)   
 [CreateParameter 메서드 (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)   
 [Field 개체](../../../ado/reference/ado-api/field-object.md)   
 [필드 컬렉션 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [Parameter 개체](../../../ado/reference/ado-api/parameter-object.md)
