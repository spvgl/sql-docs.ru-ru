---
title: Переразметка (SQL Server надстроек интеллектуального анализа данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data preparation
- relabel
- data cleaning
ms.assetid: af041b39-fdd1-4cb5-a5ef-2f3ddab84614
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5471720cbd3084c661dec93d9c7f4f680e066b86
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66070395"
---
# <a name="relabel-sql-server-data-mining-add-ins"></a>Переразметка (надстройки интеллектуального анализа данных SQL Server)
  ![Значок Office 13 для средства «Переразметка»](media/dm13-relabel.gif "Значок Office 13 для средства «Переразметка»")  
  
 С помощью клиента интеллектуального анализа данных для Excel можно создать для данных новые метки, чтобы облегчить понимание результатов анализа.  
  
 Причины для переразметки:  
  
-   Данные содержат закодированные результаты, например 1 — мужчины, 2 — женщины.  
  
-   Вы группируете числовые значения и хотите указать описательные имена для диапазонов.  
  
-   Вы хотите упростить длинные имена.  
  
## <a name="using-the-relabel-wizard"></a>Использование мастера переразметки  
  
1.  На ленте **интеллектуальный анализ данных** нажмите кнопку **очистить** , а затем выберите пункт **изменить метку**.  
  
2.  Выберите таблицу или диапазон данных, содержащий данные, которые необходимо исправить.  
  
3.  На странице мастера **переразметки** выберите один столбец, либо выбрав столбец из раскрывающегося списка, либо щелкнув столбец на панели **образцы данных** .  
  
     На панели " **образцы данных** " отображается только около 50 строк данных, но они вычисляются, чтобы убедиться, что вы видите хороший разворот значений.  
  
     Щелкните заголовок столбца **Count** , чтобы выполнить сортировку по количеству значений.  
  
     Кроме того, можно выполнять сортировку по **исходным меткам**, что удобно, если необходимо сначала повторно пометить все наиболее или наименьшие значения.  
  
4.  На странице " **переметка** данных" мастера проверьте значения в столбце **исходные метки** и выберите способ группировки или редактирования.  
  
5.  Введите новое значение в строку под заголовком **новые метки**. Также можно выбрать значение из списка существующих значений. При вводе новых значений они сразу же становятся доступными для повторного использования.  
  
6.  Если введено достаточное количество строк, нажмите кнопку **Далее**, а затем на странице **Выбор назначения** выберите место сохранения перепомеченных данных.  
  
    -   **Добавление нового столбца на текущий лист**  
  
         Щелкните, чтобы добавить новый столбец в таблицу, содержащую новые значения.  
  
    -   **Копирование данных листа с изменениями на новый лист**  
  
         Щелкните, чтобы создать новый лист, содержащий обновленные данные.  
  
    -   **Изменение данных на месте**  
  
         Щелкните, чтобы заменить исходные данные новыми значениями.  
  
## <a name="see-also"></a>См. также:  
 [Исследование и очистка данных](exploring-and-cleaning-data.md)  
  
  
