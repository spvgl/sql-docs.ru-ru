---
title: Проверка подписок | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 5b08849b3d0a16916f9e4af4910586cc9e29ea8d
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68769249"
---
# <a name="validate-subscriptions"></a>Проверка подписок
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Диалоговое окно **Проверить подписки** позволяет указать подписки на публикации транзакций, которые нужно проверить в следующий раз агентом распространителя при каждом запуске подписки. Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Параметры  
 **Проверить все подписки SQL Server**  
 Выберите, чтобы проверить все подписки SQL Server на данную публикацию.  
  
 **Проверить следующие подписки**  
 Выберите, если не нужно проверять все подписки. Выберите из списка подписки, которые нужно проверять.  
  
 **Параметры проверки**  
 Нажмите, чтобы получить доступ к диалоговому окну **Параметры проверки подписки** , которое позволит указать, следует ли использовать проверку по количеству строк или по двоичной контрольной сумме.  
  
## <a name="see-also"></a>См. также:  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  
