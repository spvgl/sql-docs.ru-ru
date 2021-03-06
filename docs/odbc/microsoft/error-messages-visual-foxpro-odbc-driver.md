---
title: Сообщения об ошибках (драйвер ODBC для Visual FoxPro) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- error messages [ODBC], Visual FoxPro ODBC driver
- Visual FoxPro ODBC driver [ODBC], error messages
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error messages
ms.assetid: 58ea9734-4edf-44da-ba80-938aa7b340e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6072a6e317ab87118376b08790fc0fb49c495e3b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "67952519"
---
# <a name="error-messages-visual-foxpro-odbc-driver"></a>Сообщения об ошибках (драйвер ODBC для Visual FoxPro)
При возникновении ошибки драйвер Visual FoxPro возвращает следующие сведения:  
  
-   Основной номер ошибки и текст сообщения об ошибке  
  
-   Сообщение SQLSTATE (код ошибки ODBC) и текст сообщения об ошибке  
  
 Чтобы получить доступ к этой информации об ошибке, вызовите [SqlError](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md).  
  
## <a name="native-errors"></a>Собственные ошибки  
 Для ошибок, возникающих в источнике данных, драйвер Visual FoxPro возвращает собственный номер ошибки и текст сообщения об ошибке. Список машинных номеров ошибок см. в разделе [собственные сообщения об ошибках драйвера ODBC для Visual FoxPro](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md).  
  
## <a name="sqlstate-odbc-error-codes"></a>SQLSTATE (коды ошибок ODBC)  
 Для ошибок, обнаруженных и возвращаемых драйвером Visual FoxPro, драйвер сопоставляет возвращенный номер собственной ошибки с соответствующим SQLSTATE. Если номер собственной ошибки не содержит код ошибки ODBC для сопоставлений, драйвер Visual FoxPro возвращает значение SQLSTATE S1000 (общая ошибка).  
  
 Список значений SQLSTATE, созданных драйвером ODBC для Visual FoxPro для соответствующих ошибок Visual FoxPro, см. в статье [коды ошибок ODBC](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md).  
  
## <a name="syntax"></a>Синтаксис  
 Сообщения об ошибках имеют следующий формат:  
  
 **[** *Vendor* **] [** *ODBC_component* **]** *ERROR_MESSAGE*  
  
 Префиксы в квадратных скобках ([]) определяют источник ошибки, как определено в следующей таблице.  
  
|Источник данных|Prefix (Префикс)|Значение|  
|-----------------|------------|-----------|  
|Диспетчер драйверов|разработчика<br />[ODBC_component]<br />[data_source]|NNTP<br />[Диспетчер драйверов ODBC]<br />Недоступно|  
|Драйвер Visual FoxPro|разработчика<br />[ODBC_component]<br />[data_source]|NNTP<br />[Драйвер ODBC Visual FoxPro]<br />Недоступно|  
  
 Например, если драйверу ODBC для Visual FoxPro не удалось найти файл Employee. dbf, он может вернуть следующее сообщение об ошибке:  
  
 "[*Microsoft*] [*драйвер ODBC Visual FoxPro*] файл" Employee. dbf "не существует"
