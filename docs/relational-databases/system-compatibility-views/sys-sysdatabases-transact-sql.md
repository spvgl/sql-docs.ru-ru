---
title: sys. sysdatabases (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysdatabases_TSQL
- sys.sysdatabases_TSQL
- sys.sysdatabases
- sysdatabases
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysdatabases compatibility view
- sysdatabases system table
ms.assetid: 60a93880-62f1-4eda-a886-f046706ba90c
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2b0dab1ca5f21ced6a54192a4b0173ead68fd6f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68089169"
---
# <a name="syssysdatabases-transact-sql"></a>sys.sysdatabases (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждой базы данных в экземпляре [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. При [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] первой установке **sysdatabases** содержит записи для баз данных **master**, **model**, **msdb**и **tempdb** .  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**name**|**имеет sysname**|Имя базы данных|  
|**DBID**|**smallint**|Идентификатор базы данных|  
|**sid**|**varbinary (85)**|Системный идентификатор создателя базы данных.|  
|**режима**|**smallint**|Для внутреннего применения: блокирует базу данных во время ее создания.|  
|**состояние**|**int**|Биты состояния, некоторые из которых можно задать с помощью [инструкции ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql.md) , как указано ниже.<br /><br /> 1 = **Автозакрытие** (ALTER DATABASE)<br /><br /> 4 = **Выбор в/bulkcopy** (ALTER DATABASE с помощью Set Recovery)<br /><br /> 8 = **TRUNC. log на chkpt** (ALTER DATABASE с помощью Set Recovery)<br /><br /> 16 = **обнаружение разорванных страниц** (ALTER DATABASE)<br /><br /> 32 = **Загрузка**<br /><br /> 64 = **предварительное восстановление**<br /><br /> 128 = **Восстановление**<br /><br /> 256 = **восстановление не** выполнено<br /><br /> 512 = **вне сети** (ALTER DATABASE)<br /><br /> 1024 = **только для чтения** (ALTER DATABASE)<br /><br /> 2048 = **только для использования dbo** (ALTER DATABASE с помощью Set RESTRICTED_USER)<br /><br /> 4096 = **один пользователь** (ALTER DATABASE)<br /><br /> 32768 = **аварийный режим**<br /><br /> 65536 = **контрольная сумма** (ALTER DATABASE)<br /><br /> 4194304 = **автосжатие** (ALTER DATABASE)<br /><br /> 1073741824 = **аккуратное завершение работы**<br /><br /> В одно и то же время несколько битов могут находиться в состоянии ON.|  
|**status2**|**int**|16384 = **ANSI NULL по умолчанию** (ALTER DATABASE)<br /><br /> 65536 = **сцепление значений NULL дает NULL** (ALTER DATABASE)<br /><br /> 131072 = **Рекурсивные триггеры** (ALTER DATABASE)<br /><br /> 1048576 = **по умолчанию локальный курсор** (ALTER DATABASE)<br /><br /> 8388608 = **заключенный в кавычки идентификатор** (ALTER DATABASE)<br /><br /> 33554432 = **курсор закрывается при фиксации** (ALTER DATABASE)<br /><br /> 67108864 = **значения NULL ANSI** (ALTER DATABASE)<br /><br /> 268435456 = **предупреждения ANSI** (ALTER DATABASE)<br /><br /> 536870912 = **полнотекстовый режим включен** (устанавливается с помощью **sp_fulltext_database**)|  
|**crdate**|**datetime**|Дата создания.|  
|**процессу**|**datetime**|Зарезервирован для использования в будущем.|  
|**категори**|**int**|Содержит битовую карту данных, применяемых при репликации:<br /><br /> 1 = опубликовано для репликации моментальных снимков или транзакций;<br /><br /> 2 = есть подписка на публикацию моментальных снимков или на публикации транзакций;<br /><br /> 4 = опубликовано для репликации слиянием;<br /><br /> 8 = есть подписка на публикацию слиянием;<br /><br /> 16 = база данных распространителя.|  
|**cmptlevel**|**tinyint**|Уровень совместимости для базы данных. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md).|  
|**файлов**|**nvarchar(260)**|Имя основного файла базы данных и путь к нему в операционной системе.<br /><br /> **имя файла** отображается для **dbcreator**, **sysadmin**, владельца базы данных с разрешениями на создание любых баз данных или участников, имеющих одно из следующих разрешений: ALTER любая база данных, создание любой базы данных, просмотр любого определения. Чтобы получить путь и имя файла, запросите представление совместимости [sys. sysfiles](../../relational-databases/system-compatibility-views/sys-sysfiles-transact-sql.md) или представление [sys. database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) .|  
|**Версия**|**smallint**|Внутренний номер версии того кода [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с которым была создана база данных. [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>См. также:  
 [&#41;Transact-SQL ALTER DATABASE &#40;](../../t-sql/statements/alter-database-transact-sql.md)   
 [Сопоставление системных таблиц с системными представлениями &#40;&#41;Transact-SQL](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [Представления совместимости &#40;Transact-SQL&#41;](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
