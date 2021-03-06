---
title: Функция SQLMoreResults | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3ca7ed4f6bbcd31b8f67b95dc14a2c6c301b5a59
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138831"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults, функция
**Соответствия**  
 Представленная версия: соответствие стандартам ODBC 1,0: ODBC  
  
 **Сводка**  
 **SQLMoreResults** определяет, доступны ли дополнительные результаты в инструкции, содержащей инструкции **SELECT**, **Update**, **INSERT**или **Delete** , и, если это так, инициализирует обработку для этих результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>Аргументы  
 *статеменсандле*  
 Входной Маркер инструкции.  
  
## <a name="returns"></a>Возвращает  
 SQL_SUCCESS, SQL_SUCCESS_WITH_INFO, SQL_STILL_EXECUTING, SQL_NO_DATA, SQL_ERROR, SQL_INVALID_HANDLE ИЛИ SQL_PARAM_DATA_AVAILABLE.  
  
## <a name="diagnostics"></a>Диагностика  
 Когда **SQLMoreResults** возвращает SQL_ERROR или SQL_SUCCESS_WITH_INFO, связанное значение SQLSTATE может быть получено путем вызова **SQLGetDiagRec** с *параметром handletype* SQL_HANDLE_STMT и *маркером* *статеменсандле*. В следующей таблице перечислены значения SQLSTATE, обычно возвращаемые функцией **SQLMoreResults** , и объясняется каждый из них в контексте этой функции. Нотация "(DM)" предшествует описаниям SQLSTATE, возвращаемым диспетчером драйверов. Код возврата, связанный с каждым значением SQLSTATE, имеет SQL_ERROR, если не указано иное.  
  
|SQLSTATE|Ошибка|Description|  
|--------------|-----------|-----------------|  
|01000|Общее предупреждение|Информационное сообщение для конкретного драйвера. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|01S02|Значение параметра изменено|Значение атрибута инструкции изменилось при обработке пакета. (Функция возвращает SQL_SUCCESS_WITH_INFO.)|  
|08S01|Сбой канала связи|Канал связи между драйвером и источником данных, к которому был подключен драйвер, был неудачен до завершения обработки функции.|  
|40001|Сбой сериализации|Произошел откат транзакции из-за взаимоблокировки ресурсов с другой транзакцией.|  
|40003|Неизвестное завершение инструкции|Не удалось выполнить связанное подключение во время выполнения этой функции, и состояние транзакции не может быть определено.|  
|HY000|Общая ошибка|Произошла ошибка, для которой нет определенного SQLSTATE и для которого не определен SQLSTATE для конкретной реализации. Сообщение об ошибке, возвращаемое функцией **SQLGetDiagRec** в буфере * \*MessageText* , описывает ошибку и ее причину.|  
|HY001|Ошибка выделения памяти|Драйверу не удалось выделить память, необходимую для поддержки выполнения или завершения функции.|  
|HY008|Operation canceled|Асинхронная обработка включена для *статеменсандле*. Была вызвана функция **SQLMoreResults** , и до завершения ее выполнения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле*. Затем в *статеменсандле*вызывается функция **SQLMoreResults** .<br /><br /> Была вызвана функция **SQLMoreResults** , и до ее завершения была вызвана **SQLCancel** или **склканцелхандле** в *статеменсандле* из другого потока многопоточного приложения.|  
|HY010|Ошибка последовательности функций|(DM) вызвана асинхронно исполняемая функция для маркера соединения, связанного с *статеменсандле*. Эта асинхронная функция все еще выполнялась при вызове функции **SQLMoreResults** .<br /><br /> (DM) вызывается асинхронно исполняемая функция (не эта одна) для *статеменсандле* и все еще выполнялась при вызове этой функции.<br /><br /> (DM) **SQLExecute**, **SQLExecDirect**, **SQLBulkOperations**или **SQLSetPos** были вызваны для *статеменсандле* и возвращены SQL_NEED_DATA. Эта функция была вызвана перед отправкой данных для всех параметров или столбцов данных, выполняемых во время выполнения.|  
|HY013|Ошибка управления памятью|Не удалось обработать вызов функции, так как не удалось получить доступ к базовым объектам памяти, возможно, из-за нехватки памяти.|  
|HY117|Подключение приостановлено из-за неизвестного состояния транзакции. Допускаются только функции отключения и только для чтения.|(DM) Дополнительные сведения о состоянии SUSPENDED см. в разделе [функция SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).|  
|HYT01|Время ожидания подключения истекло|Время ожидания соединения истекло до ответа источника данных на запрос. Время ожидания соединения задается через **SQLSetConnectAttr**, SQL_ATTR_CONNECTION_TIMEOUT.|  
|IM001|Драйвер не поддерживает эту функцию|(DM) драйвер, связанный с *статеменсандле* , не поддерживает функцию.|  
|IM017|Опрос отключен в режиме асинхронного уведомления|При использовании модели уведомления опрос отключен.|  
|IM018|**Склкомплетеасинк** не был вызван для завершения предыдущей асинхронной операции с этим обработчиком.|Если предыдущий вызов функции в обработчике возвращает SQL_STILL_EXECUTING и если включен режим уведомления, то для обработки после обработки и завершения операции необходимо вызвать **склкомплетеасинк** .|  
  
