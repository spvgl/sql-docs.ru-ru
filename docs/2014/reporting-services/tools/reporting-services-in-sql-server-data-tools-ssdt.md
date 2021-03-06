---
title: Службы Reporting Services в среде SQL Server Data Tools (SSDT) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence Development Studio, Reporting Services in
ms.assetid: 0903c7b2-ac59-45f1-b7d0-922ecd9d76f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f9c9719f3e73326c2b86117b3a78a8ede927198d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68888933"
---
# <a name="reporting-services-in-sql-server-data-tools-ssdt"></a>Службы Reporting Services в SQL Server Data Tools (SSDT)
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)][!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] — это среда с усовершенствованиями, характерными для решений бизнес-аналитики. Среда [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] входит в состав [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
 Среда [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] используется для создания решений и проектов отчетов и связанных с отчетами элементов служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] и управления ими. В [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] имеется конструктор отчетов. В конструкторе отчетов можно открывать, изменять, просматривать, сохранять и развертывать определения отчетов, общие источники данных, общие наборы данных и элементы отчетов.  
  
 В этом разделе описываются решения, проекты, шаблоны проектов и конфигурации служб [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] для [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], а также представления, меню, панели инструментов и сочетания клавиш, которые можно использовать в конструкторе отчетов.  
  
 Чтобы приступить к разработке отчетов, см. раздел [Разработка отчетов с использованием конструктора отчетов (SSRS)](design-reporting-services-paginated-reports-with-report-designer-ssrs.md).  
  
##  <a name="bkmk_SolutionsandProjects"></a>Решения и проекты  
 Проект отчета выступает в качестве контейнера для определений отчета и ресурсов. Когда проект развернут, каждый файл проекта отчета публикуется на сервере отчетов. При первом создании проекта также создается решение в качестве контейнера для проекта. К одному решению можно добавить несколько проектов.  

##  <a name="bkmk_Configurations"></a>Configuration  
 Чтобы создать несколько наборов свойств проекта для различных вариантов развертывания, например для тестового и рабочего серверов отчетов предприятия, следует использовать диспетчер конфигурации. Дополнительные сведения см. в разделе [Развертывание и поддержка версий в SQL Server Data Tools (службы SSRS)](deployment-and-version-support-in-sql-server-data-tools-ssrs.md).  
  
##  <a name="bkmk_ReportServerProjects"></a>Проекты сервера отчетов  
 После установки служб [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]становятся доступны следующие шаблоны проектов.  
  
-   **Проект сервера отчетов.** При выборе проекта сервера отчетов открывается конструктор отчетов. Проект сервера отчетов — это шаблон проекта бизнес-аналитики, установленный в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] и доступный в диалоговом окне **Создание проекта** . Дополнительные сведения см. в разделе [Добавление в проект отчета нового или существующего отчета (службы SSRS)](add-a-new-or-existing-report-to-a-report-project-ssrs.md). Свойства проекта сервера отчетов относятся ко всем отчетам и общим источникам данных проекта среды [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]. В число этих свойств входит URL-адрес сервера отчетов и имена папок для отчетов и общих источников данных. Текущие значения свойств можно просмотреть с помощью диалогового окна **Страницы свойств проекта** . Чтобы открыть это диалоговое окно, в меню **проект** выберите пункт _ \<имя проекта>_ **Свойства**.  
  
