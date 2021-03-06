---
title: Анализ ключевых факторов влияния (средства анализа таблиц для Excel) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: df6622abc3a507d917aefd2a8a5a1bf9505a2622
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66062263"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a>Анализ ключевых факторов влияния (средства анализа таблиц для Excel)
  ![Кнопка «Анализ ключевых факторов влияния» на ленте](media/tat-aki.gif "Кнопка «Анализ ключевых факторов влияния» на ленте")  
  
 С помощью средства **Анализ ключевых факторов влияния** вы выбираете столбец, содержащий целевой результат, и алгоритм определяет, какие факторы приводят к наибольшему влиянию на результат.  
  
 Средство создает новые таблицы данных с факторами, связанными с каждым результатом, и графически отображает вероятность связи между ними. Эти таблицы можно отфильтровать по различным факторам и результатам, чтобы подробнее проанализировать результаты.  
  
 Вы также можете выбрать пару возможных результатов и сравнить их. Например, можно сравнить различные группы потребителей, чтобы определить факторы, влияющие на принятие решений.  
  
## <a name="using-the-analyze-key-influencers-tool"></a>Использование средства «Анализ ключевых факторов влияния»  
  
1.  Откройте таблицу данных Excel.  
  
2.  В окне **инструменты таблицы**на ленте **анализ** щелкните **Анализ ключевых факторов влияния.**  
  
3.  Выберите столбец, который будет целью анализа.  
  
4.  При необходимости нажмите кнопку **выбрать столбцы, которые будут использоваться для анализа**. В диалоговом окне **Выбор дополнительных столбцов** выберите столбцы, которые, скорее всего, будут содержать нужные данные. Чтобы повысить производительность и точность, отмените выбор столбцов, например идентификатора или имени, не относящихся к анализу закономерностей. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Выбор дополнительных столбцов** .  
  
5.  Нажмите кнопку **Запустить**.  
  
     Средство **Анализ ключевых факторов влияния** выполняет анализ данных для определения оптимальных параметров и автоматически задает все параметры.  
  
6.  Если закономерности не были обнаружены, то мастер создаст новый лист, в котором будет описана проблема.  
  
7.  При обнаружении закономерностей мастер создаст на новом листе отчет, в котором будут отображены эти закономерности. Отчет называется **ключевыми факторами влияния для \<>столбца **. Отчет можно настроить, как это описано в следующей процедуре.  
  
#### <a name="create-a-custom-report"></a>Создание пользовательского отчета  
  
1.  В диалоговом окне **Сравнение на основе ключевых факторов влияния** выберите два значения, которые необходимо сравнить, выбрав их в раскрывающихся списках **значение 1** и **значение 2** . Например, можно сравнить покупателей и тех, кто не покупает.  
  
2.  Нажмите кнопку **Добавить отчет**.  
  
     Мастер создаст новый лист и добавит таблицу для каждой пары сравнения ключевых факторов влияния.  
  
3.  Завершив сравнение, нажмите кнопку **Закрыть**.  
  
## <a name="understanding-the-key-influencers-report"></a>Основные сведения об отчете по ключевым факторам влияния  
 После создания модели данных средство **Анализ ключевых факторов влияния** создает отчеты, помогающие исследовать и сравнивать ключевые факторы влияния.  
  
-   Отчет в левой части создается по умолчанию. В нем отображаются столбцы, которые лучше всего подходят для прогнозирования столбца итогового результата (зависимой переменной).  
  
-   Отчет, отображаемый в правой части, является необязательным. Его можно создать путем сравнения двух конкретных значений результатов. Этот отчет сравнивает тех, кто купил, и тех, кто не купил.  
  
-   Обратите внимание, что новый лист добавляется для каждого создаваемого отчета. Таблицы после их создания можно перемещать. Для сравнения мы разместили их рядом друг с другом.  
  
 ![DM13](media/dm13-tat-aki-report.gif "DM13")  
  
 **Относительное влияние**  
 Затененная полоса в первом отчете показывает степень взаимосвязи этого атрибута с результатом.  
  
 Длина полосы показывает вероятность влияния фактора на результат и, следовательно, чем она длиннее, тем теснее взаимосвязь.  
  
 **Подходит**  
 Во втором отчете сравниваемые целевые значения приведены в двух столбцах, а связанные факторы указаны в порядке нисходящей достоверности.  
  
