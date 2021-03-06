---
title: Присоединение базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.attachdatabase.f1
helpviewer_keywords:
- database attaching [SQL Server]
- attaching databases [SQL Server]
ms.assetid: b4efb0ae-cfe6-4d81-a4b4-6e4916885caa
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b4c9a3160224078b908059c3902e66ef59608bac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62872255"
---
# <a name="attach-a-database"></a>Присоединение базы данных
  В этом разделе описывается присоединение базы данных в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Эту функцию можно использовать для копирования, перемещения или обновления базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Предварительные требования](#Prerequisites)  
  
     [Рекомендации](#Recommendations)  
  
     [Безопасность](#Security)  
  
-   **Присоединение базы данных с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [после обновления базы данных](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Prerequisites"></a> Предварительные требования  
  
-   Базу данных сначала необходимо отсоединить. Попытка присоединить базу данных, которая не была отсоединена, приведет к возникновению ошибки. Дополнительные сведения см. [в разделе отсоединение базы данных](detach-a-database.md).  
  
-   При присоединении базы данных должны быть доступны все файлы данных (файлы MDF и LDF). Если у какого-либо файла данных путь отличается от того, каким он был при первом создании или последнем присоединении, необходимо указать текущий путь к файлу.  
  
-   Если при присоединении базы данных файлы MDF и LDF находятся в разных каталогах, а один из путей содержит \\\\?\GlobalRoot, операция завершается ошибкой.  
  
###  <a name="Recommendations"></a> Рекомендации  
Рекомендуется перемещать базы данных с помощью процедуры `ALTER DATABASE` запланированного перемещения вместо того, чтобы использовать отсоединение и присоединение. Дополнительные сведения см. в статье [Move User Databases](move-user-databases.md).  
  
###  <a name="Security"></a> безопасность  
Разрешения на доступ к файлам устанавливаются во время выполнения определенных операций с базами данных, включая отсоединение и присоединение баз данных. Дополнительные сведения о разрешениях доступа к файлам, задаваемые во время отсоединения и присоединения базы данных, см. в разделе [Защита данных и файлов журналов](https://technet.microsoft.com/library/ms189128.aspx) электронной документации по [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] .  
  
Не рекомендуется подключать или восстанавливать базы данных, полученные из неизвестных или ненадежных источников. В этих базах данных может содержаться вредоносный код, вызывающий выполнение непредусмотренных инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] или появление ошибок из-за изменения схемы или физической структуры базы данных. Прежде чем использовать базу данных из неизвестного или ненадежного источника, выполните [инструкцию DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) в базе данных на непроизводительном сервере, а также изучите код, например хранимые процедуры или другой пользовательский код, в базе данных. Дополнительные сведения о присоединении баз данных и сведения об изменениях, вносимых при присоединении баз данных в метаданные, см. в статье [Присоединение и отсоединение базы данных (SQL Server)](database-detach-and-attach-sql-server.md).  
  
####  <a name="Permissions"></a> Permissions  
Требуется разрешение `CREATE DATABASE`, `CREATE ANY DATABASE` или `ALTER ANY DATABASE`.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] подключитесь к экземпляру [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]и разверните его.  
  
2.  Щелкните правой кнопкой мыши узел **Базы данных** и выберите команду **Присоединить**.  
  
3.  Чтобы указать присоединяемую базу данных, в диалоговом окне **Присоединение баз данных** нажмите кнопку **Добавить**, в диалоговом окне **Расположение файлов базы данных** выберите диск, на котором находится база данных, и разверните дерево каталогов, чтобы найти и выбрать MDF-файл, например:  
  
     `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA\AdventureWorks2012_Data.mdf`  
  
    > [!IMPORTANT]  
    > При попытке выбора базы данных, которая уже присоединена, возникает ошибка.  
  
     **Базы данных для присоединения**  
     Отобразятся сведения о выбранных базах данных.  
  
     
      \<нет заголовка столбца>  
 Отображается значок, указывающий на состояние операции присоединения. Возможные значки описываются в приводимом ниже описании **Состояние** .  
  
     **Расположение файла MDF**  
     Отображается путь и имя выбранного MDF-файла.  
  
     **Имя базы данных**  
     Отображается имя базы данных.  
  
     **Присоединить как**  
     Необязательный параметр, указывает другое имя, под которым присоединяется база данных.  
  
     **Владелец**  
     Содержит раскрывающийся список возможных владельцев базы данных, из которого при необходимости можно выбрать другого владельца.  
  
     **Состояние**  
     Отображается состояние базы данных в соответствии со следующей таблицей.  
  
    |Значок|Текст состояния|Description|  
    |----------|-----------------|-----------------|  
    |(Нет значка)|(Нет текста)|Операция присоединения не была запущена или находится в режиме ожидания для этого объекта. Это состояние по умолчанию при открытии диалогового окна.|  
    |Зеленый, указывающий направо треугольник|выполняется;|Операция присоединения была запущена, но не завершена.|  
    |Зеленый флажок|Успех|Объект успешно присоединен.|  
    |Красный кружок с белым крестом внутри|Ошибка|При выполнении операции присоединения возникла ошибка, и операция не была успешно завершена.|  
    |Кружок с двумя черными квадратами (слева и справа) и двумя белыми квадратами (сверху и снизу)|Остановлена|Операция присоединения не была успешно завершена, т.к. пользователь остановил операцию.|  
    |Кружок, содержащий изогнутую стрелку, указывающую в направлении против часовой стрелки|Выполнен откат|Операция присоединения была успешной, но был выполнен ее откат из-за ошибки, возникшей при вложении другого объекта.|  
  
     **Сообщение**  
     Отображается пустое сообщение или гиперссылка «Файл не найден».  
  
     **Добавление**  
     Найдите необходимые основные файлы базы данных. Если пользователь выбирает mdf-файл, необходимые сведения автоматически вводятся в соответствующие поля сетки **Базы данных для присоединения** .  
  
     **Удалить**  
     Удаляет выбранный файл из сетки **Базы данных для присоединения** .  
  
     **** *<database_name>* **"сведения о базе данных**  
     Отображаются имена файлов, которые необходимо присоединить. Чтобы проверить или изменить путь к файлу, нажмите кнопку **Обзор** (**...**).  
  
    > [!NOTE]  
    > Если файл не существует, в столбце **Сообщение** отображается сообщение «Не найден». Если файл журнала не найден, то он существует в другом каталоге или был удален. Необходимо или обновить путь файла в сетке **Сведения о базе данных** таким образом, чтобы этот путь указывал на правильное расположение, или удалить файл журнала из сетки. Если MDF-файл не найден, необходимо обновить путь этого файла в сетке таким образом, чтобы этот путь указывал на правильное расположение.  
  
     **Исходное имя файла**  
     Отображается имя присоединенного файла, принадлежащего базе данных.  
  
     **Тип файла**  
     Указывается тип файла: **Данные** или **Журнал**.  
  
     **Текущий путь к файлу**  
     Отображается путь к выбранному файлу базы данных. Путь может быть изменен вручную.  
  
     **Сообщение**  
     Отображает пустое сообщение или гиперссылку "**файл не найден**".  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
### <a name="to-attach-a-database"></a>Присоединение базы данных  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Используйте инструкцию [Create Database](/sql/t-sql/statements/create-database-sql-server-transact-sql) с предложением `FOR ATTACH` Close.  
  
     Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере производится присоединение файлов базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] с ее последующим переименованием в `MyAdventureWorks`.  
  
    ```sql  
    CREATE DATABASE MyAdventureWorks   
        ON (FILENAME = 'C:\MySQLServer\AdventureWorks_Data.mdf'),   
        (FILENAME = 'C:\MySQLServer\AdventureWorks_Log.ldf')   
        FOR ATTACH;  
    ```  
  
    > [!NOTE]  
    > Кроме того, можно вызвать хранимую процедуру [sp_attach_db](/sql/relational-databases/system-stored-procedures/sp-attach-db-transact-sql) или [sp_attach_single_file_db](/sql/relational-databases/system-stored-procedures/sp-attach-single-file-db-transact-sql) . Но эти расширенные хранимые процедуры в будущих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]будут удалены. Избегайте использования этого компонента в новых разработках и запланируйте изменение существующих приложений, в которых он применяется. Рекомендуется использовать CREATE DATABASE... Вместо этого для присоединения.  
  
##  <a name="FollowUp"></a>Дальнейшие действия. После обновления базы данных SQL Server  
 вставить обновление базы данных с помощью метода Attach, база данных немедленно становится доступной и автоматически обновляется. Если база данных содержит полнотекстовые индексы, то в процессе обновления будет произведен их импорт, сброс или перестроение в зависимости от установленного значения свойства сервера **Режим обновления полнотекстового каталога** . Если при обновлении выбран режим **Импортировать** или **Перестроить**, то полнотекстовые индексы во время обновления будут недоступны. В зависимости от объема индексируемых данных процесс импорта может занять несколько часов, а перестроение — в несколько (до десяти) раз больше. Обратите внимание, что если при обновлении выбран режим **Импортировать**, а полнотекстовый каталог недоступен, то связанные с ним полнотекстовые индексы будут перестроены.  
  
Если уровень совместимости пользовательской базы данных до обновления был 100 или выше, после обновления он останется таким же. Если уровень совместимости до обновления был 90, в обновленной базе данных он устанавливается в 100, что является минимально поддерживаемым уровнем совместимости в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Дополнительные сведения см. в разделе [Уровень совместимости инструкции ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level).  
  
## <a name="see-also"></a>См. также:  
 [Создание &#40;базы данных SQL Server&#41;Transact-SQL](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [Отсоединение базы данных](detach-a-database.md)  
  
  
