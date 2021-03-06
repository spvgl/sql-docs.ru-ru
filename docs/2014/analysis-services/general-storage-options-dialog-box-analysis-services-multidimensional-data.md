---
title: Общие (диалоговое окно "Параметры хранилища") (Analysis Services-многомерные данные) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.cubeeditor.partitiondesigner.partitionstoragesettings.setstorageoptions.storage.f1
ms.assetid: ee1fac79-ae15-4c3c-9a98-33db04388817
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3c7ddd5311232ae12b3eb9f66adc0cd1f5714b32
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "66081010"
---
# <a name="general-storage-options-dialog-box-analysis-services---multidimensional-data"></a>Общие (диалоговое окно «Параметры хранилища») (службы Analysis Services — многомерные данные)
  Воспользуйтесь вкладкой **Общие** диалогового окна **Параметры хранилища** в среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] для установки режима хранения и настроек упреждающего кэширования измерения, куба, группы мер или секции.  
  
> [!NOTE]  
>  Для изменения этих настроек необходимо ознакомиться с режимами хранения и функциональными возможностями упреждающего кэширования. Дополнительные сведения см. в разделе [Упреждающее кэширование (секции)](multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md).  
  
## <a name="options"></a>Параметры  
  
|Термин|Определение|  
|----------|----------------|  
|**Режим хранения**|Выбирает режим хранения, используемый для этого объекта.<br /><br /> **MOLAP**<br /> Объект использует многомерное хранилище OLAP (MOLAP).<br /><br /> **HOLAP**<br /> Объект использует смешанное хранилище OLAP (MOLAP).<br /><br /> **ROLAP**<br /> Объект использует реляционное хранилище OLAP (ROLAP).|  
|**Разрешить упреждающее кэширование**|Включает упреждающее кэширование.<br /><br /> Примечание. Если этот параметр не выбран, все параметры, кроме параметра **Режим хранения** , отключены.|  
|**Обновлять кэш по мере изменения данных**|Использует метод уведомления, выбранный на вкладке **Уведомления**, для обновления образа MOLAP объекта при получении извещения. Дополнительные сведения о вкладке **Уведомления** см. в разделе [Уведомления (диалоговое окно "Параметры хранилища") (службы Analysis Services — многомерные данные)](notifications-storage-options-dialog-analysis-services-multidimensional-data.md).<br /><br /> Примечание. Этот параметр отключен, если не выбран параметр **Разрешить упреждающее кэширование**.|  
|**Интервал бездействия**|Устанавливает минимальный интервал и единицы времени, в течение которого не должно происходить никакой активности объекта, пока упреждающее кэширование не начнет создание нового образа MOLAP объекта.<br /><br /> Примечание. Этот параметр отключен, если не установлен параметр **Обновлять кэш по мере изменения данных**.|  
|**Интервал прерывания бездействия**|Устанавливает максимальный интервал и единицы измерения времени, в течение которого после получения уведомления для объекта начинается упреждающее кэширование, создающее новый образ MOLAP объекта, независимо от текущей активности объекта. Уведомления, полученные после достижения этого интервала, не отменяют обработку образа MOLAP, запущенную во время этого интервала.<br /><br /> Примечание. Этот параметр отключен, если не установлен параметр **Обновлять кэш по мере изменения данных**. Также обратите внимание, что этот параметр не следует задавать, если для **режима хранения** задано значение **HOLAP**.|  
|**Очистить устаревший кэш**|Определяет период между началом создания нового кэша MOLAP и удалением существующего кэша MOLAP.<br /><br /> Примечание. Этот параметр отключен, если не выбран параметр **Разрешить упреждающее кэширование**. Также обратите внимание, что этот параметр не следует задавать, если для **режима хранения** задано значение HOLAP.|  
|**Latency**|Определяет интервал и единицы измерения времени периода между началом создания нового кэша MOLAP и удалением существующего кэша MOLAP.<br /><br /> Примечание. Этот параметр отключен, если не установлен параметр **Очистить устаревший кэш**. Также обратите внимание, что этот параметр не следует задавать, если для **режима хранения** задано значение **HOLAP**.|  
|**Периодически обновлять кэш**|Регулярно обновляет образ MOLAP, независимо от уведомления.<br /><br /> Примечание. Этот параметр отключен, если не выбран параметр **Разрешить упреждающее кэширование**. Также обратите внимание, что этот параметр не следует задавать, если для **режима хранения** задано значение **HOLAP**.|  
|**Интервал перестроения**|Выбирает интервал и единицы измерения времени для периода, в течение которого после создания [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] нового образа MOLAP запускает процесс обработки образа MOLAP для объекта, независимо от уведомления. Уведомления, полученные после достижения этого интервала, не отменяют обработку образа MOLAP, запущенную во время этого интервала.<br /><br /> Примечание. Этот параметр отключен, если не выбран параметр **Периодически обновлять кэш**. Также обратите внимание, что этот параметр не следует задавать, если для **режима хранения** задано значение **HOLAP**.|  
|**Немедленно соединиться**|Немедленно переводит объекты в режим в сети. Если этот параметр установлен, объекты используют базовое хранилище ROLAP для разрешения запросов во время пересоздания кэша MOLAP. Если этот параметр не установлен, объекты переходят в режим в сети только после завершения создания кэша MOLAP объектов.|  
|**Разрешить агрегаты ROLAP**|Использует материализованные представления, на котором основывается базовый источник данных для хранения статистических функций.<br /><br /> Примечание. Если базовый источник данных не поддерживает материализованные представления, при обработке объекта происходит ошибка.|  
|**Применить установки к измерениям**|Применяет режим хранения и настройки упреждающего кэширования к связанным измерениям.|  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно "Параметры хранилища" &#40;Analysis Services многомерных данных&#41;](storage-options-dialog-box-analysis-services-multidimensional-data.md)   
 [Уведомления &#40;диалоговое окно "Параметры хранилища"&#41; &#40;Analysis Services многомерных данных&#41;](notifications-storage-options-dialog-analysis-services-multidimensional-data.md)  
  
  
