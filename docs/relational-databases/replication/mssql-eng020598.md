---
title: MSSQL_ENG020598 | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG020598 error
ms.assetid: 1c3032f2-23d1-4ead-94ee-16ac4d75cd0c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: c65e6d67890f1f2a3bab91a6d61abcddd0f51a0e
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76286851"
---
# <a name="mssql_eng020598"></a>MSSQL_ENG020598
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20598|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|При применении реплицированной команды строка на подписчике не была найдена.|  
  
## <a name="explanation"></a>Объяснение  
 Данная ошибка возникает в репликации транзакций, если строка, которую агент распространителя пытается обновить на подписчике, была удалена или ее первичный ключ был изменен. По умолчанию для подписчиков все подписки на публикацию транзакций доступны только для чтения, так как все изменения нельзя применить на издателе. В случае с репликацией транзакций пользователь должен вносить изменения на подписчике только при использовании обновляемых подписок или одноранговой репликации. Сведения об этих параметрах см. в разделе [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md) и [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md).  
  
## <a name="user-action"></a>Действие пользователя  
 **Чтобы разрешить эту проблему:**  
  
1.  Если в ходе репликации был обнаружен источник ошибки, но репликация при этом должна быть продолжена, укажите параметр **-SkipErrors 20598** для агента распространителя. Это позволит агенту пропустить изменения, приведшие к ошибке 20598, но разрешит при этом репликацию других изменений.  
  
2.  Определите на подписчике строки, которые были удалены или имеют первичный ключ, отличный от первичного ключа соответствующих строк на издателе. При помощи [tablediff Utility](../../tools/tablediff-utility.md) можно определить, какие строки в базах данных публикации и подписки отличаются. Сведения об использовании этой программы с реплицированными базами данных см. в статье [Сравнение реплицируемых таблиц на предмет различий (программирование репликации)](../../relational-databases/replication/administration/compare-replicated-tables-for-differences-replication-programming.md).  
  
3.  Используя программу **tablediff** или другой способ, внесите необходимые исправления в строки подписчика.  
  
4.  Удалите параметр **-SkipErrors** (необязательно).  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  
