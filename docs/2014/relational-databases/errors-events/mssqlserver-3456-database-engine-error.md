---
title: MSSQLSERVER_3456 | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3456 (Database Engine error)
ms.assetid: d11b2b2c-3ae4-4023-b82f-05b561bfacce
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b2077d736f15787fe35a4a18d5c03dbd9ddd36a4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62914302"
---
# <a name="mssqlserver_3456"></a>MSSQLSERVER_3456
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3456|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_REDOLSNMISMATCH|  
|Текст сообщения|Не удалось повторить запись журнала %S_LSN для идентификатора транзакции %S_XID на странице %S_PGID базы данных "%.*ls" (идентификатор базы данных %d). Page: LSN = %S_LSN, type = %ld. Log: OpCode = %ld, context %ld, PrevPageLSN: %S_LSN. Восстановите базу данных из резервной копии или исправьте ее.|  
  
## <a name="explanation"></a>Объяснение  
 Операции восстановления не удалось выполнить повтор журнала транзакций. В результате этой ошибки состояние базы данных изменилось на SUSPECT. Первичная файловая группа и, возможно, другие файловые группы могут быть повреждены. Эта база данных не может быть восстановлена во время загрузки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и поэтому недоступна. Для разрешения этой проблемы требуется вмешательство пользователя.  
  
 Следует отметить, что если эта ошибка возникает для базы данных **tempdb**, экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] завершает работу.  
  
## <a name="user-action"></a>Действие пользователя  
 Эта ошибка может вызываться временным состоянием, существовавшим в системе во время данной попытки запуска экземпляра сервера или восстановления базы данных. Эта ошибка может быть также вызвана неустранимым сбоем, который возникает при каждой попытке запуска базы данных. Для выяснения причины проверьте журнал событий Windows, в котором должна содержаться предшествующая ошибка, которая указывает на конкретный сбой.  
  
 Чтобы получить сведения о причине возникновения ошибки 3456, изучите в журнале событий Windows предшествующее сообщение об ошибке, в котором указан конкретный сбой. Соответствующее действие пользователя зависит от того, что указывают сведения в журнале событий Windows: ошибка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] была вызвана временным состоянием или неустранимым сбоем. Сведения о действиях пользователя по устранению ошибки 3456 приведены в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL ALTER DATABASE &#40;](/sql/t-sql/statements/alter-database-transact-sql)   
 [DBCC CHECKDB &#40;&#41;Transact-SQL](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)   
 [Полное восстановление базы данных &#40;простой модели восстановления&#41;](../backup-restore/complete-database-restores-simple-recovery-model.md)   
 [MSSQLSERVER_824](mssqlserver-824-database-engine-error.md)   
 [sys.databases (Transact-SQL)](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql)  
  
  
