---
title: Сохранение пакета программным образом | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- programmatically saving a package
- saving a package programmatically
ms.assetid: 4204f817-d5df-475a-9338-d7f01305d566
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a65b7559770b6de0d1ebd928815458c02acfd41
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "71299044"
---
# <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  После программного построения нового или изменения существующего пакета обычно необходимо сохранить изменения.  
  
 Все методы, используемые в данном разделе для сохранения пакетов, требуют наличия ссылки на сборку **Microsoft.SqlServer.ManagedDTS** . После добавления ссылки в новый проект импортируйте пространство имен <xref:Microsoft.SqlServer.Dts.Runtime> с помощью инструкции **using** или **Imports**.  
  
## <a name="saving-a-package-programmatically"></a>Сохранение пакета программным образом  
 Для программного сохранения пакета вызовите один из следующих методов класса [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <xref:Microsoft.SqlServer.Dts.Runtime.Application>.  
  
|Место хранения|Вызываемый метод|  
|----------------------|--------------------|  
|Файл|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToXml%2A>|  
|Хранилище пакетов служб SSIS|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServer%2A><br /><br /> или диспетчер конфигурации служб<br /><br /> <xref:Microsoft.SqlServer.Dts.Runtime.Application.SaveToSqlServerAs%2A>|  
  
> [!IMPORTANT]  
>  Методы класса <xref:Microsoft.SqlServer.Dts.Runtime.Application> для работы с хранилищем пакетов служб SSIS поддерживают только «.» и имя сервера для локального сервера. Использование имен «(local)» и «localhost» невозможно.  
  
## <a name="see-also"></a>См. также:  
 [Сохранение пакетов](../../integration-services/save-packages.md)  
  
  
