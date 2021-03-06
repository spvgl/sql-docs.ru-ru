---
title: Функция SQLDescribeCol | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeCol
helpviewer_keywords:
- SQLDescribeCol function [ODBC]
ms.assetid: eddef353-83f3-4a3c-8f24-f9ed888890a4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 63982d87f0dbbe0c8ab1a540185e298d9943f630
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68104796"
---
# <a name="sqldescribecol-function"></a>SQLDescribeCol, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ISO 92  
  
 **Сводка**  
 **SQLDescribeCol** возвращает дескриптор результата — имя столбца, тип, размер столбца, десятичные цифры и допустимость значений NULL — для одного столбца в результирующем наборе. Эти сведения также доступны в полях IRD.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLDescribeCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLCHAR *      ColumnName,  
      SQLSMALLINT    BufferLength,  
      SQLSMALLINT *  NameLengthPtr,  
      SQLSMALLINT *  DataTypePtr,  
      SQLULEN *      ColumnSizePtr,  
      SQLSMALLINT *  DecimalDigitsPtr,  
      SQLSMALLINT *  NullablePtr);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
 *ColumnNumber*  
 Входной Число столбцов результатов, упорядоченное последовательно в возрастающем порядке столбцов, начиная с 1. Аргумент *columnNumber* также может иметь значение 0 для описания столбца Bookmark.  
  
 *ColumnName*  
 Проверки Указатель на буфер, заканчивающийся нулем, в котором возвращается имя столбца. Это значение считывается из поля SQL_DESC_NAME IRD. Если столбец не имеет имени или имя столбца не может быть определено, драйвер возвращает пустую строку.  
  
 Если *ColumnName* имеет значение null, *намеленгсптр* будет возвращать общее количество символов (исключая символ завершения null для символьных данных), доступных для возврата в буфер, на который указывает *ColumnName*.  
  
 *BufferLength*  
 Входной Длина **ColumnName* buffer в символах.  
  
 *намеленгсптр*  
 Проверки Указатель на буфер, в котором возвращается общее число символов (исключая нулевое завершение), доступных для возврата в \* *ColumnName*. Если число возвращаемых символов больше или равно значению *BufferLength*, имя столбца в \* *ColumnName* усекается до *BufferLength* минуса длину символа завершения null.  
  
 *дататипептр*  
 Проверки Указатель на буфер, в котором возвращается тип данных SQL столбца. Это значение считывается из поля SQL_DESC_CONCISE_TYPE IRD. Это будет одно из значений в [типах данных SQL](../../../odbc/reference/appendixes/sql-data-types.md)или тип данных SQL, зависящий от драйвера. Если тип данных не может быть определен, драйвер возвращает SQL_UNKNOWN_TYPE.  
  
 В ODBC 3. *x*, SQL_TYPE_DATE, SQL_TYPE_TIME или SQL_TYPE_TIMESTAMP возвращается в * \*дататипептр* для данных даты, времени или отметки времени соответственно; в ODBC 2. возвращается *x*, SQL_DATE, SQL_TIME или SQL_TIMESTAMP. Диспетчер драйверов выполняет необходимые сопоставления при использовании ODBC 2. Приложение *x* работает с ODBC 3. драйвер *x* или при использовании ODBC 3. Приложение *x* работает с ODBC 2. драйвер *x* .  
  
 Если *columnNumber* равен 0 (для столбца закладки), SQL_BINARY возвращается в * \*дататипептр* для закладок переменной длины. (SQL_INTEGER возвращается, если закладки используются ODBC 3. Приложение *x* , работающее с ODBC 2. драйвер *x* или ODBC 2. Приложение *x* , работающее с ODBC 3. драйвер *x* .)  
  
 Дополнительные сведения об этих типах данных см. в разделе [типы данных SQL](../../../odbc/reference/appendixes/sql-data-types.md) в приложении г: типы данных. Дополнительные сведения о типах данных SQL, относящихся к драйверам, см. в документации по драйверу.  
  
 *колумнсизептр*  
 Проверки Указатель на буфер, в котором возвращается размер столбца в источнике данных (в символах). Если размер столбца определить нельзя, драйвер возвращает значение 0. Дополнительные сведения о размере столбцов см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении г: типы данных.  
  
 *деЦималдигитсптр*  
 Проверки Указатель на буфер, в котором возвращается число десятичных разрядов столбца в источнике данных. Если число десятичных разрядов не может быть определено или неприменимо, драйвер возвращает 0. Дополнительные сведения о десятичных цифрах см. в разделе [размер столбца, десятичные цифры, длина октета и размер дисплея](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md) в приложении D: типы данных.  
  
 *нуллаблептр*  
 Проверки Указатель на буфер, в котором возвращается значение, указывающее, допускает ли столбец значения NULL. Это значение считывается из поля SQL_DESC_NULLABLE IRD. Значение может быть одним из следующих:  
  
 SQL_NO_NULLS: столбец не допускает значений NULL.  
  
 SQL_NULLABLE: столбец допускает значения NULL.  
  
 SQL_NULLABLE_UNKNOWN: драйвер не может определить, допускает ли столбец значения NULL.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_ERROR или SQL_INVALID_HANDLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Если **SQLDescribeCol** возвращает либо SQL_ERROR, либо SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE можно получить, вызвав **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLDescribeCol** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01004|Строковые данные, усеченные справа|Значение буфера \* *ColumnName* недостаточно велико для возврата всего имени столбца, поэтому имя столбца было усечено. Длина неусеченного имени столбца возвращается в **намеленгсптр*. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|07005|Подготовленная инструкция не является *спецификацией курсора*|Инструкция, связанная с *статеменсандле* , не вернула результирующий набор. Нет столбцов для описания.|  
