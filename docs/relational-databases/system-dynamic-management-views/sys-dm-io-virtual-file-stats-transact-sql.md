---
title: sys. dm_io_virtual_file_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/11/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_io_virtual_file_stats
- sys.dm_io_virtual_file_stats_TSQL
- sys.dm_io_virtual_file_stats
- dm_io_virtual_file_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_io_virtual_file_stats dynamic management function
ms.assetid: fa3e321f-6fe5-45ff-b397-02a0dd3d6b7d
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0ad2d38c031f97e46ef36f33f5e7a0fc82bcb5e0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74412840"
---
# <a name="sysdm_io_virtual_file_stats-transact-sql"></a>sys.dm_io_virtual_file_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Возвращает статистику ввода-вывода для данных и файлов журнала. Это динамическое административное представление заменяет функцию [fn_virtualfilestats](../../relational-databases/system-functions/sys-fn-virtualfilestats-transact-sql.md) .  
  
> [!NOTE]  
>  Чтобы вызвать эту функцию [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]из, используйте имя **sys. dm_pdw_nodes_io_virtual_file_stats**. 

## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database

sys.dm_io_virtual_file_stats (   
    { database_id | NULL },  
    { file_id | NULL }  
)  
```  

```  
-- Syntax for Azure SQL Data Warehouse

sys.dm_pdw_nodes_io_virtual_file_stats
```
  
## <a name="arguments"></a>Аргументы  


 *database_id* | ЗАКАНЧИВАЮЩ

 **применимо к:** SQL Server (начиная с 2008), база данных SQL Azure

 Идентификатор базы данных. *database_id* имеет тип int и не имеет значения по умолчанию. Допустимыми входными значениями являются идентификационный номер базы данных или NULL. Когда указывается значение NULL, возвращаются все базы данных экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Может быть указана встроенная функция [DB_ID](../../t-sql/functions/db-id-transact-sql.md).  
  
*file_id* | ЗАКАНЧИВАЮЩ

**применимо к:** SQL Server (начиная с 2008), база данных SQL Azure
 
Идентификатор файла. *file_id* имеет тип int и не имеет значения по умолчанию. Правильные значения — идентификационный номер файла или значение NULL. Когда указывается значение NULL, возвращаются все файлы базы данных.  
  
 Можно указать встроенную функцию [FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md) и ссылается на файл в текущей базе данных.  
  
## <a name="table-returned"></a>Возвращаемая таблица  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**database_name**|**имеет sysname**|имя базы данных.</br></br>Для хранилища данных SQL это имя базы данных, хранящейся на узле, который определяется pdw_node_id. Каждый узел имеет одну базу данных tempdb с 13 файлами. Каждый узел также имеет одну базу данных для каждого распределения, и каждая база данных распространителя имеет 5 файлов. Например, если каждый узел содержит 4 распределения, в результатах отобразится 20 файлов базы данных распространителя на pdw_node_id. 
|**database_id**|**smallint**|Идентификатор базы данных.|  
|**file_id**|**smallint**|Идентификатор файла.|  
|**sample_ms**|**bigint**|Число миллисекунд, прошедших со времени запуска компьютера. Этот столбец может быть использован для сравнения различных вариантов выполнения этой функции.</br></br>Тип данных — **int** для [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|**num_of_reads**|**bigint**|Количество считываний для этого файла.|  
|**num_of_bytes_read**|**bigint**|Общее число байтов, считанных из этого файла.|  
|**io_stall_read_ms**|**bigint**|Общее время задержек считывания файла, в миллисекундах.|  
|**num_of_writes**|**bigint**|Число записей, сделанных в этот файл.|  
|**num_of_bytes_written**|**bigint**|Общее число байтов, записанных в файл.|  
|**io_stall_write_ms**|**bigint**|Общее время задержек выполнения записи в файл, в миллисекундах.|  
|**io_stall**|**bigint**|Общее время задержек выполнения операций чтения-записи над файлом, в миллисекундах.|  
|**size_on_disk_bytes**|**bigint**|Число байтов, используемых файлом на диске. Для разреженных файлов это показывает реальное число байт, занимаемых на диске, которое используется для моментальных снимков базы данных.|  
|**file_handle**|**varbinary**|Дескриптор данного файла в Windows.|  
|**io_stall_queued_read_ms**|**bigint**|**Не применяется к:**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с до [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)].<br /><br /> Общая задержка ввода-вывода, созданная регулированием ресурсов ввода-вывода для чтения. Не допускает значение NULL. Дополнительные сведения см. в разделе [sys. dm_resource_governor_resource_pools &#40;&#41;Transact-SQL ](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md).|  
|**io_stall_queued_write_ms**|**bigint**|**Не применяется к:**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] с до [!INCLUDE[ssSQL12](../../includes/sssql11-md.md)].<br /><br />  Общая задержка ввода-вывода, созданная регулированием ресурсов ввода-вывода для записи. Не допускает значение NULL.|
|**pdw_node_id**|**int**|**Применимо к:**[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]</br></br>Идентификатор узла для распределения.
 
## <a name="remarks"></a>Remarks
При запуске службы SQL Server (MSSQLSERVER) счетчики инициализируются пустыми.
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение VIEW SERVER STATE. Дополнительные сведения см. в разделе [динамические административные представления и функции &#40;&#41;Transact-SQL ](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md).  
  
## <a name="examples"></a>Примеры  

### <a name="a-return-statistics-for-a-log-file"></a>A. Возврат статистики для файла журнала

**Применимо к:** SQL Server (начиная с 2008), база данных SQL Azure

 В следующем примере возвращается вся статистика для файла журнала в базе данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)].  
  
```sql  
SELECT * FROM sys.dm_io_virtual_file_stats(DB_ID(N'AdventureWorks2012'), 2);  
GO  
```  
  
### <a name="b-return-statistics-for-file-in-tempdb"></a>Б. Возврат статистики для файла в базе данных tempdb

**Применимо к:** Хранилище данных SQL Azure

```sql
SELECT * FROM sys.dm_pdw_nodes_io_virtual_file_stats 
WHERE database_name = 'tempdb' AND file_id = 2;

```

## <a name="see-also"></a>См. также:  
 [Динамические административные представления и функции (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [Динамические административные представления и функции, связанные с I O &#40;языке Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/i-o-related-dynamic-management-views-and-functions-transact-sql.md)   
 [sys. database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys. master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  

