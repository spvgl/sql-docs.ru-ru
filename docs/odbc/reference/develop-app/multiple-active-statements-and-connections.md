---
title: Множественные активные инструкции и соединения | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], multiple active statements and connections
- multiple active statements and connections [ODBC]
ms.assetid: a6571356-b23e-4f10-a17b-bce09460b71e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76b74ff748a62a401955e4ea4a995f507314124e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67942828"
---
# <a name="multiple-active-statements-and-connections"></a>Множественные активные инструкции и подключения
Некоторые драйверы и СУБД ограничивают количество инструкций и соединений, которые могут быть активными за один раз. Эти числа могут быть меньше одного. Дополнительные сведения см. в статьях параметры SQL_MAX_CONCURRENT_ACTIVITIES и SQL_MAX_DRIVER_CONNECTIONS в описании функции [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) , а также [дескрипторы инструкций](../../../odbc/reference/develop-app/statement-handles.md) и [дескрипторы соединения](../../../odbc/reference/develop-app/connection-handles.md).
