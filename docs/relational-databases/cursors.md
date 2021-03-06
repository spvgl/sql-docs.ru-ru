---
title: Курсоры | Документация Майкрософт
ms.custom: ''
ms.date: 11/28/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- results [SQL Server], cursors
- Transact-SQL cursors, about cursors
- cursors [SQL Server]
- data access [SQL Server], cursors
- result sets [SQL Server], cursors
- requesting cursors
- cursors [SQL Server], about cursors
ms.assetid: e668b40c-bd4d-4415-850d-20fc4872ee72
author: rothja
ms.author: jroth
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: de565a5d34ddbf8388e2c20a564bc8c872a0a1c9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68140812"
---
# <a name="cursors"></a>Курсоры
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Операции в реляционной базе данных выполняются над множеством строк. Например, набор строк, возвращаемый инструкцией `SELECT`, содержит все строки, которые удовлетворяют условиям, указанным в предложении `WHERE` инструкции. Такой полный набор строк, возвращаемых инструкцией, называется результирующим набором. Приложения, особенно интерактивные, не всегда эффективно работают с результирующим набором как с единым целым. Им нужен механизм, позволяющий обрабатывать одну строку или небольшое их число за один раз. Курсоры являются расширением результирующих наборов, которые предоставляют такой механизм.  
  
 Курсоры позволяют усовершенствовать обработку результатов:  
  
-   позиционируясь на отдельные строки результирующего набора;  
  
-   получая одну или несколько строк от текущей позиции в результирующем наборе;  
  
-   поддерживая изменение данных в строках в текущей позиции результирующего набора;  
  
-   поддерживая разные уровни видимости изменений, сделанных другими пользователями для данных, представленных в результирующем наборе;  
  
-   предоставляя инструкциям [!INCLUDE[tsql](../includes/tsql-md.md)] в скриптах, хранимых процедурах и триггерах доступ к данным результирующего набора.  
  
> [!TIP]
> В некоторых сценариях при наличии первичного ключа для таблицы цикл `WHILE` может использоваться вместо курсора, что позволяет избежать недостатков, присущих курсорам.
> Однако существуют сценарии, когда курсоры не только неизбежны, но и действительно необходимы. В этом случае, если не требуется выполнять обновление таблиц с учетом курсора, используйте курсоры *firehose*, то есть курсоры [быстрой прокрутки и только для чтения](#forward-only).
  
## <a name="cursor-implementations"></a>Реализации курсоров  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает три способа реализации курсоров.  
  
### <a name="transact-sql-cursors"></a>курсоры Transact-SQL  
Курсоры [!INCLUDE[tsql](../includes/tsql-md.md)] основаны на синтаксисе `DECLARE CURSOR` и в основном используются в скриптах, хранимых процедурах и триггерах [!INCLUDE[tsql](../includes/tsql-md.md)]. [!INCLUDE[tsql](../includes/tsql-md.md)] реализуются на сервере и управляются инструкциями [!INCLUDE[tsql](../includes/tsql-md.md)] , отправляемыми от клиента серверу. Они также могут содержаться в пакетах, хранимых процедурах или триггерах.  
  
### <a name="application-programming-interface-api-server-cursors"></a>Серверные курсоры интерфейса прикладного программирования (API)  
Курсоры API поддерживают функции курсоров API в OLE DB и ODBC. Курсоры API реализуются на сервере. Всякий раз, когда клиентское приложение вызывает функцию курсора API, поставщик OLE DB или драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] передает требование на сервер для выполнения действия в отношении серверного курсора API.  
  
### <a name="client-cursors"></a>Клиентские курсоры  
Клиентские курсоры реализуются внутренне драйвером ODBC для собственного клиента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] и библиотекой DLL, реализующей API-интерфейс ADO. Клиентские курсоры реализуются посредством кэширования всех строк результирующего набора на клиенте. Каждый раз, когда клиентское приложение вызывает функцию курсора API, драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] или ADO DLL выполняет операцию курсора на строках результирующего набора, кэшированных на клиенте.  
  
