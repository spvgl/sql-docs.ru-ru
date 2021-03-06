---
title: Использование репозиториев тестирования (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Test Cases Repository
- Test Results Repository
ms.assetid: f941cce4-d3e3-4aeb-a88a-4f101a97a9f4
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: da99b63c986029a1791793fbbd33910bb95d4b7b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68086804"
---
# <a name="using-test-repositories-oracletosql"></a>Использование репозиториев тестирования (OracleToSQL)
В репозитории тестов SSMA хранятся тестовые случаи и результаты тестов тестеров SSMA для последующего использования. Данные репозитория сохраняются в SQL Server таблицах **тесткасерепоситори** и **рунтесткасересултрепоситори** в схеме **ssma_oracle_utilities** базы данных **ссматестердб** .  
  
В диалоговом окне репозиторий тестовых случаев доступны следующие кнопки:  
  
-   Нажмите кнопку " **Обновить** ", чтобы обновить список тестовых случаев или результаты теста.  
  
-   Нажмите кнопку **Закрыть** , чтобы закрыть диалоговое окно репозиторий для тестовых случаев.  
  
## <a name="test-cases-repository"></a>Репозиторий тестовых случаев  
Чтобы просмотреть репозиторий тестовых случаев, щелкните **тестовые случаи...** в меню **Тестер** . Затем SSMA отображает диалоговое окно **репозиторий тестовых случаев** со списком сохраненных тестовых случаев на странице **тестовые случаи** .  
  
В сетке отображаются следующие сведения о каждом тестовом случае.  
  
-   Имя. имя тестового случая.  
  
-   Создано: Дата создания тестового случая.  
  
-   Изменено: Дата последнего изменения тестового случая.  
  
-   Описание: описания тестовых случаев.  
  
На странице тестовые случаи доступны следующие кнопки:  
  
-   Нажмите кнопку **Добавить** , чтобы запустить мастер тестовых случаев и создать новый тест.  
  
-   Нажмите кнопку **Удалить** , чтобы удалить выбранный тест из репозитория. При удалении тестового случая также удаляются все связанные результаты теста.  
  
-   Нажмите кнопку **изменить** , чтобы запустить мастер тестовых случаев и изменить выбранный тест.  
  
-   Нажмите кнопку **выполнить** , чтобы открыть диалоговое окно [Запуск тестовых случаев (OracleToSQL)](https://msdn.microsoft.com/fc208cdb-7373-4f6b-8f6c-cdff9d3dcd02) и выполнить выбранный тест.  
  
## <a name="test-results-repository"></a>Репозиторий результаты теста  
Репозиторий результаты теста можно просмотреть на **Результаты теста** странице репозитория в окне " **тестовые случаи** ". Откройте его, нажав кнопку **Результаты теста..** . в меню **Тестер** .  
  
На **Результаты теста** странице можно использовать два фильтра:  
  
-   Фильтр имени тестового случая: позволяет выбирать результаты теста по имени тестового случая. Значение **всех тестовых случаев** этого фильтра позволяет отображать результаты тестов для всех тестовых случаев.  
  
-   Дата выполнения тестового случая фильтр: фильтрует результаты теста по дате сохранения. Значение " **весь период** " этого фильтра позволяет отображать результаты теста для любой даты сохранения.  
  
В сетке отображаются следующие сведения о результатах теста.  
  
-   Имя: имя тестового случая.  
  
-   Сохранено: Дата сохранения в тестовых случаях.  
  
-   Результаты: Краткая сводка выполнения теста (всплывающая подсказка этой ячейки содержит полную сводку выполнения теста).  
  
На странице результатов теста доступны следующие кнопки:  
  
-   Нажмите кнопку **Просмотр** , чтобы открыть окно [Просмотр отчетов о тестовых случаях &#40;OracleToSQL&#41;](../../ssma/oracle/viewing-test-case-reports-oracletosql.md) текущего результата тестового случая.  
  
-   Нажмите кнопку " **Удалить** ", чтобы удалить выбранный результат теста  
  
## <a name="see-also"></a>См. также:  
[Выполнение тестовых случаев &#40;OracleToSQL&#41;](../../ssma/oracle/running-test-cases-oracletosql.md)  
[Тестирование перенесенных объектов базы данных &#40;OracleToSQL&#41;](../../ssma/oracle/testing-migrated-database-objects-oracletosql.md)  
  
