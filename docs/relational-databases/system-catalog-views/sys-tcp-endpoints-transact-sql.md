---
title: sys. tcp_endpoints (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7e4b711a7d36e7677f6f32b87ff4c696db231730
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68116730"
---
# <a name="systcp_endpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Содержит по одной строке для каждой из конечных точек TCP, имеющихся в системе. Конечные точки, описанные в статье **sys. tcp_endpoints** , предоставляют объект для предоставления и отзыва привилегий подключения. Отображаемые сведения о портах и IP-адресах не используются для настройки протоколов и могут не соответствовать фактической конфигурации протоколов. Для просмотра и настройки протоколов следует использовать диспетчер конфигурации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**< наследуемые столбцы>**||Наследует столбцы из представления [sys. Endpoints](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md).|  
|**порту**|INT|Номер порта, который прослушивается конечной точкой. Не допускает значение NULL.|  
|**is_dynamic_port**|bit|1 = Номер порта назначается динамически.<br /><br /> Не допускает значение NULL.|  
|**ip_address**|**nvarchar (45)**|IP-адрес средства прослушивания, указанный в предложении LISTENER_IP. Допускает значение NULL.|  
  
## <a name="remarks"></a>Remarks  
 Выполните следующий запрос для сбора сведений о конечных точках и соединениях. Конечные точки без текущих соединений или соединений TCP будут отображены со значениями NULL. Добавьте `WHERE des.session_id = @@SPID` предложение **WHERE** , чтобы получить сведения о текущем соединении.  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>Разрешения  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]Дополнительные сведения см. в разделе [Настройка видимости метаданных](../../relational-databases/security/metadata-visibility-configuration.md).  
  
## <a name="see-also"></a>См. также:  
 [Представления каталога (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [Представления каталога конечных точек &#40;&#41;Transact-SQL](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