## <a name="type-of-cursors"></a>Типы курсоров  
[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает четыре типа курсоров. 

> [!NOTE]
> Курсоры могут использовать рабочие таблицы базы данных tempdb. Как и агрегирование или операции сортировки, которые выполняют сброс, они влияют на возможности ввода-вывода и являются потенциальным узким местом производительности. Курсоры `STATIC` используют рабочие таблицы с начала действия. Дополнительные сведения см. в описании рабочих таблиц в [руководстве по архитектуре обработки запросов](../relational-databases/query-processing-architecture-guide.md#worktables).

### <a name="forward-only"></a>Однонаправленный  
Однонаправленный курсор указывается как `FORWARD_ONLY` и `READ_ONLY` и не поддерживает прокрутку. Он также называется курсором *firehose* и поддерживает только получение строк последовательно, от начала до конца курсора. Строки нельзя получить из базы данных, пока они не будут выбраны. Результаты всех инструкций `INSERT`, `UPDATE` и `DELETE`, влияющих на строки результирующего набора (выполненных текущим пользователем или зафиксированных другими пользователями), отображаются как строки, выбранные из курсора.  
  
 Так как курсор не может быть прокручен назад, большинство изменений, сделанных в строках базы данных после извлечения сроки, не видны через курсор. Если значение, использованное для определения положения строки в результирующем наборе, модифицируется, например в случае обновления столбца, входящего в кластеризованный индекс, то значение видимо через курсор.  
  
 Хотя в моделях курсоров API базы данных курсор последовательного доступа рассматривается как курсор отдельного типа, в [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] принят другой подход. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] принимает однонаправленность и возможность прокрутки курсоров как параметры, которые могут быть применены к статическим, управляемым набором ключей и динамическим курсорам. [!INCLUDE[tsql](../includes/tsql-md.md)] курсоры поддерживают однонаправленные статические, управляемые набором ключей и динамические курсоры. Модели курсора API базы данных предполагают, что статические, управляемые набором ключей и динамические курсоры всегда могут быть прокручены. Если атрибут или свойство курсора API базы данных установлены в значение «однонаправленный», [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] реализует это как однонаправленный динамический курсор.  
  
### <a name="static"></a>Статические  
 Полный результирующий набор статического курсора создается в базе данных **tempdb** при открытии курсора. Статический курсор всегда отображает результирующий набор точно в том виде, в котором он был при открытии курсора. Статическими курсорами обнаруживаются лишь некоторые изменения или не обнаруживаются вовсе, но при этом в процессе прокрутки такие курсоры потребляют сравнительно мало ресурсов.  
  
Курсор не отражает изменения в базе данных, влияющие на вхождение в результирующий набор или изменяющие значения в столбцах строк, составляющих набор строк. Статический курсор не отображает новые строки, вставленные в базу данных после открытия курсора, даже если они соответствуют критериям поиска инструкции `SELECT` курсора. Если входящие в результирующий набор строки обновляются другими пользователями, то новые значения данных в статическом курсоре не отображаются. Статический курсор продолжает отображать строки, удаленные из базы данных после открытия курсора. Операции `UPDATE`, `INSERT` и `DELETE` не отображаются в статическом курсоре (до тех пор, пока курсор не будет закрыт и открыт повторно), не отображаются даже изменения, сделанные в том же соединении, в котором был открыт курсор.  
  
> [!NOTE]
> [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] статические курсоры всегда доступны только для чтения.  
  
> [!NOTE]
> Так как результирующий набор статического курсора хранится в рабочей таблице базы данных **tempdb**, то размер строк результирующего набора не может превышать максимальный размер строк таблицы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
> Дополнительные сведения см. в описании рабочих таблиц в [руководстве по архитектуре обработки запросов](../relational-databases/query-processing-architecture-guide.md#worktables). Дополнительные сведения о максимальном размере строк см. в разделе [Спецификации максимально допустимых параметров SQL Server](../sql-server/maximum-capacity-specifications-for-sql-server.md#Engine).  
  
[!INCLUDE[tsql](../includes/tsql-md.md)] использует для описания статических курсоров термин «нечувствительный». Некоторые интерфейсы API баз данных называют их курсорами моментальных снимков.  
  
### <a name="keyset"></a>Keyset  
Членство и порядок строк в курсоре, управляемом набором ключей, являются фиксированными при открытии курсора. Такие курсоры управляются с помощью набора уникальных идентификаторов — ключей. Ключи создаются из набора столбцов, который уникально идентифицирует строки результирующего набора. Набор ключей — это набор ключевых значений всех строк, попадающих под действие инструкции `SELECT` на момент открытия курсора. Набор ключей, управляющий курсором, создается в базе данных **tempdb** при открытии курсора.  
  
### <a name="dynamic"></a>Динамический  
Динамические курсоры — это противоположность статических курсоров. Динамические курсоры отражают все изменения строк в результирующем наборе при прокрутке курсора. Значения типа данных, порядок и членство строк в результирующем наборе могут меняться для каждой выборки. Все инструкции `UPDATE`, `INSERT` и `DELETE`, выполняемые пользователями, видимы посредством курсора. Обновления видимы сразу, если они сделаны посредством курсора с помощью функции API (например, **SQLSetPos**) или предложения [!INCLUDE[tsql](../includes/tsql-md.md)] `WHERE CURRENT OF`. Обновления, сделанные вне курсора, не видны до момента фиксации, если только уровень изоляции транзакций с курсорами не имеет значение READ UNCOMMITTED. Дополнительные сведения об уровнях изоляции см. в разделе [SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../t-sql/statements/set-transaction-isolation-level-transact-sql.md). 
 
> [!NOTE]
> В планах динамических курсоров никогда не используются пространственные индексы.  
  
## <a name="requesting-a-cursor"></a>Запрос курсора  
 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает два метода запроса курсоров.  
  
-   [!INCLUDE[tsql](../includes/tsql-md.md)]  
  
     Язык [!INCLUDE[tsql](../includes/tsql-md.md)] поддерживает синтаксис для использования курсоров, созданных в соответствии с синтаксисом курсоров ISO.  
  
-   API-функции курсоров базы данных.  
  
     [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] поддерживает функциональность курсоров для следующих API-интерфейсов баз данных:  
  
    -   ADO ([!INCLUDE[msCoName](../includes/msconame-md.md)] ActiveX Data Object);  
  
    -   OLE DB  
  
    -   открытый интерфейс доступа к базам данных (ODBC).  
  
Оба этих способа никогда не должны использоваться в приложении одновременно. Приложение, применяющее API-интерфейс для определения режима работы курсоров, не может затем выполнить инструкцию [!INCLUDE[tsql](../includes/tsql-md.md)] DECLARE CURSOR для запроса нового курсора [!INCLUDE[tsql](../includes/tsql-md.md)] . Инструкция DECLARE CURSOR может использоваться только в том случае, если все атрибуты API-курсоров будут установлены в значения по умолчанию.  
  
Если не был запрошен ни [!INCLUDE[tsql](../includes/tsql-md.md)] , ни API-курсор, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] целиком возвращает по умолчанию результирующий набор приложению (это называется результирующим набором по умолчанию).  
  
## <a name="cursor-process"></a>Обработка курсоров  
 [!INCLUDE[tsql](../includes/tsql-md.md)] и API-курсоры имеют различный синтаксис, но для всех курсоров [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] используется одинаковый цикл обработки.  
  
1.  Связать курсор с результирующим набором инструкции [!INCLUDE[tsql](../includes/tsql-md.md)] и задать его характеристики (например возможность обновления строк).  
  
2.  Выполнить инструкцию [!INCLUDE[tsql](../includes/tsql-md.md)] для заполнения курсора.  
  
3.  Получить в курсор необходимые строки. Операция получения в курсор одной и более строк называется выборкой. Выполнение серии выборок для получения строк в прямом или обратном направлении называется прокруткой.  
  
4.  При необходимости выполнить операции изменения (обновления или удаления) строки в текущей позиции курсора.  
  
5.  Закрыть курсор.  
  
## <a name="related-content"></a>См. также  
[Режимы работы курсоров](../relational-databases/native-client-odbc-cursors/cursor-behaviors.md)    
[Способы реализации курсоров](../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
## <a name="see-also"></a>См. также:  
[DECLARE CURSOR (Transact-SQL)](../t-sql/language-elements/declare-cursor-transact-sql.md)   
[Курсоры (Transact-SQL)](../t-sql/language-elements/cursors-transact-sql.md)   
[Функции работы с курсорами (Transact-SQL)](../t-sql/functions/cursor-functions-transact-sql.md)   
[Хранимые процедуры курсора (Transact-SQL)](../relational-databases/system-stored-procedures/cursor-stored-procedures-transact-sql.md)   
[SET TRANSACTION ISOLATION LEVEL (Transact-SQL)](../t-sql/statements/set-transaction-isolation-level-transact-sql.md)    

  
