---
title: MSSQLSERVER_9790 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 5747a13e60182596610f25dd4ed1243670ff5018
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62912178"
---
# <a name="mssqlserver_9790"></a>MSSQLSERVER_9790
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9790|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Текст сообщения|Не удалось найти маршрут для входящего сообщения. Системная база данных MSDB, содержащая сведения о маршрутах, находится в режиме SINGLE USER.|  
  
## <a name="explanation"></a>Объяснение  
 Произошла ошибка при попытке определения категории сообщения, полученного в автономном режиме, поскольку база данных MSDB находилась в однопользовательском режиме.  
  
## <a name="user-action"></a>Действие пользователя  
 С помощью команды ALTER DATABASE измените режим MSDB на MULTI USER.  
  
  
