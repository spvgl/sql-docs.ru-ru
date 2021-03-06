---
title: Совместная работа обработчиков событий | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- events [ADO], about event handlers
- unpaired event handlers [ADO]
- paired event handlers [ADO]
- single event handlers [ADO]
- event handlers [ADO]
- multiple object event handlers [ADO]
ms.assetid: a86c8a02-dd69-420d-8a47-0188b339858d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b744dbd464aedbd9b87d22aa74277787fcc3c7a3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67925043"
---
# <a name="how-event-handlers-work-together"></a>Совместная работа обработчиков событий
Если вы не программируете в Visual Basic, необходимо реализовать все обработчики событий для **соединений** и событий **набора записей** независимо от того, действительно ли вы обрабатываете все события. Объем работ по реализации зависит от языка программирования. Дополнительные сведения см. в разделе [Создание экземпляра события ADO по языку](../../../ado/guide/data/ado-event-instantiation-by-language.md).  
  
## <a name="paired-event-handlers"></a>Сопряженные обработчики событий  
 Каждый обработчик событий будет иметь связанный **полный** обработчик событий. Например, когда приложение изменяет значение поля, вызывается обработчик событий **виллчанжефиелд** . Если изменение допустимо, приложение оставляет параметр **адстатус** без изменений и выполняется операция. По завершении операции событие **фиелдчанжекомплете** уведомляет ваше приложение о завершении операции. Если оно успешно завершено, **адстатус** содержит **адстатусок**; в противном случае **адстатус** содержит **адстатусеррорсоккурред** , и необходимо проверить объект **Error** , чтобы определить причину ошибки.  
  
 При вызове **виллчанжефиелд** можно определить, что изменение не должно выполняться. В этом случае задайте для **адстатус** значение **адстатусканцел.** Операция отменяется, а событие **фиелдчанжекомплете** получает значение **адстатус** **адстатусеррорсоккурред**. Объект **Error** содержит **адерроператионканцеллед** , чтобы обработчик **фиелдчанжекомплете** знал, что операция была отменена. Однако необходимо проверить значение параметра **адстатус** перед его изменением, так как задание **адстатус** в **адстатусканцел** не будет действовать, если для параметра было задано значение **адстатускантдени** при записи в процедуру.  
  
 Иногда операция может вызвать более одного события. Например, объект **Recordset** имеет парные события для изменения **полей** и внесения изменений в **записи** . Когда приложение изменяет значение **поля**, вызывается обработчик событий **виллчанжефиелд** . Если он определяет, что операция может быть продолжена, также вызывается обработчик событий **виллчанжерекорд** . Если этот обработчик также разрешает продолжение события, выполняется изменение и вызываются обработчики событий **фиелдчанжекомплете** и **рекордчанжекомплете** . Порядок, в котором будут вызываться обработчики событий для определенной операции, не определен, поэтому следует избегать написания кода, который зависит от вызывающих обработчиков в определенной последовательности.  
  
 В случаях, когда возникает несколько событий, одно из событий может отменить отложенную операцию. Например, когда приложение изменяет значение **поля**, обычно вызываются обработчики событий **виллчанжефиелд** и **виллчанжерекорд** . Однако если операция отменяется в первом обработчике событий, соответствующий **полный** обработчик вызывается с **адстатусоператионканцеллед**. Второй обработчик никогда не вызывается. Тем не менее, если первый обработчик событий разрешает продолжение события, вызывается другой обработчик событий. Если он отменяет операцию, **то оба события** будут вызываться как в предыдущих примерах.  
  
## <a name="unpaired-event-handlers"></a>Непарные обработчики событий  
 Пока состояние, переданное в событие, не **адстатускантдени**, можно отключить уведомления о событиях для любого события, возвращая **адстатусунвантедевент** в параметре *Status* . Например, если **полный** обработчик событий вызывается впервые, можно вернуть **адстатусунвантедевент**. Впоследствии **будут получены только события** . Однако некоторые события могут быть активированы по более чем одной причине. В этом случае событие будет иметь параметр *Reason* . Когда вы вернете **адстатусунвантедевент**, вы перестанете получать уведомления для этого события только в том случае, если они появятся по этой конкретной причине. Иными словами, вы будете получать уведомления по каждой возможной причине, когда событие может быть активировано.  
  
 Если требуется изучить параметры, **которые будут использоваться** в операции, можно использовать обработчики событий Single. Можно изменить эти параметры операции или отменить операцию.  
  
 Или оставьте уведомление о **завершении** события включено. При вызове первого обработчика событий возвращается **адстатусунвантедевент**. Впоследствии будут получены только **полные** события.  
  
 Для управления асинхронными операциями можно **использовать отдельные** обработчики событий. Каждая асинхронная операция имеет соответствующее **полное** событие.  
  
 Например, заполнение большого объекта [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) может занять много времени. Если приложение является соответствующим образом записанным, можно запустить `Recordset.Open(...,adAsyncExecute)` операцию и продолжить обработку. Со временем вы будете уведомлены о заполнении **набора записей** событием **ексекутекомплете** .  
  
## <a name="single-event-handlers-and-multiple-objects"></a>Отдельные обработчики событий и несколько объектов  
 Гибкость языка программирования, например Microsoft Visual C++®, позволяет одному обработчику событий обрабатывать события из нескольких объектов. Например, у вас может быть один обработчик событий **Disconnect** , обрабатывающий события из нескольких объектов **соединения** . Если одно из соединений завершилось, будет вызван обработчик событий **Disconnect** . Можно определить, какое соединение вызвало событие, так как параметр объекта обработчика событий будет установлен в соответствующий объект **соединения** .  
  
> [!NOTE]
>  Этот метод не может использоваться в Visual Basic, поскольку этот язык может сопоставлять только один объект с обработчиком событий.  
  
## <a name="see-also"></a>См. также:  
 [Сводка по обработчику событий ADO](../../../ado/guide/data/ado-event-handler-summary.md)   
 [Создание экземпляра события ADO по языку](../../../ado/guide/data/ado-event-instantiation-by-language.md)   
 [Параметры события](../../../ado/guide/data/event-parameters.md)   
 [Типы событий](../../../ado/guide/data/types-of-events.md)
