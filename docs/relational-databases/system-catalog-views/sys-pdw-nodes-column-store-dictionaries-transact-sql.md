---
title: sys. pdw_nodes_column_store_dictionaries (Transact-SQL)
ms.date: 03/03/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.custom: seo-dt-2019
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 7ae1c2e4-45c0-4880-a692-1f299fbcfd19
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 4e4ecf91491a88e002c92a82d321e5712d48ef76
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "74399822"
---
# <a name="syspdw_nodes_column_store_dictionaries-transact-sql"></a>sys. pdw_nodes_column_store_dictionaries (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Содержит по одной строке для каждого словаря, используемого в индексах columnstore. Словари используются для кодирования некоторых, но не всех типов данных, поэтому не все столбцы в индексе columnstore имеют словари. Словарь может существовать в качестве основного словаря (для всех сегментов) и, возможно, для других вспомогательных словарей, используемых для подмножества сегментов столбца.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**bigint**|Указывает идентификатор секции. Уникален в базе данных.|  
|**hobt_id**|**bigint**|Идентификатор индекса куча или сбалансированное дерево (HoBT) для таблицы, которая имеет этот индекс columnstore.|  
|**column_id**|**int**|Идентификатор столбца columnstore.|  
|**dictionary_id**|**int**|Идентификатор словаря.|  
|**Версия**|**int**|Версия формата словаря.|  
|**type**|**int**|Тип словаря:<br /><br /> 1 — хэш-словарь, содержащий значения **int**<br /><br /> 2 — не используется<br /><br /> 3 — хэш-словарь, содержащий строковые значения<br /><br /> 4. хэш-словарь, содержащий значения **float**|  
|**last_id**|**int**|Последний идентификатор данных в словаре.|  
|**entry_count**|**bigint**|Количество записей в словаре.|  
|**on_disc_size**|**bigint**|Размер словаря в байтах.|  
|**pdw_node_id**|**int**|Уникальный идентификатор [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] узла.|  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение `VIEW SERVER STATE`.  
  
## <a name="see-also"></a>См. также:  
 [Хранилища данных SQL и представления каталога параллельных хранилищ данных](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)   
 [Создание индекса COLUMNSTORE &#40;&#41;Transact-SQL](../../t-sql/statements/create-columnstore-index-transact-sql.md)   
 [sys. pdw_nodes_column_store_segments &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-segments-transact-sql.md)   
 [sys. pdw_nodes_column_store_row_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-nodes-column-store-row-groups-transact-sql.md)  
  
  
