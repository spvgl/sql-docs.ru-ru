---
title: Проблемы развития базы данных (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], multuser database changes
- database evolution [SQL Server]
ms.assetid: 1ed6ae10-d212-4ec2-8569-1b94ab1cba6d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d3a1f10ae77061983a5cf64ddd5a3462bb4be49b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63035593"
---
# <a name="issues-of-database-evolution-visual-database-tools"></a>Проблемы развития базы данных (визуальные инструменты для баз данных)
  При изменении структуры развернутой базы данных необходимо следить, чтобы изменения были совместимы с существующими данными и структурой базы данных. Возможно, необходимо будет принять особые меры при выполнении следующих изменений:  
  
-   **Добавление ограничения** При добавлении ограничения база данных уже может содержать данные, которые не соответствуют ей. При попытке сохранить ограничение [диалоговое окно "Уведомления после сохранения" (визуальные инструменты для баз данных)](visual-database-tools.md) сообщает, что не удалось создать ограничение в базе данных. Чтобы принудительно принять новое ограничение в базе данных, можно снять флажок **Проверять существующие данные при создании** .  
  
-   **Добавление связи** При добавлении связи база данных может уже содержать строки таблицы внешнего ключа, не имеющие соответствующих строк в таблице первичного ключа. То есть существующие данные могут не удовлетворять условию ссылочной целостности. При попытке сохранить новую связь [диалоговое окно "Уведомления после сохранения" (визуальные инструменты для баз данных)](visual-database-tools.md) сообщает, что серверу базы данных не удалось сохранить исправленную таблицу внешнего ключа. Чтобы принудительно принять изменение, можно снять флажок **Проверять существующие данные при создании** .  
  
-   **Изменение таблицы, участвующей в индексированном представлении** При изменении таблицы, которая участвует в Microsoft SQL Server индексированном представлении, индексы представления будут потеряны. Дополнительные сведения о повторном создании индексов см. в электронной документации SQL Server.  
  
-   **Удаление объекта** Если удалить объект, например столбец, таблицу или представление, сначала убедитесь, что на объект не ссылается другой объект в базе данных.  
  
 При любых изменениях структуры базы данных необходимо сохранять журнал изменений. Одним из подходов является сохранение скриптов всех изменений, когда-либо сделанных в производственной базе данных.  
  
## <a name="see-also"></a>См. также:  
 [Ограничения UNIQUE и проверочные ограничения](../../relational-databases/tables/unique-constraints-and-check-constraints.md)   
 [Многопользовательские среды (визуальные инструменты для баз данных)](multiuser-environments-visual-database-tools.md)  
  
  
