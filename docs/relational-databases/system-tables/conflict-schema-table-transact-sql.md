---
title: "conflict_&lt;схемы&gt;_&lt;таблицы&gt; (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 01/15/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- conflict_
- conflict_TSQL
dev_langs: TSQL
helpviewer_keywords: conflict_<schema>_<table>
ms.assetid: 15ddd536-db03-454e-b9b5-36efe1f756d7
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cfb2f078495256ee53d021bb09801323bdca094f
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="conflictltschemagtlttablegt-transact-sql"></a>conflict_&lt;схемы&gt;_&lt;таблицы&gt; (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Conflict_\<схема > _\<таблицы > Таблица содержит сведения о конфликтующих строках в-одноранговая репликация. Для каждой реплицируемой таблицы в публикации существует таблица конфликтов, при этом к имени таблицы конфликтов добавляются имя схемы и имя статьи. Такие таблицы конфликтов существуют во всех базах данных публикаций для каждой из статей.  
  
 При одноранговой репликации агент распространителя при обнаружении конфликта завершается ошибкой. Эта ошибка заносится в журнал, но данные конфликта не записываются в таблицу конфликтов и поэтому недоступны для просмотра. Если агенту распространителя разрешено продолжение работы, то конфликт заносится в локальный журнал на каждом из узлов, где он обнаружен. Дополнительные сведения см. в подразделе «Обработка конфликтов» раздела [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|__$originator_id|**int**|Идентификатор узла, из которого было произведено изменение, вызвавшее конфликт. Список идентификаторов, выполните [sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md).|  
|__$origin_datasource|**int**|Узел, на котором было произведено изменение, вызвавшее конфликт.|  
|__$tranid|**nvarchar (40)**|Регистрационный номер транзакции в журнале (LSN) изменения, вызвавшего конфликт, при его применении на __$origin_datasource.|  
|__$conflict_type|**int**|Тип конфликта, который может принимать одно из следующих значений:<br /><br /> 1: не удалось выполнить обновление, поскольку локального строка была изменена другим обновлением или она была удалена и затем повторно вставлено.<br /><br /> 2: не удалось выполнить обновление, поскольку Локальная строка уже удалена.<br /><br /> 3: удаление сбой, так как локальный строка была изменена другим обновлением или он был удален и затем вновь вставляется.<br /><br /> 4: не удалось выполнить удаление, поскольку Локальная строка уже удалена.<br /><br /> 5: вставка не удалась, поскольку Локальная строка уже была вставлена или вставлена, а затем обновляются.|  
|__$is_winner|**bit**|Указывает, была ли строка в этой таблице победителем конфликта, что означает, что она была применена к локальному узлу.|  
|__$pre_version|**varbinary (32)**|Версия базы данных, из которой было произведено изменение, вызвавшее конфликт.|  
|__$reason_code|**int**|Код разрешения конфликта. Может использоваться одно из следующих значений:<br /><br /> 0<br /><br /> 1<br /><br /> 2<br /><br /> <br /><br /> Дополнительные сведения см. в разделе **__ $reason_text**.|  
|__$reason_text|**nvarchar (720)**|Разрешение конфликта. Может использоваться одно из следующих значений:<br /><br /> 1 = Разрешен<br /><br /> 2 = Не разрешен<br /><br /> 0 = Неизвестно|  
|__$update_bitmap|**varbinary (**  *n*  **)**. Размер зависит от содержимого.|Битовая карта, указывающая столбцы, которые были обновлены в случае конфликта «обновление-обновление».|  
|__$inserted_date|**datetime**|Дата и время вставки конфликтующей строки в эту таблицу.|  
|__$row_id|**timestamp**|Версия строки, которая связана со строкой, вызвавшей конфликт.|  
|__$change_id|**двоичный файл (8)**|Для локальной строки это значение равно __$row_id входящей строки, вызвавшей конфликт с локальной строкой. Для входящей строки это значение равно NULL.|  
|\<имена столбцов базовой таблицы >|\<базовые типы столбцов таблицы >|Конфликтующая строка содержит один столбец для каждого из столбцов базовой таблицы.|  
  
## <a name="see-also"></a>См. также:  
 [Таблицы репликации &#40; Transact-SQL &#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [Представления репликации (Transact-SQL)](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  