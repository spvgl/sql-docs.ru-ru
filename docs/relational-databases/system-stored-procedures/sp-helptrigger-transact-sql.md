---
title: sp_helptrigger (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1e6244443fc1f6ba7d83376226fedd56563e0d39
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68048220"
---
# <a name="sp_helptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Возвращает тип или типы триггеров DML, определенных в указанной таблице для текущей базы данных. sp_helptrigger нельзя использовать с триггерами DDL. Вместо этого запросите представление каталога [системных хранимых процедур](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @tabname = ] 'table'`Имя таблицы в текущей базе данных, для которой возвращаются сведения о триггере. *Table* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @triggertype = ] 'type'`Тип триггера DML, о котором возвращаются сведения. *Type имеет тип* **char (6)**, значение по умолчанию NULL и может принимать одно из следующих значений.  
  
|Значение|Description|  
|-----------|-----------------|  
|**DELETE**|Возвращает сведения о триггере DELETE.|  
|**INSERT**|Возвращает сведения о триггере INSERT.|  
|**UPDATE**|Возвращает сведения о триггере UPDATE.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
 Следующая таблица показывает данные в результирующем наборе.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**имеет sysname**|Имя триггера.|  
|**trigger_owner**|**имеет sysname**|Имя владельца таблицы, для которой определен триггер.|  
|**Обновление**|**int**|1=триггер UPDATE<br /><br /> 0=не триггер UPDATE|  
|**удалить**|**int**|1=триггер DELETE<br /><br /> 0=не триггер DELETE|  
|**isinsert**|**int**|1=триггер INSERT<br /><br /> 0=не триггер INSERT|  
|**isafter**|**int**|1=триггер AFTER<br /><br /> 0=не триггер AFTER|  
|**isinsteadof**|**int**|1=триггер INSTEAD OF<br /><br /> 0=не триггер INSTEAD OF|  
|**trigger_schema**|**имеет sysname**|Имя схемы, к которой принадлежит триггер.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение на [настройку видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md) для таблицы.  
  
## <a name="examples"></a>Примеры  
 В следующем примере выполняется хранимая процедура `sp_helptrigger` для получения сведений о триггерах для таблицы `Person.Person`.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER (Transact-SQL)](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)   
 [УДАЛИТЬ триггер &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
