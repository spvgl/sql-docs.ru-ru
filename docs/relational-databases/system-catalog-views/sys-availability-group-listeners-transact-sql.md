---
title: sys. availability_group_listeners (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- availability_group_listeners_TSQL
- sys.availability_group_listeners
- sys.availability_group_listeners_TSQL
- availability_group_listeners
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_group_listeners catalog view
- Availability Groups [SQL Server], listeners
ms.assetid: b5e7d1fb-3ffb-4767-8135-604c575016b1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b363e410f35eb7880933520dd1dbf47f258b651e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68041060"
---
# <a name="sysavailability_group_listeners-transact-sql"></a>sys.availability_group_listeners (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Для каждой группы доступности AlwaysOn не возвращает ни одной строки, указывая на то, что с группой доступности не связаны имена сети, либо возвращает по одной строке для каждой конфигурации прослушивателей групп доступности в кластере WSFC. Это представление отображает получаемые из кластера в реальном времени сведения о конфигурации.  
  
> [!NOTE]  
>  В этом представлении каталога не описывается подробно конфигурация IP-адресов, заданная в кластере WSFC.  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**UNIQUEIDENTIFIER**|Идентификатор группы доступности (**group_id**) из [sys. availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md).|  
|**listener_id**|**nvarchar (36)**|Идентификатор GUID из идентификатора ресурса кластера.|  
|**dns_name**|**nvarchar (63)**|Настроенное сетевое имя (hostname) прослушивателя группы доступности.|  
|**порту**|**int**|Номер TCP-порта, заданного для прослушивателя группы доступности.<br /><br /> NULL = прослушиватель настроен вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], его номер порта не был добавлен в группу доступности. Чтобы добавить порт, плеасеусе параметр modify Listener инструкции [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] .|  
|**is_conformant**|**bit**|Соответствует ли стандартам эта конфигурация IP-адресов, одно из следующих значений:<br /><br /> 1 = прослушиватель соответствует стандартам. Между IP-адресами существует только отношение "или". *Согласование* охватывает каждую IP-конфигурацию, созданную инструкцией [CREATE Availability Group](../../t-sql/statements/create-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)] . Кроме того, если конфигурация IP-адресов была создана вне [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], например с помощью диспетчера отказоустойчивого кластера WSFC (но ее можно изменить с помощью инструкции ALTER AVAILABILITY GROUP), то конфигурация IP-адресов считается соответствующей стандартам.<br /><br /> 0 = прослушиватель не соответствует стандартам. Как правило, это указывает на наличие IP-адреса, который не удалось настроить с помощью команд [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и который вместо этого был определен непосредственно в кластере WSFC.|  
|**ip_configuration_string_from_cluster**|**nvarchar(max)**|Строки конфигурации IP-адресов кластера для этого прослушивателя, если они имеются. NULL = прослушиватель не имеет виртуальных IP-адресов. Пример:<br /><br /> IPv4-адрес `65.55.39.10`:.<br /><br /> IPv6-адрес:`2001::4898:23:1002:20f:1fff:feff:b3a3`|  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Always On динамические административные представления и функции групп доступности &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Always On представления каталога групп доступности &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Мониторинг групп доступности &#40;&#41;Transact-SQL](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [Always On группы доступности &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
