---
title: Редактор преобразования "Уточняющий запрос" (страница "соединение") | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.lookuptransformation.referencetable.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: e90d6b69-5a26-43c5-8433-5c3c9588e08c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7985f713093e839d258a0c9b80bb5d4e6e58f37f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66057950"
---
# <a name="lookup-transformation-editor-connection-page"></a>Редактор преобразования «Уточняющий запрос» (страница «Соединение»)
  Используйте страницу **Соединение** диалогового окна **Редактор преобразования «Уточняющий запрос»** для выбора диспетчера соединения. При выборе диспетчера соединений OLE DB также выбирается и запрос, таблица или представление для формирования эталонного набора данных.  
  
 Дополнительные сведения о преобразовании «Уточняющий запрос» см. в разделе [Lookup Transformation](data-flow/transformations/lookup-transformation.md).  
  
## <a name="options"></a>Параметры  
 При выборе пунктов **Полное кэширование** и **Диспетчер соединений с кэшем** на странице «Общие» диалогового окна **Редактор преобразования «Уточняющий запрос»** доступны следующие параметры.  
  
 **Диспетчер соединений с кэшем**  
 Выберите из списка существующий диспетчер соединений с кэшем или создайте новое соединение, нажав кнопку **Создать**.  
  
 **Создать**  
 Создайте новое соединение с помощью диалогового окна **Редактор диспетчера соединений с кэшем** .  
  
 При выборе пунктов **Полное кэширование**, **Частичное кэширование**или **Без кэширования**, а также **Диспетчер соединений OLE DB**на странице «Общие» диалогового окна **Редактор преобразования «Уточняющий запрос»** доступны следующие параметры.  
  
 **Диспетчер подключений OLE DB**  
 Выберите существующий диспетчер соединений OLE DB из списка или создайте новое подключение, выбрав пункт **Создать**.  
  
 **Создать**  
 Создайте новое соединение с помощью диалогового окна **Настройка диспетчера соединений OLE DB** .  
  
 **Использовать таблицу или представление**  
 Выберите существующую таблицу или представление из списка или создайте новую таблицу, выбрав пункт **Создать**.  
  
> [!NOTE]  
>  Если на странице **Дополнительно****Редактора преобразования «Уточняющий запрос»** задать инструкцию SQL, то эта инструкция принудительно переопределит имя таблицы, выбранное там. Дополнительные сведения см. в разделе [Редактор преобразования "Уточняющий запрос" (страница "Дополнительно")](../../2014/integration-services/lookup-transformation-editor-advanced-page.md).  
  
 **Создать**  
 Создайте новую таблицу с помощью диалогового окна **Создание таблицы** .  
  
 **Использование результатов запроса SQL**  
 Выберите этот параметр для поиска существующего запроса, создания нового запроса, проверки синтаксиса запроса и просмотра результатов запроса.  
  
 **Построить запрос**  
 Создайте для выполнения инструкцию Transact-SQL с помощью **Построителя запросов**, графического средства, используемого для создания запросов с помощью просмотра данных.  
  
 **Обзор**  
 Используйте этот параметр для просмотра ранее созданного запроса, сохраненного в файле.  
  
 **Анализ запроса**  
 Проверка синтаксиса запроса.  
  
 **Предварительный просмотр**  
 Просмотрите предварительные результаты, используя диалоговое окно **Предварительный просмотр результатов запроса** . В окне предварительного просмотра может отображаться до 200 строк.  
  
## <a name="external-resources"></a>Внешние ресурсы  
 Запись в блоге [Режимы кэша уточняющих запросов](https://go.microsoft.com/fwlink/?LinkId=219518) на сайте blogs.msdn.com  
  
## <a name="see-also"></a>См. также:  
 [Редактор преобразования "Уточняющий запрос" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор преобразования «Уточняющий запрос» &#40;столбцов&#41;](../../2014/integration-services/lookup-transformation-editor-columns-page.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница "Дополнительно"&#41;](../../2014/integration-services/lookup-transformation-editor-advanced-page.md)   
 [Редактор преобразования "Уточняющий запрос" &#40;страница "вывод ошибок"&#41;](../../2014/integration-services/lookup-transformation-editor-error-output-page.md)   
 [преобразование «Нечеткий уточняющий запрос»](data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  
