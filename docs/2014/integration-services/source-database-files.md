---
title: Файлы базы данных источника | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: ac7d4b590fa5c3efccd16deebf3bafab83b74f6b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055536"
---
# <a name="source-database-files"></a>Файлы базы данных-источника
  Диалоговое окно **Файлы базы данных-источника** используется для просмотра имен файлов базы данных и их размещения на исходном сервере, а также для указания общей сетевой папки в задаче «Передача базы данных». Дополнительные сведения об этой задаче см. в разделе [Задача "Передача базы данных"](control-flow/transfer-database-task.md).  
  
 Чтобы наполнить диалоговое окно именами файлов базы данных и ресурсов исходного сервера, сначала укажите параметры **SourceConnection** (Подключение к источнику) и **SourceDatabaseName** (Имя базы данных-источника) на странице **Базы данных** диалогового окна **Редактор задачи «Передача базы данных»** .  
  
## <a name="options"></a>Параметры  
 **Исходный файл**  
 Имена файлов базы данных на исходном сервере, которые будут перенесены. **Исходный файл** доступен только для чтения.  
  
 **Исходная папка**  
 Папка на исходном сервере, в которой хранятся файлы базы данных, подлежащей переносу. **Исходная папка** доступна только для чтения.  
  
 **Общая сетевая папка**  
 Сетевая общая папка на исходном сервере, из которой будут перенесены файлы базы данных. Используйте **сетевую общую папку** при переносе базы данных в автономном режиме, указав **значение DatabaseOffline параметра** для **метода** на странице **базы данных** диалогового окна **Редактор задачи «перемещение базы данных** ».  
  
 Введите путь к общей сетевой папке или нажмите кнопку обзора **(...)**, чтобы найти эту папку.  
  
 При переносе базы данных в режиме вне сети файлы базы данных копируются в заданную параметром **Сетевая общая папка** папку на исходном сервере, прежде чем они будут перенесены на целевой сервер.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и сообщениям Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Редактор задачи "Перемещение базы данных" &#40;общие&#41;страницы](general-page-of-integration-services-designers-options.md)   
 [Редактор задачи "Перемещение базы данных" &#40;"базы данных"&#41;](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
