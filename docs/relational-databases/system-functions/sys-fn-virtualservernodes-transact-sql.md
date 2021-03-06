---
title: sys. fn_virtualservernodes (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_virtualservernodes
- fn_virtualservernodes_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- nodes [Faillover Clustering], virtual servers
- nodes [Faillover Clustering]
- virtual servers [Faillover Clustering]
- failover clustering [SQL Server], nodes
- fn_virtualservernodes function
- sys.fn_virtualservernodes function
ms.assetid: 257f3b8d-93c0-4444-87f1-ea211bd8cad0
author: rothja
ms.author: jroth
monikerRange: '>=aps-pdw-2016||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: da218e1afeec389d69b1727160a420c889225783
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059198"
---
# <a name="sysfn_virtualservernodes-transact-sql"></a>sys.fn_virtualservernodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-pdw-md.md)]

  Возвращает список узлов экземпляров с отказоустойчивом кластером, на которых может запускаться экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти сведения полезны в средах отказоустойчивой кластеризации.  
  
> [!IMPORTANT]
>  Эта [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] системная функция включена для обеспечения обратной совместимости. Вместо этого рекомендуется использовать [sys. dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md) .  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_virtualservernodes()  
```  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Если текущий сервер является кластерным сервером, **fn_virtualservernodes** возвращает список узлов экземпляра кластера отработки отказа, на которых был [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] определен данный экземпляр.  
  
 Если текущий экземпляр сервера не является кластерным сервером, **fn_virtualservernodes** возвращает пустой набор строк.  
  
## <a name="permissions"></a>Разрешения  
 Пользователь должен иметь разрешение VIEW SERVER STATE на экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="examples"></a>Примеры  
 В следующем примере функция `fn_virtualservernodes` используется для запроса на кластеризованном экземпляре сервера:  
  
```  
SELECT * FROM fn_virtualservernodes();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 NodeName  
  
 -------\-  
  
 SS3-CLUSN1  
  
 SS3-CLUSN2  
  
## <a name="see-also"></a>См. также:  
 [sys. dm_os_cluster_nodes &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-nodes-transact-sql.md)   
 [sys. fn_servershareddrives &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-servershareddrives-transact-sql.md)  
  
  