## <a name="comments"></a>Комментарии  
 Инструкции **SELECT** возвращают результирующие наборы. Инструкции **Update**, **INSERT**и **Delete** возвращают количество затронутых строк. Если какая-либо из этих инструкций пакетирована, передается с массивами параметров (с нумерацией в порядке возрастания параметров в том порядке, в котором они отображаются в пакете) или в процедурах они могут возвращать несколько результирующих наборов или строк. Сведения о пакетах инструкций и массивов параметров см. в разделе [пакеты инструкций SQL](../../../odbc/reference/develop-app/batches-of-sql-statements.md) и [массивов значений параметров](../../../odbc/reference/develop-app/arrays-of-parameter-values.md).  
  
 После выполнения пакета приложение позиционируется на первый результирующий набор. Приложение может вызывать **SQLBindCol**, **SQLBulkOperations**, **SQLFetch**, **SQLGetData**, **SQLFetchScroll**, **SQLSetPos**и все функции метаданных на первом или любом последующем результирующем наборе, точно так же, как при наличии только одного результирующего набора. После завершения выполнения первого результирующего набора приложение вызывает **SQLMoreResults** для перехода к следующему результирующему набору. Если доступен другой результирующий набор или счетчик, **SQLMoreResults** возвращает SQL_SUCCESS и инициализирует результирующий набор или число для дополнительной обработки. Если между инструкциями создания результирующего набора появляются какие-либо операторы создания подсчета строк, то их можно пошаговым образом вызвать **SQLMoreResults**. После вызова **SQLMoreResults** для инструкций **Update**, **INSERT**или **Delete** приложение может вызвать **SQLRowCount**.  
  
 Если существовал текущий результирующий набор со строками без выборки, **SQLMoreResults** отклоняет этот результирующий набор и делает доступным следующий результирующий набор или количество. Если все результаты обработаны, **SQLMoreResults** возвращает SQL_NO_DATA. Для некоторых драйверов выходные параметры и возвращаемые значения недоступны до тех пор, пока не будут обработаны все результирующие наборы и количество строк. Для таких драйверов выходные параметры и возвращаемые значения становятся доступными, когда **SQLMoreResults** возвращает SQL_NO_DATA.  
  
 Все привязки, установленные для предыдущего результирующего набора, по-прежнему остаются действительными. Если структуры столбцов отличаются для этого результирующего набора, то вызов **SQLFetch** или **SQLFetchScroll** может привести к ошибке или усечению. Чтобы избежать этого, приложение должно вызвать **SQLBindCol** для явной повторной привязки (или сделать это, установив поля дескриптора). Кроме того, приложение может вызвать **SQLFreeStmt** с *возможностью* SQL_UNBIND, чтобы отменить привязку всех буферов столбцов.  
  
 Значения атрибутов инструкции, такие как тип курсора, параллелизм курсоров, размер набора ключей или максимальная длина, могут измениться при переходе приложения по пакету по вызову **SQLMoreResults**. В этом случае **SQLMoreResults** возвратит SQL_SUCCESS_WITH_INFO и SQLSTATE 01S02 (значение параметра изменилось).  
  
 Вызов **SQLCloseCursor**или **SQLFreeStmt** с *параметром* SQL_CLOSE удаляет все результирующие наборы и счетчики строк, которые были доступны в результате выполнения пакета. Обработчик инструкции возвращает либо выделенное, либо подготовленное состояние. Вызов **SQLCancel** для отмены асинхронно выполняемой функции при выполнении пакета, а маркер инструкции находится в состоянии выполненного, позиционированного курсора или асинхронного состояния, результатом которого являются все результирующие наборы и счетчики строк, сформированные пакетом, который удаляется при успешном вызове отмены. Затем инструкция возвращает в подготовленное или выделенное состояние.  
  
 Если пакет инструкций или процедура, объединяющая другие инструкции SQL с инструкциями **SELECT**, **Update**, **INSERT**и **Delete** , эти другие инструкции не влияют на **SQLMoreResults**.  
  
 Дополнительные сведения см. в разделе [несколько результатов](../../../odbc/reference/develop-app/multiple-results.md).  
  
 Если искомая инструкция UPDATE, INSERT или DELETE в пакете инструкций не влияет на строки в источнике данных, **SQLMoreResults** возвращает SQL_SUCCESS. Это отличается от варианта поиска, вставки или удаления инструкции, выполняемой с помощью **SQLExecDirect**, **SQLExecute**или **метод SQLParamData**, которая возвращает SQL_NO_DATA, если она не влияет на строки в источнике данных. Если приложение вызывает **SQLRowCount** для получения числа строк после того, как вызов **SQLMoreResults** не затронул ни одной строки, **SQLRowCount** возвратит SQL_NO_DATA.  
  
 Дополнительные сведения о допустимой последовательности функций обработки результатов см. в [приложении б: таблицы переходов по состоянию ODBC](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md).  
  
 Дополнительные сведения о SQL_PARAM_DATA_AVAILABLE и потоковых выходных параметрах см. в разделе [получение выходных параметров с помощью SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md).  
  
