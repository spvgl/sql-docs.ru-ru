---
title: MSSQLSERVER_8651 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8651 (Database Engine error)
ms.assetid: 4cc3498d-5449-4c4e-b1f9-3271831c725a
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 429956528484a11b26caf6c39a666ef933515314
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62762374"
---
# <a name="mssqlserver_8651"></a>MSSQLSERVER_8651
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|8651|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MEMGRANT_ERR|  
|Текст сообщения|Не удалось выполнить запрошенную операцию, потому что недоступна минимально необходимая память для запроса. Уменьшите значение параметра конфигурации сервера «min memory per query».|  
  
## <a name="explanation"></a>Объяснение  
 Память сервера потребляют другие процессы (усиливая нагрузку на память на сервере).  
  
## <a name="user-action"></a>Действие пользователя  
 Уменьшите значение параметра конфигурации сервера «min memory per query» или снизьте интенсивность запросов на сервере.  
  
 Далее представлены общие шаги, которые помогут при устранении неполадок с памятью.  
  
1.  Проверьте, не используют ли память данного сервера другие приложения или службы. Измените настройки таким образом, чтобы менее важные приложения или службы использовали меньший объем памяти.  
  
2.  Начните сбор счетчиков системного монитора для **SQL Server: диспетчер буферов**, **SQL Server: диспетчер памяти**.  
  
3.  Проверьте следующие параметры конфигурации памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
    -   **max server memory**  
  
    -   **min server memory**  
  
    -   **min memory per query**  
  
     Обратите внимание на нестандартные параметры. При необходимости измените их. Параметры по умолчанию приведены в разделе «Настройка параметров конфигурации сервера» электронной документации по SQL Server.  
  
4.  Проверьте рабочую нагрузку (например, число параллельных сеансов, в текущий момент выполняющих запросы).  
  
 Следующие действия могут позволить использовать больший объем памяти в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Если какие-либо отличные от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] приложения используют необходимые ресурсы, попытайтесь прекратить выполнение этих приложений или перенесите их выполнение на отдельный сервер. Это снизит внешнюю нагрузку на память.  
  
-   Если установлен параметр **max server memory**, увеличьте его значение.  
  
 Выполните следующие команды DBCC для освобождения нескольких кэшей памяти [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   DBCC FREESYSTEMCACHE  
  
-   DBCC FREESESSIONCACHE  
  
-   DBCC FREEPROCCACHE  
  
 Если проблема не исчезла, необходимо продолжить ее исследование и, возможно, снизить рабочую нагрузку.  
  
## <a name="see-also"></a>См. также:  
 [DBCC FREESYSTEMCACHE &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-freesystemcache-transact-sql)   
 [DBCC FREESESSIONCACHE &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-freesessioncache-transact-sql)   
 [DBCC FREEPROCCACHE &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-freeproccache-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [SQL Server, объект диспетчера буферов](../performance-monitor/sql-server-buffer-manager-object.md)   
 [SQL Server, объект Memory Manager](../performance-monitor/sql-server-memory-manager-object.md)  
  
  
