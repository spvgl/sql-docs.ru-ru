---
title: Установка Reporting Services и службы IIS параллельно (собственный режим служб SSRS) | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- deploying [Reporting Services], IIS
ms.assetid: 9b651fa5-f582-4f18-a77d-0dde95d9d211
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 514774acc7255f2f499bfe7fdd6e731944ab67fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67285044"
---
# <a name="install-reporting-services-and-internet-information-services-side-by-side-ssrs-native-mode"></a>Параллельная установка служб Reporting Services и служб IIS (собственный режим SSRS)
  Можно установить и запустить [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] службы (SSRS) и службы IIS (IIS) на одном компьютере. От используемой версии служб IIS будет зависеть, какие возникнут проблемы совместимости.  
  
||  
|-|  
|[!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Собственный режим|  
  
|Версия служб IIS|Проблемы|Description|  
|-----------------|------------|-----------------|  
|IIS 6.0, 7.0, 8.0, 8.5|Запросы, предназначенные для одного приложения, принимаются другим приложением.<br /><br /> Компонент HTTP.SYS предписывает правила приоритета для резервирования URL-адресов. Запросы, передаваемые в приложения, которые имеют одинаковое имя виртуального каталога и совместно отслеживают запросы, поступающие через порт 80, могут не достичь намеченной цели, если применяемое резервирование URL-адресов слабее резервирования URL-адресов другого приложения.|При определенных условиях зарегистрированная конечная точка, URL-адрес которой предшествует URL-адресу другой конечной точки в схеме резервирования URL-адресов, может получать HTTP-запросы, предназначенные для другого приложения.<br /><br /> Использование уникальных имен виртуальных каталогов для веб-службы сервера отчетов и диспетчера отчетов может помочь избежать этого конфликта.<br /><br /> Подробные сведения об этом сценарии приведены в этом разделе.|  
  
## <a name="precedence-rules-for-url-reservations"></a>Правила приоритета для резервирования URL-адресов  
 Прежде чем приступать к устранению проблем совместимости служб IIS и [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], необходимо понять правила приоритета резервирования URL-адресов. Правила приоритета можно обобщить следующим образом: резервирование URL-адресов, более явно определяющих значения, становится первым в очереди на получение запросов по соответствующим URL-адресам.  
  
-   Резервирование URL-адресов, указывающее виртуальный каталог, является более явным по сравнению с тем, в котором виртуальный каталог не задан.  
  
-   Резервирование URL-адресов, в котором указан единственный адрес (в виде IP-адреса, полного доменного имени, сетевого имени компьютера или имени узла), является более явным по сравнению с резервированием, в котором указан шаблон.  
  
-   Резервирование URL-адресов, в котором указан сильный шаблон, является более явным по отношению к резервированию со слабым шаблоном.  
  
 В следующих примерах приведен ряд резервирований URL-адресов, начиная от наиболее явного и заканчивая наименее явным:  
  
|Пример|Запрос|  
|-------------|-------------|  
|http:\//123.234.345.456:80/отчеты|Получает все запросы, отправленные на http:\//123.234.345.456/reports или http://\<ComputerName>/Reports, если служба доменных имен может разрешить IP-адрес в это имя узла.|  
|http://+:80/reports|Получает любые запросы, отправленные любому IP-адресу или имени узла, являющимся допустимыми для этого компьютера, при условии, что URL-адрес содержит имя виртуального каталога reports.|  
|http:\//123.234.345.456:80|Получает любой запрос, указывающий HTTP\/:/123.234.345.456 или\<http://ComputerName>, если служба доменных имен может разрешить IP-адрес в это имя узла.|  
|http://+:80|Получает запросы, которые еще не получены другими приложениями, применительно к любым конечным точкам приложений, сопоставленным со значением **Все назначенные**.|  
|http://*:80|Получает запросы, которые еще не получены другими приложениями, применительно к любым конечным точкам приложений, сопоставленным со значением **Все неназначенные**.|  
  
 Одним из признаков конфликта портов является следующее сообщение об ошибке: "System.IO.FileLoadException. Процесс не может получить доступ к файлу, так как этот файл занят другим процессом. (Исключение в HRESULT: 0x80070020)".  
  
## <a name="url-reservations-for-iis-60-70-80-85-with-includesssql14includessssql14-mdmd-reporting-services"></a>Резервирования URL-адресов для служб IIS 6.0, 7.0, 8.0 и 8.5 со службами [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] Reporting Services  
 Изучение правил приоритета, приведенных в предыдущем разделе, позволяет разобраться, как резервирования URL-адресов, определенные для служб Reporting Services и IIS, поддерживают совместимость. Службы Reporting Services получают запросы, в которых явно указаны имена виртуальных каталогов для их приложений; службы IIS получают все остальные запросы, которые могут затем быть направлены приложениям, запущенным в рамках модели процесса IIS.  
  
|Приложение|Резервирование URL-адресов|Description|Прием запроса|  
|-----------------|---------------------|-----------------|---------------------|  
|Сервер отчетов|http://+:80/ReportServer|Сильный шаблон для доступа к порту 80, с указанием виртуального каталога сервера отчетов.|Получает все запросы на порт 80, в которых указан виртуальный каталог сервера отчетов. Веб-служба сервера отчетов получает все запросы, отправленные по адресу http://\<имя_компьютера>/reportserver.|  
|Диспетчер отчетов|http://+:80/Reports|Сильный шаблон для доступа к порту 80, с указанием виртуального каталога Reports.|Получает все запросы на порт 80, в которых указан виртуальный каталог reports. Диспетчер отчетов получает все запросы к http://\<ComputerName>/Reports.|  
|IIS|http://*:80/|Слабый шаблон для доступа к порту 80.|Получает любые оставшиеся запросы на порт 80, которые не получены другим приложением.|  
  
## <a name="side-by-side-deployments-of-includesscurrentincludessscurrent-mdmd-and-sql-server-2005-reporting-services-on-iis-60-70-80-85"></a>Параллельное развертывание [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и служб SQL Server 2005 Reporting Services на службы IIS 6.0, 7.0, 8.0, 8.5  
 Если веб-сайты IIS имеют имена виртуальных каталогов, идентичные используемым в службах Reporting Services, возникают проблемы функциональной совместимости служб IIS и служб Reporting Services. Например, предположим, что имеется следующая конфигурация.  
  
-   Веб-сайт в службах IIS, который назначен на порт 80 и виртуальный каталог с именем Reports.  
  
-   Экземпляр [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] сервера отчетов, установленный в конфигурации по умолчанию, в котором резервирование URL-адресов также указывает порт 80, а диспетчер отчетов приложение также использует "Reports" для имени виртуального каталога.  
  
 Учитывая эту конфигурацию, запрос, отправленный в http://\<ComputerName>:80/Reports, будет получен диспетчер отчетов. Приложение, доступ к которому предоставляется с помощью виртуального каталога Reports в службах IIS, после установки экземпляра сервера отчетов [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] больше не будет получать запросы.  
  
 При работе развернутых параллельно старой и новой версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], по всей вероятности будут обнаруживаться только что описанные проблемы маршрутизации. Это связано с тем, что во всех версиях служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] в качестве имен виртуальных каталогов для приложений сервера отчетов и диспетчера отчетов используется ReportServer и Reports, в результате чего повышается вероятность наличия виртуальных каталогов reports и reportserver в службах IIS.  
  
 Чтобы обеспечить получение всеми приложениями направленных к ним запросов, руководствуйтесь следующими рекомендациями.  
  
