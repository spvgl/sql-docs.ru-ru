---
title: 'Счетчики производительности для объектов производительности ReportServer: Service и ReportServerSharePoint: Service | Документация Майкрософт'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Report Server service, performance counters
ms.assetid: 2bcacab2-3a4f-4aae-b123-19d756b9b9ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 001e62869146a7090fe4598650c763a690809cfb
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66103641"
---
# <a name="performance-counters-for-the-reportserverservice--and-reportserversharepointservice-performance-objects"></a>Счетчики производительности для объектов производительности ReportServer:Service и ReportServerSharePoint:Service
  В данном разделе описаны счетчики производительности для следующих объектов производительности [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] :  
  
-   `ReportServer:Service`  
  
-   `ReportServerSharePoint:Service`  
  
> [!NOTE]  
>  Эти объекты производительности служат для наблюдения за событиями на локальном сервере отчетов. При запуске сервера отчетов в масштабном развертывании счетчики относятся к текущему серверу, а не к масштабному развертыванию в целом.  
  
 Объекты производительности доступны в системном мониторе Windows (**Perfmon.exe**). Дополнительные сведения см. в документации по Windows. [Профилирование среды выполнения](https://msdn.microsoft.com/library/w4bz2147.aspx) (https://msdn.microsoft.com/library/w4bz2147.aspx).  
  
 В этом разделе:  
  
-   [Счетчики производительности ReportServer: Service (сервер отчетов в собственном режиме)](#bkmk_ReportServer)  
  
-   [ReportServerSharePoint: Service (сервер отчетов в режиме SharePoint)](#bkmk_ReportServerSharePoint)  
  
-   [Использование командлетов PowerShell для возврата списков](#bkmk_powershell)  
  
 [!INCLUDE[applies](../../includes/applies-md.md)][!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Режим интеграции с SharePoint | Собственный режим.  
  
##  <a name="bkmk_ReportServer"></a>Счетчики производительности ReportServer: Service (сервер отчетов в собственном режиме)  
 Объект производительности `ReportServer:Service` включает коллекцию счетчиков для отслеживания связанных с HTTP и памятью событий для экземпляра сервера отчетов. Этот объект производительности отображается однократно для каждого экземпляра служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] на компьютере; счетчики объекта производительности можно добавлять или удалять для каждого экземпляра. Счетчики для экземпляра по умолчанию отображаются в формате `ReportServer:Service`. Счетчики для именованных экземпляров отображаются в `ReportServer$<`формате *instance_name*`>:Service`.  
  
 Объект `ReportServer:Service` производительности был впервые использован в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]и предоставляет подмножество счетчиков, включенных в службы IIS (IIS) и [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] в предыдущих версиях. [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Эти новые счетчики являются уникальными для служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]. Они отслеживают связанные с HTTP события для сервера отчетов, такие как запросы, соединения и попытки входа. Кроме того, этот объект производительности включает счетчики для отслеживания событий управления памятью.  
  
 В следующей таблице перечислены счетчики, включенные в объект производительности `ReportServer:Service`.  
  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий сценарий Windows PowerShell вернет список счетчиков производительности для CounterSetName  
  
```  
(get-counter -listset "ReportServer:Service").paths  
```  
  
|Счетчик|Description|  
|-------------|-----------------|  
|`Active connections`|Количество активных в текущий момент соединений на сервере.|  
|`Bytes Received Total`|Число байт, полученных сервером. Этот счетчик ведет подсчет общего приблизительного числа байтов, полученных как диспетчером отчетов, так и сервером отчетов.|  
|`Bytes Received/sec`|Число байтов, полученных сервером за одну секунду. Этот счетчик обновляется только при завершении передачи. Это означает, что значение счетчика остается равным 0, а затем значение растет после завершения передачи.|  
|`Bytes Sent Total`|Число байтов, отправленных сервером. Этот счетчик ведет подсчет общего приблизительного числа байтов, оправленных как диспетчером отчетов, так и сервером отчетов.|  
|`Bytes Sent/sec`|Число байтов, отправленных сервером за секунду. Этот счетчик обновляется только при завершении передачи. Это означает, что значение счетчика остается равным 0, а затем значение растет после завершения передачи.|  
|`Errors Total`|Общее число ошибок, возникших во время выполнения HTTP-запросов. Эти ошибки включают 400-е и 500-е коды состояния HTTP.|  
|`Errors/sec`|Общее число ошибок, возникших во время выполнения HTTP-запросов за одну секунду. Эти ошибки включают 400-е и 500-е коды состояния HTTP.|  
|`Logon Attempts Total`|Число попыток входа, выполненных из типов проверки подлинности RSWindows. Типы проверок подлинности RSWindows включают RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos и RSWindowsBasic. Нулевое значение (0) отвечает за нестандартную проверку подлинности.|  
|`Logon Attempts/sec`|Число попыток входа.|  
|`Logon Successes Total`|Число успешных входов для типов проверки подлинности RSWindows. Типы проверок подлинности RSWindows включают RSWindowsNegotiate, RSWindowsNTLM, RSWindowsKerberos и RSWindowsBasic. Нулевое значение (0) отвечает за нестандартную проверку подлинности.|  
|`Logon Successes/sec`|Число успешных входов.|  
|`Memory Pressure State`|Одно из следующих чисел от 1 до 5, указывающее текущее состояние памяти на сервере.<br /><br /> 1: нет нагрузки<br /><br /> 2: низкая нагрузка<br /><br /> 3: средняя нагрузка<br /><br /> 4: высокая нагрузка<br /><br /> 5: чрезмерная нагрузка|  
|`Memory Shrink Amount`|Число байтов, запрошенных сервером для сжатия используемой памяти.|  
|`Memory Shrink Notifications/sec`|Число уведомлений, сформированных сервером в последнюю секунду для сжатия используемой памяти. Это число указывает, как часто сервер испытывает недостаток памяти.|  
|`Requests Disconnected`|Число отсоединений запросов, возникших из-за сбоя в канале связи.|  
|`Requests Executing`|Количество запросов, обрабатываемых в настоящий момент.|  
|`Requests Not Authorized`|Число запросов, завершенных с кодом состояния HTTP 401.|  
|`Requests Rejected`|Общее число запросов, не обработанных из-за недостаточных ресурсов сервера. Этот счетчик отражает число запросов, возвращенных с кодом состояния HTTP 503, указывающим на то, что сервер слишком загружен.|  
|`Requests Total`|Общее число запросов, полученных службой сервера отчетов с момента запуска. Этот счетчик ведет подсчет запросов, отправленных диспетчеру отчетов, а также запросов, отправленных диспетчером отчетов серверу отчетов.|  
|`Requests/sec`|Количество обрабатываемых за секунду запросов. Это значение отражает текущую пропускную способность приложения.|  
|`Tasks Queued`|Число задач, ожидающих доступности потока для обработки. Каждый запрос, выполненный к серверу отчетов, соответствует одной или нескольким задачам. Этот счетчик представляет только число задач, готовых к обработке; он не включает число выполняющихся в настоящее время задач.|  
  
##  <a name="bkmk_ReportServerSharePoint"></a>ReportServerSharePoint: Service (сервер отчетов в режиме SharePoint)  
 Объект `ReportServerSharePoint:Service` производительности был добавлен в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].  
  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий сценарий Windows PowerShell вернет список счетчиков производительности для CounterSetName  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
|Счетчик|  
|-------------|  
|`Memory Pressure State`|  
|`Memory Shrink Amount`|  
|`Memory Shrink Notifications/Sec`|  
  
##  <a name="bkmk_powershell"></a>Использование командлетов PowerShell для возврата списков  
 ![Содержимое, связанное с PowerShell](../media/rs-powershellicon.jpg "Содержимое, связанное с PowerShell") Следующий сценарий Windows PowerShell вернет список счетчиков производительности для CounterSetName "ReportServerSharePoint: Service":  
  
```  
(get-counter -listset "ReportServerSharePoint:Service").paths  
```  
  
## <a name="see-also"></a>См. также:  
 [Наблюдение за производительностью сервера отчетов](monitoring-report-server-performance.md)   
 [Счетчики производительности для объектов производительности веб-службы MSRS 2014 и службы Windows MSRS 2014 &#40;основном режиме&#41;](../report-server/performance-counters-msrs-2011-web-service-performance-objects.md)   
 [Счетчики производительности для объектов производительности "веб-служба MSRS 2014" в режиме интеграции с SharePoint и MSRS 2014 режим службы Windows в режиме интеграции &#40;SharePoint&#41;].. /performance-counters-msrs-2011-sharepoint-mode-performance-objects.md)  
  
  
