---
title: sp_bindsession (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_bindsession
- sp_bindsession_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_bindsession
ms.assetid: 1436fe21-ad00-4a98-aca1-1451a5e571d2
author: stevestein
ms.author: sstein
ms.openlocfilehash: fac327d88aa8a6d74e153c1c7b2f3d637bf6f936
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68046021"
---
# <a name="sp_bindsession-transact-sql"></a>sp_bindsession (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Привязывает или отменяет привязку сеанса к другим сеансам в том же экземпляре [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssDE](../../includes/ssde-md.md)]. Привязывание сеансов позволяет двум и более сеансам участвовать в одной транзакции и общих блокировках, пока выполняется ROLLBACK TRANSACTION или COMMIT TRANSACTION.  
  
> [!IMPORTANT]  
>  
  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] Используйте режим MARS или распределенные транзакции. Дополнительные сведения см. в статье [Использование множественных активных результирующих наборов &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_bindsession { 'bind_token' | NULL }  
```  
  
## <a name="arguments"></a>Аргументы  
 **"** *bind_token* **"**  
 Токен, идентифицирующий транзакцию, первоначально полученную с помощью **sp_getbindtoken** или функции **Srv_getbindtoken** Open Data Services. *bind_token*имеет тип **varchar (255)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="remarks"></a>Remarks  
 Два объединенных сеанса совместно используют только транзакции и блокировки. Каждый сеанс сохраняет свой собственный уровень изоляции, и установка нового уровня изоляции на одном сеансе не затронет уровень изоляции другого сеанса. Каждый сеанс идентифицируется по его учетной записи безопасности и может обращаться только к тем ресурсам базы данных, на которые учетной записи предоставлены разрешения.  
  
 **sp_bindsession** использует маркер привязки для привязки двух или более существующих сеансов клиента. Эти сеансы клиента должны быть на одном экземпляре компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], от которого был получен токен связывания. Сеанс — это клиент, выполняющий команду. Привязанные сеансы баз данных совместно используют пространство транзакций и блокировок.  
  
 Токен связывания, полученный от одного экземпляра компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)], не может использоваться для сеанса клиента, подключенного к другому экземпляру, даже для транзакций DTC. Токен связывания допустим только локально внутри каждого экземпляра и не может совместно использоваться множеством экземпляров. Чтобы привязать клиентские сеансы к другому [!INCLUDE[ssDE](../../includes/ssde-md.md)]экземпляру, необходимо получить другой маркер привязки, выполнив **sp_getbindtoken**.  
  
 **sp_bindsession** завершится ошибкой, если он использует неактивный токен.  
  
 Отменяйте привязку сеанса с помощью **sp_bindsession** без указания *bind_token* или путем передачи значения NULL в *bind_token*.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере указанный токен привязки привязывается к текущему сеансу.  
  
> [!NOTE]  
>  Токен привязки, показанный в примере, был получен путем запуска **sp_getbindtoken** перед выполнением **sp_bindsession**.  
  
```  
USE master;  
GO  
EXEC sp_bindsession 'BP9---5---->KB?-V'<>1E:H-7U-]ANZ';  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sp_getbindtoken (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-getbindtoken-transact-sql.md)   
 [API srv_getbindtoken &#40;расширенных хранимых процедур&#41;](../../relational-databases/extended-stored-procedures-reference/srv-getbindtoken-extended-stored-procedure-api.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
