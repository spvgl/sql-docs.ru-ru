---
title: Компоненты сервера ядра OLAP | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, architecture
- ports [Analysis Services]
- XML/A listener
- server architecture [Analysis Services]
ms.assetid: 5193c976-9dcd-459c-abba-8c3c44e7a7f2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0537be8bda9c367fc381140183b10ddf383cf16a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68889527"
---
# <a name="olap-engine-server-components"></a>Серверные компоненты ядра OLAP
  Серверный компонент компонента [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] — это приложение **msmdsrv. exe** , которое выполняется как служба Windows. Оно состоит из компонентов безопасности, компонента прослушивания XML для аналитики (XMLA), компонента обработчика запросов и множества других внутренних компонентов, выполняющих следующие функции:  
  
-   Синтаксический анализ инструкций, получаемых от клиентов  
  
-   Управление метаданными  
  
-   Обработка транзакций  
  
-   Обработка вычислений  
  
-   Сохранение измерения и данных ячеек  
  
-   Создание агрегатов  
  
-   Планирование запросов  
  
-   Кэширование объектов  
  
-   Управление ресурсами сервера  
  
## <a name="architectural-diagram"></a>Архитектурная диаграмма  
 Экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] запускается как изолированная служба, взаимодействие с этой службой происходит через XMLA с использованием протокола HTTP или TCP. Объекты AMO — это прослойка между приложением пользователя и экземпляром служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Они предоставляют доступ к административным объектам служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]. Объект AMO — это библиотека классов, которая принимает команды от клиентского приложения и преобразует их в XMLA-сообщения для экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] . Объекты AMO представляют объекты экземпляра служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] , как классы для приложения конечного пользователя, с элементами-методами, запускающими команды и элементами-свойствами, хранящими данные объектов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] .  
  
 Следующий рисунок отображает архитектуру компонентов служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], включая все главные элементы, запущенные на экземпляре служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], и все пользовательские компоненты, взаимодействующие с этим экземпляром. Рисунок также отображает, что единственным путем доступа к экземпляру является прослушиватель XML для аналитики или использование протокола HTTP или TCP.  
  
 ![Диаграмма архитектуры системы служб Analysis Services](https://docs.microsoft.com/analysis-services/analysis-services/dev-guide/media/analysisservicessystemarchitecture.gif "Диаграмма архитектуры системы служб Analysis Services")  
  
## <a name="xmla-listener"></a>Прослушиватель XML для аналитики  
 Компонент прослушивателя XML для аналитики обрабатывает все XMLA-взаимодействия между службами [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] и их клиентами. [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] `Port` Параметр конфигурации в файле msmdsrv. ini можно использовать для указания порта, который прослушивает [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] экземпляр. Значение 0 указывает на то, что [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] прослушивает порт по умолчанию. По умолчанию службы [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] пользуются следующими TCP-портами:  
  
|Порт|Description|  
|----------|-----------------|  
|2383|Экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]по умолчанию.|  
|2382|Перенаправитель для других экземпляров [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
|Динамически назначается при запуске сервера|Именованный экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].|  
  
 Дополнительные сведения см. в разделе [Настройка брандмауэра Windows для разрешения Analysis Servicesного доступа](../../instances/configure-the-windows-firewall-to-allow-analysis-services-access.md) .  
  
## <a name="see-also"></a>См. также:  
 [Правила именования объектов &#40;Analysis Services&#41;](object-naming-rules-analysis-services.md)   
 [Физическая архитектура &#40;Analysis Services многомерных данных&#41;](understanding-microsoft-olap-physical-architecture.md)   
 [Логическая архитектура &#40;Analysis Services многомерных данных&#41;](../olap-logical/understanding-microsoft-olap-logical-architecture.md)  
  
  
