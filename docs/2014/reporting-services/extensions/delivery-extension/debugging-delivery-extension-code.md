---
title: Отладка кода модулей доставки | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery extensions [Reporting Services], debugging
- debugging delivery extensions [Reporting Services]
- troubleshooting [Reporting Services], delivery extensions
ms.assetid: a7d959da-5005-4a50-aca7-2cef36aa9947
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 0d289b3d4c4177ed885a3153bb758d0052286bec
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63164331"
---
# <a name="debugging-delivery-extension-code"></a>Отладка кода модулей доставки
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Предоставляет несколько средств отладки, которые могут помочь в анализе кода модуля доставки и обнаружении ошибок в [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] нем. Какое средство будет наилучшим, зависит от того, что нужно выполнить. В этом примере используется [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)].  
  
#### <a name="to-debug-your-delivery-extension-code"></a>Отладка кода в модуле доставки  
  
1.  Запустите среду [!INCLUDE[vsOrcas](../../../includes/vsorcas-md.md)] и откройте проект модуля доставки.  
  
2.  Выполните построение проекта и разверните сборку модуля доставки и сопровождающего ее PDB-файла на сервере отчетов и в диспетчере отчетов. Дополнительные сведения о развертывании см. в разделе [Развертывание модуля доставки](deploying-a-delivery-extension.md).  
  
3.  Если создан пользовательский интерфейс подписки, расширяющий диспетчер отчетов, откройте обозреватель Internet Explorer и перейдите к диспетчеру отчетов, оставив код модуля доставки открытым в среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]. Если для диспетчера отчетов не развернут пользовательский интерфейс подписки, просто откройте клиентское приложение, из которого можно вызывать модуль доставки по API-интерфейсу SOAP.  
  
4.  Перейдите в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] к проекту модуля доставки и задайте в коде несколько точек останова.  
  
5.  Пока окно с проектом модуля доставки остается активным, выберите в меню **Отладка** команду **Присоединить к процессу**.  
  
     Откроется диалоговое окно **Присоединение к процессу**.  
  
6.  В списке процессов выберите процесс aspnet_wp.exe (или w3wp.exe, если приложение развернуто на сервере IIS 6.0) и нажмите кнопку **Присоединить**.  
  
7.  Определите новую подписку с помощью модуля доставки. Для этого обычно используется диспетчер отчетов или API-интерфейс SOAP. Будет запущен отладчик и начнется выполнение кода с учетом заданных точек останова.  
  
8.  Пройдите код с помощью клавиши **F11** . Дополнительные сведения об использовании среды [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] для отладки см. в документации по среде [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>См. также:  
 [Реализация модуля доставки](implementing-a-delivery-extension.md)   
 [Библиотека модулей Reporting Services](../reporting-services-extension-library.md)  
  
  
