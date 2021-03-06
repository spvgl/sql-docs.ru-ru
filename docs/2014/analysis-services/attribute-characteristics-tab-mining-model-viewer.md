---
title: Вкладка «Характеристики атрибута» (средство просмотра моделей интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.naivebayse.characteristics.f1
ms.assetid: f0c3350d-84c0-4ab8-9fb8-1527c2647299
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e35cf7db00effb5ce700a1ac883877f67650d3cc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66063051"
---
# <a name="attribute-characteristics-tab-mining-model-viewer"></a>Вкладка «Характеристики атрибутов» (средство просмотра моделей интеллектуального анализа данных)
  Используйте панель **Характеристики атрибутов** для исследования связей между результатами и входными атрибутами в модели упрощенного алгоритма Байеса. Вы можете использовать значение целевого атрибута, а затем просмотреть список входных атрибутов, имеющих самое сильное влияние на результаты.  
  
 Дополнительные **сведения:** [упрощенный алгоритм Байеса (Майкрософт](data-mining/microsoft-naive-bayes-algorithm.md)), [Просмотр модели с помощью средства Microsoft Байеса Байеса](data-mining/browse-a-model-using-the-microsoft-naive-bayes-viewer.md)  
  
## <a name="options"></a>Параметры  
 **Обновить содержимое средства просмотра**  
 Перезагрузить модель интеллектуального анализа данных в средстве просмотра.  
  
 **Модель интеллектуального анализа данных**  
 Выбрать модель интеллектуального анализа данных для просмотра из числа моделей в текущей структуре интеллектуального анализа данных. Модель интеллектуального анализа данных будет автоматически открыта в пользовательском средстве просмотра, наиболее подходящем для определенного типа выбранной модели.  
  
 **Программой**  
 Выберите средство просмотра для выбранной модели интеллектуального анализа данных. Для каждой модели можно выбрать пользовательское средство просмотра или средство просмотра содержимого интеллектуального анализа данных [!INCLUDE[msCoName](../includes/msconame-md.md)] . Подключаемые модули просмотра также отображаются в этом списке, если они доступны.  
  
 **attribute**  
 Выберите прогнозируемый атрибут, который требуется проанализировать.  
  
 **Value**  
 Выберите состояние прогнозируемого атрибута, установленное в поле **Атрибут**. Поскольку модели упрощенного алгоритма Байеса не поддерживают непрерывные переменные, все целевые атрибуты имеют дискретные или дискретизированные результаты. Атрибут Missing всегда автоматически добавляется к списку.  
  
 **Характеристики \<прогнозируемого состояния>**  
 Диаграмма содержит следующие столбцы, которые описывают, как состояния входных атрибутов связаны с состоянием выбранного прогнозируемого атрибута.  
  
|Значение|Description|  
|-----------|-----------------|  
|**Перемен**|Перечисляет входные атрибуты в модели интеллектуального анализа данных.|  
|**Значения**|Перечисляет каждое состояние входного атрибута в списке **Переменная**.|  
|**Воспроизведение**|Полоса представляет вероятность того, что атрибут и значение в этой строке связаны с выбранным состоянием прогнозируемого атрибута. Наведите курсор мыши на полосу для просмотра вероятности (в процентах).|  
  
## <a name="see-also"></a>См. также:  
 [Алгоритмы интеллектуального анализа данных &#40;Analysis Services — интеллектуальный анализ данных&#41;](data-mining/data-mining-algorithms-analysis-services-data-mining.md)   
 [Средства просмотра моделей интеллектуального анализа &#40;конструктор моделей интеллектуального анализа данных&#41;](mining-model-viewers-data-mining-model-designer.md)   
 [Средства просмотра моделей интеллектуального анализа данных](data-mining/data-mining-model-viewers.md)  
  
  
