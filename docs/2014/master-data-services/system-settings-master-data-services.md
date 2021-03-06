---
title: Системные параметры (службы Master Data Services) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- Master Data Services, system settings
- system settings [Master Data Services]
ms.assetid: 83075cdf-f059-4646-8ba2-19be8202f130
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: a411290435a10e351c05e9dd1350bde597dbe449
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "65478819"
---
# <a name="system-settings-master-data-services"></a>Системные параметры (службы Master Data Services)
  Для всех веб-приложений и веб-служб, связанных с базой данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] , можно задавать системные настройки.  
  
 Многие из этих параметров можно изменить в [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] на странице **База данных** . Другие параметры можно настроить в таблице системных параметров (mdm.tblSystemSetting) в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
 Параметры можно разделить на следующие категории:  
  
-   [Общие параметры](#General)  
  
-   [Параметры управления версиями](#Versions)  
  
-   [Параметры промежуточного хранения](#Staging)  
  
-   [Параметры обозревателя](#Explorer)  
  
-   [Надстройка для параметров Excel](#xls)  
  
-   [Параметры бизнес-правил](#BusinessRules)  
  
-   [Параметры уведомлений](#Notifications)  
  
-   [Параметры безопасности](#Security)  
  
-   [Не используется](#NotUsed)  
  
##  <a name="General"></a>Общие параметры  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**Время ожидания подключения к базе данных**|**датабасеконнектионтимеаут**|Число секунд, которое база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] отводит на установление соединения. Если в течение этого времени соединение не установлено, оно отменяется и возвращается ошибка. Значение по умолчанию — **60** секунд (1 минута).|  
|**Время ожидания команды базы данных**|**датабасекоммандтимеаут**|Число секунд, которое база данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] отводит на выполнение команды. Если команда не завершается в течение указанного времени, то она отменяется и возвращается ошибка. Значение по умолчанию — **3600** секунд (60 минут).|  
|**Время ожидания веб-службы**|**ServerTimeOut**|Число секунд, которое ASP.NET отводит на выполнение запроса страницы [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Если запрос не выполняется в течение указанного периода времени, выполнение запроса отменяется и возвращается ошибка. Значение по умолчанию — **120000** секунд (2000 минут).|  
|**Время ожидания клиента**|**клиенттимеаут**|Период неактивности в секундах, по истечении которого [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] возвращается на домашнюю страницу. Значение по умолчанию — **300** секунд (5 минут).|  
|**Число строк в пакете**|**ровспербатч**|Число записей для извлечения в каждом пакете, возвращаемом веб-службой. Значение по умолчанию — **50**.|  
||**ApplicationName**|Текст, отображаемый в журналах событий. Значение по умолчанию — **MDM**.|  
||**ситетитле**|Текст, отображаемый в заголовке окна веб-браузера [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] . Значение по умолчанию — **Диспетчер основных данных**.|  
  
##  <a name="Versions"></a>Параметры управления версиями  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**Копировать только зафиксированные версии**|**копйонликоммиттедверсион**|В [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]определяет, могут ли пользователи копировать версии модели с состоянием **Зафиксирована**либо версии с произвольным состоянием. Значение по умолчанию — **Да** или **1**. Оно указывает, что пользователи могут копировать только версии в состоянии **Зафиксировано** . Чтобы разрешить пользователям копировать все версии, измените это значение на **Нет** или **2**.|  
  
 Дополнительные сведения см. в разделе [Версии (службы Master Data Services)](versions-master-data-services.md).  
  
##  <a name="Staging"></a>Параметры промежуточного хранения  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**Регистрировать все промежуточные транзакции**|**стагингтрансактионлоггинг**|Применимо только к SQL Server 2008 R2. Определяет, будет ли вестись запись в журнал транзакций при загрузке промежуточных данных в базу данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Значение по умолчанию — **Выключено** или **2**. Измените значение на **Включено** или **1** , чтобы включить ведение журнала.|  
|**Интервал промежуточного пакета**|**стагингбатчинтервал**|В функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Integration Management** functional area, the number of seconds after you select **Start Batches** that your batch is processed. Значение по умолчанию — **60** секунд (1 минута).|  
  
 Дополнительные сведения см. в разделе [Импорт данных (службы Master Data Services)](overview-importing-data-from-tables-master-data-services.md).  
  
##  <a name="Explorer"></a>Параметры обозревателя  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**Число элементов в иерархии по умолчанию**|**хиерарчичилдноделимит**|В функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Обозреватель** отображается максимальное количество элементов, которые отображаются в каждом узле иерархии до появления ссылки **…еще…**. Ссылку **…еще…** можно щелкнуть для отображения следующей группы элементов. Значение по умолчанию — **50**.|  
|**Показывать имена в иерархии по умолчанию**|**шовнамесинхиерарчи**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, determines the default setting that is selected when you view hierarchies.<br /><br /> Значение по умолчанию — **Да** или **1**, что задает отображение имени и кода каждого элемента. Измените значение на **Нет** или **2** , чтобы отображать только код.|  
|**Число атрибутов на основе домена в списке**|**дбалистровлимит**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the number of attributes that are displayed in a list when you double-click a domain-based attribute value in the grid. Значение по умолчанию — **50**. Если имеется более 50 элементов, вместо этого отображается диалоговое окно с возможностью поиска.|  
||**гридфилтердефаултфуззисимиларитилевел**|Определяет функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the level of similarity used when using the **Matches** filter criteria. Значение по умолчанию — **0,3**. При выборе значения ближе к **1** возвращаются элементы, более соответствующие указанным критериям. Задайте значение **1** для точного сопоставления.|  
  
##  <a name="xls"></a>Надстройка для параметров Excel  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|Отображать текст надстройки для Excel на домашней странице веб-сайта|ShowAddInText|Отображать ссылку на домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , чтобы пользователь мог скачать [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)].|  
|Путь установки надстройки для Excel на домашней странице веб-сайта|AddInURL|Если на домашней странице [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] отображается ссылка на [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] , то это будет место, куда будут переходить пользователи при нажатии на эту ссылку.|  
  
##  <a name="BusinessRules"></a>Параметры бизнес-правил  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**Число, на которое увеличиваются новые бизнес-правила**|**бусинессруледефаултприоритинкремент**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **System Administration** functional area, the number the priority of each new business rule is incremented by. Значение по умолчанию — **10**.|  
|**Число элементов, к которым применяются бизнес-правила**|**бусинессрулереалтимемемберкаунт**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **Explorer** functional area, the maximum number of members in the grid to apply business rules to. В [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)]— максимальное число элементов на активном листе, к которым применяется бизнес-правило. Значение по умолчанию — **10000**.|  
  
 Дополнительные сведения см. в статье [Бизнес-правила (службы Master Data Services)](../../2014/master-data-services/business-rules-master-data-services.md).  
  
##  <a name="Notifications"></a>Параметры уведомлений  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
|**URL-адрес диспетчер основных данных для уведомлений**|**мдмрутурл**|URL-адрес для веб-приложения [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], используемый в ссылке в уведомлениях, передаваемых по электронной почте, например http://constoso/mds.|  
|**Интервал отправки уведомлений по электронной почте**|**нотификатионинтервал**|Частота отправки уведомлений по электронной почте в секундах. Значение по умолчанию — **120** секунд (2 минуты).|  
|**Количество уведомлений в одном сообщении электронной почты**|**нотификатионсперемаил**|Максимальное число ошибок проверки, которые могут быть перечислены в одном уведомлении по электронной почте. Остальные ошибки, если они есть, не будут включены в сообщение электронной почты, но с ними можно ознакомиться в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].|  
|**Формат электронной почты по умолчанию**|**емаилформат**|Формат для всех уведомлений по электронной почте. Значение по умолчанию — **HTML** или **1**. Значение **2** этого параметра базы данных означает **Текст**.<br /><br /> Примечание. Этот формат можно переопределить для отдельного пользователя в [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], изменив и сохранив **Формат электронной почты** на вкладке **Общие** пользователя.|  
|**Регулярное выражение для адреса электронной почты**|**емаилрежекспаттерн**|[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] В функциональной области **разрешения пользователей и групп** регулярное выражение, используемое для проверки адреса электронной почты, указанного на вкладке **Общие** пользователя. Дополнительные сведения о регулярных выражениях см. в разделе [элементы языка регулярных выражений](https://go.microsoft.com/fwlink/?LinkId=164401) в библиотеке MSDN.|  
|**Учетная запись Database Mail**|**емаилпрофилепринЦипалаккаунт**|Отображает учетную запись компонента Database Mail, которая используется при отправке уведомлений по электронной почте. Профиль по умолчанию — **mds_email_user**.|  
|**Профиль Database Mail**|**датабасемаилпрофиле**|Профиль компонента Database Mail, который используется при отправке уведомлений по электронной почте. Значение по умолчанию — пусто.|  
||**валидатиониссуехтмл**|В формате HTML — текст сообщения электронной почты, которое получают пользователи при сбое проверки бизнес-правила.|  
||**валидатиониссуетекст**|В текстовом формате — текст сообщения электронной почты, которое получают пользователи при сбое проверки бизнес-правила.|  
||**версионстатусчанжетекст**|В текстовом формате — текст сообщения электронной почты, которое получают пользователи при изменении состояния версии. Это сообщение электронной почты получают только пользователи, имеющие разрешение **Обновление** для всей модели.|  
||**версионстатусчанжехтмл**|В формате HTML — текст электронного сообщения, которые получают пользователи при изменении состояния версии. Это сообщение электронной почты получают только пользователи, имеющие разрешение **Обновление** для всей модели.|  
  
 Дополнительные сведения см. в разделе [Уведомления (службы Master Data Services)](../../2014/master-data-services/notifications-master-data-services.md).  
  
##  <a name="Security"></a>Параметры безопасности  
  
|Параметр диспетчера конфигурации|Системный параметр|Description|  
|-----------------------------------|--------------------|-----------------|  
||**секуритимемберпроцессинтервал**|Определяет в функциональной области [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **User and Group Permissions** functional area, the frequency, in seconds, that user and group permissions set on the **Hierarchy Members** tab are applied. Значение по умолчанию — **3600** секунд (60 минут).|  
  
 Дополнительные сведения см. в разделе [Срочное применение разрешений для элемента (службы Master Data Services)](../../2014/master-data-services/immediately-apply-member-permissions-master-data-services.md).  
  
##  <a name="NotUsed"></a>Не используется  
 Следующие параметры в таблице системных параметров не используются:  
  
-   **SecurityMode**  
  
-   **мдшубнаме**  
  
-   **аппликатионлоггинг**  
  
-   **ReportServer**  
  
-   **репортдиректори**  
  
-   **бусинессрулингинеитератионлимит**  
  
-   **бусинессруликстенсибилити**  
  
-   **аттрибутиксплорермаркаллактионмемберкаунт**  
  
## <a name="see-also"></a>См. также:  
 [&#40;Master Data Services безопасности объектов базы данных&#41;](../../2014/master-data-services/database-object-security-master-data-services.md)  
  
  
