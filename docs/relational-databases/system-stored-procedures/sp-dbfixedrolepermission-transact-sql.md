---
title: sp_dbfixedrolepermission (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dbfixedrolepermission
- sp_dbfixedrolepermission_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dbfixedrolepermission
ms.assetid: b8c30191-f532-49cd-83f3-c271f63ce572
author: stevestein
ms.author: sstein
ms.openlocfilehash: 91a7278230a0e7201e78354a38af58f417ac26ce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108157"
---
# <a name="sp_dbfixedrolepermission-transact-sql"></a>sp_dbfixedrolepermission (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает разрешения предопределенной роли базы данных. **sp_dbfixedrolepermission** возвращает правильные сведения в [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]. Изменения в иерархии разрешений, реализованные в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], не отражаются. Дополнительные сведения см. в разделе[разрешения &#40;ядро СУБД&#41;](../../relational-databases/security/permissions-database-engine.md).  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_dbfixedrolepermission [ [ @rolename = ] 'role' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @rolename = ] 'role'`Имя допустимой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предопределенной роли базы данных. Аргумент *Role* имеет тип **sysname**и значение по умолчанию NULL. Если *роль* не указана, отображаются разрешения для всех предопределенных ролей базы данных.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**DbFixedRole**|**имеет sysname**|Имя предопределенной роли базы данных|  
|**Разрешение**|**nvarchar (70)**|Разрешения, связанные с **дбфикседроле**|  
  
## <a name="remarks"></a>Remarks  
 Чтобы отобразить список предопределенных ролей базы данных, выполните **sp_helpdbfixedrole**. В следующей таблице представлены предопределенные роли базы данных.  
  
|Предопределенная роль базы данных|Description|  
|-------------------------|-----------------|  
|**db_owner**|Владельцы базы данных|  
|**db_accessadmin**|Администраторы доступа к базе данных|  
|**db_securityadmin**|Администраторы безопасности базы данных|  
|**db_ddladmin**|Администраторы языка определения данных (DDL)|  
|**db_backupoperator**|Операторы резервного копирования базы данных|  
|**db_datareader;**|Модули чтения данных из базы данных|  
|**db_datawriter.**|Модули записи данных в базу данных|  
|**db_denydatareader**|Модули чтения данных из базы данных, которым отказано в доступе|  
|**db_denydatawriter**|Модули записи данных в базу данных, которым отказано в доступе|  
  
 Члены предопределенной роли базы данных **db_owner** имеют разрешения всех других предопределенных ролей базы данных. Чтобы отобразить разрешения для предопределенных ролей сервера, выполните **sp_srvrolepermission**.  
  
 В результирующий набор входят инструкции языка [!INCLUDE[tsql](../../includes/tsql-md.md)], которые могут быть выполнены, и другие особые действия, которые могут быть выполнены членами роли базы данных.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
 Следующий запрос возвращает разрешения для всех предопределенных ролей базы данных, так как не указывает предопределенную роль базы данных.  
  
```  
EXEC sp_dbfixedrolepermission;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Хранимые процедуры безопасности &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droprolemember-transact-sql.md)   
 [sp_helpdbfixedrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdbfixedrole-transact-sql.md)   
 [sp_srvrolepermission &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-srvrolepermission-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
