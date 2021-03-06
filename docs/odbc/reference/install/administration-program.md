---
title: Программа администрирования | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- administration program [ODBC]
- ODBC administrator [ODBC]
ms.assetid: a6c8248a-7a01-42e7-aaed-99dc94d50028
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9cb78dae32bb17598ee0e86c26e621be1b6362c6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68068557"
---
# <a name="administration-program"></a>Программа администрирования
> [!NOTE]  
>  Начиная с Windows XP и Windows Server 2003, ODBC входит в операционную систему Windows. Следует явно устанавливать ODBC только в более ранних версиях Windows.  
  
 Программа администрирования, администратор ODBC, входит в состав пакета SDK для Windows SDK и MDAC. Эта программа и может распространяться пользователями пакета SDK. Кроме того, разработчики могут создавать собственные программы для администрирования. Как правило, разработчики пишут собственные программы администрирования, только если они хотят полностью контролировать конфигурацию источника данных или настраивают источники данных непосредственно из приложения, которое выступает в роли программы администрирования. Например, программа электронной таблицы может позволить пользователям добавлять и использовать источники данных во время выполнения.  
  
 Программа администрирования сначала загружает библиотеку DLL установщика. Затем он вызывает функции в библиотеке DLL установщика для выполнения следующих задач:  
  
-   **Добавление, изменение или удаление источников данных в интерактивном режиме.** Программа администрирования может вызывать **склманажедатасаурцес**, **склкреатедатасаурце**или **SQLConfigDataSource**.  
  
     **Склманажедатасаурцес** отображает диалоговое окно, с помощью которого пользователь может добавлять, изменять или удалять источники данных, а также задавать параметры трассировки. Эта функция вызывается при вызове библиотеки DLL установщика непосредственно из панели управления. **Склкреатедатасаурце** отображает диалоговое окно, с помощью которого пользователь может добавлять только источники данных. **SQLConfigDataSource** передает вызов непосредственно в библиотеку DLL установки драйвера.  
  
     Во всех случаях библиотека DLL установщика вызывает **ConfigDSN** в библиотеке DLL установки драйвера для фактического добавления, изменения или удаления источника данных. Библиотека DLL установки драйвера может предложить пользователю получить дополнительные сведения.  
  
-   **Автоматическое добавление, изменение или удаление источников данных.** Программа администрирования вызывает **SQLConfigDataSource** в библиотеке DLL установщика и передает ей нулевой маркер окна, имя источника данных для добавления, изменения или удаления, а также список значений для реестра. Библиотека DLL установщика вызывает **ConfigDSN** в библиотеке DLL установки драйвера для фактического добавления, изменения или удаления источника данных.  
  
-   **Добавление, изменение или удаление источника данных по умолчанию.** Источник данных по умолчанию такой же, как и любой другой источник данных, за исключением того, что его имя — Default. Он добавляется, изменяется и удаляется так же, как и любой другой источник данных.
