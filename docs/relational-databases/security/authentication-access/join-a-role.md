---
title: Присоединение к роли | Документация Майкрософт
ms.custom: ''
ms.date: 07/14/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
f1_keywords:
- SQL13.SWB.DATABASEUSER.MEMBERSHIP.F1
helpviewer_keywords:
- adding a member to a role
- join a role
ms.assetid: 05c8d10d-5823-46c6-8b1a-81722da6a42b
author: VanMSFT
ms.author: vanto
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 909a8156556cd4a654dcfd6406de2bd45826e31b
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "67990495"
---
# <a name="join-a-role"></a>присоединение к роли
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  В этом разделе описывается назначение ролей для имен входа и пользователей базы данных в [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../../includes/tsql-md.md)]. Для эффективного управления разрешениями в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] используются роли. Назначайте разрешения ролям, а затем добавляйте и удаляйте пользователей и имена входа в роли. Благодаря ролям нет необходимости задавать разрешения для каждого пользователя в отдельности.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает четыре типа ролей.  
  
-   Предопределенные роли сервера  
  
-   Определяемые пользователем роли сервера  
  
-   Предопределенные роли базы данных  
  
-   Определяемые пользователем роли базы данных  
  
 Предопределенные роли доступны в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]автоматически. Предопределенные роли обладают необходимыми разрешениями для выполнения типичных задач. Дополнительные сведения о предопределенных ролях см. в следующих разделах. Определяемые пользователем роли создаются пользователем, им могут быть заданы любые разрешения по его выбору. Дополнительные сведения об определяемых пользователем ролях см. в следующих разделах.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Для назначения ролей именам входа и пользователям базы данных используется:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Изменение имени роли базы данных не изменяет идентификационный номер, владельца или разрешения роли.  
  
-   Роли базы данных видны в представлениях каталога sys.database_role_members и sys.database_principals.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Требуется разрешение **ALTER ANY ROLE** на базу данных, разрешение **ALTER** на роль или членство в роли **db_securityadmin**.  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>Добавление члена в предопределенную роль сервера  
  
1.  В обозревателе объектов разверните сервер, для которого нужно изменить предопределенную роль сервера.  
  
2.  Разверните папку **Безопасность** .  
  
3.  Разверните папку **Роли сервера**  
  
4.  Щелкните правой кнопкой мыши роль, которую необходимо изменить, и выберите пункт **Свойства**.  
  
5.  В диалоговом окне **Свойства роли сервера —** _имя\_роли\_сервера_ на странице **Члены** нажмите кнопку **Добавить**.  
  
6.  В диалоговом окне **Выбор имени входа или роли сервера** в разделе **Введите имена объектов для выбора (примеры)** введите имя входа или роль сервера для добавления в эту роль сервера. Также можно нажать кнопку **Обзор** и выбрать любые из доступных объектов в диалоговом окне **Выбор объектов**. Нажмите кнопку **ОК**, чтобы вернуться к диалоговому окну **Свойства роли сервера —** _имя\_роли\_сервера_.  
  
7.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>Добавление члена к определяемой пользователем роли базы данных  
  
1.  В обозревателе объектов разверните сервер, для которого нужно изменить определяемую пользователем роль базы данных.  
  
2.  Разверните папку **Базы данных** .  
  
3.  Разверните базу данных, в которой нужно изменить определяемую пользователем роль базы данных.  
  
4.  Разверните папку **Безопасность** .  
  
5.  Разверните папку **Роли** .  
  
6.  Разверните папку **Роли сервера** .  
  
7.  Щелкните правой кнопкой мыши роль, которую необходимо изменить, и выберите пункт **Свойства**.  
  
8.  В диалоговом окне **Свойства роли базы данных —** _имя\_роли\_базы_данных_ на странице **Общие** нажмите кнопку **Добавить**.  
  
9. В диалоговом окне **Выбор пользователя или роли базы данных** в разделе **Введите имена объектов для выбора (примеры)** введите имя входа или роль базы данных для добавления в эту роль базы данных. Также можно нажать кнопку **Обзор** и выбрать любые из доступных объектов в диалоговом окне **Выбор объектов**. Нажмите кнопку **ОК**, чтобы вернуться к диалоговому окну **Свойства роли базы данных —** _имя\_роли\_базы_данных_.  
  
10. [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-add-a-member-to-a-fixed-server-role"></a>Добавление члена в предопределенную роль сервера  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    ALTER SERVER ROLE diskadmin ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Дополнительные сведения см. в разделе [ALTER ROLE (Transact-SQL)](../../../t-sql/statements/alter-role-transact-sql.md).  
  
#### <a name="to-add-a-member-to-a-user-defined-database-role"></a>Добавление члена к определяемой пользователем роли базы данных  
  
1.  В **обозревателе объектов**подключитесь к экземпляру компонента [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  На стандартной панели выберите пункт **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**.  
  
    ```  
    ALTER ROLE Marketing ADD MEMBER [Domain\Juan] ;  
    GO  
    ```  
  
 Дополнительные сведения см. в статье [sp_addrolemember (Transact-SQL)](../../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
 [Роли уровня сервера](../../../relational-databases/security/authentication-access/server-level-roles.md)   
 [Роли уровня базы данных](../../../relational-databases/security/authentication-access/database-level-roles.md)   
 [Роли приложений](../../../relational-databases/security/authentication-access/application-roles.md)  
  
  
