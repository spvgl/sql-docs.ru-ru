---
title: Диалоговое окно "свойства каталога" | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.ssms.iscatalogprop.general.f1
- sql12.ssis.ssms.iscreatecatalog.f1
ms.assetid: 3e2fcf11-e010-41c6-bc26-e4b281c0bfbc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 8d3492cce19906322ef9b420718aae0ae9e0e62d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66061105"
---
# <a name="catalog-properties-dialog-box"></a>Диалоговое окно свойств каталога
  Диалоговое окно свойств каталога служит для настройки каталога SSISDB. Свойства каталога определяют, как конфиденциальные данные шифруются, как сохранены данные операций и версий проекта, а затем время ожидания операций проверки. Каталог SSISDB — это центральная точка хранения и администрирования для [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] проектов, пакетов, параметров и сред.  
  
 Свойства каталога можно также просмотреть в представлении catalog.catalog_property и задать эти свойства с помощью хранимой процедуры catalog.configure_catalog. Дополнительные сведения см. в разделах [catalog.catalog_properties (база данных SSISDB)](/sql/integration-services/system-views/catalog-catalog-properties-ssisdb-database) и [catalog.configure_catalog (база данных SSISDB)](/sql/integration-services/system-stored-procedures/catalog-configure-catalog-ssisdb-database).  
  
 Дополнительные сведения о создании каталога SSISDB см. в разделе [Создание каталога служб SSIS](catalog/ssis-catalog.md).  
  
 **Что необходимо сделать?**  
  
-   [Открытие диалогового окна «Свойства каталога»](#open_dialog)  
  
-   [Настройка параметров](#options)  
  
##  <a name="open_dialog"></a>Открытие диалогового окна «Свойства каталога»  
  
1.  Откройте среду [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].  
  
2.  Создайте соединение с компонентом Microsoft SQL Server Database Engine.  
  
3.  В обозревателе объектов разверните узел **Службы Integration Services** , щелкните правой кнопкой мыши элемент **SSISDB**и выберите пункт **Свойства**.  
  
##  <a name="options"></a>Настройка параметров  
  
### <a name="options"></a>Параметры  
 В следующей таблице описаны некоторые свойства, определенные в диалоговом окне, а также соответствующие свойства в представлении catalog.catalog_property.  
  
|Имя свойства (диалоговое окно свойств каталога)|Имя свойства (представление catalog.catalog_property)|Description|  
|-----------------------------------------------------|------------------------------------------------------|-----------------|  
|Имя алгоритма шифрования|ENCRYPTION_CLEANUP_ENABLED|Указывает тип шифрования, который используется при шифровании значений конфиденциальных параметров каталога. Допустимы следующие значения:<br /><br /> **DES**<br /><br /> **TRIPLE_DES**<br /><br /> **TRIPLE_DES_3KEY**<br /><br /> **DESPX**<br /><br /> **AES_128**<br /><br /> **AES_192**<br /><br /> **AES_256** (по умолчанию)|  
|Время ожидания проверки (в секундах)|VALIDATION_TIMEOUT|Задайте максимальное время в секундах, в течение которого может выполняться операция проверки проекта или пакета до того, как будет остановлена. Значение по умолчанию — 300 секунд.<br /><br /> Выполнение проверки является асинхронной операцией. Чем больше проект или пакет, тем больше времени необходимо для проверки.<br /><br /> Дополнительные сведения о проверке проектов и пакетов см. в разделе [Integration Services Data Types in Expressions](expressions/integration-services-data-types-in-expressions.md).|  
|Периодическая очистка журналов|OPERATION_CLEANUP_ENABLED|Установите это свойство в значение True, чтобы указать, что задание агента SQL Server по очистке операций выполняется. В противном случае установите свойство в значение False.|  
|Срок хранения (в днях)|RETENTION_WINDOW|Задайте максимальный срок хранения данных о допустимых операциях (в днях). Данные, которые хранятся дольше указанного числа дней, удаляются заданием агента SQL Server по очистке операций.|  
|Максимальное количество версий в проекте|MAX_PROJECT_VERSIONS|Укажите, сколько версий проекта будет храниться в каталоге. Когда общее количество версий превышает максимальное значение, более ранние версии проектов удаляются при выполнении задания по очистке версий проекта.|  
  
  
