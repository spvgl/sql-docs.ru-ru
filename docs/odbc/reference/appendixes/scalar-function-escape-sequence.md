---
title: Escape-последовательность скалярной функции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], scalar function
- scalar functions [ODBC], escape sequences
- ODBC escape sequences [ODBC], scalar function
ms.assetid: aaf5d516-e090-445f-8839-9e39581c69c7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 36e108fcc61b2390d5fd72ac4ad322778ccfb4b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68057075"
---
# <a name="scalar-function-escape-sequence"></a>Escape-последовательность скалярной функции
ODBC использует escape-последовательности для скалярных функций. Синтаксис этой escape-последовательности выглядит следующим образом:  
  
```  
{fn scalar-function}  
```  
  
## <a name="remarks"></a>Remarks  
 В нотации BNF синтаксис выглядит следующим образом:  
  
 *ODBC-скалярная функция-escape* :: =  
  
 *ODBC-ESC-инициатор* , *Скалярная функция ODBC-ESC-признак конца*  
  
 *Скалярная функция* :: = *Function-Name* (*Argument-List*)  
  
 (Определения для нетерминальных *функций-имя* и *имя функции* (*Argument-List*) являются производными от списка скалярных функций в [приложении E: скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).)  
  
 *ODBC-ESC-инициатор* :: = {  
  
 *ODBC-ESC-признак конца* :: =}  
  
 Чтобы определить, поддерживает ли источник данных процедуры, и драйвер поддерживает синтаксис вызова процедуры ODBC, приложение может вызвать **SQLGetInfo**. Дополнительные сведения см. в разделе [Приложение E. скалярные функции](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md).
