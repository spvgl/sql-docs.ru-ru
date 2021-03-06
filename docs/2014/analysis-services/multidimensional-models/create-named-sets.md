---
title: Создание именованных наборов | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c1fc4ab5d778535fdc4e2186c5bc88741b4367f5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66076140"
---
# <a name="create-named-sets"></a>Создание именованных наборов
  Именованный набор — это набор элементов измерения или выражение набора, которые создаются для многократного использования, например в запросах на языке многомерных выражений. Для создания именованных наборов может использоваться сочетание данных куба, арифметических операторов, чисел и функций. Например, можно создать именованный набор с именем Top Ten Factories, содержащий десять элементов измерения Factories с наибольшими значениями показателя Production. Затем набор Top Ten Factories можно использовать в запросах конечных пользователей. Например, конечный пользователь помещает набор Top Ten Factories на одну ось, а измерение меры, включая Production, — на другую ось. Дополнительные сведения см. в разделах [Вычисления в многомерных моделях](calculations-in-multidimensional-models.md) и [Построение именованных наборов в многомерных выражениях](mdx/mdx-named-sets-building-named-sets.md).  
  
 Чтобы создать именованный набор, можно воспользоваться командой **Создать именованный набор** на вкладке **Вычисления** конструктора кубов. Эта команда может быть вызвана из меню **Куб** на панели инструментов вкладки **Вычисления** . Эта команда отображает форму для задания следующих параметров именованного набора.  
  
 **Название**  
 Выберите имя именованного набора. Это имя отображается при просмотре куба конечными пользователями.  
  
 **Выражение**  
 Укажите выражение, из которого получается именованный набор. Это выражение может быть записано на языке многомерных выражений. Выражение может содержать любой из следующих объектов:  
  
-   выражения данных, которые представляют компоненты куба, такие как измерения, уровни, меры и т. д.;  
  
-   арифметические операторы;  
  
-   числа.  
  
-   функции.  
  
 Можно скопировать или перетащить компоненты куба с вкладки **Метаданные** панели **Средства вычисления** в поле **Выражение** панели **Редактор форм именованных наборов** . Можно скопировать или перетащить функции с вкладки **Функции** панели **Средства вычисления** в поле **Выражение** панели **Редактор форм именованных наборов** .  
  
> [!IMPORTANT]  
>  Если выражение набора создается путем явного именования элементов в наборе, заключите список элементов в пару фигурных скобок ({}).  
  
## <a name="see-also"></a>См. также:  
 [Вычисления в многомерных моделях](calculations-in-multidimensional-models.md)  
  
  
