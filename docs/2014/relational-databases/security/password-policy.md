---
title: Политика паролей | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- ALTER LOGIN statement
- passwords [SQL Server], policy enforcement
- logins [SQL Server], passwords
- CHECK_EXPIRATION option
- complex passwords [SQL Server]
- passwords [SQL Server], expiration
- manual bad password count resets
- MUST_CHANGE option
- expiration [SQL Server]
- expired password [SQL Server]
- symbols [SQL Server]
- NetValidatePasswordPolicy() API
- passwords [SQL Server]
- password policy [SQL Server]
- resetting bad password counts
- security [SQL Server], passwords
- CHECK_POLICY option
- passwords [SQL Server], symbols
- bad password counts
- passwords [SQL Server], complexity
- characters [SQL Server], password policies
ms.assetid: c0040c0a-a18f-45b9-9c40-0625685649b1
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 7b28043d797585496686dea6fd0c5fad276f16b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63187970"
---
# <a name="password-policy"></a>Политика паролей
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживается использование механизмов политики паролей Windows. Политика паролей применяется к имени входа, которое использует проверку подлинности [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , и к пользователю автономной базы данных с паролем.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] могут применяться политики сложности и истечения срока действия, которые применяются в Windows к паролям, используемым в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Эти возможности построены на API-интерфейсе `NetValidatePasswordPolicy` .  
  
## <a name="password-complexity"></a>Сложность пароля  
 Политика сложности паролей позволяет отражать атаки, использующие простой перебор, путем увеличения числа возможных паролей. Если применяется политика сложности паролей, новые пароли должны удовлетворять следующим требованиям.  
  
-   Пароль не содержит имя учетной записи пользователя.  
  
-   Длина пароля составляет не менее восьми символов.  
  
-   Пароль содержит символы, соответствующие трем из следующих четырех категорий:  
  
    -   прописные латинские буквы (А-Z)  
  
    -   строчные латинские буквы (a-z)  
  
    -   цифры (0-9)  
  
    -   Символы, отличные от буквенно-цифровых: восклицательный знак (!), знак доллара ($), решетка (#) или знак процента (%).  
  
 Пароли могут иметь длину до 128 символов. Рекомендуется использовать максимально длинные и сложные пароли.  
  
## <a name="password-expiration"></a>Истечение срока действия пароля  
 Политика истечения срока действия паролей используется для управления продолжительностью действия пароля. Когда [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] применяет политику истечения срока действия паролей, пользователи получают уведомления о необходимости изменения старых паролей, а учетные записи с истекшим сроком действия пароля отключаются.  
  
## <a name="policy-enforcement"></a>Применение политики  
 Применение политики паролей можно настроить отдельно для каждого имени входа SQL Server. Чтобы настроить параметры политики паролей для имени входа SQL Server, выполните инструкцию [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql) . Для настройки принудительного применения политики паролей действуют следующие правила.  
  
-   При переключении параметра CHECK_POLICY на значение ON происходит следующее:  
  
    -   параметр CHECK_EXPIRATION также изменяется на ON, если он не будет прямо изменен на OFF;  
  
    -   Журнал паролей инициализируется значением хэша текущего пароля.  
  
    -   Также включается **длительность блокировки**учетной записи, **порог блокировки учетной**записи и **Сброс счетчика блокировки учетных** записей.  
  
-   При переключении параметра CHECK_POLICY в значение OFF происходит следующее:  
  
    -   Параметр CHECK_EXPIRATION также получает значение OFF.  
  
    -   Журнал паролей очищается.  
  
    -   Значение параметра `lockout_time` сбрасывается.  
  
 Некоторые сочетания параметров политик не поддерживаются.  
  
-   Если задан параметр MUST_CHANGE, то параметры CHECK_EXPIRATION и CHECK_POLICY должны иметь значение ON. В противном случае выполнение инструкции приведет к ошибке.  
  
-   Если значение параметра CHECK_POLICY установлено равным OFF, то параметр CHECK_EXPIRATION не может иметь значения ON. Выполнение инструкции ALTER LOGIN с таким сочетанием параметров завершится ошибкой.  
  
 При установке параметра CHECK_POLICY = ON блокируется создание следующих паролей:  
  
-   пустых или неопределенных;  
  
-   совпадающих с именем компьютера или именем входа;  
  
-   представляющих собой любую из следующих строк: "password", "admin", "administrator", "sa", "sysadmin".  
  
 Политика безопасности может быть настроена в Windows или получена из домена. Для просмотра политики паролей на компьютере используется оснастка консоли управления "Локальная политика безопасности" (**secpol.msc**).  
  
## <a name="related-tasks"></a>Связанные задачи  
 [CREATE LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-login-transact-sql)  
  
 [ALTER LOGIN &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-login-transact-sql)  
  
 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)  
  
 [&#41;Transact-SQL ALTER USER &#40;](/sql/t-sql/statements/alter-user-transact-sql)  
  
 [Создание имени входа](authentication-access/create-a-login.md)  
  
 [Создание пользователя базы данных](authentication-access/create-a-database-user.md)  
  
## <a name="related-content"></a>См. также  
 [Надежные пароли](strong-passwords.md)  
  
  
