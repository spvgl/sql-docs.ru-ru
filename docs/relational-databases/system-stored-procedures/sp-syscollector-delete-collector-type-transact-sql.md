---
title: sp_syscollector_delete_collector_type (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_delete_collector_type
- sp_syscollector_delete_collector_type_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_delete_collector_type
ms.assetid: 3f32905e-0005-42cb-aef1-7bd04c51fbac
author: stevestein
ms.author: sstein
ms.openlocfilehash: c22170fff456a2ed65c295a1974539da20499c52
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68000871"
---
# <a name="sp_syscollector_delete_collector_type-transact-sql"></a>sp_syscollector_delete_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Удаляет определение типа сборщика.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_delete_collector_type [[ @collector_type_uid = ] 'collector_type_uid' ]  
          , [[ @name = ] 'name' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @collector_type_uid = ] 'collector_type_uid'`Идентификатор GUID для типа сборщика. *collector_type_uid* имеет тип **uniqueidentifier** и должен иметь значение, если *Name* имеет значение null.  
  
`[ @name = ] 'name'`Имя типа сборщика. Аргумент *Name* имеет тип **sysname** и должен иметь значение, если *collector_type_uid* имеет значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Либо *collector_type_uid* , либо *имя* должны иметь значение, которое не может быть null.  
  
 Эта процедура вызовет ошибку, если существуют элементы сбора этого типа сборщика.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных **dc_admin** (с разрешением EXECUTE).  
  
## <a name="example"></a>Пример  
 В этом примере удаляется тип сборщика «Универсальный запрос T-SQL».  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_delete_collector_type @collector_type_uid = '302E93D1-3424-4be7-AA8E-84813ECF2419';  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  
