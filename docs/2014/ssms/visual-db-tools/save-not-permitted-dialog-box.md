---
title: Диалоговое окно "Сохранение (запрещено)" | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.table.tablerecreatenosave.f1
ms.assetid: 7efda8e3-739f-4c97-a497-b8808a0acbea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 5540fd90b71bd75336cf9fc094926c1f643d56e9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62472878"
---
# <a name="save-not-permitted-dialog-box"></a>Диалоговое окно «Сохранение (запрещено)»
  Диалоговое окно **Сохранение (запрещено)** выдает предупреждение о том, что сохранение невозможно, поскольку выполненные изменения требуют удаления и повторного создания перечисленных таблиц.  
  
 Повторное создание таблицы может понадобиться для следующих действий:  
  
-   добавление нового столбца в середину таблицы;  
  
-   удаление столбца;  
  
-   изменение допустимости значения NULL для столбца;  
  
-   изменение порядка столбцов;  
  
-   изменение типа данных столбца.  
  
 Чтобы изменить этот параметр, в меню **Сервис** выберите пункт **Параметры**, разверните **Конструкторы**и щелкните **Конструкторы таблиц и баз данных**. Установите или снимите флажок **Запретить сохранение изменений, требующих повторного создания таблицы** .  
  
  
