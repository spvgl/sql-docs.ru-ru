---
title: Анализ в Excel (вкладка «браузер», конструктор кубов) (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2833fb2ecbbac269442ce149cd5673abedcf83c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062368"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Анализ в Excel (вкладка «Браузер», конструктор кубов) (службы Analysis Services — многомерные данные)
  **Анализ в Excel** предоставляет разработчику кубов возможность быстро просмотреть, как будет выглядеть проект для конечного пользователя. Функция **Анализ в Excel** открывает Microsoft Excel, создает соединение с источником данных, которым выступает база данных рабочей области, и автоматически добавляет сводную таблицу на лист. Эта функция заменяет веб-элемент управления Office на вкладке «Браузер», который в предыдущих версиях содержал внедренную сводную таблицу.  
  
 **Для просмотра данных куба выполните следующие действия.**  
  
1.  В среде [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]в обозревателе решений дважды щелкните куб, чтобы открыть его в конструкторе кубов.  
  
2.  Перейдите на вкладку **Браузер** .  
  
3.  Чтобы проверить соединение, нажмите кнопку **Повторное соединение** .  
  
4.  Щелкните значок Excel в строке меню.  
  
5.  Нажмите кнопку **Включить**в окне, предлагающем включить подключения к данным. Открывается Excel с использованием текущего подключения к данным, на лист добавляется сводная таблица, и можно просматривать данные.  
  
 Теперь можно построить сводную таблицу в интерактивном режиме, перетаскивая меры из таблицы фактов в область «Значения», а атрибуты измерения — в области «Строки» и «Столбцы». Имеющиеся иерархии добавляются в область «Строки» или «Столбцы». Можно выполнять свертку и детализацию углублением иерархии для просмотра данных фактов на разных уровнях.  
  
 Объекты и данные просматриваются в контексте действующего пользователя или роли и перспективы. В Excel при выполнении запроса для соединения с источником данных используются учетные данные текущего пользователя, а не указанные на странице **Сведения об олицетворении** .  
  
> [!NOTE]  
>  Для использования функции «Анализ в Excel» приложение Excel должно быть установлено на одном компьютере со средой [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Если Excel не установлен на этом компьютере, можно использовать Excel на другом компьютере для подключения к кубу как к источнику данных. Затем можно вручную добавить сводную таблицу на лист. Объекты модели (таблицы, столбцы, меры и ключевые показатели эффективности) включаются в качестве полей в список полей сводной таблицы.  
  
 Дополнительные сведения о функции **Анализ в Excel** см. в следующих ресурсах:  
  
 [Анализ в Excel &#40;табличные&#41;SSAS](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [Анализ табличной модели в Excel &#40;табличные&#41;SSAS](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [Просмотр данных и метаданных в кубе](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a>См. также:  
 [Обозреватель &#40;конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Панель инструментов &#40;вкладка «браузер», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Вкладка браузера &#40;метаданных, конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Вкладка «браузер запросов и фильтров &#40;», конструктор кубов&#41; &#40;Analysis Services многомерных данных&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  
