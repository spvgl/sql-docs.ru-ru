---
title: Курсортипинум | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorTypeEnum
helpviewer_keywords:
- CursorTypeEnum enumeration [ADO]
ms.assetid: ffc6e245-4471-42ae-84dd-e85bddfce983
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f6333934997c9de38b8df1dd08849886ff3dd7f2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933275"
---
# <a name="cursortypeenum"></a>CursorTypeEnum
Указывает тип курсора, используемого в объекте [набора записей](../../../ado/reference/ado-api/recordset-object-ado.md) .  
  
|Постоянно|Значение|Description|  
|--------------|-----------|-----------------|  
|**адопендинамик**|2|Использует динамический курсор. Видимыми могут быть дополнения, изменения и удаления других пользователей, а также все типы перемещений через **набор записей** , за исключением закладок, если они не поддерживаются поставщиком.|  
|**адопенфорвардонли**|0|По умолчанию. Использует однопроходный курсор. Идентичен статическому курсору, за исключением того, что можно прокручивать только записи вперед. Это повышает производительность, если необходимо выполнить только один проход по **набору записей**.|  
|**адопенкэйсет**|1|Использует курсор KEYSET. Как и динамический курсор, за исключением того, что вы не можете видеть записи, добавленные другими пользователями, хотя записи, удаляемые другими пользователями, недоступны из **набора записей**. Изменения данных, внесенные другими пользователями, по-прежнему видимы.|  
|**адопенстатик**|3|Использует статический курсор, который представляет собой статическую копию набора записей, которые можно использовать для поиска данных или создания отчетов. Добавление, изменение или удаление других пользователей не отображается.|  
|**адопенунспеЦифиед**|-1|Не указывает тип курсора.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Постоянно|  
|--------------|  
|Адоенумс. примеры CursorType. DYNAMIC|  
|Адоенумс. примеры CursorType. ФОРВАРДОНЛИ|  
|Адоенумс. примеры CursorType. KEYSET|  
|Адоенумс. примеры CursorType. STATIC|  
|Адоенумс. примеры CursorType. не указано|  
  
## <a name="applies-to"></a>Применяется к  
 [Свойство CursorType (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
