---
title: Задача "Отправка почты" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sendmailtask.f1
helpviewer_keywords:
- mail [Integration Services]
- Send Mail task
- e-mail [Integration Services]
- messages [Integration Services]
- sending messages
ms.assetid: fe0b7cbc-fe8e-4fe2-95b4-2953efff5869
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3308899190aa63ebb9be93c4c9af15d5e0f94600
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62830398"
---
# <a name="send-mail-task"></a>Задача «Отправка почты»
  Задача «Отправка почты» производит отправку сообщения электронной почты. Эта задача позволяет пакету отправлять сообщения при успешном или неуспешном завершении задач в рабочем процессе пакета либо в ответ на события, инициируемые при выполнении пакета. Например, задача может уведомить администратора базы данных об успешном или неуспешном завершении задачи резервного копирования базы данных.  
  
 Задачу «Отправка почты» можно настроить следующими способами:  
  
-   Укажите текст сообщения электронной почты.  
  
-   Укажите строку темы сообщения электронной почты.  
  
-   Установите уровень приоритета сообщения. Задача поддерживает три уровня приоритета: обычный, низкий и высокий.  
  
-   Укажите получателей в строках «Кому», «Копия» и «Резервная копия». Если указываются несколько получателей, они должны быть разделены точками с запятой.  
  
    > [!NOTE]  
    >  Строки «Кому», «Копия» и «СК» ограничены длиной в 256 символов в соответствии со стандартами Интернета.  
  
-   Добавьте вложения. Если указываются несколько вложений, они должны быть разделены вертикальной чертой (|).  
  
    > [!NOTE]  
    >  Если файл вложения на момент выполнения пакета отсутствует, произойдет ошибка.  
  
-   Укажите используемый диспетчер соединений SMTP.  
  
    > [!IMPORTANT]  
    >  Диспетчер SMTP-соединений поддерживает только анонимную проверку подлинности и проверку подлинности Windows. Обычная проверка подлинности не поддерживается.  
  
 В качестве текста сообщения может быть указана строка, соединение с файлом, содержащим текст, либо имя переменной, в которой содержится текст. Подключение к файлу производится задачей при помощи диспетчера подключения файлов. Дополнительные сведения см. в статье [Flat File Connection Manager](../connection-manager/file-connection-manager.md).  
  
 Задача производит подключение к почтовому серверу при помощи диспетчера соединений SMTP. Дополнительные сведения см. в статье [SMTP Connection Manager](../connection-manager/smtp-connection-manager.md).  
  
## <a name="custom-logging-messages-available-on-the-send-mail-task"></a>Пользовательские сообщения для ведения журнала, доступные в задаче «Отправка почты»  
 В следующей таблице перечислены пользовательские записи в журнале для задачи «Отправка почты». Дополнительные сведения см. в разделах [Ведение журналов в службах Integration Services (SSIS)](../performance/integration-services-ssis-logging.md) и [Пользовательские сообщения для ведения журнала](../custom-messages-for-logging.md).  
  
|Запись журнала|Описание|  
|---------------|-----------------|  
|`SendMailTaskBegin`|Указывает, что задача приступила к отправке сообщения электронной почты.|  
|`SendMailTaskEnd`|Указывает, что задача завершила отправку сообщения электронной почты.|  
|`SendMailTaskInfo`|Выводит описательные сведения об этой задаче.|  
  
## <a name="configuring-the-send-mail-task"></a>Настройка задачи «Отправка почты»  
 Значения свойств можно задавать с помощью конструктора [!INCLUDE[ssIS](../../includes/ssis-md.md)] или программными средствами.  
  
 Дополнительные сведения о свойствах, которые можно задать в конструкторе служб [!INCLUDE[ssIS](../../includes/ssis-md.md)] , см. в следующих разделах.  
  
-   [Редактор задачи «Отправка почты» &#40;страница «Общие»&#41;](../general-page-of-integration-services-designers-options.md)  
  
-   [Редактор задачи "Отправка почты" &#40;страницу почты&#41;](../send-mail-task-editor-mail-page.md)  
  
-   [Страница «Выражения»](../expressions/expressions-page.md)  
  
 Сведения о задании этих свойств программными средствами см. в следующем разделе:  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.SendMailTask.SendMailTask>  
  
## <a name="related-tasks"></a>Связанные задачи  
 Дополнительные сведения о настройке свойств этих свойств в конструкторе [!INCLUDE[ssIS](../../includes/ssis-md.md)] см. в разделе [Задание свойств задач или контейнеров](../set-the-properties-of-a-task-or-container.md).  
  
## <a name="related-content"></a>См. также  
  
-   Техническая статья [How to send email with delivery notification in C#](https://go.microsoft.com/fwlink/?LinkId=237625)на сайте shareourideas.com  
  
## <a name="see-also"></a>См. также:  
 [Задачи Integration Services](integration-services-tasks.md)   
 [Поток управления](control-flow.md)  
  
  
