---
title: База данных сервера отчетов не настроена (советник по переходу) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- report servers [Reporting Services], upgrade issues
ms.assetid: b964300c-b220-4244-9fa6-c0c6a57760f6
author: maggiesMSFT
ms.author: maggies
manager: craigg
ms.openlocfilehash: bb5dd5968930319532a29ff7c3909c36af99b3a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "71952108"
---
# <a name="report-server-database-is-not-configured-upgrade-advisor"></a>База данных сервера отчетов настроена (советник по переходу)
  Обновление заблокировано в связи с тем, что настройка сервера отчетов не завершена. База данных сервера отчетов не настроена.  
  
||  
|-|  
|**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]В основном режиме [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] &#124; в режиме интеграции с SharePoint.|  
  
## <a name="component"></a>Компонент  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]  
  
## <a name="description"></a>Description  
 Программа обновления может обновить только полностью настроенный экземпляр сервера отчетов. Чтобы продолжить, необходимо либо настроить базу данных сервера отчетов, либо с помощью **панели управления** Microsoft Windows удалить компонент сервера отчетов из установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . После удаления служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]можно произвести обновление других компонентов [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
## <a name="corrective-action"></a>Действие по исправлению  
 Если база данных сервера отчетов не была настроена, сервер отчетов находится в нерабочем состоянии и должен быть удален до обновления.  
  
 Дополнительные сведения об удалении служб [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] см. в разделе [Удаление служб Reporting Services 2012](https://technet.microsoft.com/library/hh479745.aspx\(v=sql.11\)). в разделе описывается удаление конкретной версии. Эта процедура похожа на ту, которая была в предыдущих версиях.  
  
## <a name="see-also"></a>См. также:  
 [Reporting Services проблем обновления &#40;советник по переходу&#41;](../../../2014/sql-server/install/reporting-services-upgrade-issues-upgrade-advisor.md)  
  
  
