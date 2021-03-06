---
title: 'Управление записными книжками: Azure Data Studio'
titleSuffix: SQL Server Big Data Clusters
description: Сведения об управлении записными книжками в Azure Data Studio. Сюда входит открытие записных книжек, их сохранение и изменение подключения к кластеру больших данных.
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: mihaelab
ms.metadata: seo-lt-2019
ms.date: 12/13/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 8cf37ff6a4ad5e2b627fa5d968391cc5a7597a4a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "75244088"
---
# <a name="how-to-manage-notebooks-in-azure-data-studio"></a>Управление записными книжками в Azure Data Studio

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Эта статья описывает, как открывать и сохранять файлы записных книжек в Azure Data Studio с использованием SQL Server. В ней также показано, как изменить подключение к кластеру больших данных SQL Server.

## <a name="prerequisites"></a>Предварительные требования

В этой статье предполагается, что у вас уже есть записная книжка, которую нужно использовать в Azure Data Studio. Если вы хотите создать записную книжку, см. статью [Использование записных книжек в SQL Server](notebooks-guidance.md). Чтобы использовать записные книжки в Azure Data Studio, нужно выполнить следующие предварительные требования.

- [Развертывание кластера больших данных](quickstart-big-data-cluster-deploy.md).
- [Средства для работы с большими данными SQL Server 2019](deploy-big-data-tools.md)
   - **Azure Data Studio**
   - **Расширение SQL Server 2019**
   - **kubectl**

## <a name="open-a-notebook"></a>Открытие записной книжки

Диалоговое окно **Открытие записной книжки** можно открыть несколькими способами. Можно использовать меню "Файл", панель мониторинга и палитру команд. В приведенных ниже разделах описан каждый из этих способов.

### <a name="file-menu"></a>Меню "Файл"

Выберите **Файл > Открыть** в меню "Файл" (сочетание клавиш CTRL+O в Windows или CMD+O в Mac).

![Откройте диалоговое окно "Открытие файла", выбрав "Файл" > "Открыть"](./media/notebooks-how-to-manage/open-file-1.png) 

### <a name="dashboard"></a>Панель мониторинга

Щелкните **Открыть записную книжку** на панели мониторинга, чтобы открыть диалоговое окно "Открытие файла".

![Откройте диалоговое окно "Открытие файла", выбрав "Открыть записную книжку" на панели мониторинга](./media/notebooks-how-to-manage/open-file-2.png) 

### <a name="command-palette"></a>Палитра команд

Используйте команду **Файл: открыть** из палитры команд, нажав клавиши CTRL+SHIFT+P (в Windows) и CMD+SHIFT+P (в Mac).

![Откройте диалоговое окно "Открытие файла", введя "Файл: открыть" в палитре команд](./media/notebooks-how-to-manage/open-file-3.png)

## <a name="save-a-notebook"></a>Сохранение записной книжки

Сейчас доступен всего один способ сохранения записной книжки. Нужно выбрать элемент **Сохранить** на панели инструментов записной книжки.

![Сохраните файл, нажав элемент "Сохранить" на панели инструментов записной книжки.](./media/notebooks-how-to-manage/save-file-1.png)

> [!NOTE]
> На данный момент следующие способы не сохраняют изменения в записных книжках:
>
> - команды **Файл > Сохранить**, **Файл > Сохранить как...** и **Файл > Сохранить все** в меню "Файл";
> - команды **Файл: сохранить**, вводимые в палитре команд.

## <a name="change-the-big-data-cluster"></a>Изменение кластера больших данных

Чтобы изменить кластер больших данных SQL Server для записной книжки, сделайте следующее.

1. На панели инструментов записной книжки щелкните меню **Присоединить к**.

   ![На панели инструментов записной книжки щелкните меню "Присоединить к"](./media/notebooks-how-to-manage/select-attach-to-1.png)

2. Выберите сервер в меню **Присоединить к**.

   ![Выберите сервер в меню "Присоединить к"](./media/notebooks-how-to-manage/select-attach-to-2.png)

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о записных книжках в Azure Data Studio см. в статье [Использование записных книжек в SQL Server 2019](notebooks-guidance.md).
