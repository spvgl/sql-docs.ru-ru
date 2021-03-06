---
title: managed_backup. sp_backup_config_advanced (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_backup_config_optional
- sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional_TSQL
- managed_backup.sp_backup_config_optional
dev_langs:
- TSQL
helpviewer_keywords:
- sp_backup_config_optional
- managed_backup.sp_backup_config_optional
ms.assetid: 4fae8193-1f88-48fd-a94a-4786efe8d6af
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0178d4df6a5941b8896e6ff530802fd4c6bc6909
ms.sourcegitcommit: 64e96ad1ce6c88c814e3789f0fa6e60185ec479c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/27/2020
ms.locfileid: "77652953"
---
# <a name="managed_backupsp_backup_config_advanced-transact-sql"></a>managed_backup. sp_backup_config_advanced (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Настраивает дополнительные параметры для [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)].  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
EXEC managed_backup.sp_backup_config_advanced   
    [@database_name = ] 'database_name'  
    ,[@encryption_algorithm = ] 'name of the encryption algorithm'  
    ,[@encryptor_type = ] {'CERTIFICATE' | 'ASYMMETRIC_KEY'}  
    ,[@encryptor_name = ] 'name of the certificate or asymmetric key'  
    ,[@local_cache_path = ] 'NOT AVAILABLE'  
```  
  
##  <a name="Arguments"></a>Даваемых  
 @database_name  
 Имя базы данных для включения управляемого резервного копирования в определенной базе данных. Если задано значение NULL или *, то эта управляемая резервная копия применяется ко всем базам данных на сервере.  
  
 @encryption_algorithm  
 Имя алгоритма шифрования, используемого во время резервного копирования для шифрования файла резервной копии. Аргумент @encryption_algorithm имеет тип **sysname**. Это обязательный параметр при настройке конфигурации [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] в первый раз для базы данных. Укажите **NO_ENCRYPTION** , если вы не хотите шифровать файл резервной копии. При изменении параметров [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] конфигурации этот параметр является необязательным. Если параметр не указан, существующие значения конфигурации сохраняются. Разрешенные значения для этого параметра:  
  
-   AES_128  
  
-   AES_192  
  
-   AES_256  
  
-   TRIPLE_DES_3KEY  
  
-   NO_ENCRYPTION  
  
 Дополнительные сведения об алгоритмах шифрования см. в разделе [Choose an Encryption Algorithm](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md).  
  
 @encryptor_type  
 Тип шифратора, который может быть либо "CERTIFICATE", либо "ASYMMETRIC_KEY". Параметр @encryptor_type имеет тип **nvarchar (32)**. Этот параметр является необязательным, если для параметра задано значение @encryption_algorithm NO_ENCRYPTION.  
  
 @encryptor_name  
 Имя существующего сертификата или асимметричного ключа для шифрования резервной копии. Аргумент @encryptor_name имеет тип **sysname**. При использовании асимметричного ключа он должен быть сконфигурирован поставщиком расширенного управления ключами (EKM). Этот параметр является необязательным, если для параметра задано значение @encryption_algorithm NO_ENCRYPTION.  
  
 Дополнительные сведения см. в разделе [Расширенное управление ключами &#40;Расширенный поиск ключей&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 @local_cache_path  
 Этот параметр пока не поддерживается.  
  
## <a name="return-code-value"></a>Значения кодов возврата  
 0 (успех) или 1 (сбой).  
  
## <a name="security"></a>безопасность  
  
### <a name="permissions"></a>Разрешения  
 Требуется членство в роли базы данных **db_backupoperator** , с разрешениями **ALTER ANY CREDENTIAL** и **EXECUTE** для хранимой процедуры **sp_delete_backuphistory** .  
  
## <a name="examples"></a>Примеры  
 В следующем примере задаются дополнительные параметры [!INCLUDE[ss_smartbackup](../../includes/ss-smartbackup-md.md)] конфигурации для экземпляра SQL Server.  
  
```sql
Use msdb;  
Go  
   EXEC managed_backup.sp_backup_config_advanced  
                @encryption_algorithm ='AES_128'  
                ,@encryptor_type = 'CERTIFICATE'  
                ,@encryptor_name = 'MyTestDBBackupEncryptCert'  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [managed_backup. sp_backup_config_basic (Transact-SQL)](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-basic-transact-sql.md)   
 [managed_backup. sp_backup_config_schedule &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/managed-backup-sp-backup-config-schedule-transact-sql.md)  
  
  
