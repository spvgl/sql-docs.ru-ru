---
title: dbo. сисалертс (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4645b586c07635a405b2e678b84c4846762f7582
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68084678"
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит одну строку для каждого предупреждения. Предупреждение — это сообщение, отправляемое как реакция на событие. Предупреждения могут направлять сообщения не только в среде [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Например, предупреждение может быть сообщением электронной почты или пейджера. Предупреждения также могут создавать задачи.  Эта таблица хранится в базе данных **msdb** .
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**удостоверения**|**int**|Идентификатор предупреждения.|  
|**name**|**имеет sysname**|Имя предупреждения.|  
|**event_source**|**nvarchar (100)**|Источник события: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|**event_category_id**|**int**|Зарезервирован для использования в будущем.|  
|**event_id**|**int**|Зарезервирован для использования в будущем.|  
|**message_id**|**int**|Определяемый пользователем идентификатор сообщения или ссылка на сообщение **sysmessages** , которое запускает это оповещение.|  
|**серьезности**|**int**|Серьезность события, вызвавшего это предупреждение.|  
|**доступной**|**tinyint**|Состояние предупреждения:<br /><br /> **0** = отключено.<br /><br /> **1** = включено.|  
|**delay_between_responses**|**int**|Время ожидания между отправкой уведомлений для этого предупреждения (в секундах).|  
|**last_occurrence_date**|**int**|Дата последнего возникновения предупреждения.|  
|**last_occurrence_time**|**int**|Время последнего возникновения предупреждения.|  
|**last_response_date**|**int**|Дата последней отправки предупреждения.|  
|**last_response_time**|**int**|Время последней отправки предупреждения.|  
|**notification_message**|**nvarchar(512)**|Дополнительные сведения, отправляемые вместе с предупреждением.|  
|**include_event_description**|**tinyint**|Битовая маска, показывающая, отправляется ли описание события по электронной почте, по пейджеру или с помощью команды net send. Значения см. на диаграмме ниже.|  
|**database_name**|**nvarchar(512)**|База данных, в которой должно произойти предупреждение, чтобы оно сработало.|  
|**event_description_keyword**|**nvarchar (100)**|Шаблон, с которым должна совпасть ошибка для срабатывания этого предупреждения.|  
|**occurrence_count**|**int**|Количество раз, когда возникало этого предупреждение.|  
|**count_reset_date**|**int**|Значение счетчика "день (дата)" будет сброшено в **0**.|  
|**count_reset_time**|**int**|Время суток будет сброшено до **0**.|  
|**job_id**|**UNIQUEIDENTIFIER**|Идентификатор задачи, выполняемой, когда происходит предупреждение.|  
|**has_notification**|**int**|Количество операторов, получающих при возникновении предупреждения уведомление по электронной почте.|  
|**Метки**|**int**|Зарезервировано.|  
|**performance_condition**|**nvarchar(512)**|Зарезервировано.|  
|**category_id**|**int**|Зарезервировано.|  
  
 ## <a name="remarks"></a>Remarks

В следующей таблице показаны значения битовой маски include_event_description. Значение десятичного числа возвращается dbo. сисалертс. 

|Decimal | binary | значение |
|------|------|------|
|0 |0000 |нет сообщения |
|1 |0001 |email |
|2 |0010 |pager |
|3 |0011 |пейджер и электронная почта |
|4 |0100 |Команда Net send |
|5 |0101 |NET SEND и email |
|6 |0110 |NET SEND и пейджер |
|7 |0111 |NET SEND, пейджер и электронная почта |
  
