---
title: Использование CacheSize | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- locks [ADO], CacheSize property
- CacheSize property [ADO]
ms.assetid: ca1c3422-b6a4-4ba6-af55-54f975b698b1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2e3a67e9ad0f1f26f804ecb38e960041863fad9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67923578"
---
# <a name="using-cachesize"></a>Using CacheSize
Свойство **CacheSize** используется для управления количеством записей, получаемых за один раз в локальную память от поставщика. Например, если **CacheSize** имеет значение 10, после первого открытия объекта **Recordset** поставщик получает первые 10 записей в локальную память. При перемещении по объекту **Recordset** поставщик возвращает данные из буфера локальной памяти. Как только вы перейдете за последнюю запись в кэше, поставщик извлекает следующие 10 записей из источника данных в кэш.  
  
> [!NOTE]
>  **CacheSize** основан на максимальном свойстве, специфическом для поставщика **открытых строк** (в коллекции **свойств** объекта **Recordset** ). Нельзя задать для **CacheSize** значение, превышающее **Максимальное число открытых строк.** Чтобы изменить количество строк, которые могут быть открыты поставщиком, установите **Максимальное число открытых строк**.  
  
 Значение **CacheSize** можно скорректировать в течение жизненного цикла объекта **Recordset** , но изменение этого значения влияет только на количество записей в кэше после последующих извлечений из источника данных. Изменение только значения свойства не приведет к изменению текущего содержимого кэша.  
  
 Если число записей для получения меньше, чем **CacheSize** , поставщик возвращает оставшиеся записи и не выдает ошибку.  
  
 Нулевой параметр **CacheSize** не допускается и возвращает ошибку.  
  
 Записи, полученные из кэша, не отображают параллельные изменения, внесенные другими пользователями в исходные данные. Чтобы принудительно обновить все кэшированные данные, используйте метод [Resync](../../../ado/reference/ado-api/resync-method.md) .  
  
 Если для **CacheSize** задано значение больше 1, методы навигации ([Move](../../../ado/reference/ado-api/move-method-ado.md), [MoveFirst, MoveLast, MoveNext и MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)) могут привести к перемещению удаленной записи, если удаление происходит после извлечения записей. После первоначальной выборки последующие удаления не будут отражены в кэше данных до тех пор, пока не будет произведена попытка получить доступ к значению данных из удаленной строки. Однако установка для **CacheSize** значения 1 исключает эту ошибку, так как не удается получить удаленные строки.