## <a name="availability-of-row-counts"></a>Доступность счетчиков строк  
 Если пакет содержит несколько последовательных инструкций по подсчету количества строк, то возможно, что эти счетчики строк сведены в одно число строк. Например, если пакет содержит пять инструкций INSERT, то некоторые источники данных могут возвращать пять отдельных строк. Некоторые другие источники данных возвращают только одно число строк, представляющее сумму пяти отдельных строк.  
  
 Если в пакете содержится сочетание инструкций создания результирующего набора и создания количества строк, количество строк может быть недоступно. Поведение драйвера в отношении доступности счетчиков строк перечисляется в SQL_BATCH_ROW_COUNT типе сведений, доступном через вызов **SQLGetInfo**. Например, предположим, что пакет содержит инструкцию **SELECT**, за которой следуют две операции вставки и вторая **инструкция** **SELECT**. Тогда возможны следующие варианты:  
  
-   Количество строк, соответствующее двум инструкциям **INSERT** , недоступно. Первый вызов **SQLMoreResults** будет позиционировать вас на результирующий набор второй инструкции **SELECT** .  
  
-   Количество строк, соответствующее двум инструкциям **INSERT** , доступно по отдельности. (Вызов **SQLGetInfo** не возвращает бит SQL_BRC_ROLLED_UP для SQL_BATCH_ROW_COUNTного типа данных.) Первый вызов **SQLMoreResults** будет позиционировать вас на число строк первой **вставки**, а второй вызов будет располагать вас по числу строк второй операции **вставки**. Третий вызов **SQLMoreResults** будет позиционировать вас на результирующий набор второй инструкции **SELECT** .  
  
-   Количество строк, соответствующих двум **вставкам** , сведено в одно число доступных строк. (Вызов **SQLGetInfo** возвращает бит SQL_BRC_ROLLED_UP для SQL_BATCH_ROW_COUNTного типа сведений.) Первый вызов **SQLMoreResults** будет расположить вас на сведенном количестве строк, а второй вызов **SQLMoreResults** будет располагать вас по результирующему набору второго **SELECT**.  
  
 Некоторые драйверы делают количество строк доступным только для явных пакетов, а не для хранимых процедур.  
  
## <a name="related-functions"></a>Связанные функции  
  
|Тема|См. следующие документы.|  
|---------------------------|---------|  
|Отмена обработки инструкции|[Функция SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|Выборка блока данных или прокрутка результирующего набора|[Функция SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|Выборка одной строки или блока данных в прямом направлении|[Функция SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|Выборка части или всего столбца данных|[Функция SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>См. также:  
 [Справочник по API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Файлы заголовков ODBC](../../../odbc/reference/install/odbc-header-files.md)   
 [Получение выходных параметров с помощью метода SQLGetData](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
