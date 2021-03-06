---
title: Внедренный SQL | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL [ODBC], embedded SQL
- sending SQL statements to DBMS [ODBC]
- SQL statements [ODBC], embedded SQL
- ODBC [ODBC], SQL
- embedded SQL [ODBC]
ms.assetid: 8eee3527-f225-4aa2-bd18-a16bd3ab0fb7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6a7fa2b3105aedee6cb054c5d5dfa76f3c430f35
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67915427"
---
# <a name="embedded-sql"></a>Embedded SQL
Первым методом отправки инструкций SQL в СУБД является внедренный SQL. Поскольку в SQL не используются переменные и инструкции управления потоком, они часто используются в качестве подязыка базы данных, который можно добавить в программу, написанную на традиционном языке программирования, например C или COBOL. Это центральная идея внедренного SQL: помещение инструкций SQL в программу, написанную на языке программирования узла. Вкратце, для внедрения инструкций SQL на основном языке используются следующие методы:  
  
-   Внедренные инструкции SQL обрабатываются специальным предкомпилятором SQL. Все инструкции SQL начинаются с символа начала и заканчиваются признаком конца, который помечает инструкцию SQL для предварительной компиляции. Введение и признак конца различаются в зависимости от языка узла. Например, знакомым является «EXEC SQL» в C и «&SQL (» в МУМПС, а Терминатор — точкой с запятой (;) в C и правой круглой скобке в МУМПС.  
  
-   Переменные из программы приложения, называемые переменными узла, могут использоваться в внедренных инструкциях SQL везде, где разрешены константы. Они могут использоваться на входе для адаптации инструкции SQL к определенной ситуации и на выходе для получения результатов запроса.  
  
-   Запросы, возвращающие одну строку данных, обрабатываются с помощью одноэлементной инструкции SELECT. Эта инструкция задает как запрос, так и переменные узла, в которых возвращаются данные.  
  
-   Запросы, возвращающие несколько строк данных, обрабатываются с помощью курсоров. Курсор отслеживает текущую строку в результирующем наборе. Инструкция DECLARE CURSOR определяет запрос, инструкция OPEN начинает обработку запроса, инструкция FETCH получает последовательные строки данных, а Инструкция CLOSE завершает обработку запросов.  
  
-   При открытом курсоре можно использовать инструкции позиционированного обновления и позиционированного удаления, чтобы обновить или удалить строку, выбранную в данный момент курсором.  
  
 Этот раздел содержит следующие подразделы.  
  
-   [Пример Embedded SQL](../../odbc/reference/embedded-sql-example.md)  
  
-   [Компиляция программы на Embedded SQL](../../odbc/reference/compiling-an-embedded-sql-program.md)  
  
-   [Статический SQL](../../odbc/reference/static-sql.md)  
  
-   [Динамический SQL](../../odbc/reference/dynamic-sql.md)
