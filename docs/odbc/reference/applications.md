---
title: Приложения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- off-the-shelf applications [ODBC]
- ODBC architecture [ODBC], applications
- shrink-wrapped applications [ODBC]
- application development [ODBC], types
- custom applications [ODBC]
- virtual applications [ODBC]
- generic applications [ODBC]
ms.assetid: 39d6461f-0d24-4b7d-a723-843ade15ad73
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f15b5e8eb6eb7c63ab771030f0c31e8c9ff92724
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135675"
---
# <a name="applications"></a>Приложения
*Приложение* — это программа, которая вызывает API ODBC для доступа к данным. Хотя многие типы приложений возможны, большинство из них делятся на три категории, которые используются в качестве примеров в рамках этого руководством.  
  
-   **Универсальные приложения** Они также называются приложениями с оболочкой сжатия или готовыми приложениями. Универсальные приложения предназначены для работы с различными СУБД. Примеры включают в себя электронную таблицу или пакет статистики, который использует ODBC для импорта данных для дальнейшего анализа и текстовый процессор, использующий ODBC для получения списка рассылки из базы данных.  
  
     Важная Подкатегория универсальных приложений — это среды разработки приложений, такие как PowerBuilder или Microsoft® Visual Basic®. Несмотря на то, что приложения, созданные с этими средами, скорее всего, будут работать только с одной СУБД, сама среда должна работать с несколькими СУБД.  
  
     Все универсальные приложения часто являются взаимодействующими в СУБД и должны использовать ODBC в относительно универсальном способе. Дополнительные сведения о взаимодействии см. [в разделе Выбор уровня взаимодействия](../../odbc/reference/develop-app/choosing-a-level-of-interoperability.md).  
  
-   **Вертикальные приложения** Вертикальные приложения выполняют задачи одного типа, например ввод заказов или отслеживание производственных данных, и работают со схемой базы данных, управляемой разработчиком приложения. Для конкретного клиента приложение работает с одной СУБД. Например, небольшой бизнес может использовать приложение с dBase, в то время как большой бизнес может использовать его с Oracle.  
  
     Приложение использует ODBC таким образом, что приложение не привязано ни к одной СУБД, хотя оно может быть привязано к ограниченному количеству СУБД, которые предоставляют аналогичные функциональные возможности. Таким образом, разработчик приложения может продавать приложение независимо от СУБД. Вертикальные приложения являются взаимодействующими при разработке, но иногда изменяются для включения нонинтероперабле кода после выбора клиентом СУБД.  
  
-   **Пользовательские приложения** Пользовательские приложения используются для выполнения определенной задачи в одной компании. Например, приложение в большой компании может собирать данные о продажах из нескольких подразделений (каждая из которых использует другую СУБД) и создавать один отчет. Используется ODBC, поскольку он является общим интерфейсом и позволяет программистам изучать несколько интерфейсов. Как правило, такие приложения не поддерживают взаимодействие и записываются в определенные СУБД и драйверы.  
  
 Некоторые задачи являются общими для всех приложений, независимо от того, как они используют ODBC. Вместе они в основном определяют поток любого приложения ODBC. Задачи:  
  
-   Выбор источника данных и подключение к нему.  
  
-   Отправка инструкции SQL для выполнения.  
  
-   Получение результатов (если они есть).  
  
-   Обработка ошибок.  
  
-   Фиксация или откат транзакции, включающей в себя инструкцию SQL.  
  
-   Отключение от источника данных.  
  
 Так как большая часть работы по доступу к данным выполняется с помощью SQL, основная задача, для которой приложения используют ODBC, — Отправка инструкций SQL и получение результатов (при их наличии), созданных этими инструкциями. Другие задачи, в которых приложения используют ODBC, включают определение возможностей драйвера и просмотр каталога базы данных.
