---
title: "sys.dm_exec_cached_plans (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 09/18/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_exec_cached_plans
- dm_exec_cached_plans
- dm_exec_cached_plans_TSQL
- sys.dm_exec_cached_plans_TSQL
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_cached_plans dynamic management view
ms.assetid: 95b707d3-3a93-407f-8e88-4515d4f2039d
caps.latest.revision: "44"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 816fcb7a7fbf362f2f531b93629508ab3ab2b76f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexeccachedplans-transact-sql"></a>sys.dm_exec_cached_plans (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает строку для каждого плана запроса, кэшируемого [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для более быстрого выполнения запросов. Можно использовать динамическое административное представление для поиска кэшированных планов запросов, кэшированного текста запросов, объема памяти, занимаемого кэшированными планами и счетчика повторного использования кэшированных планов.  
  
 Динамические административные представления в среде [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] не могут предоставлять информацию, которая может повлиять на автономность базы данных, или информацию о других базах данных, к которым имеет доступ пользователь. Чтобы избежать предоставления этих сведений, все строки, содержащие данные, не принадлежащие к подключенному клиенту, фильтруются. Кроме того, значения в столбцах **memory_object_address** и **pool_id** фильтруются; значение столбца равно NULL.  
  
> [!NOTE]  
>  Вызов его из [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] или [!INCLUDE[ssPDW](../../includes/sspdw-md.md)], используйте имя **sys.dm_pdw_nodes_exec_cached_plans**.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|bucketid|**int**|Идентификатор сегмента хэша, в который кэшируется запись. Значение указывает диапазон от 0 до значения размера хэш-таблицы для типа кэша.<br /><br /> Для кэшей SQL Plans и Object Plans размер хэш-таблицы может достигать 10007 на 32-разрядных версиях систем и 40009 — на 64-разрядных. Для кэша Bound Trees размер хэш-таблицы может достигать 1009 на 32-разрядных версиях систем и 4001 на 64-разрядных. Для кэша расширенных хранимых процедур размер хэш-таблицы может достигать 127 на 32-разрядных и 64-разрядных версиях систем.|  
|refcounts|**int**|Число объектов кэша, ссылающихся на данный объект кэша. **Refcounts** должен быть по крайней мере 1 запись в кэш.|  
|usecounts|**int**|Количество повторений поиска объекта кэша. Остается без увеличения, если параметризованные запросы обнаруживают план в кэше. Может быть увеличен несколько раз при использовании инструкции showplan.|  
|size_in_bytes|**int**|Число байтов, занимаемых объектом кэша.|  
|memory_object_address|**varbinary(8)**|Адрес памяти кэшированной записи. Это значение можно использовать с [sys.dm_os_memory_objects](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md) чтобы проанализировать распределение памяти кэшированного плана и с [sys.dm_os_memory_cache_entries](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)для определения затрат на кэширование записи.|  
|cacheobjtype|**nvarchar(34)**|Тип объекта в кэше. Значение может быть одним из следующих:<br /><br /> Compiled Plan (скомпилированный план)<br /><br /> Compiled Plan Stub (заглушка скомпилированного плана)<br /><br /> Parse Tree (дерево синтаксического анализа)<br /><br /> Extended Proc (расширенные процедуры)<br /><br /> CLR Compiled Func (скомпилированная функция CLR)<br /><br /> CLR Compiled Proc (скомпилированная процедура CLR)|  
|objtype|**nvarchar(16) в формате**|Тип объекта. Ниже приведены возможные значения и их соответствующие описания.<br /><br /> Proc: Хранимая процедура<br />Подготавливается: Подготовленная инструкция<br />Adhoc: нерегламентированного запроса. Ссылается на [!INCLUDE[tsql](../../includes/tsql-md.md)] отправляемым как языковые события с помощью **osql** или **sqlcmd** вместо виде удаленных вызовов процедур.<br />ReplProc: Фильтр процедура репликации<br />Триггер: триггер<br />Представления: представление<br />По умолчанию: по умолчанию<br />UsrTab: Пользовательская таблица<br />SysTab: Системная таблица<br />Проверка: ПРОВЕРОЧНОЕ ограничение<br />Правило: правило|  
|plan_handle|**varbinary(64)**|Идентификатор плана в оперативной памяти. Этот идентификатор является временным и константным, только пока план сохраняется в кэше. Это значение можно использовать со следующими функциями динамического управления:<br /><br /> [sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)<br /><br /> [sys.dm_exec_query_plan](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)<br /><br /> [sys.dm_exec_plan_attributes](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)|  
|pool_id|**int**|Идентификатор пула ресурсов, для которого подсчитывается использование памяти для плана.|  
|pdw_node_id|**int**|**Применяется к**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)],[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> Идентификатор для узла, это распределение.|  
  
 <sup>1</sup>  
  
## <a name="permissions"></a>Permissions  
 На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо разрешение VIEW SERVER STATE на сервере.  
  
 На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-returning-the-batch-text-of-cached-entries-that-are-reused"></a>A. Возвращение текста пакета повторно используемых кэшированных записей  
 Следующий пример возвращает SQL-текст всех кэшированных записей, использованных более одного раза.  
  
```  
SELECT usecounts, cacheobjtype, objtype, text   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_sql_text(plan_handle)   
WHERE usecounts > 1   
ORDER BY usecounts DESC;  
GO  
```  
  
### <a name="b-returning-query-plans-for-all-cached-triggers"></a>Б. Возвращение планов запросов для всех кэшированных триггеров  
 Следующий пример возвращает планы запросов для кэшированных триггеров.  
  
```  
SELECT plan_handle, query_plan, objtype   
FROM sys.dm_exec_cached_plans   
CROSS APPLY sys.dm_exec_query_plan(plan_handle)   
WHERE objtype ='Trigger';  
GO  
```  
  
### <a name="c-returning-the-set-options-with-which-the-plan-was-compiled"></a>В. Возвращение параметров SET, с которыми был скомпилирован план  
 Следующий пример возвращает параметры SET, с использованием которых был скомпилирован план. `sql_handle` Для плана также возвращается. Оператор PIVOT используется для вывода `set_options` и `sql_handle` атрибуты столбцов, а не строк. Дополнительные сведения о значении, возвращаемом в `set_options`, в разделе [sys.dm_exec_plan_attributes &#40; Transact-SQL &#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md).  
  
```  
SELECT plan_handle, pvt.set_options, pvt.sql_handle  
FROM (  
      SELECT plan_handle, epa.attribute, epa.value   
      FROM sys.dm_exec_cached_plans   
      OUTER APPLY sys.dm_exec_plan_attributes(plan_handle) AS epa  
      WHERE cacheobjtype = 'Compiled Plan'  
      ) AS ecpa   
PIVOT (MAX(ecpa.value) FOR ecpa.attribute IN ("set_options", "sql_handle")) AS pvt;  
GO  
```  
  
### <a name="d-returning-the-memory-breakdown-of-all-cached-compiled-plans"></a>Г. Возвращение распределения памяти всех кэшированных скомпилированных планов  
 Следующий пример возвращает распределение памяти, используемой всеми скомпилированными планами в кэше.  
  
```  
SELECT plan_handle, ecp.memory_object_address AS CompiledPlan_MemoryObject,   
    omo.memory_object_address, pages_allocated_count, type, page_size_in_bytes   
FROM sys.dm_exec_cached_plans AS ecp   
JOIN sys.dm_os_memory_objects AS omo   
    ON ecp.memory_object_address = omo.memory_object_address   
    OR ecp.memory_object_address = omo.parent_address  
WHERE cacheobjtype = 'Compiled Plan';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [&#40; динамические административные представления и функции, связанные с выполнением Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys.dm_exec_query_plan &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-plan-transact-sql.md)   
 [sys.dm_exec_plan_attributes &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-plan-attributes-transact-sql.md)   
 [sys.dm_exec_sql_text &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)   
 [sys.dm_os_memory_objects &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)   
 [sys.dm_os_memory_cache_entries &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-entries-transact-sql.md)   
 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)  
  
  

