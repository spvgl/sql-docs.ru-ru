---
title: SQLForeignKeys | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8481b0f19566ed0e55f31480f9ab8be0c9441c7d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63184475"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает каскадные обновления и удаления через механизм ограничения внешнего ключа. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение SQL_CASCADE для столбцов, имеющих признак UPDATE_RULE и DELETE_RULE, если параметр CASCADE задан в предложении ON UPDATE или ON DELETE ограничения FOREIGN KEY. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает значение SQL_NO_ACTION для столбцов, имеющих признак UPDATE_RULE и DELETE_RULE, если параметр NO ACTION задан в предложении ON UPDATE или ON DELETE ограничения FOREIGN KEY.  
  
 Если в любом параметре функции **SQLForeignKeys** имеются недопустимые значения, функция **SQLForeignKeys** возвращает значение SQL_SUCCESS. **SQLFetch** возвращает SQL_NO_DATA, если в этих параметрах используются недопустимые значения.  
  
 **SQLForeignKeys** может выполняться на статическом серверном курсоре. При попытке выполнить функцию **SQLForeignKeys** для обновляемого курсора (динамического или набора ключей) будет возвращено значение SQL_SUCCESS_WITH_INFO, которое указывает на то, что тип курсора был изменен.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает выдачу сведений о таблицах, находящихся на связанных серверах, принимая двухкомпонентное имя в параметрах *FKCatalogName* и *PKCatalogName* : *Имя_Связанного_Сервера.Имя_Каталога*.  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLForeignKeys](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  
