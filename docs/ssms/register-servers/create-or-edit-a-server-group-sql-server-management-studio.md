---
title: Создание или изменение группы серверов
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.swb.editgroup.f1
- sql13.swb.newgroup.f1
helpviewer_keywords:
- Registered Servers [SQL Server], server groups
- server groups [SQL Server]
- groups [SQL Server], server
ms.assetid: d4a942bd-2dd1-42db-ad0e-e9a9ae5b856d
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.openlocfilehash: 61b9111eb218f479a2b46636b648a5c9715d49f7
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75246550"
---
# <a name="create-or-edit-a-server-group-sql-server-management-studio"></a>Создание или изменение группы серверов (среда SQL Server Management Studio)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

В этом разделе описывается организация серверов в компоненте «Зарегистрированные серверы» в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] путем создания групп серверов и помещения серверов в эти группы. Группы серверов в зарегистрированных серверах можно создавать в любое время, либо делать это при их регистрации.  

## <a name="SSMSProcedure"></a>

### <a name="to-create-a-server-group-in-registered-servers"></a>Создание группы серверов в зарегистрированных серверах  

1. В окне «Зарегистрированные серверы» выберите обозначение типа сервера на панели инструментов зарегистрированных серверов. Если окно «Зарегистрированные серверы» не отображается, выберите **Зарегистрированные серверы** в меню **Вид** .  

2. Щелкните правой кнопкой сервер или группу серверов, выберите пункт **Создать**и щелкните **Группа серверов**.  

3. В диалоговом окне **Создание группы серверов** перейдите к полю со списком **Имя группы** и введите уникальное имя для группы серверов. Имя группы серверов должно быть уникальным для текущего места в дереве «Зарегистрированные серверы».

4. В поле со списком **Описание группы** введите понятное имя, описывающее группу серверов, например «Финансовые серверы в Латинской Америке».  

5. В поле **Выберите место размещения новой группы серверов** выберите размещение группы и нажмите **Сохранить**.  

   > [!NOTE]
   > Также можно создать новую группу серверов при регистрации сервера. Для этого нажмите кнопку **Создать группу**и заполните параметры в диалоговом окне **Новая группа** .  

## <a name="see-also"></a>См. также:

[Регистрация серверов](../../tools/sql-server-management-studio/register-servers.md)