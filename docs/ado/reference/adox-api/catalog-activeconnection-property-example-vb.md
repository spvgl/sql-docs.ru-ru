---
title: Пример свойства ActiveConnection каталога (Visual Basic) | Документация Майкрософт
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
- ActiveConnection property [ADOX], Visual Basic example
ms.assetid: bb3274b1-764d-43a7-a49f-ef55680ecd26
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4c6d30aeeb650525873669ccd175155c7e69cd0b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67967119"
---
# <a name="catalog-activeconnection-property-example-vb"></a>Пример свойства ActiveConnection объекта Catalog (Visual Basic)
Если задать для свойства [ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md) допустимое, открытое соединение, каталог будет открыт. Из открытого каталога можно получить доступ к объектам схемы, содержащимся в этом каталоге.  
  
```  
' BeginOpenConnectionVB  
Sub Main()  
    On Error GoTo OpenConnectionError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Debug.Print cat.Tables(0).Type  
  
    'Clean up  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
OpenConnectionError:  
  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndOpenConnectionVB  
```  
  
 При присвоении свойству **ActiveConnection** допустимой строки соединения также открывается каталог.  
  
```  
Attribute VB_Name = "Catalog"  
```  
  
## <a name="see-also"></a>См. также:  
 [Свойство ActiveConnection (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Объект каталога (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Объект Table (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [Коллекция Tables (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Свойство Type (Table) (ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
