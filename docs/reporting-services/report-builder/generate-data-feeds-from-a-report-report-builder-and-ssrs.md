---
title: Формирование веб-каналов данных из отчета (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-builder
ms.topic: conceptual
ms.assetid: e68baae2-9f2a-4f13-9179-9ac7f29111c5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: a94df8959adf40edfe2e78c7c281dd5d57f90266
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "65580763"
---
# <a name="generate-data-feeds-from-a-report-report-builder-and-ssrs"></a>Формирование веб-каналов данных из отчета (построитель отчетов и службы SSRS)

Можно формировать Atom-совместимые веб-каналы данных из отчетов с разбиением на страницы, а затем применять эти веб-каналы в приложениях, например Power Pivot или Power BI, которые могут использовать веб-каналы данных.  
  
 Модуль Atom подготовки отчетов служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] формирует сервисный документ канала Atom, в котором перечислены потоки данных, доступные в отчете. Этот документ содержит сведения по меньшей мере об одном потоке данных для каждой области данных отчета. В зависимости от типа области данных и самих данных, которые отображает эта область, службы [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] могут сформировать из нее несколько потоков данных.  
  
 Сервисный документ Atom содержит для каждого потока данных уникальный идентификатор, который упоминается в URL-адресе для доступа к содержимому потока данных.  
  
 Дополнительные сведения см. в разделе [Формирование веб-каналов данных из отчетов (построитель отчетов и службы SSRS)](../../reporting-services/report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-generate-an-atom-service-document"></a>Формирование сервисного документа Atom  
  
1.  на веб-портале [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] перейдите к отчету, для которого требуется создать веб-каналы данных.  
  
2.  Щелкните отчет.  
  
     Отчет выполняется.  
  
3.  На панели инструментов нажмите кнопку **Экспорт в поток данных** .  
  
     Появится запрос, что нужно сделать с файлом: сохранить или открыть документ Atom, содержащий поток данных.  
  
4.  Щелкните **Сохранить** , чтобы сохранить документ в файловой системе, или **Открыть** , чтобы просмотреть содержимое документа перед сохранением. **По умолчанию документ открывается в браузере.**  
  
5.  Укажите расположение для сохранения документа.  
  
6.  При необходимости имя файла можно изменить.  
  
    > [!NOTE]  
    >  По умолчанию имя документа совпадает с именем отчета.  
  
7.  Убедитесь, что документ имеет тип **ATOMSVC**, затем нажмите кнопку **Сохранить**.  
  
8.  При необходимости откройте файл ATOMSVC в браузере либо в текстовом или XML-редакторе.  
  
### <a name="to-view-an-atom-compliant-data-feed"></a>Просмотр Atom-совместимого потока данных  
  
1.  Если сервисный документ Atom еще не открыт, найдите и откройте его в браузере, например в Internet Explorer.  
  
2.  Скопируйте в браузер URL-адрес потока данных, который требуется просмотреть из сервисного документа Atom.  
  
     Формат URL-адреса будет следующим:  
  
     `https://<server name>/ReportServer?%2f<ReportName>rs%3aCommand=Render&rs%3aFormat=ATOM&rc%3aDataFeed=<Identifier>`  
  
3.  Нажмите клавишу ВВОД.  
  
     Появится запрос, что нужно сделать с файлом: сохранить или открыть документ Atom, содержащий поток данных.  
  
4.  Щелкните **Сохранить** , чтобы сохранить документ в файловой системе, или **Открыть** , чтобы просмотреть поток данных перед сохранением.  
  
5.  Укажите расположение для сохранения документа.  
  
6.  При необходимости имя файла можно изменить.  
  
    > [!NOTE]  
    >  По умолчанию имя документа совпадает с именем отчета. Если в сервисном документе Atom есть несколько потоков, все они используют по умолчанию одно и то же имя — имя отчета. Чтобы различать их, дайте им значимые имена.  
  
7.  Убедитесь, что документ имеет тип **ATOM**, затем нажмите кнопку **Сохранить**.  
  
8.  При необходимости откройте файл ATOM в браузере либо в текстовом или XML-редакторе.  

## <a name="next-steps"></a>Дальнейшие действия

[Экспорт отчетов](../../reporting-services/report-builder/export-reports-report-builder-and-ssrs.md)  

Остались вопросы? [Посетите форум служб Reporting Services](https://go.microsoft.com/fwlink/?LinkId=620231).
