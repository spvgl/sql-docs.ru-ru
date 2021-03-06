---
title: Команда UPDATE-SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- update [ODBC]
ms.assetid: ff1e0331-c060-4304-b280-039725b45f63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0230329d10d2414724379d4b9d38c4851a031bca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912335"
---
# <a name="update---sql-command"></a>UPDATE (команда SQL)
Обновляет записи в таблице новыми значениями.  
  
 Драйвер ODBC для Visual FoxPro поддерживает для этой команды собственный синтаксис языка Visual FoxPro. Сведения, относящиеся к драйверу, см. в разделе **Примечания к драйверам**.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
UPDATE [DatabaseName1!]TableName1  
SET Column_Name1 = eExpression1  
   [, Column_Name2 = eExpression2 ...]  
   WHERE FilterCondition1 [AND | OR FilterCondition2 ...]  
```  
  
## <a name="arguments"></a>Аргументы  
 Обновление [ *DatabaseName1!*] *TableName1*  
 Указывает таблицу, в которую обновляются записи с новыми значениями.  
  
 *DatabaseName1!* Указывает имя базы данных, отличной от базы данных, указанной в источнике данных, содержащем таблицу. Если база данных не является текущей, необходимо включить имя базы данных, содержащей таблицу. Включите разделитель восклицательного знака (!) после имени базы данных и перед именем таблицы.  
  
 Set *Column_Name1*= *eExpression1*[, *Column_Name2*= *eExpression2*  
 Указывает обновляемые столбцы и их новые значения. Если опустить предложение WHERE, то каждая строка в столбце будет обновлена с тем же значением.  
  
 ГДЕ *FilterCondition1*[и &#124; или *FilterCondition2*...]  
 Указывает записи, которые обновляются новыми значениями.  
  
 *Филтеркондитион* указывает критерии, которым должны соответствовать записи для обновления новыми значениями. Можно включить любое количество условий фильтра, подключив их к оператору AND или or. Можно также использовать оператор NOT для изменения значения логического выражения или можно использовать **Empty**() для проверки пустого поля.  
  
## <a name="remarks"></a>Remarks  
 UPDATE-SQL может обновлять только записи в одной таблице.  
  
 В отличие от Replace, UPDATE-SQL использует блокировку записей при обновлении нескольких записей в таблицах, открытых для общего доступа. Это уменьшает состязание за записи в многопользовательской ситуации, но может снизить производительность. Для достижения максимальной производительности откройте таблицу для монопольного использования или используйте **флокк**() для блокировки таблицы.  
  
## <a name="driver-remarks"></a>Примечания к драйверам  
 Когда приложение отправляет обновление инструкции SQL ODBC в источник данных, драйвер ODBC для Visual FoxPro преобразует команду в команду Visual Фокспраупдате без перевода.  
  
## <a name="see-also"></a>См. также:  
 [Команда DELETE-SQL](../../odbc/microsoft/delete-sql-command.md)   
 [INSERT (команда SQL)](../../odbc/microsoft/insert-sql-command.md)