-   **Мастер проектов сервера отчетов.** При выборе проекта мастера сервера отчетов автоматически создается проект сервера отчетов и открывается мастер отчетов. Отчеты можно создавать с помощью мастера. Для этого необходимо выполнять инструкции на каждой странице: создается строка подключения с источником данных, указываются учетные данные для соединения с ним, создается запрос, добавляются области данных таблицы или матрицы, задаются данные отчета и групп, выбирается цвет шрифта и стиля, отчет публикуется на сервере отчетов и просматривается в локальном режиме. После создания отчета с помощью мастера можно изменить данные и структуру отчета с помощью конструктора отчетов в проекте сервера отчетов.  
  
 ![Новые шаблоны проекта в SSDT](https://docs.microsoft.com/analysis-services/analysis-services/media/ssdt-biprojects.png "Новые шаблоны проекта в SSDT")  

##  <a name="bkmk_ReportDesignerWindowsandPanes"></a>конструктор отчетов окна и панели  
 Конструктор отчетов поддерживает два представления: **Конструктор**, в котором задаются данные и макет отчета, и **Предварительный просмотр**, позволяющее просмотреть подготовленный отчет. В каждом представлении можно вывести несколько окон для удобства конструирования или просмотра отчета.  
  
###  <a name="bkmk_ReportDataPane"></a>Область данных отчета  
 В области данных отчета отображаются встроенные поля, источники данных, наборы данных, коллекции полей, параметры отчетов и изображения.  
  
 Область данных отчета используется для просмотра следующих элементов.  
  
-   **Встроенные поля** Стандартные сведения об отчете, такие как имя отчета или время обработки отчета.  
  
-   **Источники данных** Источник данных представляет имя и соединение с источником данных.  
  
-   **Наборы данных** Каждый набор данных включает запрос, указывающий, какие данные необходимо получить из источника данных. Раскройте набор данных, чтобы просмотреть коллекции полей, определенные запросом к набору данных.  
  
     В некоторых конструкторах запросов для многомерных наборов данных на панели «Фильтры» можно задать фильтры и указать, следует ли создавать параметры отчета. Если указать параметр отчета, автоматически создается специальный набор данных для заполнения списка допустимых значений параметра.  По умолчанию этот набор данных не отображается в области данных отчета. Дополнительные сведения см. в разделе [Отображение скрытых наборов данных для значений параметра в многомерных данных (построитель отчетов и службы SSRS)](../report-data/show-hidden-datasets-for-parameter-values-multidimensional-data.md).  
  
-   **Параметры отчета** Список параметров отчета. Параметры могут быть созданы вручную или автоматически, если запрос к набору данных включает параметры запроса.  
  
-   **Образы** Список изображений, которые можно включить в отчет в виде элемента отчета с изображением.  
  
 Источники и наборы данных в области данных отчета представляют элементы в определении отчета. Область данных отчета — это функция, поддерживаемая многими средами создания отчетов. В построителе отчетов это единственная доступная панель для управления источниками и наборами данных. В конструкторе отчетов область данных отчета работает вместе с обозревателем решений, в котором общие источники и наборы данных отображаются в виде файлов. Общие источники и наборы данных в области данных отчета должны указывать на соответствующие общие источники данных и общие наборы данных в обозревателе решений. Элементы в области данных отчета содержат ссылки на файлы данных в обозревателе решений. Свойства проекта определяют, должны ли общие источники и наборы данных развертываться на сервере отчетов или на сайте SharePoint. Дополнительные сведения см. в разделе [Преобразование источника данных из внедренного в общие &#40;построитель отчетов и службы SSRS&#41;](../report-data/convert-data-sources-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  Если область данных отчета не видна, в меню **вид** выберите пункт **данные отчета**. Если область данных отчета открывается как плавающее окно, его можно закрепить. Дополнительные сведения см. в разделе [Закрепление области данных отчета в конструкторе отчетов (службы SSRS)](dock-the-report-data-pane-in-report-designer-ssrs.md).  

###  <a name="bkmk_GroupingPane"></a>Панель группирования  
 На панели группирования определяются группы для области данных табликса. Для таблиц можно задавать группы строк и сведений, а для матриц — группы строк и столбцов. Панель группирования нельзя использовать для определения групп для диаграмм или других областей данных. Дополнительные сведения см. в разделе [Основные сведения о группах (построитель отчетов и службы SSRS)](../report-design/understanding-groups-report-builder-and-ssrs.md).  
  
 Панель группирования имеет два режима:  
  
-   **Параметры.** Текущие значения свойств можно просмотреть с помощью диалогового окна **По умолчанию** используется для отображения всех групп строк и столбцов в иерархическом формате, показывающем связи между родительскими группами, дочерними группами, смежными группами и группами сведений. Дочерняя группа выводится ниже родительской группы и на один уровень отступа правее. Смежная группа выводится на том же уровне отступа, что и группы одного с ней уровня.  
  
     Добавление, удаление и изменение групп происходит в режиме по умолчанию. Если группа создана на основе одного поля набора данных, то это поле можно перетащить на панель «Группы строк» или «Группы столбцов». Группу можно вставить выше или ниже существующей группы. Для добавления смежной группы щелкните правой кнопкой мыши одноуровневую группу и воспользуйтесь функциями контекстного меню. Чтобы отобразить ячейки табликса, принадлежащие к группе, выделите группу на панели группирования.  
  
-   **Продвинут.** Текущие значения свойств можно просмотреть с помощью диалогового окна **Расширенный** используется для отображения элементов статических и динамических групп строк и столбцов выбранной области данных табликса.  Элементы групп используются для настройки свойств, управляющих отображением строк и столбцов, связанных с группой или элементом группы, а также для настройки правил, согласно которым модули подготовки отчетов пытаются выводить группы вместе на одной странице. В области конструктора отобразятся элементы группы в виде ячеек в областях групп строк и групп столбцов.  
  
> [!NOTE]  
>  Для переключения между режимом **По умолчанию** и **Расширенный** щелкните правой кнопкой мыши стрелку вниз, расположенную справа от значка **Группы столбцов** .  
  
 Дополнительные сведения см. в разделе [Grouping Pane](grouping-pane.md).  

###  <a name="bkmk_Toolbox"></a>Инструментов  
 Панель элементов содержит элементы отчета, которые можно перетащить в область конструктора. Области данных — это элементы отчета, с помощью которых упорядочиваются данные отчета. Таблица, матрица, список, диаграмма, датчик, гистограмма, спарклайн и индикатор являются областями данных. К другим элементам отчета относятся карта, текстовое поле, прямоугольник, линия, изображение и вложенный отчет. Пользовательские элементы отчета тоже могут входить в этот список, если они установлены и зарегистрированы системным администратором.  
  
###  <a name="bkmk_PropertiesPane"></a>Панель "Свойства"  
 Панель свойств представляет собой стандартное окно среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , в котором отображаются имена и значения свойств элемента отчета, выбранного в данный момент в области конструктора. В большинстве случаев имена свойств соответствуют элементам и атрибутам, которые хранятся в файле на языке определения отчетов (RDL). Наиболее часто используемые свойства можно установить с помощью диалогового окна «Свойства» выбранного элемента. Чтобы открыть нужное диалоговое окно, нажмите кнопку **Страницы свойств** на панели инструментов на панели свойств. Опытные пользователи могут задавать значения свойств непосредственно на панели свойств.  
  
 Панель свойств используется для следующих действий.  
  
-   Задание свойств для текущего выбранного элемента в области конструктора. Некоторые свойства имеют раскрывающийся список значений. Кроме того, можно ввести значение непосредственно в ячейку. Некоторые свойства содержат коллекцию значений, что обозначается как **(Коллекция)**. Большинство свойств может принимать выражение. сложные выражения обозначаются ** \<выражением значения>**. Щелкните ** \<выражение>** , чтобы открыть диалоговое окно **выражение** . Дополнительные сведения см. в разделе [Expression Dialog Box](../expression-dialog-box.md).  
  
-   С помощью кнопок панели инструментов на панели свойств можно переключать сетку с вида по категориям на вид в алфавитном порядке. В представлении по категориям можно развернуть ту или иную категорию, чтобы увидеть все принадлежащие к ней свойства. Чтобы открыть диалоговое окно свойств элемента, нажмите кнопку **Страницы свойств** на панели инструментов или щелкните элемент правой кнопкой мыши и выберите **Свойства**.  
  
-   Задание свойств для элемента группы, выбранного в данный момент на панели группирования. Свойства элементов групп помогают управлять повторением статических строк заголовков и нижних колонтитулов для каждого экземпляра группы. Дополнительные сведения см. в разделе [Отображение верхних и нижних колонтитулов в группе (построитель отчетов и службы SSRS)](../report-design/display-headers-and-footers-with-a-group-report-builder-and-ssrs.md).  
  
 Для вывода панели свойств выберите пункт **Окно свойств** в меню **Вид**. Можно отменить закрепление этой панели и переместить ее в другую часть окна среды [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]либо вывести как представление со вкладками в области конструктора.  

###  <a name="bkmk_SolutionExplorer"></a>обозреватель решений  
 Обозреватель решений представляет собой стандартный компонент среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] , в котором отображаются все элементы проекта. Для проекта сервера отчетов сюда входят папки, позволяющие упорядочить общие источники данных, общие наборы данных, отчеты и ресурсы. Элементы в папках автоматически упорядочиваются по алфавиту при открытии файла решения. Чтобы просмотреть свойства элемента на панели "Свойства", выделите этот элемент.  
  
###  <a name="bkmk_Output"></a>Проверки  
 В окне «Вывод» отображаются ошибки обработки при предварительном просмотре отчета и ошибки публикации — при развертывании отчета или общего источника данных.  
  
 Окна «Вывод» и «Структура документа» можно использовать для отладки ошибок в выражениях.  

###  <a name="bkmk_DocumentOutline"></a>Структура документа  
 Окно «Структура документа» предназначено для просмотра иерархии всех элементов отчета в определении отчета. Чтобы открыть панель структуры документа, в меню **Вид** укажите **Другие окна** и щелкните **Окно документа**.  
  
 Панель «Структура документа» используется для идентификации текстовых полей и других элементов отчета по именам. При выборе элемента на панели структуры документа соответствующий элемент также выбирается в области конструктора.  
  
###  <a name="bkmk_TaskList"></a>список задач  
 В окне «Список задач» отображаются ошибки сборки для неподдерживаемых функций, если отчет импортирован из другого приложения, например [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Access.  

##  <a name="bkmk_ReportDesignerDesignView"></a>конструктор отчетов представление конструктора  
 По умолчанию при создании проекта сервера отчетов конструктор отчетов открывается в представлении конструктора с открытой областью конструктора. По умолчанию в области конструктора отображается текст отчета и фон.  
  
 Контекстное меню фона содержит функции добавления верхнего и нижнего колонтитула отчета, а с помощью меню «Вид» можно отобразить линейку и панель группирования.  
  
 С помощью элемента управления масштабированием можно уменьшать и увеличивать масштаб, в котором выводится отчет.  
  
 Для конструирования отчета элементы отчета можно перетаскивать с панели элементов в область конструктора, чтобы затем настраивать их свойства и менять их расположение в отчете.  

##  <a name="bkmk_ReportDesignerPreview"></a>Предварительный просмотр конструктор отчетов  
 Предварительный просмотр используется для запуска отчета и просмотра подготовленного отчета с помощью средства просмотра отчетов. При предварительном просмотре данные отчета сохраняются в локальном кэше. Кроме того, можно настроить конфигурацию для запуска отчета в представлении отладки с помощью браузера.  
  
 При предварительном просмотре отчета конструктор отчетов подключается к источникам данных отчета, запускает запросы наборов данных, кэширует данные на локальном компьютере, обрабатывает отчет (в ходе обработки данные и макет объединяются) и подготавливает его к просмотру. Отчет можно просмотреть на вкладке «Предварительный просмотр» или настроить свойства проекта для просмотра отчета в режиме отладки или непосредственно в браузере.  
  
-   **Предварительный просмотр параметризованных отчетов.** При предварительном просмотре отчеты обрабатываются автоматически, если все параметры отчета имеют допустимые значения по умолчанию. Если у одного или нескольких параметров отчета нет допустимых значений по умолчанию, то нужно выбрать значение для каждого такого параметра, затем нажать кнопку **Просмотреть отчет**на панели инструментов отчета.  
  
-   **Основные сведения о локальном кэше данных** При предварительном просмотре отчета обработчик отчетов выполняет все запросы для наборов данных в отчете с использованием текущих параметров по умолчанию и сохраняет результаты в виде файла локального кэша данных (RDL. Data). Если запросы набора данных отчета и параметры отчета не изменились, то можно воспользоваться уже полученными данными из кэша и продолжать конструирование отчета без дополнительной нагрузки на ресурсы для их повторного получения.  
  
-   **Предварительный просмотр отчета с помощью Configuration Manager и отладки.** Свойства проекта в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]определяют, каким образом будут развертываться и отлаживаться отчеты. Эти свойства относятся ко всем отчетам и общим источникам данных проекта. Чтобы настроить свойства проекта, щелкните в меню **Проект** пункт **Свойства**. С помощью этих параметров можно тестировать отчеты и публиковать их на сервере отчетов.  
  
-   **Мониторинг области вывода для сообщений об ошибках.** Если при предварительном просмотре отчета обработчик обнаруживает проблему, он выводит сообщения об ошибках на панель вывода.  

##  <a name="bkmk_ReportDesignerMenus"></a>конструктор отчетов меню  
 Если проект конструктора отчетов активен в среде [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], то на главную панель инструментов добавляются следующие панели инструментов. Меню конструктора отчетов видны только в режиме конструктора.  
  
###  <a name="FormatMenu"></a>Меню "формат"  
 При выборе элемента в области конструктора меню **Формат** содержит следующие команды.  
  
-   **Цвет переднего плана** Выберите цвет текста. Цвет по умолчанию — черный.  
  
-   **Цвет фона** Выберите цвет фона для текстовых полей и областей данных.  
  
-   **Шрифт** Укажите, является ли текст полужирным, курсивом или подчеркнутым.  
  
-   **Выровнять по ширине** Укажите, выровнен ли текст по правому краю, по центру или по левому краю.  
  
-   **Выровняйте по** Укажите способ выровняйте выделенные объекты относительно друг друга в отчете.  
  
-   **Сделать одинаковый размер** Измените размер выбранных объектов в отчете.  
  
-   **Отступ по горизонтали** Настройка интервала по горизонтали между выделенными объектами в отчете.  
  
-   **Вертикальные пробелы** Настройка интервала по вертикали между выделенными объектами в отчете.  
  
-   **Центрировать в форме** Центрирование выделенного объекта по вертикали и горизонтали относительно окна конструктор отчетов.  
  
-   **Порядок следования** Переместить выбранные объекты в фон или на передний план.  
  
###  <a name="ReportMenu"></a>Меню «Отчет»  
 Когда область конструктора отчетов находится в фокусе, меню **Отчет** содержит следующие команды.  
  
-   **Свойства отчета** Выберите этот пункт, чтобы открыть диалоговое окно **Свойства отчета** . В этом диалоговом окне задаются общие свойства отчета, например имя автора, размер шага сетки, а также такие свойства макета отчета, как число столбцов и размеры страниц. Можно также указать пользовательский код, ссылки на сборки и классы, имена выходных элементов, преобразований и схем данных.  
  
-   **Просмотр** Переключение между двумя конструктор отчетов вкладками: проектирование и предварительный просмотр.  
  
-   **Верхний колонтитул страницы** Добавление или удаление верхнего колонтитула страницы в отчете. При удалении верхнего колонтитула страницы удаляются также все его элементы.  
  
-   **Нижний колонтитул страницы** Добавление или удаление нижнего колонтитула страницы отчета. При удалении нижнего колонтитула страницы удаляются также все его элементы.  
  
-   **Панель группирования** Показать или скрыть панель группирования.  
  
###  <a name="ViewMenu"></a>Меню "вид"  
 С помощью меню **Вид** можно отобразить следующие окна и панели инструментов конструктора отчетов.  
  
-   **Список ошибок** Используйте этот параметр для отображения ошибок, обнаруженных при публикации или предварительном просмотре отчета.  
  
-   **Выходные данные** Этот параметр используется для отображения ошибок, обнаруженных при публикации или обработке отчета, а также для получения дополнительных сведений об ошибках выражений, когда в отчете отображается текст "#Error".  
  
-   **Окно "свойства** " Используйте этот параметр для отображения значений свойств выбранного в данный момент элемента отчета в области конструктора. Чтобы увидеть свойства вложенных элементов отчета, щелкните элемент отчета несколько раз для перемещения по иерархии элементов отчета и всех его вложенных элементов. Проверьте имя элемента, показанное в верхней части панели свойств, чтобы узнать, свойства какого элемента отчета отображены в настоящий момент.  
  
-   **Панель элементов** Используйте этот параметр для вывода панели элементов.  
  
-   **Другие окна** Используйте этот параметр, чтобы отобразить следующую панель:  
  
    -   **Структура документа** Этот параметр используется для отображения иерархического представления элементов отчета и их коллекций текстовых полей в отчете.  
  
-   **Панели инструментов** Используйте этот параметр для отображения панелей инструментов, поддерживающих конструктор отчетовные функции, включая **границы отчета** и **Форматирование отчета**. Дополнительные сведения см. в разделе [Панели инструментов конструктора отчетов](#bkmk_ReportDesignerToolbars).  
  
-   **Данные отчета** Используйте этот параметр, чтобы отобразить область данных отчета, в которой можно добавить параметры отчета, источники данных, DataSets и изображения.  
  
###  <a name="ProjectMenu"></a>Меню "проект"  
 Меню **Проект** используется для управления общими источниками данных и отчетами проекта. При добавлении и удалении элементов отчета иерархическое представление элементов отчета в обозревателе решений обновляется автоматически.  
  
-   **Добавить новый элемент** Добавьте новый общий источник данных или новый отчет в проект.  
  
-   **Добавить существующий элемент** Добавление существующего общего источника данных или существующего отчета в проект.  
  
-   **Импорт отчетов** Импорт отчетов из другого приложения, например Microsoft Access.  
  
-   **Исключить из проекта** Исключите элементы из проекта. Этот параметр не удаляет файлы из файловой системы.  
  
-   **Отобразить все файлы** Отображение всех файлов в проекте.  
  
-   **Обновить элементы панели элементов проекта** Обновите кэш панели элементов при установке новых пользовательских элементов отчета в проекте.  
  
-   **Свойства** Откройте диалоговое окно **страницы свойств** для этого проекта. Дополнительные сведения см. в разделе [Диалоговое окно страниц свойств проекта](project-property-pages-dialog-box.md).  

##  <a name="bkmk_ReportDesignerToolbars"></a>конструктор отчетов панели инструментов  
 В конструкторе отчетов предусмотрены следующие специализированные панели инструментов для построения отчетов.  
  
-   **Отчет о** Добавьте верхний или нижний колонтитул, задайте свойства отчета, переключите линейку или панель группирования или используйте масштаб для изменения представления отчета.  
  
-   **Границы отчета** Задайте цвет, стиль и ширину для всех выбранных строк и границ всех выбранных элементов отчета.  
  
-   **Форматирование отчета** Задайте формат выбранных элементов отчета. Для текстовых полей с помощью этой панели инструментов можно изменить следующие виды форматирования: свойства шрифта, цвет текста, цвет фона, выравнивание текста.  
  
-   **Макет** Задает порядок отображения элементов отчета и объединение ячеек в области данных.  
  
-   **Стандартный выпуск** Открытие или сохранение проектов, отображение окон и выбор конфигурации отладки.  
  
 С помощью меню **Вид** можно управлять отображением этих панелей инструментов. Другие панели инструментов [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] могут быть отключены, если их возможности неприменимы к функциям конструктора отчетов.  

##  <a name="bkmk_SourceControl"></a>Система управления версиями  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]может интегрироваться с подключаемыми модулями источника. Используйте страницы "проекты и решения" в диалоговом окне " **Параметры** ", чтобы указать подключаемый модуль и настроить свойства.  
  
##  <a name="bkmk_CustomReportTemplates"></a>Пользовательские шаблоны отчетов  
 Чтобы использовать пользовательские отчеты в качестве шаблонов для создания новых отчетов просто скопируйте их в папку ReportProject на том компьютере, где установлена среда [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)] . По умолчанию эта папка находится в \<папке Drive>: \Program Files\Microsoft Visual Studio 10.0 \ Common7\IDE\Private ассемблиес\прожектитемс\репортпрожект. Когда в проект отчета добавляется новый элемент, пользовательский отчет отображается на панели «Шаблоны».  
  
 Можно также добавить пользовательские стили в мастер отчета.  

##  <a name="bkmk_CommandLineSupportForssdt"></a>Поддержка командной строки для SQL Server Data Tools  
 [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)]основывается на [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 10,0 и базовом приложении devenv. exe. Прежде чем использовать эти параметры, необходимо задать верное значение для следующих двух элементов.  
  
-   Свойства проекта для OverwriteDataSources, TargetDataSourceFolder, TargetReportFolder и TargetServerURL.  
  
-   Как минимум один набор свойств конфигурации, например, Debug или Release.  
  
 Дополнительные сведения см. в разделе [Publishing Data Sources and Reports](../reports/publishing-data-sources-and-reports.md).  
  
 Для проекта сервера отчетов необходимо задать следующие параметры в командной строке.  
  
-   **/deploy** Развертывание отчетов с помощью свойств проекта, указанных в файле конфигурации. Например, следующие команды выполняют развертывание отчетов, указанных в файле решения Reports.sln с использованием параметров конфигурации Release, которые заданы в свойствах проекта.  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /deploy "Release"  
    ```  
  
-   **/Build** Создайте файл решения, но не развертывайте его. Например, следующие команды создают отчеты, указанные в файле решения Reports.sln, с использованием параметров конфигурации Debug, которые заданы в свойствах проекта.  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /build "Debug"  
    ```  
  
-   **/out** Перенаправьте выходные данные, созданные при построении решения, в указанный файл. Например, следующая команда перенаправляет вывод из сборки, созданной в предыдущем примере, в файл mybuildlog.txt.  
  
    ```  
    devenv.exe "C:\Users\MyUser\Documents\Visual Studio 2010\Projects\Reports\Reports.sln" /build "Debug" /out mybuildlog.txt  
    ```  

##  <a name="bkmk_KeyboardShortcuts"></a>Сочетания клавиш в Reporting Services  
 Сочетания клавиш можно использовать для следующих действий.  
  
-   Управление окнами и режимами в среде [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)].  
  
    |Description|Сочетание клавиш|  
    |-----------------|---------------------|  
    |Выполнить сборку выбранного проекта|CTRL + SHIFT + B|  
    |Открыть окно «Свойства»|F4|  
    |Открыть окно «Данные»|CTRL + Alt + D|  
    |Запуск отладки|F5|  
    |Переместиться от одного открытого окна к следующему|F6,|  
  
