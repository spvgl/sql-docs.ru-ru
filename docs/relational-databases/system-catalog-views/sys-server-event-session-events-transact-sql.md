---
title: sys. server_event_session_events (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_event_session_events
- server_event_session_events_TSQL
- sys.server_event_session_events
- sys.server_event_session_events_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_event_session_events catalog view
- xe
ms.assetid: 75986e91-1fc7-4f14-98ac-4e90154a74db
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9ac3c2bd13b5f89ea8d87336e579e196e3754c5c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68133229"
---
# <a name="sysserver_event_session_events-transact-sql"></a>sys.server_event_session_events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает строку для каждого события в сеансе событий.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|Идентификатор сеанса событий. Не допускает значение NULL.|  
|event_id|**int**|Идентификатор события. Этот идентификатор уникален внутри объекта сеанса событий. Не допускает значение NULL.|  
|name|**имеет sysname**|Имя события. Не допускает значение NULL.|  
|Пакет|**имеет sysname**|Имя пакета событий, который содержит событие. Не допускает значение NULL.|  
|module|**имеет sysname**|Имя модуля, который содержит событие. Не допускает значение NULL.|  
|predicate|**nvarchar (3000)**|Выражение предиката, применяемое к событию. Допускает значение NULL.|  
|predicate_xml|**nvarchar (3000)**|Выражение предиката XML, применяемое к событию. Допускает значение NULL.|  
  
## <a name="permissions"></a>Разрешения  
 необходимо разрешение VIEW SERVER STATE на сервере.  
  
## <a name="remarks"></a>Remarks  
 Это представление имеет следующее количество элементов связей.  
  
||||  
|-|-|-|  
|С|Кому|Связь|  
|sys.server_event_session_events.event_session_id|sys. server_event_sessions. event_session_id|Многие к одному|  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога расширенных событий (Transact-SQL)](../../relational-databases/system-catalog-views/extended-events-catalog-views-transact-sql.md)   
 [Расширенные события](../../relational-databases/extended-events/extended-events.md)  
  
  
