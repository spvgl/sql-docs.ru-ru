---
title: Настройка уведомления электронной почты
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- e-mail [Master Data Services], configuring
- notifications [Master Data Services], configuring notifications
ms.assetid: 4241a6ab-7465-471b-9890-57c6b572037e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2b49a2a9b52df3cf5364f0e4f86b4181439ff61b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73729650"
---
# <a name="configure-email-notifications-master-data-services"></a>Настройка уведомления электронной почты (службы Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  Настройка автоматической отправки уведомлений по электронной почте в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
### <a name="to-configure-notifications"></a>Настройка уведомлений  
  
1.  Выберите свою базу данных [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]на странице **База данных** в [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] .  
  
2.  В разделе **Системные настройки** нажмите **Создать профиль**.  
  
3.  Заполните все необходимые поля. Дополнительные сведения см. в разделе [Диалоговое окно "Создание профиля электронной почты и учетной записи базы данных" (диспетчер конфигурации служб Master Data Services)](../master-data-services/create-database-mail-profile-and-account-dialog-box.md).  
  
4.  Нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    >  После настройки уведомлений вносить изменения с помощью [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] нельзя. Это нужно делать непосредственно в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в статье [Database Mail Configuration Objects](../relational-databases/database-mail/database-mail-configuration-objects.md).  
  
## <a name="next-steps"></a>Next Steps  
  
-   В [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] есть параметры, влияющие на рассылку уведомлений. Эти параметры можно настроить в программе [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)] или непосредственно в таблице системных параметров в базе данных [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] . Дополнительные сведения см. в разделе [Системные параметры (службы Master Data Services)](../master-data-services/system-settings-master-data-services.md).  
  
## <a name="see-also"></a>См. также:  
 [Master Data Services &#40;уведомлений&#41;](../master-data-services/notifications-master-data-services.md)   
 [Устранение неполадок с уведомлениями по электронной почте (Master Data Services)](https://social.technet.microsoft.com/wiki/contents/articles/troubleshooting-email-notifications-master-data-services.aspx)   
 [Настройка бизнес-правил для отправки уведомлений &#40;Master Data Services&#41;](../master-data-services/configure-business-rules-to-send-notifications-master-data-services.md)  
  
  
