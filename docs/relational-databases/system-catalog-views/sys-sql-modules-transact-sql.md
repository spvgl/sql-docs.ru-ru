---
title: sys. sql_modules (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 11/06/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sql_modules_TSQL
- sql_modules
- sql_modules_TSQL
- sys.sql_modules
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sql_modules catalog view
ms.assetid: 23d3ccd2-f356-4d89-a2cd-bee381243f99
author: stevestein
ms.author: sstein
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8f3e007a0676afd507af54e3b3406297cf40042e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108992"
---
# <a name="syssql_modules-transact-sql"></a>sys.sql_modules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает по строке для каждого объекта, который является определенным языком SQL в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], включая скалярно скомпилированную определяемую пользователем функцию. Объекты типа P, RF, V, TR, FN, IF, TF и R имеют сопоставленный с ними SQL модуль. Изолированные значения по умолчанию и объекты типа D в этом представлении также имеют определение SQL модуля. Описание этих типов см. в столбце **тип** в представлении каталога [sys. Objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md) .  
  
 Дополнительные сведения см. в разделе [Скалярные определяемые пользователем функции для выполняющейся в памяти OLTP](../../relational-databases/in-memory-oltp/scalar-user-defined-functions-for-in-memory-oltp.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|Идентификатор объекта, содержащего данный объект. Уникален в базе данных.|  
|**макроопределения**|**nvarchar(max)**|Текст на языке SQL, определяющий этот модуль. Это значение можно также получить с помощью встроенной функции [OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md) .<br /><br /> NULL = зашифрован.|  
|**uses_ansi_nulls**|**bit**|Модуль был создан с параметром SET ANSI_NULLS ON.<br /><br /> Всегда будет равен 0 (нулю) для правил и умолчаний.|  
|**uses_quoted_identifier**|**bit**|Модуль был создан с параметром SET QUOTED_IDENTIFIER ON.|  
|**is_schema_bound**|**bit**|Модуль был создан с параметром SCHEMABINDING.<br /><br /> Всегда содержит значение 1 для скомпилированных собственными средствами хранимых процедур.|  
|**uses_database_collation**|**bit**|1 = определение модуля, ограниченное схемой, зависит от принятых по умолчанию параметров сортировки базы данных для правильной оценки; в противном случае — 0. Такая зависимость предотвращает изменение параметров сортировки по умолчанию для базы данных.|  
|**is_recompiled**|**bit**|Процедура была создана с параметром WITH RECOMPILE.|  
|**null_on_null_input**|**bit**|Модуль был объявлен, чтобы обеспечить выходные значения NULL для любых входных значений NULL.|  
|**execute_as_principal_id**|**Int**|ID-идентификатор участника базы данных, указанного в инструкции EXECUTE AS.<br /><br /> По умолчанию и в случае EXECUTE AS CALLER имеет значение NULL.<br /><br /> ИДЕНТИФИКАТОР указанного участника, если он выполняется как SELF или выполняется как \<основной>.<br /><br /> -2 = EXECUTE AS OWNER.|  
|**uses_native_compilation**|**bit**|**Применимо к** [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] : [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]с до.<br /><br /> 0 = не скомпилированы в собственном коде<br /><br /> 1 = скомпилированы в собственном коде<br /><br /> По умолчанию используется значение 0.|  
|**is_inlineable**|**bit**|**Область применения**: [!INCLUDE[ssSQL15](../../includes/sssqlv15-md.md)] и более поздних версий.<br/><br />Указывает, является ли модуль встроенным. Встраивание зависит от условий, указанных [здесь](../user-defined-functions/scalar-udf-inlining.md#inlineable-scalar-udfs-requirements).<br /><br /> 0 = невстраиваемые<br /><br /> 1 = является встроенным. <br /><br /> Для скалярных пользовательских функций значение будет равно 1, если определяемая пользователем функция является встроенной, и 0 в противном случае. Он всегда содержит значение 1 для встроенного возвращающие табличное, а 0 — для всех других типов модулей.<br />|  
|**inline_type**|**bit**|**Область применения**: [!INCLUDE[ssSQL15](../../includes/sssqlv15-md.md)] и более поздних версий.<br /><br />Указывает, включено ли встраивание для модуля в настоящее время. <br /><br />0 = встраивание отключено<br /><br /> 1 = Встраивание включено.<br /><br /> Для скалярных пользовательских функций значение будет равно 1, если встраивание включено (явно или неявно). Значение всегда будет равно 1 для встроенных возвращающие табличное и 0 для других типов модулей.<br />|  

  
## <a name="remarks"></a>Remarks  
 Выражение SQL для ограничения по УМОЛЧАНИю, объект типа D, находится в представлении каталога [sys. default_constraints](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md) . Выражение SQL для ПРОВЕРОЧного ограничения, объект типа C, находится в представлении каталога [sys. CHECK_CONSTRAINTS](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md) .  
  
 Эти сведения также описаны в статье [sys. dm_db_uncontained_entities &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-db-uncontained-entities-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="examples"></a>Примеры  
 В ходе выполнения представленного ниже примера выполняется отображение имен, типов и определений всех модулей в текущей базе данных.  
  
```  
SELECT sm.object_id, OBJECT_NAME(sm.object_id) AS object_name, o.type, o.type_desc, sm.definition  
FROM sys.sql_modules AS sm  
JOIN sys.objects AS o ON sm.object_id = o.object_id  
ORDER BY o.type;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога объектов &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [Запросы к системному каталогу SQL Server вопросы и ответы](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
