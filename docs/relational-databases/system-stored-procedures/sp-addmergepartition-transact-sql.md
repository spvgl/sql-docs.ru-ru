---
title: sp_addmergepartition (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepartition
- sp_addmergepartition_TSQL
helpviewer_keywords:
- sp_addmergepartition
ms.assetid: 02a5f46b-e5ff-4932-a3ff-7f0fd82d0981
author: stevestein
ms.author: sstein
ms.openlocfilehash: 21e9d91978a01152f22d18f03fa54bf29b776b8a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68769169"
---
# <a name="sp_addmergepartition-transact-sql"></a>sp_addmergepartition (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Создает динамически фильтруемую секцию для подписки, которая фильтруется по значениям [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) или [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. Данная хранимая процедура выполняется на издателе публикуемой базы данных и используется для создания секций вручную.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_addmergepartition [ @publication = ] 'publication'  
        , [ @suser_sname = ] 'suser_sname'  
        , [ @host_name = ] 'host_name'  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Публикация слиянием, в которой создается секция. Аргумент *publication* имеет тип **sysname**и не имеет значения по умолчанию. Если указан параметр *SUSER_SNAME* , значение *HostName* должно быть равно null.  
  
`[ @suser_sname = ] 'suser_sname'`Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md) на подписчике. Аргумент *SUSER_SNAME* имеет тип **sysname**и не имеет значения по умолчанию.  
  
`[ @host_name = ] 'host_name'`Значение, используемое при создании секции для подписки, которая фильтруется по значению функции [HOST_NAME](../../t-sql/functions/host-name-transact-sql.md) на подписчике. Аргумент *HOST_NAME* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_addmergepartition** используется в репликации слиянием.  
  
## <a name="example"></a>Пример  
 [!code-sql[HowTo#sp_MergeDynamicPubPlusPartition](../../relational-databases/replication/codesnippet/tsql/sp-addmergepartition-tra_1.sql)]  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_addmergepartition**.  
  
## <a name="see-also"></a>См. также:  
 [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)   
 [Параметризованные фильтры строк](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)  
  
  
