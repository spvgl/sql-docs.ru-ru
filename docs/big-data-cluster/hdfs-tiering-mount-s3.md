---
title: Подключение S3 для распределения по уровням HDFS
titleSuffix: SQL Server big data clusters
description: В этой статье описывается настройка уровней HDFS для подключения внешней файловой системы S3 к HDFS в [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)].
author: nelgson
ms.author: negust
ms.reviewer: mikeray
ms.date: 08/21/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 653f9a48c03df18fc0591f7bd8060d951567c779
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69652306"
---
# <a name="how-to-mount-s3-for-hdfs-tiering-in-a-big-data-cluster"></a>Подключение S3 для распределения по уровням HDFS в кластере больших данных

В следующих разделах приводится пример настройки распределения по уровням HDFS для источника данных хранилища S3.

## <a name="prerequisites"></a>предварительные требования

- [Развернутый кластер больших данных](deployment-guidance.md)
- [Средства работы с большими данными](deploy-big-data-tools.md)
  - **azdata**
  - **kubectl**
- Создание и загрузка данных в контейнер S3 
  - Загрузка файлов CSV или Parquet в контейнер S3. Это внешние данные HDFS, которые будут подключены к HDFS в кластере больших данных.

## <a name="access-keys"></a>Ключи доступа

### <a name="set-environment-variable-for-access-key-credentials"></a>Установка переменной среды для учетных данных ключей доступа

Откройте командную строку на клиентском компьютере, который может получать доступ к кластеру больших данных. Задайте переменную среды в следующем формате. Обратите внимание, что учетные данные нужно задавать в виде списка с разделителями-запятыми. В Windows используется команда "set". В Linux следует использовать команду "export".

   ```text
    set MOUNT_CREDENTIALS=fs.s3a.access.key=<Access Key ID of the key>,
    fs.s3a.secret.key=<Secret Access Key of the key>
   ```

   > [!TIP]
   > Дополнительные сведения о создании ключей доступа S3 см. в разделе [Ключи доступа S3](https://docs.aws.amazon.com/general/latest/gr/aws-sec-cred-types.html#access-keys-and-secret-access-keys).

## <a id="mount"></a> Подключение удаленного хранилища HDFS

После подготовки файла учетных данных с ключами доступа вы можете начать процесс подключения. Чтобы подключить удаленное хранилище HDFS в S3 к локальному хранилищу HDFS в кластере больших данных, выполните следующие действия.

1. Используйте **kubectl** для определения IP-адреса службы конечной точки **controller-svc-external** в кластере больших данных. Найдите параметр **External-IP**.

   ```bash
   kubectl get svc controller-svc-external -n <your-big-data-cluster-name>
   ```

1. Войдите в **azdata**, используя внешний IP-адрес конечной точки контроллера, а также имя и пароль пользователя кластера:

   ```bash
   azdata login -e https://<IP-of-controller-svc-external>:30080/
   ```
   
1. Задайте переменную среды MOUNT_CREDENTIALS в соответствии с приведенными выше инструкциями.

1. Подключите удаленное хранилище HDFS в Azure с помощью команды **azdata bdc hdfs mount create**. Замените значения заполнителей, после чего выполните следующую команду:

   ```bash
   azdata bdc hdfs mount create --remote-uri s3a://<S3 bucket name> --mount-path /mounts/<mount-name>
   ```

   > [!NOTE]
   > Команда mount create выполняется асинхронной. Сейчас сообщения об успешном подключении не реализованы. Чтобы проверить состояние подключений, обратитесь к разделу [status](#status).

Если подключение выполнено успешно, вы сможете запрашивать данные HDFS и выполнять задания Spark для их обработки. Данные для вашего кластера больших данных будут отображаться в HDFS в месте, которое задается атрибутом `--mount-path`.

## <a id="status"></a> Получение информации о состоянии подключений

Чтобы просмотреть состояние всех подключений в вашем кластере больших данных, выполните следующую команду:

```bash
azdata bdc hdfs mount status
```

Чтобы просмотреть состояние подключения с заданным путем в HDFS, выполните следующую команду:

```bash
azdata bdc hdfs mount status --mount-path <mount-path-in-hdfs>
```

## <a name="refresh-a-mount"></a>Обновление подключения

В следующем примере выполняется обновление подключения.

```bash
azdata bdc hdfs mount refresh --mount-path <mount-path-in-hdfs>
```

## <a id="delete"></a> Удаление подключения

Чтобы удалить подключение, выполните команду **azdata bdc hdfs mount delete** и укажите путь к подключению в HDFS:

```bash
azdata bdc hdfs mount delete --mount-path <mount-path-in-hdfs>
```

## <a name="next-steps"></a>Дальнейшие действия

Дополнительные сведения о [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)] см. в статье [Что такое [!INCLUDE[big-data-clusters-2019](../includes/ssbigdataclusters-ver15.md)]?](big-data-cluster-overview.md).
