---
title: Добавление обработчика событий в пакет | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 589d90b52647241b22929473efc9c6e54eb3b75f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062027"
---
# <a name="add-an-event-handler-to-a-package"></a>Добавление к пакету обработчик событий
  При выполнении контейнеров и задач происходят разные события. Возможно создание обработчиков пользовательских событий, которые отвечают на возникающие события запуском рабочего процесса. Например, можно создать обработчик событий, который по электронной почте посылает сообщение, если задача завершается неудачей.  
  
 Обработчик событий аналогичен пакету. Как и пакет, обработчик событий обеспечивает область действия для переменных и включает поток управления и потоки данных по выбору. Можно построить обработчик событий для пакетов, контейнера «цикл по каждому элементу», контейнера «цикл по элементам», контейнера последовательности и всех задач.  
  
 Создайте обработчик событий, используя область конструктора вкладки **Обработчики событий** в конструкторе служб [!INCLUDE[ssIS](../includes/ssis-md.md)] .  
  
 Если вкладка **Обработчики событий** активна, узлы **Элементы потока управления** и **Задачи плана обслуживания** в области элементов конструктора служб [!INCLUDE[ssIS](../includes/ssis-md.md)] содержат задачу и контейнеры для построения потока управления в обработчике событий. Узлы **Источники потока данных**, **Преобразования**и **Назначения потока данных** содержат источники данных, преобразования и назначения для построения потоков данных в обработчике событий. Дополнительные сведения см. в разделах [Поток управления](control-flow/control-flow.md) и [Поток данных](data-flow/data-flow.md).  
  
 Вкладка **Обработчики событий** также включает зону диспетчеров **Соединения** , в которой можно создавать и изменять диспетчеры соединений, используемых обработчиками событий для соединения с серверами и источниками данных. Дополнительные сведения см. в разделе [Создание диспетчеров соединений](../../2014/integration-services/create-connection-managers.md).  
  
### <a name="to-create-an-event-handler"></a>Создание обработчика событий  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]откройте проект служб [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] , содержащий необходимый пакет.  
  
2.  Чтобы открыть пакет, дважды щелкните его в обозревателе решений.  
  
3.  Перейдите на вкладку **Обработчики событий** .  
  
     ![Снимок экрана: область конструктора с обработчиком событий](media/eventhandlers.gif "Снимок экрана: область конструктора с обработчиком событий")  
  
     Создание потока управления и потоков данных в обработчике событий аналогично созданию потока управления и потока данных в пакете. Дополнительные сведения см. в разделах [Поток управления](control-flow/control-flow.md) и [Поток данных](data-flow/data-flow.md).  
  
4.  В списке **Исполняемый объект** выберите исполняемый объект, для которого создается обработчик события.  
  
5.  В списке **Обработчик событий** выберите обработчик событий, который необходимо построить.  
  
6.  Щелкните ссылку в области конструктора на вкладке **Обработчик событий** .  
  
7.  Добавьте элементы потока управления к обработчику событий и подключите элементы, используя управление очередностью (перетаскивая ограничение из одного элемента потока управления в другой). Дополнительные сведения см. в разделе [Поток управления](control-flow/control-flow.md).  
  
8.  Дополнительно можно добавить задачу потока данных и в области конструктора на вкладке **Поток данных** создать поток данных для обработчика событий. Дополнительные сведения см. в статье [Поток данных](data-flow/data-flow.md).  
  
9. Чтобы сохранить пакет, в меню **Файл** выберите пункт **Сохранить выбранные элементы** .  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md)   
 [Ведение журнала&#41; Integration Services &#40;SSIS](performance/integration-services-ssis-logging.md)  
  
  
