---
title: sp_help_log_shipping_monitor_secondary (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_log_shipping_monitor_secondary
- sp_help_log_shipping_monitor_secondary_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_log_shipping_monitor_secondary
ms.assetid: 3ac091ea-c9a8-4c05-a0b6-1ccf4e001339
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b1acf456bda88eeee0493d3f9d7ccc063a5bda50
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001008"
---
# <a name="sp_help_log_shipping_monitor_secondary-transact-sql"></a>sp_help_log_shipping_monitor_secondary (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает из таблиц мониторинга информацию о базе данных-получателе.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_help_log_shipping_monitor_secondary  
[ @secondary_server = ] 'secondary_server',  
[ @secondary_database = ] 'secondary_database'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @secondary_server = ] 'secondary_server'`Имя сервера-получателя. Аргумент *secondary_server* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @secondary_database = ] 'secondary_database'`Имя базы данных-получателя. Аргумент *secondary_database* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Столбец|Description|  
|------------|-----------------|  
|**secondary_server**|Имя дополнительного экземпляра [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журналов.|  
|**secondary_database**|Имя базы данных-получателя в конфигурации доставки журналов.|  
|**secondary_id**|Идентификатор сервера-получателя в конфигурации доставки журналов.|  
|**primary_server**|Имя первичного экземпляра компонента [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] в конфигурации доставки журнала.|  
|**primary_database**|Имя базы данных-источника в конфигурации доставки журналов.|  
|**restore_threshold**|Время (в минутах), которое может пройти между операциями восстановления, прежде чем сформируется предупреждение.|  
|**threshold_alert**|Предупреждение, создаваемое при истечении порогового срока восстановления.|  
|**threshold_alert_enabled**|Этот аргумент определяет, активированы ли предупреждения об истечении порогового срока восстановления.<br /><br /> 1 = включено.<br /><br /> 0 = отключено.|  
|**last_copied_file**|Имя последнего файла резервной копии, скопированного на сервер-получатель.|  
|**last_copied_date**|Дата и время последней операции копирования на сервер-получатель.|  
|**last_copied_date_utc**|Дата и время последней операции копирования на сервер-получатель по времени в формате UTC.|  
|**last_restored_file**|Имя файла последней резервной копии, восстановленной в базу данных-получатель.|  
|**last_restored_date**|Дата и время последней операции восстановления в базе данных-получателе.|  
|**last_restored_date_utc**|Дата и время последней операции восстановления в базу данных-получатель по времени в формате UTC.|  
|**history_retention_period**|Время (в минутах) хранения истории доставки журналов для конкретной базы данных-получателя; по истечении этого времени записи удаляются.|  
  
## <a name="remarks"></a>Remarks  
 **sp_help_log_shipping_monitor_secondary** должны быть запущены из базы данных **master** на сервере мониторинга.  
  
## <a name="permissions"></a>Разрешения  
 Эту процедуру могут выполнять только члены предопределенной роли сервера **sysadmin** .  
  
## <a name="see-also"></a>См. также раздел  
 [SQL Server &#40;доставки журналов&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
