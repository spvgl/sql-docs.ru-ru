---
title: sys. dm_db_rda_migration_status (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.dm_db_rda_migration_status
- sys.dm_db_rda_migration_status_TSQL
- dm_db_rda_migration_status
- dm_db_rda_migration_status_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_rda_migration_status dynamic management view
ms.assetid: faf3901c-a0e0-4e0c-8b1b-86d9f15f34dd
author: pmasl
ms.author: pelopes
ms.openlocfilehash: 21e5230e4f3efd86fe90382202f0b21a0187a214
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67937066"
---
# <a name="stretch-database---sysdm_db_rda_migration_status"></a>Stretch Database-sys. dm_db_rda_migration_status
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждого пакета перенесенных данных из каждой таблицы с поддержкой растяжения на локальном экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Пакеты идентифицируются по времени начала и времени окончания.  
  
 представление **sys. dm_db_rda_migration_status** ограничивается контекстом текущей базы данных. Убедитесь, что вы находитесь в контексте базы данных таблиц с растяжением, для которых требуется просмотреть состояние миграции.  
  
 В [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]выходные данные **sys. dm_db_rda_migration_status** ограничены 200 строками.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**table_id**|**int**|Идентификатор таблицы, из которой были перенесены строки.|  
|**database_id**|**int**|Идентификатор базы данных, из которой были перенесены строки.|  
|**migrated_rows**|**bigint**|Число строк, перенесенных в этом пакете.|  
|**start_time_utc**|**datetime**|Время в формате UTC, когда был запущен пакет.|  
|**end_time_utc**|**datetime**|Время (в формате UTC) завершения выполнения пакета.|  
|**error_number**|**int**|Если пакет не выполняется, номер ошибки, возникшей в результате ошибки; в противном случае значение null.|  
|**error_severity**|**int**|Если пакет не выполняется, серьезность возникшей ошибки; в противном случае значение null.|  
|**error_state**|**int**|Если пакет не выполняется, состояние возникшей ошибки; в противном случае значение null.<br /><br /> **ERROR_STATE** указывает условие или расположение, в котором произошла ошибка.|  
  
## <a name="see-also"></a>См. также:  
 [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
  