-   Управление элементами в области конструктора отчета.  
  
    |Description|Сочетание клавиш|  
    |-----------------|---------------------|  
    |Переместить фокус с элемента отчета на следующий элемент отчета|TAB|  
    |Переместить выбранный элемент отчета|Клавиши со стрелками|  
    |Сдвинуть выбранный элемент отчета|CTRL + клавиши со стрелками|  
    |Увеличить или уменьшить размер выбранного элемента отчета|CTRL + SHIFT + клавиши со стрелками|  
    |В текстовом поле переместить курсор в начало отображаемого текста, который является видимым|CTRL + HOME|  
    |В текстовом поле переместить курсор в конец отображаемого текста, который является видимым|CTRL + END|  
    |В текстовом поле выбрать текст от текущей позиции курсора до начала отображаемого текста, который является видимым|SHIFT + HOME|  
    |В текстовом поле выбрать текст от текущей позиции курсора до конца отображаемого текста, который является видимым|SHIFT + END|  
    |В текстовом поле выбрать текст от текущей позиции курсора до начала выражения|CTRL + SHIFT + HOME|  
    |В текстовом поле выбрать текст от текущей позиции курсора до конца выражения|CTRL + SHIFT + END|  
    |Открыть контекстное меню для выбранного элемента отчета|SHIFT + F10 + клавиша свойств на новых клавиатурах|  

## <a name="see-also"></a>См. также:  
 [обозреватель решений](../../ssms/solution/solution-explorer.md)   
 [Отчеты Reporting Services &#40;SSRS&#41;](../reports/reporting-services-reports-ssrs.md)   
 [Язык определения отчетов &#40;службы SSRS&#41;](../reports/report-definition-language-ssrs.md)   
 [Развертывание и поддержка версий в службах SQL Server Data Tools &#40;SSRS&#41;](deployment-and-version-support-in-sql-server-data-tools-ssrs.md)  
  
  
