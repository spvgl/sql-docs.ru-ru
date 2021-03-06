---
title: Ограничения использования курсоров, управляемых набором ключей | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], cursors
- keyset-driven cursors [ODBC]
ms.assetid: 59d86fed-387c-4719-9550-36343e74da44
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0c35f900faf1a30788b3642af3fdd65d672951d5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68054119"
---
# <a name="limitations-of-using-keyset-driven-cursors"></a>Ограничения на использование курсоров, управляемых ключевым набором
> [!IMPORTANT]  
>  Эта функция будет удалена в следующей версии Windows. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Вместо этого используйте драйвер ODBC, предоставляемый Oracle.  
  
 Необходимо иметь возможность получить один столбец ROWID для запрашиваемой таблицы. Курсор, управляемый набором ключей, не может использоваться в соединениях, запросах или инструкциях, содержащих предложения DISTINCT, GROUP BY, UNION, INTERSECT или минус.  
  
 Кроме того, если приложение использует Псевдонимы таблиц, курсоры, управляемые набором ключей, не будут работать. требуются однонаправленные или статические типы курсоров. Использование типа курсора набора ключей с псевдонимами таблиц приведет к следующей ошибке: "[Microsoft] [драйвер ODBC для Oracle] не может использовать курсор, управляемый набором ключей, при соединении, с Union, INTERSECT или минус или в результирующем наборе только для чтения".  
  
> [!NOTE]  
>  Из-за того, как драйвер обрабатывает инструкцию SQL, которая отправляется на сервер Oracle, Oracle внутренне возвращает следующее сообщение об ошибке: "ORA-00964: имя таблицы не входит в список".
