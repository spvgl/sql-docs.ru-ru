---
title: Кнопки навигации адресной книги | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS scenarios [ADO], navigation buttons
- address book application scenario [ADO], navigation buttons
ms.assetid: f0dd84c6-5c33-4ab9-82b4-4c42dfdd2277
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 158b9084ebe9aac28a2ec05c18938338c1bc90ae
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67922961"
---
# <a name="address-book-navigation-buttons"></a>Кнопки навигации адресной книги
В приложении адресной книги отображаются кнопки навигации в нижней части веб-страницы. С помощью кнопок навигации можно перемещаться по данным в сетке HTML путем выбора первой или последней строки данных или строк, примыкающих к текущему выделению.  
  
> [!IMPORTANT]
>  Начиная с Windows 8 и Windows Server 2012, компоненты RDS больше не включены в операционную систему Windows (Дополнительные сведения см. в статье о совместимости Windows 8 и [Windows server 2012 Cookbook](https://www.microsoft.com/download/details.aspx?id=27416) ). Клиентские компоненты RDS будут удалены в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Приложения, использующие RDS, должны переноситься в [службу данных WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="navigation-sub-procedures"></a>Процедуры навигации  
 Приложение адресной книги содержит несколько процедур, которые позволяют пользователям щелкать **первую**, **следующую**, **предыдущую**и **последнюю** кнопки для перемещения по данным.  
  
 Например, при нажатии **первой** кнопки активируется процедура VBScript First_OnClick. Процедура выполняет метод [MoveFirst](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) , который делает первую строку данных текущей выделенной областью. При нажатии **последней** кнопки активируется процедура Last_OnClick, которая вызывает метод [MoveLast](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md) , делая последнюю строку данных текущей выделенной областью. Остальные кнопки навигации работают аналогичным образом.  
  
```vb
' Move to the first record in the bound Recordset.  
Sub First_OnClick  
   DC1.Recordset.MoveFirst  
End Sub  
  
' Move to the next record from the current position   
' in the bound Recordset.  
Sub Next_OnClick  
   If Not DC1.Recordset.EOF Then    ' Cannot move beyond bottom record.  
      DC1.Recordset.MoveNext  
      Exit Sub  
   End If     
End Sub  
  
' Move to the previous record from the current position in the bound   
' Recordset.  
Sub Prev_OnClick  
   If Not DC1.Recordset.BOF Then    ' Cannot move beyond top record.  
      DC1.Recordset.MovePrevious  
      Exit Sub  
   End If  
End Sub  
  
' Move to the last record in the bound Recordset.  
Sub Last_OnClick  
   DC1.Recordset.MoveLast  
End Sub  
```  
  
## <a name="see-also"></a>См. также:  
 [Объект элемента управления (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Методы MoveFirst, MoveLast, MoveNext и MovePrevious (служба удаленных рабочих столов)](../../../ado/reference/rds-api/movefirst-movelast-movenext-and-moveprevious-methods-rds.md)



