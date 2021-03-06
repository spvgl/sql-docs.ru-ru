---
title: Изоляция моментальных снимков в SQL Server
description: Описание поддержки изоляции моментальных снимков — механизма управления версиями строк, предназначенного для сокращения блокировок в транзакционных приложениях.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 2d2e27fafabc259be6bfbc0137b66e34d310f449
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75251150"
---
# <a name="snapshot-isolation-in-sql-server"></a>Изоляция моментальных снимков в SQL Server

![Download-DownArrow-Circled](../../../ssdt/media/download.png)[Скачать ADO.NET](../../sql-connection-libraries.md#anchor-20-drivers-relational-access)

Изоляция моментальных снимков улучшает параллелизм для приложений OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Основные сведения об изоляции моментальных снимков и управлении версиями строк  
После включения изоляции моментального снимка обновленные версии строк для каждой транзакции содержатся в **tempdb**. Уникальный порядковый номер транзакции идентифицирует каждую транзакцию, и эти уникальные числа записываются для каждой версии строки. Транзакция работает с последними версиями строк, порядковый номер которых предшествует порядковому номеру транзакции. Транзакция игнорирует более новые версии строк, созданные после начала транзакции.  
  
Термин "моментальный снимок" означает, что все запросы в транзакции имеют одну и ту же версию или моментальный снимок базы данных, исходя из состояния базы данных в момент начала транзакции. В транзакции моментального снимка не происходит блокировок базовых строк данных или страниц данных, что позволяет выполнять другие транзакции без блокировки предыдущей незавершенной транзакцией. Транзакции, изменяющие данные, не блокируют транзакции, считывающие данные, а транзакции, считывающие данные, не блокируют транзакции, которые записывают данные, так как в SQL Server они обычно находятся на стандартном уровне изоляции READ COMMITTED. Такое неблокирующее поведение также значительно снижает вероятность взаимоблокировок в сложных транзакциях.  
  
Изоляция моментальных снимков использует модель оптимистической блокировки. Если транзакция моментального снимка пытается зафиксировать изменения в данных, которые имели место с момента начала транзакции, произойдет откат транзакции и возникнет ошибка. Этого можно избежать, используя указания UPDLOCK для инструкций SELECT, обращающихся к изменяемым данным. Дополнительные сведения см. в разделе об указаниях блокировок в электронной документации по SQL Server.  
  
Для использования изоляции моментальных снимков в транзакции необходимо включить эту функцию с помощью параметра ALLOW_SNAPSHOT_ISOLATION ON базы данных. Это приводит к активизации механизма сохранения версий строк во временной базе данных (**tempdb**). Необходимо включить изоляцию моментальных снимков в каждой использующей ее базе данных с помощью инструкции Transact-SQL ALTER DATABASE. В этом отношении изоляция моментальных снимков отличается от традиционных уровней изоляции READ COMMITTED, REPEATABLE READ, SERIALIZABLE и READ UNCOMMITTED, которые не требуется настраивать. Следующие инструкции активируют изоляцию моментальных снимков и заменяют зафиксированное поведение по умолчанию READ COMMITTED на SNAPSHOT:  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
Включение параметра READ_COMMITTED_SNAPSHOT (ON) позволяет получить доступ к строкам с контролем версий на стандартном уровне изоляции READ COMMITTED. Если параметр READ_COMMITTED_SNAPSHOT имеет значение OFF, необходимо явно задать уровень изоляции моментального снимка для каждого сеанса, чтобы получить доступ к строкам с версиями.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Управление параллелизмом с помощью уровней изоляции  
Уровень изоляции, при котором выполняется инструкция Transact-SQL, определяет поведение блокировки и управления версиями строк. Уровень изоляции имеет область действия на уровне подключения, и после установки подключения с помощью инструкции SET TRANSACTION ISOLATION LEVEL он действует до тех пор, пока подключение не будет разорвано или не будет установлен другой уровень изоляции. После разрыва подключения и возвращения в пул сохраняется уровень изоляции из последней инструкции SET TRANSACTION ISOLATION LEVEL. Последующие подключения, использующие подключение из пула, применяют уровень изоляции, действовавший в момент добавления подключения в пул.  
  
Отдельные запросы, выдаваемые в подключении, могут содержать указания блокировки, которые изменяют изоляцию для отдельной инструкции или транзакции, но не влияют на уровень изоляции подключения. Уровни изоляции или указания блокировки, заданные в хранимых процедурах или функциях, не изменяют уровень изоляции вызывающего их подключения и действуют только во время выполнения хранимой процедуры или вызова функции.  
  
В ранних версиях SQL Server поддерживались четыре уровня изоляции, определенные в стандарте SQL-92:  
  
- READ UNCOMMITTED — это наименее строгий уровень изоляции, так как он игнорирует блокировки, размещенные другими транзакциями. Транзакции, выполняемые с помощью инструкции READ UNCOMMITTED, могут считывать измененные значения данных, которые еще не были зафиксированы другими транзакциями. Такие операции чтения называются чтением "грязных" данных.  
  
- READ COMMITTED является уровнем изоляции по умолчанию для SQL Server. Он предотвращает операции чтения "грязных" данных, указывая, что инструкции не могут считывать значения данных, которые были изменены, но еще не зафиксированы другими транзакциями. Другие транзакции по-прежнему могут изменять, вставлять или удалять данные между выполнениями отдельных инструкций в текущей транзакции, результатом чего будет неповторяемое чтение или фантомные данные.  
  
- REPEATABLE READ — это более строгий уровень изоляции, чем READ COMMITTED. Он включает в себя READ COMMITTED и дополнительно указывает, что никакие другие транзакции не могут изменять или удалять данные, которые были считаны текущей транзакцией, пока текущая транзакция не будет зафиксирована. Учитывая то, что совмещаемые блокировки на считываемых данных сохраняются до завершения транзакции и не снимаются в конце каждой инструкции, степень совпадений ниже, чем при уровне изоляции READ COMMITTED.  
  
- SERIALIZABLE — самый строгий уровень изоляции, поскольку он блокирует целые диапазоны ключей и сохраняет блокировку до завершения транзакции. Он включает в себя REPEATABLE READ и добавляет ограничение, запрещающее другим транзакциям вставлять новые строки в диапазоны, которые были прочитаны транзакцией, пока транзакция не будет завершена.  
  
Дополнительные сведения: [Руководство по блокировке и управлению версиями строк транзакций](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md).  
  
### <a name="snapshot-isolation-level-extensions"></a>Расширения уровня изоляции моментальных снимков  
SQL Server предоставляет расширения уровней изоляции стандарта SQL-92 путем представления уровня изоляции SNAPSHOT и дополнительных изменений в READ COMMITTED. Уровень изоляции READ_COMMITTED_SNAPSHOT может прозрачно заменять READ COMMITTED для всех транзакций.  
  
- Изоляция уровня SNAPSHOT указывает, что данные, считываемые в рамках транзакции, никогда не будут отражать изменения, внесенные другими одновременными транзакциями. Транзакция использует версии строк данных, которые существуют в начале транзакции. При чтении данные не блокируются, поэтому транзакции моментальных снимков не блокируют запись данных другими транзакциями. Транзакции, осуществляющие запись данных, не блокируют считывание данных транзакциями моментальных снимков. Для использования изоляции моментальных снимков необходимо включить ее, настроив параметр базы данных ALLOW_SNAPSHOT_ISOLATION.  
  
- Параметр базы данных READ_COMMITTED_SNAPSHOT определяет поведение стандартного уровня изоляции READ COMMITTED, если изоляция моментальных снимков включена в базе данных. Если не указать параметр READ_COMMITTED_SNAPSHOT явным образом, то для всех неявных транзакций применяется уровень READ COMMITTED. Это приводит к тому же поведению, что и при использовании параметра READ_COMMITTED_SNAPSHOT (по умолчанию). Если действует параметр READ_COMMITTED_SNAPSHOT, ядро СУБД использует совмещаемые блокировки для применения уровня изоляции по умолчанию. Если параметру базы данных READ_COMMITTED_SNAPSHOT присвоить значение ON, то ядро СУБД использует управление версиями строк и режим изоляции моментальных снимков по умолчанию вместо блокировок для защиты данных.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Основные сведения об изоляции моментальных снимков и управлении версиями строк  
Если включен уровень изоляции SNAPSHOT, то при обновлении каждой строки компонент SQL Server Database Engine сохраняет копию исходной строки в базе данных **tempdb** и добавляет в строку порядковый номер транзакции. Ниже приведены происходящие события в последовательном порядке.  
  
1. Инициируется новая транзакция, и ей назначается порядковый номер.  
  
2. Компонент Database Engine считывает строку внутри транзакции и получает версию строки из базы данных **tempdb**, чей порядковый номер наиболее близок и ниже порядкового номера транзакции.  
  
3. Ядро СУБД проверяет, не находится ли порядковый номер транзакции в списке порядковых номеров незафиксированных транзакций, активных при запуске транзакции моментальных снимков.  
  
4. Транзакция считывает версию строки, которая была текущей во время запуска транзакции, из базы данных **tempdb**. Новые строки, вставленные после запуска транзакции, не будут видны, так как эти порядковые номера будут выше, чем значение порядкового номера транзакции.  
  
5. Текущая транзакция обнаруживает строки, которые были удалены после ее запуска, поскольку версия любой строки в базе данных **tempdb** имеет меньшее значение порядкового номера, чем транзакция.  
  
Конечный результат изоляции моментального снимка заключается в том, что транзакция видит все данные в том виде, в котором они существовали в начале транзакции, без учета или размещения каких-либо блокировок в базовых таблицах. Это может привести к улучшению производительности в ситуациях, когда возникает состязание.  
  
Транзакция моментального снимка всегда использует управление оптимистической блокировкой, удерживая все блокировки, которые препятствуют обновлению строк другими транзакциями. Если транзакция моментального снимка пытается зафиксировать обновление строки, которая была изменена после начала транзакции, то выполняется откат транзакции и возникает ошибка.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Работа с изоляцией моментальных снимков в ADO.NET  
Изоляция моментальных снимков поддерживается в ADO.NET классом <xref:Microsoft.Data.SqlClient.SqlTransaction>. Если в базе данных включена изоляция моментального снимка, но настройка конфигурации не выполнена с учетом параметра READ_COMMITTED_SNAPSHOT со значением ON, то необходимо инициировать транзакцию <xref:Microsoft.Data.SqlClient.SqlTransaction> с помощью значения перечисления **IsolationLevel.Snapshot** при вызове метода <xref:Microsoft.Data.SqlClient.SqlConnection.BeginTransaction%2A>. В этом фрагменте кода предполагается, что подключение является открытым объектом <xref:Microsoft.Data.SqlClient.SqlConnection>.  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Пример  
В следующем примере демонстрируется поведение различных уровней изоляции при попытке доступа к заблокированным данным. Этот пример не предназначен для использования в рабочем коде.  
  
В коде устанавливается соединение с образцом базы данных **AdventureWorks** в SQL Server, создается таблица с именем **TestSnapshot** и производится вставка одной строки данных. В коде используется инструкция ALTER DATABASE Transact-SQL, чтобы включить изоляцию моментального снимка для базы данных, но не задан параметр READ_COMMITTED_SNAPSHOT. При этом действует поведение стандартного уровня изоляции READ COMMITTED. Затем код выполняет следующие действия.  
  
1. Он начинает, но не завершает транзакцию sqlTransaction1, которая использует уровень изоляции SERIALIZABLE для запуска транзакции обновления. При этом блокируется таблица.  
  
2. В коде открывается второе соединение и инициируется вторая транзакция с использованием уровня изоляции SNAPSHOT для чтения данных из таблицы **TestSnapshot**. Так как изоляция моментальных снимков включена, эта транзакция может считывать данные, существовавшие до начала транзакции sqlTransaction1.  
  
3. В коде открывается третье подключение и инициируется транзакция с использованием уровня изоляции READ COMMITTED для чтения данных из таблицы. В этом случае в коде исключается возможность считывать данные, поскольку чтение не может быть выполнено после установки блокировок на таблице в первой транзакции, поэтому код завершает свою работу в связи с истечением времени ожидания. Аналогичный результат был бы получен при использовании уровней изоляции REPEATABLE READ и SERIALIZABLE, поскольку эти уровни изоляции также не позволяют выполнять чтение после установки блокировок в первой транзакции.  
  
4. В коде открывается четвертое подключение и инициируется еще одна транзакция с использованием уровня изоляции READ UNCOMMITTED, которая выполняет "грязное" чтение незафиксированного значения в sqlTransaction1. Это значение может фактически не существовать в базе данных, если первая транзакция не будет зафиксирована.  
  
5. В нем выполняется откат первой транзакции и производится чистка путем удаления таблицы **TestSnapshot** и выключения изоляции моментального снимка в базе данных **AdventureWorks**.  
  
> [!NOTE]
>  В следующих примерах используется та же строка подключения, в которой отключено использование пулов подключений. Если подключение входит в пул, сброс его уровня изоляции не приводит к сбросу уровня изоляции на сервере. В результате последующие подключения, использующие одно и то же внутреннее подключение в составе пула, запускаются с уровнями изоляции, заданными для подключения в пуле. Вместо отключения пулов подключений можно явно задать уровень изоляции для каждого подключения.  
  
[!code-csharp[DataWorks Isolation_Snapshot.Demo#1](~/../sqlclient/doc/samples/Isolation_Snapshot.cs#1)]
  
### <a name="example"></a>Пример  
В следующем примере демонстрируется поведение изоляции моментального снимка в случае изменения данных. Код выполняет следующие действия.  
  
1. Соединяется с образцом базы данных **AdventureWorks** и включает уровень изоляции SNAPSHOT.  
  
2. Создает таблицу с именем **TestSnapshotUpdate** и вставляет три строки из образца данных.  
  
3. Транзакция sqlTransaction1 запускается, но не завершается с использованием изоляции SNAPSHOT. В транзакции выбираются три строки данных.  
  
4. Открывает второе соединение **SqlConnection** с базой данных **AdventureWorks** и создает вторую транзакцию, используя уровень изоляции READ COMMITTED, который обновляет значение в одной из строк, выбранных в sqlTransaction1.  
  
5. Транзакция sqlTransaction2 фиксируется.  
  
6. Выполняется возврат к транзакции sqlTransaction1, и осуществляется попытка обновить ту же строку, которая уже зафиксирована в sqlTransaction1. Возникает ошибка 3960, и для транзакции sqlTransaction1 выполняется автоматический откат. Сообщения **SqlException.Number** и **SqlException.Message** отображаются в окне консоли.  
  
7. Выполняет код очистки для выключения изоляции моментального снимка в **AdventureWorks** и удаления таблицы **TestSnapshotUpdate**.  
  
    [!code-csharp[DataWorks Isolation_Snapshot1#1](~/../sqlclient/doc/samples/Isolation_Snapshot1.cs#1)]
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Использование указаний блокировки с изоляцией моментальных снимков  
В предыдущем примере первая транзакция выбирает данные, а вторая обновляет данные до того, как первая транзакция сможет завершиться, что приведет к конфликту обновления, когда первая транзакция попытается обновить одну и ту же строку. Можно уменьшить вероятность конфликтов обновления в длительных транзакциях моментальных снимков, предоставив указания блокировки в начале транзакции. Следующая инструкция SELECT использует указание UPDLOCK для блокировки выбранных строк:  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
Использование указания блокировки UPDLOCK блокирует любые строки, пытающиеся обновить строки до завершения первой транзакции. Это гарантирует, что выбранные строки не будут иметь конфликтов, когда они будут обновлены позже в транзакции. Дополнительные сведения см. в разделе об указаниях блокировок в электронной документации по SQL Server.  
  
Если в приложении много конфликтов, изоляцию моментальных снимков лучше не использовать. Указания следует использовать, только если это действительно требуется. Приложение не должно быть спроектировано таким образом, чтобы оно постоянно полагалось на указания блокировки для своей работы.  
  
## <a name="next-steps"></a>Дальнейшие действия
- [SQL Server и ADO.NET](index.md)
- [Руководство по блокировке и управлению версиями строк транзакций](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md)
