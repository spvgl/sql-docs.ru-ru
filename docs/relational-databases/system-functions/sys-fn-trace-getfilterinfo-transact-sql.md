---
title: sys. fn_trace_getfilterinfo (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_trace_getfilterinfo
- fn_trace_getfilterinfo_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], filters
- sys.fn_trace_getfilterinfo function
- filters [SQL Server], traces
- fn_trace_getfilterinfo function
ms.assetid: 09fe4a28-ff8a-4655-9da1-4654d5bc514d
author: rothja
ms.author: jroth
ms.openlocfilehash: 22b1b6bf2abbf322cec690d9e466f2ea40fcb72a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68059249"
---
# <a name="sysfn_trace_getfilterinfo-transact-sql"></a>sys.fn_trace_getfilterinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о фильтрах, примененных к указанной трассировке.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]Вместо этого используйте Расширенные события.  
  
 
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
fn_trace_getfilterinfo ( trace_id )  
```  
  
## <a name="arguments"></a>Аргументы  
 *trace_id*  
 Идентификатор трассировки. *trace_id* имеет **тип int**и не имеет значения по умолчанию.  
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
 Возвращает следующие данные. Дополнительные сведения о столбцах см. в разделе [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md).  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**columnid**|**int**|Идентификатор столбца, к которому применяется фильтр.|  
|**logical_operator**|**int**|Указывает, какой применяется оператор: AND или OR.|  
|**comparison_operator**|**int**|Задает тип сравнения.<br /><br /> 0 = равны.<br /><br /> 1 = не равны.<br /><br /> 2 = больше чем.<br /><br /> 3 = меньше чем.<br /><br /> 4 = больше или равно.<br /><br /> 5 = меньше или равно.<br /><br /> 6 = схожи.<br /><br /> 7 = не схожи.|  
|**значений**|**sql_variant**|Задает значение, к которому применяется фильтр.|  
  
## <a name="remarks"></a>Remarks  
 Пользователь задает *trace_id* значение для обнаружения, изменения и управления трассировкой. При передаче идентификатора определенной трассировки **fn_trace_getfilterinfo** возвращает сведения о любом фильтре этой трассировки. Если к указанной трассировке не применяются фильтры, функция возвращает пустой набор строк. Если передать недопустимый идентификатор, эта функция вернет пустой набор строк. Аналогичные сведения о трассировках см. в разделе [sys. fn_trace_getinfo &#40;&#41;Transact-SQL ](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение ALTER TRACE на сервере.  
  
## <a name="examples"></a>Примеры  
 В следующем примере возвращаются сведения обо всех фильтрах, применяемых к трассировке 2.  
  
```  
SELECT * FROM fn_trace_getfilterinfo(2) ;  
GO  
  
```  
  
## <a name="see-also"></a>См. также:  
 [Создание &#40;трассировки&#41;Transact-SQL](../../relational-databases/sql-trace/create-a-trace-transact-sql.md)   
 [sp_trace_setfilter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setfilter-transact-sql.md)   
 [sp_trace_create &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-create-transact-sql.md)   
 [sp_trace_generateevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-generateevent-transact-sql.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [sp_trace_setstatus &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setstatus-transact-sql.md)   
 [sys. fn_trace_geteventinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-geteventinfo-transact-sql.md)   
 [sys. fn_trace_getinfo &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-getinfo-transact-sql.md)   
 [sys. fn_trace_gettable &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-trace-gettable-transact-sql.md)  
  
  
