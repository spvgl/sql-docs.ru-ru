---
title: Собственный клиент, обновление приложения SQL 2005
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, updating applications
ms.assetid: 1e1e570c-7f14-4e16-beab-c328e3fbdaa8
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2eddd2284ec77a1a4979389f964baeafb6932dc5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "75243814"
---
# <a name="updating-an-application-from-sql-server-2005-native-client"></a>Обновление приложения с переходом от собственного клиента SQL Server 2005
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В этом разделе рассматриваются критические изменения в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в сравнении с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].  
  
 При обновлении с компонентов доступа к данным MDAC к собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] могут возникнуть определенные изменения в работе. Дополнительные сведения см. [в статье обновление приложения для SQL Server Native Client из MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 поставляется в составе [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]. 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 поставляется в составе [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].  Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 10.5 поставляется в составе [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)]. Клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 поставляется в составе [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] и [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].  
  
|Изменения в поведении собственного клиента SQL Server, начиная с версии [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]|Description|  
|------------------------------------------------------------------------------------|-----------------|  
|OLE DB дополняет данные только до заданного масштаба.|Для преобразований, в которых преобразованные данные отправляются на сервер, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственный [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]клиент (начиная с версии) дополняет конечные нули в данных до максимальной длины значений **типа DateTime** . Собственный клиент SQL Server версии 9.0 дополнял данные до 9 разрядов.|  
|Проверьте DBTYPE_DBTIMESTAMP для Икоммандвиспараметер:: SetParameterInfo.|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Собственный клиент (начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) реализует OLE DB требование для *bScale* в икоммандвиспараметер:: SetParameterInfo для задания точности доли секунды для DBTYPE_DBTIMESTAMP.|  
|Хранимая процедура **sp_columns** теперь возвращает значение **"No** " вместо **"No"** для столбца IS_NULLABLE.|Начиная с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]), **sp_columns** хранимая процедура теперь возвращает **"No** " вместо **"No"** для IS_NULLABLE столбца.|  
|SQLSetDescRec, SQLBindParameter и SQLBindCol теперь выполняют проверку согласованности.|До [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0 Установка SQL_DESC_DATA_PTR не вызывала проверку согласованности для любого типа дескриптора в SQLSetDescRec, SQLBindParameter или SQLBindCol.|  
|Теперь Склкопидеск проверяет согласованность дескриптора.|До [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0 склкопидеск не выполнял проверку согласованности, когда поле SQL_DESC_DATA_PTR было задано для конкретной записи.|  
|SQLGetDescRec больше не выполняет проверку согласованности дескрипторов.|До [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0 SQLGetDescRec выполнил проверку согласованности дескрипторов при задании поля SQL_DESC_DATA_PTR. Этого не требовалось по спецификации ODBC, и собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) и более поздних версий уже не проводит эту проверку согласованности.|  
|При выходе значения даты за пределы диапазона теперь происходит возврат другого значения ошибки.|Для типа **даты и времени** в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственном клиенте (начиная с [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]версии) будет возвращен другой номер ошибки, отличный от диапазона, возвращенного в более ранних версиях.<br /><br /> В частности [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , собственный клиент 9,0 возвратил 22007 для всех значений года за пределами диапазона при преобразовании строк в **DateTime**, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] а собственный клиент,[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]начинающийся с версии 10,0 (), возвращает 22008, если дата находится в диапазоне, поддерживаемом **datetime2** , но вне диапазона, поддерживаемого типом данных **DateTime** или **smalldatetime**.|  
|значение **DateTime** усекает доли секунды и неокругление, если округление изменит день.|До появления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 10.0 клиент, передавая данные типа **datetime** на сервер, округлял их до ближайшей 1/300-й доли секунды. Начиная с собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0, в этой ситуации происходит усечение долей секунды, если округление приводит к изменению значения дня.|  
|Возможные усечение в секундах для значения **DateTime** .|В приложении, построенном с помощью собственного клиента [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (или более поздних версий), при подключении к серверу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2005 (или более ранней версии) будут усекаться секунды и доли секунды в части отправленных на сервер данных, относящейся ко времени, если выполняется привязка к столбцу типа datetime с идентификатором типа DBTYPE_DBTIMESTAMP (OLE DB) или SQL_TIMESTAMP (ODBC) и масштабом 0.<br /><br /> Пример:<br /><br /> Входные данные: 1994-08-21 21:21:36.000<br /><br /> Вставляемые данные: 1994-08-21 21:21:00.000|  
|Преобразование данных OLE DB из типа DBTYPE_DBTIME в DBTYPE_DATE больше не вызывает изменения значения дня.|До появления собственного клиента версии 10.0 для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], если часть времени для значения DBTYPE_DATE отстояла от полуночи не более чем на полсекунды, то применение кода преобразования OLE DB приводило к изменению дня. Начиная с собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0, день не изменяется (доли секунды усекаются, а не округляются).|  
|Изменения преобразования IBCPSession::BCColFmt.|Начиная с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] собственного клиента 10,0 при использовании IBCPSession:: бкоколфмт для преобразования SQLDATETIME или SQLDATETIME в строковый тип экспортируется дробное значение. Например, при преобразовании типа SQLDATETIME в тип SQLNVARCHARMAX более ранние версии собственного клиента для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращали следующее:<br /><br /> 1989-02-01 00:00:00. Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 и более поздних версий возвращает 1989-02-01 00:00:00.0000000.|  
|Размер пересылаемых данных должен соответствовать длине, заданной параметром SQL_LEN_DATA_AT_EXEC.|При использовании параметра SQL_LEN_DATA_AT_EXEC размер данных должен соответствовать длине, заданной параметром SQL_LEN_DATA_AT_EXEC. Можно использовать параметр SQL_DATA_AT_EXEC, но SQL_LEN_DATA_AT_EXEC дает некоторый выигрыш в производительности.|  
|В пользовательских приложениях, в которых используется API BCP, теперь могут обнаруживаться предупреждающие сообщения.|API BCP выдает предупреждающее сообщение, если длина данных превышает заданную длину для полей всех типов. Раньше это предупреждение выдавалось только для символьных типов, но не для всех типов.|  
|Вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, вызывает ошибку.|В [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 9.0 вставка пустой строки в объект типа **sql_variant**, привязанный как тип даты и времени, не вызывала ошибки. Собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии 10.0 (или более поздних версий) в этом случае совершенно обоснованно возвращает ошибку.|  
|Более строгая проверка параметров типа SQL_C_TYPE _TIMESTAMP и DBTYPE_DBTIMESTAMP.|До [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] собственного клиента значения **DateTime** округляются в соответствии с масштабом столбцов **DateTime** и smalldatetime. **** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Теперь в собственном клиенте [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] (и более поздних версиях) применяются более строгие правила проверки, определенные в базовой спецификации ODBC для долей секунды. Если значение параметра не удается преобразовать в тип SQL с помощью масштаба, заданного или подразумеваемого клиентской привязкой, без усечения конечных разрядов, то возвращается ошибка.|  
|
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может возвращать различные результаты при выполнении триггера.|Изменения, внесенные в [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], могут привести к тому, что приложение получит другие результаты при выполнении инструкции, вызвавшей выполнение триггера при действующем параметре **NOCOUNT OFF**. В такой ситуации в приложении может возникнуть ошибка. Чтобы устранить эту ошибку, установите параметр **NOCOUNT ON** в триггере или вызовите SQLMoreResults, чтобы перейти к следующему результату.|  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