-   **Синяя** полоса показывает атрибуты, влияющие на результат «нет» (= не приобретается).  
  
-   **Красная** полоса показывает атрибуты, влияющие на результат "Да" (= куплен велосипед).  
  
 Цвета заливки произвольные. Цвета можно изменить путем задания параметров для проекта таблицы в Excel.  
  
 При создании отчета, сравнивающего два значения, во втором отчете ключевые факторы влияния сортируются с учетом их влияния на целевые значения.  
  
 Поскольку все диаграммы созданы на основе таблиц Excel, данные можно фильтровать и сортировать для выделения определенных факторов или результатов.  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a>Дополнительные сведения об использовании средства «Анализ ключевых факторов влияния»  
 Когда средство **Анализ ключевых факторов влияния** анализирует данные, оно выполняет следующие действия:  
  
-   Создает структуру данных, в которой хранятся основные сведения о распределении данных.  
  
-   Создает модель с помощью упрощенного алгоритма Байеса (Майкрософт).  
  
-   Создает прогнозы, в которых каждый столбец данных связывается с указанным результатом.  
  
-   Использует показатель достоверности для каждого из прогнозов с целью определения факторов, оказывающих наибольшее влияние при получении целевого результата.  
  
-   Создает отчет, в котором описываются ключевые факторы влияния, упорядоченные по достоверности.  
  
### <a name="requirements"></a>Требования  
 Если целевой столбец содержит непрерывные числовые значения, они автоматически сегментируются на группы. Эти группы представляют собой кластеры вариантов, имеющих схожие характеристики. Однако числовые значения могут быть не разделены на удобные для пользователей группы. Например, отчет может содержать группирование «\<12,85701», в то время как пользователи отчетов обычно должны видеть группирования, использующие целые числа, такие как 10-19, 20-29 и т. д.  
  
 Если требуется сгруппировать числовые данные по-другому, то перед созданием анализа их необходимо соответствующим образом сегментировать. Например, можно использовать средство [Переразметка](relabel-sql-server-data-mining-add-ins.md) в клиенте интеллектуального анализа данных для Excel, чтобы создать новую метку группирования в отдельном столбце, а затем использовать только этот новый столбец в анализе.  
  
### <a name="related-tools"></a>Дополнительные средства  
 На ленте **интеллектуальный анализ данных** предоставляются более сложные средства, включая возможность настройки моделей интеллектуального анализа данных.  
  
 При сохранении модели с помощью средства **Анализ ключевых факторов влияния** можно использовать клиент интеллектуального анализа данных для просмотра модели и более подробного изучения связей. Дополнительные сведения см. [в разделе Просмотр моделей в Excel &#40;SQL Server надстройки интеллектуального анализа данных&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md). Microsoft Office Visio можно использовать для создания графиков и схем, отображающих связи в виде кластеров или сетей зависимостей. Дополнительные сведения см. в разделе [Устранение неполадок диаграмм интеллектуального анализа данных Visio &#40;SQL Server надстроек интеллектуального анализа данных&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).  
  
> [!NOTE]  
>  Модели, создаваемые при работе со средствами анализа таблиц, удаляются при закрытии листа или разрыве соединения с сервером служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. В связи с этим можно только просматривать модели, пока соединение остается открытым. Невозможно подготовить модели к просмотру в Visio после разрыва соединения или закрытия листа.  
  
 Дополнительные сведения о алгоритме, используемом средством **анализа ключевых факторов влияния** , см. в подразделе "упрощенный алгоритм Байеса (Майкрософт)" в Электронная документация на SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [Средства анализа таблиц для Excel](table-analysis-tools-for-excel.md)   
 [Создание модели интеллектуального анализа данных](creating-a-data-mining-model.md)  
  
  
