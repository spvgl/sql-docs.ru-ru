---
title: Запуск SQL Server с минимальной конфигурацией | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- minimal configuration [SQL Server]
- starting SQL Server, minimal configuration
ms.assetid: 4d733c99-28b3-42d8-b7f6-7b943b548173
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cf7065d064e322e45fb95a38aed514b2acfc714a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62756224"
---
# <a name="start-sql-server-with-minimal-configuration"></a>Запустите SQL Server с минимальной конфигурацией
  При возникновении проблем с конфигурацией, препятствующих запуску сервера, можно запустить экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с помощью параметра минимальной настройки запуска. Это параметр запуска **-f**. Запуск экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с минимальной конфигурацией автоматически переводит сервер в однопользовательский режим.  
  
 При запуске экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации обратите внимание на следующее:  
  
-   может подключиться только один пользователь, операция CHECKPOINT не выполняется;  
  
-   удаленный доступ и упреждающее чтение отключены;  
  
-   запуск хранимых процедур не осуществляется.  
  
 После запуска сервера с минимальной конфигурацией необходимо изменить значение или значения параметра соответствующего сервера, остановить сервер и заново запустить его.  
  
> [!IMPORTANT]  
>  Используйте программу **sqlcmd** и выделенное административное соединение (DAC) для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При использовании обычного соединения, перед тем как соединяться с экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в режиме минимальной конфигурации, необходимо остановить службу агента SQL Server. В противном случае служба агента SQL Server использует это соединение, тем самым блокируя его.  
  
## <a name="see-also"></a>См. также:  
 [Запуск, остановка или приостановка службы агент SQL Server](../../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)   
 [Диагностическое соединение для администраторов баз данных](diagnostic-connection-for-database-administrators.md)   
 [Программа sqlcmd](../../tools/sqlcmd-utility.md)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)   
 [Параметры запуска службы Database Engine](database-engine-service-startup-options.md)  
  
  