|07009|Недопустимый индекс дескриптора|(DM) значение, указанное для аргумента *columnNumber* , равно 0, а параметр инструкции SQL_ATTR_USE_BOOKMARKS был SQL_UB_OFF.<br /><br /> Значение, указанное для аргумента *columnNumber* , больше числа столбцов в результирующем наборе.|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Функция была вызвана, и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** для *статеменсандле*. Затем функция была вызвана в *статеменсандле*.<br /><br /> Функция была вызвана и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове **SQLDescribeCol** .<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**или **SQLMoreResults** были вызваны для *статеменсандле* и возвращены SQL_PARAM_DATA_AVAILABLE. Эта функция была вызвана до получения данных для всех потоковых параметров.<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) функция была вызвана до вызова **SQLPrepare**, **SQLExecute**или функции каталога в обработчике инструкции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY090|Недопустимая длина строки или буфера|(DM) значение, указанное для аргумента *BufferLength* , было меньше 0.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
 **SQLDescribeCol** может возвращать любое значение SQLSTATE, которое может быть возвращено **SQLPrepare** или **SQLExecute** при вызове после **SQLPrepare** и до **SQLExecute**, в зависимости от того, когда источник данных оценивает инструкцию SQL, связанную с обработчиком инструкций.  
  
 Из соображений производительности приложение не должно вызывать **SQLDescribeCol** перед выполнением инструкции.  
  
## <a name="comments"></a>Комментарии  
 Приложение обычно вызывает **SQLDescribeCol** после вызова **SQLPrepare** и до или после связанного вызова **SQLExecute**. Приложение также может вызвать **SQLDescribeCol** после вызова **SQLExecDirect**. Дополнительные сведения см. в разделе [метаданные результирующего набора](../../../odbc/reference/develop-app/result-set-metadata.md).  
  
 **SQLDescribeCol** извлекает имя столбца, тип и длину, созданные инструкцией **SELECT** . Если столбец является выражением, **ColumnName* является либо пустой строкой, либо именем, определенным драйвером.  
  
> [!NOTE]  
>  ODBC поддерживает SQL_NULLABLE_UNKNOWN как расширение, хотя в спецификации интерфейса Open Group и группы доступа SQL не указан параметр для **SQLDescribeCol**.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Привязка буфера к столбцу в результирующем наборе|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Отмена обработки инструкции|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Возврат сведений о столбце в результирующем наборе|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|Выборка нескольких строк данных|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Возвращение количества столбцов результирующего набора|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|Подготовка инструкции к выполнению|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)
