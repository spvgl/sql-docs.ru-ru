---
title: Диспетчер подключений Oracle | Документация Майкрософт
ms.custom: ''
ms.date: 08/14/2019
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 092760fdd99a6840e77278fce96e2d321ea4edc9
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "69553247"
---
# <a name="oracle-connection-manager"></a>Диспетчер подключений Oracle

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]

Диспетчер подключений Oracle разрешает пакету извлекать данные из баз данных Oracle DB и загружать их туда.

Свойству **ConnectionManagerType** диспетчера подключений Oracle присваивается значение **ORACLE**.

## <a name="configuring-the-oracle-connection-manager"></a>Настройка диспетчера подключений Oracle

Изменения конфигурации диспетчера подключений Oracle будут разрешены службами Integration Services во время выполнения. Диалоговое окно **Диспетчер подключений Oracle** используется для добавления подключения к источнику данных Oracle.

![Диспетчер соединений](media/oracle-connection-manager.png)

### <a name="options"></a>Параметры

#### <a name="connection-manager-information"></a>Сведения о диспетчере подключений

Введите данные о подключении Oracle.

**имя**;

Введите имя для подключения Oracle. Имя по умолчанию — Oracle Connection Manager. 

**Описание** 

Введите описание диспетчера подключений. Это необязательно.

**Имя службы TNS**

Введите имя базы данных Oracle, которую вы используете. Имя службы TNS может быть следующим:

- Имя дескриптора подключения определено в файле tnsnames.ora, расположенном в папке Admin клиента Oracle.

- Формат EzConnect: [//]host[:port][/service_name]

Дополнительные сведения см. в документации Oracle.

#### <a name="connection-manager-logging"></a>Ведение журнала для диспетчера подключений

Выберите один из следующих параметров:

- **Использовать проверку подлинности Windows**. Выберите этот параметр, чтобы использовать проверку подлинности Windows.

- **Использовать проверку подлинности Oracle**. Выберите этот параметр, чтобы использовать проверку подлинности базы данных Oracle. Если вы выбрали этой вариант проверки подлинности, введите следующие учетные данные Oracle:  
    **Имя пользователя**. Введите имя пользователя для подключения к базе данных Oracle.  
    **Пароль**. Введите пароль базы данных Oracle для пользователя, имя которого указано в соответствующем поле.

> [!NOTE]
>
>Проверка подлинности Windows не поддерживается клиентом Oracle Server 18c.

**Проверка соединения**

Нажмите кнопку **Проверить подключение**, чтобы проверить правильность предоставленных сведений. Если указанные сведения подходят для подключения к базе данных Oracle, вы получите сообщение **Проверка подключения выполнена успешно**.

### <a name="custom-properties"></a>Пользовательские свойства

В диспетчере подключений Oracle есть следующие пользовательские свойства:

- **EnableDetailedTracing**. Не используется.

- **OracleHome**. Укажите 32-разрядное имя корневого каталога Oracle или другой папки, которая будет использоваться соединителем. (необязательно)

- **OracleHome64**. Укажите 64-разрядное имя корневого каталога Oracle или другой папки, которые будут использоваться соединителем при работе в 64-разрядном режиме. (необязательно)

Пользовательские свойства не перечислены в редакторе диспетчера подключений Oracle. Чтобы задать свойства **OracleHome** и **OracleHome64**, сделайте следующее:

1. В области диспетчера подключений Oracle щелкните правой кнопкой мыши имя используемого диспетчера и выберите **Свойства**.

2. На панели **Свойства** задайте свойство **OracleHome** или **OracleHome64** и укажите полный путь к корневому каталогу Oracle.

## <a name="next-steps"></a>Дальнейшие действия

- Настройка [источника Oracle](oracle-source.md).
- Настройка [назначения Oracle](oracle-destination.md).
- Если у вас возникнут вопросы, посетите страницу [технического сообщества](https://aka.ms/AA5u35j).
