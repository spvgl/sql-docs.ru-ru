---
title: Microsoft SQL Server Reporting Services общая служба SharePoint установлена параллельно (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 6ae1017e-129b-4702-9ea7-00ac9b024062
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: 529e07dc7beed8dc37741f6c9dab0b0b080d4898
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952691"
---
# <a name="microsoft-sql-server-reporting-services-sharepoint-shared-service-is-installed-side-by-side-upgrade-advisor"></a>Общая служба Microsoft SQL Server Reporting Services SharePoint установлена параллельно (советник по переходу)
  Советник по переходу обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , что общая служба SharePoint установлена параллельно с предыдущей версией [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]Режим интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Советник по переходу обнаружил [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] , [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] что общая служба SharePoint установлена параллельно с предыдущей версией, которая не основана на архитектуре общей службы SharePoint. Поскольку на компьютере параллельно установлены старая и новая версии служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], связанных с технологиями SharePoint, обновление заблокировано.  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Чтобы продолжить обновление, необходимо удалить одну из существующих установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. После удаления одной из установок служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] повторно запустите помощник по обновлению, чтобы убедиться в отсутствии других проблем обновления.  
  
  
