---
title: Занятие 1. Создание структуры интеллектуального анализа данных для потребительской корзины | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62676281"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a>Урок 1. Создание структуры интеллектуального анализа "Потребительская корзина"
  На этом занятии требуется создать структуру интеллектуального анализа, позволяющуюй делать прогнозы относительно товаров [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], которые клиент обычно покупает одновременно. Дополнительные сведения о структурах интеллектуального анализа данных и их ролях в интеллектуальном анализе см. в разделе [структуры интеллектуального анализа данных &#40;Analysis Services-&#41;интеллектуального анализа ](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).  
  
 Структура интеллектуального анализа данных взаимосвязей, которая будет создана на этом занятии, поддерживает добавление моделей интеллектуального анализа данных на основе [алгоритма взаимосвязей (Майкрософт](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)). На следующих занятиях с помощью этих моделей интеллектуального анализа будет сформирован прогноз относительно типов товара, покупаемых клиентом одновременно, называемый анализом потребительской корзины.  Например, можно обнаружить, что обычно клиенты покупают одновременно горные велосипеды, шины для велосипедов и шлемы.  
  
 На данном занятии структура интеллектуального анализа определяется с помощью вложенных таблиц. Использование вложенных таблиц необходимо, потому что определяемый структурой домен данных содержится в двух различных исходных таблицах. Дополнительные сведения о вложенных таблицах см. в разделе [вложенные таблицы &#40;Analysis Services-&#41;интеллектуального анализа данных ](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).  
  
## <a name="create-mining-structure-statement"></a>Инструкция CREATE MINING STRUCTURE  
 Чтобы создать структуру интеллектуального анализа данных, содержащую вложенную таблицу, используется инструкция [CREATE интеллектуального анализа данных &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) . Код инструкции можно разбить на следующие части:  
  
-   Присвоение структуре имени  
  
-   Определение ключевого столбца  
  
-   Определение столбцов интеллектуального анализа данных  
  
-   Определение столбцов вложенных таблиц  
  
 В следующем фрагменте показан общий пример инструкции CREATE MINING STRUCTURE:  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 Первая строчка кода определяет имя структуры:  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 Сведения об именовании объекта в расширениях интеллектуального анализа данных см. в разделе [идентификаторы &#40;&#41;расширений интеллектуального анализа данных ](/sql/dmx/identifiers-dmx).  
  
 Следующая строка кода определяет ключевой столбец структуры интеллектуального анализа данных, уникально определяющий сущность в исходных данных:  
  
```  
<key column>  
```  
  
 В следующей строке кода определяются столбцы интеллектуального анализа, используемые моделями интеллектуального анализа, связанными со структурой интеллектуального анализа:  
  
```  
<mining structure columns>  
```  
  
 В следующих строках кода определяются столбцы вложенных таблиц:  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 Дополнительные сведения о типах столбцов структуры интеллектуального анализа данных, которые можно определить, см. в разделе [столбцы структуры интеллектуального анализа данных](../../2014/analysis-services/data-mining/mining-structure-columns.md).  
  
> [!NOTE]  
>  По умолчанию среда [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] создает 30-процентный набор контрольных данных для каждой структуры интеллектуального анализа данных. Однако, если для создания структуры используются расширения интеллектуального анализа данных, набор контрольных данных необходимо добавить вручную, если он нужен.  
  
## <a name="lesson-tasks"></a>Задачи занятия  
 На этом занятии будут выполнены следующие задачи.  
  
-   Создание нового пустого запроса  
  
-   Изменение запроса, чтобы создать структуру интеллектуального анализа данных  
  
-   Выполнение запроса  
  
## <a name="creating-the-query"></a>Создание запроса  
 На первом этапе необходимо подключиться к экземпляру служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] и создать новый DMX-запрос в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a>Создание нового DMX-запроса в среде SQL Server Management Studio  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
2.  В диалоговом окне **соединение с сервером** в поле **тип сервера**выберите **Analysis Services**. В поле **имя сервера**введите `LocalHost`или имя экземпляра [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] , к которому необходимо подключиться для этого занятия. Нажмите кнопку **Соединить**.  
  
3.  В окне **Обозреватель объектов**щелкните правой кнопкой мыши экземпляр служб [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], укажите **Создать запрос**, а затем выберите пункт **Расширения интеллектуального анализа данных**.  
  
     Откроется редактор запросов, содержащий новый, пустой запрос.  
  
## <a name="altering-the-query"></a>Изменение запроса  
 На следующем этапе необходимо изменить описанную выше инструкцию CREATE MINING STRUCTURE, чтобы создать структуру интеллектуального анализа «Потребительская корзина».  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a>Настройка инструкции CREATE MINING STRUCTURE  
  
1.  В редакторе запросов скопируйте общий пример инструкции CREATE MINING STRUCTURE в пустое окно запроса.  
  
2.  Вместо  
  
    ```  
    [mining structure name]   
    ```  
  
     на:  
  
    ```  
    [Market Basket]  
    ```  
  
3.  Вместо  
  
    ```  
    <key column>  
    ```  
  
     на:  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  Вместо  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     на:  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     Язык TEXT KEY указывает, что столбец модели является ключевым столбцом для вложенной таблицы.  
  
     Полная инструкция создания структуры интеллектуального анализа данных должна выглядеть так:  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  В меню **Файл** щелкните **Сохранить DMXQuery1.dmx как**.  
  
6.  В диалоговом окне **Сохранить как** перейдите в соответствующую папку и присвойте файлу `Market Basket Structure.dmx`имя.  
  
## <a name="executing-the-query"></a>Выполнение запроса  
 На последнем шаге нужно выполнить запрос. После создания и сохранения запроса его нужно выполнить (то есть нужно выполнить инструкцию), чтобы создать на сервере структуру интеллектуального анализа данных. Дополнительные сведения о выполнении запросов в редакторе запросов см. в разделе [ядро СУБД редактор запросов &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).  
  
#### <a name="to-execute-the-query"></a>Выполнение запроса  
  
-   На панели инструментов редактора запросов нажмите кнопку **выполнить**.  
  
     Состояние запроса отображается на вкладке **сообщения** в нижней части редактора запросов после завершения выполнения инструкции. Сообщение должно выглядеть следующим образом:  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     На сервере теперь существует новая структура с именем " **Потребительская корзина** ".  
  
 На следующем занятии к созданной структуре интеллектуального анализа «Потребительская корзина» будет добавлена модель интеллектуального анализа.  
  
## <a name="next-lesson"></a>Следующее занятие  
 [Урок 2. Добавление моделей интеллектуального анализа данных к структуре интеллектуального анализа данных "Потребительская корзина"](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
