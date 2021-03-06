---
title: Обновление данных PowerPivot с SharePoint 2013 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 34f03407-2ec4-4554-b16b-bc9a6c161815
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 4076e27a800f9c9653e8a191c1fd53467cba9f75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66071226"
---
# <a name="powerpivot-data-refresh-with-sharepoint-2013"></a>Обновление данных PowerPivot с SharePoint 2013
  Проектирование для обновления моделей [!INCLUDE[ssGemini](../../includes/ssgemini-md.md)] данных в SharePoint 2013 использует службы Excel в качестве основного компонента для загрузки и обновления моделей данных на экземпляре [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающем в режиме интеграции с SharePoint. Сервер [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] работает на внешней ферме SharePoint.  
  
 Ранее использовавшаяся архитектура обновления данных при загрузке и обновлении моделей данных полагалась исключительно на системные службы PowerPivot экземпляра служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Экземпляр служб [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] запускался локально на сервере приложений PowerPivot. В новой архитектуре появился новый метод поддержания актуальности информации в виде метаданных элемента книги, находящейся в библиотеке документов. Архитектура служб SharePoint 2013 Excel поддерживает как **интерактивное** , так и **плановое**обновление данных.  
  
 **[!INCLUDE[applies](../../includes/applies-md.md)]** SharePoint 2013  
  
 **В этом разделе:**  
  
-   [Интерактивное обновление данных](#bkmk_interactive_refresh)  
  
-   [Проверка подлинности Windows с подключением к данным книги и интерактивным обновлением данных](#bkmk_windows_auth_interactive_data_refresh)  
  
-   [плановое](#bkmk_scheduled_refresh)  
  
-   [Архитектура планового обновления данных в SharePoint 2013](#bkmk_refresh_architecture)  
  
-   [Дополнительные рекомендации по проверке подлинности](#datarefresh_additional_authentication)  
  
-   [Дополнительные сведения](#bkmk_moreinformation)  
  
## <a name="background"></a>Историческая справка  
 SharePoint Server 2013 службы Excel управляют обновлением данных для книг Excel 2013 и запускает обработку модели данных на [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сервере, работающем в режиме интеграции с SharePoint. Для книг Excel 2010 службы Excel также управляют загрузкой и сохранением книг и моделей данных. Однако при этом службы Excel при отправке и обработке команд к модели данных полагаются на системные службы PowerPivot. В следующей таблице сведены компоненты, которые отправляют команды на обновление данных, в зависимости он версии книги. В качестве рабочей среды подразумевается ферма SharePoint 2013, настроенная на использование служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Server в режиме интеграции с SharePoint.  
  
||||  
|-|-|-|  
||Книги Excel 2013|Книги Excel 2010|  
|Запуск обновления данных|**Интерактивный:** Прошедший проверку пользователь<br /><br /> По **расписанию:** системная служба PowerPivot|Системная служба PowerPivot|  
|Загрузка книги из баз данных содержимого|Службы SharePoint 2013 Excel|Службы SharePoint 2013 Excel|  
|Загрузка модели данных на экземпляр служб Analysis Services|Службы SharePoint 2013 Excel|Службы SharePoint 2013 Excel|  
|Отправка команд обработки на экземпляр служб Analysis Services|Службы SharePoint 2013 Excel|Системная служба PowerPivot|  
|Обновление данных книги|Службы SharePoint 2013 Excel|Службы SharePoint 2013 Excel|  
|Сохранение книги и модели данных в базе данных содержимого|**Интерактивный:** Н/Д<br /><br /> По **расписанию:** Службы Excel 2013 SharePoint|Службы SharePoint 2013 Excel|  
  
 В следующей таблице сведены поддерживаемые возможности обновления на ферме SharePoint 2013, настроенной на использование служб [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Server в режиме интеграции с SharePoint.  
  
|Книга создана в|плановое|Интерактивное обновление данных|  
|-------------------------|----------------------------|-------------------------|  
|2008 R2 PowerPivot для Excel|Не поддерживается. Обновление книги **(\*)**|Не поддерживается. Обновление книги **(\*)**|  
|2012 PowerPivot для Excel|Поддерживается|Не поддерживается. Обновление книги **(\*)**|  
|Excel 2013|Поддерживается|Поддерживается|  
  
 **(\*)** Дополнительные сведения об обновлении книги см. в статье [обновление книг и запланированное обновление данных &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
##  <a name="bkmk_interactive_refresh"></a>Интерактивное обновление данных  
 Интерактивное или ручное обновление данных в службах SharePoint Server 2013 Excel Services может обновить модели сведениями из оригинальных источников данных. Интерактивное обновление данных становится доступным после настройки приложения служб Excel путем регистрации сервера [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] в режиме интеграции с SharePoint. Дополнительные сведения см. в разделе [Управление параметрами модели данных служб Excel (SharePoint Server 2013)](https://technet.microsoft.com/library/jj219780.aspx).  
  
> [!NOTE]  
>  Интерактивное обновление данных доступно только для книг, созданных в Excel 2013. При попытке обновить книгу Excel 2010 службы Excel выводят сообщение об ошибке, похожее на "сбой операции PowerPivot: книга была создана в более ранней версии Excel, и PowerPivot не может быть обновлен до обновления файла". Дополнительные сведения об обновлении книг см. в статье [Обновление книг и создание расписания обновления данных (SharePoint 2013)](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
 **Основная особенность интерактивного обновления**  
  
-   При интерактивном обновлении данных обновляются только данные в сеансе текущего пользователя. Данные автоматически не сохраняются в книге, хранящейся в базе данных содержимого SharePoint.  
  
-   **Учетные данные:** Интерактивное обновление данных может использовать удостоверение вошедшего в систему пользователя в качестве учетных данных или сохраненных учетных данных для подключения к источнику данных. Какие именно учетные данные используются, зависит от настроек проверки подлинности служб Excel при подключении к внешнему источнику данных для книги.  
  
-   **Поддерживаемые книги:**  Книги, созданные в Excel 2013.  
  
 **Обновление данных**  
  
-   См. порядок действий на иллюстрации.  
  
1.  В библиотеке документов SharePoint откройте книгу PowerPivot в браузере.  
  
2.  В окне браузера в меню **Данные** выберите пункт **Обновить выбранное соединение** или **Обновить все соединения**.  
  
3.  Службы Excel загружают базу данных PowerPivot, обрабатывают ее и затем выполняют к ней запрос, чтобы обновить кэш книги Excel.  
  
4.  **Примечание.** Обновленная книга не сохраняется автоматически обратно в библиотеку документов.  
  
 ![интерактивное](../media/as-interactive-datarefresh-sharepoint2013.gif "интерактивное")  
  
###  <a name="bkmk_windows_auth_interactive_data_refresh"></a>Проверка подлинности Windows с подключением к данным книги и интерактивным обновлением данных  
 Службы Excel отправляют серверу службы Analysis Services команду обработки на олицетворение учетной записи пользователя. Чтобы получить системные права, достаточные для выполнения процедуры делегирования и олицетворения для пользователя, учетная запись службы Analysis Services запрашивает право доступа **Работа в режиме операционной системы** на локальном сервере. Кроме того, сервер службы Analysis Services должен иметь возможность делегировать учетные записи пользователя источникам данных. Результат запроса отправляется службам Excel.  
  
 Типичное взаимодействие с пользователем. когда клиент выбирает команду "обновить все подключения" в книге Excel 2013, содержащей модель PowerPivot, выводится сообщение об ошибке следующего вида:  
  
-   **Сбой обновления внешних данных:** Произошла ошибка при работе с моделью данных в книге. Повторите попытку. Не удалось обновить одно или несколько подключений в данной книге.  
  
 В зависимости от используемого поставщика данных вы увидите в журнале ULS сообщение, аналогичное следующему.  
  
 **С помощью SQL Native Client:**  
  
-   Не удалось создать внешнее соединение или выполнить запрос. Сообщение поставщика. Был задан, но не используется внешний объект «DataSource», ссылающийся на идентификаторы «20102481-39c8-4d21-bf63-68f583ad22bb».  Ошибка OLE DB или ODBC. При установлении соединения с сервером SQL Server произошла ошибка, связанная с сетью или с определенным экземпляром. Сервер не найден или недоступен. Проверьте, правильно ли указано имя экземпляра и настроен ли SQL Server для открытия удаленных соединений. Дополнительные сведения см. в электронной документации по SQL Server; 08001; Поставщик SSL: затребованный пакет безопасности не существует; 08001; Клиенту не удается установить связь; 08001; Клиент не поддерживает шифрование; 08001,  , имя соединения: ThisWorkbookDataModel, книга: book1.xlsx.  
  
 **Для поставщика Microsoft OLE DB для SQL Server:**  
  
-   Не удалось создать внешнее соединение или выполнить запрос. Сообщение поставщика: «Задан, но не используется внешний объект DataSource, соответствующий идентификатору 6e711bfa-b62f-4879-a177-c5dd61d9c242». Ошибка OLE DB или ODBC. , имя соединения: ThisWorkbookDataModel, книга: OLEDB Provider.xlsx.  
  
 **Для поставщика данных .NET Framework для SQL Server:**  
  
-   Не удалось создать внешнее соединение или выполнить запрос. Сообщение поставщика. Был задан, но не используется внешний объект «DataSource», ссылающийся на идентификаторы f5fb916c-3eac-4d07-a542-531524c0d44a.  Ошибки в реляционном модуле высокого уровня. Следующее исключение возникло при использовании управляемого интерфейса IDbConnection: не удалось загрузить файл или сборку «System.Transactions, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089» или один из его зависимых компонентов. Либо не обеспечен необходимый уровень олицетворения, либо уровень олицетворения недопустим. (Исключение HRESULT: 0x80070542.)  , имя соединения: ThisWorkbookDataModel, книга: NETProvider.xlsx.  
  
 **Сводка по этапам настройки** Чтобы настроить **действие действия в составе операционной системы** на локальном сервере, выполните следующие действия.  
  
1.  На сервере службы Analysis Services в режиме интеграции с SharePoint добавьте для учетной записи службы Analysis Services привилегию**Работа в качестве части операционной системы**:  
  
    1.  Выполните команду`secpol.msc`""  
  
    2.  Выберите **Параметр локальной безопасности**, затем **Локальные политики**, а затем **Назначение прав пользователя**.  
  
    3.  Добавьте учетную запись службы.  
  
2.  Перезапустите службы Excel и перезагрузите сервер службы Analysis Services.  
  
3.  Делегирование от учетной записи службы Excel или службы токенов Claims to Windows (C2WTS) экземпляру служб Analysis services не требуется. Поэтому никакая настройка KCD из служб Excel или C2WTS службе PowerPivot AS не нужна. Если серверный источник данных находится на том же сервере, что и экземпляр [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , ограниченное делегирование Kerberos не требуется. Однако учетной записи службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] необходимо право на работу в качестве части операционной системы.  
  
 ![as_interactive_data_refresh2012SP1_windowsauth](../media/as-interactive-data-refresh2012sp1-windowsauth.gif "as_interactive_data_refresh2012SP1_windowsauth")  
  
 Дополнительные сведения см. [в разделе Работа в составе операционной системы](https://technet.microsoft.com/library/cc784323\(WS.10\).aspx).  
  
##  <a name="bkmk_scheduled_refresh"></a>Запланированное обновление данных  
 **Основные моменты по запланированному обновлению данных:**  
  
-   Требует развертывания надстройки PowerPivot для SharePoint. Дополнительные сведения см. в разделе [Установка или удаление надстройки PowerPivot для SharePoint &#40;SharePoint 2013&#41;](../instances/install-windows/install-or-uninstall-the-power-pivot-for-sharepoint-add-in-sharepoint-2013.md).  
  
-   Пользователь настраивает расписание обновления для книги. В запланированное время системная служба PowerPivot отправляет службе Excel запрос:  
  
    -   на загрузку и обработку базы данных PowerPivot;  
  
    -   обновление книги;  
  
    -   сохранение книги в базе данных содержимого.  
  
-   **Учетные данные:** Использует сохраненные учетные данные. Удостоверение текущего пользователя не используется.  
  
-   **Поддерживаемые книги:** Книги, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] созданные с помощью надстройки PowerPivot для Excel 2010 или с помощью Excel 2013. Не поддерживаются книги, созданные в Excel 2010 с надстройкой [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] PowerPivot. Обновите книгу по крайней мере до формата [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] PowerPivot. Дополнительные сведения об обновлении книг см. в статье [Обновление книг и создание расписания обновления данных (SharePoint 2013)](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md).  
  
 Отображение страницы **Управление обновлением данных**  
  
-   См. порядок действий на иллюстрации.  
  
1.  В библиотеке документов SharePoint нажмите кнопку **Меню открытия** (**…**) для книги PowerPivot.  
  
2.  Нажмите вторую кнопку **Меню открытия** и выберите **Управление обновлением данных PowerPivot**.  
  
3.  На странице **Управление обновлением данных** щелкните **Включить** , а затем настройте расписание обновления.  
  
4.  В заданное время системная служба PowerPivot отправляет службе Excel запрос:  
  
    -   на загрузку и обработку модели данных PowerPivot;  
  
    -   обновление книги;  
  
    -   сохранение книги в базе данных содержимого.  
  
 ![управление контекстным меню обновления данных](../media/as-manage-datarefresh-sharepoint2013.gif "управление контекстным меню обновления данных")  
  
> [!TIP]  
>  Сведения об обновлении книг из SharePoint Online см. в разделе [обновление книг Excel с внедренными моделями PowerPivot из SharePoint Online (технический документ)](https://technet.microsoft.com/library/jj992650.aspx) (https://technet.microsoft.com/library/jj992650.aspx).  
  
##  <a name="bkmk_refresh_architecture"></a>Архитектура запланированного обновления данных в SharePoint 2013  
 На следующем рисунке показана архитектура обновления данных для SharePoint 2013 и SQL Server 2012 с пакетом обновления 1 (SP1).  
  
 ![архитектура обновления данных SQL Server 2012 с пакетом обновления 1 (SP1)](../media/as-scheduled-data-refresh2012sp1-architecture.gif "архитектура обновления данных SQL Server 2012 с пакетом обновления 1 (SP1)")  
  
||Description||  
|-|-----------------|-|  
|**одного**|Подсистема служб Analysis Services|Сервер [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , работающем в режиме интеграции с SharePoint. Сервер работает за пределами фермы SharePoint.|  
|**открыт**|Пользовательский интерфейс|Пользовательский интерфейс состоит из двух страниц. На одной из них определяется расписание, а на второй можно просмотреть журнал обновления. Эти страницы не осуществляют прямого доступа к базам данных приложения службы PowerPivot, но пользуются системной службой PowerPivot для доступа к этим базам данных.|  
|**(3)**|Системная служба PowerPivot|Эта служба устанавливается при развертывании надстройки PowerPivot для SharePoint. Она служит для выполнения следующих действий.<br /><br /> В этой службе размещается исполняющий механизм планирования обновления, который вызывает API служб Excel для обновления данных в книгах Excel 2013. Для книг Excel 2010 эта служба непосредственно выполняет обработку модели данных, но продолжает обрабатывать запросы служб Excel на загрузку модели данных и обновление книги.<br /><br /> Эта служба содержит методы для таких компонентов, как страницы пользовательского интерфейса, для обмена данными с системной службой.<br /><br /> Управляет запросами на внешний доступ к книгам как к источнику данных, принимаемыми через веб-службу PowerPivot.<br /><br /> Управление запросами на плановое обновление данных по заданиям таймера и страницам конфигурации. Эта служба управляет запросами на считывание данных из базы данных приложения службы и запускает обновление данных вместе со службами Excel.<br /><br /> Обработка использования и связанные задания таймера.|  
|**четырех**|Службы вычислений Excel|Отвечают за загрузку моделей данных.|  
|**5.0**|Служба Secure Store|Если параметры проверки подлинности в книге настроены для **использования учетной записи пользователя, прошедшего проверку подлинности** , или **нет**, то для обновления данных используются учетные данные, хранящиеся в идентификаторе целевого приложения Secure Store. Дополнительные сведения см. в подразделе [Другие вопросы проверки подлинности](#datarefresh_additional_authentication) этой статьи.|  
|**1-6**|Задание таймера обновления данных PowerPivot|Указывает системной службе PowerPivot подключиться к службам Excel для обновления моделей данных.|  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]требуются соответствующие поставщики данных и клиентские библиотеки, чтобы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] сервер в режиме интеграции с SharePoint мог обращаться к источникам данных.  
  
> [!NOTE]  
>  Поскольку системная служба PowerPivot больше не загружает и не сохраняет модели PowerPivot, большинство настроек кэширования на сервере приложений на ферме SharePoint 2013 не действуют.  
  
## <a name="data-refresh-log-data"></a>Данные журнала обновления данных  
 **Данные об использовании:** Данные об обновлении данных можно просмотреть на панели управления PowerPivot. Просмотр данных об использовании  
  
1.  В центре администрирования SharePoint выберите **Панель управления PowerPivot** в группе **Общие параметры приложения** .  
  
2.  В нижней части панели мониторинга см. статью **Обновление данных — последние действия** и **Обновление данных — последние ошибки**.  
  
3.  Дополнительные сведения об использовании и о том, как включить сбор этих данных, см. в разделе [PowerPivot Management Dashboard and Usage Data](power-pivot-management-dashboard-and-usage-data.md).  
  
 **Данные журнала диагностики:** Вы можете просматривать данные журнала диагностики SharePoint, связанные с обновлением данных. Сначала проверьте конфигурацию ведения журнала диагностики в разделе **Служба PowerPivot** на странице **Мониторинг** центра администрирования SharePoint. Может потребоваться увеличить уровень ведения журнала для журнала "минимальное критическое событие". Например, временно установите значение **Подробно** и снова выполните операцию обновления данных.  
  
 Журнал содержит следующие сведения:  
  
-   
  **Область****Службы PowerPivot**.  
  
-   Категория **Обновления данных**.  
  
 Просмотрите **Настройка ведения журнала диагностики**. Дополнительные сведения см. в статьях [Настройка и просмотр файлов журнала SharePoint и журнала диагностики &#40;PowerPivot для SharePoint&#41;](configure-and-view-sharepoint-and-diagnostic-logging.md).  
  
##  <a name="datarefresh_additional_authentication"></a>Дополнительные рекомендации по проверке подлинности  
 Параметры в диалоговом окне **Параметры проверки подлинности служб Excel** в Excel 2013 задают удостоверение Windows, которым службы Excel и [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] пользуются для обновления данных.  
  
-   **Использовать учетную запись пользователя, прошедшего проверку подлинности**. службы Excel выполняют обновление данных под удостоверением пользователя, вошедшего в систему.  
  
-   **Использовать сохраненную учетную запись**. Предполагается, что в службах Excel используется идентификатор приложения Служба Secure Store, который используются для получения имени пользователя и пароля для проверки подлинности при обновлении данных.  
  
-   **Нет**: используется **Автоматическая учетная запись службы** Excel. Эта учетная запись службы связана с прокси-сервером Secure Store. Настройте параметры на странице **Параметры приложения служб Excel** в разделе **Внешние данные** .  
  
 Открытие диалогового окна «Параметры проверки подлинности»  
  
1.  Откройте вкладку **Данные** в Excel 2013.  
  
2.  Нажмите на ленте **Соединения** .  
  
3.  В диалоговом окне **Соединения книги**выберите соединение и нажмите **Свойства**.  
  
4.  В диалоговом окне **Свойства соединения** щелкните **Определение**, а затем нажмите кнопку **Параметры проверки подлинности...** .  
  
 ![Параметры проверки подлинности служб Excel](../media/as-authentication-settings-4-ecs-in-excel2013.gif "Параметры проверки подлинности служб Excel")  
  
 Дополнительные сведения о проверке подлинности при обновлении данных и использовании учетных данных см. в записи блога [Refreshing PowerPivot Data in SharePoint 2013](https://blogs.msdn.com/b/analysisservices/archive/2012/12/21/refreshing-powerpivot-data-in-sharepoint-2013.aspx)(на английском языке).  
  
##  <a name="bkmk_moreinformation"></a>Дополнительные сведения  
 [Устранение неполадок при обновлении данных PowerPivot](https://social.technet.microsoft.com/wiki/contents/articles/3870.troubleshooting-powerpivot-data-refresh.aspx).  
  
 [Службы Excel в SharePoint 2013](https://www.enjoysharepoint.com/configure-excel-service-application-in-sharepoint-2013/). 
  
## <a name="see-also"></a>См. также:  
 [Обновление книг и обновление данных по расписанию &#40;SharePoint 2013&#41;](../instances/install-windows/upgrade-workbooks-and-scheduled-data-refresh-sharepoint-2013.md)   
 [Установка PowerPivot для SharePoint 2013](../instances/install-windows/install-analysis-services-in-power-pivot-mode.md)  
  
  
