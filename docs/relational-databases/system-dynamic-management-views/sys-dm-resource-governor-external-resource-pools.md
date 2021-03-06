---
title: sys. dm_resource_governor_external_resource_pools (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 07/24/2019
ms.prod: sql
ms.technology: machine-learning
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_resource_governor_external_resource_pools_TSQL
- sys.dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools
- dm_resource_governor_external_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- dm_resource_governor_external_resource_pools
- sys.dm_resource_governor_external_resource_pools
author: dphansen
ms.author: davidph
manager: cgronlun
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: cf77a073a1432df839bfd13046c66018496e79f1
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68468513"
---
# <a name="sysdm_resource_governor_external_resource_pools-transact-sql"></a>sys. dm_resource_governor_external_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss-xxxx-xxxx-xxx-md.md)]

Возвращает сведения о текущем состоянии внешнего пула ресурсов, текущую конфигурацию пулов ресурсов и статистику пула ресурсов. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md).  
  
|Имя столбца      |Тип данных      |Description|  
|----------------|---------------|-----------------| 
| external_pool_id|**int**|Идентификатор пула ресурсов. Не допускает значение NULL. |
| name|**имеет sysname**|Имя пула ресурсов. Не допускает значение NULL. 
| pool_version|**int**|Внутренний номер версии.|
| max_cpu_percent|**int**|Текущая конфигурация максимальной средней пропускной способности ЦП, разрешенной для всех запросов в пуле ресурсов при возникновении состязания использования ЦП. Не допускает значение NULL. |
| max_processes|**int**|Максимальное количество одновременных внешних процессов. Значение по умолчанию равно 0 и означает отсутствие ограничений. Не допускает значение NULL.|
| max_memory_percent|**int**|Текущая конфигурация процентной доли от общего объема памяти сервера, которая может использоваться для запросов в данном пуле ресурсов. Не допускает значение NULL. |
| statistics_start_time|**datetime**|Время, когда была очищена статистика для данного пула. Не допускает значение NULL. 
| peak_memory_kb|**bigint**|Максимальный объем используемой памяти (в килобайтах) для пула ресурсов. Не допускает значение NULL. |
| write_io_count|**int**|Общая сумма выполненных операций ввода-вывода записи с момента сброса регулятора ресурсов. Не допускает значение NULL. |
| read_io_count|**int**|Общая сумма выполненных операций ввода-вывода с момента сброса регулятора ресурсов. Не допускает значение NULL. |
| total_cpu_kernel_ms|**bigint**|Общее время ядра пользователя ЦП (в миллисекундах), прошедшее с момента сброса статистики сброса регулятора ресурсов. Не допускает значение NULL. |
| total_cpu_user_ms|**bigint**|Совокупное время пользователя ЦП в миллисекундах, прошедшее с момента сброса статистики сброса регулятора ресурсов. Не допускает значение NULL. |
| active_processes_count|**int**|Количество внешних процессов, выполняемых в момент запроса. Не допускает значение NULL. |

 
## <a name="permissions"></a>Разрешения

Требуется разрешение `VIEW SERVER STATE`.

## <a name="see-also"></a>См. также:  
 [sys. dm_resource_governor_external_resource_pool_affinity &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-external-resource-pool-affinity-transact-sql.md)  
  
  
