---
title: sys. database_filestream_options (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- database_filestream_options
- sys.database_filestream_options_TSQL
- database_filestream_options_TSQL
- sys.database_filestream_options
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_filestream_options catalog view
ms.assetid: 3383c607-0bbc-456a-ab37-7230f4cbf0e9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 95d9c980927d565b907d666af1317e883126087e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915028"
---
# <a name="sysdatabase_filestream_options-transact-sql"></a>sys.database_filestream_options (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает сведения об уровне нетранзакционного доступа к данным FILESTREAM в каждой из включенных таблиц FileTable. Содержит по одной строке для каждой базы данных в экземпляре SQL Server.  
  
 Дополнительные сведения о таблицах FileTable см. в разделе [Таблицы FileTable (SQL Server)](../../relational-databases/blob/filetables-sql-server.md).  
  
  
|Столбец|Тип|Description|  
|------------|----------|-----------------|  
|**database_id**|**int**|Идентификатор базы данных. Это значение уникально в рамках экземпляра [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**directory_name**|**nvarchar(255)**|Каталог на уровне базы данных для всех пространств имен FileTable:|  
|**non_transacted_access**|**tinyint**|Включенный уровень нетранзакционного доступа к данным FILESTREAM. Уровень доступа задается параметром NON_TRANSACTED_ACCESS инструкции **Create Database** или **ALTER DATABASE** .<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> 0 — не включено. Это значение по умолчанию. Этот уровень задается путем предоставления значения **Off** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 1 — доступ только для чтения. Этот уровень задается путем предоставления значения **READ_ONLY** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 3 — полный доступ. Этот уровень задается путем указания значения **Full** для параметра **NON_TRANSACTED_ACCESS** .<br /><br /> 5 — переход в состояние READONLY.<br /><br /> 6 — Переход в режим «Выкл.»|  
|**non_transacted_access_desc**|**nvarchar (60)**|Описание уровня нетранзакционного доступа, определенного в non_transacted_access.<br /><br /> Этот параметр имеет одно из следующих значений:<br /><br /> НЕТ — это значение по умолчанию.<br /><br /> READ_ONLY<br /><br /> FULL<br /><br /> IN_TRANSITION_TO_READ_ONLY<br /><br /> IN_TRANSITION_TO_OFF|  
  
## <a name="see-also"></a>См. также:  
 [Включение необходимых компонентов для таблицы FileTable](../../relational-databases/blob/enable-the-prerequisites-for-filetable.md)  
  
  
