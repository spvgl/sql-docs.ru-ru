---
title: Настройка IntelliSense (среда SQL Server Management Studio)
ms.custom: seo-lt-2019
ms.date: 06/02/2016
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Options [SQL Server Management Studio], IntelliSense
- modifying IntelliSense options
- IntelliSense [SQL Server], modifying options
ms.assetid: 3ffc9f31-4efa-4c1a-a033-ed1dc48b065f
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3310c432e872ca7819c6d9f60b777d1b077f9f98
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75253953"
---
# <a name="configure-intellisense-sql-server-management-studio"></a>Настройка IntelliSense (среда SQL Server Management Studio)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Большинство параметров технологии [!INCLUDE[msCoName](../../includes/msconame-md.md)] IntelliSense по умолчанию включено. Отдельные параметры IntelliSense можно отключить и вместо этого выполнять соответствующие действия посредством команды меню или сочетания клавиш.  
  
> [!IMPORTANT]  
>  Некоторые изменения вступают в силу только после перезапуска редактора.  Чтобы увидеть изменения, откройте новый сеанс редактора Transact-SQL.
  
### <a name="to-turn-statement-completion-options-off-by-default"></a>Чтобы отключить параметры заполнения инструкций по умолчанию  

> [!NOTE]
> Хранилище данных SQL не поддерживает IntelliSense.
>
>
  
1.  В меню **Сервис** выберите команду **Параметры**.  
  
2.  Раскройте список **Редактор текстов**, затем список **Все языки**, **Transact-SQL**или **XML**, после чего выберите пункт **Общие**.  
  
3.  Снимите флажки параметров заполнения инструкций, которые не требуются, а затем нажмите кнопку **ОК**.  
  
### <a name="to-modify-transact-sql-intellisense-options"></a>Изменение параметров технологии Transact-SQL IntelliSense  
  
1.  В меню **Сервис** выберите команду **Параметры**.  
  
2.  Раскройте список **Текстовый редактор**, затем список **Transact-SQL**, после чего выберите **IntelliSense**.  
  
3.  Снимите флажки параметров IntelliSense, которые не требуются.  
  
4.  Чтобы изменить размер скрипта, при котором отключаются функции IntelliSense, выберите размер из списка **Максимальный размер скрипта** .  
  
5.  Чтобы изменить правила учета регистра, применяемые к именам функций в списках завершения, выберите спецификацию регистра в списке **Регистр для имен встроенных функций** .  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
