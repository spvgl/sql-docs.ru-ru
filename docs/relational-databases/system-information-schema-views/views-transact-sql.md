---
title: ПРЕДСТАВЛЕНИЯ (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- VIEWS_TSQL
- VIEWS
dev_langs:
- TSQL
helpviewer_keywords:
- VIEWS view
- INFORMATION_SCHEMA.VIEWS view
ms.assetid: 6119bc94-0b22-45d4-a34b-967afd810a9d
author: CarlRabeler
ms.author: carlrab
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b4e2a969450c2ec4593c7daec1b9c9b203b18410
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68078358"
---
# <a name="views-transact-sql"></a>VIEWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает одну строку для представлений, доступ к которым имеет текущий пользователь в текущей базе данных.  
  
 Чтобы получить сведения из этих представлений, укажите полное имя **INFORMATION_SCHEMA.** _view_name_.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CATALOG**|**nvarchar (** 128 **)**|Квалификатор представления.|  
|**TABLE_SCHEMA**|**nvarchar (** 128 **)**|Имя схемы, содержащей представление.<br /><br /> **&#42;&#42; важно &#42;&#42;** Не используйте INFORMATION_SCHEMA представления для определения схемы объекта. Единственный надежный способ найти схему объекта — направить запрос к представлению каталога sys.objects.|  
|**TABLE_NAME**|**nvarchar (** 128 **)**|Имя представления.|  
|**VIEW_DEFINITION**|**nvarchar (** 4000 **)**|Если длина определения больше **nvarchar (** 4000 **)**, этот столбец имеет значение null. В противном случае этот столбец является текстом определения представления.|  
|**CHECK_OPTION**|**varchar (** 7 **)**|Тип инструкции WITH CHECK OPTION. CASCADE, если первоначальное представление было создано с помощью инструкции WITH CHECK OPTION. Иначе возвращается значение NONE.|  
|**IS_UPDATABLE**|**varchar (** 2 **)**|Указывает, можно ли обновлять это представление. Всегда возвращает NO.|  
  
## <a name="see-also"></a>См. также:  
 [Системные представления &#40;&#41;Transact-SQL](https://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)   
 [Представления информационной схемы &#40;&#41;Transact-SQL](~/relational-databases/system-information-schema-views/system-information-schema-views-transact-sql.md)   
 [sys. sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys. views &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/sys-views-transact-sql.md)  
  
  
