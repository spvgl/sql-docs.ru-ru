---
title: Создание прогнозов в модели кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень) | Документация Майкрософт
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 94a8d4f9-a76a-49c5-9785-917010359511
author: minewiskan
ms.author: owend
manager: kfilee
ms.openlocfilehash: 893067e234d868ae6dde2f93d93bfd50458bfeb2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63217744"
---
# <a name="creating-predictions-on-a-sequence-clustering-model-intermediate-data-mining-tutorial"></a>Создание прогнозов для модели кластеризации последовательностей (учебник по интеллектуальному анализу данных — средний уровень)
  После того, как модель кластеризации последовательностей будет лучше понять, просмотрев ее в средстве просмотра, можно создать прогнозирующие запросы с помощью конструктор запросов прогнозирования на вкладке **Прогноз модели интеллектуального анализа** данных в конструкторе интеллектуального анализа. Чтобы создать прогноз, сначала необходимо выбрать модель кластеризации последовательностей, а затем входные данные. Входные данные можно выбрать из внешнего источника данных или можно создать одноэлементный запрос и предоставить значения в диалоговом окне.  
  
 В этом занятии предполагается, что вы уже знакомы с работой построителя прогнозирующих запросов и хотите научиться создавать запросы, относящиеся к модели кластеризации последовательностей. Общие сведения об использовании конструктор запросов прогнозирования см. в статьях [интерфейсы запросов интеллектуального](../../2014/analysis-services/data-mining/data-mining-query-tools.md) анализа данных или в разделе учебника по интеллектуальному анализу данных — [создание прогнозов &#40;учебник по интеллектуальному анализу данных&#41;](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md).  
  
## <a name="creating-predictions-on-the-regional-model"></a>Создание прогнозов для региональной модели  
 В этом сценарии сначала будет создано несколько одноэлементных прогнозирующих запросов, чтобы получить представление о том, насколько прогнозы могут отличаться друг от друга в зависимости от региона.  
  
#### <a name="to-create-a-singleton-query-on-a-sequence-clustering-model"></a>Создание одноэлементного запроса к модели кластеризации последовательностей  
  
1.  Перейдите на вкладку **Прогноз модели интеллектуального анализа** данных конструктора интеллектуального анализа.  
  
2.  В меню столбец **модели интеллектуального анализа данных** выберите **одноэлементный запрос**.  
  
     Появится панель **модель интеллектуального анализа данных** и **одноэлементный запрос** .  
  
3.  На панели **модель интеллектуального анализа данных** щелкните **выбрать модель**. (Если модель кластеризации последовательностей уже выбрана, этот шаг можно пропустить.)  
  
     Откроется диалоговое окно **Выбор модели интеллектуального анализа данных** .  
  
4.  Разверните узел, представляющий структуру интеллектуального анализа данных **Кластеризация последовательностей с помощью региона**, и выберите модель **Кластеризация последовательностей с регионом**. Нажмите кнопку **ОК**. На данном этапе входная панель не учитывается. Входные данные нужно будет указать после настройки прогнозирующих функций.  
  
5.  В сетке щелкните пустую ячейку в разделе **источник** и выберите **функция прогнозирования.** В **поле**в ячейке выберите **PredictSequence**.  
  
    > [!NOTE]  
    >  Можно также использовать функцию **Predict** . В этом случае выберите версию функции **Predict** , которая принимает столбец таблицы в качестве аргумента.  
  
6.  На панели **модель интеллектуального анализа данных** выберите вложенную `v Assoc Seq Line Items`таблицу и перетащите ее в сетку в поле **критерий или аргумент** для функции **PredictSequence** .  
  
     Путем перетаскивания имен таблиц и столбцов можно создавать сложные инструкции без синтаксических ошибок. Однако он заменяет текущее содержимое ячейки, которое содержит другие необязательные аргументы функции **PredictSequence** . Чтобы просмотреть другие аргументы, можно на время добавить в сетку второй экземпляр функции и использовать его для справки.  
  
7.  Нажмите кнопку **результат** в верхнем углу конструктор запросов прогноза.  
  
 Ожидаемые результаты содержат один столбец с **выражением**заголовка. Столбец **выражение** содержит вложенную таблицу с тремя столбцами, как показано ниже.  
  
|$SEQUENCE|Line Number|Модель|  
|---------------|-----------------|-----------|  
|1||Велосипед Mountain-200|  
  
 Что означают эти результаты? Помните, что входные данные не были указаны. Следовательно, прогноз создается для всей совокупности вариантов, а службы Analysis Services возвращают наиболее вероятный общий прогноз.  
  
### <a name="adding-inputs-to-a-singleton-prediction-query"></a>Добавление входных данных к одноэлементному прогнозирующему запросу  
 До настоящего момента никакие входные данные не были указаны. В следующей задаче будет использоваться панель **ввода одноэлементного запроса** , чтобы указать некоторые входные данные для запроса. Во-первых, необходимо использовать столбец [Region] в качестве входных данных для региональной модели кластеризации последовательностей, чтобы определить, одинаковы ли спрогнозированные последовательности для всех регионов. Затем будет рассмотрено, как изменить запрос, чтобы добавить вероятность для каждого прогноза, а также как преобразовать результаты в плоский формат для более удобного просмотра.  
  
##### <a name="to-generate-predictions-for-a-specific-customer-group"></a>Создание прогнозов для определенной группы клиентов  
  
1.  Нажмите кнопку **конструктор** в верхнем левом углу конструктор запросов прогнозирования, чтобы вернуться к сетке создания запросов.  
  
2.  В диалоговом окне **Ввод одноэлементного запроса** щелкните поле **значение** для `Region`и выберите **Европа**.  
  
3.  Нажмите кнопку **результат** , чтобы просмотреть прогнозы для клиентов в Европе.  
  
4.  Нажмите кнопку **конструктор** в верхнем левом углу конструктор запросов прогнозирования, чтобы вернуться к сетке создания запросов.  
  
5.  В диалоговом окне **Ввод одноэлементного запроса** щелкните поле **значение** для `Region`и выберите **Северная Америка**.  
  
6.  Нажмите кнопку **результат** , чтобы просмотреть прогнозы для клиентов в Северная Америка.  
  
### <a name="adding-probabilities-by-using-a-custom-expression"></a>Добавление вероятностей с помощью пользовательского выражения  
 Немного сложнее получить степень вероятности для каждого прогноза, поскольку вероятность является атрибутом прогноза и выводится в виде вложенной таблицы. Владея языком расширений интеллектуального анализа данных (DMX), запрос можно легко изменить, добавив в него инструкцию подзапроса выборки для вложенной таблицы. При этом инструкцию подзапроса выборки также можно создать и в построителе прогнозирующих запросов путем добавления пользовательского выражения.  
  
##### <a name="to-output-probabilities-for-a-predicted-sequence-by-using-a-custom-expression"></a>Вывод вероятностей для прогнозируемой последовательности с помощью пользовательского выражения  
  
1.  Нажмите кнопку **конструктор** в верхнем левом углу конструктор запросов прогнозирования, чтобы вернуться к сетке создания запросов.  
  
2.  В сетке в разделе **источник**щелкните новую строку и выберите **пользовательское выражение**.  
  
3.  Оставьте **поле в поле пустым.**  
  
4.  В качестве **псевдонима**введите `t`.  
  
5.  В поле **критерий или аргумент** введите полную инструкцию подзапроса выборки, как показано в следующем примере кода. Не забудьте включить открывающую и закрывающую круглые скобки.  
  
    ```  
    (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))  
    ```  
  
6.  Нажмите кнопку **результат** , чтобы просмотреть прогнозы для клиентов в Европе.  
  
 Теперь результаты содержат две вложенные таблицы, в первой из которых указан прогноз, а во второй — степень вероятности этого прогноза. Если запрос не работает, можно переключиться в режим проектирования запросов и проверить полную инструкцию запроса, которая должна иметь следующий вид:  
  
```  
SELECT  
  PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
  ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
FROM  
  [Sequence Clustering with Region]  
NATURAL PREDICTION JOIN  
(SELECT 'Europe' AS [Region]) AS t  
```  
  
### <a name="working-with-results"></a>Работа с результатами  
 Если результаты содержат много вложенных таблиц, такие результаты можно преобразовать в плоский формат для более удобного просмотра. С этой целью можно вручную изменить запрос и добавить ключевое слово `FLATTENED`.  
  
##### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a>Преобразование вложенных наборов строк в плоский формат в прогнозирующем запросе  
  
1.  Нажмите кнопку **запроса** в углу конструктор запросов прогнозирования.  
  
     Сетка будет преобразована в открытую панель, в которой можно просмотреть и изменить инструкцию DMX, созданную построителем прогнозирующих запросов.  
  
2.  После ключевого слова `SELECT` введите `FLATTENED`.  
  
     Полный текст запроса должен быть аналогичен следующему:  
  
    ```  
    SELECT FLATTENED  
      PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]),  
      ( (SELECT PredictProbability([Model]) FROM PredictSequence([Sequence Clustering with Region].[v Assoc Seq Line Items]))) as [t]  
    FROM  
      [Sequence Clustering with Region]  
    NATURAL PREDICTION JOIN  
    (SELECT 'Europe' AS [Region]) AS t  
    ```  
  
3.  Нажмите кнопку **результаты** в верхнем углу конструктор запросов прогнозирования.  
  
 После редактирования запроса вручную нельзя вернуться в конструктор, не потеряв изменения. Тем не менее созданную вручную инструкцию DMX можно сохранить в текстовый файл, а затем снова вернуться в конструктор. При этом в окне конструктора будет восстанавливаться последняя версия запроса, имевшаяся до выхода из него.  
  
## <a name="creating-predictions-on-the-related-model"></a>Создание прогнозов для связанной модели  
 В предыдущих примерах в качестве входных данных для одноэлементного прогнозирующего запроса использовался столбец Region в таблице вариантов, так как вам было интересно узнать, нашла ли модель какие-либо различия между регионами. Однако после изучения модели стало понятно, что эти различия недостаточно существенны для составления рекомендаций по товарам на основании региона. Что вас действительно интересует в прогнозировании — это элементы, выбираемые клиентами. Поэтому в последующих запросах будет использована модель кластеризации последовательностей, не содержащая столбец Region, в целях создания рекомендаций для всех клиентов.  
  
### <a name="using-nested-table-columns-as-input"></a>Использование столбцов вложенной таблицы в качестве входных данных  
 Прежде всего необходимо создать одноэлементный прогнозирующий запрос, который в качестве входных данных использует один элемент и возвращает следующий наиболее вероятный элемент. Чтобы получить прогноз такого типа, нужно в качестве входного значения использовать столбец вложенной таблицы. Это требование вызвано тем, что прогнозируемый атрибут Model является частью вложенной таблицы. Analysis Services предоставляет диалоговое окно **входные данные вложенной таблицы** , помогающее легко создавать прогнозирующие запросы к атрибутам вложенной таблицы с помощью конструктор запросов прогнозирования.  
  
##### <a name="to-use-a-nested-table-as-input-to-a-prediction"></a>Использование вложенной таблицы в качестве входных данных для прогноза  
  
1.  Нажмите кнопку **конструктор** в верхнем левом углу конструктор запросов прогнозирования, чтобы вернуться к сетке создания запросов.  
  
2.  В диалоговом окне **Ввод одноэлементного запроса** щелкните поле **значение** для `Region`и выберите пустую строку, чтобы очистить входные данные для этого поля.  
  
3.  В диалоговом окне **Ввод одноэлементного запроса** щелкните поле **значение** для `vAssocSeqLineItems`, а затем нажмите кнопку (...).  
  
4.  В диалоговом окне **входные данные вложенной таблицы** нажмите кнопку **Добавить**.  
  
5.  В новой строке щелкните поле в разделе `Model`и выберите в списке пункт Туристический велосипед. Нажмите кнопку **ОК**.  
  
6.  Нажмите кнопку **результат** , чтобы просмотреть прогнозы.  
  
 Модель рекомендует следующие элементы, перечисленные ниже, для всех клиентов, выбравших в качестве первого элемента шину для велосипеда (Touring Tire). В результате изучения модели уже становится известно, что товары Touring Tire и Touring Tire Tube часто приобретаются клиентами вместе. Следовательно, эти рекомендации вполне обоснованы.  
  
|$SEQUENCE|Line Number|Модель|  
|---------------|-----------------|-----------|  
|1||Камера для покрышки туристического велосипеда|  
|2||Sport-100|  
|3||Кофта с длинными рукавами и эмблемой|  
  
### <a name="creating-a-bulk-prediction-query-using-nested-table-inputs"></a>Создание массового прогнозирующего запроса, используя входные данные вложенной таблицы  
 Теперь, когда модель создает прогнозы, которые можно использовать для предоставления рекомендаций, нужно создать прогнозирующий запрос, который сопоставляется с внешним источником данных. Из источника данных будут взяты значения, представляющие текущие продукты. Поскольку необходимо создать прогнозирующий запрос, предоставляющий идентификатор клиента и список продуктов в качестве входных данных, потребуется добавить таблицу клиентов в качестве таблицы вариантов и таблицу покупок в качестве вложенной таблицы. Затем нужно добавить прогнозирующие функции для создания рекомендаций, как это делалось ранее.  
  
 Данная процедура аналогична процедуре создания прогнозов в сценарии потребительской корзины, описанном в занятии 3. Однако в модели кластеризации последовательностей для прогнозов также нужно указать заказ в качестве входных данных.  
  
##### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a>Создание прогнозирующего запроса с использованием входных данных вложенной таблицы  
  
1.  На панели **модель интеллектуального анализа данных** выберите модель кластеризации последовательностей, если она еще не выбрана.  
  
2.  В диалоговом окне **Выбор входных таблиц** нажмите кнопку **выбрать таблицу вариантов**.  
  
3.  В диалоговом окне **Выбор таблицы** для поля источник данных выберите заказы. В списке **имя таблицы или представления** выберите vAssocSeqOrders и нажмите кнопку **ОК**.  
  
4.  В диалоговом окне **Выбор входных таблиц** нажмите кнопку **выбрать вложенную таблицу**.  
  
5.  В диалоговом окне **Выбор таблицы** для поля **источник данных**выберите заказы. В списке **имя таблицы или представления** выберите vAssocSeqLineItems и нажмите кнопку **ОК**.  
  
     Службы Analysis Services выполнят попытку выявить связи и создать их автоматически, если типы данных и имена столбцов совпадают. Если создаваемые связи неверны, можно щелкнуть правой кнопкой мыши линию соединения и выбрать пункт **Изменить соединения** , чтобы изменить сопоставление столбцов, или щелкнуть правой кнопкой мыши строку соединения и выбрать команду **Удалить** , чтобы полностью удалить связь. В таком случае эти связи автоматически добавляются на панели конструирования, поскольку таблицы уже были соединены в представлении источника данных.  
  
6.  Добавьте в сетку новую строку. В поле **источник**выберите vAssocSeqOrders, а для **поля**выберите CustomerKey.  
  
7.  Добавьте в сетку новую строку. В поле **источник**выберите **функция прогнозирования**, а для **поля**выберите **PredictSequence**.  
  
8.  Перетащите vAssocSeqLineItems в поле **критерий или аргумент** . Щелкните в конце поля **критерий или аргумент** и введите следующие аргументы: `2`.  
  
     Полный текст в поле **критерий или аргумент** должен быть следующим:`[Sequence Clustering].[v Assoc Seq Line Items],2`  
  
9. Нажмите кнопку **результат** , чтобы просмотреть прогнозы для каждого клиента.  
  
 Учебник по моделям кластеризации последовательностей завершен.  
  
## <a name="next-steps"></a>Next Steps  
 Если вы выполнили все разделы [учебника по интеллектуальному анализу данных &#40;Analysis Services-&#41;интеллектуального анализа данных ](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md), то на следующем этапе можно научиться использовать инструкции расширений интеллектуального анализа данных для построения моделей и формирования прогнозов. Дополнительные сведения см. в статьях [Создание и запрос моделей интеллектуального анализа данных с помощью расширений интеллектуального анализа: учебники &#40;Analysis Services-&#41;интеллектуального анализа данных ](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md).  
  
 Пользователи, которым знакомы основные понятия программирования, также могут использовать объекты AMO для работы с объектами интеллектуального анализа данных программным путем. Дополнительные сведения см. в разделе [Классы интеллектуального анализа данных объектов AMO](https://docs.microsoft.com/bi-reference/amo/amo-data-mining-classes).  
  
## <a name="see-also"></a>См. также:  
 [Примеры запросов к модели кластеризации последовательностей](../../2014/analysis-services/data-mining/sequence-clustering-model-query-examples.md)   
 [Содержимое модели интеллектуального анализа данных для моделей кластеризации последовательностей &#40;Analysis Services-интеллектуальный анализ данных&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-sequence-clustering-models.md)  
  
  
