---
title: Проверка подсистемы дискового ввода-вывода на наличие проблем задержки ввода-вывода
description: Узнайте, как включить политику для проверки подсистемы дискового ввода-вывода на наличие проблем с задержкой операций ввода-вывода путем проверки в журнале событий сообщения об ошибке 833 для управления на основе политик с SQL Server.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 23863340-d8e0-48d6-928b-462745885d37
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 0cf1dc8196ef8e248da485b01efc4bf192d4248c
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "75558179"
---
# <a name="check-disk-input-and-output-subsystem-for-io-delay-problems"></a>Проверка на наличие проблем задержки ввода-вывода в подсистеме дискового ввода-вывода
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Это правило проверяет журнал событий на наличие сообщения об ошибке 833. Это сообщение указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издал запрос чтения или записи на диск, и выполнение запроса заняло более 15 секунд. Эта ошибка выдается [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и указывает на проблему в подсистеме дискового ввода-вывода. Такие долгие задержки могут существенно снизить производительность среды [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="best-practices-recommendations"></a>Рекомендации  
 Для устранения этой ошибки найдите в журнале системных событий сообщения об ошибках, связанных с оборудованием. Также изучите журналы оборудования, если они доступны.  
  
 При помощи системного монитора проверьте следующие счетчики.  
  
-   Среднее время обращения к диску (сек)  
  
-   Средняя длина очереди диска  
  
-   Текущая длина очереди диска  
  
 Например, значение Average Disk Sec/Transfer на компьютере, где выполняется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , обычно не превышает 15 миллисекунд. Если значение счетчика Average Disk Sec/Transfer увеличивается, это указывает на то, что подсистема ввода-вывода диска не справляется с запросами на операции ввода-вывода.  
  
## <a name="for-more-information"></a>Дополнительные сведения см. в разделе  
   
  
 [Статья 897284 базы знаний Майкрософт](https://go.microsoft.com/fwlink/?linkid=117743)  
  
 [Основные операции ввода-вывода в SQL Server, раздел 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10))