-   Для установок служб Reporting Services используйте имена виртуальных каталогов, которые не используются ни одним веб-сайтом IIS на том же порте, что и в службе Reporting Services. Если возникает конфликт, установите службы Reporting Services в режиме «только файлы» (с помощью программы установки, но не настраивая параметры сервера в мастере установки), чтобы иметь возможность настроить виртуальные каталоги после завершения установки. Одним из признаков конфликта конфигурации является следующее сообщение об ошибке: "System.IO.FileLoadException. Процесс не может получить доступ к файлу, так как этот файл занят другим процессом. (Исключение в HRESULT: 0x80070020)".  
  
-   Для установок, настраиваемых вручную, применяйте предусмотренные по умолчанию соглашения об именах в настраиваемых URL-адресах. Если службы [!INCLUDE[ssRSCurrent](../../includes/ssrscurrent-md.md)] устанавливаются в качестве именованного экземпляра, включите имя экземпляра при создании виртуального каталога.  
  
## <a name="see-also"></a>См. также:  
 [Настройка URL-адресов сервера отчетов (диспетчер конфигурации служб SSRS)](configure-report-server-urls-ssrs-configuration-manager.md)   
 [Настройка URL-адреса (диспетчер конфигурации служб SSRS)](configure-a-url-ssrs-configuration-manager.md)   
 [Установка сервера отчетов служб Reporting Services в собственном режиме](install-reporting-services-native-mode-report-server.md)  
  
  
